---
title: "[SOLVED] No touch pad in Ubuntu 8.04"
date: 2008-05-26
forum: Hardware
---

### Post by jonwestin on 2008-05-26
Hi. Im having trouble getting my touch pad to work on my Znote 6024W with Ubuntu.. Ive had a look at a couple of forums and tried out the solution of adding the touch pad to xorg.conf, but it still wont work and I get an error message when trying to start GSynaptics (same as in [http://ubuntuforums.org/showthread.php?t=526459):](http://ubuntuforums.org/showthread.php?t=526459):) 

"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

also i tried this

```
jon@flaptop:~$ cat /var/log/Xorg.0.log | grep "ynaptics"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
(II) LoadModule: "synaptics"
(II) Reloading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Synaptics touchpad driver version 0.14.6 (1406)
touchpad no synaptics event device found (checked 18 nodes)
Query no Synaptics: 6003C8
(EE) touchpad no synaptics touchpad detected and no repeater device
(EE) touchpad Unable to query/initialize Synaptics hardware.
(II) UnloadModule: "synaptics"

```

Any suggestions?

---

### Post by bobnutfield on 2008-05-26
Hello,

Please post the results of:

> dmesg | grep Synaptics

---

### Post by jonwestin on 2008-05-26
> **bobnutfield said:**
> Hello,

Please post the results of:

Hi. Zero zip nada. Is that bad? :) And what does it mean?

---

### Post by bobnutfield on 2008-05-26
Well, it initially looks like your installation did not recognized the touchpad.  Look at:

> dmesg | grep mouse

and see how the mouse is recognized.  Does the cursor work by running your finder across it?

Bob

---

### Post by jonwestin on 2008-05-26
> **bobnutfield said:**
> Well, it initially looks like your installation did not recognized the touchpad.  Look at:



and see how the mouse is recognized.  Does the cursor work by running your finder across it?

Bob

```
jon@flaptop:~$ dmesg | grep mouse
[  121.338775] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[  121.367822] mice: PS/2 mouse device common for all mice
jon@flaptop:~$ 

```

My usb mouse works fine but the touch pad wont react at all.

---

### Post by bobnutfield on 2008-05-26
OK, I know these are a lot of commands to run, but we have to see if the touchpad is recognized at all.

Post the output of:

> lspci

What you are looking for is any reference to the touchpad or synaptics.  The driver is loaded, but the hardware has not been found.

Bob

---

### Post by jonwestin on 2008-05-26
> **bobnutfield said:**
> OK, I know these are a lot of commands to run, but we have to see if the touchpad is recognized at all.

Post the output of:



What you are looking for is any reference to the touchpad or synaptics.  The driver is loaded, but the hardware has not been found.

Bob

```
jon@flaptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
jon@flaptop:~$ 

```

Ah any help is welcome mate! Hopefully Ill learn something.. Doesnt seem like there is any..?

---

### Post by bobnutfield on 2008-05-26
Actually, your mouse may not show up in lspci, it was just to see what kind of device it is.  OK, still need to look for the touchpad in devices.  Type:

> cat /proc/bus/input/devices

This will list all of the recognized input devices on the system.

Bob

---

### Post by jonwestin on 2008-05-26
> **bobnutfield said:**
> Actually, your mouse may not show up in lspci, it was just to see what kind of device it is.  OK, still need to look for the touchpad in devices.  Type:



This will list all of the recognized input devices on the system.

Bob

Aight, here goes:

```
jon@flaptop:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=09da Product=000a Version=0110
N: Name="A4Tech PS/2+USB Mouse"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb4/4-1/4-1:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=17
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=303
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=event4 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=40001
B: SND=6

```

---

### Post by bobnutfield on 2008-05-26
OK, looks like the only mouse recognized is the USB you have plugged in.  Did you have the USB mouse plugged it when you installed?  I ask because I cannot understand why the laptop mouse is not picked up in dmesg.  I will do a little reseach and get back to you.

Bob

---

### Post by jonwestin on 2008-05-26
> **bobnutfield said:**
> OK, looks like the only mouse recognized is the USB you have plugged in.  Did you have the USB mouse plugged it when you installed?  I ask because I cannot understand why the laptop mouse is not picked up in dmesg.  I will do a little reseach and get back to you.

Bob

Yes, I was using my USB mouse when installing. Ubuntu somehow got a bit slow recently so Im trying a reinstall anyways. But please, if you find something out let me know. Thanks man!

---

### Post by bobnutfield on 2008-05-26
When you reinstall, try installing without the USB mouse connecting to Hardy the chance to pick up the touchpad during the installation.  I know the driver is installed, but also check and see if you hae libsynaptics0 installed.  It should not be needed to make the hardware work, it is mainly a library for applications that want to use the touchpad.  But it would not hurt to install it.  Before doing that, try uninstalling and reinstalling the Synaptics driver (latest version available in the repos).

I have checked the specs on that laptop and the touchpad is just a standard Synaptics, so it should have been automatically picked up.  I recently had an issue with Fedora 9 not allowing tap-to-click but the touchpad was already recognized and I could move the cursor, just no tapping.  Reinstalling the latest drivers fixed it.  But, if I understand correctly your touchpad is not functioning at all, not even cursor movement.

If installing the drivers and rebooting (without the USB moust connected), it may in fact require a re-installtion.

Bob

---

### Post by Arthur Archnix on 2008-05-26
Have you checked to see if you're touchpad has a physical switch to disable it? If it's physically disabled it might not be picked up by the operating system.

---

### Post by jonwestin on 2008-05-27
> **Arthur Archnix said:**
> Have you checked to see if you're touchpad has a physical switch to disable it? If it's physically disabled it might not be picked up by the operating system.

Hey. Thanks a lot for the help both of you. I tried installing the synaptics driver in my Windows and it didnt work either so I reckon the touch pad is actually broker. Cant find anything about a switch.. :(

---

### Post by Arthur Archnix on 2008-05-27
Bummer. Hopefully that thing is still on warranty. :)

---

### Post by jonwestin on 2008-05-30
> **jonwestin said:**
> Hey. Thanks a lot for the help both of you. I tried installing the synaptics driver in my Windows and it didnt work either so I reckon the touch pad is actually broker. Cant find anything about a switch.. :(

This is solved now. I did reinstall Ubuntu, but it still wasnt working. Then all of a sudden it did. Dunno why, but even the activating/deactivating Fn-button works so its all good :)

---

