---
title: "Permissions /  bcm wlan issue"
date: 2010-03-02
forum: Hardware
---

### Post by Nolind on 2010-03-02
I'm new to Linux. I have installed Ubuntu 9.10 om my HP DV6000 lap top. My problem is the broadcom wlan won't instal;. Every method I've found for correcting the problem ends with a permission denied message. How do I give myself the permissions to change config files ie , to blacklist the generic b34 driver and sys file in etc/modprobe.d ?   I can change the file but it won't let me save it. The same applies in terminal.
 
I can get the wlan to work in Fedora but I'd much rather use Ubuntu.
 
I have the OS dual booting with Windows xp.
 
I'm slowly getting to grips with the terminal and file systems I just need the correct level of permission.
 
Thanks.

---

### Post by Ayuthia on 2010-03-02
> **Nolind said:**
> I'm new to Linux. I have installed Ubuntu 9.10 om my HP DV6000 lap top. My problem is the broadcom wlan won't instal;. Every method I've found for correcting the problem ends with a permission denied message. How do I give myself the permissions to change config files ie , to blacklist the generic b34 driver and sys file in etc/modprobe.d ?   I can change the file but it won't let me save it. The same applies in terminal.
 
I can get the wlan to work in Fedora but I'd much rather use Ubuntu.
 
I have the OS dual booting with Windows xp.
 
I'm slowly getting to grips with the terminal and file systems I just need the correct level of permission.
 
Thanks.

You should be able to edit the file by using gedit with sudo (gksu is the graphical version) privilege:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```

I hope that helps.

---

### Post by j2010 on 2010-03-02
Hi
I guess you try to edit the file configuration directly with a graphical editor. To let you edit in administrator mode just enter the command (in Alt-F2)
```
gksu gedit
```
or in terminal
```
sudo gedit
```

---

### Post by Nolind on 2010-03-02
Thanks for your help so far. I have managed to edit the config file but I still get an error message "not permitted" when I try to perform some functions in the terminal.  Even if I open the terminal via alt/f2.  I'm currently logging on in my profile do I have to login as admin in some way. i.e. switch users or re-boot?  I don't know how permissions work in Ubuntu.

---

### Post by Ayuthia on 2010-03-02
In Ubuntu you will need to use sudo (instead of having full root access the whole time) in order to gain admin status for certain commands.  This is a feature of Ubuntu so that you don't accidentally remove or change something.

If there is a certain command or folder that you are having problems with, please feel free to ask.

---

### Post by Nolind on 2010-03-03
Thanks everyone. I've sussed the sudo thing now. In the end I didn't need to.
I reinstalled 9.10 and the installed the broadcom driver package from the 10.04 alpha disc. (It wouldn't load the one on the 9.10 image file dowloaded from the site!).  All is well.

:popcorn:

---

