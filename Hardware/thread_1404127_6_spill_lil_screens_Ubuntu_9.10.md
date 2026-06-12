---
title: "6 spill lil screens Ubuntu 9.10"
date: 2010-02-11
forum: Hardware
---

### Post by hoho32 on 2010-02-11
hey master Guys.
i install a new ubuntu 9.10
and then go to update hardware drivers ,after that i restart my mashine then 
i found my screen divide and spilt into 6 lil screens :!: ..if you could guys help me in that issue i'll be thankfull
may i know what i can do cuz im really new in this system

---

### Post by shriramrs31 on 2010-02-11
May be this helps: 

Try booting into recovery mode and choose xfix.

I think all it does is, "dpkg-reconfigure xserver-xorg". So, you can try doing the same via a console.

FYI: you can access many consoles using CTRL+ALT+F1 till F6 and F7 is the GUI screen. If this works for you, you can try out the above command from there instead of recovery mode.

---

### Post by hoho32 on 2010-02-11
i hit Ctrl+Alt+f4 
then i type xfix
and thats what happen 
"" no command 'xfix' found 
then 
dpkg-reconfigure xserver-xorg

then he send me back

"" usr/spin/dpkg-reconfigure must be run as root

---

### Post by bandiora on 2010-02-11
Hello guys

I installed Ubuntu 9.10 and hve the following trouble. aftrer restarting the system the screen is not on, while booting it is on until the screen of logon in the system, so I can non see it and so I cannot log in in my Linux. My machine is Acer Aspire 5000. Plese helt. Everything ok, but without screen I cannot work!!!

---

### Post by shriramrs31 on 2010-02-11
> **hoho32 said:**
> 

"" usr/spin/dpkg-reconfigure must be run as root

Okay, all the system configuration commands require root access in ubuntu. you have to run these commands with the prefix "sudo". It means do as superuser.

so do "sudo dpkg-reconfigure xserver-xorg", you will be asked for password (which u gave during installation).

---

### Post by shriramrs31 on 2010-02-11
> **hoho32 said:**
>  
"" no command 'xfix' found 


xfix is available only in recovery mode.

have a look at this howto to boot into recovery mode ;-)

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by hoho32 on 2010-02-11
i have added you on skype ..can we talk ?

---

### Post by shriramrs31 on 2010-02-11
Unfortunately I cannot be online in skype right now. But let me give you a detailed explanation.

In the grub boot menu (when you start your system), you have the option to choose recovery mode -> your kernel version (Recovery Mode).

Choose this option and boot into it. Choose and go into the root with networking option and you will be dropped into a console.

Type in there, the command I pointed out in my last reply.

This should restore you to the previous graphical mode hopefully.

---

### Post by shriramrs31 on 2010-02-11
can u also tell me what graphics card you have ?

---

### Post by wojox on 2010-02-11
Edit /etc/X11/xorg.conf

Under Device add:

Option "ModeValidation" "NoTotalSizeCheck"

Save and reboot.

---

### Post by hoho32 on 2010-02-11
its ubuntu, linux 2.6.31-19-generic (recovery mode) 
but actully i dont need this recovery mode 
cuz i installed this graphic card new ((Nvidia g 100m ))

in graphics hard drive update its nvidia185 the program name x-server nvidia

i enter the recover mode and network .the same issu

" Error : no write permission/octet-stream

---

