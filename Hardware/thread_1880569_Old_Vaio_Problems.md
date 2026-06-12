---
title: "Old Vaio Problems"
date: 2011-11-13
forum: Hardware
---

### Post by reubenfaber on 2011-11-13
I'm not really a newbie, I just am having an issue with an old vaio laptop. I cannot boot from usb or cd with this machine. The bios is set to boot from cd first, and I tried the option of booting from cd using the boot menu of the bios. The laptop just won't boot from the cd no matter what I do. I have also tried taking the hard drive out of the computer and installing lubuntu on it via usb with another computer. The laptop then booted from the hard drive, but there was nothing on the monitor. I tried hooking up an external monitor, but there was nothing on it either. Not even after rebooting with the external monitor hooked up. The fn key sequence to change to the external monitor did not help either. Any ideas/suggestions would be greatly appreciated. Thanks in advance.

---

### Post by Rodney9 on 2011-11-14
I'm sorry I have no ideas but I suggest you put a link to this post in the [Lubuntu One Stop Thread]("http://ubuntuforums.org/showthread.php?t=1844755")
where other Lubuntu users will see it and may be able to help. I know it's mainly a hardware problem, but more eyes the better and we try to help other Lubuntu users.

The Lubuntu One Stop Thread also has lots of tips, how-to's, screencasts and other info purely on Lubuntu

Rodney
_______

---

### Post by whatthefunk on 2011-11-14
What model number is your Vaio?

Most Vaios wont boot from USB, so youre out of luck there.  Is your CD player external?  Im on an old Vaio and got the OS on there through an external CD drive through the s400 port.

It could also be a problem with the CD I guess.  Did you burn your CD at a slow speed.  What version of Lubuntu are you trying?  Have you tested the CD player to make sure that it works properly?

---

### Post by reubenfaber on 2011-11-14
Thank you gentlemen, the cd is fine... it works great in another pc, but I'm not 100% on the drive. After a good night's sleep though, I'm planning to try to make a bootable grub floppy and see if I can get it to load the cd. I'll be sure to keep you updated on my progress. I now see error file not found and grub rescue when the pc is turned on. 
Well, I have to go to work now. I'll try the floppy tonight.

---

### Post by reubenfaber on 2011-11-14
I will try to post the model number of the laptop asap. Off work now btw.
I do know it is a vaio obviously, but it has
 
700/500 mhz speed step pentium 3
192 mb of pc100 ram @ 100 mhz
Integrated gpu
10 gb hdd
internal floppy
internal cd
2 usb ports
ethernet (Very exciting there... Had a few laptops before too old for that even)
Various other jacks on the back... serial, vga, printer
 
Nice machine other than being old, which is why Linux is my first choice for an os. Will try to get to working at getting a working boot floppy after dinner. I've never needed a floppy for anything before, although I have a few on hand, and a working ubuntu pc that I can use to make a grub boot floppy. Wish me luck!
 
[[SIZE=5][COLOR=#000000]whatthefunk[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=1202558")  is that a picture from Young Frankenstein you use as your avatar? Just curious.

---

### Post by reubenfaber on 2011-11-14
Well, that problem is solved. the cd drive is bad. I had 4 spare drives, so that was not too serious. Now on to installing and testing. Thank You!
 
These were helpful links, at least for those of us that unfortunately learned about computers with Windows first.
 
[[COLOR=#234786]http://schierlm.users.sourceforge.net/bootdisk/indexold.html[/COLOR]]("http://schierlm.users.sourceforge.net/bootdisk/indexold.html")
 
[www.pendrivelinux.com]("http://www.pendrivelinux.com")
 
I LOVE PendriveLinux!
 
The model number is pcg-955a

---

### Post by whatthefunk on 2011-11-14
Glad you figured it out.  Installing shouldnt be that big of a problem now.  Your Vaio is from around the same era as mine.  I had to use an alternate install ISO because my graphics card couldnt handle the normal install program.  You may have to do the same.

---

### Post by reubenfaber on 2011-11-14
True. I have the alternate install cd. But now I seem to get stuck on the message
Undefined video mode number: 314
Not sure about that. I'm not stuck on Lubuntu necessarily, so I may try a different distro. Are you using Lubuntu?

---

### Post by whatthefunk on 2011-11-14
> **reubenfaber said:**
> True. I have the alternate install cd. But now I seem to get stuck on the message
Undefined video mode number: 314
Not sure about that. I'm not stuck on Lubuntu necessarily, so I may try a different distro. Are you using Lubuntu?

Yeah, I use Lubuntu.  When you get the video mode error message, is there an option to skip the video mode set up?  If I remember correctly that is what I did.

---

### Post by reubenfaber on 2011-11-15
I think there is, but it just seems to get stuck shortly after. I'm trying Legacy OS 2 now.
The system requirements are pretty low: 500mhz processor and 192mb of ram.

---

### Post by reubenfaber on 2011-11-16
Lubuntu gives the option to scan for video modes, or continue. If I continue, it goes to a blank screen, and if I hit scan, it gives me a few very low resolution options like 60x80... and goes to a blank screen after that anyway.
Legacy OS seems to work from the cd, but not after installing to the hd. I would rather use Lubuntu, but I am about ready to scrap the laptop. Or at least shelve it untill a later date.

---

### Post by reubenfaber on 2011-11-19
I hate to admit, but I had to use Windows XP. It installed with no issues, and had all the drivers except the modem, which windows update fixed. I would rather have used a much lighter weight os, but I needed to have the pc done. Sorry all. I do think that with more time I could have gotten it to work. Thank you for your help!

---

