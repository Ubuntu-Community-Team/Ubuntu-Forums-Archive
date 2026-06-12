---
title: "Non system Disk error"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by 2 Fingers on 2009-03-16
Hi, new to the world of ubuntu. Windows xp is corrupt & will not boot, i' over the constant virus problems and i've disscovered ubuntu, woohoo. Trouble is when booting from usb i get non system disk error. Can someone help please

---

### Post by PenguinsFan on 2009-03-16
Welcome to the world of Ubuntu! I think you'll like it here :)

When exactly do you receive the message? Is it during the Ubuntu boot sequence? Do you ever see the splash screen with the Ubuntu logo and the options below it?

---

### Post by 2 Fingers on 2009-03-16
Thanks for the reply, it gets to verifying DMI pool data then the message appears

---

### Post by 2 Fingers on 2009-03-16
I dont see a splash screen, in the bios i have selectef usb-hdd 1st in boot sequence if i choose ls120 or  or usb-fdd it will boot to windows which will ask me for a product key wich is incorrect (corrupt) and the message says that windows is not activated

---

### Post by Mark Phelps on 2009-03-17
OK, couple of things ...

The XP messages you're seeing having nothing whatsoever to do with "corruption"; instead, they mean that your copy of XP is no longer activated (or, in the case of bootleg installs, the crack/hack is no longer working).  The simple solution is to go online and activate it -- which means providing a legitimate product key.  Whether or not you have that, or want to do that, is entirely up to you ... and not a topic for this forum.  Just wanted to let you know that, in all likelihood, your XP installation, and the files, are still intact -- not corrupt.

As to your questions, what are you really trying to do:
1) Run Ubuntu from a USB stick?
2) Install Ubuntu from a USB stick over your XP installation?
3) Install ubuntu from a USB stick in dual-boot mode with your XP installation?

And, how did you come by an installable version of Ubuntu on USB stick?

---

### Post by 2 Fingers on 2009-03-18
I was checking  ebay for a new copy of windows,this is were i first saw ubuntu for sale on a usb stick for $2. being a total cheapskate i did some research and thought i could just download ubuntu and do it myself. Studied unix a while back as part of an engineering diploma and i am excited to see how far its come as back then we only used command line prompts. Tryed burning the CD but vista says that i dont have enough space on my 700mb blank disk although the iso file is smaller. Not really a computer wiz, but i would like to give it a go. The ebay ad said yiu could boot ubuntu from the usb stick,yhats what i,m trying to do.  Cheers

---

### Post by 2 Fingers on 2009-03-18
Just re -read the post. I am trying to install ubuntu over windows from the usb stick 2gb and wipe the computer clean and just run ubuntu

---

### Post by furcino on 2009-03-18
I would not run ubuntu from USB. It's too big... If you want an ubuntu-like system for your usb **try PUD Linux**. It is ubuntu-based but it has like 280MB. I run it from my 4GB USB without any problems whatsoever. Even added my own 16 color boot-screen ;) PUD lets you connect to the net in a user-friendly manner (unlike Knoppix or similar USB dist.) and is fairly small. It also gives you the option of casper-rw (because it still has its ubuntu powers).

You can download it from: 
[http://www.pendrivelinux.com/pud-linux-flash-drive-install-windows/]("http://www.pendrivelinux.com/pud-linux-flash-drive-install-windows/")

Just make sure to use the instal.bat from the second zip file and not the one included and try to follow these: [http://groups.google.com/group/pud-linux/browse_thread/thread/9ae4fbd4169d99b3]("http://groups.google.com/group/pud-linux/browse_thread/thread/9ae4fbd4169d99b3")

If you really want to stick to running the ubuntu you've installed **try searching for syslinux.exe**, because it sounds like you have to make your USB drive bootable. If it still does not work, then try checking your **syslinux.cfg** file, which should be in the root folder and try to fix it somehow.

---

