---
title: "[SOLVED] GParted made XP fail to boot after resize"
date: 2008-09-03
forum: General Help
---

### Post by Pro-reason on 2008-09-03
I normally dual-boot between Ubuntu and Windows XP (to play *Europa Barbarorum*), but recently I decided to resize my XP partition in order to make room for a third system: OpenSolaris.

XP won't boot any more.

I can still mount the XP partition (which is formatted as NTFS), and see that all the files seem fine.

The MBR is not the problem, because another drive is the boot drive, with GRUB, and my Ubuntu installation.

I ran CHKDSK from the XP installation CD.  It found and fixed a couple of errors, but this had no effect on booting.

I suppose that GParted's NTFS support must be a bit shaky still.  What damage could it have done?  Any idea about how to reverse it?  I don't want to have to reinstall.

P.S. I had trouble with OpenSolaris so I deleted it and put the XP partition back how it was.  Still won't boot.

---

### Post by cdtech on 2008-09-03
Could you post the output of:
```
sudo fdisk -l
```
and:
```
/boot/grub/menu.lst
```

---

### Post by Pro-reason on 2008-09-03
I doubt this info will do any good.

```
Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f340f34

   Device Boot      Start         End      Blocks   Id  System
[B]/dev/sda1               1         127     1020096   82  Linux swap / Solaris
/dev/sda2   *         128        4500    35126122+   7  HPFS/NTFS[/B]

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26bc26bb

   Device Boot      Start         End      Blocks   Id  System
[B]/dev/sdb1   *           1         255     2048256   82  Linux swap / Solaris
/dev/sdb2             256       19457   154240065    f  W95 Ext'd (LBA)
/dev/sdb5             517       13428   103715640   83  Linux
/dev/sdb6             256         516     2096419+  82  Linux swap / Solaris
/dev/sdb7           13429       19457    48427911   83  Linux[/B]

```

```

default		0
timeout		2
#hiddenmenu
color cyan/blue white/blue
splashimage=(hd0,6)/boot/grub/splashimages/Erin-widescreen.xpm.gz


## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret


### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hdc7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=true

## ## End Default Options ##
[B]
title		Ubuntu 8.04.1
root		(hd0,6)
kernel		/vmlinuz root=LABEL=Ubuntu ro splash savedefault vga=normal
initrd		/initrd.img
savedefault[/B]

### END DEBIAN AUTOMAGIC KERNELS LIST

title		GRUB-invaders
root		(hd0,6)
kernel		/boot/invaders  
boot
[B]
title XP
root (hd1,1)
chainloader +1
savedefault
makeactive[/B]

```

---

### Post by bigken on 2008-09-03
did you defrag the windows partition 1st ?

you could also try the [UBCD]("http://www.ubcd4win.com/") and use the registry wizard to restore to an earlier date

---

### Post by Pro-reason on 2008-09-03
> **bigken said:**
> did you defrag the windows partition 1st
That doesn't help fix the problem, does it?

I didn't defrag immediately before the operation, but I defrag most times that I use Windows, so the data is kept towards the beginning of the drive, and should be relatively unfragmented.  GParted would have not had to move too many blocks of data to the beginning of the drive.  I do realise that NTFS is a Microsoft trade secret, so any operations on an NTFS drive from Linux run the risk of data loss.  I'm just surprised that the drive seems intact, and yet Windows won't boot.

---

### Post by bigken on 2008-09-03
thats the cause of your problem you should always defrag at least twice before you resize your partition


try running chkdsk /p /r


as a last resort you could do a repair install of windows and then reinstall grub boot loader [http://www.howtogeek.com/howto/ubunt...-wipes-it-out/](http://www.howtogeek.com/howto/ubunt...-wipes-it-out/)

---

### Post by plucky on 2008-09-03
Fellas,

What is this trying to boot?

```

title XP
root (hd1,1)
chainloader +1
savedefault
makeactive
```

```
/dev/sdb2             256       19457   154240065    f  W95 Ext'd (LBA)
```

and what is this?

```
[color=red]/dev/sda1               1         127     1020096   82  Linux swap / Solaris[/color]
/dev/sda2   *         128        4500    35126122+   7  HPFS/NTFS

```


Something is not right

Good Luck

---

### Post by Pro-reason on 2008-09-03
> **bigken said:**
> thats the cause of your problem you should always defrag at least twice before you resize your partition
That shouldn't be a problem.  Any other filesystem requires no previous defragging.  I appreciate that Linux NTFS support is shaky, and that the more you defrag, the lower the chance of a screw-up, but the drive was reasonably unfragmented.  The resizing may or may not have been more successful with further defragging.  This doesn't get me closer to a fix.

> **bigken said:**
> 
try running chkdsk /p /r
I've already mentioned that I did that.

> **bigken said:**
> 
as a last resort you could do a repair install of windows and then reinstall grub boot loader [http://www.howtogeek.com/howto/ubunt...-wipes-it-out/](http://www.howtogeek.com/howto/ubunt...-wipes-it-out/)
I know what the last resort is.  I mentioned that I'm looking for an alternative to the last resort.


> **plucky said:**
> Fellas,

What is this trying to boot?

```

title XP
root (hd1,1)
chainloader +1
savedefault
makeactive
```
Windows.  It has always worked like that.


> **plucky said:**
> 
```
/dev/sdb2             256       19457   154240065    f  W95 Ext'd (LBA)
```

and what is this?
That's an extended partition, which contains several logical partition.  They are the main ones that I use.

> **plucky said:**
> 
```
[color=red]/dev/sda1               1         127     1020096   82  Linux swap / Solaris[/color]
/dev/sda2   *         128        4500    35126122+   7  HPFS/NTFS

```

That's a swap-space, and my NTFS-formatted Windows drive.  The one with the problem.

Thanks, everyone.

---

### Post by cdtech on 2008-09-03
I'm guessing the Windows boot.ini file. Since you moved the XP partition the boot.ini file is searching the wrong partition.

Try mounting the Windows partition and looking at the boot.ini file.

---

### Post by bigken on 2008-09-03
did you run chkdsk with the /p /r the only alternative is try using UBCD

---

### Post by Pro-reason on 2008-09-03
> **cdtech said:**
> I'm guessing the Windows boot.ini file. Since you moved the XP partition the boot.ini file is searching the wrong partition.

Try mounting the Windows partition and looking at the boot.ini file.
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
multi(0)disk(1)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
multi(1)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
multi(1)disk(1)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
multi(1)disk(1)rdisk(1)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

There was originally just one option in there, but I tried a few things in an effort to make it boot.

Unfortunately, it never gets to the selection screen that that file generates.

What else does NTLDR need in order to start the system?

Edit: the boot sector (MBR) of sda is not in use, because I'm using GRUB (which is installed to the MBR of sdb).  However, the boot sector of the sda2 partition may be relevant here.  Do I have to fix it in some way for Windows to boot?

---

### Post by Etirn on 2008-09-03
title XP
root (hd1,1)
chainloader +1
savedefault
makeactive

shouldent this be 

title XP
root (hd**0**,1)
chainloader +1
savedefault
makeactive

---

### Post by dodle on 2008-09-03
I had the same problem the first time that I resized a Windows partition with Gparted.  I didn't find an answer for it but I have a hypothesis as to why this happens, because I have resized nfts partitions successfully without any problems.  

My Hard Drive started out as a single partition:
[IMG]http://www.freewebs.com/jordansroom/01.png[/IMG]

The first time I resized it, I did it like this:
[IMG]http://www.freewebs.com/jordansroom/02.png[/IMG]

I believe most of Windows' system files are stored toward the inside of the disk (the left side of the partition map), I'm guessing some of those files were corrupted somewhere while gparted was moving them around and I wasn't able to boot in again.  I had to reinstall my system.  

The next time I resized my HD from the outside:
[IMG]http://www.freewebs.com/jordansroom/03.png[/IMG]

This left Windows' system files alone and I was able to boot into it with no problems.  Unfortunately, this doesn't solve the problem of fixing the already resized partition, but it's a good way to prevent it from happening again.  But what cdtech said sounds like it is worth a try, from what you posted it looks like grub says that windows in on hd1.  Your boot.ini file is probably looking for it on hd0..... or does grub bypass boot.ini?  Anyway, good luck.

Edit:  It took me a while to write this and make the visuals, so I missed some posts.

---

### Post by Pro-reason on 2008-09-03
I've just gone into the BIOS, and changed the default boot device.

So now the computer looks at the MBR of the Windows drive rather than the MBR of the Ubuntu drive (which uses GRUB).

It boots just fine, going to the OS choices menu laid out in boot.ini.  I'm able to choose the first option and start Windows XP.  Success.

This confirms that my Windows installation is perfectly fine.  However, I want to be able to boot into Ubuntu.  I could install GRUB onto the MBR of the Windows drive, but there is no guarantee that it would successfully boot Windows.

It seems clear that Windows simply got confused about where partitions were.  It is more fragile than Linux in this regard.

Surely there is some file I can edit so that Windows will successfully boot even if the drives are not in the order it currently expects them to be in.

---

### Post by Pro-reason on 2008-09-03
> **Etirn said:**
> title XP
root (hd1,1)
chainloader +1
savedefault
makeactive

shouldent this be 

title XP
root (hd**0**,1)
chainloader +1
savedefault
makeactive

You have a point, but no, that is not it.

If Windows were located on (hd0), then the entry that points at (hd0) to start Ubuntu would fail.  And it does not fail.  So, (hd1) must be the correct drive.

I know that *sda* ought to correspond to (hd0) and *sdb* ought to correspond to (hd1), but it is not always so.

GRUB and Linux are disagreeing about which drive is the first one.

Windows doesn't know what to do.

---

### Post by mixmaster on 2008-09-03
In the days of my youth, micros**t operating systems always had to be on the first (primary) partition.  From habit I've always set my machines up that way so I don't know if that is the case nowadays.

In your case, I would move windows to the beginning of sda1 and fix your boot order so that sda1 and hd0 are the same thing and that sda1 is the default boot device.  I think anything else is likely to cause grief in the long term (on one occasion grub managed to point my windows boot record to the manufacturers recovery partition, which was not a good thing).

---

### Post by Pro-reason on 2008-09-03
OK, I decided to try keeping the Windows drive as the boot drive, which means installing GRUB to its MBR.

I made the necessary adjustments in /boot/grub/menu.lst to make things point at the right drives.  I checked /etc/fstab to make sure nothing needed changing there.

The system now boots into Windows or Ubuntu perfectly.  I bet that I could try OpenSolaris again, and have more luck installing it this time.

Thanks to everyone for their suggestions, although I pretty much fixed it myself.

The moral of the story is that Windows can get confused about what drive is what, if you move things around.  Linux is more flexible.  Therefore, for a dual-boot system, you have to indulge Windows like a spoilt child, and let it have its way.  Order the drives however Windows wants them, and then make Linux accept that order too.

---

