---
title: "GRUB returning error 21 after clean install of Ubuntu (Jaunty)"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by str8aces on 2009-06-21
I'm experiencing a GRUB boot error on my laptop (HP Pavilion dv5z) which reads:

GRUB loading stage 1.5


GRUB loading, please wait...
Error 21

There is one hard drive installed in my laptop, which contains only Ubuntu (Jaunty). The error starting occurring after I performed a clean install of Ubuntu.

Any help is appreciated.

Below I've posted the results of a boot info script that I ran while using the live CD.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002f9fd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       996,029       995,967  83 Linux
/dev/sda2             996,030   200,989,214   199,993,185  83 Linux
/dev/sda3         200,989,215   480,986,099   279,996,885  83 Linux
/dev/sda4         480,986,100   488,392,064     7,405,965   5 Extended
/dev/sda5         480,986,163   488,392,064     7,405,902  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="e6b7f8e4-069d-4026-b83b-0619d1578aca" TYPE="ext2" 
/dev/sda2: UUID="801384cd-f02c-4c5f-8e6b-af9d17641e13" TYPE="ext4" 
/dev/sda3: UUID="e6ef15c9-c67b-4e76-8422-3cabce4fffa5" TYPE="ext4" 
/dev/sda5: UUID="a427ffaf-e5e6-4fc6-91c2-577f3623beda" TYPE="swap" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)

============================= sda1/grub/menu.lst: =============================

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
# kopt=root=UUID=801384cd-f02c-4c5f-8e6b-af9d17641e13 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e6b7f8e4-069d-4026-b83b-0619d1578aca

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
uuid        e6b7f8e4-069d-4026-b83b-0619d1578aca
kernel        /vmlinuz-2.6.28-11-generic root=UUID=801384cd-f02c-4c5f-8e6b-af9d17641e13 ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e6b7f8e4-069d-4026-b83b-0619d1578aca
kernel        /vmlinuz-2.6.28-11-generic root=UUID=801384cd-f02c-4c5f-8e6b-af9d17641e13 ro  single
initrd        /initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e6b7f8e4-069d-4026-b83b-0619d1578aca
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/menu.lst
    .1GB: grub/stage2
    .0GB: initrd.img-2.6.28-11-generic
    .0GB: vmlinuz-2.6.28-11-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=801384cd-f02c-4c5f-8e6b-af9d17641e13 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=e6b7f8e4-069d-4026-b83b-0619d1578aca /boot           ext2    relatime        0       2
# /home was on /dev/sda3 during installation
UUID=e6ef15c9-c67b-4e76-8422-3cabce4fffa5 /home           ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=a427ffaf-e5e6-4fc6-91c2-577f3623beda none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=======Devices which don't seem to have a corresponding hard drive==============

 sdc 
```

---

### Post by quixote on 2009-06-22
I'm not certain, but I think there's a problem where it's marked in bold:
> title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        **e6b7f8e4-069d-4026-b83b-0619d1578aca**
kernel        /vmlinuz-2.6.28-11-generic root=UUID=**801384cd-f02c-4c5f-8e6b-af9d17641e13** ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
quiet

Those two UUIDs should be the same, I think, or else you're telling the machine to look on two different disks for the same information.  So it returns "Error 21" which is it's cryptic way of saying "can't find disk".

The first one (/dev/sda1: UUID="e6b7f8e4-069d-4026-b83b-0619d1578aca" TYPE="ext2") looks like the right one judging by the UUIDs in the blkid section.

Meanwhile, what do you actually do?  

Boot from a LiveCD and follow the instructions [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to use grub directly from the command line.  That involves less typing of interminable UUIDs than the next method. :)

Or: boot with a LiveCD, and mount your boot partition (eg by clicking on it in nautilus). Then *(update: in a terminal)* do ```
sudo gedit path-to-your-boot-partition/boot/grub/menu.lst
```For instance, if nautilus shows it mounted as /media/disk-1 then it would be sudo gedit /media/disk-1/boot/grub/menu.lst.  And then edit the faulty UUID numbers to match reality.  Then reboot.

---

### Post by presence1960 on 2009-06-23
sorry wrong thread

---

### Post by str8aces on 2009-06-23
Okay, I tried your suggesting about changing the UUID, but I'm still experiencing the boot error.  I think my first post might be a little lacking in detail about the problem, so here is some additonal information.  It seems like the problem starting occurring after I flashed the BIOS on my laptop and clean installed Ubuntu.  In order to flash it, I had to install W*****s Vista because the HP utility only runs in W******.  After I deleated the Vista installation and installed Ubuntu, the problem started.  Could this have something to do with the BIOS update?  The BIOS went from F.23 to F.33.  I only updated because the new BIOS version added support for ACPI thermal protection in Linux.

Thanks for your response

```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ** e6b7f8e4-069d-4026-b83b-0619d1578aca**
kernel       /vmlinuz-2.6.28-11-generic root=UUID=**e6b7f8e4-069d-4026-b83b-0619d1578aca** ro quiet splash 
initrd       /initrd.img-2.6.28-11-generic
quiet                      

```

---

### Post by quixote on 2009-06-23
Previous commenter noted that an ext2 filesystem can't mount ext4, which I wasn't aware of.  That's what your system is trying to do, since only your boot partition is on sda1 (ext2), but the other files needed to boot are on sda2 (ext4).  (and which has that second root=interminable-UUID-ending-in-e13)

If my suggestions don't work, this is the problem.  The simplest solution may be to back up your current sda1.  Reformat that partition to ext4.  And restore your original /boot.

---

### Post by quixote on 2009-06-23
I think our messages went flying through the ether at the same time. :)  I didn't see your most recent one when posting the last comment above.

What you say makes it sound like it really may be the ext2/ext4 problem.

I doubt it's the Vista install, or the new BIOS.  If it was BIOS, presumably the boot would hang up right at the very beginning, before ever getting to grub.  And the Vista install is history.  (Problems crop up the other way around: if you install Windoze or Vista second, it doesn't play well with other OSes in a dual-boot setup)

I don't know what the most elegant way is to fix the ext2 / ext4 problem, aside from the reformat of sda1 I suggested.  Search the forums for "9.04 ext2 ext4 install" (no quotes) or something like that.  I'm sure there are people out there with some experience on this.

---

### Post by str8aces on 2009-06-23
Thanks, I'll do another clean install and change the boot partition type to ext4.  I'll post back with the results.

---

### Post by str8aces on 2009-06-23
I just clean installed Ubuntu and set up the boot partition as ext4.  After restarting, the same error message appeared. I then followed your previous suggestion about changing the UUID, but the error still comes up.

From:
```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid         [COLOR=Red]**0bde0ec9-05f9-4213-b682-73e6abb8c265**[/COLOR]
kernel       /vmlinuz-2.6.28-11-generic root=UUID=[COLOR=Red]**63db0c33-1369-47c7-806c-0884db622d4c**[/COLOR] ro quiet splash 
initrd       /initrd.img-2.6.28-11-generic
quiet

```To:
```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid         [COLOR=Red]**0bde0ec9-05f9-4213-b682-73e6abb8c265**[/COLOR]
kernel       /vmlinuz-2.6.28-11-generic root=UUID=[COLOR=Red]**0bde0ec9-05f9-4213-b682-73e6abb8c265**[/COLOR] ro quiet splash 
initrd       /initrd.img-2.6.28-11-generic
quiet

```

---

### Post by quixote on 2009-06-23
I think my suggestion about the two UUID's is bad because your boot partition is in one place and your root filesystem is (except for /boot) in another.  So making the two the same still isn't telling grub correctly where to find everything.

One possibility is maybe not to use UUIDs at all.  In the Good Old Days, we used, for instance, (for /boot on /dev/sda1 and root filesystem on /dev/sda2)
boot (hd0,0)
root (hd0,1)

It might be worth following the instructions at the fixing grub link above ([https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)).  That's relatively easy.

Alternatively, as I say, try just manually defining everything and then make sure that's the default choice.  (Does grub give you a chance to enter a choice?  No, right?)

So, near the begining of menu.lst, so that it boots the first choice:
```
default     0
```
and then as the first choice:
```
title		Ubuntu 9.04
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.28-11-generic  ##change to match your path & file
initrd		/boot/initrd.img-2.6.27-14-generic ##change to match your path & file
savedefault
boot            (hd0,0)
```

I'm improvising, so no guarantees :).  But since it can't get worse than not booting at all, it's worth trying.

---

### Post by str8aces on 2009-06-23
I modified the file to reflect your suggestions, but the same error message still keeps appearing.  The instructions that were in the link you provided did not fix the error either.  This error just won't go away :confused:.  Thanks for all of your help so far.

From:
```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid         0bde0ec9-05f9-4213-b682-73e6abb8c265
kernel       /vmlinuz-2.6.28-11-generic root=UUID=63db0c33-1369-47c7-806c-0884db622d4c ro quiet splash 
initrd       /initrd.img-2.6.28-11-generic
quiet

```To:
```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root         (hd0,1)
kernel       /boot/vmlinuz-2.6.28-11-generic ro quiet splash 
initrd       /boot/initrd.img-2.6.28-11-generic
savedefault
boot         (hd0,0)
quiet

```

---

### Post by quixote on 2009-06-24
Well, I'm out of ideas.  Since you've reinstalled recently anyway, one thing to try might be to do it again, but this time don't put /boot and the rest of / on two different partitions.  Separate / and /home, that's usually harmless, but don't have a separate /boot partition.  Or have you tried that already, and it didn't work?  It's the only thing I can think of in this case because it's the only thing that's different from other situations I've encountered.

Somehow, don't ask me how, grub's drive designations and the real ones must not agree.  But how?  What's the output of ```
sudo fdisk -l
```

---

### Post by str8aces on 2009-06-24
I'll try reinstalling without making a dedicated partition for /boot.  This was how my original install of Ubuntu was before I had to install W*****s for the BIOS update.  I might also try a different Linux distribution to see if that will fix the problem, but I highly doubt that it will do anything.  If neither of these work, then I will try installing my old laptop hard drive to see if that changes anything.  I'll update this post if I find a solution.
  
Here's the result of fdisk.

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002f9fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          62      497983+  83  Linux
/dev/sda2              63       12511    99996592+  83  Linux
/dev/sda3           12512       29940   139998442+  83  Linux
/dev/sda4           29941       30401     3702982+  82  Linux swap / Solaris

```

---

### Post by DaftVader on 2009-06-25
From what I've seen of ext4 on other distros, i.e. Fedora 11, the problem is the current version of GRUB, which won't boot from an ext4 partition.

So, when you install Ubuntu, you just need to make sure that you create a separate /boot partition that is using ext3, then your / partition can be set as ext4 and your system should boot OK.

Apparently the next version of GRUB sorts this all out!

:D

---

### Post by quixote on 2009-06-25
Interesting.  They need to warn us ordinary users about some of these, shall we say, Issues! :D

Sounds like we've been barking up the wrong tree, str8aces.  :(

---

### Post by presence1960 on 2009-06-25
Hmmm, I didn't create a separate boot partition and my ext 4 / partition boots fine. never had a problem.

I may be wrong but I still seem to think it is because his menu.lst is on an ext 2 partition is why he can't boot. Ext 2 & ext 3 cannot access ext 4 partitions. I have hardy also on my machine and I can not mount any ext 4 partitions, even the data ones from hardy. Since ext 2 can't mount ext 4 that may be why you are getting error 21 that the selected file or device does not exist.

If I am incorrect, I will be following this thread to see what the outcome is so I can increase my knowledge with your help.

P.S. all my attempts to chainload jaunty from Hardy's menu.lst have failed resulting in error 21. I just tried it again to make sure.

---

### Post by str8aces on 2009-06-26
There must be something pretty messed up with my laptop because I've tried using both ext3 and ext4 on the /boot partition, but the problem returns every time the laptop boots.  I've also tried keeping boot in the root partition with an ext4 file system.  Of course, this did not work.  I'm really starting to think that it is either my hard drive or the updated BIOS (maybe corrupted?) that is causing this problem.  Everything was fine with my Ubuntu installation before I had to install W*****s for the BIOS update.  The strange thing is that once in Ubuntu (using Live CD), the hard drive appears to work without any problems.  I guess I could reluctantly install W*****s ](*,) and see if it boots okay.

---

### Post by quixote on 2009-06-26
Since the HD is fine as far as the LiveCD can tell, it's probably not a hardware fault.  Unless it's right in that first sector where the boot record goes.  I can't see that it would be the BIOS, because then the boot process would never get as far as grub.  I think.  :?:

There are ways to test hardware in linux, but I keep forgetting what they are.  Somebody out there: tell us! :D

I also thought that what Windows did to the Master Boot Record concerned only Windows, but who knows?  If you have bootable Windows media (a CD for instance), boot from that and run ```
fixmbr
``` That does what it sounds like: it fixes the MBR.

Alternatively, you could try reinstalling Windows, and if it still won't boot, you *know* you need fixmbr.  Then, once whatever hash it's made out of the first sector is fixed, maybe you can reinstall a real OS and have it work.  :?:  Although, for simplicity's sake, I'd keep all of / on one partition and one filesystem.  Just to keep that variable out of the mix for now.

Keep us posted on how things go.

---

### Post by str8aces on 2009-06-26
Now the strange part, I just installed W*****s Vista and it boots without any problems whatsoever.  The hard drive and BIOS are obviously fine.  Now I just have to figure out why GRUB won't do the same.  In the meantime, I'm stuck with this poor excuse of an OS](*,).

---

### Post by presence1960 on 2009-06-26
strange indeed! keep us posted I am sure the others want to know how you make out and hopefully you can share with us what the problem was.

---

### Post by unutbu on 2009-06-26
str8aces, the BIOS does not seem to be recognizing your hard drive at the time when GRUB is booting. This would lead to a GRUB 21 error.

Perhaps try this:
Boot the computer and go to the BIOS menu. 
Look for hard-drive-related configuration settings. 
Check for some option for setting the hard drive as "Auto","Primary","Secondary". 
Try them all, but record what the settings were originally.

I might be wrong about what in particular needs to be changed in the BIOS menu, but
I suspect the problem lies in the configuration of the BIOS, rather than in your configuration of GRUB, ext4 or Jaunty.

---

### Post by quixote on 2009-06-26
> stuck with this poor excuse of an OS
#-o

How about partitioning the drive and putting on Ubuntu as dual boot?  If that's okay, and then you reformat the Vista partition as something else and it quits working again . . . 

then I think it's time to start thinking laterally.  Just because you're paranoid, doesn't mean they're not after you!  No, seriously.  In that case I'd start wondering whether Vista, by accident or by accident-on-purpose, makes the boot record somehow unusable for other OSes.  At that point, it's the only variable left.  You may be on to something big here!  :cool:

---

### Post by str8aces on 2009-06-26
Unfortunately, HP tries to make the BIOS setup "user friendly", so there are few settings which can be changed.  The only thing I can change relating to the hard drive is the boot order and I've tried doing this, but without any success at eliminating the boot error.  My understanding is that the BIOS would have to recognize the hard drive in order to execute the information stored in the MBR.  GRUB is loading stage 1 fine, which would lead me to believe that the problem is occurring at stage 2.

---

### Post by str8aces on 2009-06-26
> How about partitioning the drive and putting on Ubuntu as dual boot?I'll give this a try and post back with the results.

---

### Post by unutbu on 2009-06-26
str8aces, I could be wrong, but I seem to recall a situation similar to yours where the problem was solved by changing a BIOS setting. I'll try to dig it up.

Here is one, somewhat along the same lines, though not the one I was thinking about:
[http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-install-boot/380673-grub-error-21-a.html](http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-install-boot/380673-grub-error-21-a.html)

(I understand your BIOS is not offering any options to change, so whatever the case, this is probably a dead-end. Sorry.)

---

### Post by str8aces on 2009-06-26
This is certainly a strange problem because GRUB loads :D without any errors at all now that I'm dual booting Vista and Ubuntu, but why?  Thanks quixote for suggesting this solution.

---

### Post by quixote on 2009-06-27
(Now I'm **sure** it's a plot.  :shock: )

Glad to hear it's working, though, with just a bit of dead space sacrificed to Veeesta.  :D

---

### Post by DaftVader on 2009-06-30
Sounds like you're making progress at last - it's been very odd problem.

The frustrating thing is that I'm sure had this same error a couple of months back but I can't remember the final solution. I do now recall having to go in and manually update some references in the menu.lst GRUB configuration file - I seem to vaguely recall that GRUB had got the boot device UUID mixed up or something (nothing to do with the ext3/ext4 boot issue that I've seen mentioned elsewhere) and I'm certain that Windows provoked it.

In terms of giving up space to Vista (spit, spit), well another approach is to do what I've done and virtualise everything with VirtualBox. I run Ubuntu 9.04 as the host O/S and everything else is a guest O/S inside a VM. That way, if I really have to run Windows (avoid, avoid), then I can just run it as a VM. It runs full screen and you'd never know you were running a VM until you (thankfully) switch away from it back to Ubuntu. The other great thing about running everything virtualised is it makes it easy to try new Linux distros and create server/client networks to test and evaluate all sorts of systems and software.

Funnily enough, Windows in a VM seems to work better than when it's installed natively - must be because Linux is taking care of all that tricky hardware stuff... \\:D/

---

