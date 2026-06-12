---
title: "GRUB issues"
date: 2008-08-12
forum: General Help
---

### Post by iconoclast hero on 2008-08-12
I installed Hardy onto a separate drive on my XP system and it dual-boots.  When the system boots, GRUB defaults to Ubuntu...  Not really a problem, although I would rather program it to wait until I decided (so if someone has that answer, great).  The problem is that in my current setup I have XP on c: drive/40gb/master and Ubuntu on d: drive/20gb/slave.  If I swap out the 20 gb so that I can access the 140 gb drive I have sitting around with info on it, GRUB crashes and goes no further even when I select XP to boot.  Is there a way around this?

P.S. And why does a tag have to be 3 characters?  Shouldn't there be an exception for XP?
[INDENT]> The following errors occurred with your submission:                                           
[LIST=1]
[*]You specified a tag that was too short. A tag must be at least 3 characters.
[/LIST]
[/INDENT]

---

### Post by caljohnsmith on 2008-08-13
It sounds like the problem is you have Grub installed to the Master Boot Record (MBR) of your Win XP HDD, and yet Grub's /boot/grub config files are on your other HDD, the Ubuntu one. So when you remove the Ubuntu HDD, your computer still tries to load Grub on startup since it is in the MBR of your Win XP HDD, but of course it doesn't work since Grub can't access its config files on your Ubuntu HDD. 

Probably the easiest solution is to restore the Windows XP MBR to your Windows XP HDD, and then install Grub to the MBR of the Ubuntu HDD. Then you can set your BIOS so that when your Ubuntu HDD is present, it will boot from that HDD.

Does this sound like what you want to do? If so I can give you more details of how to actually do it. And by the way, do you have a Win XP install CD? That would be the easiest way to recover your Win XP MBR.

---

### Post by iconoclast hero on 2008-08-13
> **caljohnsmith said:**
> It sounds like the problem is you have Grub installed to the Master Boot Record (MBR) of your Win XP HDD, and yet Grub's /boot/grub config files are on your other HDD, the Ubuntu one. So when you remove the Ubuntu HDD, your computer still tries to load Grub on startup since it is in the MBR of your Win XP HDD, but of course it doesn't work since Grub can't access its config files on your Ubuntu HDD. 

This sounds quite plausible.  I did not even consider that as being possible.

> Probably the easiest solution is to restore the Windows XP MBR to your Windows XP HDD, and then install Grub to the MBR of the Ubuntu HDD. Then you can set your BIOS so that when your Ubuntu HDD is present, it will boot from that HDD.

Why not just move the /boot/grub config files onto the Win XP HDD?  I don't know about setting the BIOS up to boot to the Ubuntu HDD when present.  The way I've gotten around it in the past is to set the master as no HDD and then it boots to the slave HDD.  Interestingly, when the slave boots, the master is still there once it has booted up.  The pc is a Dell and the bios is not terribly flexible.


> Does this sound like what you want to do? If so I can give you more details of how to actually do it. And by the way, do you have a Win XP install CD? That would be the easiest way to recover your Win XP MBR.

It is an option I would certianly like to discuss further!  I do have the XP install CD.

---

### Post by caljohnsmith on 2008-08-13
> **iconoclast hero said:**
> Why not just move the /boot/grub config files onto the Win XP HDD? 
The NTFS filesystem used by Win XP is not natively supported by Grub, which means that you couldn't just move your /boot/grub files into your Win XP partition and have Grub look there for its config files. But one option is you could create a really small partition (~50 MB) on your Win XP HDD and use that as a dedicated partition for Grub. Because I install and try out so many Linux distros, I decided a while ago to do what I just described and give my Grub its own dedicated partition, so now I don't have to worry about which linux distro controls the boot process. It's not too tough to do either.
> **iconoclast hero said:**
> I don't know about setting the BIOS up to boot to the Ubuntu HDD when present.  The way I've gotten around it in the past is to set the master as no HDD and then it boots to the slave HDD.  Interestingly, when the slave boots, the master is still there once it has booted up.  The pc is a Dell and the bios is not terribly flexible.
So on startup, are you able to boot the Ubuntu HDD directly and get a Grub menu, or are you still booting the Win XP HDD first and getting the Grub menu that way? Please run the following commands in Ubuntu and copy/paste the output back here:
```
sudo fdisk -l
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
```
Also just for completeness, please post your menu.lst in case we need that:
```
cat /boot/grub/menu.lst
```

---

### Post by iconoclast hero on 2008-08-13
> **caljohnsmith said:**
> The NTFS filesystem used by Win XP is not natively supported by Grub, which means that you couldn't just move your /boot/grub files into your Win XP partition and have Grub look there for its config files. But one option is you could create a really small partition (~50 MB) on your Win XP HDD and use that as a dedicated partition for Grub. Because I install and try out so many Linux distros, I decided a while ago to do what I just described and give my Grub its own dedicated partition, so now I don't have to worry about which linux distro controls the boot process. It's not too tough to do either. 

Ahh yes, that makes sense.  I would like to go that route...  I can make a 50 MB partition...  Should I format it as FAT, NTFS, or ext3?  I don't think that XP will do it as ext3, so if I create the partition I'll need to know how to make Ubuntu format the partition that way (as I'm assuming I do).


> So on startup, are you able to boot the Ubuntu HDD directly and get a Grub menu, or are you still booting the Win XP HDD first and getting the Grub menu that way? 
I don't think I know for sure, but since the XP HDD as master still brings up the Grub menu without the Ubuntu HDD in as slave, I assume that it is the latter...  Also, I assume that the code to follow will help you figure that out.

```
iconoclast@mustang-linux:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4111    33021576    7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20000000000 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2325    18675531   83  Linux
/dev/sdb2            2326        2431      851445    5  Extended
/dev/sdb5            2326        2431      851413+  82  Linux swap / Solaris
iconoclast@mustang-linux:~$ sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
2 bytes (2 B) copied, 0.0213066 s, 0.1 kB/s
0000000 8100                                   
0000002
iconoclast@mustang-linux:~$ sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 0000                                   
0000002
2 bytes (2 B) copied, 0.000119459 s, 16.7 kB/s
iconoclast@mustang-linux:~$ cat /boot/grub/menu.lst
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
timeout        10

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
# kopt=root=UUID=caf71c96-4225-40e7-92b9-f795f3886317 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=caf71c96-4225-40e7-92b9-f795f3886317 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=caf71c96-4225-40e7-92b9-f795f3886317 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


```

---

### Post by caljohnsmith on 2008-08-13
To make a new partition for Grub on your Windows HDD, follow these steps:
[LIST=1]
[*]First thing I would do would be to make sure you have all important data backed up from your Windows XP (not that you need to be alarmed, it is just a safe practice to do when doing something major like repartitioning). Also, it would be ideal to defragment your Windows XP before proceeding, but it is probably not absolutely necessary. Also you might as well disconnect your external HDD to remove all possibility of something accidentally happening to it during repartitioning.
[*]Next boot up your Ubuntu Live CD and open up the partition editor. I think it's under System > Admin > Partition Editor if I remember correctly. Or you can run the partition editor by doing:
```
gksudo gparted &
```
[*]Now I'm not in the partition editor, but the bottom line is you want to shrink your existing NTFS partition on /dev/sda (your Win XP partition), and then create a new partition for Grub, 50 MB is adequate. You can make the new partition a "primary" partition, and format it to the "ext2" file system. I would recommend ext2 because it uses less overhead then ext3, and you don't need the additional features of ext3 for a dinky grub partition.
[/LIST]
Let me know once your Grub partition is ready, and I'll give the rest of the instructions for installing Grub there.

---

### Post by iconoclast hero on 2008-08-13
Ok...

First:  I have no external HDD on that PC.  Both of the drives I'm talking about are internal IDEs...  I know that sounds strange that I'm swapping them out, but it is a long story.

Second:  I'm going to boot into XP and defrag... 

The rest is probably going to be later on.  Water heater conked out on me and GF doesn't like taking cold showers in the morning.  

Thanks again

---

### Post by caljohnsmith on 2008-08-13
Better to fix your water heater as I'm sure you don't want to get in "hot water" with your girlfriend at this point. :D

I was thinking, before you repartition your Windows XP drive, why don't we first see if you could simply replace the Windows XP MBR to your Win XP HDD, install Grub to the MBR of your Ubuntu HDD, and then boot off your Ubuntu HDD when it is present? I'm just thinking that this would really be the easiest solution at this point, and if it doesn't work you can always go the route of giving Grub its own dedicated partition. If you want to give it a try, follow these steps:
[LIST=1]
[*]Anyway, boot up your Windows Install CD, enter the recovery mode, and run the command "fixmbr". That will reinstall the Win XP MBR to your Win HDD. 
[*]Next boot up the Ubuntu Live CD, open a terminal and run:
```
sudo grub
grub> find /boot/grub/stage1
[will return your Ubuntu partition in the form (hdX,Y), most likely will be (hd1,0)]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
[*]Lastly you would need to modify your menu.lst:
```
sudo mount /dev/sdb /mnt
gksudo gedit /mnt/boot/grub/menu.lst &
```
Just make all the Ubuntu entries use (hd0,0) instead of (hd1,0).
[/LIST]
If you're willing, let's give that a try and see if you can then boot from your Ubuntu HDD.

---

### Post by iconoclast hero on 2008-08-13
Well Grub doesn't necessarily need to boot up linux...  I could use it to dual boot more than one XP install in addition to the Ubuntu?  

I'm willing to give it a try, but
> install[ing] Grub to the MBR of your Ubuntu HDD, and then boot[ing] off your Ubuntu HDD when it is presentwon't work if it is slave, right?  Not unless when I boot, I go into BIOS and tell it that there is no master and make it think it has to boot to the slave...  Assuming I want to keep the 40 gb XP HDD (for the time being) as master and only swap in and out the 20/140 GB (Win XP) drives as necessary...

---

### Post by caljohnsmith on 2008-08-13
> **iconoclast hero said:**
> Well Grub doesn't necessarily need to boot up linux...  I could use it to dual boot more than one XP install in addition to the Ubuntu?  
I'm not sure I follow what you mean, but Ubuntu needs Grub (or some other boot loader) to boot up.
> **iconoclast hero said:**
> 
won't work if it is slave, right?  Not unless when I boot, I go into BIOS and tell it that there is no master and make it think it has to boot to the slave...  Assuming I want to keep the 40 gb XP HDD (for the time being) as master and only swap in and out the 20/140 GB (Win XP) drives as necessary...
Yes, you would have to tweak your BIOS to boot off your Ubuntu (slave) HDD when you want to boot Ubuntu. When you want to boot Windows, you would have to tell BIOS to boot from that HDD. Or if you would rather have Grub always control your boot process (like I do) and not mess with BIOS, you could put that small dedicated Grub partition on your Windows HDD. And there's even other alternatives like "WinGrub" which will allow you to modify your Win XP boot loader so it will boot either Windows or Linux. I personally prefer just giving Grub a dinky 50 MB dedicated partition and using that to boot everything. It's up to you.

---

### Post by mazz72 on 2008-08-13
Hey guys. I'm having a problem with grub as well, and didn't know if I should start yet another thread on the topic. I've read through so many threads about this, but I can't seem to find a working solution. The problem is basically that I can't figure out where to install GRUB so it sees both my Ubuntu and XP partitions. 

I have one hdd with both OS's setup on it. When I run "find /boot/grub/stage1" in the terminal, it says "0,0"...so I run grub> root (hd0,0) and grub> setup (hd0) and then quit and reboot. The grub menu comes up and shows both XP and Ubuntu on the list, but when I try to boot to XP I get the message "error 21: selected disk does not exist". Ubuntu boots fine.

However, I know the XP installation is ok, because I can boot from the Super Grub Disc, and repair the MBR in XP. Only problem there is, when I do that, then the system boots directly to XP, with no GRUB menu. Basically, it looks like I replaced the XP MBR with GRUB, and then in trying to fix it, did the exact opposite, and replaced GRUB with XP's MBR. I tried various other solutions within the Super Grub Disc, and I basically wind up just going back and forth between booting solely to XP, or booting solely to Ubuntu. I'm obviously not installing GRUB in the right place, even though it's where the "find" command in the terminal tells me it should go. :confused:

I have one hdd with 4 partitions. 1st is for Ubuntu's "/". 2nd is a swap file. 3rd is "/home". The 4th partition is the ntfs partition with XP on it. So where do I put GRUB???

---

### Post by caljohnsmith on 2008-08-13
> **mazz72 said:**
> Hey guys. I'm having a problem with grub as well, and didn't know if I should start yet another thread on the topic. I've read through so many threads about this, but I can't seem to find a working solution. The problem is basically that I can't figure out where to install GRUB so it sees both my Ubuntu and XP partitions. 

I have one hdd with both OS's setup on it. When I run "find /boot/grub/stage1" in the terminal, it says "0,0"...so I run grub> root (hd0,0) and grub> setup (hd0) and then quit and reboot. The grub menu comes up and shows both XP and Ubuntu on the list, but when I try to boot to XP I get the message "error 21: selected disk does not exist". Ubuntu boots fine.

However, I know the XP installation is ok, because I can boot from the Super Grub Disc, and repair the MBR in XP. Only problem there is, when I do that, then the system boots directly to XP, with no GRUB menu. Basically, it looks like I replaced the XP MBR with GRUB, and then in trying to fix it, did the exact opposite, and replaced GRUB with XP's MBR. I tried various other solutions within the Super Grub Disc, and I basically wind up just going back and forth between booting solely to XP, or booting solely to Ubuntu. I'm obviously not installing GRUB in the right place, even though it's where the "find" command in the terminal tells me it should go. :confused:

I have one hdd with 4 partitions. 1st is for Ubuntu's "/". 2nd is a swap file. 3rd is "/home". The 4th partition is the ntfs partition with XP on it. So where do I put GRUB???
Actually you had it right when you had Grub in the MBR; the only reason you couldn't boot Win XP was most likely because you have the wrong (hdX,Y) partition specified for it in your /boot/grub/menu.lst file. 

Go ahead and reinstall Grub to the MBR using the "root (hd0,0)" then "setup (hd0)" in the Grub CLI. Once you boot up Ubuntu, open up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst &
```
And for the Windows entry, change it to:
```
title		Windows XP
root		[COLOR="Blue"](hd0,3)[/COLOR]
makeactive
chainloader	+1

```
Save, reboot, and you should be able to boot Windows.

---

### Post by mazz72 on 2008-08-13
Ya know, I sat there staring at my grub menu list forever trying to figure out what was wrong. I knew it had to be something in there, but I could not figure it out. 

As soon as you pointed that out, I felt like a complete idiot. I knew it would work before I even changed it, and yes....it did. Thank you so much. I can't believe I missed something so obvious. My grub list had the XP partition as (hd1,0). I don't know why, but I also don't know why I didn't see what was staring me right in the face. 1st hdd, 4th partition....makes sense, lol. :shaking head: 

Thanks a lot for the help. :)

Now, quick question, just to see if I'm actually getting the hang of this. The setting that was in there (hd1,0) WOULD work if XP were installed on a different drive than Ubuntu, and it was the second hdd....so, Ubuntu on one drive, XP on a second, XP would be hd1,0. Am I right?

---

### Post by falcon61102 on 2008-08-13
Not to butt in, but yeah, that would be correct.

---

### Post by caljohnsmith on 2008-08-13
> **mazz72 said:**
> 
Thanks a lot for the help. :)
No problem, glad it's clear for you now. :)
> **mazz72 said:**
> 
Now, quick question, just to see if I'm actually getting the hang of this. The setting that was in there (hd1,0) WOULD work if XP were installed on a different drive than Ubuntu, and it was the second hdd....so, Ubuntu on one drive, XP on a second, XP would be hd1,0. Am I right?
You would be absolutely right *if* Windows XP didn't have this really awful trait that it insists on being on the master HDD or it won't boot. So what that means is that if you have it on a second HDD (hd1,0) or slave drive, then you have to trick Win XP with Grub to make it think it is really being booted as though it were on the master HDD:
```
title		Windows XP
root		(hd1,0)
makeactive
[COLOR="Blue"]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
chainloader	+1
```
Isn't that just one of the best examples of Microsoft's arrogance and idiocy--to insist their OS can only be booted from the master HDD? :rolleyes:

---

### Post by mazz72 on 2008-08-13
Yeah well, would you expect anything less?:rolleyes:

But yeah, I'm probably not going to be doing the two seperate disk setup anyway. I was just curious to see if I was right. hehe. Actually I'm working on getting a laptop to put Ubuntu on, and then just keeping my desktop a Windows machine. I do a lot of video editing, and unfortunately, I haven't found any open-source editing apps that I really like yet. That's the only thing I keep Windows for. 

Anyway, that's neither here nor there. Thanks again for the help. :)

And thanks falcon61102 for your reply, as well. :)

---

### Post by iconoclast hero on 2008-08-13
First Mazz, welcome to this thread, lol.

> **caljohnsmith said:**
> I'm not sure I follow what you mean, but Ubuntu needs Grub (or some other boot loader) to boot up.


Right, but Grub doesn't necessarily need to boot linux.  It could control two different installs of XP (on the current master HDD and the one I want to swap in...  I told you it was a long story) and when the 20 GB it could boot ubuntu.  

> Yes, you would have to tweak your BIOS to boot off your Ubuntu (slave) HDD when you want to boot Ubuntu. When you want to boot Windows, you would have to tell BIOS to boot from that HDD. Or if you would rather have Grub always control your boot process (like I do) and not mess with BIOS, 

yes please!

> you could put that small dedicated Grub partition on your Windows HDD. And there's even other alternatives like "WinGrub" which will allow you to modify your Win XP boot loader so it will boot either Windows or Linux. I personally prefer just giving Grub a dinky 50 MB dedicated partition and using that to boot everything. It's up to you.

Thats what I wanted to go with, but when you suggested 'sperimentin', I said hey what the hell...

If you want to 'speriment, I'm game, but I think the 50 mb partition is really the way I want to end up going.  :)

---

### Post by caljohnsmith on 2008-08-14
Iconoclast hero, OK if you want to go the route of a small partition for Grub, first follow my previous instructions on creating a Grub partition. Also I should mention that if you have repartitioning software that came with your HDD, if you feel more comfortable with that software, you could use that instead to create the 50 MB partition; but you would still need to use gparted (or other linux software) to format the partition as ext2 file system.

Once you create the partition and it is formatted as ext2, here's how to install Grub to it:
[LIST=1]
[*]Boot into Ubuntu (either on your HDD or from a Live CD, doesn't matter)
Open a terminal and do:
```
sudo fdisk -l
```
Find the device name of your Grub partition (/dev/[COLOR="Blue"]sdXY[/COLOR]), just look for the partition that says "Linux" under "System" and is approximately ~50 MB under the "Blocks" category. For you it will probably be /dev/sda2.

[*]Once you've determined "sdXY" for your Grub partition, do the following:
```
sudo mount /dev/sdXY /mnt
sudo mkdir -p /mnt/boot/grub
sudo grub-install --root-directory=/mnt /dev/sdX
```
The above commands install Grub to the MBR of HDD sdX, and also create all of Grub's config files in /mnt/boot/grub/. 

[*]The only thing left is copying over your /boot/grub/menu.lst from your Ubuntu HDD into the /mnt/boot/grub directory, and you shouldn't need to modify it in your case. So if you booted into your Ubuntu HDD and not a Live CD, just do:
```
sudo cp /boot/grub/menu.lst /mnt/boot/grub/
```
[/LIST]
Then reboot and see if it works. :)

---

### Post by Mgiacchetti on 2008-08-14
you could also do the above (install grub on the ubuntu disk)

then

install bootpart in windows at c:\bootpart, and start>run>cmd
cd c:\bootpart
bootpart

this will list all your partitions with a number to the left of them
find your linux native that corresponds to ubuntu
type 

bootpart x c:\ubuntu.lnx LBA Ubuntu
where x = the number of the partition in question 
c:\ubuntu.lnx will be added to boot.ini with a menu item selection of 'Ubuntu'
NTLDR is now your boot manager

---

### Post by iconoclast hero on 2008-08-14
> **caljohnsmith said:**
> 
Once you create the partition and it is formatted as ext2, here's how to install Grub to it:
[LIST=1]
[*]Boot into Ubuntu (either on your HDD or from a Live CD, doesn't matter)
Open a terminal and do:
```
sudo fdisk -l
```Find the device name of your Grub partition (/dev/[COLOR=Blue]sdXY[/COLOR]), just look for the partition that says "Linux" under "System" and is approximately ~50 MB under the "Blocks" category. For you it will probably be /dev/sda2.
[*]Once you've determined "sdXY" for your Grub partition, do the following:
```
sudo mount /dev/sdXY /mnt
sudo mkdir -p /mnt/boot/grub
sudo grub-install --root-directory=/mnt /dev/sdX
```The above commands install Grub to the MBR of HDD sdX, and also create all of Grub's config files in /mnt/boot/grub/.
[/LIST]
Ok, I installed and ran gparted from a booted session (I'm actually on VNC to the Ubuntu box so that I can use both computers at the same time).  I added a 50+ MB partition at the end of the drive and found I have like 5 GB sitting there as unformatted space for some reason.  Anyway, I ran your commands as is, but I modified the last line above to /dev/[COLOR=Blue]sdXY[/COLOR] because it really looked like a typo.  (I just noticed the line "The above commands install Grub to the MBR of HDD sdX" -- ****)  Here is what I got:

```
iconoclast@mustang-linux:~$ sudo grub-install --root-directory=/mnt /dev/sda2
Probing devices to guess BIOS drives. This may take a long time.
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb

```

> The only thing left is copying over your /boot/grub/menu.lst from your Ubuntu HDD into the /mnt/boot/grub directory, and you shouldn't need to modify it in your case. So if you booted into your Ubuntu HDD and not a Live CD, just do:

[LIST=1]
[*] ```
sudo cp /boot/grub/menu.lst /mnt/boot/grub/
```
[/LIST]
Then reboot and see if it works. :)

Ok, as I said I was inside Ubuntu the entire time and I'm about to reboot.

---

### Post by caljohnsmith on 2008-08-14
> iconoclast@mustang-linux:~$ sudo grub-install --root-directory=/mnt /dev/[COLOR="Blue"]sda2[/COLOR]

Actually that wasn't a typo; what you did by using sda2 instead of sda is to install Grub to the boot sector of the sda2 partition. You actually need to use [COLOR="Blue"]sda[/COLOR] to install Grub to the MBR.

---

### Post by iconoclast hero on 2008-08-14
Ok, I rebooted.  Config:

[LIST]
[*]  HDD 0 40 GB / XP
[*]HDD 1 20 GB / Ubuntu
[/LIST]
Worked fine.  Was able to boot into both OSs.

Ok, I rebooted.  Config:

[LIST]
[*]  HDD 0 40 GB / XP
[*]HDD 1 140 GB / XP
[/LIST]
After the BIOS I got:
```
Grub Loading
Error 17

```

Should I clear out the 50 MB partition on the 40 GB and try it again?

---

### Post by iconoclast hero on 2008-08-14
Sorry...  judgement was off... :(

> **caljohnsmith said:**
> Actually that wasn't a typo; what you did by using sda2 instead of sda is to install Grub to the boot sector of the sda2 partition. You actually need to use [COLOR=Blue]sda[/COLOR] to install Grub to the MBR.

---

### Post by iconoclast hero on 2008-08-14
Ok, I executed the following
```
iconoclast@mustang-linux:~$ sudo grub-install --root-directory=/mnt /dev/sda
[sudo] password for iconoclast: 
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
```

Now it was able to boot properly (into Ubuntu at least), however when I swap in the other XP HDD (I checked and it is 160 GB), I get the following as before:

```
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17

```

---

### Post by caljohnsmith on 2008-08-14
OK, keep the 160 GB HDD in place, boot a Ubuntu Live CD this time, open a terminal and please post the output of:
```
sudo fdisk -l
sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
```
Next go into Grub and see if it finds your new Grub partition:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return (hd0,1), but it could return (hd1,1) if Grub sees the order of your HDDs as different as BIOS sees them. Please let me know the result of what it returns, but continue using that result you get from the find command:
```
grub> root (hdX,Y)
grub> setup (hdX)
```
Where (hdX) is not a typo. :) Then reboot and see if you get the Grub menu on startup.

---

### Post by iconoclast hero on 2008-08-14
> **caljohnsmith said:**
> 
Where (hdX) is not a typo. :) Then reboot and see if you get the Grub menu on startup.

Ok, will do...  Sorry about the typo.  Heh this means I need to put the puppy back in his crate and go upstairs!  :)  I don't trust that the rawhide is more enticing than other things that may be about...

---

### Post by iconoclast hero on 2008-08-14
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4111    33021576    7  HPFS/NTFS
/dev/sda2            4860        4866       56227+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c032c02

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo dd if=/dev/sda  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 8100                                   
0000002
2 bytes (2 B) copied, 0.0036433 s, 0.5 kB/s
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb  bs=1 skip=1049 count=2 | hexdump
2+0 records in
2+0 records out
0000000 0000                                   
0000002
2 bytes (2 B) copied, 0.00287825 s, 0.7 kB/s

``````
grub> find /boot/grub/stage1
 (hd0,1)
``````
grub> root (hd0,1)







grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,1)/boot/grub/stage2
grub> 


```

rebooting

---

### Post by iconoclast hero on 2008-08-14
Ok.  Looks like that worked.  I was able to boot into XP with the 40 and the 160 GB HDDs in.  I haven't swapped in the 20 GB Ubuntu HDD yet, but I assume that will work too...  Now the two questions I have are:


[LIST]
[*]How can I configure Grub to offer me the option to boot off of the 20 GB as master...  Based on what I've gathered so far, this just ammounts to adding an MBR/Grub to that HDD and it shouldn't matter which HDD is slaved if any.
[*]How do I add another XP entry into Grub so that if the 40 GB XP is master and the 160 GB is slave, it will allow me to pick b/w them...  This is solvable via bios, but Grub should be able to do this, right?
[/LIST]
Thanks

---

### Post by caljohnsmith on 2008-08-14
> **iconoclast hero said:**
> How can I configure Grub to offer me the option to boot off of the 20 GB as master...  Based on what I've gathered so far, this just ammounts to adding an MBR/Grub to that HDD and it shouldn't matter which HDD is slaved if any.
If you add Grub to the MBR of the 20 GB HDD, yes you will be able to boot off of it, but you will have to set your BIOS to boot that HDD instead of your 40 GB Win XP HDD. Or, are you asking if you can boot your 40 GB HDD, and then from the Grub menu boot the 20 GB HDD to get to the Grub menu on the 20 GB HDD? If so, yes, that's possible.
> **iconoclast hero said:**
> How do I add another XP entry into Grub so that if the 40 GB XP is master and the 160 GB is slave, it will allow me to pick b/w them...  This is solvable via bios, but Grub should be able to do this, right?

Yes, you can do what I explained to mazz72 in post #15; add that entry to the /boot/grub/menu.lst that's in your /dev/sda2 partition, and you should be able to boot the Windows that's on your 160 GB HDD.

---

