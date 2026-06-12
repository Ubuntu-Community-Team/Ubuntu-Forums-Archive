---
title: "Not able to read a file"
date: 2008-10-29
forum: General Help
---

### Post by charanpreethu on 2008-10-29
I wrote a c program to read a file and print it..both file and program is on desktop..the program shown below

#include<stdio.h>
#include<string.h>

int main()
{
   char ch;
   FILE *fp;
   
   fp=fopen("a.c","r");
   if(fp==NULL)
   {
      printf("no file found");
       return 0;
   }
   
 while( (ch=getc(fp))!=EOF)
   {   
     puts(ch);
     }
    fclose(fp);
}




I am getting segmentation fault error...what is the mistake???

---

### Post by Portmanteaufu on 2008-10-29
A quick guess (I didn't compile this or test it) would be that "puts" expects a C string and not a single character.

Try replacing that with "putchar", maybe.

---

### Post by SteveLefty on 2008-10-29
You definitely want to use putchar(char c).  You also don't have main returning anything after your while loop, which will create another error:

ch = getc(fp);

while((ch != EOF){
putchar(ch);
ch = getc(fp);
}

fclose(fp);
return 0;

---

