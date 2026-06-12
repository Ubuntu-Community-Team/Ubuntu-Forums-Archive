---
title: "Help Programming C++"
date: 2008-09-24
forum: General Help
---

### Post by Cyberbanana1 on 2008-09-24
Our homework was to compile a program at home that we did at school, but i have a different compiler and it doesn't seem to work. I was wondering if anyone could tell me how I could make this program work, and explain why it happens that way. My program thing was 
"
#include <iostream>
using namespace std;
int main (void)
{
int a,b;

a=2;
b=3;

cout << a << '+' << b << "=" << (a+b) <<

cout << (a+b)<< "\n";

return 0;
}
"
when ran, i got "2+3=50x8049d245" Thanks to anyone that can help.

---

### Post by leg on 2008-09-24
.

---

### Post by Cyberbanana1 on 2008-09-24
i took leg's advice, now the code reads as such

#include <iostream>
using namespace std;
int main (void)
{
int a,b;

a=2;
b=3;

cout << a << '+' << b << "=" << (a+b);

cout << (a+b)<< "\n";

return 0;
}



Now the answer is 55. Much closer. But there must be something im missing

---

### Post by leg on 2008-09-24
You are out putting the answer twice, once on each cout line.

---

### Post by Cyberbanana1 on 2008-09-24
Oh, thanks. i got it now.

---

### Post by dmizer on 2008-09-24
The Ubuntu forums are not a homework service.

Thread closed.

---

