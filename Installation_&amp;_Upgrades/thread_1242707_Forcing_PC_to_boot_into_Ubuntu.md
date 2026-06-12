---
title: "Forcing PC to boot into Ubuntu"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by mt6112a on 2009-08-17
Hello there,
 
So I'm having a little trouble forcing my computer to boot into Ubuntu without the Live CD. I have gone through and installed the program (v9.04) but my computer does not seem to be recognizing this as my OS. I had the same problem with Windows, which is why I started with Ubuntu in the first place. Upon startup, the computer asks me to: 
 
"Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key"
 
So I ran off the live CD for a bit, but want my CDRom back. The computer is essentially unresponsive before this screen; I can't access the BIOS or setup menu or anything by hitting F1, F8, F10, F11 or any other keys. It always goes to this screen.
 
As I said, I've installed Ubuntu, after reformatting my hard drive to the ext3 system. I told the installer to use the entire hard disk for the installation. I was told that the computer doesn't seem to be recognizing the installation as the root file system. In a previous thread, I was told to run the following command: 
 
Code:
sudo grubroot (hd0,0)setup (hd0)quit 
And then to remove the Live CD and restart. Unfortunately, this didn't solve my problem and the computer still gives me that error message.
 
Any ideas?

---

### Post by SoftwareExplorer on 2009-08-17
How old is the computer? Maybe it has the older drive connection interface (PATA) that depends on the right pins being jumpered on the drive. Pata has a cable about 1.5 inches wide to the drive, SATA (the newer way) is about 1 CM across.

---

### Post by presence1960 on 2009-08-17
before we go off guessing at what it might be, lets get a look at your setup & boot process first. Boot off the ubuntu Live CD, choose "try ubuntu without any changes", when the desktop loads open Firefox and come back here. Download to your desktop the Boot Info Script 0.32 from my signature line. Once it is on desktop open a terminal & run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file here. After pasting here highlight all text and click the # sign on the toolbar to place code tags around the text. We  will see what you have on there and if it is your install or boot process that is the problem.

---

### Post by mt6112a on 2009-08-19
Hello there,

So I'm having a little trouble forcing my computer to boot into Ubuntu without the Live CD. I have gone through and installed the program (v9.04) but my computer does not seem to be recognizing this as my OS. I had the same problem with Windows, which is why I started with Ubuntu in the first place. Upon startup, the computer asks me to: 

"Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key"

So I ran off the live CD for a bit, but want my CDRom back. The computer is essentially unresponsive before this screen; I can't access the BIOS or setup menu or anything by hitting F1, F8, F10, F11 or any other keys. It always goes to this screen.

As I said, I've installed Ubuntu, after reformatting my hard drive to the ext3 system. I told the installer to use the entire hard disk for the installation. I was told that the computer doesn't seem to be recognizing the installation as the root file system. In a previous thread, I was told to run the following command: 

Code:
sudo grubroot (hd0,0)setup (hd0)quit 
And then to remove the Live CD and restart. Unfortunately, this didn't solve my problem and the computer still gives me that error message.

Any ideas?

---

### Post by Bucky Ball on 2009-08-19
You need to go to the BIOS and check you have the correct disk first up in the boot order.

When your computer boots, you need to hit F1 or ESC or Delete to get to the BIOS. If you booted from the install CD to install, then it is still set to the CD first and possibly the wrong hard drive second (it should skip the CD when it finds nothing in there and go to the hard drive).

Did you format the partiton to EXT3 first? From memory, Jaunty uses EXT4 as default so who knows, could be some weird conflict. Generally, you don't need to format anything first, you can do this as part of the install. I would install again and this time go for MANUAL partitioning, set them up that way with:

/
/home
/swap

... at least and see how you go.

You can also boot from the Live CD and run System->Admin->Partition Editor to see how your disk has been divided up.

---

### Post by raymondh on 2009-08-19
> **mt6112a said:**
>  I can't access the BIOS or setup menu or anything by hitting F1, F8, F10, F11 or any other keys. It always goes to this screen.

See if you can recall the BIOS access from this[ list]("http://michaelstevenstech.com/bios_manufacturer.htm").

---

### Post by mt6112a on 2009-08-27
Yeah I really really can't get into my BIOS on startup.  I've tried hitting just about every button there is.  The keyboard is completely unresponsive before I get onto the desktop of whatever OS I'm on (well Windows doesn't work so it's really only ubuntu).  But I cannot get into that BIOS when I start up
 
I did format the drive as ext3, in fact I did it more than once.  And when I did the install the last time (I tried it more than once) I had the installer set to put ubuntu on my entire hard drive.  So it should have formatted the drive again as ext3 and taken the entire hard disk for the installation.
 
I'm going to try one other thing before I reinstall.  But thanks for the help.  I'll let you know how it turns out

---

### Post by mt6112a on 2009-08-27
Hey,

sorry it took so long to respond; i forgot to subscribe to my own post and thought it was just lost in the aether.  Anyway, to answer the first question, come on! It's old but not that old.  it's got a SATA

As for the second post, I didn't have that option when I boot from the CD, but I just went in and it started up with no trouble.  So I ran that command and here is the result:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02cc02cb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   231,834,014   231,833,952  83 Linux
/dev/sda2         231,834,015   234,436,544     2,602,530   5 Extended
/dev/sda5         231,834,078   234,436,544     2,602,467  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="99e1192f-7db4-4a8d-bd95-35f72c632acd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="9c560f72-4fde-43d4-bc84-1554ddccfb20" 
/dev/ramzswap0: TYPE="swap" 

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


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=99e1192f-7db4-4a8d-bd95-35f72c632acd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=99e1192f-7db4-4a8d-bd95-35f72c632acd

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
uuid        99e1192f-7db4-4a8d-bd95-35f72c632acd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=99e1192f-7db4-4a8d-bd95-35f72c632acd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        99e1192f-7db4-4a8d-bd95-35f72c632acd
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=99e1192f-7db4-4a8d-bd95-35f72c632acd ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        99e1192f-7db4-4a8d-bd95-35f72c632acd
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=99e1192f-7db4-4a8d-bd95-35f72c632acd /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9c560f72-4fde-43d4-bc84-1554ddccfb20 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  17.4GB: boot/grub/menu.lst
  17.5GB: boot/grub/stage2
  17.5GB: boot/initrd.img-2.6.28-11-generic
  17.5GB: boot/vmlinuz-2.6.28-11-generic
  17.5GB: initrd.img
  17.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

That's what I've got.  let me know what I should do from here.  Thanks for the help

-Mike

---

### Post by presence1960 on 2009-08-27
Everything from the script looks good. I would tend to lean towards some type of hardware problem because 1) you had this problem prior with windows and 2) something is definitely wrong if you can't access BIOS. I would start checking my hardware.

---

### Post by mt6112a on 2009-08-27
Is there anything in particular I should check out?  Any way to check the harddisk from ubuntu?  I'm a novice at best with computer repair, so I wouldn't really even know what to look at...
 
Or am I basically I'm SOL with what I'm working with and should investigate buying a new computer?

---

### Post by presence1960 on 2009-08-27
First off please don't create duplicate threads for the same issue. I justed posted a response in the other thread you created. 

Secondly do you have a USB keyboard? If so switch out for a PS2 keyboard. That should get you into BIOS. Then if you want to use the USB keyboard go into BIOS and look for a USB Legacy setting. That will allow you to use a USB keyboard. Then reboot after switching back to the USB keyboard.

---

### Post by presence1960 on 2009-08-27
> **mt6112a said:**
> Is there anything in particular I should check out?  Any way to check the harddisk from ubuntu?  I'm a novice at best with computer repair, so I wouldn't really even know what to look at...
 
Or am I basically I'm SOL with what I'm working with and should investigate buying a new computer?
 look back at your dulicate thread you created. I posted something that is pretty basic. it may or may not be the problem, or only part of the problem. 

But please refrain from creating more than a single thread on the same issue. thanks.

---

### Post by mt6112a on 2009-08-27
yeah my bad on that like i said i forgot to subscribe to my posts so i thought no one had responded.  let's just work off of this one.
 
i don't have a USB keyboard, just the one with the purple plug like most keyboards I've seen.
 
Any other suggestions?  Should I just try another installation with manual partitioning as was suggested in the other post?

---

### Post by Bucky Ball on 2009-08-28
> **mt6112a said:**
> yeah my bad on that like i said i forgot to subscribe to my posts so i thought no one had responded.  let's just work off of this one.
 
i don't have a USB keyboard, just the one with the purple plug like most keyboards I've seen.
 
Any other suggestions?  Should I just try another installation with manual partitioning as was suggested in the other post?

And try with the Alternate ISO (text based install) rather than the Desktop (GUI). It sometimes fixes things, especially on older hardware.

---

### Post by zman58 on 2009-08-28
> **mt6112a said:**
> Is there anything in particular I should check out?  Any way to check the harddisk from ubuntu?  I'm a novice at best with computer repair, so I wouldn't really even know what to look at...
 
Or am I basically I'm SOL with what I'm working with and should investigate buying a new computer?

Focusing a little on the hardware, some things to try:
1. I think there is an alternate boot capability on the Live CD which lets you "boot from the fist hard disk". Try to force boot to the fist hard drive with that option selected.
2. unplug and re-plug the hard drive cables. Then try to boot again.
3. Use a jumper to clear BIOS settings back to default. This is usually found on the motherboard. It normally requires you to remove a jumper, wait for a couple of minutes, then replace it. The machine should be powered down when you do this.

---

### Post by Bucky Ball on 2009-08-28
> **zman58 said:**
> 
3. Use a jumper to clear BIOS settings back to default. This is usually found on the motherboard. It normally requires you to remove a jumper, wait for a couple of minutes, then replace it. The machine should be powered down when you do this.

Or you can take the battery out for the same amount of time. Does the same. Also, check you have the jumpers on the hard drives themselves set correctly (master and slave).

---

### Post by raymondh on 2009-08-28
> **Bucky Ball said:**
> Or you can take the battery out for the same amount of time. Does the same. Also, check you have the jumpers on the hard drives themselves set correctly (master and slave).

depends on where the battery is ;)  On mine, it lay underneath the graphics card which took a while.

---

### Post by mt6112a on 2009-08-31
OK I've tried most of what was suggested, at least what I know how to do.  I don't have any options before I get to the desktop.  Well, I have the option for language I think then it goes right into Ubuntu.  Either way, the computer is unresponsive before I hit the desktop, so I can't select anything anyway.  I am absolutely sure of that.
 
I installed with a .ISO file.  I don't know what a GUI/desktop install is,  but I don't think I did that.
 
I unplugged and re-plugged the hard drive cables.  No luck there.  I unplugged them, let it sit for like 5 minutes, then plugged both back in. I still get the same message on startup when I don't have the live CD in.  I don't know exactly what the battery looks like for me to take it out, so I didn't try that.
 
I don't know what a jumper is.  What is it and where can I get one?

---

### Post by presence1960 on 2009-08-31
> **mt6112a said:**
> OK I've tried most of what was suggested, at least what I know how to do.  I don't have any options before I get to the desktop.  Well, I have the option for language I think then it goes right into Ubuntu.  Either way, the computer is unresponsive before I hit the desktop, so I can't select anything anyway.  I am absolutely sure of that.
 
I installed with a .ISO file.  I don't know what a GUI/desktop install is,  but I don't think I did that.
 
I unplugged and re-plugged the hard drive cables.  No luck there.  I unplugged them, let it sit for like 5 minutes, then plugged both back in. I still get the same message on startup when I don't have the live CD in.  I don't know exactly what the battery looks like for me to take it out, so I didn't try that.
 
I don't know what a jumper is.  What is it and where can I get one?

Sometimes it is best to take a break and a step back and let it sit for a while. Some of the things you have said indicate you may need to educate yourself a little about the subject matter. This is not a put down, because we all start out knowing not much. You have been computing how long without Ubuntu? Another few days, weeks or even months won't kill you. Take some time away from this ( a day or two) then come back fresh and try to absorb all you can about the topics and instructions given in your thread. We want you to have ubuntu if that is what you want, but unfortunately we can't come to you to see what the problem and the solution is for you. You will have to do most of that yourself with our remote help.

---

### Post by SoftwareExplorer on 2009-09-01
Have a look at this picture. It has the battery labeled. [IMG]http://www.kids-online.net/learn/click/details/mother.jpg[/IMG]

---

### Post by SoftwareExplorer on 2009-09-01
[IMG]http://theolarch.tripod.com/jumper01.jpg[/IMG]
These are what jumpers look like on a motherboard. You would be looking for one with something like Clear CMOS near it. (It will probably be white letters--like the ones in this picture that say IRQ)
Edit:To be technical, the jumper is the plastic piece that connects two of the pins together.

---

### Post by Bucky Ball on 2009-09-01
> **SoftwareExplorer said:**
> Have a look at this picture. It has the battery labeled. [IMG]http://www.kids-online.net/learn/click/details/mother.jpg[/IMG]

Where's the picture?

The battery is a flat, round battery which is very easy to see on your motherboard. Just pop it out, wait about 30 seconds, then pop it back in again (earth yourself by making contact with the computer case while you do this and make sure you don't dislodge anything). If you have the manual for you MB you will find it easily.

Just remember, deep breath and stay relaxed when you're doing this. :)

---

### Post by SoftwareExplorer on 2009-09-01
> **Bucky Ball said:**
> Where's the picture?

Are they not showing up? Because it works on my computer.

---

### Post by Swagman on 2009-09-01
Point to note.

**WHEN** is he hitting the key to try and get into BIOS ?

The microsecond you switch on press delete.. and keep pressing it  (lots of times... just to be sure ..lol) until you fill the buffer.

Delete is found to the right of the keyboard, above the up, down, left, right arrows. **NOT** DEL on the keypad.

Sorry if this sounded condescending but... basic things first right ?

What computer is it your trying to access BIOS on ? sorry if you already stated it... it's not in the list below.

You may well have to google the make of computer to ascertain which BIOS your using.

Failing that it looks like the BIOS is locked out and from what I've been told recently, even removing the battery and resetting CMOS wont work.

Which, of course begs the question........ Who locked the BIOS and why ?

---

### Post by Bucky Ball on 2009-09-01
> **Swagman said:**
> Failing that it looks like the BIOS is locked out and from what I've been told recently, even removing the battery and resetting CMOS wont work.

By locked out I presume you mean someone has put a password on it. What exactly do you mean by 'locked out'?

All BIOS passwords will be removed when you reset.

As I stated before, when you boot up, the key you need to press to get to the BIOS will be clearly displayed, it will not be displayed for long, that is all, so you need to be on the lookout.

---

### Post by presence1960 on 2009-09-01
> **bucky ball said:**
> by locked out i presume you mean someone has put a password on it. What exactly do you mean by 'locked out'?

All bios passwords will be removed when you reset.

As i stated before, when you boot up, the key you need to press to get to the bios will be clearly displayed, it will not be displayed for long, that is all, so you need to be on the lookout.

+1

---

### Post by Swagman on 2009-09-01
> **Bucky Ball said:**
> By locked out I presume you mean someone has put a password on it. What exactly do you mean by 'locked out'?

All BIOS passwords will be removed when you reset.

As I stated before, when you boot up, the key you need to press to get to the BIOS will be clearly displayed, it will not be displayed for long, that is all, so you need to be on the lookout.


Indeed, this is what I always believed to be the case.

However, someone knowledgeable.. On these very forums stated quite vehemently that around 2005 removing the battery and resetting CMOS WILL NOT remove BIOS password.

I haven't tested that statement out personally because I can't be bothered. 

Really.. There's no point for me to password protect my BIOS.

---

### Post by Bucky Ball on 2009-09-01
I have tested that statement out many times and it is false in my experience. Maybe that someone knowledgable did not leave the battery out or the reset jumper switched for long enough (essential or no result at all). :)

---

### Post by presence1960 on 2009-09-01
> **Bucky Ball said:**
> I have tested that statement out many times and it is false in my experience. Maybe that someone knowledgable did not leave the battery out or the reset jumper switched for long enough (essential or no result at all). :)

+1

I have a Biostar mobo purchased 2/08. I just checked the documentation and there is a jumper setting which will clear CMOS. There has to be one. What would happen if you set a password and couldn't remember it. Are you locked out forever?

---

### Post by mt6112a on 2009-09-01
Wow there are some hostile people on ubuntu forums huh?  To answer your question, I've been computing for more years than I can count, but only recently started dabbling in trying to repair them.  I know my way around software pretty well but as you can see, hardware isn't quite my forte.  I just started with Ubuntu a little while ago because my windows went down on this computer (it's an HP pavilion a220n desktop, I think someone asked what type of computer it was), after i had been working off Knoppix.  I am trying to convert this to ubuntu because i don't think restoring windows is really an option at this point.  I have absorbed what has been said and tried everything that's been thrown my way, so excuse me if I don't know what a jumper is.
 
And I thought I knew what the battery was but wanted to be certain before i went ripping things out of my mobo.   I don't have a manual or any documentation or software for the computer, otherwise I probably wouldn't be on here asking these questions that apparently bother presence so much.
 
Software explorer - your pictures don't display for some reason.
 
And I don't know how many times I need to say it, but I can not get into the BIOS.  I haven't tried the delete button to fill the buffer, which i can give a whirl when I get home.  
 
But I didn't put a password on or anything.  This error message appeared one day after I power cycled my equipment and I haven't been able to access my BIOS or windows since.  
 
the computer is unresponsive before i hit the ubuntu desktop.  I can't select anything, the keyboard simply does not work before i get into ubuntu.  It tells me I need to hit F1, but i'm telling you, I've done that a thousand times, and my computer won't go into the BIOS that way.  seriously.
 
So. What now folks?

---

### Post by Bucky Ball on 2009-09-01
Hostile? Just stating fact. I speak from exerience of doing this heaps of times. :)

---

### Post by mt6112a on 2009-09-01
i wasn't referring to you, Bucky.  thanks for your help

---

### Post by Bucky Ball on 2009-09-01
:)

I would probably still try reset the BIOS. I am pretty convinced that your machine is trying to boot from the CD but getting nowhere but I could be wrong. Maybe why you are getting your original message:

"Reboot and Select proper Boot device *(means get into the BIOS and change boot order)*
or Insert Boot Media in selected Boot device and press a key *(means insert a CD)*"

If you MB says anywhere what it is you maybe able to do a search and download the manual or at least a layout of the board. 
   

I'll keep thinking.

---

### Post by DonaldJ on 2009-09-01
For that problem I would install Ubuntu in a different tower, then install that hd into the troublesome tower...  It works for me...  It might take about 30 seconds more than usual to boot-up the first time...

---

### Post by mt6112a on 2009-09-01
Whoa!  I just found a whole mess of mobo info on HP's website.  As soon as I can sift through this mess to find info on my PC (which is like 6+ years old), and find the jumper and figure out how to reset the BIOS, I'll do it.  I'll be back on after I try that to let you know how it turns out.  Thanks again Bucky.

---

### Post by Swagman on 2009-09-01
Sorry if we sound a bit abrupt. It's not intentional

Ok.. I googled your model No.

[ **Manual**](http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&cc=us&dlc=en&product=329076)



 [img]http://www.upload3r.com/serve/010909/1251816132.jpeg[/img]

---

### Post by Bucky Ball on 2009-09-01
Good work, Swagman. ;-)

Battery has a little release mechanism on one side (it is on the left in the graphic above). You'll see it. It might be a little tricky to get too cos of cabling and depends how much space you got in the box but bring a torch! Pop the battery then go have a coffee. 

Pop it back in and see if you can slap F1 and get into the BIOS.

---

### Post by presence1960 on 2009-09-01
> **mt6112a said:**
> Wow there are some hostile people on ubuntu forums huh?  To answer your question, I've been computing for more years than I can count, but only recently started dabbling in trying to repair them.  I know my way around software pretty well but as you can see, hardware isn't quite my forte.  I just started with Ubuntu a little while ago because my windows went down on this computer (it's an HP pavilion a220n desktop, I think someone asked what type of computer it was), after i had been working off Knoppix.  I am trying to convert this to ubuntu because i don't think restoring windows is really an option at this point.  I have absorbed what has been said and tried everything that's been thrown my way, so excuse me if I don't know what a jumper is.
 
And I thought I knew what the battery was but wanted to be certain before i went ripping things out of my mobo.   I don't have a manual or any documentation or software for the computer, otherwise I probably wouldn't be on here asking these questions that apparently bother presence so much.
 
Software explorer - your pictures don't display for some reason.
 
And I don't know how many times I need to say it, but I can not get into the BIOS.  I haven't tried the delete button to fill the buffer, which i can give a whirl when I get home.  
 
But I didn't put a password on or anything.  This error message appeared one day after I power cycled my equipment and I haven't been able to access my BIOS or windows since.  
 
the computer is unresponsive before i hit the ubuntu desktop.  I can't select anything, the keyboard simply does not work before i get into ubuntu.  It tells me I need to hit F1, but i'm telling you, I've done that a thousand times, and my computer won't go into the BIOS that way.  seriously.
 
So. What now folks?

It doesn't bother me but as you just readily admitted you don't know a whole lot about this. That's why I suggested to take a break from this problem and come back and start learning all you can before tackling this again. If that is being hostile then so be it. My suggestion to you still stands without alteration-> take a break and regroup. Then learn about the things you aren't too sure about before tackling them again. Common sense in my book.

P.S. If you think I am hostile or not helpful I challenge you to view my other posts (close to 2,000) and see what you think.

---

### Post by presence1960 on 2009-09-01
> **Swagman said:**
> Sorry if we sound a bit abrupt. It's not intentional

Ok.. I googled your model No.

[ **Manual**](http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&cc=us&dlc=en&product=329076)



 [img]http://www.upload3r.com/serve/010909/1251816132.jpeg[/img]

That kind of stuff is what I am referring to. You could have went to HP's site and got your manual as well as all other documentation for your machine and looked it over so you would know what others have been asking you to do. I don't mind helping people (that's why I come in here, as well as to increase my own knowledge) but those being helped have to do some leg work too.

---

### Post by dvdljns on 2009-09-01
Who made that comp and what model #. You should research how to get into bios. post the comp info and motherboard info. I had one that went past the setup option so fast I had to start hitting delete before anything showed on the monitor.

---

### Post by Bucky Ball on 2009-09-02
> **dvdljns said:**
> Who made that comp and what model #. You should research how to get into bios. post the comp info and motherboard info. I had one that went past the setup option so fast I had to start hitting delete before anything showed on the monitor.

Could you read the whole thread and not just the first post? We are way beyond this. OP needs to hit F1 to get into BIOS. 

Read the thread.

---

### Post by mt6112a on 2009-09-02
> **presence1960 said:**
> That kind of stuff is what I am referring to. You could have went to HP's site and got your manual as well as all other documentation for your machine and looked it over so you would know what others have been asking you to do. I don't mind helping people (that's why I come in here, as well as to increase my own knowledge) but those being helped have to do some leg work too.
 
Yes and you'll see if you read above that I did in fact find my way to the HP site before Swagman so generously posted that picture for me.  I couldn't find my exact Mobo layout because the search function on the site isn't great and I only spent like 2 minutes at work browsing through, but as I said before I just needed to sift through the stuff to find my exact info.  I was not aware that there were Mobo layouts online in general, because as I've said most hardware is still pretty foreign to me.  But I was able to go through and find it and frankly, I resent the accusation that I'm not trying to "do any legwork" on this.  I've been busting my hump trying to get this darn computer up and running.  There is a difference between not doing anything and not knowing what to do or what to look for.  After I learned i could find Mobo layouts online, I gladly went ahead and tried to find mine on my own.  Swagman just posted that picture before I could sort it out (which I still haven't really had the chance to do as I wasn't home last night).
 
So when i get home tonight I'm going to try the delete button trick mentioned before and if that doesn't succeed i'll move on to removing the battery and using the jumper to reset the BIOS.

---

### Post by presence1960 on 2009-09-02
> **mt6112a said:**
> Yes and you'll see if you read above that I did in fact find my way to the HP site before Swagman so generously posted that picture for me.  I couldn't find my exact Mobo layout because the search function on the site isn't great and I only spent like 2 minutes at work browsing through, but as I said before I just needed to sift through the stuff to find my exact info.  I was not aware that there were Mobo layouts online in general, because as I've said most hardware is still pretty foreign to me.  But I was able to go through and find it and frankly, I resent the accusation that I'm not trying to "do any legwork" on this.  I've been busting my hump trying to get this darn computer up and running.  There is a difference between not doing anything and not knowing what to do or what to look for.  After I learned i could find Mobo layouts online, I gladly went ahead and tried to find mine on my own.  Swagman just posted that picture before I could sort it out (which I still haven't really had the chance to do as I wasn't home last night).
 
So when i get home tonight I'm going to try the delete button trick mentioned before and if that doesn't succeed i'll move on to removing the battery and using the jumper to reset the BIOS.

Now aren't you doing exactly what I suggested you need to do? That is take a break and read up or study the material you don't understand or are not familiar with. I rest my case. I really hope you get Ubuntu running, and in the end you are doing what I suggested you do. So you are very welcome.

P.S. I have learned I don't have to like the person helping me. i am not here for friendship, I am here to help and be helped. To share what I know and have others share their knowledge with me. I don't have to like any of them. I have made a few buddies in this community but that is icing on the cake.

---

### Post by mt6112a on 2009-09-03
Hey,
 
So the delete trick did not work, but removing and replacing the battery did.  It seems to have not only reset my BIOS, but my keyboard is now responsive before I hit the Ubuntu desktop again (I could actually select the language and then reached the disc menu on startup).  I just want to say thanks again to everyone for all your help.  I guess I'm now officially an ubuntuer.
 
-Mike

---

### Post by Swagman on 2009-09-03
Congrats

---

### Post by mt6112a on 2009-09-03
Oh and PS - for anyone reading this who may for some reason have this same darn antique computer I have, the battery didn't look exactly like it did in the picture.  Instead of laying flat against the Mobo, it's actually standing straight up off of it, perpendicular to the mobo.  And it looks like a large watch battery.  Just to let you know what to look for
 
Thanks again everybody

---

### Post by presence1960 on 2009-09-03
Glad you got it up & running. Enjoy Ubuntu!

---

### Post by Bucky Ball on 2009-09-03
> **mt6112a said:**
> Hey,
 
So the delete trick did not work, but removing and replacing the battery did.  It seems to have not only reset my BIOS, but my keyboard is now responsive before I hit the Ubuntu desktop again (I could actually select the language and then reached the disc menu on startup).  I just want to say thanks again to everyone for all your help.  I guess I'm now officially an ubuntuer.
 
-Mike

Excellent work! Yep, guess you are so welcome, enjoy and don't forget to post a new thread with any further problems. :)

I like it when a plan comes together! ;-)

... and presence ... all the OP had to do was take the battery out, which is what a few of us have been saying all along. That simple. :)

---

