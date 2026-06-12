---
title: "How Do I Start Up Linux?"
date: 2006-02-14
forum: Installation &amp; Upgrades
---

### Post by lfmasieri on 2006-02-14
I'm new to linux, I installed the latest version of linux and now I turn on my computer and what appears to me is like a DOS window, there are just letter and command and i enter the login and passwords as a command to, this isnt the way i have see the screenshoot fro login. what's wrong? I need to fix this error to work on my new linux like if it werre widnows, i ned the normal login screen? PLEASE HELP ME! THANKS YOU!

---

### Post by aysiu on 2006-02-14
Did you download a .ISO?
Did you burn it as a disk image?
Did you set your BIOS to boot from CD before the hard drive?

---

### Post by rfruth on 2006-02-14
"startx" should start the GUI you want but install (not server install) should have included the GUI for you (i.e. shouldn't have to startx every time) but hey if terminal (command line) is working then 
```

To install KDE: sudo apt-get install kubuntu-desktop 

To install Gnome: sudo apt-get install ubuntu-desktop 
 
``` should get things going :)

---

### Post by lfmasieri on 2006-02-15
Could you please explain these to me? I dont understand what are you talking about. Starts? sudo apt-get install kubuntu-desktop ? what do i ned to do with this?

[QUOTE=rfruth]"startx" should start the GUI you want but install (not server install) should have included the GUI for you (i.e. shouldn't have to startx every time) but hey if terminal (command line) is working then 
```

To install KDE: sudo apt-get install kubuntu-desktop 

To install Gnome: sudo apt-get install ubuntu-desktop 
 
``` should get things going :)[/QUOTE]

---

### Post by hornett on 2006-02-15
lfmasieri, it sounds like GRUB didn't install properly for some reason. (GRUB is a small program called a bootloader, which lets you choose wether to boot Linux or other operating systems you have installed eg Windows)

Write down exactly what appears on screen, and post it here - I'm sure somebody will be able to help.

---

### Post by aysiu on 2006-02-15
Can you confirm, first of all, what exactly your screen looks like right now?

Is it basically a totally black screen with a little bit of white text that looks something like this: ```
lfmasieri@ubuntu~$
``` or is it more like a black screen with a little bit of white text that looks like this: ```
grub>
```

---

### Post by lfmasieri on 2006-02-15
It looks like CODE "lfmasieri@ubuntu~$ ", it ask me for my login and password and then it loks like CODE as you mented

[QUOTE=aysiu]Can you confirm, first of all, what exactly your screen looks like right now?

Is it basically a totally black screen with a little bit of white text that looks something like this: ```
lfmasieri@ubuntu~$
``` or is it more like a black screen with a little bit of white text that looks like this: ```
grub>
```[/QUOTE]

---

### Post by XDevHald on 2006-02-15
lfmasieri, what you need to do is type the following command: [B]sudo passwd root

[/B]Once it asks you to type the password, type a password that you will remember, then type it again, to confirm the password.

Once you have done so, type: **su** then hit "enter" and then type your password to login as root. Once you have done this step, type **startx** and the command will execute the GDM login for you to get to your desktop.

---

### Post by DarkED on 2006-02-15
Looks like its all taken care of, but I think what he was trying to say is:

"I updated my linux kernel and now I can't get to the desktop!"

Meaning he already has Ubuntu installed but couldn't get it to load KDE/Gnome/Etc...

---

### Post by aysiu on 2006-02-15
[QUOTE=lfmasieri]It looks like CODE "lfmasieri@ubuntu~$ ", it ask me for my login and password and then it loks like CODE as you mented[/QUOTE] Okay, when you're at that prompt, try typing this command: ```
startx
``` If that doesn't work, try this command ```
sudo /etc/init.d/gdm restart
``` If that doesn't work, try this command ```
sudo dpkg-reconfigure xserver-xorg
``` If that doesn't work, try these commands ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
startx
``` When you're asked for your password, it's your **user** password. Forget what people are telling you about enabling a root account.

---

