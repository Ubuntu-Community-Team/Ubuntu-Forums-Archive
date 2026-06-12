---
title: "aspire v5-171 linux ready?"
date: 2012-07-17
forum: Hardware
---

### Post by sacridex on 2012-07-17
Hello,

I am wondering if [this laptop]("http://us.acer.com/ac/en/US/content/model/NX.M3AAA.002") is linux ready.
Especially the Touchpad, Wifi. I doubt there are any problems with the CPU/GPU.

Anyone tested already?
thx

---

### Post by pelle.k on 2012-08-11
I'm kind of interested of buying this notebook myself. Did you eventually buy it, and if so, how does it run ubuntu 12.04?

---

### Post by ragefury32 on 2012-09-14
I just did - if you are talking about the [V5-171 6867 submodel]("http://us-store.acer.com/product/acerproduct.aspx?prodid=252"), it's Linux-ready, but with some caveats:

What works OOTB:
Video
Bluetooth
Gigabit Ethernet
2-in-one removable media reader
keyboard
trackpad
USB3
Most Fn function keys

What doesn't work:
Broadcom BCM943328 a/g/n wireless card (you'll need the Broadcom restricted STA driver for it)
Brightness adjustments (the Fn-key maps but the brightness stays the same)
Intel Quick Sync encode/decode 
Fn-function to re-enable the trackpad if you accidentally turn it off

Some extra notes: 
This machine actually has quite a bit of hidden talents for your Linux power user.  It can do VMX and DMA remapping (VT-d) out of the box, so no need to hack up the BIOS to enable them for KVM virtualization.  The RAM slots (there's 2) are readily accessible with only one screw, and the machine can run with 16GB of RAM maximum (2 sticks of 8GB DDR3-204 Pin).  The hard drive is also standard 9.5mm 2.5", so you can swap it for a faster model or go SSD altogether.  The BIOS does not do white-list enforcement so you can conceivably swap the MiniPCIe card out for something else as long as it can take 2 antennas (Intel 6250 WiMax, 6235N combo, Atheros WB222, etc).  If you are a DIY/hacker type, this is great value.    One warning, though.  That trackpad is sketchy.  Be prepared to buy a Bluetooth or wired mouse for prolonged use...or if you are in APAC, buy a Lenovo ThinkPad Edge E130 instead.   The new one has the same feature set as the V5-171 and a better keyboard/mouse to boot.

---

### Post by jusr on 2012-12-05
Thank you, ragefury32. I have bought this laptop after having read your message. I bought the V5-171-32364G50ASS submodel (with i3-2367M CPU). I installed Debian Wheezy on it.

What didn't work out of the box:
- brightness adjustment via Fn keys
- bluetooth (because of this bug in Debian: [http://bugs.debian.org/682971]("http://bugs.debian.org/682971"))
- touchpad

To solve the Fn keys issue, just edit /etc/default/grub to add "acpi_osi=Linux" to the boot command line, via the GRUB_CMDLINE_LINUX_DEFAULT variable:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux"

```
Then run "update-grub" as root.

To solve the bluetooth issue, just type those 2 commands as root:
```
modprobe btusb
echo "0489 e046" >> /sys/bus/usb/drivers/btusb/new_id

```
Note: 0489 and e046 are the product ID and the device ID of the bluetooth adapter. They may be different from those on your model, so run "lsusb" to find them out. You should see a line like "Bus 001 Device 003: ID 0489:e046 Foxconn / Hon Hai" which corresponds to your bluetooth adapter.

I don't know what I did to solve the touchpad issue. I guess adding the "acpi_osi=Linux" boot option helped, but I'm not sure. If you can't get your touchpad to work, try to enable/disable WIFI with the Fn keys. If it works, then you should read the documentation of the synaptics Xorg driver (man 4 synaptics), especially the "ClickPad support" section. The touchpad on this laptop is actually a clickpad, which doesn't support middle button emulation. What you can do to overcome this is to configure the synaptics driver to make a two-finger tap trigger the middle button. Here is my configuration file :

```
Section "InputClass"
        Identifier      "Touchpad"                      # required
        MatchIsTouchpad "yes"                           # required
        Driver          "synaptics"                     # required
        Option          "TapButton1"            "1"
        Option          "TapButton2"            "2"     # multitouch
        Option          "TapButton3"            "3"     # multitouch
        Option          "VertTwoFingerScroll"   "1"     # multitouch
        Option          "HorizTwoFingerScroll"  "1"     # multitouch
        Option          "VertEdgeScroll"        "1"
        Option          "CoastingSpeed"         "8"
        Option          "CornerCoasting"        "1"
        Option          "CircularScrolling"     "1"
        Option          "CircScrollTrigger"     "7"
        Option          "EdgeMotionUseAlways"   "1"
EndSection
```

You can put this into /etc/X11/xorg.conf.d/synaptics.conf (you may have to create the /etc/X11/xorg.conf.d/ directory first), then restart Xorg. You can also use the synclient command to configure Xorg on the fly:

```
synclient TapButton2=2 TapButton3=3 VertTwoFingerScroll=1

```

Now about the display. The colors are poorly calibrated by default (too much blue, because this is a LED display). What I did to solve this is to install xcalib, and use it with this ICC profile: [http://img1.focus-numerique.com/focus/profils-LCD/Acer%20Aspire-2920_832G32Mn.icc]("http://img1.focus-numerique.com/focus/profils-LCD/Acer%20Aspire-2920_832G32Mn.icc"). This profile is not made for this laptop, but I found out that it does a good job. Load it with this command (inside a xterm or any X11 terminal, while Xorg is running):
```
xcalib 'Acer Aspire-2920_832G32Mn.icc'
```

You can put this command line into your ~/.Xsession to have Xorg load it at boot time.

The HDMI output works fine, but I would advise you to turn on the laptop first, then plug the HDMI cable, otherwise it seems that the graphic card thinks that the HDMI output is your primary display. Try to plug the HDMI cable before launching Xorg if you have any problem. If the screen connected via HDMI doesn't have the same definition as the built-in display, or if you want to have 2 different displays anyway, then use xrandr to setup dual-head, as explained here: [http://intellinuxgraphics.org/dualhead.html]("http://intellinuxgraphics.org/dualhead.html")

What I do is this:
```
xrandr --output HDMI1 --right-of LVDS1
```
Then I restart my window manager (fvwm, not Xorg itself) so it can take the new parameters into account (otherwise it thinks that the screen connected via HDMI has the same definition as the built-in screen).

I did not test the card reader. All I know is that its driver puts an error message in the syslog: "sdhci-pci 0000:04:00.1: Invalid iomem size. You may experience problems.", but it may work.

I did not test the built-in webcam and microphone.

The WIFI seems to work fine (I installed the broadcom-sta-dkms debian package to make it work) but I only tested it during one hour or so.

Ethernet interface works fine. I can't think of anything else. Overall, Linux works great with this laptop, even though you may have to tweak it a little. One last thing, be advised that the hard drive is very thin, not all 2.5" drives will fit, if you want to replace it (I tried with an old SSD but it was too thick).

---

### Post by NuageBleu on 2012-12-11
Thank to you! After reading this thread information I bought this laptop. And it's working much better than I expected! 
(precisely Acer Aspire V5 171, i5 3317U, 11.6" HD", 4GB RAM, 500GB HDD)
(ref number: NX.M3AEZ.002, V5-171-53314G50ass)

Here are the extra information I can give, especially related to this thread:

1) This is **not** a standard 9.5[mm] HDD, but a **7.0[mm]** HDD, so this is **not** suitable for regular 2.5" SDD...
(This  was a bad surprise, as I'm on a budget and I wanted to reuse my SDD.  Actually the end of my story is good: All the Crucial SDD that I bought  can be unscrewed, remove a plastic frame, crewed back, to make a and  reduced to a 7[mm] SDD, even that it kills the warranty on the way)

2) Otherwise Kubuntu would install with almost everything working right out of the box!! (K/Ubuntu 12.04 LTS) 
I  was expecting to work a bit, but I could use it immediately. Only had  to switch to the old BIOS, easy (press F2 all the time at start-up to  access it)

3) I can also confirm that the official specifications  of memory 2x4[GB] is not accurate, as I could install 4[GB] + 8[GB] on  my laptop. It's indeed super simple to access it 

4) To remove  the HDD, you just have to pull it out carefully, it's not screwed, only  hold by plastic lines on the side. You have to pull surprisingly strong,  there is a place on the finger at the bottom side of the HDD.

5) My Wifi worked out of the box, but this is apparently an other hardware:
$ lspci
03:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)

6) Also the Fn function key to re-enable the track-pad is working for me OOTB.

More details:

What worked for me OOTB:
- Video
- Ethernet 100
- keyboard
- trackpad (with all tapping features)
- USB2
- All Fn function keys except brightness adjustments
- Wifi (tested a bit, 'rsynced' my data, a bit of ssh, 1 day I'm doing that)

Untested:
- Bluetooth
- 2-in-one removable media reader
- USB3

What doesn't work:
- Fn function key for brightness adjustments

Thank  again for the valuable info!
Now I'll try to fix and test it more. Also I know nothing about  MiniPCIe, now I want to know how I can play with that :) I'll also get a Bluetooth mouse soon, I'll report if I find anything interesting.

---

### Post by abecbert on 2012-12-20
hey all,

having some issues myself with the bluetooth for my v5-171, lsusb returned that mine was 0489:e04e.

tried to fix bluetooth with this

modprobe btusb
echo "0489 e04e" >> /sys/bus/usb/drivers/btusb/new_id

bluetooth still not working and now lsusb does not show my device id anymore :/

any help please?

---

### Post by arjuan on 2013-01-19
> **abecbert said:**
> hey all,

having some issues myself with the bluetooth for my v5-171, lsusb returned that mine was 0489:e04e.

tried to fix bluetooth with this

modprobe btusb
echo "0489 e04e" >> /sys/bus/usb/drivers/btusb/new_id

bluetooth still not working and now lsusb does not show my device id anymore :/

any help please?

I'm having the same problem. When i run the second command with sudo I get the following error:

bash: /sys/bus/usb/drivers/btusb/new_id: Permission denied

---

### Post by arjuan on 2013-01-20
> **arjuan said:**
> I'm having the same problem. When i run the second command with sudo I get the following error:

bash: /sys/bus/usb/drivers/btusb/new_id: Permission denied

Nevermind, I fixed this by enabling the super user account in Ubuntu:

First, set a password for root user as shown below.

$ sudo passwd root
[sudo] password for ubuntu:
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

Now with the new password you can login as super user with su command

$ su -
Password:
#

---

### Post by jusr on 2013-02-01
> **abecbert said:**
> bluetooth still not working and now lsusb does not show my device id anymore :/

any help please?
I think your bluetooth device is disabled. Try to enable it by pressing Fn+F3 (after the two commands you tried). You may have to press Fn+F3 two or three times (because it first enables/disables wifi). Then lsusb will hopefully show your bluetooth device.


> **arjuan said:**
> I'm having the same problem. When i run the second command with sudo I get the following error:

bash: /sys/bus/usb/drivers/btusb/new_id: Permission denied
This is because "sudo" only applies to "echo", and the output of echo is sent to /sys/bus/usb/drivers/btusb/new_id with no root privilege. If you want to use sudo, then you can do this:

```
sudo sh -c 'echo 0489 e04e >> /sys/bus/usb/drivers/btusb/new_id'
```You can get this done automatically at boot by creating a file named 10-bluetooth.rules in /etc/udev/rules.d

/etc/udev/rules.d/10-bluetooth.rules :
```
SUBSYSTEM=="usb", ATTRS{idVendor}=="0489", ATTRS{idProduct}=="e046", RUN+="/bin/sh -c 'echo 0489 e046 > /sys/bus/usb/drivers/btusb/new_id'"
```Don't forget to replace 0489 and e046 by the correct ids for your device. Then restart udev with this command:

```
/etc/init.d/udev restart
```

---

### Post by mbieni on 2013-02-12
I've had problems with the Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01).  My network keeps connecting and disconnecting every few minutes with Ubuntu 12.4.  Any suggestions?

---

### Post by Yellow Pasque on 2013-02-12
> **mbieni said:**
> I've had problems with the Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01).  My network keeps connecting and disconnecting every few minutes with Ubuntu 12.4.  Any suggestions?
[https://bugs.launchpad.net/linuxmint/+bug/1040943](https://bugs.launchpad.net/linuxmint/+bug/1040943)

---

### Post by jusr on 2013-02-16
For those who would like to buy this laptop, be advised that some models have a Broadcom BCM43228 wireless card, which works poorly under Linux. The driver provided by Broadcom ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) is buggy and you'll get frequent disconnections.

It seems that there is an open-source driver in recent Linux kernels (from v3.6, see [https://patchwork.kernel.org/patch/1228211/](https://patchwork.kernel.org/patch/1228211/) and [http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211)). I did not test it.

The Broadcom wireless card provides both WIFI and Bluetooth, so if you replace it, you'll lose your Bluetooth device. I replaced it with an Intel Centrino Advanced-N 6230 card, which also provides Bluetooth:
[http://www.intel.com/content/www/us/en/processors/centrino/centrino-advanced-n-6230-brief.html](http://www.intel.com/content/www/us/en/processors/centrino/centrino-advanced-n-6230-brief.html)

It seems to work very well, no disconnection so far (in 24 hours). Bluetooth also works well, just load the btusb module and it will be ready to work. As with the Broadcom card, you have to press Fn+F3 to turn on WIFI, Bluetooth, both or none.

---

### Post by mulluysavage on 2013-05-24
The SD slot doesn't seem to work. [Others say the same.]("http://ubuntuforums.org/showthread.php?t=1543009&page=33")

---

### Post by jusr on 2013-05-25
> **mulluysavage said:**
> The SD slot doesn't seem to work. [Others say the same.]("http://ubuntuforums.org/showthread.php?t=1543009&page=33")
It works for me (model: V5-171-32364G50ASS). I'm using Debian, so I'm not sure it would work with Ubuntu.

By the way, I discovered a problem with the Western Digital HDD used in this laptop. See this: [http://ubuntuforums.org/showthread.php?t=1578003](http://ubuntuforums.org/showthread.php?t=1578003)
This problem could be solved with [http://idle3-tools.sourceforge.net/](http://idle3-tools.sourceforge.net/) (use at your own risk, and check your Load Cycle Count first), but I didn't try.

Clearly, the hard drive is put into sleep mode very often, and each time it goes into sleep mode, you have to wait 2 or 3 seconds for the HDD to wake up, before the laptop becomes responsive again. It can even happen while you're playing a video, making the video freeze.

 I bought this laptop 6 months ago, and the Load Cycle Count of the HDD is 305647. I suppose this problem can lower the runtime of the laptop on battery, if the load/unload operation of the hard drive is power consuming.

---

### Post by mulluysavage on 2013-07-20
> 
To solve the bluetooth issue, just type those 2 commands as root:
```
modprobe btusb
echo "0489 e046" >> /sys/bus/usb/drivers/btusb/new_id

```
Note: 0489 and e046 are the product ID and the device ID of the bluetooth adapter. They may be different from those on your model, so run "lsusb" to find them out. You should see a line like "Bus 001 Device 003: ID 0489:e046 Foxconn / Hon Hai" which corresponds to your bluetooth adapter.


Working on bluetooth on my V5-171-9661. Stangely, System Profiler shows *no* USB devices. lsusb returns: 

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 064e:e330 Suyin Corp. 

Is it the Suyin thing?

---

### Post by jusr on 2013-07-31
> **mulluysavage said:**
> Is it the Suyin thing?
No. Your bluetooth device is probably disabled at the hardware level. Try to press Fn+F3, then try lsusb again. If you still don't see the bluetooth device, then press again Fn+F3 (because it cycles through wifi and bluetooth disabled, only wifi activated, only bluetooth activated, both activated, I don't remember in which order). Also, you can run "tail -f /var/log/syslog" in a root shell, to see what device appears to the kernel when you press Fn+F3.

---

### Post by mulluysavage on 2013-08-08
> **jusr said:**
> No. Your bluetooth device is probably disabled at the hardware level. Try to press Fn+F3, then try lsusb again. If you still don't see the bluetooth device, then press again Fn+F3 (because it cycles through wifi and bluetooth disabled, only wifi activated, only bluetooth activated, both activated, I don't remember in which order). Also, you can run "tail -f /var/log/syslog" in a root shell, to see what device appears to the kernel when you press Fn+F3.

Bluetooth issue SOLVED by pressing fn-f3 once. Bluetooth device is enabled:
Bus 001 Device 007: ID 0489:e04e Foxconn / Hon Hai

---

### Post by jusr on 2013-08-08
> **mulluysavage said:**
> Bluetooth issue SOLVED by pressing fn-f3 once.
Great. Thank you for reporting that it worked. If one day you want to use the wifi card and Linux can't find it, remember that it's probably the same issue.

---

### Post by mulluysavage on 2013-10-16
My SD card slot wasn't working at first. Then it was. Then sometimes it was and sometimes it wasn't.  Now it doesn't. Don't see it in Gparted, 


lspci:
04:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)

fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=B297-4A93  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda8 during installation
UUID=4978a582-d003-4365-b312-9a6f0c032bc6 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=e9f58f11-4966-41e1-9d20-6596ba76c7f1 none            swap    sw              0       0
#storage mount
UUID=19A8317B4736F421 /media/storage ntfs-3g user,rw 0 0

---

