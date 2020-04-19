public RandomLinkedListNode CopyRandomListWeaved(RandomLinkedListNode head)
        {

            if (head == null) return null;

            RandomLinkedListNode ptr = head;

            while(ptr!=null)
            {
                RandomLinkedListNode newNode = new RandomLinkedListNode(ptr.val,null,null);

                newNode.next = ptr.next;
                ptr.next = newNode;
                ptr = newNode.next;
            }

            ptr = head;

            while(ptr!=null)
            {
                ptr.next.random = (ptr.random != null) ? ptr.random.next : null;
                ptr = ptr.next.next;
            }

            RandomLinkedListNode ptr_old_list = head; // A->B->C
            RandomLinkedListNode ptr_new_list = head.next; // A'->B'->C'
            RandomLinkedListNode head_old = head.next;

            while (ptr_old_list != null)
            {
                ptr_old_list.next = ptr_old_list.next.next;
                ptr_new_list.next = (ptr_new_list.next != null) ? ptr_new_list.next.next : null;
                ptr_old_list = ptr_old_list.next;
                ptr_new_list = ptr_new_list.next;
            }

            return head_old;
        }
