---
title: "vista downgrade questions"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by CorntoeGoblin on 2009-05-24
Alright so i have a laptop that originally came with vista. Being a linux lover myself and my hatred towards vista i quickly installed ubuntu. the partition are setup like this

sda1=ntfs windows
sda2=ext3 linux
sda3=swap

I recently starting getting very serious about music applications and the only reason windows is still on my computer was for two programs traktor and ableton live since i failed to get anything productive out of wine. what i want to find out is how to remove vista and install xp but still preserve the GRUB boot loader with the proper settings.  i dont care about migrating settings from the vista install as everything i do is in ubuntu.
Any help would be greatly appreciated as vista is currently bustin my balls with compatibility with all my soundgear and slowness.

Corntoe

---

### Post by CorntoeGoblin on 2009-05-24
bump!

could really use some help guys

---

### Post by presence1960 on 2009-05-24
You can delete the Vista partition with partition editor (gparted) from the Ubuntu live CD. Boot from the Ubuntu CD. Choose use Ubuntu with no change to your computer. When the desktop appears go System > Administration > Partition Editor. Delete the Vista partition. Then create a partition from the resulting space and format it as NTFS while still in partition editor. Exit the Live CD and boot from your XP install disk. Install XP to the newly created NTFS partition.

Now you are going to have to restore GRUB. There is no way around this, XP will overwrite GRUB. Pop in the Ubuntu Live CD and boot from it, choose use Ubuntu with no change to your computer, then when the desktop appears do this:

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

You should be good to go.

---

