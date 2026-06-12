---
title: "dvd won't read"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by ravengirl1960 on 2007-06-22
At first, I thought this was a codecs issue, but i've got all the libdvd libraries, etc. None of my players will read a dvd (kaffeine, totem, mplayer, noatun, gxine, etc) and k9copy gives me a 'can't open main ifo' error. However, if i put a dvd into the drive and open up k3b, it sees it with no problems. So, i'm thinking either my fstab is wrong, or i've got a missing link somewhere?
my fstab is:

# Pluggable devices are handled by uDev, they are not in fstab
# /dev/sda1 -- converted during upgrade to edgy
UUID=1d7a99af-5d0f-4e5d-beec-3fbb0110308c / ext3 defaults,noatime 1 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=92b34f94-cb04-412c-adfe-77c5c158b39d swap swap sw,pri=1 0 0
none /proc proc defaults 0 0
none /proc/bus/usb usbfs devmode=0666 0 0
none /dev/pts devpts mode=0622 0 0
none /sys sysfs defaults 0 0
# /dev/sda3 -- converted during upgrade to edgy
UUID=70c1b374-0953-4593-b32e-34dd7634bdb5 /home ext3 defaults,noatime 1 2
/dev/cdrom /media/cdrom iso9660,udf noauto,users,exec,ro 0 0
# Dynamic entries below, identified by 'users' option
/dev/sda1 /mnt/sda1 ext3 noauto,users,exec 0 0
/dev/sda2 swap swap sw,pri=1 0 0
/dev/sda3 /mnt/sda3 ext3 noauto,users,exec 0 0

I don't know how to check for the symlinks, to see what's there and what's not...
any ideas/comments?

edit: i just found out, i can also mount the dvd, thru k3b, and then copy it to my hd, etc...

---

