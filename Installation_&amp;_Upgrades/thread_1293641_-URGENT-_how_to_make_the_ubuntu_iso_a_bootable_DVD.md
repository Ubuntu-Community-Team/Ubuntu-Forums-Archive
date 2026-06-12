---
title: "-URGENT- how to make the ubuntu iso a bootable DVD instead of CD"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Miki800 on 2009-10-17
hello, I'm going in a few to someone and I need to bring ubuntu with me.

this question has nothing to do with linux actually, I just need to know how to make the bootable ubuntu iso image I can download from almost anywhere - a bootable dvd iso

because I know two things which makes this question relevant -
1. cd iso will not ever burn successfully to a dvd - it will fail - and I say that from previous experience
2. the X few first bytes, sectors, segments (there's a better name for this I just don't remember it right now) that is burnt on a disk or written on a hard disk makes whats calls the MBR. that is the thing which tells the BIOS how the device is bootable or something like that.
 so thats why simply mounting the image and copying the files with nero or something will not work because I have no control over things that are not files like the MBR.


I can not run linux on the sole computer I have right now with a dvd burner so linux solutions will not help me right now
and I'm asking this in the first place because I have no CDs left only new DVDs :P

thanks ahead

[edit]
I CAN prepare the dvd-iso to be burnt later on with a computer that has cygwin / ubuntu,
I just don't know how to.
[/edit]

---

### Post by wojox on 2009-10-17
[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

---

### Post by Miki800 on 2009-10-17
> **wojox said:**
> [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

this did not answer my question, though thank you for the link never the less.

I already have downloaded the ISO of a cd, it contains all the data I need, my connection gives me max 200 kbps which is lame but thats what I can get around where I live.

I feel like downloading 4 gigs is totally useless and a waste of my precious (yes, its already too late) time,
when all the data I need is already in that cd and theoretically all I need to do is convert it's format from cd to dvd.

I do not need this anymore but I'm still interested in how to accomplish that.

---

### Post by tosk on 2009-10-17
I'm typing this from a freshly-installed copy of Ubuntu 9.04. I burned the CD ISO to a DVD from Windows with no trouble.

Could be your burning software not wanting to cooperate. Or your drive maybe. Not sure why you can't just burn the CD ISO to a DVD.

---

### Post by brunoscunha on 2009-11-01
I'm also having trouble burning the iso. I've tried burning it on windows on ubuntu and still can't make it bootable. I've done this serveral times with other ubuntu releases and all went well.
Right now i'm burning the iso file from [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/).
This is the first time this happens to me.

---

### Post by pootan on 2009-11-01
I had quite a few problems initially with burn errors using multiple burners from Ubuntu and XP until I tried K3b from the repositories. I went down and bought a brand new DVD +RW loaded it back into the drive and chose create a DVD iso from the bottom option panels. This time however before I hit burn I **set the burn speed on the right drop down menu to the lowest setting which for me was x2. **

Also some older computers like  Hewlett-Packard(mine) and Compaq can be very buggy unless you format the disc beforehand, even if its a new beast. For this reason I always burn to rewritable formats in case something goes wrong.


To the thread creator. I have burned many isos to dvd without a hitch. The only time I have run into problems is when the iso image is larger than 2 gig which requires it to be mounted using a different format.

---

### Post by brunoscunha on 2009-11-01
Yes indeed. What I have is an HP/Compaq 6910P laptop. I burned at 3.0x and even at that speed the CD/DVD is not bootable. I'll try to burn it at work and see if I'm lucky

---

### Post by pootan on 2009-11-01
Also the K3b burner has an option to Force Format a blank DVD when you highlight it, then use the right click menu. Good luck.

---

