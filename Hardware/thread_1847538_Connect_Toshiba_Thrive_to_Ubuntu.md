---
title: "Connect Toshiba Thrive to Ubuntu"
date: 2011-09-21
forum: Hardware
---

### Post by denisk on 2011-09-21
Hey everyone.
I've got my Toshiba Thrive tablet today, however, I can't make ubuntu 11.04 see it when connecting through mini usb. Surprisingly, there is no information about this kind of problem, except of this topic on thrive forums [http://www.thriveforums.org/forum/toshiba-thrive-help/1462-connecting-thrive-ubuntu-11-04-a.html](http://www.thriveforums.org/forum/toshiba-thrive-help/1462-connecting-thrive-ubuntu-11-04-a.html)
They describe the way of mounting it manually, but this doesn't work for me - ```
sudo fdisk -l
``` doesn't show any new filesystems.
Any help would be greatly appreciated.

---

### Post by papibe on 2011-09-21
That command is used to show what disks are mounted, but it does not actually do anything. Could you post the result of that command?

Regards.

---

### Post by denisk on 2011-09-21
Sure, here it is
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671        7826    49445888   83  Linux
/dev/sda4            7826       38914   249708545    5  Extended
/dev/sda5            7826        8313     3907584   82  Linux swap / Solaris
/dev/sda6            8313       38914   245799936   83  Linux

```
First and second ones are Windows partitions (shipped with the laptop).
I ran into another tutorial, which is pretty nice, except that it didn'n work for me.
[http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html](http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html)
However, in 
```
lsusb
```
I can see the tablet, which means that the hardware and the cable are OK:
```
...
Bus 001 Device 002: ID 0930:7100 Toshiba Corp. 
...
```
Can 
```
mtpfs
```
be broken?
It's funny - I have HTC desire (android 2.2) which connects to ubuntu flawlessly, but what happened with android 3.1?

---

### Post by denisk on 2011-09-21
Stupid me, I have mis-configured my **/etc/fstab** file. It was
```
mtpfs    /media/thrive     fuse    [COLOR=Red]denisk[/COLOR],noauto,allow_other    0    0
```
instead of
```
mtpfs    /media/thrive     fuse    [COLOR=SeaGreen]user[/COLOR],noauto,allow_other    0    0
```
After that remounted
```
sudo mount -a
```
... and I have thrive as my disk. So, the aforementioned tutorial really works!:)

---

### Post by papibe on 2011-09-21
:P Glad you solved it!

---

### Post by ussndmac on 2011-12-10
I'm attempting to do this with my new thrive to no avail.

lsusb shows the thrive.

syslog shows no activity when the device is plugged in, i.e. no mtpfs logged.

Any ideas?

This is with Android 3.2 and Ubuntu 11.04

Regards,
Mac

---

### Post by papibe on 2011-12-10
I would try this: shutdown your PC, turn on the Thrive and connect it to the PC. Now boot your PC with the Thrive on and connected. 

I think that would increase the chances for the device being recognized.

Just a thought.
Regards.

---

### Post by WoollyW on 2012-04-24
Can anyone walk me through manually mounting my at100 (thrive)?

I've hunted around Google and most of what I need to do I've never done before and don't want to mess anything up!

From this tutorial I've got as far as creating the thrive directory, and that's it, as I'm not sure what path I should be entering of whether I need to create a udev entry, or how to correctly for that matter...

[http://www.thriveforums.org/forum/toshiba-thrive-help/1462-connecting-thrive-ubuntu-11-04-a.html](http://www.thriveforums.org/forum/toshiba-thrive-help/1462-connecting-thrive-ubuntu-11-04-a.html)

any help available?

or should I start a fresh thread as this one is marked Solved?

Thanks!

---

