---
title: "Problems putting Windows drive back into system."
date: 2006-01-18
forum: Hardware &amp; Laptops
---

### Post by siorai on 2006-01-18
Firstly, I know, I know.. This is pretty much well blasphemy. Until Cedega gets more on the ball though, Actually having Windows available is going to be the only way to play certain games without a totally headache to get them working.

Here's the story: First, I had the one drive with XP on it. On a second drive I then installed Ubuntu and had a dual boot for a short while. Once I was comfortable enough in Ubuntu, I took out the Windows drive and installed grub onto the Ubuntu drive leaving me with Ubuntu as my only OS. I've been having the desire to play a couple of games (Halflife2 and Battlefield2) since I got a new widescreen monitor.

I was thinking that I could simply put the Windows drive back in (it still has Windows on it, I didn't format it), modify my menu.lst accordingly and be back with a dual boot for those moments of gaming weakness. It couldn't be so easy though. 

I installed the drive, checked that it was being recognized properly in the BIOS and tried to boot. No luck. Grub gives me an Error 17. I figure this might very well be due there actually being grub on the Windows drive? If so, is there any way around this? I'd rather not have to reinstall Windows on that drive and go through all that if I can avoid it. I guess if need be, I can do without those games, but I'd really rather not..

---

### Post by vruum on 2006-01-19
could you maybe give a little more info? perhaps a short history of how your drives have been seated in the system. 
If you set your bios to boot from the ubuntu drive, will it boot? 
If you're still able to boot ubuntu it might be as simple as doing [this]("http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation")
and tweaking it to your setup. 
It might be even simpler, it might just be a matter of tweaking the menu.lst or adding the right windows reference to it. so, could you post your menu.lst and also the output of 
```
 sudo fdisk -l 
```

---

### Post by lha on 2006-01-19
Please give a more detailed list of things you have done dual-booting and removing Windows drive. (Especially how you had configured your hd's during each step.) Please also post the output of
```
cat /boot/grub/menu.lst
``` and
```
sudo fdisk -l
```
Also, please tell the BIOS boot order you used during different phases.

---

### Post by siorai on 2006-01-19
cat /boot/grub/menu.lst :
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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
## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-686-smp 
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-686-smp
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-686-smp (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-686-smp root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.12-10-686-smp
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin  
boot

title           Windows XP Pro
root            (hd1,0)
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```


sudo fdisk -l :
```
Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hdc2            1276       14945   109804275    f  W95 Ext'd (LBA)
/dev/hdc5            1276       14945   109804243+   7  HPFS/NTFS

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9821    78887151   83  Linux
/dev/sda2           10200       12748    20474842+   c  W95 FAT32 (LBA)
/dev/sda3           12749       36483   190651387+   7  HPFS/NTFS
/dev/sda4            9822       10199     3036285   82  Linux swap / Solaris

Partition table entries are not in disk order
```

So I'm a fair bit closer now. I didn't realize that in the BIOS, not only did I have to set the drive to boot from, but I also needed to set which drive was considered to be first. Now with that sorted out, I can boot normally and get into Ubuntu fine. I can't boot into XP though. I'm at a bit of a loss now. I thought that the grub entry for the XP root should be fine, but obviously it isn't. The odd thing is that when I get to the grub list, if I choose to edit the XP root line and use tab, it says my only options for the partition to use are 1 and 4. So it's not even letting me choose partition 0. :confused:

---

### Post by lha on 2006-01-20
[QUOTE=siorai]

So I'm a fair bit closer now. I didn't realize that in the BIOS, not only did I have to set the drive to boot from, but I also needed to set which drive was considered to be first. Now with that sorted out, I can boot normally and get into Ubuntu fine. I can't boot into XP though. I'm at a bit of a loss now. I thought that the grub entry for the XP root should be fine, but obviously it isn't.[/QUOTE]

Please change this
```
title           Windows XP Pro
root            (hd1,0)
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```
into
```
### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows XP Pro
root            (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader     +1

```

[QUOTE=siorai]
The odd thing is that when I get to the grub list, if I choose to edit the XP root line and use tab, it says my only options for the partition to use are 1 and 4. So it's not even letting me choose partition 0. :confused:[/QUOTE]

That sounds really odd to me, too. It can indicate a harder problem that I was expecting. Hopefully those changes in menu.lst are enough.

---

### Post by siorai on 2006-01-20
[QUOTE=lha]Please change this
```
title           Windows XP Pro
root            (hd1,0)
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```
into
```
### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows XP Pro
root            (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader     +1

```



That sounds really odd to me, too. It can indicate a harder problem that I was expecting. Hopefully those changes in menu.lst are enough.[/QUOTE]

That did the trick. Thanks. :D I never thought of that because previously the Windows drive was the primary drive so it wasn't needed. Now that it is the secondary drive, obviously it is.

---

