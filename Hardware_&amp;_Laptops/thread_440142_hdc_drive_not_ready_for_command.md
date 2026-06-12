---
title: "hdc: drive not ready for command"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by red_Marvin on 2007-05-11
This error fortunately doesn't occur very often, but when it does it's a real pita:

When doing nothing special, the computer would just freeze for 5-15 seconds at a time and then work for 1-5 seconds, and if I'm able to open up a terminal for dmesg or switch to console mode,
I get a number of "hdc: drive not ready for command" messages, efen if I'm not using hdc at the time (the cdrom), and my hdd is a sata one so it's not mounted on hd-anything.

Hw:
Asus F3T
Amd athlon 64x2 1.6GHz
Most things on the motherboard are either branded Nidia MCP51 or Nvidia C51 according to lspci.

---

### Post by snipe on 2007-05-11
same problem for me
**[SIZE="4"]TEMPORARY SOLUTION[/SIZE]**
 **[SIZE="3"]You can try(at your own risk because it reset IDE device)[/SIZE]**
```
sudo hdparm -w /dev/hdc
```

and after to SET DMA because the reset unset it
```
sudo hdparm -d 1 /dev/hdc
```

After that i didn't get anymore errors but my drive wasn't detect by gnome( serpentine & brasero)

To perform a detection of your drive do (or invert i don't remember which one depends on the other)
```
sudo rmmod cdrom ide_cd
```   
```
sudo modprobe cdrom ide_cd
```

---

### Post by Eddie Hung on 2007-05-17
I am experiencing exactly the same problem.

There is a bug report here: [https://bugs.launchpad.net/bugs/75295](https://bugs.launchpad.net/bugs/75295)

Does this temporary solution described only stops the problem for occurring for a little while? Or does it cure the problem until a reboot?

Eddie

---

### Post by freerick on 2007-05-19
I have the same problem. I checked the bug report, but no one has posted a fix  yet; resetting the drive does NOT work. Has anyone found a solution to this problem yet? This is a pretty severe bug I would say, since it renders all your drives useless.

---

### Post by freerick on 2007-05-19
correction: resetting the drive doesn't solve the problem *right away*, I had to umount/mount the drive a few more times before it stopped hanging each time;

This bug only occurred on a fresh install of Ubuntu Feisty.
**[SOLUTION] ** I noted that the default installation does not come with the libdvdcss3 package (for legal reasons), which is required to read encrypted DVDs. After installing it per instructions at [http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux). After that, everything worked fine for all of my drives.

:-D
*watching Family Guy*

---

### Post by WI_Mike on 2007-08-08
Hello, 

I am a n00b so sorry if this doesn't make sense. But.. I have the same problem. When boot into Ubuntu 7.04 I get this message every second:

[553.188.000] hdc: drive not ready for command
[553.188.000] hdc: drive not ready for command
[553.188.000] hdc: drive not ready for command
[553.188.000] hdc: drive not ready for command

every second, this message flashes on my screen and the hard drive thrashes over and over. I dual boot with Windows XP and I have not problems in Windows. I have reinstalled Ubuntu 7.04 twice now and I keep getting the same message.  

I have tried the temporary solution and it does not help. Please help because this is preventing me from loading Ubuntu.  I can't even access my hard drive partition /dev/hda because this message floods the screen and I can't do anything.

Help, please?!


:confused:

---

