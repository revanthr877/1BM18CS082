#include<stdio.h>
#include<stdlib.h>

typedef struct node{
	int data;
    struct node *next;
    struct node *prev;
}*Node;

Node create_node(){
	Node temp;
	temp=(Node)malloc(sizeof(Node));
	return temp;
}

Node insert_front(Node head,int ele){
	Node p;
	p=create_node();
	p->data=ele;
	p->next=head;
	p->prev=NULL;
	if(head!=NULL)
		head->prev=p;
	return p;
}

Node insert_rear(Node head,int ele){
	Node p,q;
	p=create_node();
	p->data=ele;
	p->next=NULL;
	p->prev=NULL;
	if(head==NULL)
		return p;
	else{
		q=head;
		while(q->next!=NULL)
			q=q->next;
		q->next=p;
		p->prev=q;
		return head;
	}
}

Node insert_position(Node head,int ele,int pos){
	int count=1;
	Node p,q,n;
	p=create_node();
	p->data=ele;
	p->next=NULL;
	p->prev=NULL;
	if(head==NULL){
		if(pos==1)
			return p;
		else
			printf("Invalid\n");
	}
	else{
		q=head;
		if(pos==1){
			p->next=head;
			head->prev=p;
			return p;
		}
		while(q!=NULL && count!=pos){
			n=q;
			q=q->next;
			count++;
		}
		if(count==pos){
			n->next=p;
			p->prev=n;
			p->next=q;
			if(q!=NULL)
				q->prev=p;
		}
		else
			printf("Invalid\n");
	}
	return head;
}

Node delete_front(Node head){
	Node p;
	if(head==NULL)
		return head;
	p=head->next;
	printf("Deleted element: %d",head->data);
	free(head);
	if(p!=NULL)
		p->prev=NULL;
	return p;
}

Node delete_rear(Node head){
	Node p,q;
	if(head==NULL)
		return head;
	if(head->next==NULL){
		printf("Deleted element: %d\n",head->data);
		free(head);
		return NULL;
	}
	p=head;
	while(p->next!=NULL){
		q=p;
		p=p->next;
	}
	printf("Deleted element: %d\n",p->data);
	q->next=NULL;
	free(p);
	return head;
}

Node delete_position(Node head,int pos){
	Node p,q;
	int c=1;
	if(head==NULL)
		return head;
	if(pos==1)
		return(delete_front(head));
	p=head;
	while(p->next!=NULL && c!=pos){
		q=p;
		p=p->next;
		c++;
	}
	if(c==pos){
		printf("Deleted element: %d\n",p->data);
		q->next=p->next;
		if(p->next!=NULL){
			(p->next)->prev=q;
		}
		free(p);
	}
	else
		printf("Invalid choice\n");
	return head;
}

void display(Node head){
	Node p;
	p=head;
	if(head==NULL)
		printf("List is empty\n");
	else{
		printf("Elements: ");
		while(p!=NULL){
			printf("%d ",p->data);
			p=p->next;
		}
	}
	printf("\n");
}

int main(){
	Node head=NULL;
	int option,ele,pos;
	do{
		printf("\n1)Insert Rear\n2)Insert Front\n3)Insert At Position\n4)Delete front\n5)Delete Rear\n6)Delete at position\n7)Exit\n");
		printf("Enter your option: ");
		scanf("%d",&option);
		switch(option){
			case 1: printf("Enter the element to be inserted: ");
			        scanf("%d",&ele);
			        head=insert_rear(head,ele);
			        display(head);
			        break;
			case 2: printf("Enter the element to be inserted: ");
			        scanf("%d",&ele);
			        head=insert_front(head,ele);
			        display(head);
			        break;
			case 3: printf("Enter the element to be inserted and position: ");
			        scanf("%d %d",&ele,&pos);
			        head=insert_position(head,ele,pos);
			        display(head);
			        break;
			case 4: head=delete_front(head);
			        display(head);
			        break;
			case 5: head=delete_rear(head);
			        display(head);
			        break;
			case 6: printf("Enter the position: ");
                    scanf("%d",&pos);
                    head=delete_position(head,pos);
			        display(head);
			        break;  
			case 7: break;          
			default: printf("Invalid choice\n");       
		}
	}while(option!=7);
	return 0;
}
