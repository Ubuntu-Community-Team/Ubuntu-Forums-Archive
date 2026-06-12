---
title: "No volume control after upgrade to 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Rat2000 on 2009-11-06
Since I've upgraded from 9.04 to 9.10 I no longer can change the volume.
For starters I can no longer add a volume control panel as there is none available.

Second, when I try to change the volume using my keyboards volume control knob, it doesn't work. Curiously, while running Miro, using the keyboard knob seems to make the Miro controls "flicker" while I turn the knob.

Under System > Preferences, if I run "Sound", I only get a "Waiting for sound system to respond". This happens no matter if no other media apps are running after a fresh reboot. And of course, it waits forever.

I've tried installing some Pulse Audio Volume Control package but I only get a "Connection failed: Connection refused" message which I guess is the core of the problem.

Thanks for any help!

---

### Post by khelben1979 on 2009-11-06
Try [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer")gui.

```
sudo apt-get install alsamixergui
```
to install it. You might have better luck with controlling your volume bars with this one.

---

### Post by Rat2000 on 2009-11-06
Thanks, it works via that GUI but I would like to be able to use my keyboard's volume knob.

---

### Post by khelben1979 on 2009-11-07
> **Rat2000 said:**
> Thanks, it works via that GUI but I would like to be able to use my keyboard's volume knob.

To have this working your Linux kernel must support your computer hardware. Hopefully it does and this means that you need to install some package which relates to your laptop hardware.

What is the model of your laptop?

```
lspci
```
would be useful in this case.

---

### Post by Rat2000 on 2009-11-07
It's a desktop computer (+2 year old hardware) and I can hear sound fine. It's the volume control that seems to be missing since the update.

Here is my lspci output:

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by khelben1979 on 2009-11-07
I can't see what type of keyboard you have from that list:
```
lsusb
```
will give an output of your usb devices as well.

If it's Logitech for example your should either be looking for some keyboard package which relates to logitech using the [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager").

You can also take a look at your /etc/X11/xorg.conf which will show what keyboard driver you're currently using.

---

### Post by Rat2000 on 2009-11-07
I have a Dell keyboard with the fancy shortcut buttons and volume knob.

Here is the lsusb output:

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

All my shortcut keys seem to work and as I stated in my initial post, the volume knob seems to be recognized by the OS as when I run Miro I get some sort of flicker when I turn it. What worries me is that there is no volume control applet as there should have been and the Sound administration is not working.

---

### Post by khelben1979 on 2009-11-07
I found [this thread]("http://ubuntuforums.org/showthread.php?t=1284219"), might help you in this.

---

### Post by Rat2000 on 2009-11-14
OK so I've found the solution in yet another thread:

> **TomtheWombat said:**
> I had a file in my home directory called '/home/username/.pulse-cookie' that was owned by root and write protected.

I did 'sudo rm ~/.pulse-cookie' and everything started working instantly.

Now my volume control works :p.

---

### Post by depaulmatthew on 2009-11-20
> **Rat2000 said:**
> OK so I've found the solution in yet another thread:



Now my volume control works :p.
i have the same problem.. but this doesnt fix my problem.

---

### Post by depaulmatthew on 2009-11-20
> **Rat2000 said:**
> OK so I've found the solution in yet another thread:



Now my volume control works :p.
I reinstalled pulse audio.. and it worked for me.

---

