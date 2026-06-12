---
title: "terminal problem"
date: 2008-07-24
forum: General Help
---

### Post by stoppage on 2008-07-24
Hi, could somebody please explain to me why I can only „cd“ in terminal to some but not all folders in my home directory. I need to get into „QuickStart“ folder in home directory using the live cd. Much obliged

---

### Post by mikewhatever on 2008-07-24
What happens when you try to cd to quickstart? Any errors? Check the permissions of that directory with <ls -l path-to-folder>.

---

### Post by stoppage on 2008-07-25
Strangely enough and out-of-the-blue, now I CAN cd to it.

Permissions... 
ubuntu@ubuntu:/media/disk/home/tony/QuickStart$ ls -l 
total 112 
-rwxrwxrwx 1 1000 1000 95468 2008-07-12 19:39 QuickStart 
-rw-r--r-- 1 1000 1000   258 2008-07-20 22:08 QuickStart.desktop 
-rw-r--r-- 1 1000 1000    52 2008-07-12 19:39 QuickStart.md5sum 
-rwxr-xr-x 1 1000 1000   947 2008-07-12 19:39 READ_ME 
-rwxr-xr-x 1 1000 1000  2759 2008-07-12 19:39 Version_Updates

But when I try to run it....
ubuntu@ubuntu:/media/disk/home/tony$ QuickStart 
bash: QuickStart: command not found 
Thanks for your time....any ideas please?

---

### Post by ajmorris on 2008-07-25
> **stoppage said:**
> Strangely enough and out-of-the-blue, now I CAN cd to it.

Permissions... 
ubuntu@ubuntu:/media/disk/home/tony/QuickStart$ ls -l 
total 112 
-rwxrwxrwx 1 1000 1000 95468 2008-07-12 19:39 QuickStart 
-rw-r--r-- 1 1000 1000   258 2008-07-20 22:08 QuickStart.desktop 
-rw-r--r-- 1 1000 1000    52 2008-07-12 19:39 QuickStart.md5sum 
-rwxr-xr-x 1 1000 1000   947 2008-07-12 19:39 READ_ME 
-rwxr-xr-x 1 1000 1000  2759 2008-07-12 19:39 Version_Updates

But when I try to run it....
ubuntu@ubuntu:/media/disk/home/tony$ QuickStart 
bash: QuickStart: command not found 
Thanks for your time....any ideas please?

cd into /media/disk/home/tony/QuickStart  and issue ./QuickStart

AJ

---

### Post by danwood76 on 2008-07-25
To run programs within a folder that arent isntalled completely to your system you need to give a complete path.

This path can be relative as in the example above.
**./** is this directory
**~/** is home directory
Or the path can be absolute
**/media/disk/home/tony/QuickStart/QuickStart**

---

### Post by stoppage on 2008-07-25
Something's wrong here...
ubuntu@ubuntu:/media/disk/home/tony/QuickStart$ QuickStart
bash: QuickStart: command not found
ubuntu@ubuntu:/media/disk/home/tony/QuickStart$ ./QuickStart
bash: ./QuickStart: Permission denied

---

