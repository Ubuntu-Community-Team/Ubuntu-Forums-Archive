---
title: "Can't mount cdrom"
date: 2006-12-22
forum: Hardware &amp; Laptops
---

### Post by radiant chains on 2006-12-22
Hi, I'm running Kubuntu Edgy (upgraded from Dapper). The cdrom drive is no longer able to mount any cds or dvds. I know it's not a hardware problem because I can still boot a LiveCd from power-on. 

Here's my fstab, if that might help:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=7de00ac1-d71e-4d39-aaa3-afae4c44ac35 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=5815f0f3-88eb-4c1a-94ca-8a975175622e none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by taurus on 2006-12-22
What happens if you pop in a CD and see if you can mount it from a terminal?

Applications -> Accessories -> Terminal
```
sudo mount -t iso9660 /dev/hdc  /media/cdrom0
```

---

### Post by radiant chains on 2006-12-22
When I try that command, the terminal pauses for about 15 seconds, and then displays:

```
mount: mount point /media/cdrom0 does not exist
```

---

### Post by taurus on 2006-12-22
What's the output of this command from a terminal then?

```
ls -la /media
```

---

### Post by radiant chains on 2006-12-22
```
total 12
drwxr-xr-x  3 root root 4096 2006-12-22 17:25 .
drwxr-xr-x 21 root root 4096 2006-12-14 05:53 ..
lrwxrwxrwx  1 root root    6 2006-08-09 19:42 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-08-09 19:42 cdrom0
lrwxrwxrwx  1 root root   42 2006-12-14 05:53 .hidden -> /etc/kubuntu-default-settings/hidden-media

```

---

### Post by taurus on 2006-12-22
Hmm...  There is a /media/cdrom0!  What happens if you run this from a terminal?

```
sudo mount -t iso9660 /dev/hdc  /media/cdrom
```

---

### Post by radiant chains on 2006-12-22
Same result:

```
mount: mount point /media/cdrom does not exist
```

---

### Post by taurus on 2006-12-22
Okay, try this then...

```
sudo mkdir /mnt/cdrom
sudo mount -t iso9660 /dev/hdc  /mnt/cdrom
```

---

### Post by radiant chains on 2006-12-22
Hmm... after trying that the terminal displays this and then locks (i cant type anymore and ctrl-c doesn't cancel the command):

```
[17180271.928000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
```

I just tried rebooting, and it seems that if i put in a cd while the os is starting up, it's auto-mounted after KDM login. However, as soon as I remove the cd and try another, it refuses to mount again, even with the same cd.

---

### Post by radiant chains on 2006-12-22
I also ran a ```
dmesg | grep 'hdc'
```

and it gave pages full of```
[17180751.928000] hdc: lost interrupt
[17180751.928000] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

```

---

### Post by taurus on 2006-12-22
Maybe you need to open up the case and check the cable to your CD-ROM drive  to be sure it's securely in place...

---

### Post by JanEnEm on 2006-12-30
I am curious as to what has happened since the last post. 
I ran into a similar problem, however my situation may be different: I run VMware server with a Ubunto Dapper (6.06 LTS) as virtual machine. I tried to install CUPS with the same error. My virtual machine CD definition has the Ubuntu ISO mounted as CDrom.
Thanks to the prevoius discussion I founnd out that the activation of the VMware Tools installation overruled this CD to be connected/mounted on Ubuntu..
The command
 [FONT="Courier New"]ls /media/cdrom [/FONT]
showed the files from VMware tools in stead of the Ubuntu CD!
Lesson to be learned: make sure VMware tools installation is no longer active before you start using the CDrom as normal CDrom!

---

### Post by Tibor60 on 2006-12-30
I could not mount my fd0 floppy. I was furious and for a lot of work I found that vmware kills my fd0... the short problem solving:

root@GOLDEN10:~# mount /dev/fd0
mount: /dev/fd0 already mounted or /media/floppy0 busy
root@GOLDEN10:~# mount /dev/fd1
root@GOLDEN10:~# umount /dev/fd0
umount: /dev/fd0: not mounted
root@GOLDEN10:~# lsof /dev/fd0
COMMAND    PID  USER   FD   TYPE DEVICE SIZE NODE NAME
vmware-vm 5393 tibor  179u   BLK    2,0      9378 /dev/fd0
vmware-vm 5398 tibor  179u   BLK    2,0      9378 /dev/fd0
vmware-vm 5399 tibor  179u   BLK    2,0      9378 /dev/fd0
vmware-vm 5400 tibor  179u   BLK    2,0      9378 /dev/fd0
vmware-vm 5401 tibor  179u   BLK    2,0      9378 /dev/fd0
vmware-vm 5402 tibor  179u   BLK    2,0      9378 /dev/fd0
vmware-vm 5404 tibor  179u   BLK    2,0      9378 /dev/fd0
vmware-vm 5405 tibor  179u   BLK    2,0      9378 /dev/fd0
root@GOLDEN10:~# kill -9 5393
root@GOLDEN10:~# lsof /dev/fd0
root@GOLDEN10:~#
root@GOLDEN10:~# mount /dev/fd0
root@GOLDEN10:~#
root@GOLDEN10:~#

Maybe in your case vmware is sitting on your CDROM. Look for it.

I still could not find the final solution, this problem is repeating after rebooting the PC...

---

### Post by radiant chains on 2007-01-01
Still haven't figured out the problem... I've uninstalled VMWare and now any attempts to mount are met with: 

```
mount: special device /dev/hdc does not exist
```

---

### Post by radiant chains on 2007-01-01
Also, running a *dmesg | grep 'hdc'* now gives me:
```
[   25.378841]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
[    2.424000] hdc: TSSTcorpCD/DVDW TS-L532R, ATAPI CD/DVD-ROM drive
[    2.488000] hdc: ERROR, PORTS ALREADY IN USE
```

---

### Post by scanray on 2007-01-17
I have the same error:

hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

The situation is: I have installed kubuntu with no errors. My hd boot is a p-ata. Later, I have installed an s-ata drive. Now, the error appears.
After trying some settings with no results, I have changed in the bios of my PC under "IDE Configuration" the option "enhanced" to "compatible".
After that, no more erros, but, I cant see my s-ata disk.

Another thing: I have in another partition Mandriva. The same problem and the same solution. Posibly error of kernel.

I am continue searching another solution. :-D 

PD: soory for my english. :-|

---

