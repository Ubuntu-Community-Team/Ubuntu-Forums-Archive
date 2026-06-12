---
title: "Toshiba with ATI drivers Hibernate Fix"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Ryangarve on 2007-10-24
This was fix was originally for an Acer laptop but I figured I would try it on my Toshiba Satellite.  I have yet to try suspend but I don't this is for that, also the only way this works is if you use the terminal command sudo s2disk, but for someone with a laptop this is a lifesaver.

> Okay.

I have figured out how to fix hibernate for My Acer Laptop.

Disable the ATI Driver(In KDE, KDE->System Settings->Advanced->Restricted Drivers), for Gnome.. I have no idea.

After you disable the ATI Driver,

go to a terminal and:

sudo nano /etc/uswsusp.conf

(If you do not have nano, sudo apt-get install nano - I'm pretty sure it comes on all installs)

It should look something like this:

Code:

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
resume device = UUID=70554dbc-5ffc-4c5c-bd2e-258ad118db4f
splash = y
compress = y
early writeout = y
image size = 425876684
RSA key file = /etc/uswsusp.key
shutdown method = platform

You need to change the UUID= part, and replace it with your swap's /dev/ address.

To do this, just type 'sudo fdisk -l' - and you should find your swap in there.

Code:

wastedfluid@fluid:~$ sudo fdisk -l
[sudo] password for wastedfluid:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1305    10482381   83  Linux
/dev/hda2            1306       12030    86148562+  83  Linux
/dev/hda3           12031       12161     1052257+   5  Extended
/dev/hda5           12031       12161     1052226   82  Linux swap / Solaris
wastedfluid@fluid:~$

Ok, so my swap is /dev/hda5.. now, go back to your 'sudo nano /etc/uswsusp.conf' - and comment out that long UUID= number, and add your /dev/hda5.. or YOUR swap. Mine looks like this:

Code:

wastedfluid@fluid:~$ cat /etc/uswsusp.conf
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
#resume device = UUID=70554dbc-5ffc-4c5c-bd2e-258ad118db4f
resume device = /dev/hda5
splash = y
compress = y
early writeout = y
image size = 425876684
RSA key file = /etc/uswsusp.key
shutdown method = platform
wastedfluid@fluid:~$

After you replace your resume device with your swap /dev/ address,

go to a terminal and type

'sudo dpkg-reconfigure uswsusp'

And it should re-configure everything. Give it a go, and type sudo s2disk. This should work for most Acer laptops...

---

