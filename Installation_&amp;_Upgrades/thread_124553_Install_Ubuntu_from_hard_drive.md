---
title: "Install Ubuntu from hard drive?"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by Lemony Fresh on 2006-02-01
I have a notebook without a usb bootable cd; I do have a floppy drive.  There is no option in the bios to boot USB either.  I have tried serveral bootable usb cd floppies.  None have worked.  Is there any method to remove the notebook drive and copy the install files to the drive; then boot to a floppy and initiate the install?  I have the means to accomplish the hardware side.  I just need some help with the software side.  This is my first SERIOUS plunge into the Linux scene.  So please go easy on me.  Is there a way, IF I make a 4GB partition to store setup files, to boot to floppy mount the install partition and run setup?  I could do this with dos boxes all day.  Linux is another story for me.  

Thanks in advance

---

### Post by lha on 2006-02-02
[QUOTE=Lemony Fresh]I have a notebook without a usb bootable cd; I do have a floppy drive.  There is no option in the bios to boot USB either.  I have tried serveral bootable usb cd floppies.  None have worked.  Is there any method to remove the notebook drive and copy the install files to the drive; then boot to a floppy and initiate the install?  I have the means to accomplish the hardware side.  I just need some help with the software side.  This is my first SERIOUS plunge into the Linux scene.  So please go easy on me.  Is there a way, IF I make a 4GB partition to store setup files, to boot to floppy mount the install partition and run setup?  I could do this with dos boxes all day.  Linux is another story for me.  

Thanks in advance[/QUOTE]

If you have internet connection, take a look at [netinstall floppies.]("http://ubuntuforums.org/showthread.php?t=75372&highlight=install+floppies")

---

### Post by Lemony Fresh on 2006-02-02
[QUOTE=lha]If you have internet connection, take a look at [netinstall floppies.]("http://ubuntuforums.org/showthread.php?t=75372&highlight=install+floppies")[/QUOTE]

I get 'error 25: error reading disk' on the boot disk.  Does my hard drive need to be formatted for linux?  If so what is the best way to accomplish that.  I can connect the drive to another linux box here if needed.  Thanks for your help.

---

### Post by tmahmood on 2006-02-02
try using syslinux [http://syslinux.zytor.com/faq.php](http://syslinux.zytor.com/faq.php)

---

### Post by lha on 2006-02-02
[QUOTE=Lemony Fresh]I get 'error 25: error reading disk' on the boot disk.  Does my hard drive need to be formatted for linux?  If so what is the best way to accomplish that.  I can connect the drive to another linux box here if needed.  Thanks for your help.[/QUOTE]
Did you use rawwrite to write those disk images to floppies? If you did, try with another disk. Floppies are notorious for failing. You don't have to format your hd to use those floppies.

If you have older Windows (something like 9x/ME, maybe NT's work, too), take a look [here.]("http://ubuntuforums.org/showthread.php?p=647002#post647002") I got frustrated with a broken cd drive and a floppy drive and used an existing Windows98 to start Ubuntu installer.

---

### Post by Lemony Fresh on 2006-02-03
I am very happy to report that the DOS install worked!  I installed DOS in a 2GB partition and copied all of the ubuntu setup files as instructed.  Everything went fine even the web install.  I thank you all for the help.

---

### Post by Lemony Fresh on 2006-03-02
Give this a shot.  It worked for me.
[http://ubuntuforums.org/showthread.php?t=75372&highlight=install+floppies](http://ubuntuforums.org/showthread.php?t=75372&highlight=install+floppies)

---

