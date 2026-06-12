---
title: "USB Hard disk not auto-mounting on boot"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by markonhismobile on 2007-08-20
I've got a bit of a strange one here, so I'll give it a go!

I'm running an old Samsung laptop running Feisty Server edition with LAMP to host Torrentflux (amongst other things). I'm using a USB 2.0 PCMCIA card to connect to an external HDD to provide the storage I need as the internal HDD on the laptop is to small for this!

The HDD is recognized and mounts great except when the system is rebooted (something I have to to about once a week as Apache (I think)seems to stop responding every 7 days forcing a reboot - I'm a newbie so bear with me!) it doesn't auto-mount on startup! I've selected the option to mount at startup when I was setting it up in Webmin but it just doesn't seem to!

Here's my FSTAB:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d4044ad4-74ba-477e-955b-07f15887a445 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8a3a87f1-4571-4427-962a-178d98547048 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1  /mnt/USB  ext3  user,suid,dev,exec  0  0

I can mount the HDD from within Webmin, or via the CLI but it just throws off Torrentflux and Firefly as they both rely on this drive for their data and it's a pain to do each time I reboot!
Failing that could I use a simple shell script, run via init.d or rc.d, to mount it on boot?

I'm not to sure if this is caused by the fact I'm using the server kernal: 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686 GNU/Linux - the USB drive doesn't appear under the /media directory.

If so is there an easy way to change over to the regular desktop kernal - would it just be as simple as apt-get-ting the most current one?

Thank you in advance!

---

