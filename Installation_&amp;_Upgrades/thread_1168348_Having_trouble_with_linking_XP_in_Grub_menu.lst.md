---
title: "Having trouble with linking XP in Grub menu.lst"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by intransit on 2009-05-24
Gday everyone

Having a bit of trouble sorting out my menu.lst.
I set up as follows, and installed XP first:

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19551955

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8312    66766108+   7  HPFS/NTFS
/dev/sda2            8313        8443     1052257+  82  Linux swap / Solaris
/dev/sda3            8444        9733    10361925   83  Linux



So basically when I installed ubuntu 9.04 it added entries for 3 ubuntu's (memtest86 etc)
So i've added in the following:

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

So I'm fairly sure i'm addressing it properly, but now what happens is, if i let it timeout and boot automatically, i get a windows blue screen saying something like "UNMOUNTABLE_BOOT_VOLUME"
Strange.
So the even weirder thing is, if I hit esc and select XP from the list, it boots into it fine.

Any ideas on how I could fix this?

I'm guessing the first hting i'll try is to just not make it the automatic selection so i have to select it from the list, but hopefully there's a more graceful solution.

Thanks heaps for any help

---

### Post by intransit on 2009-05-24
Random.

So I removed savedefault and now I can leave it to timeout to XP with no bluescreen.
How strange?

---

### Post by presence1960 on 2009-05-24
try editing your windows entry in menu.lst to this:

```
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1
```

For additional GUI startup options install startupmanager from the repositories either thru Synaptic package manager or in terminal run > sudo apt-get install startupmanager

Edit: startupmanager is a GUI program for setting startup options. Not GUI startup options. sorry my bad!

---

### Post by intransit on 2009-05-24
hmmm
when I installed ubuntu i already had xp on the first partition
so the options i got were wipe entire hd and install only ubuntu
or advanced manual partitions
so i used that
installed ubuntu on sda3 mount as "/"

should I have set mount on XP to something?

i got the blue screen again with my changed settings so i'll try yours and see how I go. The weird thing is as soon as it does boot into windows, sometimes it takes a couple of goes i get blue screen then chose to "start windows normally" when i get in everythings fine.... so its weird why i only get this error occasionally

---

### Post by presence1960 on 2009-05-24
> **intransit said:**
> hmmm
when I installed ubuntu i already had xp on the first partition
so the options i got were wipe entire hd and install only ubuntu
or advanced manual partitions
so i used that
installed ubuntu on sda3 mount as "/"

should I have set mount on XP to something?

i got the blue screen again with my changed settings so i'll try yours and see how I go. The weird thing is as soon as it does boot into windows, sometimes it takes a couple of goes i get blue screen then chose to "start windows normally" when i get in everythings fine.... so its weird why i only get this error occasionally

On install you cant set windows with a mountpoint. If you are getting a menu that includes "start windows normally" there may be a problem with your windows install such as an unclean shutdown. You may want to run a scan of your disk in windows.

---

### Post by intransit on 2009-05-24
yes, still getting blue screen with your settings too.
as i mention earlier though,appears only happens when i dont hit esc and chose manually
strange!

---

### Post by intransit on 2009-05-24
il try format and reinstall windows on sda1

will i lose grub after reinstalling windows though?

---

### Post by presence1960 on 2009-05-24
> **intransit said:**
> il try format and reinstall windows on sda1

will i lose grub after reinstalling windows though?

you will have to restore GRUB. In case you don't know how:

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

in #6 I would install GRUB to MBR

---

### Post by zubin71 on 2009-05-24
yes; you will lose the grub

if you are reinstalling windows, you can install the grub later on as follows :-

1. put in a live cd
2. get a terminal
3. run the following one by one

$ sudo grub

grub> find /boot/grub/stage1

grub> setup(hd0)

the above commands should do it! :-)

---

### Post by intransit on 2009-05-24
whats MBR?

---

### Post by zubin71 on 2009-05-24
MBR starts for Master Boot Record. Its the first 512 bytes of your hard disk. 446 bytes for the GRUB you see, and 64 bytes for the partition table.
Now, if its "asking-doubts" you give us the info, and present your problem in a clear manner.

---

