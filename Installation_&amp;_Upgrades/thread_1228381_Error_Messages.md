---
title: "Error Messages"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by cquigley on 2009-07-31
Hello Everyone-
 
I am new to linux and having problems when installing programs. When trying to install wvdial I get a error that says;
 
**[COLOR=red]Er[/COLOR][COLOR=red]ror: Dependency is not satisfiable: libuniconf4.4[/COLOR]**
 

[COLOR=black]I am running Ubuntu Jaunty 9.04 on a acer aspire 5100. I have a amd turion 64 processor. However it says I need use the i360.[/COLOR]
 
This error also happens with all the others apps I try to install excelt "libuniconf4.4" is replaced with something else.
 
Please any help on this would be great.
 
Thanks,
cquigley

---

### Post by Partyboi2 on 2009-07-31
Hi, the easiest way to install programs is to open up Synaptic (System>Admin>Synaptic) and search for the programs you want to install and install them. This will take care of all the dependecies for the packages you are trying to install.

---

### Post by cquigley on 2009-07-31
Thx-
 
However, the main issue I am having right now is that computer with jaunty on it is not connected to the interent.
 
I a pantech um175 from verizon wireless, and from what I seen online I need to apps to configure it.
 
I am on a windows computers connected to the interenet trying to figure all this out. Does anyone know how to find the packages a app needs from a website or something.
 
Please let me know,
 
thanks fo your help
 
 cquigley

---

### Post by Partyboi2 on 2009-07-31
You can use [[COLOR=Blue]Keyrx[/COLOR]]("http://keryxproject.org/") to install packages on your offline machine or you will have to go [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/") and look for the missing dependencies eg. [COLOR=Black]libuniconf4.4[/COLOR] and  download and install them for installing wvdial.

---

### Post by cquigley on 2009-08-01
thx, kervyx is a good software.
 
However it seems that it only get updates for the OS only. can't to get it to search for a particular software.
 
Anyone know where Ican find out how to use it for a specific software.
 
cquigley

---

### Post by Bucky Ball on 2009-08-01
Tried this?

[http://support.real-time.com/linux/index.html](http://support.real-time.com/linux/index.html)

---

### Post by GeorgeVita on 2009-08-01
Hi **cquigley**,
to restore wvdial+dependencies on 9.04 without internet connection, read:
[http://ubuntuforums.org/showthread.php?p=7245790#post7245790](http://ubuntuforums.org/showthread.php?p=7245790#post7245790)
Regards,
George

---

### Post by cquigley on 2009-08-01
Thanks GoergeVita, however it will not install anything because each time I doubled clicked on the file to install it, it said in was missing dependencies and could not install, then it closed.

This is where I'm getting fustrated, can't seem to install anything, everytime it says it needs dependencies. then I when I go online and d/l the dependencies on my vista machine, then go to install them, they need dependencies. 

feels like a vicious circle right now. Can anyone hep out?

thx,
  cquigley

---

### Post by cquigley on 2009-08-01
Got it installed, your link worked georgevita. I had had some broken packages in the kernel that wasn't allowing to do anything.

Got that fixed and following your instructions and it worked perfectly, thanks so much every1.

cquigley

---

