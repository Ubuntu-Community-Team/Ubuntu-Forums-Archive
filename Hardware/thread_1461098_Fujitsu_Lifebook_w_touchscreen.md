---
title: "Fujitsu Lifebook w/ touchscreen"
date: 2010-04-23
forum: Hardware
---

### Post by stealintv on 2010-04-23
Hello all! I recently acquired a Fujitsu Lifebook b6210 that has a touchscreen. I installed Ubuntu Netbook Remix and cannot get the touchscreen to work. Can anyone guide me in the right direction? I am not afraid to read, just need some help getting started.

btw.. this system had winxp prior to the current OS and the touchscreen worked then.

I have installed the evtouch drivers through synaptic and went to use the calibration tool, but to my dismay, it reported that no devices were found that it supports. 

From what I have read, there are other drivers, but none seem to work. Also, from my google-ing, I have not had much luck locating a guide on this subject, thus I have turned to a forum.

Thanks in advance for any help that can be given.

Cheers!

---

### Post by Ayuthia on 2010-04-23
I am not for sure about the touchscreen hardware in your Lifebook.  Have you checked lsusb or lspci to see if it shows up there?

---

### Post by stealintv on 2010-04-23
Thanks for the speedy reply. That's what I was looking for was some command line input I guess. I will check that after dinner and post back if nothing stands out to me.

---

### Post by Ayuthia on 2010-04-23
From a quick search, it looks like you have the correct driver.  Did you check /var/log/Xorg.0.log to see if the touchscreen was found?  It could be that either that the kernel module for your touchscreen is not loaded or else evtouch had an issue with loading it.

---

### Post by stealintv on 2010-04-23
ok i'm back

output from the following as requested.

lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
08:03.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 20)
08:03.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 20)
```

cat /var/log/Xorg.0.log :
 output in attachment - too long to post

Thanks!

---

### Post by Ayuthia on 2010-04-23
I am not seeing any information for the touchscreen anywhere.  My guess is that there is no kernel module that is getting attached to your touchscreen.  If there was, most likely evdev would have tried to attach itself to it.

Is there anything in dmesg?
```
dmesg|grep -i touch
```

If you still have Windows on it, you might go into the Device Drivers and see if you can find the make and model of the touchscreen.

---

### Post by stealintv on 2010-04-24
output of dmesg | grep -i touch:

```
[   16.166984] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x202000
[   16.226592] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
```

Not looking good?

Also, I found an older guide to evtouch and it says to edit the /etc/X11/xorg.conf however I do not have that file. Is Netbook Remix configured different?

---

### Post by stealintv on 2010-04-25
found in dmesg:

```
[   14.648305] input: Fujitsu FUJ02B1 as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/FUJ02B1:00/input/input6
[   14.648374] ACPI: Fujitsu FUJ02B1 [FJEX] (on)
[   14.648986] input: Fujitsu FUJ02E3 as /devices/LNXSYSTM:00/device:00/FUJ02E3:00/input/input7
[   14.649025] ACPI: Fujitsu FUJ02E3 [FEXT] (on)
[   14.649527] fujitsu-laptop: BTNI: [0xf0001]
[   14.649546] fujitsu-laptop: driver 0.5.0 successfully loaded.

```

Any ideas what this might be?

---

### Post by Ayuthia on 2010-04-25
I am not for sure what that is either.

Have you checked in Windows to see the make and model of the touchscreen?

Another thing to check out is lshal.  Can you attach the results of:
```
lshal > lshal.txt
```
It might help us see what that previous message is.

As for the xorg.conf, 9.10 changed things a little bit.  It is configuring the devices through .fdi files instead of xorg.conf.  However, xorg.conf can still be used.  So the system will start off without one and if you need it, you can create it.

---

### Post by stealintv on 2010-04-26
Ayuthia, Thank you so much for helping me with this. Sorry it took so long to respond. 

Unfortunately, when I obtained this laptop, I removed windows completely so I cannot check on what you asked for.

I have been doing some research on this and found ndiswrapper. Is that program only for wireless network cards or does it work for any windows drivers to get unsupported devices working in a *nix environment? I thought it might be a good idea to download the windows driver for this touhscreen and see if a text document was present, but couldn't find a make/manufacturer. 

Anyway, sorry I am getting off topic. Here is the output of the command you requested:

```
lshal > lshal.log && tar -czf lshal.log.gz lshal.log
```
SEE ATTACHMENT.

Thanks again for all of your help.

---

### Post by Ayuthia on 2010-04-26
I am not for sure if ndiswrapper would work for this or not.  I have never tried it on anything else but wireless cards.

However, I did find an interesting [mail archive link]("http://www.mail-archive.com/linux-input@atrey.karlin.mff.cuni.cz/msg00254.html").  It looks like there might be some commands that need to be done to get the device started.  There is a section where they state:
> 
Please try the patch below. You will need to load 8250_pnp,
serport and fujitsu_ts modules, then do

        inputattach -fjt /dev/ttyS0

So it looks like you need to do:
```

sudo modprobe 8250_pnp
sudo modprobe serport
sudo modprobe fujitsu_ts

```
then do:
```

inputattach -fjt /dev/ttyS0

```
I am not for sure if the last command needs to be with sudo or not but my guess is that it does.  You might try it once without it to see if it works or not.  The worst case is that it will give you a Permission Denied message.

Hopefully that will get the touchscreen loaded.  If nothing happens yet, you might try the following:
```
sudo service gdm restart
```
and that will restart your session (so close out everything but the Terminal window).  After that, hopefully evdev will find it and try to use it.

---

### Post by stealintv on 2010-04-26
Thanks for the speedy response. Ok, I tried what you said after reading that link. I received two errors:

```
FATAL: Module 8250_pnp not found.
&
inputattach: invalid mode
```

I'm guessing that inputattach didn't work because the first command failed...?

Cheers.

---

### Post by Ayuthia on 2010-04-26
That is my guess also.

I have found another [link]("http://ubuntuforums.org/showthread.php?t=1370750") for a Fujitsu of another model, but it looks like it also needs to configure the serial port to make it work.  You might try those commands.

---

### Post by toastmiami2 on 2011-03-02
Having trouble getting the touchscreen on my Fujitsu B6210 Lifebook running 10.04 configured as well.

Did you ever figure it out?

My Xorg.0.log shows that it attempts to configure it as a Wacom tablet, and then...

(EE) Couldn't init device "Serial Wacom Tablet"

......all help appreciated....

---

### Post by Favux on 2011-03-02
Hi toastmiami2,

Welcome to Ubuntu forums!

If you have a Wacom/Fujitsu digitizer in your model then a lot of folks have found restarting X gets the digitizer initialized.

I think the model on this thread might be a new Wacom touchscreen, not digitizer.  The touchscreens use the ISDV4 serial W8001 driver and a kernel module that provides a sythetic device input event like a usb device.  The inputattach links that ttyS.  So I don't think they're talking about your model.  It's getting confusing.

If restarting X doesn't work we might want to try upgrading your xf86-input-wacom (the X driver).  Some more Fujitsu support was added since the Maverick default xf86-input-wacom-0.10.8.

---

### Post by stealintv on 2011-05-01
bump!

A year later and I just dug this little laptop out again. I will be trying this again and will post if I come across a solution.

Any of you recent posters find anything out?

---

