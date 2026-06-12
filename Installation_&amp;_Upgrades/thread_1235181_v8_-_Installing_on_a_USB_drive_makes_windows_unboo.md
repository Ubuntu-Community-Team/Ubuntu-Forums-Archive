---
title: "v8 - Installing on a USB drive makes windows unbootable?"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by kenji_03 on 2009-08-08
First of all, thank you for your time, I took the dive into Linux today and I think I screwed up somewhere.  Now I can't even retreat back to my safety net of Windows.

[B]bottom line:
[/B]I have removed the boot CD and detached the USB drive from my computer, I DID NOT install Ubuntu on my main drive, yet I get a "Grub Error 21" when booting my windows partition on the Hard Drive that I did not install Ubuntu on.

**Backstory: **
I downloaded and burned a Ubuntu 8 CD, booted it onto my laptop and attached the SATA Hard Drive I wanted to install Ubuntu on via a USB enclouser.

The hard drive had 2, 300 GB partitions, one 10 GB partition, and one 3xx GB partition.  All of these were NTFS.  I thought you could install Linux on a pre-existing partion but apparently not.

I used the help info to learn how to format partitions in Ubuntu, deleted my 3xx GB (after moving the 1GB of data off it) and deleted it.  I went to the "install Ubuntu" button on the "test CD" and was very carful to ensure I selected the (guessing the proper term) "sdb5" drive and not my windows vista "sda1/sda2/sda3" drives.

I let it do it's formatting and noticed a (guessing again) "Journal script" 3.0 and 4.0 (the installer wanted to format to the 3.0 by default).  I went with 4.0, probably a dumb move considering I don't know the difference but I did it and it's not worth explaining why.  Still, the format went okay according to the boot disk.

After the installation of Ubuntu was completed and everything should have been set to go it told me "would you like to restart now or continue with the demo".  I selected restart now, removed the CD and left the usb SATA hard drive connected to my laptop.

I restarted the laptop and got a "Grub 15 error".  I thought 'oh well, i'll fix it later.  Onto vista' and turned off the usb SATA hard drive.  After that, I restarted what I thought would be vista but nope.  now I get a "Grub 21 error" without the Ubuntu SATA drive attached.

**MY MAIN QUESTIONS:**
(1) most importantly of all this is HOW DO I GET VISTA BACK *(something I thought I'd never in a million years say)*.  I need a working OS that I know how to operate, so anyone know how I can get it back?  I have a MSI laptop so I didn't get a boot CD, instead I hvae a boot partition that works AS a bot CD.
(2) a second important question is what did I do wrong and how can I get this SATA hard drive to have a fully functional Ubuntu install.  The files ARE there when I checked using the boot CD so what gives?
(3) what is the difference between that Journal system 3.0 and 4.0?

---

### Post by pytheas22 on 2009-08-08
First of all, try booting to Vista a few more times if you haven't already.  Sometimes grub just fails on the first try but will work on a second try.

If that doesn't help, the [grub boot disk]("http://www.supergrubdisk.org/") might be able to.  Just follow the instructions on the website for creating a bootable CD (or USB), and boot to it.  It will hopefully be able to figure out how to get you booted back into Vista.

It may also help if you repeated the process for installing Ubuntu, doing everything as you did before.  It's possible that the grub bootloader was corrupted on the first installation, and that reinstalling it all again would solve the problem and allow you to boot both to Ubuntu and Vista.

Please give this a try and report back.  If none of the above helps you, we can try other things, but I'll probably need more information from you first.

To answer your questions:

(1) Vista should still be there, if everything you wrote above is true.  It sounds like the bootloader that Ubuntu installed (which replaces the Microsoft bootloader) is just having trouble starting Vista for some reason.  Hopefully my suggestions above will help you straighten that out; if not, in a worst case we can boot Vista by hand on the grub command line.

Of course, if you can get your hands on a Windows CD and boot to it, you may be able to use that to fix your system.  I don't have much Windows experience, but I think the installation CD has some option for repairing existing installations or something.

(2) I don't see anywhere where you went wrong in the steps you described above.  I'm guessing the problem is just due to a corrupted bootloader, or possibly issues with your hard disks or BIOS or something else weird like that.  This kind of stuff is rare, but it happens.

(3) ext4 is a newer file system than ext3 and is faster and better in other ways.  But ext3 still works fine; you can choose either one.  It's very unlikely that this is related to the boot problem.

---

### Post by kerry_s on 2009-08-08
sounds like you installed grub to your drives mbr instead of the usb, so you'll need to use your windows disk to fix the mbr.

---

### Post by running_rabbit07 on 2009-08-08
> **kerry_s said:**
> sounds like you installed grub to your drives mbr instead of the usb, so you'll need to use your windows disk to fix the mbr.
+1

You will have to use your Vista disk to repair your MBR or you can just make a really small 10Gig partition and install Ubuntu and save all of your files to flash whichever is more convenient.

---

### Post by pytheas22 on 2009-08-08
> sounds like you installed grub to your drives mbr instead of the usb, so you'll need to use your windows disk to fix the mbr.

I agree that's probably what happened, but even if grub was installed there, it should still be able to boot Vista and Ubuntu, no?  That's why I suspect grub corruption.

---

### Post by kenji_03 on 2009-08-09
> **pytheas22 said:**
> First of all, try booting to Vista a few more times if you haven't already.  Sometimes grub just fails on the first try but will work on a second try.

If that doesn't help, the [grub boot disk]("http://www.supergrubdisk.org/") might be able to.  Just follow the instructions on the website for creating a bootable CD (or USB), and boot to it.  It will hopefully be able to figure out how to get you booted back into Vista.

It may also help if you repeated the process for installing Ubuntu, doing everything as you did before.  It's possible that the grub bootloader was corrupted on the first installation, and that reinstalling it all again would solve the problem and allow you to boot both to Ubuntu and Vista.

Please give this a try and report back.  If none of the above helps you, we can try other things, but I'll probably need more information from you first.

To answer your questions:

(1) Vista should still be there, if everything you wrote above is true.  It sounds like the bootloader that Ubuntu installed (which replaces the Microsoft bootloader) is just having trouble starting Vista for some reason.  Hopefully my suggestions above will help you straighten that out; if not, in a worst case we can boot Vista by hand on the grub command line.

Of course, if you can get your hands on a Windows CD and boot to it, you may be able to use that to fix your system.  I don't have much Windows experience, but I think the installation CD has some option for repairing existing installations or something.

(2) I don't see anywhere where you went wrong in the steps you described above.  I'm guessing the problem is just due to a corrupted bootloader, or possibly issues with your hard disks or BIOS or something else weird like that.  This kind of stuff is rare, but it happens.

(3) ext4 is a newer file system than ext3 and is faster and better in other ways.  But ext3 still works fine; you can choose either one.  It's very unlikely that this is related to the boot problem.

[SIZE=4]**Thank you for the through reply!**[/SIZE]

I will try that asap.

Edit: I'd LOVE to know how to boot Vista by hand, as I'm a total novice to Linux that'd be helpful information!

> **kerry_s said:**
> sounds like you installed grub to your drives mbr instead of the usb, so you'll need to use your windows disk to fix the mbr.

Unfortunately I didn't get a windows disk, (this is a MSI laptop with a recovery partition ONLY).  **Does Microsoft offer a program or disk that I can use to restore the MBR without a floppy** (as no one has those anymore)

---

### Post by kerry_s on 2009-08-09
> **pytheas22 said:**
> I agree that's probably what happened, but even if grub was installed there, it should still be able to boot Vista and Ubuntu, no?  That's why I suspect grub corruption.

no, the boot folder is on the usb.

kenji_03,
did you try plugging in the usb that you have the install on, it contains the stuff needed to boot.

i'm going to point you to google on the recovery thing.
[http://www.google.com/search?q=Vista+Recovery+CD&ie=utf-8&oe=utf-8&aq=t&rls=org.debian:en-US:unofficial&client=iceweasel-a](http://www.google.com/search?q=Vista+Recovery+CD&ie=utf-8&oe=utf-8&aq=t&rls=org.debian:en-US:unofficial&client=iceweasel-a)

---

### Post by kenji_03 on 2009-08-09
> **kerry_s said:**
> no, the boot folder is on the usb.

kenji_03,
did you try plugging in the usb that you have the install on, it contains the stuff needed to boot.

i'm going to point you to google on the recovery thing.
[http://www.google.com/search?q=Vista+Recovery+CD&ie=utf-8&oe=utf-8&aq=t&rls=org.debian:en-US:unofficial&client=iceweasel-a](http://www.google.com/search?q=Vista+Recovery+CD&ie=utf-8&oe=utf-8&aq=t&rls=org.debian:en-US:unofficial&client=iceweasel-a)

Yes, I had my "USB SATA" both attached and removed when trying different methods.  I tried using the "boot menu" from my bios to force it to boot from the SATA USB, it doesn't do anything.  It just goes to the standard dos blinking "_" for 10+ minutes (I restared after 10 min).

When I do not have the USB SATA attached, I still get a GRUB error, it's an error 21.  When the USB SATA is attached I have received GRUB error 15, and 17 once after some tinkering.

Edit: on a side note.  Thank you all for your speedy replies and abundant help!  I'm totally lost when it comes to this and it's really nice to see people sympathetically helping out.

---

### Post by kerry_s on 2009-08-09
just go for 1 of those recovery disks & fix the mbr.

---

### Post by kenji_03 on 2009-08-09
> **kerry_s said:**
> just go for 1 of those recovery disks & fix the mbr. I got the disk burned and will try that ASAP, but that still leaves the question of setting up Ubuntu.

I am using an external hard drive to install Ubuntu on my SATA hard drive from my laptop.  From what [GRUB 15/17 errors]("http://www.uruk.org/orig-grub/errors.html#stage2") are, it looks like Ubuntu isn't installing properly to my USB external hard drive...

Again, that hard drive already has 3 NTFS partitions on it and I deleted the 4th NTFS partition to make way for that ext4 file system.  In case that contradiction causes Ubunto to have a 404 like error.

Edit: oh, and once again thanks for keeping up with this.  I really appreciate it

---

### Post by kerry_s on 2009-08-09
for usb installs i use unetbootin, it takes care of everything.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by kenji_03 on 2009-08-09
> **kerry_s said:**
> for usb installs i use unetbootin, it takes care of everything.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I'm doing that right now.  I am a native windows user so I was confused as all hell when I had to run the program in Terminal via [these steps]("http://www.gnuise.co.cc/gnulinux-tips/live-usb-installation").

Man, Linux is awesome.  I don't quite understand it but I am totally stoked at the prospect of memorizing such commands due to repetitive use! :P


> **kerry_s said:**
> just go for 1 of those recovery disks & fix the mbr.
Ok, so umm... Vista still = fail on all accounts.

I got the CD, burned it, and unfortunately it doesn't see anything wrong when I try to recover it using the automatic "cannot boot" option.  I _don't_ think I need to restore windows to an earlier point or if that would even help, so yeah...  Does this mean I'll have to re-install windows completely or is there a command-promp command I can use to repair the MBR?

I'm starting to feel really bad about needing my hand held so much throughout all this, but I guess all of us are at this stage at one point in time or another then we pay it back by becoming a "wtf?" user on here :lolflag:

---

### Post by pipesville on 2009-08-09
I tried the same install and now my laptop is screwed up too.  I like Ubuntu but they need to make it clearer in the install that if your not careful you won't be able to boot up without the flash drive installed.  I can boot Vista from the list with the flash drive inserted but still can't boot Ubuntu from the flash.  Now I'm just trying to get the laptop back to normal so I can boot Vista without the flash installed.  Any suggestions?

---

### Post by kerry_s on 2009-08-09
> is there a command-promp command I can use to repair the MBR?

my windows fu is really rusty, but i think the command is:
**/FixMbr**

a quick google says its right. :lolflag:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by kenji_03 on 2009-08-09
> **kerry_s said:**
> my windows fu is really rusty, but i think the command is:
**/FixMbr**

a quick google says its right. :lolflag:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I have nothing but love for you Kerry_s.  It turns out Ubuntu does have a problem when trying to install to a portable hard drive.  I tried installing several times using that usb enclosure but when I used the usb enclosure to usb-attach a CD drive to my desktop (that is incapable of support a usb drive on it's own due to it's 120 power supply) I ended up installing Ubuntu just fine.

I'm a bit busy having fun toying with Ubuntu so I'll try that window /FixMbr soon.

Again, nothing but love for your help Kerry_s

---

### Post by pytheas22 on 2009-08-10
> I tried the same install and now my laptop is screwed up too. I like Ubuntu but they need to make it clearer in the install that if your not careful you won't be able to boot up without the flash drive installed. I can boot Vista from the list with the flash drive inserted but still can't boot Ubuntu from the flash. Now I'm just trying to get the laptop back to normal so I can boot Vista without the flash installed. Any suggestions?

I'm not positive and this sounds strange (if you have Windows installed on an internal hard disk, I'm not sure why you would need to have the Ubuntu USB drive inserted to boot to the internal disk), but I would give /fixmbr a try.

---

### Post by kenji_03 on 2009-08-11
Yeah.  I hate ***dows.  Command Prompt on the vista recovery CD is a "watered down" version of command prompt.  It doesn't know /fixmbr or even /help.  It can only "cd" "dir" and "copy".  Not even del... ugh.. I hate you Microsoft...

> **pytheas22 said:**
> I'm not positive and this sounds strange (if you have Windows installed on an internal hard disk, I'm not sure why you would need to have the Ubuntu USB drive inserted to boot to the internal disk), but I would give /fixmbr a try.

I don't have to have the usb external plugged in, because it won't boot either way.  I have to use the boot CD to boiot into Ubuntu.  I did not install ubuntu onto my Vista laptop, I instaleld it onto my external hard drive and ti somehow messed up the MBR.  I luckily don't have much on my C drive so I might just re-install vista.  I only really need it for my "windows only" games and stuff anyway.  Thanks for all your help people and if you know an unwatered down Command Prompt boot CD program I'd love to have it

---

