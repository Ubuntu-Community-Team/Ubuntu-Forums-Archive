---
title: "[SOLVED] Upgrade asked about menu.lst, now GRUB Error: 5"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by madhartigan on 2008-12-06
I just completed an update and during the update I was asked whether I wanted to keep the menu.lst that I had or use the one supplied with the upgrade.

There were a bunch of options in the drop down list of the dialog box but I didn't think they applied to me.

Well, I figured that I wanted an updated menu.lst because in my "noobness"  updated seems better than outdated.  I guess I was wrong.

I completed the update by rebooting my system and was immediately confronted by a Grub Error 5: Partition table invalid or corrupt.

I know it's not corrupt because everything was running just fine before I did this update.

If anyone could help me repair my menu.lst so I can get up and running, I'd really appreciate it.


Thank you,

Darryl

---

### Post by caljohnsmith on 2008-12-06
OK, how about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

### Post by madhartigan on 2008-12-07
Ok here's the outputs:

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003b2cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   139219289    69609613+  83  Linux
/dev/sdc2       139219290   145211534     2996122+   5  Extended
/dev/sdc5       139219353   145211534     2996091   82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table
ubuntu@ubuntu:~$ 

```

```

ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sda
0000
ubuntu@ubuntu:~$ 

```

```

ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdb
0000
ubuntu@ubuntu:~$ 

```

```

ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdc
eb48
ubuntu@ubuntu:~$ 

```

```

ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdd
0000
ubuntu@ubuntu:~$ 

```

```

ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sde
0000
ubuntu@ubuntu:~$ 

```

```

ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sdc
00ff
ubuntu@ubuntu:~$ 

```


Note: Drives sda and sdd are members of one RAID array and drives sdb and sde are members of another RAID array.

Hope this information helps you to diagnose.

I've tried changing my menu.lst entries from (hd2,0) to various locations ((hdx,y) changing x and y) and haven't hit upon the right one.  I'm sure that's all I have to do to get this fixed.

TIA for your help!!

EDIT:  Well, it turns out that my items in menu.lst needed to be pointed to hd0,0 now I'm booting fine.

I do have another issue but that's for a different forum and new thread.

Thanks!!

---

### Post by caljohnsmith on 2008-12-07
OK, so according to the results of those commands, it looks like you have Grub properly installed to the MBR of your Ubuntu sdc drive. So do you get the Grub error 5 before you see the Grub menu on start up, or after you choose to boot Ubuntu from the Grub menu? If it is the latter case, then as you say, the menu.lst probably is using the wrong (hdX,Y) for Ubuntu. So if it is the latter case, first open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And use (hd0,0) for all the Ubuntu entries, similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root            [COLOR="Blue"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

```
And then you should hopefully be all set. Or if you get the error 5 before seeing the Grub menu, let me know and we can work from there. :)

---

