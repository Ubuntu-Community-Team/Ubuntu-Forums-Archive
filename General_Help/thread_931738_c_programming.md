---
title: "c programming?"
date: 2008-09-27
forum: General Help
---

### Post by overtime on 2008-09-27
so I am trying to make a basic program but am running into problems.

I have this code:

[I]#include <stdlib.h>
#include <stdio.h>

int main()
{
  printf("runninf ps with system\n");
  system("ps ax");
  printf("dont\n");
  exit(0);
}[/I]


And then I try to compile it but I get errors.
gcc system1.c -o system1

It says:

system1.c:1:20: error: stdlib.h: No such file or directory
system1.c:2:18: error: stdio.h: No such file or directory
system1.c: In function 'main':
system1.c:7: warning: incompatible implicit declaration of built-in function 'printf'
system1.c:10: warning: incompatible implicit declaration of built-in function 'exit'


I dont understand why I get these.

---

### Post by cariboo on 2008-09-27
It looks like you don't have build-essential installed.

JIm

---

### Post by niteshifter on 2008-09-27
Hi,

You need to get the package "build-essential" from the repositories.

---

### Post by overtime on 2008-09-27
where do I get that from? And how?

I am very very new to Ubuntu, Unix and Linux. So please explain to me things as if i dont know anything.

Thanks

---

### Post by Xiong Chiamiov on 2008-09-27
> **overtime said:**
> where do I get that from? And how?

I am very very new to Ubuntu, Unix and Linux. So please explain to me things as if i dont know anything.

Thanks
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by werries on 2008-09-27
To say directly, open a terminal, Applications > Accessories > Terminal.
and type this command hit enter, and then enter your password.
```
sudo apt-get install build-essential
```
sudo gives you admin priveleges, apt-get is the package manager, install is the extension command of apt-get, and build-essential is the required package.

---

### Post by overtime on 2008-09-27
it asked for the ubuntu disk 7.10
which luckily i had. But what if i didnt have the disk?

---

### Post by Predator106 on 2008-09-27
I believe if you did not have the disk, you would have to go into Software Sources, then uncheck to use the CD-ROM. This would, of course require you to rebuild the software list, and have an active internet connection. I never use the CD, if you have an internet connection that is somewhat fast i.e. not 56k :) then I would suggest removing the cd option. It's more a pain than anything, especially since you wouldn't get the newest version of the application.

---

