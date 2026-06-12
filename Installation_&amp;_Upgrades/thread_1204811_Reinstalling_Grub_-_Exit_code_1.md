---
title: "Reinstalling Grub - Exit code 1"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by Hubster on 2009-07-05
Hi,

I'm trying to reinstall Grub after installing dual boot Vista but all I get from the 'Rescue system' screen is fatal error exit code 1 when I put in hd0.

This hard drive has several partitions on and I would happily put on a fresh Ubuntu install over the linux home partition but when I go to 'Partition disks' on the set up screen it only sees the entire hardrive and not the Vista or other partitions I use to store data. Those partitions are still there, I can see them clearly in windows.

I managed to rescue ubuntu last night by resintalling Grub but since then have reinstalled windows again. I came to do a rescue this morning but it won't work this time.

Can anyone please help?

---

### Post by presence1960 on 2009-07-05
I don't know to what you are referring by 'rescue", but all you need to do is restore GRUB since windows overwrote GRUB when you reinstalled windows. Do this :

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
In #6 I would use setup (hd0) to install GRUB to MBR.
Remember that numbering for hard disk & partitions starts at 0. This your first hard disk is (hd0), the first partition on first hard disk is (hd0,1) the second partition is (hd0,1). Your second hard disk if you have one is (hd1). The first partition on the second hard disk is (hd1,0). The second partition on the second disk is (hd1.1), etc.

---

### Post by Hubster on 2009-07-05
Thanks for your help, but can you just help with step 2 please :) ?

How should I open the terminal? 

I'm using the 9.04 alternate iso to boot from. I think I understand the rest

---

### Post by enli on 2009-07-05
I havent used alternate iso but I am sure it should be running terminal/tty by default.

If you see a screen like windows command prompt you are already using the tty / terminal.

---

### Post by Hubster on 2009-07-05
Just a quick message to say thank you for your help, got it all working now.

Many thanks

---

### Post by presence1960 on 2009-07-05
glad you got it working, enjoy Ubuntu. BTW, I had to bowl in my $$ league this morning so I had to leave.

---

