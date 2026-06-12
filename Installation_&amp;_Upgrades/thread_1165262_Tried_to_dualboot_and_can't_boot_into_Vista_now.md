---
title: "Tried to dualboot and can't boot into Vista now"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by mtngirl on 2009-05-20
I took a 64 bit Vista machine, followed the directions here ([http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)) and I cannot login to the Vista's partition anymore. On a reboot it shows the original BIOS menu which just gives the hard drive, CD drive, etc. If you pick the hard drive GRUB shows up and just shows Ubuntu as the option.  

Help?

(Also, the machine is no longer on the network as it was using an external wireless antena that Ubuntu doesn't seem to recognize ...)

Thanks!

---

### Post by The Real Dave on 2009-05-20
Its probable that your GRUB isnt set up right. Can you post the contents of ```
sudo gedit /boot/grub/menu.lst
```

Also, it doesnt seem as if your BIOS is booting the drive which contains GRUB first.

---

### Post by mtngirl on 2009-05-20
Thanks for the reply!

Here is /boot/grub/menu.lst

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c74f500e-8c53-4dd8-96e9-24a17a39539b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c74f500e-8c53-4dd8-96e9-24a17a39539b

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        c74f500e-8c53-4dd8-96e9-24a17a39539b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c74f500e-8c53-4dd8-96e9-24a17a39539b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        c74f500e-8c53-4dd8-96e9-24a17a39539b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c74f500e-8c53-4dd8-96e9-24a17a39539b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        c74f500e-8c53-4dd8-96e9-24a17a39539b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by mtngirl on 2009-05-20
If I do nothing, it flashes BIOS screen, GRUB and then boots into Ubuntu.

(I'd really like to have it booting to Vista as well as Ubuntu by this evening so that I can say "look at this, Ubuntu's awesome, but don't worry your Windows stuff is still all there if you need to get to it." :)

---

### Post by lindsay7 on 2009-05-20
I think you just need to edit your grub file to add the vista loader.  Since I do not know what partition is which I can only guess.  I you can post the results of type in terminal  "sudo fdisk -l" I can be sure but what you need to do is get into your grub menu by typing in the terminal 

"sudo gedit /boot/grub/menu.lst"


go to the very bottom and add these lines (I am guessing at the partition numbers, I need to see fdisk to be sure)

title Windows Vista
root (hd0,0)
makeactive
chainloader +1

save the file and reboot.  the part that says (hd0,0) is where windows is located.

---

### Post by mtngirl on 2009-05-20
From sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1967    15728640    7  HPFS/NTFS
/dev/sda3   *        1967       72726   568377340    7  HPFS/NTFS
/dev/sda4           72727       77825    40957717+   5  Extended
/dev/sda5           72727       77610    39230698+  83  Linux
/dev/sda6           77611       77825     1726956   82  Linux swap / Solaris

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80322801

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001    7  HPFS/NTFS

---

### Post by lindsay7 on 2009-05-20
Ok, I am still not sure which partition is going to be correct to load windows but we are down to three choices and I think it will be easier to do a trial and error then to do more diagnostics.

Go ahead and go the sudo gedit /boot/grub/menu.lst command in the terminal and add the lines a a laid out for you using (hd0,0) save the file and reboot. you should get the option to boot windows in the grub menu. Try it and see if it loads.  If it does great, if not go back to the grub menu i.e. sudo gedit boot/grub/menu.lst, and change the partition to (hd0,1) and save and reboot again.  If this does not work then try changing to (hd0,2) save and regoot.  These are the three possibilities and most likely the first should work.  When you get vista to boot. Let me know if Ubuntu also boots, we may need to do something on that too.

---

### Post by The Real Dave on 2009-05-20
Assuming that Vista is on the first partition of the first disk, it would be (hd0,1)

If Vista is on that second, 1TB one, it should be (hd1,1)

The best way to check this it to add the Vista option to GRUB as mentioned in the previous posts, and then, attempt to boot it from GRUB. If you get an error message, go back to the GRUB menu, select Vista, and and hit e to edit it. Go down to "root (hd0,0) and hit e again. Then play around with the disk numbering, trying out (hd0,1) (hd1,0) (hd1,1) etc. After you edit it to a different number, press Return, then b to attempt to boot it. Once you find the correct drive number, boot back into Ubuntu, ```
sudo gedit /booot/grub/menu.lst
``` and change it whichever disk number it was. Save and re-boot.

Not the most scientific way of doing it ;)

Its gotten me out of some GRUB errors :D Hope it works for you.

---

### Post by mtngirl on 2009-05-20
Ah! There was an external hard drive plugged in, so I unmounted it and we're down to one. I will try now.

Thanks so much!

---

### Post by mtngirl on 2009-05-20
Whoo-hoo!!

You guys are awesome. Thanks so much for your help! 

(In case any one cares, it was (hd0,2). And if anyone would prefer to use Vista, I think you should just have them compare boot times ...)

---

### Post by lindsay7 on 2009-05-20
To The Real Dave,

unless I am incorrect the numbering system for drives and partitions starts with 0 as the first drive and 0 as the first partition, so 

hd0,0 is the first drive, first partition
hd0,1 is the first drive, second partition
hd1,0 is the second drive, first partition
hd1,1 is the second drive, second partition
ect
ect
ect

so if th OP only has on system drive, then the operating system will be on 

hd0,0 or hd0,1 or hd0,2 as in her case.

---

### Post by lindsay7 on 2009-05-20
Good for you!!  Glad to help.

---

### Post by The Real Dave on 2009-05-21
> **lindsay7 said:**
> To The Real Dave,

unless I am incorrect the numbering system for drives and partitions starts with 0 as the first drive and 0 as the first partition, so 

hd0,0 is the first drive, first partition
hd0,1 is the first drive, second partition
hd1,0 is the second drive, first partition
hd1,1 is the second drive, second partition
ect
ect
ect

so if th OP only has on system drive, then the operating system will be on 

hd0,0 or hd0,1 or hd0,2 as in her case.

Yup, you are right, in Linux, it starts off with 0. I just got confused by the fact that he had an external drive mounted, which showed in fstab, so I wasnt sure which partition it was on :confused:

Thanks all the same though :D 

Glad to be of help mtngirl, enjoy dual booting :D Getting the benefits of both OS's on one system

---

