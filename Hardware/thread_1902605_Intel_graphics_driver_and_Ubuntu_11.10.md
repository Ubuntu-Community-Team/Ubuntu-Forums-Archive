---
title: "Intel graphics driver and Ubuntu 11.10"
date: 2011-12-31
forum: Hardware
---

### Post by am577 on 2011-12-31
I installed 11.10 on an HP laptop (G6-1257sa, i3-2330M cpu, HD Graphics). It didn't automatically install the proper Intel graphics driver, so I used these commands (as noted in this forum):
[FONT=Arial, sans-serif][SIZE=2]sudo add-apt-repository ppa:glasen/intel-driver [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2]sudo apt-get update[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2]sudo apt-get upgrade[/SIZE][/FONT]
  [FONT=Arial, sans-serif][SIZE=2]sudo apt-get install linux-image-generic-lts-backport-oneiric linux-headers-generic-lts-backport-oneiric[/SIZE][/FONT]
 The last command got:
[FONT=monospace]E: Unable to locate package linux-image-generic-lts-backport-oneiric
E: Unable to locate package linux-headers-generic-lts-backport-oneiric[/FONT]
[FONT=monospace]and it doesn't seem to have installed the proper driver - it is still using the VESA driver.[/FONT]
[FONT=monospace]What did I get wrong ?[/FONT]
[FONT=monospace]AM[/FONT]
[FONT=monospace]
[/FONT]

---

### Post by jerrrys on 2012-01-01
[FONT=Arial, sans-serif][SIZE=2]sudo apt-get install linux-image-generic-lts-backport-oneiric linux-headers-generic-lts-backport-oneiric

is wrong and needs to be replaced with maybe:

sudo apt-get install [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]glasen/intel-driver

or maybe

sudo apt-get install [/SIZE][/FONT][FONT=Arial, sans-serif][SIZE=2]glasen

I do not use this driver so I am not sure of its proper name.
 [/SIZE][/FONT]

---

### Post by meijer.o on 2012-01-01
Dear am577,

I would think that your computer is supported and that the graphic driver works fine

Why do you think that you have to install it? It is a kernel module named i915

Please open a terminal and post the output of the command

lsmod | grep i915

If the outcome is like: 
i915                  461598  3 
drm_kms_helper         42261  1 i915
drm                   241390  4 i915,drm_kms_helper
i2c_algo_bit           13368  1 i915
video                  19280  1 i915

then the driver is loaded

Best regards,
Otto

---

### Post by sourav7865 on 2012-01-02
HOw do i install Intel Media accelerator driver for Intel core i5 processor
please help

---

### Post by snafu_az on 2012-01-03
I'm having a similar problem. I have to use NOMODESET in grub for it to load up and then it only loads the VESA driver.  If I don't use NOMODESET the screen just cycles through colors, blue, yellow, green etc, over and over.

I have been searching for a couple weeks now trying differnt configs and can't get it to work correctly.  With NOMODESET it loads the VESA driver and limits me to 1280x1024.  I have a full HD screen 1920x1080.  Works great in W7 but I hate W7.

---

### Post by homeyclaus on 2012-01-03
If you look at the PPA authors' web page it states that the modes you're using are no longer supported. [https://launchpad.net/~glasen/+archive/intel-driver?field.series_filter=oneiric](https://launchpad.net/~glasen/+archive/intel-driver?field.series_filter=oneiric)

> 
Warning :

Version 2.15 and 2.17 of the Intel-driver only support KMS. If you've deactivated KMS e.g. by adding the option "i915.modeset=0" to the file "/etc/default/grub", please reactivate KMS by deleting this option.


Remove them from your /etc/default/grub file, (or just press 'e' when you boot to try it once) and see if the stock drivers work.

---

### Post by snafu_az on 2012-01-05
Removing NOMODESET doesn't work for me.  All I get is a screen of white then red, green, blue, black and then it starts over again.

That's all it does.

The only thing that caught my eye in Xorg.0.log is ...


[    11.328] (II) intel(0): Output VGA1 has no monitor section
[    11.968] (II) intel(0): Output HDMI1 has no monitor section
[    12.016] (II) intel(0): Output DP1 has no monitor section
[    12.656] (II) intel(0): Output HDMI2 has no monitor section
[    12.704] (II) intel(0): Output DP2 has no monitor section
[    12.704] (II) intel(0): EDID for output VGA1
[    13.344] (II) intel(0): EDID for output HDMI1
[    13.392] (II) intel(0): EDID for output DP1
[    14.032] (II) intel(0): EDID for output HDMI2
[    14.080] (II) intel(0): EDID for output DP2
[    14.080] (II) intel(0): Output VGA1 disconnected
[    14.080] (II) intel(0): Output HDMI1 disconnected
[    14.080] (II) intel(0): Output DP1 disconnected
[    14.080] (II) intel(0): Output HDMI2 disconnected
[    14.080] (II) intel(0): Output DP2 disconnected
[    14.080] (WW) intel(0): No outputs definitely connected, trying again...
[    14.080] (II) intel(0): Output VGA1 disconnected
[    14.080] (II) intel(0): Output HDMI1 disconnected
[    14.080] (II) intel(0): Output DP1 disconnected
[    14.080] (II) intel(0): Output HDMI2 disconnected
[    14.080] (II) intel(0): Output DP2 disconnected
[    14.080] (WW) intel(0): Unable to find connected outputs - setting 1024x768 initial framebuffer

---

### Post by homeyclaus on 2012-01-06
Can you post the output of 'cat /proc/cmdline'?

And also, is your system one of those dual mode systems with a discrete graphics chip as well as the intel one?

---

### Post by snafu_az on 2012-01-06
Here's /proc/cmdline:

BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=6111843e-87e0-4e37-bffd-2819b75953f8 ro quiet splash vt.handoff=7 nomodeset

As far as I can tell it only has the intel integrated HD graphics.  It's an all-in-one called the touchsmart 610.

---

### Post by homeyclaus on 2012-01-09
> **snafu_az said:**
> Here's /proc/cmdline:

BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=6111843e-87e0-4e37-bffd-2819b75953f8 ro quiet splash vt.handoff=7 nomodeset

As far as I can tell it only has the intel integrated HD graphics.  It's an all-in-one called the touchsmart 610.

At the grub command line, try replacing the nomodeset with i915.semaphores=1

---

### Post by snafu_az on 2012-01-09
No change. Didn't make any difference.

---

### Post by homeyclaus on 2012-01-10
I wonder if there is a way for you to attach the Xorg.0.log as an attachment, compressed of course.

gzip Xorg.0.log, and try the attachment button.

Also, did you upgrade to the glasen driver?

---

### Post by snafu_az on 2012-01-10
Do you want the one where I boot with nomodeset or without ?

---

### Post by snafu_az on 2012-01-10
I know it's a lot, but here goes

Too big for an attachment. I'll try again

---

### Post by snafu_az on 2012-01-10
Here it is zipped

---

### Post by homeyclaus on 2012-01-11
Alright, so there is something wrong with the detection logic on your board or something.

If you know your screen's specifications and the output it's connected to, you can force the x server to not autodetect for that port and just enable it.

In your case, your xorg.conf is actually a directory, /usr/share/X11/xorg.conf.d/

In this, you can set manually override the autodetection logic.

# start /usr/share/X11/xorg.conf.d/10-override

Section "Device"
Identifier "Intel HD Graphics"
Driver "intel"
Option "monitor-VGA1" "none"
Option "monitor-DP1" "MyMonitor"
Option "monitor-HDMI1" "none"
Option "monitor-HDMI2" "none"
Option "ModeDebug" "true"
EndSection

Section "Monitor"
Identifier "MyMonitor"
Option "enable" "true"
EndSection

Section "Monitor"
Identifier "none"
Option "ignore" "true"
EndSection

# end

You may have to tweak this, or set the actual graphic mode or something.

---

### Post by snafu_az on 2012-01-24
Didn't make any difference. Over the last week i wiped th hard drive and tried a few other distributions. 11.10 32bit, fedora 16, centos 5, kbuntu 11.10, open suse (what ever the latest version is) and they all do the same thing. If i don't put nomodeset in grub it won't come up right.  It just cycles red, blue, green etc over and over.

Just put Ubuntu 11.10 64bit back on. going to play with it for a while.

---

### Post by J14e on 2012-03-04
where do u even get intel graphics drivers  i just switched back to ubuntu on my toshiba and need to get drivers but no proprietary found

---

