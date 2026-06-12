---
title: "SATA filesystems unknown, bios configuration problem?"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by Sabar on 2007-04-05
Hello every one. I posted this question on the beginners forum, and I was told I should maybe post it here. 

Here is what happened.

I have been wanting to try a Linux Distribution for some time. I finally got brave enough and downloaded Ubuntu. 

I was having a hard time setting partitions on the Windows Hard Drive, so I decided to take an 80 Gig Hard drive that I had left over after scrapping a dell and install it into my Alien.

I now have a total of three Hard drives.
1. has Windows on it
2. has things I don't want to loose when I screw up windows. ( Pictures, Music, some files)
3. has Ubuntu

Being a bit scared of screwing up the other two drives I completely unplugged them. both power and connection. Then installed Ubuntu.

Everything went well, the only draw back was having to go to Bios every time I wanted to switch from Ubuntu to Windows, and Back.

Well I screwed things up In Ubuntu trying to get my Mouse to work, so I ended up reinstalling , only this time being more comfortable with what I was doing I didnt unplug my other two drives.

Now how ever the grub, upon installation noticed two Operating Systems.  so now It kicked on.  Great Loved it sure worked better than going to Bios.

Only Down Fall? I didn't have a chance to tell my Bride, I did however leave a note that she didn't see at 4 in the morning after feeding the baby boy. and she went straight to Bios and changed the boot order so windows would boot.

She then received this error

> Windows Could not start because the following file is missing or corrupt.
\Windows\System32\config\system
you can attempt to repair this file using the original setup CD-Rom select 'r' at the first screen to start repair. 

Ok no problem, after she woke me telling me how I broke my computer, I came in and the first thing I did was the Obvious, I changed the boot order in Bios back to how I had it. That should work, Right?

Wrong!

still have the same error

I only have an OEM resource disk, so I can not load that and Hit R to restore windows.  it just isn't an option. 

What I am wondering is 

A. can I fix this? Preferable with out reinstalling windows loosing everything on that drive.

B. Is it Possible to reinstall Grub? and would that fix it? I am thinking maybe it is possible that Grub went into windows and loaded it's own bit of code but in moving the boot orders around in Bios maybe it lost it. so now neither windows or Grub has a connection to this bit of code.

I really don't have even the slightest clue what it really is. that last is just me wondering.

Some things that may help to solve this is 
[The link to the Original Post]("http://ubuntuforums.org/showthread.php?t=400209&highlight=sabar")

and I was told to Add the following Information Please keep in mind that this is all Gibberish to me. I am feeling lucky I found it, and that was after some one walked me s-l-o-w-l-y threw it.



> alien@alien-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 20022 160826683+ 44 Unknown

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 30401 244196001 44 Unknown

Disk /dev/hde: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hde1 * 1 3497 28089621 83 Linux
/dev/hde2 3498 3649 1220940 5 Extended
/dev/hde5 3498 3649 1220908+ 82 Linux swap / Solaris
alien@alien-desktop:~$




alien@alien-desktop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4ac95ccc-431f-4b78-906f-3533c73efb0c ro
# kopt_2_6=root=/dev/hde1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.17-11-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hde1 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hde1 ro single
initrd /boot/initrd.img-2.6.17-11-generic
boot

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hde1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hde1 ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

alien@alien-desktop:~$



alien@alien-desktop:~$ cat /boot/grub/device.map
(hd0) /dev/hde
(hd1) /dev/sda
(hd2) /dev/sdb
alien@alien-desktop:~$ 

The other bit of information that may be helpful is this

This information was obtained from the first screen on the resource CD. What confuses me about this is the fact my 150 Gig hard drive was C and my 250 gig hard drive was D. according to this did something change? could this be my problem?
> 
Windows XP home Edition Setup

The following list shows the existing partitions and the unpartitioned space on this computer.

us the UP DOWN keys to select an item in the list.

*To set up windows XP on the selected item press enter.
*To create a partition in the Unpartitioned space, press C.
*To delete the selected partition, Press D.

157066 MB Disk 0 at ID 0 on bus 0 on atapi [MBR]

F: Partition1 [NTFS] 157057MB <136318 MB Free>
Unpartitioned space 8MB

238473 MB Disk 0 at ID 0 on Bus 0 On atapi [MBR]

G: Partitioned [NTFS] 238473 MB <173157 MB Free>

Unknown Disk
<There is no disk on this drive>


Enter=Install D=Delete Partition F3=Quit

I apologize for this being such a long post. Thank you so much if you got all the way thrue this 

Sabar

---

### Post by Herman on 2007-04-05
Hello  Sabar,
Can you see all your Windows files from Ubuntu or from a LiveCD? [Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")

I suspect that your hard drives are still not back to their original numbers somehow. This type of error seems to be consistent with a problem in your boot.ini file, exceot in your case it wasn't the boot.ini file that was changed, it was the hard disk numbering in your BIOS. See if this link seems to describe your problem reasonably well,                                        [hal.dll is missing or corrupt.]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#hal.dll_is_missing_or_corrupt") ( I realize you said the message was '                              Windows Could not start because the following file is missing or corrupt,  \Windows\System32\config\system.' It could be little silly of me maybe, but I'm hoping this is the equivalent error message for when the mistake is in the hard disk number in boot.ini rather that the partition number. 

Try making your own Windows XP boot CD [FONT=Bitstream Vera Sans Mono][FONT=serif][How to create your own boot disk for Windows XP]("http://support.microsoft.com/kb/305595/EN-US/")[/FONT][/FONT]      This is no ordinary Windows boot floppy disk. It must be formatted the way specified in the how-to. This floppy disk contians its own copy of NTDetect.com, NTLDR and boot.ini files. Since floppy disks commonly have the FAT32 filesystem, the boot.ini file will be accessible from Ubuntu if you need to edit the boot.ini to get Windows to boot. This floppy disk will by-pass most potential trouble spots for Windows booting problems.

And if that doesn't work then probably you should unplug all your hard drives except one. Check how the hard disk is set up n your BIOS and try to boot Windows again, with the floppy disk if necessary. Then plug the other two back in again one at a time, rebooting each time to make sure everything's still okay. 

Regards, Herman :)

---

### Post by Sabar on 2007-04-05
I am really new to this whole Linux thing. so there are alot of times where I am completely confused.

Ok trying to make a mounting point. after reading the supplied link, I am still a bit confused.

Having three Hard drives I am going to "mount" a file onto the Linux drive. that when opened is going to open into one of my other hard drives?

I went to terminal and entered this command.

> sudo fdisk -lu

This is the response I got back.
> 
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   321653429   160826683+  44  Unknown

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   488392064   244196001   44  Unknown

Disk /dev/hde: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *          63    56179304    28089621   83  Linux
/dev/hde2        56179305    58621184     1220940    5  Extended
/dev/hde5        56179368    58621184     1220908+  82  Linux swap / Solaris


Step three from the mounting directions is, 
> 
3) Pick out the partition you think is the right one to mount.

Then in the illustration they have a Fat 32 file highlighted. in my case trying to get into my windows files I would want to have this line

/> dev/sda1   *          63   321653429   160826683+  44  Unknown

Because I am mounting a gate way to this disk from my Linux O/S. :confused: 

Next I will make a directory ( Folder? ) for it with
> 
ubuntu@ubuntu:~$ sudo mkdir /media/windows

Then I will make my "gateway" with this line

> ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/windows -t ntfs -o nls=utf8,umask=0222

So that should be it? Now I just go to my  /media/windows file and that will take me into the drive?

I apologize for being slow, but I am learning a little. Hard to wipe out 10 years of windows work in two weeks of using Ubuntu :) 

Thanks again
Sabar

---

### Post by Herman on 2007-04-05
That looks okay to me, sabar, you're doing great! :) Yes, you should now be able to open your /media/window directory 'mountpoint' (or gateway if you like), and see the top of your Windows filesystem. It should look something like this, [**[B]            A Birds's eye view of Windows XP**[/B]]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP"). You should be able to do similar with your ntfs data drive too.

I am worried about why your fdisk output says these filesystems are 'unknown'. If you can 'see' all your files it will be great, if not, well, ...we'll cross that bridge when we get to it. I can't imagine how your filesystems could have been damaged by anything you've described so far, so I think that they'll be okay. Maybe we just need to do some more fiddling in your BIOS.

Regards, Herman :)

---

### Post by Sabar on 2007-04-06
One of the tech guys at work burnt me a copy of Windows recovery CD. 

I put it in hoping this would solve all my problems well, after getting to the main page and Hitting R For recovery it finally stoped at this screen

> 1: F:\Windows

Which Windows installation would you like to log onto
(To cancel, Press ENTER)


This is where I am getting worried. Why is it labeled as F?

It was C..

Could this be my whole problem? can this be what is messing my up? and How did it happen?. Better yet how do I fix it?

Any ideas out there?

Confused 
Sabar  :confused:

---

### Post by Sabar on 2007-04-06
and the confusion continues.

I am now trying to make a mount point and while following the directions I got this
> 
alien@alien-desktop:~$ dev/sda1 * 63 321653429 160826683+ 44 Unknown
bash: dev/sda1: No such file or directory
alien@alien-desktop:~$ 


Is it me or are things just getting worse?  I am almost ready to just tell the bride sorry I lost your stuff, disconnect the Hard drive with Ubuntu and reformat C drive. or F or what ever it is called now.

getting frustrated
Sabar

p.s. at least Ubuntu is working :)

---

### Post by Herman on 2007-04-06
>  Try making your own Windows XP boot CD [FONT=Bitstream Vera Sans Mono][FONT=serif][How to create your own boot disk for Windows XP]("http://support.microsoft.com/kb/305595/EN-US/")[/FONT][/FONT] This is no ordinary Windows boot floppy disk. It must be formatted the way specified in the how-to. This floppy disk contians its own copy of NTDetect.com, NTLDR and boot.ini files. Since floppy disks commonly have the FAT32 filesystem, the boot.ini file will be accessible from Ubuntu if you need to edit the boot.ini to get Windows to boot. This floppy disk will by-pass most potential trouble spots for Windows booting problems.
Okay. it sounds like all that's wrong is your WIndows doesn't know how to find itself anymore. The hard disk number or the partition number has changed. It's not a very bad problem, you just have to take your time and be patient. Other people have been through worse than this before. That's what the floppy disk I recommended to your earlier is good for. Try one of those and it should boot.

This link should help you with boot.ini,                                        [hal.dll is missing or corrupt]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#hal.dll_is_missing_or_corrupt"), you can edit the floppy disk's boot.ini from Ubuntu, because the floppy disk has the FAT32 filesystem, not NTFS. When you get it right, the floppy disk will boot your Windows XP. Then you can edit the Windows XP's own boot.ini from within Windows itself.

Regards, Herman.

---

### Post by Herman on 2007-04-06
Aha! I finally found it! Here's an even better link for a how-to that will get your Windows booting with a similar floppy disk or CD-ROM, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm") (and lots of similar Windows booting errors too).

You'll find all kinds of extra tips and tricks on that web site, it's great! :)
Something there should get you booting!

Regards, Herman :)

---

### Post by Sabar on 2007-04-07
Think I got it! as of a little bit ago with the help of a Recovery CD some one gave me, It looks like windows is operating again. 

Now I just want to get the "mounting?" done :) 

One thing is for sure, Learning allot about Linux this way. :) 

Thank you every one for your help in getting thrue this I can can not even begin to explain how helpful every one was

Thank you again
Sabar

---

