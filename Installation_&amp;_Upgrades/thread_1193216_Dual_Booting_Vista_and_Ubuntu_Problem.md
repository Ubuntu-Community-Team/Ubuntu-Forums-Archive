---
title: "Dual Booting Vista and Ubuntu Problem"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by kenlow on 2009-06-21
Ok this is my first time do a dual boot so please take it easy on me :)
Ok so i installed Ubuntu latest one downloaded about 3 hours ago and then installed vista i want the vista bootloader using neogrub to boot into ubuntu but i lost the menu.lst files to enter into the boot loader setting on neogrub

Can anyone with the latest version please do a 
sudo gedit /boot/grub/menu.lst and copy and paste her so i can boot into ubuntu please :)

Thank you

---

### Post by x22 on 2009-06-21
welcome to the forum

when dual booting with a Microsoft OS, the golden rule
is "install Microsoft OS first"

1. install vista
2. cut back the NTFS partition with "gparted"
3. install ubuntu

---

### Post by doughemi426 on 2009-06-21
OK, i've installed XP and Ubuntu in this order, but because of a problem with xp, y had to get format and reinstall XP. The choosing screen of SO doesn´t appear no more and starts automatically XP. What can I do to restore the grub boot?, cause it was in the main partition. Help please.
 
dr

---

### Post by merlinus on 2009-06-21
First of all, don't hijack someone else's thread.  Start your own.

And when you do, run from the live cd, open a terminal, and post results of:

```

sudo fdisk -l

```

---

### Post by TristanDee on 2009-06-21
> **x22 said:**
> 
when dual booting with a Microsoft OS, the golden rule
is "install Microsoft OS first"

1. install vista
2. cut back the NTFS partition with "gparted"
3. install ubuntu

I've also read about this "shrinking" of the Vista installation partition for installing Ubuntu. Can anyone please explain why to do this instead of installing Ubuntu/Linux on a separate partition like before!

---

### Post by merlinus on 2009-06-21
Most people either install, or buy a computer where it is already installed, on the entire hdd.  So it becomes necessary to defrag and use vista's disk management tool to shrink its partition and make space for linux.

---

### Post by TristanDee on 2009-06-21
> **merlinus said:**
> Most people either install, or buy a computer where it is already installed, on the entire hdd.  So it becomes necessary to defrag and use vista's disk management tool to shrink its partition and make space for linux.

But they say Ubuntu is being installed in the Vista installation partition, I guess. Can't it be installed in another partition of its own? Say, by deleting one partition under Vista and formatting it into ext3/ext4?

---

### Post by merlinus on 2009-06-21
Linux can be installed into any partition you wish, as long as there is available free space.  But if vista is taking up the entire hdd, then there is no room.

---

### Post by raymondh on 2009-06-21
> **TristanDee said:**
> But they say Ubuntu is being installed in the Vista installation partition, I guess. Can't it be installed in another partition of its own? Say, by deleting one partition under Vista and formatting it into ext3/ext4?

TristanDee ... I believe you are referring to a WUBI installation when you say "UBuntu is being installed in the Vista partition".  Wubi is another way to have ubuntu.  It is installed inside windows.  What Merlin was referring to is a pure dual-boot scenario when you have both OS' in their respective partition.  So yes, when you want it that way, you need to create space on the HD for Ubuntu.

To the original poster, Kenlow, do you still want a copy of the menu.lst or is your issue already solved?

Peace.

---

### Post by presence1960 on 2009-06-21
> **x22 said:**
> welcome to the forum

when dual booting with a Microsoft OS, the golden rule
is "install Microsoft OS first"

1. install vista
2. cut back the NTFS partition with "gparted"
3. install ubuntu

That rule was meant to be broken. You can install Ubuntu first and then Windows to another partition. Then all you need to do is restore GRUB. That is not too much work even for a noob! After installing windows there are only a few steps to restore GRUB:

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

Not very difficult at all!
Sometimes Ubuntu is installed as only OS, why delete Ubuntu to install Windows only to have to reinstall Ubuntu.

Or in my case I got rid of XP and installed Win 7 RC just to get some experience with it because a lot of noobs are installing it before/after Ubuntu. All that was needed was to restore the GRUB bootloader using the above steps. Now my system boots fine again into GRUB.

I say that "rule" should be downgraded to a myth. There is no one way to install a dual boot, either OS can be installed first.

P.S. We forgot the 2 most important things : defrag Windows at least once or twice if it is installed first, even after a new install as some of the worst fragmentation I have ever seen occurs after a new install. And back up your data! Don't chance it...besides you should be backing up regularly anyway!

---

### Post by presence1960 on 2009-06-21
> **doughemi426 said:**
> OK, i've installed XP and Ubuntu in this order, but because of a problem with xp, y had to get format and reinstall XP. The choosing screen of SO doesn´t appear no more and starts automatically XP. What can I do to restore the grub boot?, cause it was in the main partition. Help please.
 
dr

Merlin is right, but since you already hiacked this thread restore GRUB like this:

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

In #6 if windows & ubuntu are installed on the same hard disk use > setup (hd0)

---

