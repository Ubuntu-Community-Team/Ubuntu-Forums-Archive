---
title: "Feisty: Blacklisted modules loading"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by stoanhart on 2007-05-01
Hi everyone.

I have no idea if this is the right section of the forum, but I think it's close enough.

The problem is, my DVD drive has DMA disabled in feisty, which is due to the new libATA driver. I have googled around, and decided the best option would be to just disable libATA and use the old driver, since that worked just fine.

I added "blacklist libata" to the /etc/modprobe.d/blacklist file, and updated the initramfs (I even extracted it again, and checked the contents of it's blacklist file, which was updated). However, my system still uses the driver. I read somewhere on launchpad that blacklisting libata would cause the kernel to fall back on the old driver, but it seems this didn't work.

I have also tried moving the libata.ko file so it can't be found, hoping this would force the kernel to fall back on the old drivers. This just made my system unbootable.

Does anyone know how to force feisty to NOT use libata?

Thanks

---

### Post by kerry_s on 2007-05-01
Why not just use hdparm to turn dma on?

sudo gedit /etc/rc.local

hdparm -d1 /dev/hdc &

or

Oh, i forgot, you can also set hdparm in /etc/default/hdparm which would proably be best.

---

### Post by stoanhart on 2007-05-01
haha, yeah, I forgot to mention that part. 

```

$ sudo hdparm -d1 /dev/scd0 

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device


```

I've been looking on google and ubuntu related sites for a couple of hours, and there isn't really anything that can be done about that except use the old driver.

Thanks

Pascal

---

### Post by kerry_s on 2007-05-01
Okay, i see. 
Try> sudo hdparm -d1 /dev/scd

Did you try with the /hdc label?

---

### Post by Deksan on 2007-05-02
I have the same problem as well :( there is a bug in launchpad as well :

[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/110636](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/110636)

I got that for every hard disk i got :( (sda,sdb,sdc,sdd) :( Performance are really bad and it s not rare to have  50% iowait :(

---

### Post by stoanhart on 2007-05-02
There is no scd, just scd0. Also, hdc is not there either (since Feisty uses libATA, which assigns all hard drives as sd* and all cd drives as scd*).

Dekasn, sorry to hear that. At least I have DMA on my hard drive, so I can still use my computer most of the time. I've got a backup install of dapper too, but I need feisty for my Google SOC project, since I need up to date software.

Oh well, I can live with it for now.

---

### Post by kerry_s on 2007-05-02
> **stoanhart said:**
> There is no scd, just scd0. Also, hdc is not there either (since Feisty uses libATA, which assigns all hard drives as sd* and all cd drives as scd*).

Dekasn, sorry to hear that. At least I have DMA on my hard drive, so I can still use my computer most of the time. I've got a backup install of dapper too, but I need feisty for my Google SOC project, since I need up to date software.

Oh well, I can live with it for now.


Can you post your /etc/fstab?
What kind of drives do you have? sata or ide
How many drives do you have?

The cd will ethier be sdc/hdc but will be mounted in /media/sdc0 media/hdc0. It does not matter if hdc is not there, it is tthe original device name and can still be used, it's a backward compatiabilty thing. I don't think it's the driver, it's what your drive is seen as. unblacklist the libata and try my suggestions.

---

### Post by chalewa on 2007-05-02
> **kerry_s said:**
> Can you post your /etc/fstab?
What kind of drives do you have? sata or ide
How many drives do you have?

The cd will ethier be sdc/hdc but will be mounted in /media/sdc0 media/hdc0. It does not matter if hdc is not there, it is tthe original device name and can still be used, it's a backward compatiabilty thing. I don't think it's the driver, it's what your drive is seen as. unblacklist the libata and try my suggestions.

I guess I am confused on what you are suggesting as a solution to this problem...

---

### Post by kerry_s on 2007-05-02
> **chalewa said:**
> I guess I am confused on what you are suggesting as a solution to this problem...

Okay, what i am saying is if the drive has dma support, it can be turned on with hdparm. You just have to find the id that hdparm responds to, i have done it on a machine that was throwing up the same kind of errors. For instance if there's only 1 drive you don't need to add a # on the end, example: hdc0 is just hdc because a cd/dvd drive has no partions, so when you add a # it will fail, the hdc# is only shown in /media as the folder to mount it but not the actual device name. So as soon as i see the out put of fstab i can see what the /dev/? is for the cd/dvd and then running> sudo hdparm -d1 /dev/? < will turn on dma, can be checked with> sudo hdparm /dev/?

---

### Post by stoanhart on 2007-05-03
I'm pretty sure it is related to the driver. Here is the contents of /dev (with all the tty/pty stuff stripped out)

```

acpi
adsp
agpgart
audio
bus
cdrom    (points to /dev/scd0)
cdrw      (points to /dev/scd0)
console
core
disk
dsp
dvd
fd
full
fuse
hpet
initctl
input
kmem
kmsg
log
loop0
MAKEDEV
mem
mixer
net
null
nvidia0
nvidiactl
oldmem
port
ppp
psaux
ptmx
pts
ram0
ram1
ram10
ram11
ram12
ram13
ram14
ram15
ram2
ram3
ram4
ram5
ram6
ram7
ram8
ram9
random
rtc
scd0      <- DVD Drive
sda        <- Hard drive
sda1
sda2
sda3
sda4
sda5
sda6
sequencer
sequencer2
sg0
sg1
shm
snapshot
snd
sndstat
sr0
stderr
stdin
stdout
urandom
usbdev1.1_ep00
usbdev1.1_ep81
usbdev2.1_ep00
usbdev2.1_ep81
usbdev3.1_ep00
usbdev3.1_ep81
usbdev3.3_ep00
usbdev3.3_ep81
usbdev4.1_ep00
usbdev4.1_ep81
usbdev5.1_ep00
usbdev5.1_ep81
vcs
vcs1
vcs2
vcs3
vcs4
vcs5
vcs6
vcs7
vcs8
vcsa
vcsa1
vcsa2
vcsa3
vcsa4
vcsa5
vcsa6
vcsa7
vcsa8
watchdog
xconsole
zero

```

So, there is no hdc, as there should not be with libata. scd0 is the only option to try hdparm on, and it doesn't work. Besides, I have checked this out on other sites, and in the ubuntu bugs, where someone recommended to blacklist libata. Unblacklisting it won't make a difference, since it's being used anyways, despite the fact that it is being blacklisted. 

Here is the contents of fstab, in case you still need it:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=3a330183-b6ea-4c53-871c-8bb951e433fd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=5628999A289979A7 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=f71292bd-9e1d-4db2-826a-a74385176cc4 /media/other-linux ext3    defaults        0       2
# /dev/hda6
UUID=a15fb575-c489-43d0-b710-0a5828831ff4 /media/storage  ext3    defaults        0       2
# /dev/hda5
UUID=a85080c9-576a-406f-b28d-a8b4258f6b51 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

It's actually kind of strange that fstab would point to /dev/hdb when there is no such device. Even so, the drive works just fine, just no DMA.

So, does anyone have any idea how I can force the old driver to be used? Apparently, it is still included in Feisty, just not used by default. That would really be the easiest solution.

Pascal

---

### Post by kerry_s on 2007-05-03
Okay so your cdrom drive is  /dev/hdb, so using> sudo hdparm -d1 /dev/hdb < will give you dma on your cdrom drive, you can check it with> sudo hdparm /dev/hdb <and if it's set just add it to /etc/rc.local. It's showing as hdb because you have it set as the slave drive on a single ide cable.

Don't mess with /dev unless you want to toast your system, /dev is just that a list of devices. Your system is set up the normal way and it's not using scsi drivers, so only usb external drives will use th sdx  names on your system.

It's not that complicated unless you make it that way.

Also i would like to say it's my fault, i should have asked to see the file sooner. I just had surgery and are taking alot of meds, so i apologies if i seem a bit intolerant/off.

Here's my fstab for feisty incase you want to see, mine you i did some tweaking.->

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=785d88e5-4a57-4d97-a852-85a73bcde479 /               ext2    defaults,noatime,errors=remount-ro 0       1
# /dev/hda1
UUID=A6C0481CC047F0DB /media/Windows_XP     ntfs    users,noauto,noatime,nls=utf8,umask=007,gid=46 0       0
# /dev/hda2
UUID=FF7D-F8A2  /media/Storage     vfat    users,exec,noauto,noatime,utf8,umask=007,gid=46 0       0
# /dev/hda3
UUID=547d3947-508a-46db-8d07-0e834257b4e0 /media/Linux1     jfs     users,noauto,noatime        0       0
# /dev/hdd1
UUID=58bc17bd-ec8d-4f23-be7c-1609dfad6132 /media/Boot     ext2    users,noauto,noatime        0       0
# /dev/hdd2
/dev/hdd2 /media/Linux3     ext2     users,noauto,noatime        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by stoanhart on 2007-05-03
```

sudo hdparm -d1 /dev/hdb
/dev/hdb: No such file or directory

```

I gave you a list of my /dev folder, and told you there wasn't any hd* items. Why would your command work? I have two block devices: sda for my hard drive, and scd0 for my dvd drive, which is exactly how it should be with the new libATA driver. With libATA, all hard drives are sd*, whether they are scsi or not, and all optical drives are scd*, regardless of the interface. I'm not sure what interface my DVD drive is on, to be honest. I am using a laptop, so it is simply inserted into a bay. There are no master/slave jumpers, and no cables to be dealt with. I think internally, the motherboard uses SATA. And yes, I am quite aware what the /dev folder is. I don't have a lot of posts on the forum, but I am far from new to linux.

I appreciate that you are trying to help me, but it seems like you aren't really listening to the problem. You are just telling me to enable DMA, despite the fact that I have already explored that option, and it doens't work. I know how to use hdparm, hdparm simply isn't doing what I want it to. That's why I am asking how to properly disable libATA, not how to enable DMA. 

Pascal

---

### Post by kerry_s on 2007-05-03
Okay, i'm done.

---

### Post by chalewa on 2007-05-03
Pascal, just to verify, you are looking to blacklist the libATA driver, and then revert back to edgy's driver so that DMA can be enabled and  speed restored?

---

### Post by Deksan on 2007-05-04
If you got a solution for that i d be interested as well as i get poor hard disk performance. 
( created a thread here [http://ubuntuforums.org/showthread.php?t=432495)](http://ubuntuforums.org/showthread.php?t=432495)). From what i read libata set the parameters automatically for all the device /dev/sd??. It s maybe a good idea to check :
hdparm /dev/sd??
and 
hdparm -I /dev/sd??

The thing i have noticed is that whenever  I read from a hard disk i have a lot of cpu burnt into iowait. Maybe it s a controller issue ?

---

### Post by stoanhart on 2007-05-04
> Okay, i'm done.

Sorry if I sounded a bit aggressive, I didn't mean it that way :)

> Pascal, just to verify, you are looking to blacklist the libATA driver, and then revert back to edgy's driver so that DMA can be enabled and speed restored?

Exactly

> If you got a solution for that i d be interested as well as i get poor hard disk performance.
( created a thread here [http://ubuntuforums.org/showthread.php?t=432495)](http://ubuntuforums.org/showthread.php?t=432495)). From what i read libata set the parameters automatically for all the device /dev/sd??. It s maybe a good idea to check :
hdparm /dev/sd??
and
hdparm -I /dev/sd??

The thing i have noticed is that whenever I read from a hard disk i have a lot of cpu burnt into iowait. Maybe it s a controller issue ?

My sda device has all the parameters set automatically and correctly, as I have DMA on my hard drive. You are correct, libATA should set things correctly. Where I don't have DMA is scd0. Here's the hdparm results:

```
$ hdparm /dev/scd0 

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

$ hdparm -I /dev/scd0

/dev/scd0:
 HDIO_DRIVE_CMD(identify) failed: Input/output error

```

CPU usage is normal when no DMA is used. I copied a few hundred MB of data from a cd the other day, and my computer was almost useless during the process. I remember the same thing when I still used Windows. I had a hard drive that, for some reason, would only run in PIO mode. Whenever any intensive activity occurred on that drive, the computer would be 100% utilized by that task alone.

Pascal

---

### Post by chalewa on 2007-05-04
Ok, so essentially what needs to happen is that somehow these devices need to be renamed to what they were in edgy...

/dev/hdXX instead of /dev/sdXX

this will allow for hdparm to turn the dma on in these devices, thus restoring the speed. I as well tried to blacklist the libATA driver, but no dice.

---

### Post by Deksan on 2007-05-04
Pascal,

Did you try to add  combined_mode=libata to your kernel parameter ( /boot/grub/menu.lst) it seems to have improved performance for me ?

---

### Post by stoanhart on 2007-05-05
> **chalewa said:**
> Ok, so essentially what needs to happen is that somehow these devices need to be renamed to what they were in edgy...

/dev/hdXX instead of /dev/sdXX

this will allow for hdparm to turn the dma on in these devices, thus restoring the speed. I as well tried to blacklist the libATA driver, but no dice.

Yup. Using the old driver should cause the devices to be renamed. I tried booting Feisty with a Dapper kernel. Needless to say, it didn't work out very well. However, I did get to a root shell, and the devices were hda and hdc.

> Did you try to add combined_mode=libata to your kernel parameter ( /boot/grub/menu.lst) it seems to have improved performance for me ?

Yes, I did try that. Unfortunately, it made no difference :(

I just found this on the kernel mailing lists (from when the patch to provide the combined_mode option was added):

> Yep, worked like a charm. As it stands, I can't play DVDs on my laptop,
but with this patch I can set combined_mode=libata and
libata.atapi_enabled=1 and DVDs are no longer choppy. It's great!

Going to go try that now! Wish me luck!

---

### Post by stoanhart on 2007-05-05
Well, the kernel complained that "libata.atapi_enabled=1" was an unknown boot option. And hdparm still gives the same errors on my DVD drive. However, I just tried to watch a DVD, and it was smooth! I think i'll just leave it like this for a bit, and see how it goes.

Pascal

---

### Post by chalewa on 2007-05-05
> **stoanhart said:**
> Well, the kernel complained that "libata.atapi_enabled=1" was an unknown boot option. And hdparm still gives the same errors on my DVD drive. However, I just tried to watch a DVD, and it was smooth! I think i'll just leave it like this for a bit, and see how it goes.

Pascal

any report on whether or not this helps with burn speeds?

---

