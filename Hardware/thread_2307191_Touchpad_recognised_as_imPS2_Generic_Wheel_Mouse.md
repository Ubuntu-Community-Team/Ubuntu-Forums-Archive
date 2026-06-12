---
title: "Touchpad recognised as imPS/2 Generic Wheel Mouse"
date: 2015-12-22
forum: Hardware
---

### Post by m-vanhalen-c on 2015-12-22
Touchpad on my enigma VI laptop from pc specialist is not recognized as a touchpad.
It´s very inaccurate and it has several other problems, by the way scrolling works. 
At present i´ve tried to search every possible solution, but it seems like i´m the only one who can´t fix this issue.
My fear is that it could possibly be an hardware issue.

There are 2 lines from dmesg who scares me.

```

[    1.972011] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    1.972016] i8042: If AUX port is really absent please use the 'i8042.noaux' option
```

Any solution? Thank you!;)

---

### Post by Vladlenin5000 on 2015-12-22
Hi and welcome.

Those lines are unrelated.
What hardware are we talking about? The touchpad should appear with either lsusb or lspci...

---

### Post by m-vanhalen-c on 2015-12-23
Sorry, neither lsusb nor lspci are present in dmesg.

Actually i8042 could be related.
[https://lkml.org/lkml/2007/5/3/444](https://lkml.org/lkml/2007/5/3/444)
[http://ubuntuforums.org/showthread.php?t=2215889](http://ubuntuforums.org/showthread.php?t=2215889)

---

### Post by Vladlenin5000 on 2015-12-23
The commands I mentioned earlier are to be run as is in terminal, not to be "found" in dmesg...
They're intended to list devices in USB and PCI bus. As such, one or the other, should list the specific touchpad your notebook has. Any possible solution depends mostly, if not entirely, on this piece of information.

---

### Post by m-vanhalen-c on 2015-12-23
Thank you Vladlenin5000, this is what I get from terminal:

michele@michele-W86:~$ lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
01:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
michele@michele-W86:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 058f:3822 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Vladlenin5000 on 2015-12-23
Sorry, apparently neither reported the exact model.

According to [this document]("https://wiki.ubuntu.com/DebuggingTouchpadDetection"), here's what you should try:

```
cat /proc/bus/input/devices
```

This should list all input devices. Among them the touchpad should should be listed. Here's how it appears on mine:

```
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input10
U: Uniq=
H: Handlers=mouse1 event7 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=660800011000003
```

---

### Post by m-vanhalen-c on 2015-12-23
```
I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio2/input0
S: Sysfs=/devices/platform/i8042/serio2/input/input10
U: Uniq=
H: Handlers=mouse0 event10 
B: PROP=1
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103


```

---

### Post by Vladlenin5000 on 2015-12-23
The document I linked earlier points to kernel bug but the (other) bad news are we still don't now the exact piece of hardware your laptop has.
Perhaps in their own forum - Linux section: [https://www.pcspecialist.co.uk/forums/forumdisplay.php?32-Linux](https://www.pcspecialist.co.uk/forums/forumdisplay.php?32-Linux) - they might be able to assist.

Hopefully some other member will assist here as well.

---

### Post by m-vanhalen-c on 2015-12-23
I will try. Thanks for your precious time!

---

### Post by alexchiu11 on 2016-01-17
Hey did you ever find a solution for this? I've got the exact same problem, and I've just picked up the exact same laptop as you from PCS -  

The Touchpad works OK in windows , but i have not been able to enable anything like two finger scrolling or multitouch gestures.

In Ubuntu the i have not had any problems with accuracy, but I do find the touchpad doesnt respond immediately if you leave it idle for 4-5 seconds, which is kind of annoying. The same problem also exisit on Linux Mint. It's such a shame because I love mint and Ubuntu. I dont really want to resort to using Windows as my daily driver just becasuse of a fairly minor but annoying issue. Curious if you are experiencing the same problems.

---

