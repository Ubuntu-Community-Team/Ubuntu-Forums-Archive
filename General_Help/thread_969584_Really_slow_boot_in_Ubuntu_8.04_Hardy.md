---
title: "Really slow boot in Ubuntu 8.04 Hardy"
date: 2008-11-03
forum: General Help
---

### Post by bayernanhaenger on 2008-11-03
Hi all.  A few months ago, Ubuntu got really slow, and took a few minutes to boot up.  I've finally gotten around to getting Bootchart.  I have attached it.  175s.  

I'm kind of a beginner to Ubuntu still, so I have no idea what this means.

Help is greatly, greatly appreciated.

Thanks,
Andy

Edit:  My laptop is going on 3 years old, but still decently fast.  Windows boots faster (I know!).  I think it's 2GB of RAM.   The partition is either 22.5 GB or 50GB (out of 100gb).  System monitor says I have 2 processors.  It's a Core Duo HP laptop, nw8440, if that helps.

---

### Post by cariboo on 2008-11-03
Could you edit grub to remove the quiet spalsh from the kernel you are loading and note any messages that may lead to a way to solve your problem.

At the grub menu highlight the kernel you normally load and press **e** then arrow down to the line containing quiet splash nad press **e** again, remove the entries and hit enter. Press b to boot and note where the boot process stops.

Jim

---

### Post by unutbu on 2008-11-03
I do not know how to solve your problem, but I did notice that your udevd/udevadm process is what is taking up almost all your time during boot. If you would like to see what a more normal bootchart looks like, see [http://ubuntuforums.org/showpost.php?p=6091519&postcount=3](http://ubuntuforums.org/showpost.php?p=6091519&postcount=3).

If you can figure out what is causing udevadm to take so long, your problem will be solved.

I know very little about udev. I believe udevd is in charge of identifying your hardware and then adding entries to /dev so that other parts of your system can talk to the hardware. It reads and applies a series of rules in /etc/udev/rules.d.

So, a few months ago, did you install any new hardware? A network adapter, an external USB drive, a webcam or some such?

---

### Post by bwhite82 on 2008-11-03
See here, i just answered this question for someone else:
[http://ubuntuforums.org/showthread.php?t=969454](http://ubuntuforums.org/showthread.php?t=969454)

EDIT: Looking at your bootchart it is clear that **modprobe** is what is slowing you down the most. Pink means I/O wait. My bootchart shows modprobe being initialized a few times but only briefly.

---

### Post by bayernanhaenger on 2008-11-03
> **Soldierboy said:**
> See here, i just answered this question for someone else:
[http://ubuntuforums.org/showthread.php?t=969454](http://ubuntuforums.org/showthread.php?t=969454)

EDIT: Looking at your bootchart it is clear that **modprobe** is what is slowing you down the most. Pink means I/O wait. My bootchart shows modprobe being initialized a few times but only briefly.

Soldierboy,
Thanks much.  However, do you know how I could go about making modprobe not wait?  Or should I go about the hunt in Google?


Thank you also to the other two posters.

Thanks much!!

---

### Post by bwhite82 on 2008-11-03
Well modprobe is searching for hardware and loading the necessary drivers for it. I'm wondering if you uninstalled some unnecessary drivers if it would help.

Open Synaptic and search for 'xserver'. Get rid of any drivers that do not apply for your machine. Then reboot and see if it shaved anything off your bootchart.

You can also compile your own kernel with only the features that you need, if you're brave enough.

---

### Post by bwhite82 on 2008-11-03
Alright, you can also trim unneeded kernel modules. Run the command:

> lsmod

To find out what modules are loaded. Search the name for any you're unsure of here (that are loaded):

[http://howto.wikia.com/wiki/Main_Page](http://howto.wikia.com/wiki/Main_Page)

Then, blacklist any you don't want

> sudo gedit /etc/modprobe.d/blacklist

Then blacklist them by putting:

blacklist moduleNameHere

I just blacklisted 5 myself that I didn't need:

ipv6
ppdev
parport_pc
joydev
snd_seq_dummy

---

### Post by bayernanhaenger on 2008-11-04
Sweet.

Thanks much!

---

### Post by sysctl on 2008-11-12
I have the same problem, bootchart shows modprobe stalls for around 40 seconds. Here is dmesg output (note sharp jump in timestamp):

```

[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2404.174 MHz processor.
[   40.305779] Console: colour VGA+ 80x25
[   40.305782] console [tty0] enabled
[   40.305959] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   40.306157] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

```

---

### Post by jsjones on 2008-11-18
I'm having a similar problem since upgrading to 8.04.  It is taking >4mins to boot.  Did not have this issue with 7.10 and nothing changed; only the upgrade.  Below is the output from dmesg.

```
...
[   64.470779] Bluetooth: RFCOMM TTY layer initialized
[   64.470781] Bluetooth: RFCOMM ver 1.8
[   67.545089] eth0: no IPv6 routers present
[  241.607136] kjournald starting.  Commit interval 5 seconds
[  241.607140] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[  241.617349] EXT3 FS on sdc1, internal journal
[  241.617357] EXT3-fs: mounted filesystem with ordered data mode.
```

Is it a problem with the network interface?  Any suggestions?

Thanks, JJ

---

### Post by sysctl on 2009-02-14
Solved (at least for my case).

I disabled splash on boot to see what was the problem, and it was new hard drive causing the problem (Western Digital on a Asus P5W (DH) Deluxe motherboard).
```

...
SRST failed (errno=-16)
...

```

I switched "JMicron Controller Mode" mode from "Basic" to "AHCI" in BIOS settings.

---

