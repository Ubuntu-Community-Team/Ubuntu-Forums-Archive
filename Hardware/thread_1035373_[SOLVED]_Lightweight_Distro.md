---
title: "[SOLVED] Lightweight Distro"
date: 2009-01-09
forum: Hardware
---

### Post by Martin Marshalek on 2009-01-09
Hi, I have a question about all of the "lightweight" distros (Xubuntu, DSL, Puppy, etc). I have this old Toshiba T4700CT laptop with 24mb of RAM, 550mb hard disk, and i486 architecture that I am thinking of bringing into the 21st century with Linux so that my younger sister doesn't have to complain about how crappy it is. It currently runs Windows 3.11 for Workgroups that takes up about 200mb of space (including documents and files). Which distro would work best/be the most usable (I hear Puppy is has a better repo but DSL runs better. If I can run Xubuntu that would be even better:)) Also, this oldie only has a floppy drive and no internet access (I MAY be able to configure usb support in Windows but that is not definite) so how would I install? Finally, if at all possible, how would I create a dual-boot (just to keep Windows in case my sister hates Linux. I won't need to keep Windows though as it is sooooo old that it is horrible)?

---

### Post by namdung on 2009-01-09
Hope the following helps:
[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by kerry_s on 2009-01-09
keep dreaming. with 24mb ram you ain't going to get modern. you can try dsl, it will be slow, but might work. forget everything else there's not enough ram.

---

### Post by snowpine on 2009-01-09
Namdung's link is probably the best thread on this topic on the forums. I do not think Xubuntu, DSL, or Puppy will run well on that computer, you will need something much lighter. DeLi perhaps?

My advice is stick with Windows if it is running well.

---

### Post by pgmer6809 on 2009-01-09
On my oldest machine (AMD K-6 400Mhz) I have DSL installed as a curiosity.
Not sure which version of DSL (its about a year old or so) kernel version 2.4.31 if that helps.
My box has 256MB, but when DSL is running with the graphics desktop,
it shows it is using 19.8MB with the 'dillo' web browser running.
When I start a spreadsheet (DSL comes with apps that are as small as possible) it shows it is using 21.8MB with dillo, drops to 19.6MB when I close dillo.
Hope this is of some help - I hate junking working gear, but really with the price of used h/w on ebay, and the fact that your time must be worth something, I would not recommend trying to continue to use that box windows or linux.

pgmer6809

---

### Post by pgmer6809 on 2009-01-09
continued.
DSL install might be a problem if all you have is a floppy and no network access. (What on earth is your sister going to use this for? A cell phone these days has better note taking capabilities.:) )

Anyway my install of DSL takes about 180MB. That aint going to leave much left over if you want to keep windows as well. However DSL should be able to 'see' the windows documents in the windows file system. 

Two suggestions for install.
(1)
Remove the hard drive to another machine, and use the other machine to install. Then re-install the hard drive. This would be a no brainer if it were a desktop, but working on laptops can be a bit trickier.
Unless your laptop has an IDE expansion port? Then you could attach an external CDROM to it)

(2)
Repartition the hard drive with windows fdisk. 
Use some form of external storage to get DSL onto the hard drive.
(USB or an old 100 MB ZIP drive that connects to the parallel port)
Copy DSL to that from a machine with a CD, ). You should be able to put a bootable image on the new partition. Then using a 'smart boot manager' floppy, or using windows fdisk you can make the new partition bootable, and do your install. 
I am not sure that will work but it could.

The DSL home page may have more help.

pgmer6809

---

### Post by Martin Marshalek on 2009-01-10
It's mainly a hobby project but, since I have Ubuntu on my new computer, I would give the old one to her so she could do basic schoolwork. With Linux I would be able to even add modern network cards and actually use the computer.

---

### Post by mikjp on 2009-01-10
Maybe you should get your sister a computer that has been built in the 21st century? Something with at least 256 Mb RAM would be fine. That laptop just is not going to be newbie friendly with any distro.

If it has a network card, you might be able to run it as a X terminal where all the apps run in your Ubuntu.

---

### Post by Martin Marshalek on 2009-01-10
Thanks for the help. We will be getting her a better computer soon but, just for now (and this is mainly a hobby for me) I will try some of this.

---

