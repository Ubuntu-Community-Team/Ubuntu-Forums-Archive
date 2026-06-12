---
title: "Automount 2nd hard drive"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by TrevorNet on 2006-06-03
OS : Dapper Drake 6.06

Problem : Perma mount second hard drive on boot-up with wide-open permissions.

Additional : I've added the bottom line to my fstab file in the hopes that it will achieve the perma-mount status of additional storage space

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc1 	/slut ext3 defaults 0[/B]

Upon reboot, I am finding my "slut" folder un-loved, un-mounted and not reflecting the love I've tossed into it. That is, when I manually mounted, and mapped, hdc1 to /slut, I created a folder to store wallpaper media files in. Finding this folder empty makes me think it is acting as a standard folder on my normal dive and not a mount point for the second drive.

I have installed, through Synaptic, all the tools I thought were possible in making this happen. Nada.

On top of that, I'd like to force this drive, "/slut", to have public read, write, and execute (I know... I know...) permissions (read & write always, execute where possible).

Any suggestions as to how to make this happen?

Cheers
~t

---

### Post by jgoguen on 2006-06-03
Try this line instead of what you have:
```
/dev/hdc1     /slut     ext3     defaults     0     0
```
Note the extra 0 at the end.  Then, make sure /slut is empty before mounting and mount with
```
sudo mount /slut
```
That should just come back to a prompt.  Now, to set global permissions, do (with the empty directory still):
```
sudo chown -R root:wheel /slut
sudo chmod -R 1777 /slut
```
Now, despite being owned by root/wheel, anyone can write to this directory.  You can only modify files owned by you though, as a little security.  If you want everyone to be able to modify all files regardless of owner, then use "0777" above instead of "1777".

---

