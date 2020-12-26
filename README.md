#include <iostream>
using namespace std;

//đề nhập vào cây nhị phân xuất ra cây
//khai báo cấu trúc 1 node
struct  node
{
	int data;  //dữ liệu của node
	struct node* pLeft;//node liên kết bên trái
	struct node* pRight;//node liên kết bên phải
};
typedef struct node NODE;
typedef NODE* TREE;
void khoitaocay(TREE& t)
{
	t = NULL; //cây rỗng
}
//hàm thêm x vào cây
void themnodevaocay(TREE& t, int x)
{
	//nếu cây rỗng
	if (t == NULL)
	{
		NODE* p = new NODE;//tao 1 node để them vào cây
		p->data = x;//thêm dữ liệu x vào data
		p->pLeft = NULL;
		p->pRight = NULL;
		t = p;//x là node gốc
	}
	else //cây có tồn tài phần tử
	{
		//nếu thếm phần tử x và nhỏ hơn node gốc thì thêm bên trái
		if (t->data > x)
		{
			themnodevaocay(t->pLeft, x);//duyệt qua bên trái
		}
		else
			if (t->data < x)
			{
				themnodevaocay(t->pRight, x);//duyệt qua phải
			}


	}
}
void duyet_NLR(TREE t)
{
	if (t != NULL)
	{
		cout << t->data << " ";
		duyet_NLR(t->pLeft);
		duyet_NLR(t->pRight);
	}
}
void prind(TREE& t, int k1, int k2)
{
	if (t == NULL)
		return;
	if (k1 < t->data)

		prind(t->pLeft, k1, k2);
	if (k1 <= t->data && k2 >= t->data)
		cout << t->data << " ";
	if (k2 > t->data)
		prind(t->pRight, k1, k2);
}
int main()
{
	TREE t = NULL;
	int ch, x, n;
	int k1, k2;
	do {
		cout << "\n1:nhap     2:duyet      3:tong cay con    4:thoat ";
		cin >> ch;
		switch (ch)
		{
		case 1:
			cout << "nhap gia tri: "; cin >> x;
			themnodevaocay(t, x);
			break;
		case 2:
			duyet_NLR(t);
			break;
		case 3:
			cout << "nhap k1 :"; cin >> k1;
			cout << "nhap k2 :"; cin >> k2;
			cout << "gia tri do sau cua cay  ";
			prind(t, k1, k2);
			break;

		}
	} while (ch != 4);
	return 0;
}
