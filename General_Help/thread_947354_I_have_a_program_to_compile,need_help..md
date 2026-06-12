---
title: "I have a program to compile,need help."
date: 2008-10-14
forum: General Help
---

### Post by wxjeacen on 2008-10-14
/*This program is to permute some letters of alphabet.
 However i can not compile it .
 There are always many errors. 
 your help will be appreciated deeply.
 I am a new guy in Ubuntu .*/

#include<stdio.h>
#include<string.h>
int L;
void insort(int n,char *s,char c[]);


void insort(int n,char *s,char c[])
{  
    char *d;
   char *str1,*str2;
    int i;
    if(n==0) *s=c[n];
    for(i=n;i>=0;i--)
   { d=s;
     memcpy(str1,d,i);
     str2=d+i;
     strcat(str1,c[n]);
     strcat(str1,str2);
     d=str1;
     if (n==L)printf("%s\n",d);
     }
    if (n+1<=L)
    insort(n+1,s,c);
     
     
}




int main()

{  char *str='\0';

   char S[];
   printf("The letters to permuted are:");
   scanf("%s
",S);
   L =strlen(S);

   insort(0,str,S);

 printf("\n");
   return 0;

}

---

### Post by Sef on 2008-10-14
Read this [Howto]("https://help.ubuntu.com/community/CompilingEasyHowTo") on compiling.

---

### Post by wxjeacen on 2008-10-14
> **Sef said:**
> Read this [Howto]("https://help.ubuntu.com/community/CompilingEasyHowTo") on compiling.

:KSThank you .
I have fixed my compile environment,gcc and gdb.
This is just a problem of algorithm.

---

### Post by wxjeacen on 2008-10-14
somebody help me....

---

