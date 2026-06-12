---
title: "Grub on wrong drive (!?) + dual boot questions"
date: 2008-08-07
forum: General Help
---

### Post by Culito on 2008-08-07
Hey y'all,
I have two hard drives on my system now, one just for misc. storage and one for my main drive.
I'm planning on replacing my secondary storage drive with a larger one, and using it for a separate Windows XP setup.
However, when I switched out my second drive, the computer wouldn't boot!  It turns out, for some reason, Grub is not on my main drive; it's on the smaller secondary drive that I need to replace!
So what I need to do is install Grub on my main drive...so I can install XP on the other new drive I just got.

Any tips on how to do this?  I'd prefer not to mess with my current Ubunbu install if I don't have to (aside from installing Grub, of course!)

And then, how would I set up Windows on the other?

Many thanks,
-C

---

### Post by logos34 on 2008-08-07
simply reinstall grub from live cd (see link my signature)

---

### Post by Culito on 2008-08-08
Thanks for the reply.
I went through the procedure and I'm suitably confused, of course...

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 /               ext3    defaults,erro$
# /dev/sda5
UUID=101d4077-f824-41bb-9196-16fef228a962 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,auto     0       0
##/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /media/music    vfat    rw,user
```

/dev/sdb1 is where grub is at right now.
/dev/sda1 (or is id sda5?) is where my ubuntu installation is.

Output of Grub:
```
grub> find /boot/grub/stage1
 (hd1,0)
```

I tried setting up grub on hd0 and hd1, and my computer will still only boot from sdb1.

Not sure what to try next.  This is the first time I've messed with this stuff...not sure how /sdb1 and /sda1 translate into hard drive numbers.

Thanks,
-C

---

### Post by logos34 on 2008-08-08
> **Culito said:**
> 
/dev/sda1 (or is id sda5?) is where my ubuntu installation is.

Output of Grub:
```
grub> find /boot/grub/stage1
 (hd1,0)
```I **tried setting up grub on hd0 and hd1**, and my computer will still only boot from sdb1.

sda1 is root partition

you have to edit menu.lst to match.

gksudo gedit /boot/grub/menu.lst

-change 'groot' and 'root' lines to (hd[COLOR=Red]0[/COLOR],0)

Reboot.  If the other drive is still connected, enter the Bios and set the ubuntu drive first.

---

### Post by caljohnsmith on 2008-08-08
> **Culito said:**
> Hey y'all,
I have two hard drives on my system now, one just for misc. storage and one for my main drive.
I'm planning on replacing my secondary storage drive with a larger one, and using it for a separate Windows XP setup.
However, [COLOR="Blue"]when I switched out my second drive, the computer wouldn't boot[/COLOR]!  It turns out, for some reason, Grub is not on my main drive; it's on the smaller secondary drive that I need to replace!
[COLOR="Blue"]So what I need to do is install Grub on my main drive[/COLOR]...so I can install XP on the other new drive I just got.

Any tips on how to do this?  I'd prefer not to mess with my current Ubunbu install if I don't have to (aside from installing Grub, of course!)

And then, how would I set up Windows on the other?

Many thanks,
-C
Logos34, from Culito's post above it sounds like what he wants to do is install Grub on his main HDD (hd0), and be able to use it *while his secondary HDD is disconnected*. Is this correct, Culito?

If that is true, he will need some place on his main HDD for the Grub configuration files in /boot/grub. He could do like I have done, and create a small partition on the main HDD, say 50 MB, for his /boot/grub files. That way he will have Grub installed entirely to the main HDD, and disconnecting his secondary HDD will not cause him problems since Grub will be independent of his secondary HDD. Also, Grub will be entirely independent of all his operating systems.

Would the above scenario work for you, Culito, or did I misinterpret what you said?

---

### Post by logos34 on 2008-08-08
> **caljohnsmith said:**
> Logos34, from Culito's post above it sounds like what he wants to do is install Grub on his main HDD (hd0), and be able to use it *while his secondary HDD is disconnected*....

If that is true, he will need some place on his main HDD for the Grub configuration files in /boot/grub. He could do like I have done, and create a small partition on the main HDD, say 50 MB, for his /boot/grub files. That way he will have Grub installed entirely to the main HDD, and disconnecting his secondary HDD will not cause him problems since Grub will be independent of his secondary HDD. 

You misunderstand about how grub works.  Grub is installed on his main ubuntu drive (otherwise he wouldn't be able to boot into it at all!)...The only thing that's on the secondary storage disk is the tiny grub stage1/1.5 file on the **MBR**...it points to /boot/grub on the ubuntu disk, where it fetches the menu.lst at boot.  All Culito needs to do is write the grub bootloader code to the MBR of the ubuntu disk, then edit the 'root' lines in menu.lst to reflect the new location of the ubuntu drive as the boot disk -- i.e. (hd**0**)...

---

### Post by Culito on 2008-08-08
cal, that is exactly the scenario.
This is what I'm doing:

```
sudo grub
find /boot/grub/stage1
```

output:
(hd1.0)

```
root (hd1,0)
setup (hd0)
```

output:
Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd1,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

Then I change my menu.lst groot and root entries to hd0,0...and no go.

It will still only boot if I select my secondary hard drive to boot from, and then I have to select the recovery kernel (set for hd1,0 in menu.lst) because it cant find the files in hd0,0....

That's all I can figure out for now...

---

### Post by caljohnsmith on 2008-08-08
Logos34, please correct me if I'm wrong, but here is how I understand it from the info Culito provided:
[LIST]
[*]According to his fstab, Ubuntu is on sda1.
[*]Yet when he does "find /boot/grub/stage1" in Grub's CLI, it returns (hd1,0) and not (hd0,0). So Grub thinks Ubuntu is on the second HDD, not the first.
[/LIST]
That would mean that to install Grub to the MBR of the same HDD that Ubuntu is on, he could do:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
```
Then the only thing left will be to make sure his menu.lst is correct, and make sure BIOS has the proper boot order so it will boot the HDD with Ubuntu on it.

EDIT: Culito, try the commands above that use "setup (hd1)" instead of the "setup (hd0)" you used and I believe it should work. Also in your menu.lst for the Ubuntu entries, you should try (hd1,0), but it looks like that may be dependent on whether you have your other HDD connected.

---

### Post by logos34 on 2008-08-08
Culito,

You wanted

> root (hd1,0)

setup (hd[COLOR=Red]1[/COLOR])

like Caljohnsmith said, BUT you want menu.lst to read 'root (hd**0**,0)' because as soon as you switch the Bios to boot from the ubuntu drive it will be seen as '(hd0)'

---

### Post by Culito on 2008-08-08
Aha!
That did it.  However, the plot thickens!!

I guess the root file system is also on my storage drive!!  If I boot up from my main drive now, it just sits and waits at "waiting for root file system"...

Crap.  It looks like it might be time for a backup and fresh install, with only ONE hd hooked up this time!!  I have no idea how ubuntu would have installed this way.

Thanks for your help, guys.

---

### Post by logos34 on 2008-08-08
> **Culito said:**
> Aha!
That did it.  However, the plot thickens!!

I guess the root file system is also on my storage drive!!  If I boot up from my main drive now, it just sits and waits at "waiting for root file system"...

Sounds like an error may have crept into your ubuntu entry in menu.lst, or / needs a filesystem check.
(sudo fsck /dev/sda1)

---

### Post by caljohnsmith on 2008-08-08
Culito, would you please clarify for me: are you able to get to the Grub menu on startup, and it is when you choose to boot Ubuntu that you get that "waiting for root file system" error? 

Also, if you would post:
[LIST]
[*]The Ubuntu menu entries in your menu.lst
[*]sudo blkid -c /dev/null
[/LIST]
I think that might shed some light on your problem, if it's not a problem with your file system (that can be corrected with fsck), like Logos34 mentioned.

---

### Post by Rebelli0us on 2008-08-08
If you'd rather not install grub, Windows' boot.ini can also boot Linux. I got it to work but only if Windows and Linux partitions are on the same disk. I haven't figured how to boot Linux from a Windows installation on a different disk.

---

### Post by Culito on 2008-08-08
All right, here we go:

menu.lst:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 ro splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04.1, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a3bcad50-bac1-430a-ae5e-8abff8353b73 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I did get grub to install on the correct drive.  I chose my main drive from my BIOS boot menu and it found grub and started to boot, but hung on "waiting for root filesystem" or so.

sudo blkid -c /dev/null:

```
/dev/sda1: LABEL="MUSIC" UUID="ED80-3F80" TYPE="vfat" 
/dev/sdb1: UUID="a3bcad50-bac1-430a-ae5e-8abff8353b73" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="101d4077-f824-41bb-9196-16fef228a962" 
```

sda1 is the drive I'm replacing.
Before I can dive in to the dual boot madness (which I'm sure it will be) I have to get this straightened out first!

---

### Post by caljohnsmith on 2008-08-08
> **Culito said:**
> I chose my main drive from my BIOS boot menu and it found grub and started to boot, but hung on "waiting for root filesystem" or so.
I noticed in your menu.lst that you have Grub set to "hiddenmenu", the default timeout is 3 seconds, and the default OS Grub will choose will be the first one. I suspect you are getting that error when Grub tries to boot the first entry in your menu.lst, not while Grub is trying to load, but I could be wrong.

The "blkid" command shows that Ubuntu is actually on sdb1 (your 2nd HDD), and also when you ran that "find /boot/grub/stage1" in Grub's CLI, it also said that Ubuntu was on the 2nd HDD. Since you all ready have Ubuntu entries in your menu.lst that use (hd1,0) instead of (hd0,0), try them and see if they boot. 

But first, please temporarily comment-out that "hiddenmenu" option in Grub (put ## in front of it), and also change the default to 1:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default		1[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]##hiddenmenu[/COLOR]
```
Then when you reboot, watch to see if the Grub menu comes up. If it does, let it try to boot the second entry, which is what the new default will be. That will tell us whether (hd1,0) works.

---

### Post by Culito on 2008-08-09
Yes, it seems that Ubuntu is on my second hard drive, which is my main one.  Not sure how that happened.
The second entry in my Grub list is the recovery mode kernel, which is presently set to (hd1,0).
If I select that kernel, it just says "file not found".

(hd0,0) works now, but only if I have sda1 hooked up.  If I don't it hangs at "waiting for root file system".

Screwy.

---

### Post by caljohnsmith on 2008-08-09
> **Culito said:**
> Yes, it seems that Ubuntu is on my second hard drive, which is my main one.  Not sure how that happened.
The second entry in my Grub list is the recovery mode kernel, which is presently set to (hd1,0).
If I select that kernel, it just says "file not found".

(hd0,0) works now, but only if I have sda1 hooked up.  If I don't it hangs at "waiting for root file system".

Screwy.
Yes that is strange, and something seems contradictory to me here. I would imagine Logos34 has a better clue than I do about what is going on, as I think he has more experience with Grub then I do. But in the meantime, how about doing the following just to verify Grub has been set up properly, and it will also tell us if Grub sees your main HDD as (hd0,0) when the external HDD is disconnected:
[LIST]
[*]unhook your external HDD
[*]boot a Live CD
[*]In a terminal do the following:
```
sudo grub
grub> find /boot/grub/stage1
[that should hopefully return (hd0,0), if it does then do:]
grub> root (hd0,0)
grub> setup (hd0)

```
[/LIST]
Then try rebooting (with the external HDD disconnected still), and see if you can boot Ubuntu with either the (hd0,0) or (hd1,0) menu entries; hopefully the (hd0,0) will work.

---

### Post by Culito on 2008-08-09
First off, Mr. Caljohnsmith, I do appreciate all the help.  Thanks!

New development.  I unhooked sda1 (storage drive) and hooked up my new hard drive in it's place.  It hung on "waiting for root filesystem", like before.  Out of curiosity, I unhooked everything except for my main drive...it booted up fine!

Some wires or ones and zeroes are getting crossed somewhere, evidently.

More to come.

---

### Post by caljohnsmith on 2008-08-09
You're welcome for the help, I like to give back to the Ubuntu community when I can since I've received lots of help here myself. :)

That's great news that at least by itself, the main HDD boots fine now. I think you might be able to solve your problem about hooking up an external HDD by doing one of the following:
[LIST]
[*]Tweak your BIOS settings for the correct hard disk boot priority, [as explained on this web page]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority") for example.
[*]Or, if you boot up a Live CD (*with* the external HDD connected), you could mount your Ubuntu partition and then run a "grub-install" with the "recheck" feature so it will create a new /boot/grub/device.map in your Ubuntu partition that will allow Grub to correctly deal with your new HDD. I can give you the exact steps to do this if you want.
[/LIST]

---

### Post by Culito on 2008-08-10
I'm pretty familiar with the bios, I have that set up fine, as I'm usually a bit better with hardware than with software.
I think the computer would have booted up fine, but I'm just incredibly impatient.  The bootup is fine, but it still hangs at "waiting for root file system"...eventually it recovers.  Here's a section of dmesg when I have the new drive hooked up:

[  197.569050] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569055] end_request: I/O error, dev sda, sector 117231232
[  197.569057] printk: 4 messages suppressed.
[  197.569059] Buffer I/O error on device sda, logical block 14653904
[  197.569074] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569076] end_request: I/O error, dev sda, sector 117231232
[  197.569094] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569096] end_request: I/O error, dev sda, sector 0
[  197.569104] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569106] end_request: I/O error, dev sda, sector 8
[  197.569113] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569115] end_request: I/O error, dev sda, sector 16
[  197.569122] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569124] end_request: I/O error, dev sda, sector 24
[  197.569131] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569133] end_request: I/O error, dev sda, sector 32
[  197.569140] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569142] end_request: I/O error, dev sda, sector 40
[  197.569149] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569151] end_request: I/O error, dev sda, sector 48
[  197.569158] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569160] end_request: I/O error, dev sda, sector 56
[  197.569170] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569172] end_request: I/O error, dev sda, sector 64
[  197.569179] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569181] end_request: I/O error, dev sda, sector 72
[  197.569188] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569190] end_request: I/O error, dev sda, sector 80
[  197.569197] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569200] end_request: I/O error, dev sda, sector 88
[  197.569206] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569209] end_request: I/O error, dev sda, sector 96
[  197.569215] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569217] end_request: I/O error, dev sda, sector 104
[  197.569224] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569227] end_request: I/O error, dev sda, sector 112
[  197.569233] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569235] end_request: I/O error, dev sda, sector 120
[  197.569241] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.569244] end_request: I/O error, dev sda, sector 0
[  197.669549] Adding 2835432k swap on /dev/sdb5.  Priority:-1 extents:1 across:2835432k
[  197.775830] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.775835] end_request: I/O error, dev sda, sector 117231232
[  197.775849] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.775852] end_request: I/O error, dev sda, sector 117231232
[  197.775891] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.775894] end_request: I/O error, dev sda, sector 0
[  197.775898] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.775901] end_request: I/O error, dev sda, sector 8
[  197.775914] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.775916] end_request: I/O error, dev sda, sector 0
[  197.776200] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.776203] end_request: I/O error, dev sda, sector 117231232
[  197.776212] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.776215] end_request: I/O error, dev sda, sector 117231232
[  197.776251] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.776254] end_request: I/O error, dev sda, sector 0
[  197.776258] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.776260] end_request: I/O error, dev sda, sector 8
[  197.776273] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  197.776276] end_request: I/O error, dev sda, sector 0
[  198.267888] EXT3 FS on sdb1, internal journal
[  198.449874] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  198.449879] end_request: I/O error, dev sda, sector 117231232
[  198.449892] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  198.449895] end_request: I/O error, dev sda, sector 117231232
[  198.449936] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  198.449938] end_request: I/O error, dev sda, sector 0
[  198.449943] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  198.449945] end_request: I/O error, dev sda, sector 8
[  198.449958] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  198.449960] end_request: I/O error, dev sda, sector 0
[  198.450444] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  198.450447] end_request: I/O error, dev sda, sector 117231232
[  198.450458] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  198.450460] end_request: I/O error, dev sda, sector 117231232
[  198.450502] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  198.450505] end_request: I/O error, dev sda, sector 0
[  198.450509] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  198.450511] end_request: I/O error, dev sda, sector 8
[  198.450522] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  198.450524] end_request: I/O error, dev sda, sector 0
[  199.838726] ip_tables: (C) 2000-2006 Netfilter Core Team
[  200.549789] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ processors (2 cpu cores) (version 2.20.00)
[  200.549451] powernow-k8:    0 : fid 0x14 (2800 MHz), vid 0xa
[  200.549454] powernow-k8:    1 : fid 0x12 (2600 MHz), vid 0xc
[  200.549456] powernow-k8:    2 : fid 0x10 (2400 MHz), vid 0xe
[  200.549457] powernow-k8:    3 : fid 0xe (2200 MHz), vid 0x10
[  200.549459] powernow-k8:    4 : fid 0xc (2000 MHz), vid 0x10
[  200.549460] powernow-k8:    5 : fid 0xa (1800 MHz), vid 0x10
[  200.549462] powernow-k8:    6 : fid 0x2 (1000 MHz), vid 0x12
[  200.752416] No dock devices found.
[  202.331611] ppdev: user-space parallel port driver
[  202.624688] audit(1218411977.368:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=10169 profile="/usr/sbin/cupsd" namespace="default"
[  202.680056] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  202.680061] apm: disabled - APM is not SMP safe.
[  203.750379] Clocksource tsc unstable (delta = -177160229 ns)
[  203.774847] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  203.774853] end_request: I/O error, dev sda, sector 0
[  203.774855] printk: 94 messages suppressed.
[  203.774857] Buffer I/O error on device sda, logical block 0
[  203.774872] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK

Looks like I have some drive problems now.

---

### Post by caljohnsmith on 2008-08-10
I don't think I can help you much with those errors, Culito, but the following thread might be the same type of problem you are having now, and the solution is posted:
[http://ubuntuforums.org/showthread.php?t=771373](http://ubuntuforums.org/showthread.php?t=771373)

---

