---
title: "[SOLVED] What the #%$? No possible description comes to mind"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by Mark_in_Hollywood on 2007-07-12
The date of this post is: Thursday, July 12, 2007. My pal wants his laptop back soon.

On Monday July 9, 2007 I did a clean install on my friend's Toshiba Satellite 1905-s304 laptop.

I used a Feisty Fawn version 7.04 cd from Canonical, not downloaded from the 'net. It was mailed to me and has a nice Ubuntu cover

I had previously used this cd to install my desktop computer. Mostly everything worked from the start. I'm posting this message you are reading to LinuxQuestions from it, now.

My pal's computer has (or will have) wireless networking via a Linksys WUSB11v4 adapter. I have installed that adapter onto my desktop to learn how to install it on his Satellite 1905-s304.

In coming to understand how to install the ndiswrapper packages I was told I needed to put the Canonical cd in the drive of the laptop and add the cd. I have the correct commands for all that stuff.

When I put the cd in the drive, I received no icon on the desktop. When I put the cd in the drive and cold booted, I received no icon. The laptop's BIOS is set to boot from the cd first, then the harddisk. The optical drive has gone South!

When I clicked: Places/Computer/CD-RW/DVD-ROM and clicked on the icon this message returned:

Unable to mount media
There is probably no media in the drive.
(the Canonical cd IS in the drive)

Right clicking on the icon and looking it over I see that
under Permission the owner is:

unknown

Under Drive

Toshiba
DVD-ROM SD-R2102
Connection SCSI
Media CD-RW/DVD-ROM Drive

I don't understand why a drive that installed Feisty has "disappeared" in only 3 days.

This is the drive used to install Feisty over a broken XP, three days ago.

No modifications have been made to ANYTHING before last night. The optical drive has not been used, no files had been touched. NOTHING!

After googleing a variety of keywords, I have learned very little.

Some suggest modifying FSTAB by commenting out the /dev/scd0 [which is the cdrom entry]

Others suggest changing /dev/scd0 to /hda or /hdb, etc.

Other suggest the kernel is the problem, but I can't confirm that.

Still others suggested installing Gutsy. I downloaded the .iso, burnt a cd and put it in the laptop's drive. Re-booted. The drive clicks and clicks and never does anything else.

Now the Toshiba 1905-s304 has no optical drive that can be used.

What can be done? I have the Gutsy cd. I have the Canonical Feisty cd. But if the optical drive can't be mounted, it can't be used. Can I make a floppy on my desktop that will force the laptop to remove Feisty? Then I could try the Gutsy .iso. Suggestions?

Please save me from some major embarrassment by helping me fix this and not having to tell a "friend" that I've ruined his $2000 laptop.

---

### Post by dabl on 2007-07-12
Sorry if I missed it, but it doesn't appear that we know whether that CD/DVD drive is actually working correctly with ANY bootable CD, do we?  Do you have a Windows or other OS bootable CD around, that you could throw in it and see if it will boot anything?  You could make a GParted Live CD, or a Knoppix Live CD -- they're pretty universally recognized by most hardware.

It_ is_ within the realm of possibility that the CD/DVD drive decided to fail while the laptop was in your possession -- a true bummer.  It is pretty much _outside_ the realm of possibility, AFAIK, that booting an OS on a CD resulted in a broken optical drive.  :-?

---

### Post by Mark_in_Hollywood on 2007-07-12
The laptop will not boot from 

Gutsy Gibbon.iso

technically:

gutsy-alternate-i386.iso

It will not boot from the Canonical Feisty

---

### Post by dabl on 2007-07-12
Did you check the md5 checksum on the Gutsy ISO file?  Did your CD burner verify it after the burn? Sorry to be so skeptical, but the more CDs you can't boot, the more it looks like a hardware issue with the optical drive. :(

---

### Post by Mark_in_Hollywood on 2007-07-12
Why would a Canonical issued cd that worked to install this desktop computer fail to work after installing on a laptop?

I can't see where checksums matter in that, meanwhile, as a test, I'm downloading Knoppix and will get back to you. It looks like a 7.5 hour download via Bittorent. Yikes!

OH! Please remember that the Places/Computer/CD-RW/DVD-ROM says NOT MOUNTED. And right clicking to command: mount -- returns "probably no media".

This is a similar problem on my desktop. The CD-RW will not mount unless the media is in the drive during a cold or warm boot. Then it mostly works fine. I've burned an entire cd of .pdf files to the cd. And copied an entire cd to the harddisk.

I think this is a kernel issue, but I'm guessing. 

Does anybody know how to write fdisk to a floppy via Ubuntu so I can wipe the partition on the laptop and start over with Gutsy?

I just tried the gutsy alternate in my desktop and it offers to upgrade. I dismissed that and looked over the cd. Everything is as it should be.

---

### Post by dabl on 2007-07-12
> **Mark_in_Hollywood said:**
> Why would a Canonical issued cd that worked to install this desktop computer fail to work after installing on a laptop?


I can't imagine ... and sorry about that Knoppix download time -- it wasn't anything like that for me.

Here's my reasoning, such as it is:

- If a CD will boot correctly in other computers, then the bootable CD itself is not at fault
- If other known-good bootable CD's won't boot in that same drive, then the drive is broke
- How the drive got broke may be a mystery forever
- Software doesn't break hardware*


*It's a reasonable "rule of thumb" -- bearing in mind that software can run hardware until the hardware gets too hot, and break it that way, or load a virus that erases critical files, and thereby "break" a system installation, or turn out to be the WRONG BIOS flash version and leave you un-bootable, etc. etc. :)

---

### Post by Mark_in_Hollywood on 2007-07-12
Please have a look at:

[http://help.lockergnome.com/linux/installed-ubuntu-04-detect-cdrom0-help-ftopict423119.html](http://help.lockergnome.com/linux/installed-ubuntu-04-detect-cdrom0-help-ftopict423119.html)

I have the exact same problem as the guy above, of course, with a different fstab, but he's using Feisty, too.

I'm not saying that the software corrupted hardware (egads! how the virus writers dream of that), I'm saying that since Breezy my cd-rw doesn't really work without the disk being in the drive before the computer is turned on. That a top end laptop should not have the problem it is having of "not mounting" a drive.

The drive is 99% not likely the problem. Ubuntu not mounting it is.

---

### Post by dabl on 2007-07-12
> **Mark_in_Hollywood said:**
> Please have a look at:

[http://help.lockergnome.com/linux/installed-ubuntu-04-detect-cdrom0-help-ftopict423119.html](http://help.lockergnome.com/linux/installed-ubuntu-04-detect-cdrom0-help-ftopict423119.html)

I have the exact same problem as the guy above

Good catch!

In Kubuntu there's a "System Settings>Advanced>Drives & Filesystems" window where you can give your admin password and then "enable/disable" and/or mount or unmount devices.  There's also a similar option in Ubuntu but I'm away from my machine and cannot for the life of me pull up the mental picture of where under the System>Administration menu this one is.  But you can probably go in and enable it and mount it, once you find it.  I realize you'd like that to happen automatically, but you have to start with getting it functional, right? :-?

---

### Post by Mark_in_Hollywood on 2007-07-12
Knoppix can't be loaded either. I am as yet unconvinced that the optical drive is bad, however. because:

The floppy will also not open and it says: "Cannot mount volume", and it's owner is: unknown as well. "I could not deterine the file system type and none was specified".

---

### Post by fredj on 2007-07-12
Booting from a CD is something that is initiated through the bios and it has nothing to do with ubuntu
so it seems that the bios is now unable to access the cd. Since this is a notebook computer is it
possible to release the cd dirve physically, take it out and reinsert it? Many notebooks have a latch on
the bottom of the PC that enables you to do this (but don't use force look in the manual first). 
Also when you insert a cd into the cd drive and close the door does the CD led flicker to show drive activity?

---

### Post by dabl on 2007-07-12
OK, did you try going in to System>Preferences>Removable Drives and Media Preferences?  You've got some check-boxes there for mounting removable drives when media is inserted, that you need to make sure are checked.

---

### Post by Mark_in_Hollywood on 2007-07-12
The LED flashes a few times. The disk motor spins up. The heads click to align a few times, the screen remains blank. Finally Grub kicks in anyway and the system boots with unmountable removable media.

Thank you for your support.

---

### Post by lisati on 2007-07-12
Is the CD dirty? I had trouble with a CD/RW that worked perfectly in one machine but not in another. An inspection showed the disk to be dirty plus with a couple of scratches.

---

### Post by Mark_in_Hollywood on 2007-07-12
You could eat off of my cd-s. There are no children to touch them. I handle them  by their edges only. Seriously --- the optical media and floppy don't mount since Breezy. This is simply not a hardware problem alone.

---

### Post by Mark_in_Hollywood on 2007-07-13
Using any cd, bootable or otherwise, from a cold or warm start results in:

the cd LED flashes a few times

the drive spins up (and back down) 

the heads are heard "clicking" aligning themselves.

after a seemingly long time, all this stop, GRUB loads and the regular boot process begins.

By installing Feisty I have effectively rendered both the combo dvd/cd and floppy unusable. Yikes!!! P.S. the floppy will boot Disk Fitness Utilities, but it can't erease the MBR or wipe the disk down to 1s and 0s.

I repeat does anybody know how to write FDISK to a floppy for Ubuntu's Feisty so that I can wipe the disk and try Knoppix or something that won't freeze the removeable media?

---

### Post by Mark_in_Hollywood on 2007-07-13
By deprecating to Edgy I am able to use the combo dvd-cd drive. It's installing now with about 4:00 to go.

In spite of much confusion, the Linux and Ubuntu community has worked. Again!

---

### Post by snap on 2007-07-13
Hi,

that is one bad situation you are it, i can feel the pain, has happened to me once(not with ubuntu though but with NT4), turned out to be a H/W failure, hope it's not the same for you.

here is what i have to say....

visit 
[http://fd-doc.sourceforge.net/wiki/index.php?n=FdDocEn.FdInstall](http://fd-doc.sourceforge.net/wiki/index.php?n=FdDocEn.FdInstall)
for a copy of FreeDOS

download the CD-Rom image and the diskette(floppy)image, follow instructions for installation and booting from the floppy.

if the floppy boot detects the CD-Rom then it's a Ubuntu problem, if it fails then FreeDOS cannot see the cdrom drive too so it must be a hardware problem.

let us know the outcome, and hope this helps.

---

### Post by Mark_in_Hollywood on 2007-07-13
I deprecated to Edgy. DVD/CD found the disk and installed it. Various removeable media mounted.

After nearly 12 hours of looking I believe GRUB and the kernel may be the fault.

Please close this post.

---

### Post by steve8track on 2007-07-13
The first thought I have is if it doesn't even try to boot from the CD when the bios is set to boot from CD first, then maybe:

1.  There is something wrong with the BIOS
2.  There is something wrong with the CD drive.

Does it boot from a floppy if you set the BIOS to boot from it?  If that doesn't work, then I would guess that it isn't the CD drive, at least not it alone.  If it doesn't boot from the CD, then I would rule out ubuntu being the problem unless... I have a old Compaq desktop that wouldn't boot from CD in the drive all the time, it took probably 15 tries to get Ubuntu to load the live CD.  Now, that could be because the CD was burnt and the CD-ROM is old and doesn't recognize burnt CDs, but I think I even tried an official Windows CD, and it didn't work, so that made me think maybe the BIOS was designed to not have anything installed on it through the CD rom.  If the laptop just doesn't like to boot from other CDs, then maybe the problem really is getting it to work in Ubuntu.  However, if the problem is the CD ROM being broken, all the effort you put into troubleshooting Ubuntu won't work at fixing the problem.  Did you have trouble getting BIOS to see it when you were installing it initially?  If so, then maybe it was the problem my Compaq had and you just need to get the drive working in Ubuntu.

Another idea you could try is remove the hard drive from the laptop and put it into another laptop to install the OS.  At least then the OS could be a fresh install of whatever you want.  The bad news would be if it configured everything for that other laptop, then I don't know what it would do when you put the drive back in the laptop, since I've never tried that myself with Ubuntu, though it worked when I did that with a HD with Windows 98 SE (though it had to install a bunch of drivers on startup).

Good luck,

Steve

---

### Post by fredj on 2007-07-14
It seems that Feisty and your CD drive don't go together. Get the make and model of your drive and search
on the internet for updated firmware for the drive. Also worth making sure that you have the latest bios for
your PC installed.

---

