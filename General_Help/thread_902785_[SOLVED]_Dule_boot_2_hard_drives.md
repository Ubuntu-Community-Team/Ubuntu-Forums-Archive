---
title: "[SOLVED] Dule boot 2 hard drives"
date: 2008-08-27
forum: General Help
---

### Post by Kilroth on 2008-08-27
Okay 

I have Ubuntu 8.4 installed on my 500GB  SATA Drive add I have a Blank 80GB SATA Hard Drive that I would like to install Windows XP on I Understand that that the easiest way is to unplug the Ubuntu drive and just do a fresh install on the 80GB Hard Drive But I was told that I would have to Do something to the GRUB BOOT LOADER and I don't know what so any help would be nice thanks [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by Hellishcross on 2008-08-27
I would say do a search on dual booting using XP's NTLDR instead of GRUB because GRUB can mess with the windows boot and cause it to not work. This happened to me and that's the advice I was given. Technically what this does is let NTLDR choose which OS to load and then if you choose Linux it hands it over to Grub or LILO (on a different drive than XP so it leaves XP alone). 

Although in my situation I already had XP (which was crucial for my schoolwork) on my main drive and I wanted to try Ubuntu on my spare 80GB drive. 

**Here are some guides that I found:**

[http://www.linux.com/feature/113945]("http://www.linux.com/feature/113945")
[http://jaeger.morpheus.net/linux/ntldr.php]("http://jaeger.morpheus.net/linux/ntldr.php")
[http://highlandsun.com/hyc/linuxboot.html]("http://highlandsun.com/hyc/linuxboot.html")

---

### Post by caljohnsmith on 2008-08-28
> **Hellishcross said:**
> I would say do a search on dual booting using XP's NTLDR instead of GRUB because GRUB can mess with the windows boot and cause it to not work. This happened to me and that's the advice I was given. 
When you say "Grub can mess with the windows boot and cause it to not work", if you mean that Grub can replace the Windows boot loader in the MBR, that is true, but under any normal circumstances Grub will never cause Windows to "not work". If you replace the Windows MBR with Grub, then all you have to do is put an entry for Windows in Grub's menu.lst and you can boot Windows just fine. :)

Keeping the Windows MBR and modifying the Windows boot.ini file to boot Grub (as you allude to) is definitely another option; but simply using Grub to boot all your operating systems is usually the easiest and best method for most people, because if you use the "modified boot.ini" approach, your whole system can become unbootable if anything happens to your Windows partition. Whereas if you use Grub, you would still be able to boot into Ubuntu.
> **Kilroth said:**
> Okay 

I have Ubuntu 8.4 installed on my 500GB  SATA Drive add I have a Blank 80GB SATA Hard Drive that I would like to install Windows XP on I Understand that that the easiest way is to unplug the Ubuntu drive and just do a fresh install on the 80GB Hard Drive But I was told that I would have to Do something to the GRUB BOOT LOADER and I don't know what so any help would be nice thanks [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
Yes, the safest thing to do is disconnect your Ubuntu HDD when you go to install Win XP, but it is not absolutely necessary. About the worst thing that could happen is if Win XP decides to install its boot loader into the MBR of the Ubuntu HDD instead of its own HDD, but you can easily reinstall Grub back into the Ubuntu HDD's MBR with just a few simple commands from the Ubuntu Live CD, and all is well again in LinuxLand.

Which HDD do you plan on booting from on startup? If you boot from the Ubuntu HDD, it is really easy to add an entry into your Grub's menu.lst to boot Windows on your other HDD. That's the easiest. If for some reason you have to boot off the Windows HDD on startup, it won't be as easy making Ubuntu a booting option, but can certainly be done.

---

### Post by Wickd on 2008-08-28
I agree with above. Unplug the big one, install xp on small one and add to grub bootloader. Easy peasy

---

### Post by Kilroth on 2008-08-29
Ubuntu will be my primary so what is the comand I have to type in to add the MBR to my GRUB.lst

---

### Post by Kilroth on 2008-08-31
I am going to take the safe way out and disconnect the Ubuntu drive first. But what I need to know is what do I add to my grub menu.lst and how would I go about doing this.


Once you get your Windows installed, just add the following to your Grub menu.lst:

[CODE]
title Windows
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1[CODE]

If Windows is on the 1st partition of the 2nd HDD (which I assume it is), then above use (hd1,0). If it is on 2nd partition, use (hd1,1).

---

### Post by Kilroth on 2008-08-31
Ok I ran in to a problem I did this exactly as you posted and it does not work. What it does do is just flickers and goes back to the grub menu my cursor is still on the option Windows.

sudo fdisk -lu
cat /boot/grub/menu.lst

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0dbd836

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   775361159   387680548+  83  Linux
/dev/sda2       775361160   781417664     3028252+   5  Extended
/dev/sda5       775361223   781417664     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004e70b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156296384    78148161    7  HPFS/NTFS

---

### Post by caljohnsmith on 2008-08-31
I think I know what your problem is, Kilroth, but to confirm please also post the output of:
```
cat /boot/grub/menu.lst
```

---

### Post by Kilroth on 2008-08-31
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=b0b1b450-a02f-4ea3-a39f-a135f525d630 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b0b1b450-a02f-4ea3-a39f-a135f525d630 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b0b1b450-a02f-4ea3-a39f-a135f525d630 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b0b1b450-a02f-4ea3-a39f-a135f525d630 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=b0b1b450-a02f-4ea3-a39f-a135f525d630 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=b0b1b450-a02f-4ea3-a39f-a135f525d630 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=b0b1b450-a02f-4ea3-a39f-a135f525d630 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b0b1b450-a02f-4ea3-a39f-a135f525d630 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

#title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b0b1b450-a02f-4ea3-a39f-a135f525d630 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title 		Windows XP
root  		(hd1,0)	
map		(hd0) (hd1)
map		(hd1) (hd0)
makeactive
chainloadr +1

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by caljohnsmith on 2008-08-31
> **Kilroth said:**
> 
title 		Windows XP
root  		(hd1,0)	
map		(hd0) (hd1)
map		(hd1) (hd0)
makeactive
[COLOR="Red"]chainloadr[/COLOR] +1

I think you have a small typo: should be "chainloader" and not "chainloadr". Give that a try, and I think that may be all you need to boot Windows.

---

### Post by Kilroth on 2008-09-01
Thanks it worked like a charm I am curious if this would work for Vista but I'm not going to tempt fate if someone is willing to try please let me know

---

### Post by Kilroth on 2008-09-01
Thank it worked like a charm. I am curious if it would work fo Vista. I am not going to push my luck if someone wants to try let me know

---

### Post by caljohnsmith on 2008-09-01
> **Kilroth said:**
> Thank it worked like a charm. I am curious if it would work fo Vista. I am not going to push my luck if someone wants to try let me know
Yes, you can use the same syntax in Grub's menu.lst to boot Vista. Glad it's working for you now. :)

---

