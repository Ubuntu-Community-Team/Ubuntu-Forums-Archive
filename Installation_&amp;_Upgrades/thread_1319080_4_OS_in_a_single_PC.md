---
title: "4 OS in a single PC?"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Refreshment on 2009-11-08
Hello Ubuntu experts.

First let me start by saying that i am a very inexperienced user, so request a little bit of patience :)

I have the following set up:
-160 GB Hard Disk with Windows XP
-1 TB Hard Disk with Ubuntu 9.04 64 bit and Windows 7 32 bit
-The bootable drive is the 160 GB one.

Now, need to add Windows 7 64 bit. I was thinking of installing it in the 1 TB Hard Disk. My concern is if its gonna mess the Grub. Any suggestions on how to achieve this or where to install the new OS?

Thanks for your time.

---

### Post by presence1960 on 2009-11-08
If you put it on the 1 TB disk GRUB will be overwritten, but restoring GRUB is a 30 second process using the Ubuntu Live CD:

```
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
```

---

### Post by Refreshment on 2009-11-08
Hi presence:
I did a rehearsal up to step 5 using, Ubuntu normally and it returned this value:
 
(hd0,5)

So to recap i will:
-Install Windows 7 64 bit in the 1 TB HD with Ubuntu and Windows 7 32 bit. Total 3 OS`s.
-Some new partitions will be created for Windows 7 64 bit.
-Grub's gonna get messed.
-Boot with live CD.
-Use terminal and follow your guide.
-Use "setup (hd0,5)" to install Grub
-Boot the PC.

Did i got it right?

---

### Post by presence1960 on 2009-11-08
> **Refreshment said:**
> Hi presence:
I did a rehearsal up to step 5 using, Ubuntu normally and it returned this value:
 
(hd0,5)

So to recap i will:
-Install Windows 7 64 bit in the 1 TB HD with Ubuntu and Windows 7 32 bit. Total 3 OS`s.
-Some new partitions will be created for Windows 7 64 bit.
-Grub's gonna get messed.
-Boot with live CD.
-Use terminal and follow your guide.
-Use "setup (hd0,5)" to install Grub
-Boot the PC.

Did i got it right?

Use:
root (hd0,5)- then next run 
setup (hd0)

the root command will setup GRUB files in your Ubuntu partition
the setup command will put GRUB files on MBR so when you boot GRUB will take over.
You may have to edit menu.lst to add the new windows.

---

### Post by Refreshment on 2009-11-08
> You may have to edit menu.lst to add the new windows.
Could you please explain this step?

---

### Post by presence1960 on 2009-11-08
> **Refreshment said:**
> Could you please explain this step?

why don't you restore GRUB first after installing the new windows then we can discuss this, which would be the next step.

---

