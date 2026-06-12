---
title: "Mount an SD card"
date: 2008-10-24
forum: General Help
---

### Post by TheGreatandMightyMe on 2008-10-24
I have an SD card that I have been trying to recover some photos off of but I have a problem.  When I plug the card into a computer it  will not read.  I have an SD card that I know is good and I can read that card and it auto mounts.  The card I want to read doesn't seem to be recognized by the reader.  I can't find a way to get a windows machine to recognize the card either but I figure since Linux is awesome it might have a solution.

Thanks,
Alex

---

### Post by ajgreeny on 2008-10-24
It sounds as if the card may be dead, but can you see the photos on your camera or if you plug the camera in which you have the card, into your computer?  If not, I think you may need to look into some photo card recovery utility.

---

### Post by TheGreatandMightyMe on 2008-10-24
It's not out of the question that the card is dead but I have been doing my best not to contemplate that.  It's out of a phone that doesn't have any way to connect to a computer.  I was really hoping that their might be a way to force the card reader to say that the card was actually plugged in.

Alex

---

### Post by TheGreatandMightyMe on 2008-10-26
Anyone maybe know how to force this to think there is a card plugged in.

---

### Post by The Cog on 2008-10-26
I don't know how much help this will be, but every time I plug an SD card into this lappy, it fails to mount. Looking at log messages seems to suggest that it tried to mount it as a CD and couldn't find CD filesystem on it - Duh!

I use **sudo fdisk -l** to find out what what device number it has been given, and then mount it by hand. Like this:
[B]sudo mkdir /media/sd-card
mount /dev/sdc1 /media/sd-card[/B]

---

### Post by ryanhaigh on 2008-10-26
You should have a look at some recovery tools. Firstly you should try and make a raw copy of the entire device using dd. This will only work if the device is actually recognised.

There is a big difference between device and filesystem. You may simply have a corrupt partition table on the device in which case the system would not be able to automount the filesystem. When you plug in the cardreader/card it should create a device node for the physical disk eg. /dev/sdc and this is what you would use when using dd (note that there is no number eg. /dev/sdc**1**, the number in this example designates partition 1 on device sdc. I would guess that if dd can create an image roughly the same size as your card then the data might be recoverable, if it cannot the news might not be so good.

Once you have the dd image you can use a program like photorec (in the repos I think) to scan the image and recover files.

---

### Post by gabyc2706 on 2008-10-28
Hi, I just started using Linux, I need help too, i purchase a card reader for my kingston sd card, first, i connected it to my laptop Toshiba satellite a65 that has installed ubuntu, it detected the adapter with no problems i saw the sd icon on my desktop, and i was able to browse it, how ever, after like 5 minutes of using it, my laptop froze for the first time, i left it like that for like 5  minutes and than did hard reset, i never had to do this before to my computer, after that, the sd card would not show on my desktop, i connected the adapter to my win desktop, i have to install the drivers obviously -windows OS desktop-  how ever, i did open the devices/hardware icons, but, when i clicked on the one for the sd card it said it was not formated, i didnt want to formate it at that time because i have information!!! After some hrs, i decided i would formate it, so i clicked yes, and said could not format, I checked  the lock and it was disabled, tried again, still, same answered, turned the lock on and unable to go through, HELP PLEASE!!!!!!!!!!

---

### Post by otz070 on 2008-10-28
for good free recovery software should work in linux using wine ([http://www.winehq.org/](http://www.winehq.org/)) or windows as standalone- [http://www.filehippo.com/download_recuva/](http://www.filehippo.com/download_recuva/)

Note: I haven't tested recuva in wine yet (fortauntly didn't need to yet)
but so far Piriform software (thats who makes it) seems to work ok with wine no errors

Since some of you were looking for recovery software I thought this might help (I've used it on xp/vista many times..good stuff) as for mounting the sd card though mabye try a different computer/reader? (make sure it's the card and not just the computer/reader being incompatable with the card or some file on it, hey it's rare but it does happen) And also if all readers refuse to see it mabye the contacts on the card are dirty/corroded? (I had some stuff that I thought for sure was no good, and was going to throw away and just on a hunch cleaned the contacts and they worked!)


Anyway either way good luck and hope you get it working, as I know how it sucks to lose important files, pictures ect.

---

### Post by TheGreatandMightyMe on 2008-11-06
> **The Cog said:**
> I don't know how much help this will be, but every time I plug an SD card into this lappy, it fails to mount. Looking at log messages seems to suggest that it tried to mount it as a CD and couldn't find CD filesystem on it - Duh!

I use **sudo fdisk -l** to find out what what device number it has been given, and then mount it by hand. Like this:
[B]sudo mkdir /media/sd-card
mount /dev/sdc1 /media/sd-card[/B]

Sorry it took over a week to read this.  When I attempt the mount command I get an error saying "special device /dev/sdc1 does not exist".  I'm going to assume that /dev/sdc1 is some form of configuration file to configure a disk.  Is there any way to use another working sd card or anything else to figure out what file is used to mount good sd cards on my system?

Thanks,
Alex

---

