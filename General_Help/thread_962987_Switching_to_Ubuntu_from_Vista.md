---
title: "Switching to Ubuntu from Vista"
date: 2008-10-29
forum: General Help
---

### Post by birdd on 2008-10-29
I have been using up until now a pirate copy of Vista SP1... but it downloaded an update automatically at some stage and has now telling me to enter a valid key... so i think its now a perfect time to move to the happiness of Ubuntu now with 8.10 being released sometime today... :-)

Anyway what I am wondering is what suitable replacement programs are for what i have been using under Vista...

Hardware:
- See Signature for PC Specs
- Canon MP610
- Logitech Cordless Desktop MX-5500 Revolution Bluetooth

The Apps are:

- iTunes (Use it for music, subscribe to podcasts, sync with iPod Classic) = Banshee? or Amarok?
- Software for MP610 (CD-Label Software etc)
- DVD Shrink
- IZArc
- Software for Logitech MX5500 BT Keyboard (Has display)
- Office 2007 = OpenOffice3?
- Nero
- AnyDVD
- Live Messenger
- PuTTY
- WinSCP
- Adobe Web Premium CS3 or CS4 (Photoshop, Dreamweaver, Illustrator, etc)

Available on Linux (AFAIK)
- VLC
- Firefox
- Picasa
- Skype

The games are:
- Battlefield 1942
- Battlefield 2
- Battlefield 2142
- Need For Speed: Carbon
- Need For Speed: ProStreet
- Age of Empires 3
- Grand Theft Auto: San Andres
- Crysis
- Rollercoaster Tycoon 3
- Sims 2

Now I got CrossOver Games yesterday when they were giving it away for free... So I am wondering if I am able to run those games in CrossOver or WINE?

Any Suggestions for Alternative Apps that work just as well?

---

### Post by markharding557 on 2008-10-29
itunes =no linux has no drm
dvdshrink=dvd9copy but can run on wine
izarc=fileroller but can run on wine
openoffice is fine
nero=brasero or gnomebaker but these are simpler
live massenger=pidgin
photoshop=gimp
for windows games you can check on [http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true")

---

### Post by rags01 on 2008-10-29
> **markharding557 said:**
> itunes =no linux has no drm


Ubuntu has Rhythm Music Player which is a fantastic replacement.

---

### Post by Woody1987 on 2008-10-29
iTunes = Songbird/Amarok
DVD shrink = k9copy
IZark = archive manager (included)
office 2007 = openoffice 2.4 (included) or download and install openoffice 3
nero = brasero(included)/k3b
anyDVD = DVD::rip
Live Messenger = Pidgin(included)/amsn
putty = gnome-terminal (included)
winscp = filezilla
adobe stuff = most will run using WINE or can use GIMP
Games = Crossover/WINE some wont work with either

If you dont find suitable replacements then you should try running them in WINE and see how they work.

---

### Post by ad_267 on 2008-10-29
Yeah lots of people don't seem to like rhythmbox but I find it perfect. It shouldn't have any issues with your ipod.

Illustrator = Inkscape, inkscape is awesome.

I think CS2 works with wine.

Messenger = emesene
nero = brasero

Canon's have really poor Linux support but looks like you might be in luck because I see Pixma MP610 drivers listed. Glabels is good for making cd labels and cases.

OpenOffice 3.0 can be installed in Intrepid by adding a new software source, rather than downloading from the OpenOffice site.

---

### Post by aktiwers on 2008-10-29
You can find alternatives to many programs searching on this site:
[http://www.osalt.com/](http://www.osalt.com/)

---

### Post by fatphilthethird on 2008-10-30
Dreamweaver = Bluefish, as long as you're not after WYSIWYG
Illustrator = XaraLX. I'm not a huge fan of Inkscape, prefer XaraLX, but both have their different strengths.

What are you doing with PuTTY and WinSCP? I only use them on the Windows part of my dual boot to access my linux server. When doing that from the Ubuntu part, if I want a file browser, I just use the normal file browser in Ubuntu, nautilus, and connect over SSH. Similarly, if I want command line access, I just SSH in from the terminal.

To check your hardware, just run a session from the LiveCD. It'll be slower than a full install, but at least you'll be able to check if everything runs OK beforehand.

---

### Post by birdd on 2008-10-31
I'm not competely new to Linux... I have been using it with home servers that i have built and dabbled with since Mandrake 7 or 8 i think... and Debian 3r1 i think (might have been earlier, can't remember)...

I have used it as a desktop on my laptop for a while until i got sick of having to use Lilo as Grub made my DVD drive disappear in linux and windows... The other reason was that i was using Vista for most things as i already had it setup fully on my laptop so i wasn't finding much need to switch back and forth... (On that note does 8.10 have a new version of GRUB?)

I have done a reasonable amount of linux cmd line stuff too...

I'm using the Vista "issue" as a perfect reason to switch my main desktop competely to linux with no dual boot and really work hard to get it to do everything i want it to...

Anyway another question, i have 4GB of ram, now 32bit Ubuntu only detects 3.xGB of it, now after a bit of searching on Ubuntu forums it appears theres a couple of options: move to 64bit Ubuntu - Does anyone see any of my hardware that could cause issues?, enable PAE in the kernal - does this actually work that well? or does it just show linux that there is actually >3.xGB? Or use the Server 32bit Kernel - but this isn't optimised for desktop use and doesn't have a couple of settings enabled...

I am thinking that 64bit is possibly the way to go??? If so, is it possible to just upgrade my 32bit 8.10RC (8.10 hadn't been released when i was installing my computer last night) to 64bit 8.10?

As far as software goes:
- iTunes: I think i'll probably use either Rythmbox or Banshee
- CD-Label Software: Not sure about this one yet... Would any software be compatible with using the CD tray in the printer?
- DVD Shrink: K9to5Copy i think...
- IZArc: Builtin Archive Manager
- Software for Logitech MX5500 BT Keyboard (Has display): Haven't got any yet but actuall keyboard seems to be working fine...
- Office 2007: Downloaded OpenOffice.org 3 at work today so will use it...
- Nero: Probably just use the built in software...
- AnyDVD: DVD::rip sounds like the way to go, (does anyone know it works the same as AnyDVD where it removes the protection and allows the DVD copy software to work as normal?)
- Live Messenger: Probably Pidgen
- PuTTY: Built in SSH
- WinSCP: Built in
- Adobe Web Premium CS3 or CS4 (Photoshop, Dreamweaver, Illustrator, etc): Not sure yet, will try my copy of CS3 in Wine or Crossover otherwise might have to learn GIMP, Inkscape and other ones...

As far as Games go, i'll try them in CrossOver Games and WINE, does anyone know if Cedga support is any better than either of those? (Enough to warrent paying for it?)

---

### Post by markharding557 on 2008-10-31
> **rags01 said:**
> Ubuntu has Rhythm Music Player which is a fantastic replacement.

can you use a drm itune track on linux?i was not aware you could, i would be intrested to know

---

### Post by nitrousoxide82 on 2008-10-31
[quote=birdd]Anyway another question, i have 4GB of ram, now 32bit Ubuntu only detects 3.xGB of it, now after a bit of searching on Ubuntu forums it appears theres a couple of options: move to 64bit Ubuntu - Does anyone see any of my hardware that could cause issues?, enable PAE in the kernal - does this actually work that well? or does it just show linux that there is actually >3.xGB? Or use the Server 32bit Kernel - but this isn't optimised for desktop use and doesn't have a couple of settings enabled...

I am thinking that 64bit is possibly the way to go??? If so, is it possible to just upgrade my 32bit 8.10RC (8.10 hadn't been released when i was installing my computer last night) to 64bit 8.10?[/quote]

Yes. I have 4 GB here too and found it to be the way to go. The Server kernel has PAE enabled and can see more than ~3.2 GB but (as far as I can remember of the time I compiled my own kernels) it is better optimized for e.g. database workloads (higher throughput) than for desktop use (lower latency). To go 64-bit I think you would have to do a fresh install though.
The 64-bit system can run 32-bit binaries natively - they will require the additional installation of 32-bit library packages though, and a few of them (and this number is lowering, as system/library compatibility gets better and more applications are being worked on to be 64-bit-friendly) are picky and won't run unless they're on a 32-bit system.

---

### Post by alienprdkt on 2008-10-31
Here as you can see you can get Photoshop CS2 and Dreamweaver cS3 installed with some help from WINE:D
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by birdd on 2008-10-31
> **nitrousoxide82 said:**
> Yes. I have 4 GB here too and found it to be the way to go. The Server kernel has PAE enabled and can see more than ~3.2 GB but (as far as I can remember of the time I compiled my own kernels) it is better optimized for e.g. database workloads (higher throughput) than for desktop use (lower latency). To go 64-bit I think you would have to do a fresh install though.
The 64-bit system can run 32-bit binaries natively - they will require the additional installation of 32-bit library packages though, and a few of them (and this number is lowering, as system/library compatibility gets better and more applications are being worked on to be 64-bit-friendly) are picky and won't run unless they're on a 32-bit system.

Ok I'm going back to 32bit... 64bit was much slower... definitely noticable, was slower to boot, slower to shutdown, just generally slower... :-( 64bit must just not be there yet... And that was the basic opinion of the guys on the Linux Action Show podcast...

So i'm going back to a clean install of 32bit... damn...

So i've got a couple of options now...:
- ignore it and just keep going with 3.xGB
- Use the server Kernel
- Or roll my own kernel (which means i have to update it manually myself too)

---

