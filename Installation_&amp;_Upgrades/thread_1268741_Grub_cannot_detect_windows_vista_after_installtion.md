---
title: "Grub cannot detect windows vista after installtion"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by knightnoir on 2009-09-17
Hi, guys, I'm a totally new user to ubuntu.
I just installed it last night on a machine (hp laptop) which used to have windows vista.
According to many installation guide, after the installation of grub, it suppose to detect any other operating system itself, but it didnt work out on my hp laptop.
I try to find grub/menu.lst and grub.conf in order to modify the list, however, they dont exist in my /boot/grub folder. By the way, i install my GRUB on the same partition as my linux.

I manually added a menu.lst under /boot/grub, however, i can not reinstall grub. When i type grub-install /dev/hd0, it tells me some *.mod can not be modified.

I found a way to boot my windows manually. When GRUB ask me to choose which option to use, currently, i have 4: linux, linux safe, memory test, and memory test****. I type "e" so i can actually modify the command of the boot command. I modified one of them manually to "root=/dev/(hd0,1)  chainloader+1". And then I press ctrl+c, I load my vista successfully, however, this will not be saved into GRUB menu. Which means i have to do it every time, when i want to load my windows.

What should I do to modify my GRUB menu now?

---

### Post by lindsay7 on 2009-09-17
Try this and post how you do,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by knightnoir on 2009-09-17
Thanks, _Lindsay_.
I will try this tonight. :P
And let you know how it works out.

Btw, what is step 3 for?

---

### Post by lindsay7 on 2009-09-17
> **knightnoir said:**
> Thanks, _Lindsay_.
I will try this tonight. :P
And let you know how it works out.

Btw, what is step 3 for?

I am going to assume that you have never used the terminal before since you are asking this question, so forgive me if I assume incorrectly.

Go to the top menu bar and click Application then click accessories, then click Terminal.

Then enter the following.... sudo grub ... you will be asked for your password. This is the password that you set up when you installed Ubuntu.  You will not see what you type in (this is for security reasons).  This command gets you into the grub directory and from the you can make the changes that you need.  Just enter the commands as shown in my post. It should be easy.

---

### Post by knightnoir on 2009-09-17
> **lindsay7 said:**
> I am going to assume that you have never used the terminal before since you are asking this question, so forgive me if I assume incorrectly.

Go to the top menu bar and click Application then click accessories, then click Terminal.

Then enter the following.... sudo grub ... you will be asked for your password. This is the password that you set up when you installed Ubuntu.  You will not see what you type in (this is for security reasons).  This command gets you into the grub directory and from the you can make the changes that you need.  Just enter the commands as shown in my post. It should be easy.

Your assumption is 100% correct.
Thank you for answering so patiently.

---

### Post by knightnoir on 2009-09-17
> **lindsay7 said:**
> Try this and post how you do,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Hi, I tried to boot up with ubuntu CD.
Opened a terminal, and type sudo grub.
It returns sudo: grub: command not found.

---

### Post by lindsay7 on 2009-09-17
Just type ....  sudo grub  ....  not   ....   sudo grub.    ......

In other words do not put the . at the end of the command.

---

### Post by knightnoir on 2009-09-17
> **lindsay7 said:**
> Just type ....  sudo grub  ....  not   ....   sudo grub.    ......

In other words do not put the . at the end of the command.

lol
that i know, i did "sudo grub".
but it returns that.

---

### Post by lindsay7 on 2009-09-17
Sorry, if sudo gurb. is typed in you will get the same results that you are getting.

You may want to download "Super Grub" from their web site and their documentation.  Run the program and see if that helps.

---

### Post by knightnoir on 2009-09-18
> **lindsay7 said:**
> Sorry, if sudo gurb. it typed in you will get the same results that you are getting.

You may want to download "Super Grub" from their web site and their documentation.  Run the program and see if that helps.

Hey, buddy, by reading through super grub website, i found a very useful command "sudo update-grub". And it finds out my windows loader. :guitar:

---

### Post by lindsay7 on 2009-09-18
Happy to hear that you solved this.  Good luck with your Ubuntu system.

---

