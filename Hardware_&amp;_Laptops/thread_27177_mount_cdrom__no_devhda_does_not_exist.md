---
title: "mount cdrom : no /dev/hda does not exist"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by ggnore on 2005-04-15
Hello.

I have a computer With only one ide map. there are a dvd-rom and a cd-rom plugged on it. I also have a SATA hard drive.

When i try to mount a cd to upgrade to hoary 5.04, it doesnt work

here is what i get:

```
#mount /media/cdrom
mount: special device /dev/hda does not exist

# ls /dev/hd*
ls: /dev/hd*: no such file or directory

# ls /dev
# ls /dev
adsp      full     ram15    stdout  tty29  tty50   ttyS14  ttyS36  urandom
agpgart   i830     ram2     tty     tty3   tty51   ttyS15  ttyS37  vcs
audio     initctl  ram3     tty0    tty30  tty52   ttyS16  ttyS38  vcs1
console   input    ram4     tty1    tty31  tty53   ttyS17  ttyS39  vcs2
core      kmem     ram5     tty10   tty32  tty54   ttyS18  ttyS4   vcs3
dri       kmsg     ram6     tty11   tty33  tty55   ttyS19  ttyS40  vcs4
dsp       log      ram7     tty12   tty34  tty56   ttyS2   ttyS41  vcs5
fd        lp0      ram8     tty13   tty35  tty57   ttyS20  ttyS42  vcs6
fd0       MAKEDEV  ram9     tty14   tty36  tty58   ttyS21  ttyS43  vcs7
fd0u1040  mapper   random   tty15   tty37  tty59   ttyS22  ttyS44  vcsa
fd0u1120  mem      rtc      tty16   tty38  tty6    ttyS23  ttyS45  vcsa1
fd0u1440  mixer    sda      tty17   tty39  tty60   ttyS24  ttyS46  vcsa2
fd0u1600  null     sda1     tty18   tty4   tty61   ttyS25  ttyS47  vcsa3
fd0u1680  port     sda2     tty19   tty40  tty62   ttyS26  ttyS48  vcsa4
fd0u1722  psaux    sda5     tty2    tty41  tty63   ttyS27  ttyS49  vcsa5
fd0u1743  ptmx     sda6     tty20   tty42  tty7    ttyS28  ttyS5   vcsa6
fd0u1760  pts      sda7     tty21   tty43  tty8    ttyS29  ttyS50  vcsa7
fd0u1840  ram0     sda8     tty22   tty44  tty9    ttyS3   ttyS51  xconsole
fd0u1920  ram1     sda9     tty23   tty45  ttyS0   ttyS30  ttyS52  zero
fd0u360   ram10    shm      tty24   tty46  ttyS1   ttyS31  ttyS53
fd0u720   ram11    snd      tty25   tty47  ttyS10  ttyS32  ttyS6
fd0u800   ram12    sndstat  tty26   tty48  ttyS11  ttyS33  ttyS7
fd0u820   ram13    stderr   tty27   tty49  ttyS12  ttyS34  ttyS8
fd0u830   ram14    stdin    tty28   tty5   ttyS13  ttyS35  ttyS9

# cat /etc/fstab
...
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
...

# cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a "#", and everything on the line after them are ignored.

sd_mod
psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp


```

I really dont know what i should do.

I think there is a problem with udev, but i'm not sure at all.

May somebody help me ?  :???:

I found 2 very strange things:

```
#dmesg | grep ide
ide0: I/O resource 0x1F0-0x1F7 not free.
ide0: ports already in use, skipping probe
ide1: I/O resource 0x170-0x177 not free.
ide1: ports already in use, skipping probe

```


I tried to use MAKEDEV hd, MAKEDEV hda, ... i think that was stupid

```
# ls /media/
cdrom    hda1   hda15  hda20  hda8   hdb12  hdb18  hdb5  sg1   sg15  sg6
cdrom0   hda10  hda16  hda3   hda9   hdb13  hdb19  hdb6  sg10  sg16  sg7
cdrom1   hda11  hda17  hda4   hdb    hdb14  hdb2   hdb7  sg11  sg2   sg8
floppy   hda12  hda18  hda5   hdb1   hdb15  hdb20  hdb8  sg12  sg3   sg9
floppy0  hda13  hda19  hda6   hdb10  hdb16  hdb3   hdb9  sg13  sg4
hda      hda14  hda2   hda7   hdb11  hdb17  hdb4   sg0   sg14  sg5

```


Shouldnt all these things be in /dev ?!
Should i destroy everything that is not cdrom, cdrom0, cdrom1, floppy and floppy0 ?

---

### Post by ggnore on 2005-04-15
it seems to be related to that problem:
[bug with ata_piix](//ubuntuforums.org/archive/index.php/t-18808.html)

---

