---
title: "Ubuntu 8.04 Question ?"
date: 2008-08-16
forum: General Help
---

### Post by Fattlum on 2008-08-16
[b] hi , i have downloaded ubuntu 8.04 , and burned it into a cd..

but : actually im running in Windows XP , so i was asking ? after i install Ubuntu 8.04 , will it run as the only system or i can have WINDOWS xp , AND UBUNTU 8.04 AS BOTH OS IN MY PC ?

REPLY PLEASE.. ? [/b]

---

### Post by ajmorris on 2008-08-16
> **Fattlum said:**
> [B] hi , i have downloaded ubuntu 8.04 , and burned it into a cd..

but : actually im running in Windows XP , so i was asking ? after i install Ubuntu 8.04 , will it run as the only system or i can have WINDOWS xp , AND UBUNTU 8.04 AS BOTH OS IN MY PC ?

REPLY PLEASE.. ? [/B]

 Hi there,
yes it is possible to run both Ubuntu and windows. This is called a dual boot, when you install ubuntu, you can resize your windows partition in the partition editor, to make room for ubuntu, and then install ubuntu in that space. You can then choose between windows or ubuntu in a boot loader (grub by default in ubuntu) or you could use LILO, or add ubuntu to the windows boot loader. Grub however is the easiest to use :)
If you need help partitioning your HardDisk for your dual boot, just ask.

AJ

---

### Post by Tom--d on 2008-08-16
Yes, Thats called dual booting.

Why not try Wubi. **Its on the cd.** What it does its Install ubuntu inside Windows. [http://wubi-installer.org/](http://wubi-installer.org/) [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

No need to partition. etc etc.
Run the wubi.exe (i think thats it) off the cd while Windows is running. 
You can uninstall Ubuntu anytime with inside Windows under Add/remove programs.

Read the link. It tells you more :)

Or...
Infact. 
Just run the cd. It will run off the CD. Its called a LiveCD. It will not touch your Hard drive. It runs of the RAM. Try it ;)

also, how did you burn your cd? Through Windows Explorer? If yes, it probably wouln't boot.
look here and it will tell you how to do it properly.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) :)

---

### Post by Fattlum on 2008-08-16
well the prob. is that i have 247 MB OF RAM So , when i try 2 open the wubi.exe it says : You Need Atleast 256 MB Of RAM To run the INSTALLER..:(

---

### Post by Tom--d on 2008-08-16
> **Fattlum said:**
> well the prob. is that i have 247 MB OF RAM So , when i try 2 open the wubi.exe it says : You Need Atleast 256 MB Of RAM To run the INSTALLER..:(

Dang!
Only a few MB out.

I guess the only option is to dual boot.

---

