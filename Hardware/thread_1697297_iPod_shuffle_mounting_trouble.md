---
title: "iPod shuffle mounting trouble"
date: 2011-02-28
forum: Hardware
---

### Post by Damascushead on 2011-02-28
Hello,

I have an old school iPod shuffle, not sure what generation (but one of the elongated white stick kind.) I have been having trouble getting it to mount. It will not show up in my /media file. However, it is detected as is proven by the **output of lsusb** which is:

[B]tyler@Lazarus:/media$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:1300 Apple, Inc. iPod Shuffle
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 5986:0105 Acer, Inc 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/B]



I did edit **/etc/fstab** to mount from **/media/ipod** once i created the latter directory.

btw...this is what was added to fstab:  **/dev/sda2 /media/ipod vfat user,noauto,umask=000 0 0**

so now when i [B]sudo mount /dev/sda2
[/B]i get the following message


[B]tyler@Lazarus:/$ sudo mount /media/ipod
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


[/B]What other methods should I try, as I have never really done much of this stuff?

Thanks! :P

---

### Post by Damascushead on 2011-02-28
Ya know, after a couple of hours I got it to work. It turns out that the iPod was in /dev/sdc1 which is strange, because as i understand it most users have the device show up on /dev/sda2 or closer relative.


Thanks anyways. Problem solved.:KS

---

