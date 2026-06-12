---
title: "Wacom 22HD in ubuntu 12.04"
date: 2012-10-15
forum: Hardware
---

### Post by jdadams on 2012-10-15
I have a wacom cintiq 22HD tablet, and have a problem under
ubuntu 12.04, on a Thinkpad T400s.

I had it working, thought not well, in ubuntu 10.04. Both the 
display and usb input worked, but I couldn't get a calibration
tool to work. So I upgraded to 12.04. Now I cannot it to recognize the usb device.

I installed wacom.ko from the kernel, or also from input-wacom-0.14.0, with the same result. 

The device does show up in lsusb. (I don't have the tablet handy now, 
so I can't show the precise output. But there were two
lines with wacom in them.) However it does not show up
in /proc/bus/input/devices (as I believe it should), and 
the wacom symlink does not appear in /dev/input.

Various error messages appear, this seems to be the most relevant,
from /var/log/syslog:

Oct 15 08:02:59 atlas kernel: [ 5037.284343] usb 1-1: Product: Cintiq 22HD HUB                                                            
Oct 15 08:02:59 atlas kernel: [ 5037.284345] usb 1-1: Manufacturer: WACOM
Oct 15 08:02:59 atlas kernel: [ 5037.285316] hub 1-1:1.0: USB hub found
Oct 15 08:02:59 atlas kernel: [ 5037.286338] hub 1-1:1.0: 2 ports detected
Oct 15 08:03:00 atlas kernel: [ 5037.556335] usb 1-1.1: new full-speed USB device number 12 using ehci_hcd
Oct 15 08:03:00 atlas kernel: [ 5037.650602] usb 1-1.1: New USB device found, idVendor=056a, idProduct=00fa
Oct 15 08:03:00 atlas kernel: [ 5037.650606] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Oct 15 08:03:00 atlas kernel: [ 5037.650609] usb 1-1.1: Product: Cintiq 22HD Tablet
Oct 15 08:03:00 atlas kernel: [ 5037.650611] usb 1-1.1: Manufacturer: Tablet
Oct 15 08:03:00 atlas mtp-probe: checking bus 1, device 12: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1.1"
Oct 15 08:03:00 atlas mtp-probe: bus: 1, device: 12 was not an MTP device

That looks promising at first, but then seems to fail, I don't know whether the mtp device stuff is relevant.

According to 
[http://osdir.com/ml/ubuntu-bugs/2012-09/msg08665.html](http://osdir.com/ml/ubuntu-bugs/2012-09/msg08665.html)

This bug was fixed in the package linux - 3.5.0-14.15

so I upgraded the kernel:

Here is uname -r:
3.5.4-030504-generic

Still no luck.

My understanding is that this is a very low level problem:
the very first thing I should be able to do is detect the 
usb port, before any other system stuff should come in to 
play. 

I've tried many many things. Any help would be appreciated.
If I can provide any more information let me know. Thanks.

---

### Post by Favux on 2012-10-15
Hi jdadams,

Welcome to Ubuntu forums!


As you realize support for the Cintiq 22HD was only recently added.
Cintiq 22HD kernel support added to input-wacom on 7-19-12:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/input-wacom;a=commit;h=aae23339f1c348230dc4a2d82d0500244bfab0cd](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/input-wacom;a=commit;h=aae23339f1c348230dc4a2d82d0500244bfab0cd)  In 0.14.0+.

Cintiq 22HD X support added to xf86-input-wacom on 7-13-12:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=1a8db01e896514d06f7a69c647aac05832d54ea7](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=1a8db01e896514d06f7a69c647aac05832d54ea7)  In 0.17.0.

I don't know which kernel version has the wacom.ko that supports your model.  Maybe 3.6 because the bug report (actually a feature request) you link to seems to show the Ubuntu kernel team backporting support for it to kernel 3.5.

Of course that's what input-wacom is for.  To backport model support in newer kernels to older kernels so you end up with a wacom.ko that supports your new tablet.  You need to clone the input-wacom git repository to get the commit I linked to above.  It's not yet in a release.  Regardless of how you get the wacom.ko if it is working you should see your tablet in **lsusb** and in **xinput list**.  And if you have a xf86-input-wacom that supports your tablet you should see in xinput list (in the case of a Cintiq HD) at least 3 lines with the parent device appended by at least stylus, eraser, and pad.  Or **xsetwacom list** would be populated.

So first check for kernel support i.e. a working wacom.ko.

Then check your version of xf86-input-wacom:
```
xsetwacom -V
```
You need at least 0.17.0 to get the commit I link to above.

By the way Ron from Debian stopped updating the wacom.rules about 2 years ago now.  So there won't be a symlink for your Cintiq.  I'm not sure if Ubuntu has added new rules since his last one.  The Linux Wacom Project doesn't make new rules because they don't see the reason to use xorg.conf anymore and beside that's a Distro job.  The "current" rules table is here:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Fixed_device_files_with_udev)  I did add a few more rules past where Ron left them and supplied instructions on making a new one.

---

### Post by jdadams on 2012-10-15
Favux,

Thanks for the speedy reply.

I upgraded xf86-input-wacom to version 0.17.0.

jda@atlas:~$ xsetwacom -V
0.17.0

>I don't know which kernel version has the wacom.ko that supports >your model. Maybe 3.6 ...

>Of course that's what input-wacom is for. ... You need to clone the input-wacom git repository >...Regardless of how you get the >wacom.ko if it is working you should see your tablet in >lsusb and in xinput list. 

This is the problem. I have tried almost every wacom.ko I can think of with 
the same result. It shows up in lsusb but nowhere else, not in /proc/bus/input/devices,
nor xinput list, nor anywhere else.

jda@atlas:/var/log$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 056a:00f9 Wacom Co., Ltd 
Bus 001 Device 005: ID 17ef:480d Lenovo Integrated Webcam [R5U877]
Bus 004 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 004 Device 003: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 006: ID 056a:00fa Wacom Co., Ltd 


How can I tell if the wacom.ko is the right one? I tried the one from the kernel 3.5.4, 
as well as from the latest linuxwacom as you suggested.

I haven't tried wacom.ko from any 3.6 kernel. As far as I can tell there is no 
package for this, so I can't install it using apt-get, but I have to compile it
myself. Is there a way to compile only a few things, including wacom?

Also, when I'm testing, can I compile wacom, then rmmod wacom, modprobe wacom
(in the directory where wacom.ko is) to install it? Then test? Or do I have 
to put in in /lib/.../modules/..., and/or reboot?

---

### Post by Favux on 2012-10-15
Check the date on the wacom.ko's.  Are they both in /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko?  You only want one there.  Check the date of the input-wacom-0.14.0 one you compiled and use that one in lib/modules.

Also check on whether the wacom.ko is autoloading.  Do you see it in list modules?
```
lsmod
or
lsmod | grep wacom
```

---

### Post by Favux on 2012-10-15
Let me explain a little more.  What follows is a bit of voodoo.
> Also, when I'm testing, can I compile wacom, then rmmod wacom, modprobe wacom (in the directory where wacom.ko is) to install it? Then test? Or do I have to put in in /lib/.../modules/..., and/or reboot? 
Yes you should be able to modprobe and so on, however I never do.  This dates back to when the usb kernel driver wacom.ko was introduced.  Installing it in lib/modules was a much surer way of getting it to work.  Apparently due to some teething problems.  Additionally you often had to restart several times for it to "kick in".  And on a fair number of systems it still wouldn't auto-load.  Adding the rebuild all module dependencies, **sudo depmod -a**, cut down on that but didn't eliminate it.  In that case you need to add 'wacom' to the module list in the /etc/modules file.  I don't know why this is so.

---

### Post by jdadams on 2012-10-16
I think I'm making progress.

I had a long detour because I got the "black screen" bug in kernel 3.5.0. I see you commented on that elsewhere. In any event I finally solved that. Another bug was that 
I had to put in a symlink from /lib/modules/3.5.0-030500-generic/build to 
/usr/src/linux-headers-3.5.0-030500-generic
But that's ok now.

I compiled wacom.ko in the latest version of input-wacom, version 0.14.0 I believe, that I got from git as you said. Here is the output of git log:

commit 126ec2dd608dcb251d351754694ea282a0860423
Author: Ping Cheng <pingc@wacom.com>
Date:   Tue Oct 2 15:43:43 2012 -0700

    Add support to ISDV4 0x100 and 0x101

    Both are 10 finger-MT devices, where 0x101 is penabled.

    Signed-off-by: Ping Cheng <pinglinux@gmail.com>

[snip]

commit 4a01ca9f67874ff422455adbf710bea9799f762d
Author: Ping Cheng <pinglinux@gmail.com>
Date:   Thu Jul 19 15:04:07 2012 -0700

    input-wacom-0.14.0

which looks good. wacom.ko compiles, but then:

modprobe wacom
FATAL: Error inserting wacom (/lib/modules/3.5.0-030500-generic/kernel/drivers/input/tablet/wacom.ko): Invalid module format

and in syslog:

Oct 16 09:55:00 atlas kernel: [ 1468.784323] wacom: disagrees about version of symbol module_layout

so it seems there is still some class of versions going on.
I got this after doing depmod -a (before this I got a different
error about not finding the module). 

I'm not very good at git, so please be explicit if I need to do something with it. What I did was:

git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/inpux-wacom

You asked me to check dates of files, but everything has the current date,
October 15/16 2012.

This is my kernel:

3.5.0-030500-generic

---

### Post by Favux on 2012-10-16
You clone command is correct and the git log shows the last commit so you're up to date.

Not sure what's going wrong.  I believe input-wacom is suppose to build for 3.6.  By the way did the wacom.ko show up in the new 3.7 folder or still in 2.6.38?  Wrong headers?  Do you see the correct headers in /usr/src?

See the clone instructions in appendix 1 on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  They're the alternate to the tar instructions in part I.  Is that what you did?

---

### Post by jdadams on 2012-10-16
No, wacom.ko showed up in 2.6.38, not in 3.7. Should I try 
to compile the one in 3.7?

I'm not sure what the question about headers is, here is
/usr/src:
drwxr-xr-x 24 root root 4096 Oct 13 06:44 linux-headers-3.2.0-32
drwxr-xr-x  7 root root 4096 Oct 13 06:44 linux-headers-3.2.0-32-generic
drwxr-xr-x  7 root root 4096 Oct 13 06:44 linux-headers-3.2.0-32-generic-pae
drwxr-xr-x 23 root root 4096 Oct 16 06:36 linux-headers-3.5.0-030500
drwxr-xr-x  7 root root mdrwxr-xr-x 24 root root 4096 Oct 13 06:44 linux-headers-3.2.0-32
drwxr-xr-x  7 root root 4096 Oct 13 06:44 linux-headers-3.2.0-32-generic
drwxr-xr-x  7 root root 4096 Oct 13 06:44 linux-headers-3.2.0-32-generic-pae
drwxr-xr-x 23 root root 4096 Oct 16 06:36 linux-headers-3.5.0-030500
drwxr-xr-x  7 root root 4096 Oct 16 09:21 linux-headers-3.5.0-030500-generic
4096 Oct 16 09:21 linux-headers-3.5.0-030500-generic

I'm running kernel 3.5.0, not 3.6. Do I need to use 3.6?
I haven't done that yet because I didn't think I needed to,
and I would have to compile it myself.

Thanks for the help.

---

### Post by Favux on 2012-10-16
Sorry about confusing you.  I was just curious about the wacom.ko location.  I checked the configure.ac and it looks like 3.7 will be the first kernel to show up in the 3.7 folder.

The headers look good for your 3.5 kernel:
```
drwxr-xr-x 23 root root 4096 Oct 16 06:36 linux-headers-3.5.0-030500
drwxr-xr-x 7 root root 4096 Oct 16 09:21 linux-headers-3.5.0-030500-generic
```
And no, I was just saying I was reasonably sure I had seen folks reporting being able to build input-wacom up to and including the 3.6 kernel.  Not suggesting you switch.

In fact I wish you hadn't changed from the 3.4 to 3.5 kernel.

By the way you said you were in Precise 12.04.  But it's default kernel is 3.2.  So are you actually using Quantal 12.10 beta 2?  I think its default kernel might be 3.4.

The other thing I'm curious about is the nomenclature of your kernel labeling.  3.5.0-030500 doesn't seem to be standard Ubuntu format, which usually only has 2 digits after the hyphen.  Did you get this kernel from a PPA?

Edit:  Oops not paying attention.  The other headers are for 3.2 so you are in Precise, and what, 3.5 is Quantal's?  Anyway my suggestion would be to boot into your latest 3.2 kernel and compile input-wacom there and see how it goes.

---

### Post by jdadams on 2012-10-17
I tried kernel 3.5* because of a post mentioned above:
According to 
[http://osdir.com/ml/ubuntu-bugs/2012-09/msg08665.html](http://osdir.com/ml/ubuntu-bugs/2012-09/msg08665.html)
This bug was fixed in the package linux - 3.5.0-14.15

This is probably a red herring, my guess is it wasn't working because of the module wasn't loading.

In any event, back to 3.2.0-32-generic-pae, it is *almost* working. I am getting the wacom stuff showing up in /proc/bus/input/devices, and
in various log files. However, incredibly, when I plug in the wacom to the usb port, the (laptop) monitor goes black. By ssh-ing from
another machine, I could see what happened:

Here is /var/log/syslog
Oct 17 06:51:40 atlas kernel: [  141.852371] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Oct 17 06:51:40 atlas kernel: [  142.006437] hub 2-1:1.0: USB hub found
Oct 17 06:51:40 atlas kernel: [  142.007463] hub 2-1:1.0: 2 ports detected
Oct 17 06:51:42 atlas kernel: [  143.576555] usb 2-1.1: new full-speed USB device number 3 using ehci_hcd
Oct 17 06:51:42 atlas kernel: [  143.672843] input: Wacom Cintiq 22HD as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.1/2-1.1:1.0/input/input9
Oct 17 06:51:42 atlas mtp-probe: checking bus 2, device 3: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.1"
Oct 17 06:51:42 atlas mtp-probe: bus: 2, device: 3 was not an MTP device
Oct 17 06:51:42 atlas gnome-session[1394]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Oct 17 06:51:43 atlas acpid: client 1116[0:0] has disconnected
Oct 17 06:51:43 atlas acpid: client connected from 4205[0:0]
Oct 17 06:51:43 atlas acpid: 1 client rule loaded
Oct 17 06:51:43 atlas bluetoothd[822]: Endpoint unregistered: sender=:1.27 path=/MediaEndpoint/HFPAG
Oct 17 06:51:43 atlas bluetoothd[822]: Endpoint unregistered: sender=:1.27 path=/MediaEndpoint/A2DPSource
Oct 17 06:51:43 atlas bluetoothd[822]: Endpoint unregistered: sender=:1.27 path=/MediaEndpoint/A2DPSink
Oct 17 06:51:43 atlas kernel: [  144.774599] init: lightdm main process (1079) terminated with status 1

and kern.log:

Oct 17 06:51:40 atlas kernel: [  141.852371] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Oct 17 06:51:40 atlas kernel: [  142.006437] hub 2-1:1.0: USB hub found
Oct 17 06:51:40 atlas kernel: [  142.007463] hub 2-1:1.0: 2 ports detected
Oct 17 06:51:42 atlas kernel: [  143.576555] usb 2-1.1: new full-speed USB device number 3 using ehci_hcd
Oct 17 06:51:42 atlas kernel: [  143.672843] input: Wacom Cintiq 22HD as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.1/2-1.1:1.0/input/input9
Oct 17 06:51:43 atlas kernel: [  144.774599] init: lightdm main process (1079) terminated with status 1
Oct 17 06:51:58 atlas kernel: [  159.850525] init: failsafe-x main process (4216) terminated with status 1

I'm not sure what's up with lightdm. I'm running the default 12.04 stuff, including unity, not gnome.

Probably something is seriously messed up in my installation. Assuming this, what would be the best and easiest way
to clean it up? Can I do a partial or complete reinstall? Can I do this using apt-get?

---

### Post by Favux on 2012-10-17
Ah, perhaps an oops on me.  When you:
> I upgraded xf86-input-wacom to version 0.17.0.
did you apply the frankenserver patch to xf86-input-wacom before compiling it?
[http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034](http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034)

---

### Post by jdadams on 2012-10-19
Working! Thanks.
I'll post a summary in case anyone else is in a similar
situation.

---

### Post by jdadams on 2012-10-23
Now I've encountered another problem. I was able to calibrate 
the pen using the wacom system settings app, and everything
was working fine for a few hours.

Now, after rebooting, I cannot get calibration to work. The
icon (on the pen display) is badly offset from the (physical) 
stylus itself, so that I cannot click the calibration targets.
I've tried many different display resolutions, with and
without my laptop monitor turned on. I can send logging
information, but I don't know what it would be.

---

### Post by Favux on 2012-10-23
> Now I've encountered another problem. I was able to calibrate
the pen using the wacom system settings app, and everything
was working fine for a few hours.
I haven't worked with the Gnome Wacom applet's calibration stuff yet, since I haven't had a version that included it.  2 to 4 crosshairs that you touch with the stylus tip?  Does it show the calibration coordinates it gets when it is done?   Tell you where they are stored or how they are applied?

I think you also have a dual monitor setting in the applet.  Did you also make a change in that setting?

---

### Post by jdadams on 2012-10-23
It displays a circle with two crosshairs sequentially in each 
of the four corners of the display. No, it doesn't show any 
coordinates or any other information. And there is not any 
dual monitor setting in the applet, just a button to calibrate,
one related to the buttons, and a few settings on the pen 
(buttons, tip feel, etc).

---

### Post by Favux on 2012-10-23
Okay, then lets assume it is a bug in the applet's calibration and not go exploring how your video card is handling the Cintiq "monitor" and the "real" monitor.

Does the calibration option allow you to reset it or zero it out or otherwise not apply it?

---

### Post by jdadams on 2012-10-23
No, no such option.

---

### Post by Favux on 2012-10-23
Presumably the coordinates are stored in the gnome-settings-daemon Wacom plugin.  The key is probably called Area or maybe Calibration.  Some such anyway.

Install dconf-editor:
```
sudo apt-get install dconf-editor
```
Then open it (**dconf-editor** in a terminal).  Navigate to org.settings-daemon.gnone.peripherals.wacom.  What do you see there?

---

### Post by jdadams on 2012-10-23
I installed dconf-editor (BTW apt-get dconf-tools) and 
found org/gnome/settings-daemon/peripherals (note the gnome)  but 
no wacom there, only input, keyboard, mouse, smartcard,touchpad,
touchscreen. Also org/gnome/setting-daemon/plugins, but 
nothing there either.

Thanks for the help.

---

### Post by Favux on 2012-10-23
Well something is whackadoodle.  I'm staring at my BambooPT's keys and key values:  org.gnome.settings-daemon.peripherals.wacom.usb:056a:00d1

Are you using Kubuntu?

---

### Post by jdadams on 2012-10-23
Well, that's interesting. I also have a Bamboo tablet, so I 
plugged it in. Now I do have such a setting, and when I unplug
the Bamboo and plug in the 22HD it remains, and shows 
the values:

settings-daemon/peripherals/wacom/usb:0x56a:0xfa
area  [74699,2170,81390,51914]
display ['WAC','4146','825636144']
is-absolute (checked)

The area value is the same as that returned by xsetwacom
(see below).

By the way the performance of the calibration tool 
has changed - it is better, but still off.

For the record here is the output of xsetwacom get 15 all

Option "Area" "74699 2170 81390 51914"
'Button' requires exactly 1 value(s).
Option "ToolDebugLevel" "0"
Option "TabletDebugLevel" "0"
Option "Suppress" "2"
Option "RawSample" "4"
Option "PressureCurve" "0 25 75 100"
Option "Mode" "Absolute"
Option "TabletPCButton" "off"
Option "Touch" "on"
Option "Gesture" "off"
Option "ZoomDistance" "0"
Option "ScrollDistance" "0"
Option "TapTime" "250"
Property 'Wacom Proximity Threshold' does not exist on device.
Option "Rotate" "none"
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Option "Threshold" "27"
Option "ToolType" "249"
Option "ToolSerial" "0"
Option "ToolID" "0"
Option "ToolSerialPrevious" "0"
Option "BindToSerial" "0"
Option "TabletID" "250"

---

### Post by Favux on 2012-10-23
lol  Now isn't that special.  Appears there is a bug somewhere.

I just checked my git clone of libwacom and Jason did add a cintiq22hd.tablet data file.  See if you find that file in /usr/share/libwacom.  It isn't in my Precise libwacom.  Whether it is there or not it is still a bug that the keys and key values are invisible and suddenly appear when prompted by plugging in a BambooPT.  I assume they will disappear again on a reboot.

Now the values you are seeing seem to reflect the Citiq's coordinates offset by the monitor a la MapToOutput.
So the mistake was using the Wacom applet to calibrate.

We've tried a couple of times to add a .tablet data file to /usr/share/libwacom.  I assume there is some sort of data base registration when Gnome Control Center is compiled which is why just adding the data file doesn't work.  If so I don't know how to update the registration, if that is even possible.  Besides SourceForge is down right now.  Well I guess I could attach the data file.

So that leaves setting things up through xsetwacom maybe using coordinates from xinput_calibrator.  Since SourceForge is down the LWP mediawiki isn't available so see the [HOW TO Setup a Wacom Tablet with Multi-Monitors]("http://ubuntuforums.org/showthread.php?t=1656089").

By the way how off were the coordinates in the first place?  You know, where you felt the need to calibrate.

Edit:  Remove the .txt extension from the file.

---

### Post by jdadams on 2012-10-23
I put cintiq-22hd.tablet in place. What effect should that have?
Should I then be able to use the configuration gui? 
(Edit: no, the file was not in /usr/share/libwacom).

The configuration was off about an inch or so, certainly 
enough to require calibration.

---

### Post by Favux on 2012-10-23
I'm hoping that after a reboot when you go to the Wacom applet your Cintiq is identified by the applet and it now works correctly for you.  If it then handles calibration correctly headache avoided.  I can't remember if we tried it with a wacom tablet before.  I know we have with several non-wacom tablets that had their pen on the wacom X driver.  And their .tablet files didn't help.

---

### Post by jdadams on 2012-10-23
I don't want to get too excited, but this appears to have worked.
The configuration applet works fine, and the wacom entry appears
in the dconf-editor. I'm not counting my chickens because
it was working earlier today before all this started, but I'll 
keep my fingers crossed.

Thanks so much!

---

### Post by jdadams on 2012-10-25
I'm on the verge of giving up. When I reboot I get the
wacom stuff to show up in dconf-editor about 1/2 the time. 
The appropriate file is still in /usr/share/libwacom.
Even when it shows up in dconf-editor, I can only rarely 
get the configuration tool to work. So I fell back to using
xsetwacom to configure the stylus, but often this doesn't
even work (do I need to use MapToOutput to enable this?)

---

### Post by Favux on 2012-10-25
I don't blame you.  This is turning into more of a headache than it should be.

Since this is intermittent, while unlikely, it may be a hardware problem.  First while you are trying to get things working don't plug the Cintiq into a usb hub.  Use a usb port directly on the computer.

Are you booting with the Cintiq plugged in?  To rule out a hardware problem does the Cintiq work correctly in another release or Distro?  Or in another OS such as OSX or Windows?


If you've ruled out hardware the next step is to look at your Xorg.0.log in /var/log.  Is it showing you error messages associated with the Cintiq, especially during hot plugging?

You can turn on debugging and generate more messages in the Xorg.0.log.  Either in the wacom.conf in xorg.conf.d, see **man wacom** for the debugging options.  Or you can do it using xsetwacom debugging parameters, see **man xsetwacom** in a terminal.
> So I fell back to using
xsetwacom to configure the stylus, but often this doesn't
even work (do I need to use MapToOutput to enable this?) 
This is what raises the red flag to me.  Maybe you should expand a little more on the xsetwacom commands working intermittently?  I assume the Cintiq's display isn't being treated as a separate X screen from the monitor correct?  Which means there is a virtual screen composed of both screens.  So yes, you would use MapToMonitor to account for the offset of the monitor.

What's the output of **xrandr** in a terminal?  What video chipset are you using?
```
lspci | grep VGA

and/or

sudo lshw -C display
```

---

### Post by jdadams on 2012-10-25
It is plugged directly into a usb port on my Thinkpad T400s.
The Cintiq works fine on a mac.

A command such as 
xsetwacom set 15 Area "0 0 95500 53500" 
sometimes works, and the change appears in the output
of dconf editor. Other times it has no effect (and 
I think these are correlated with times it doesn't
appear in dconf-editor). On at least one occasion 
making the change directly in dconf-editor had the 
desired effect. 

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

root@atlas:/home/jda# lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f2000000-f23fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f2400000-f24fffff

The display is not currently plugged in, but here is xrandr:


Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
LVDS1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1440x900       60.0*+   59.9     50.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

---

