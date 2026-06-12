---
title: "how &quot;modprobe&quot; works?"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by shariefbe on 2008-12-17
Hello,
    i am new to linux...can anyone tell me how this "modprobe" works when booting the kernel....how it fetches the modules path?

---

### Post by cariboo on 2008-12-17
From man modprobe:
> modprobe intelligently adds or removes a module from the Linux  kernel:
       note  that  for  convenience, there is no difference between _ and - in
       module  names.   modprobe  looks  in  the  module  directory  /lib/mod-
       ules/`uname  -r`  for  all  the modules and other files, except for the
       optional  /etc/modprobe.conf  configuration  file  and  /etc/modprobe.d
       directory   (see   modprobe.conf(5)).    All  files  in  the  /etc/mod-
       probe.d/arch/ directory are ignored

If you are ever unsure about a command, or want to know more about it, man is your friend:

```
man modprobe
```

Jim

---

### Post by shariefbe on 2008-12-17
In that i found that "modprobe.conf" file...but in my /etc directory i didnt find any file name "modprobe.conf"...thats why i am very mush confussed....

---

### Post by shariefbe on 2008-12-17
yes i saw that....in that man page i found that

[B]except for the optional /etc/modprobe.conf configuration file and /etc/modprobe.d
directory (see modprobe.conf(5)).All files in the /etc/modprobe.d/arch/ directory are ignored.[/B]

expert for optional means?all the modules will be in "/lib/modules/uname -r"......then what this /etc/modprobe.d contains?...and i didint have any file called modprobe.conf in /etc directory

---

### Post by shariefbe on 2008-12-18
Now just i want to know the path from which the modules are loaded while the kernel boots...can anyone help me?

---

### Post by shariefbe on 2008-12-19
by using google i found that /etc/modprobe.d/aliases is the path to load the modules when kernel boots....but i saw the file /etc/modules i get confussed...
The o/p of that file tells that its the file used to load the modules when kernel boots...i dont know which is the correct one...can anyone help me...

---

### Post by Circus-Killer on 2008-12-19
just to help people answer you better, perhaps you could fill us in with what you are trying to accomplish? (beginner to intermediate users hardly ever, if ever, need to use modprobe).

have you got hardware that is not working? there can be many more causes (and usually is) than modules being the problem. usually if hardware is not working properly is generally due to a lack of support more than anything else.

---

### Post by shariefbe on 2008-12-19
No i know...only module is the reason for the hardware not to work...cause its working in the ordinary kernel with supports of all modules...just its not working in this kernel...Thats why...

     Can you tell the solution for the previous post...can anyone help me

---

### Post by markbuntu on 2008-12-19
Exactly what module are you having trouble with because as you have disovered the modules are scattered all over the place and disguised by aliases and symlinks. If you can give more specific information you can get more specific help.

---

### Post by shariefbe on 2008-12-19
Thanks for your reply...actually i disabled the entire USB support when i compile the kernel...after that i planned to do that module manually i tried to insert dynamically...and it works nice when i use insmod **"insmod"**.....but my USB port didnt work....so i decided to do with modprobe,so that all nessary module will install automatically....but when i use **"modprobe"** it tells that "**FATAL :module not found"**...so i used **"depmod -a"**....but i dont know the use of that command,one of my friend told me to use that...
after that i used **"modprobe"** now it works...and i saw that module in the **"lsmod"** too....but still my USB port is not working...

i used **"usbcore"** module to make USB to work...

---

### Post by shariefbe on 2008-12-20
Dont know what to do...kindly refer my post and reply me.....so confussed due to this.....

---

