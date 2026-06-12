---
title: "Medion E1222 - Aldi Netbook"
date: 2010-03-06
forum: Hardware
---

### Post by skarard on 2010-03-06
Hey Guys and Gals

UNR installation was ok on the little Medion E1222.

Wifi & Sentelic FingerSensingPad have been the only issues. Wifi is easy just do what it says [here]("http://ubuntuforums.org/showpost.php?p=8335065&postcount=2"). (Must be connected to Internet(Use Ethernet Port))

[http://ubuntuforums.org/showpost.php?p=8335065&postcount=2](http://ubuntuforums.org/showpost.php?p=8335065&postcount=2)

Sentelic FingerSensingPad is a bit harder. 
There was a bug filed [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311869") that has a module compiled you can modprobe in to your kernel.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311869](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/311869)

This fix is included with the 2.6.32 kernel.

This post on MSIwind forum archive from March 27th by vern is brilliant to get the Finger Sensing Pad with basic function including not going crazy after suspend. 

[http://insanelywind.com/msiarchive/viewtopic.php?f=7&t=4828&start=40](http://insanelywind.com/msiarchive/viewtopic.php?f=7&t=4828&start=40)

My FSP was /sys/devices/platform/i8042/serio2 

So in the fsp_conf file pay attention to the line:

FSP_DEV_DIR="/sys/devices/platform/i8042/serio1"

then change it appropriately.

[http://insanelywind.com/msiarchive/viewtopic.php?f=7&t=4828&start=40](http://insanelywind.com/msiarchive/viewtopic.php?f=7&t=4828&start=40)

I found the my Finger Sensing Pad stopped working after reboot so what you need to do is edit /etc/default/grub. 

```
sudo gedit /etc/default/grub
```

and change

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset=1"

Note: When installing UNR from USBStick if you ran it as a LiveCD then shut down booted from USBStick chose to "Install UNR" the Finger Sensing Pad doesn't work during install.

To resolve: add argument to boot line "i8042.reset=1"

I hope this makes sense to someone. I didn't have a lot of time so it's hashed together a bit. If people require I can try and more newbie friendly version.

---

### Post by thmweb on 2010-03-13
The difference to your configuration is, that my FSP is /sys/devices/platform/i8042/serio0

You write:
>So in the fsp_conf file pay attention to the line:
>FSP_DEV_DIR="/sys/devices/platform/i8042/serio1"

I cannot find any fsp_conf file. Where is it?
I'm unsure if the psmouse.ko does not detect my touchpad or fspc does not recognize it. When I understand it right, then the touchpad should be usable with the patched psmouse, right?

---

### Post by skarard on 2010-03-24
> **thmweb said:**
> The difference to your configuration is, that my FSP is /sys/devices/platform/i8042/serio0

You write:
>So in the fsp_conf file pay attention to the line:
>FSP_DEV_DIR="/sys/devices/platform/i8042/serio1"

I cannot find any fsp_conf file. Where is it?
I'm unsure if the psmouse.ko does not detect my touchpad or fspc does not recognize it. When I understand it right, then the touchpad should be usable with the patched psmouse, right?

fsp_conf is the file you created from the post on the MSIWind Archive. To edit it go to a terminal and type in: sudo gedit /usr/local/bin/fsp_conf 

My finger sensing pad would not work until I edited the line in /etc/default/grub: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

To read: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset=1"


The kernel will automatically load psmouse.ko when it detects the Finger Sensing Pad.  

I hope this helps I wasn't entirely sure what you meant by your question.

---

