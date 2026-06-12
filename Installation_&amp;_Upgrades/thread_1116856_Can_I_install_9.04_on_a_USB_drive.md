---
title: "Can I install 9.04 on a USB drive?"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2009-04-05
Hi, I would like to give a try to 9.04 before it's release but I don't want to go trough the whole formatting process, I'm soo short of time right now, lucky me my vacations starts on the 23th. 
I would like to know if I can install the beta offered at ubuntulinux.org into my pendrive and so test it against my laptop, I know that the model I own it's getting popular, but not everyone does the same things with their laptops. I have a Lenovo Ideapad Y530.

Also, would like to know from personal experiences if it would change something on my pendrive, do I need to format it? Should I have one exclusively for this? Any help would be appreciated. So far I'm extremely happy with Ubuntu.

---

### Post by arashiko28 on 2009-04-05
BUMP?
Anyone?

---

### Post by Pasdar on 2009-04-05
Use [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) to do that.

---

### Post by arashiko28 on 2009-04-05
Thanks but only answered half of my questions, I know it comes since 8.10 able to install to USB, I should have been more specific, I meant from the live CD and if it will make any permanent changes to my flash drive.

---

### Post by Pasdar on 2009-04-05
Whether the USB drive will be affected? The USB drive you want to put Ubuntu on? It will be completely formatted as far as I am aware.

---

### Post by GirionSoft on 2009-04-05
You can do a normal install to a flash drive from the live cd without any major issues. Your flash drive must be 4GB or larger and you should NOT install a boot loader. The way to do this is to run the installer on the live cd and change the partition to be installed on to the flash drive. Use the manual partition editor. Do not create a swap, create a single partition. You can use fat32 if you want it to be read in windows or you can use ext3.  The follow the rest of the install prompts. Make sure that when you are given the option to install a boot loader you select no boot loader. If you install grub or lilo, you will need the flash drive to boot your normal install which i am guessing is windows. I have not created a persistent 9.04 flash drive yet but I have done this with both 8.04 and 8.10.

---

### Post by GirionSoft on 2009-04-05
Sorry, I only answered half of your question. The short answer to the permanent changes is no. Any of the changes you would make can be undone with a quick reformat. The install will make your flash drive bootable and a low level format in windows wont undo this but this can easily be switched off by formating with almost any of the several of the linux partition editors or a third party windows app.

---

### Post by arashiko28 on 2009-04-07
> **GirionSoft said:**
> You can do a normal install to a flash drive from the live cd without any major issues. Your flash drive must be 4GB or larger and you should NOT install a boot loader. The way to do this is to run the installer on the live cd and change the partition to be installed on to the flash drive. Use the manual partition editor. Do not create a swap, create a single partition. You can use fat32 if you want it to be read in windows or you can use ext3.  The follow the rest of the install prompts. Make sure that when you are given the option to install a boot loader you select no boot loader. If you install grub or lilo, you will need the flash drive to boot your normal install which i am guessing is windows. I have not created a persistent 9.04 flash drive yet but I have done this with both 8.04 and 8.10.

No, I don't Use windows anymore and due to a happy mistake I deleted Vi$ta without any chance of recovering since it doesn't came on CD anymore. I'm a full time Linux user from quite a long time now :p

---

