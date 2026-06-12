---
title: "install 'C' library"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by rahul_shilps on 2009-06-06
Hi , 

i have Ubuntu 8.04 distribution and there is no inbuilt 'C' Library. I don't have internet on my machine. How can i install 'C' Library. 

Is there any provision that i download separately the 'C' Library and then take it in pen drive. And then i install it on my machine on Ubuntu 8.04. So what will be the steps to install  "C" Library in case i download it explicitly?

---

### Post by amingv on 2009-06-06
You can get the standard (basic) library in the package build-essential, which is included in the Ubuntu CD.

With your cd in the drive:

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

```

---

### Post by rahul_shilps on 2009-07-13
> **amingv said:**
> You can get the standard (basic) library in the package build-essential, which is included in the Ubuntu CD.

With your cd in the drive:

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

```

Hello,

I have done as what you said. It worked.

But now when i followed the same steps for my other Desktop machine it is no upgrading Library resources.

Please suggest me the way i can do it.

Thanks
Rahul

---

### Post by master_kernel on 2009-07-13
sudo apt-get install gcc

---

### Post by rahul_shilps on 2009-07-13
But i was able to compile the ".c" and it runs fine.

I just get error of the header files which are not included in lib.

The step you are suggesting will only install gcc. Am i right?

gcc is already installed on my machine and compilation is just fine.

---

### Post by amingv on 2009-07-13
> **rahul_shilps said:**
> But i was able to compile the ".c" and it runs fine.

I just get error of the header files which are not included in lib.

The step you are suggesting will only install gcc. Am i right?

gcc is already installed on my machine and compilation is just fine.

build-essential only has the most basic standard libraries of C (as I hinted in my first post). If the program you're trying to compile needs an additional library, you'd need to download it separately.

Try getdeb.net or
```
aptitude download <library_name>
```
In a computer with internet access, please understand, however, that you'll have to deal with any possible dependencies manually.

Also bear in mind that even if you install all the libraries corectly, you may need to point gcc to the library at compile time anyways. For example:

```
gcc -Wall foo.c -l<library_name> -o foo
```
or
```
gcc -Wall foo.c -L/path/to/search -o foo
```

---

### Post by rahul_shilps on 2009-07-15
Hi,

Internet is not available at my desktop. So now i want to know how can i download the lib on my Pen Drive?

and how can i update that library from my pen drive?

Thank in advance.

- Rahul

---

### Post by rahul_shilps on 2009-07-15
i have to download the library package from Cyber cafe and then i have to take it in Pen Dirve.
How can i download explicitly that library on Pen Drive?
How can i install library from Pen Drive?

Please tell me

---

### Post by amingv on 2009-07-15
> **rahul_shilps said:**
> i have to download the library package from Cyber cafe and then i have to take it in Pen Dirve.
How can i download explicitly that library on Pen Drive?
How can i install library from Pen Drive?

Please tell me

I gave you two ways of achieving this in my earlier post.
Asumuing the cybercafe doesn't have linux machines (which it probably doesn't) you can download the deb packages from the repositories directly:
[http://do.archive.ubuntu.com/ubuntu/pool/](http://do.archive.ubuntu.com/ubuntu/pool/)

dowload only the *.deb files of the package you're looking for; search for the packages [here]("http://packages.ubuntu.com/") beforehand to see if there's a candidate for the version you're using and to learn which dependencies may be needed.

---

### Post by rahul_shilps on 2009-07-16
Sorry,
In my previous post i said my file compiles well.
 
Actually it does not compile at all. It gives simple error like
 
"stdio.h file is not found"
 
Tell me now,
 
1) How to download library from a machine which not having Linux and take that in to Pen Drive?
2) And how to install it on Linux machine from pen drive?
 
Thank you.
 
- Rahul

---

### Post by rahul_shilps on 2009-07-17
> **rahul_shilps said:**
> Sorry,
In my previous post i said my file compiles well.
 
Actually it does not compile at all. It gives simple error like
 
"stdio.h file is not found"
 
Tell me now,
 
1) How to download library from a machine which not having Linux and take that in to Pen Drive?
2) And how to install it on Linux machine from pen drive?
 
Thank you.
 
- Rahul
 
 
Hello All,
 
Can you help me please..

---

### Post by rahul_shilps on 2009-07-17
Once agin, i will tell you what i want do
 
1st TASK
----------
I want to download all C Library from internet from the machine on which there is Windows OS and internet is available.
 
2nd TASK
-----------
And the downloaded 'C' Library i want ot install on a Ubuntu Machine.
 
How can i do this 2 tasks? Please tell me step by step.
 
Thank you.
-Rahul
(Change is the rule of universe)

---

### Post by lisati on 2009-07-17
> **rahul_shilps said:**
> Hello All,
 
Can you help me please..

Did you say something like ```
#include <stdio.h>
``` or did you put something like ```
#include stdio.h
```

---

### Post by Partyboi2 on 2009-07-17
> **rahul_shilps said:**
> Once agin, i will tell you what i want do
 
1st TASK
----------
I want to download all C Library from internet from the machine on which there is Windows OS and internet is available.
 
2nd TASK
-----------
And the downloaded 'C' Library i want ot install on a Ubuntu Machine.
 
How can i do this 2 tasks? Please tell me step by step.
 
Thank you.
-Rahul
(Change is the rule of universe)
Hi, if you don't have Internet for you ubuntu machine you can use a program called [[COLOR=Blue]Keyrx[/COLOR]]("http://keryxproject.org/") to get the packages you need and their dependencies from your windows machine.

---

