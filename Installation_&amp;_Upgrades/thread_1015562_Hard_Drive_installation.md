---
title: "Hard Drive installation?"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by Leadfinger on 2008-12-18
I have a laptop that is missing it's floppy drive and it's CD drive.  I don't think I can boot the system to a USB Flash Drive.

Is there a way I can take the hard drive, make it bootable (from XP), copy an Ubuntu image to the drive and install it from there?

---

### Post by Zack McCool on 2008-12-18
If you have another system you can install the drive in, just put it in that system and install Ubuntu on it there, then move it back to the laptop it belongs in.  Make sure it is the only drive in the system when it is being installed to, and make sure grub is installed to the mbr.

When you put it in the laptop, it will work.  You may need to do some work to get wireless working, but you should be just fine otherwise...

---

### Post by Partyboi2 on 2008-12-18
You can use [[COLOR=Blue]unetbootin [/COLOR]]("http://unetbootin.sourceforge.net/")to install ubuntu which does not require the use of a cdrom or usb

---

### Post by Leadfinger on 2008-12-18
Those are both really good ideas that I hadn't thought of...thanks guys..

---

### Post by g0rd99 on 2008-12-18
> **Leadfinger said:**
> I have a laptop that is missing it's floppy drive and it's CD drive.  I don't think I can boot the system to a USB Flash Drive.

Is there a way I can take the hard drive, make it bootable (from XP), copy an Ubuntu image to the drive and install it from there?

There is a small program to make a bootable flash drive from a distro. Your computer must be capable of booting from it. 

The program is unetbootin-linux-281. It came from a dvd on Linux Format Magazie. It's about 4M in size. It worked good for me. 

To boot from a flash drive, you must have the capability built into bios. It can be a bit tricky getting some going, and every one has been different that I've tried.

It's available at this website. Good luck

Gord

---

### Post by g0rd99 on 2008-12-18
> **Leadfinger said:**
> I have a laptop that is missing it's floppy drive and it's CD drive.  I don't think I can boot the system to a USB Flash Drive.

Is there a way I can take the hard drive, make it bootable (from XP), copy an Ubuntu image to the drive and install it from there?

There is a small program to make a bootable flash drive from a distro. Your computer must be capable of booting from it. 

The program is unetbootin-linux-281. It came from a dvd on Linux Format Magazie. It's about 4M in size. It worked good for me. 

To boot from a flash drive, you must have the capability built into bios. It can be a bit tricky getting some going, and every one has been different that I've tried.

It's available at this website. Good luck

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Gord

---

### Post by Leadfinger on 2008-12-19
Quick update...

UNBootin doesn't seem to do what I need.  It wants to make the hard drive in this (Windows) PC bootable to an Ubuntu installer, so that it can download and install Ubuntu.  Great idea...but not what I need.

I need to be able to network boot my laptop (a totally different machine) so I can do the install that way.


(Side note:  To add complexity to this problem, I first need to boot it into some sort of OS where I can flash the BIOS... THEN I can do the Ubuntu install)

Im off to do more reading...

---

### Post by logos34 on 2008-12-19
> **Leadfinger said:**
> UNBootin doesn't seem to do what I need.  It wants to make the hard drive in this (Windows) PC bootable to an Ubuntu installer, so that it can download and install Ubuntu.

Look again at the [instructions]("http://unetbootin.sourceforge.net/#install")...Select 'Disk Image' radio button (not 'Distribution') and then point it to the .iso (which you copied to the disk).

Select type at bottom (usb or hard drive) and the drive letter

Reboot and go into the bios and set the usb drive or hard disk first in the boot order.

It will then reboot to that drive and begin installing

---

### Post by Leadfinger on 2008-12-19
No joy in that scenerio either...

I set UNetBootin to look like this...

[IMG]http://www.shortsolutions.net/images/boot.jpg[/IMG]

The laptop drive is connected with a USB-to-ATA cable...

When done, I remove the the drive, insert it into the laptop and I still get "Remove disks or other media.  Press any key to restart"

---

### Post by logos34 on 2008-12-19
I wonder if usb-pata converter is causing any problem...

here'w what I'd do next:

Burn a live cd from the iso (you do have a cd burner on the windows machine?)*

Then try what was suggested above and plug the lappy drive back into your windows machine--in place of the main drive.  Then boot the live cd and install to the laptop drive.  

*Or if you can't burn a CD try this:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
(-->'CD image approach')

---

### Post by Leadfinger on 2008-12-19
> **logos34 said:**
> I wonder if usb-pata converter is causing any problem...

My thoughts exactly.  So Im pulling out my old ATA-to-Laptop ribbon cable convertor thingy and Im going to have the laptop drive installed as a proper hard drive and see how that works.

But that will have to wait until after tonight's Christmas party. 

:)

---

### Post by Leadfinger on 2008-12-20
Nope.  No love there either.  The laptop is properly see'ing the drive, it's just not booting to it.

The one thing that has struck me about all of this is that the only way I can properly select my target drive is to select the "Show All Drives" option, and the tooltip for that basically says, "Don't try this, it won't work"

So why does the tool only want to work on the C: drive?  I mean.. I already have an OS on my C: drive  :mad:

---

### Post by logos34 on 2008-12-20
> **Leadfinger said:**
> the only way I can properly select my target drive is to select the "Show All Drives" option, and the tooltip for that basically says, "Don't try this, it won't work"

So why does the tool only want to work on the C: drive?  I mean.. I already have an OS on my C: drive

just forget unetbootin--seems like everyone is having one problem or another with it on 8.10 lately.

Burn a live install cd on the windows machine if you can, or use the cd image approach

---

### Post by Leadfinger on 2008-12-20
You've been super helpful, so I hope you'll indulge me for another post or two longer...

I finally got the BIOS updated on this thing (from A03 to A09).  I ended up installing the drive into a desktop, then booting it to a Win98 floppy and running the "sys c:" command on it.  That's not what I'd call the "best" way of doing this, but it worked.  Unfortunately, it's still only seeing 256MB of RAM (I was hoping it would see 512...)

SO...

Now Im just back to trying to get the network boot to work.  I have a 8.10 Live CD available, but I'm still having no luck booting the laptop so it can see that CD.

The laptop is booting from (to?) PXE.

My desktop is running TFTPD32.

The laptop seems to be getting an IP address, but the desktop doesn't seem to be properly pushing anything to the laptop.  That's the part Im hung up on.

And, of course, the documentation for TFTPD32 sucks like a...well, it's not very good.  :(

---

### Post by logos34 on 2008-12-20
never used TFTPD3, so I can't help

---

### Post by Leadfinger on 2008-12-20
Umm, how would you do it, then?


At this point, I may do the old, "install the drive in another system and install Ubuntu there...then move the drive to the laptop"

---

### Post by logos34 on 2008-12-20
> **Leadfinger said:**
> Umm, how would you do it, then?


At this point, I may do the old, "install the drive in another system and install Ubuntu there...then move the drive to the laptop"

yep (see post #13 above).  Or cd image (post 10)

---

### Post by shclark on 2009-09-14
> **Leadfinger said:**
> Umm, how would you do it, then?


At this point, I may do the old, "install the drive in another system and install Ubuntu there...then move the drive to the laptop"


I was reading this thread looking for a clue and the above made sense, so out with the screwdrivers.    Pulled the hard drive out of one notebook and pushed into another which had the internal CD.  Loaded Ubuntu and had it working fine, so pulled out and went back to the first notebook, but it only loaded once.  Even that time all I could do was move the mouse around.  Typing was not working and now it just hangs about 20% of the way into the booting process, whether I use the standard start or the rescue mode.  I did partition the drive to keep my version of Win 98 intact and that still works if I select it - I just want to see Ubuntu working too.  Any more ideas?

---

### Post by Partyboi2 on 2009-09-15
> **shclark said:**
> I was reading this thread looking for a clue and the above made sense, so out with the screwdrivers.    Pulled the hard drive out of one notebook and pushed into another which had the internal CD.  Loaded Ubuntu and had it working fine, so pulled out and went back to the first notebook, but it only loaded once.  Even that time all I could do was move the mouse around.  Typing was not working and now it just hangs about 20% of the way into the booting process, whether I use the standard start or the rescue mode.  I did partition the drive to keep my version of Win 98 intact and that still works if I select it - I just want to see Ubuntu working too.  Any more ideas?
What are your system specs? Make sure you meet the min requirements to install Ubuntu.

---

### Post by bedeantoni on 2009-09-15
Hi guys,

I want to install new one hard drive in my current system. Should I have make any changes to my current system or should I continue with the same?

---

