---
title: "Install GRUB on external HDD"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by stallvalds on 2009-07-25
Hello all,
Last night i installed Ubuntu 10 on my 350 gb external usb hdd. It works great, but for some reason GRUB installed on my main hdd and my computer would not boot unless my external was hooked up. I fixed my windows mbr, but now ubuntu is unbootable on my external. Is there a way to install grub onto my external? I didn't remember there being an option for that when I did the installation. By the way, I chose the ex4 file system if that matters.
Thanks in advance

---

### Post by merlinus on 2009-07-25
Boot from live cd, open a terminal and run these commands:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd1,0)
root (hd1,0) #use the numbers from the previous command
setup (hd1)
quit 
```Make sure your external hdd is plugged in.

If this works, then your machine will boot to windows unless the external is plugged in, in which case you will get the grub menu.

You also may have to edit /boot/grub/menu.lst in terms of the windows entry.

---

### Post by presence1960 on 2009-07-25
Plug in your external hard drive. Run in terminal ```
sudo fdisk -l
```
Note your external drive (sdb, sdc, sde for example) and your Ubuntu root (/) partition. 

With the external drive still plugged in do this:

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

In #6 use setup (hdx), where x is the number of your external hard drive. Remember in GRUB numbering for disks & partitions start at 0. Thus:
drive sda = (hd0), drive sdb = (hd1), drive sdc = (hd2).
Partition sda1 = (hd0,0), partition sda2 = (hd0,1), etc.
Partition sdb1 = (hd1,0), partition sdb2 = (hd1,1), etc.

This will put GRUB on MBR of your external hard drive. If it isn't plugged in when you boot windows bootloader will take over. Just make sure your external drive is set to boot before your internal hard disk in BIOS so when you have the external plugged in on boot GRUB will take over.

---

### Post by stallvalds on 2009-07-25
Ok, I forgot to mention that i am a Linux noob. I'm a master of windows, but Linux distros are new for me. Is there a way to do this through the GUI? If not, then I'm sure that I can do the above command line method.

---

### Post by presence1960 on 2009-07-25
> **stallvalds said:**
> Ok, I forgot to mention that i am a Linux noob. I'm a master of windows, but Linux distros are new for me. Is there a way to do this through the GUI? If not, then I'm sure that I can do the above command line method.

Must be done through CLI. No GUI. 
I remember when I started using Linux, I was so intimidated by terminal. Now I use it a lot. it is faster and better than GUI. But remember Rome wasn't built in a day! The sooner you get more comfortable with terminal the better off you will be in linux. If you need more help post back.

---

