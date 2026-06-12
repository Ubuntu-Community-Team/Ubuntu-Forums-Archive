---
title: "Clean Install help, Old HP won't  boot from CD/ROM"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by phantom1121 on 2008-12-31
Hello all,

Newbie here and I'm completely lost..  So I downloaded ubuntu to my laptop, not for the laptop, but ended up partitioning my laptop for it anyways.  I think it's great and had no problems at all installing it on my laptop but my mothers desktop is the problem, when I download ubuntu, I originally downloaded it for her desktop as her XP disk got scratched, personally I like linux better anyways.  Anyways so here's the problem, I have her desktop set up to boot from the CD drive, I know the ubuntu disk I burned is good as I used it already to make sure it was going to work, I went in to her bios and made sure that her bios boot first from the CD drive and then HD even turned off the HD boot too.  Still can not get her desktop to boot from disk..  I get no operating system installed whic is exactly correct as the HD is wiped and empty, so what am I missing.  I seen somewhere about disabling USB legacy support, to no avail...  

My mothers desktop is an old HP with an Intel processor. not quite sure which one but I know it's not all that old.  Everything is so packed in there that I can't see and don't have the documentation.  The CD drive is newer as I purchased it for her two years ago so that shouldn't be an issue.  Any ideas or help would be greatly appreciated.  Sorry for the bonehead question, but I just want her Desktop out of my home as it's become nothing but a headache at this point in time.  Thanks in advance to anyone who helps.

Phantom1121:confused:

---

### Post by melojo on 2008-12-31
Do you have another cd drive you can throw in you moms system to test to make sure that one is good.  The reason I say this is I had a hp640 dvd r/w and it went bad.  It would not read cd's very well or write to them, but dvd's it had no problems. This hp dvd was only a couple years old at the most.  

If everything is setup in the bios correct, like booting from the cd first then it should work.  If it doesn't it seams like the cd rom is defective or some other hardware.  What makes you think that the xp cd is scratched to the point it won't work.  Will it not boot from the xp cd either?

---

### Post by phantom1121 on 2008-12-31
> **melojo said:**
> Do you have another cd drive you can throw in you moms system to test to make sure that one is good.  The reason I say this is I had a hp640 dvd r/w and it went bad.  It would not read cd's very well or write to them, but dvd's it had no problems. This hp dvd was only a couple years old at the most.  

If everything is setup in the bios correct, like booting from the cd first then it should work.  If it doesn't it seams like the cd rom is defective or some other hardware.  What makes you think that the xp cd is scratched to the point it won't work.  Will it not boot from the xp cd either?

I know the XP disk is scratch beyond belief, it's actually missing a couple files on the actual disk because of the scratch, the Drive is fine however, as it boots the xp disk and runs to a certain point but then the missing file won't allow it to o any further..  You can see the enormous scratch on it too.. eeek!!!  I had been telling my mom about ubuntu prior to this and finally convinced her to switch over as she wasn't all that happy with XP anyways, on another note either am I, Vista really irritates me!  Thanks for your reply though!

Phantom

---

### Post by melojo on 2008-12-31
It almost sound to me like your moms cdrom cannot read cd-r or cd-rw or dvd-r or dvd-rw.  What is the make and model of the cdrom?

---

### Post by phantom1121 on 2008-12-31
> **melojo said:**
> It almost sound to me like your moms cdrom cannot read cd-r or cd-rw or dvd-r or dvd-rw.  What is the make and model of the cdrom?

The make of the CD drive is a Mitsumi CD-R/RW drive.. The model number is CR-4809TE..  However it worked fine before how it could have gone bad in a day is beyond me..

---

### Post by melojo on 2008-12-31
You would think that since it is a cd-r/rw it should be able to read the one you burned. If you had another cd or dvd rom that you could throw in the system and test it that would eliminate the drive not being able to read the media you burned.  This is the only thing I can think would be the problem.  The xp cd is not cd-r/rw format, so that's why it leads me to believe its the drive.

---

### Post by phantom1121 on 2008-12-31
> **melojo said:**
> You would think that since it is a cd-r/rw it should be able to read the one you burned. If you had another cd or dvd rom that you could throw in the system and test it that would eliminate the drive not being able to read the media you burned.  This is the only thing I can think would be the problem.  The xp cd is not cd-r/rw format, so that's why it leads me to believe its the drive.

The disk I burned is in an ISO image bootable format like the XP disk, I'll try to swap out our drive for hers and see if that helps but I don't think that it's the drive.

---

### Post by logos34 on 2008-12-31
> **phantom1121 said:**
> The disk I burned is in an ISO image bootable format like the XP disk, I'll try to swap out our drive for hers and see if that helps but I don't think that it's the drive.

Sounds to me like the drive is fine, but it's having trouble reading the CD for some reason...a disc may work in one machine/drive and not in another...Try burning another copy really slow, 2x-4x...Or if you burned a cd-rw, try a cd-r next, or a different brand...That's what I'd try.  The next step after that would be to boot from a live usb if the desktop supports it

---

### Post by melojo on 2008-12-31
> **phantom1121 said:**
> The disk I burned is in an ISO image bootable format like the XP disk, I'll try to swap out our drive for hers and see if that helps but I don't think that it's the drive.
Not all cdroms and cd players are able to read cd-r media.  The xp disk is not burned in cd-r/rw media its stamped.  The firmware in the cdrom determines if it can read certain type of media.

---

### Post by melojo on 2008-12-31
here is a good guide on cdrom formats
[http://www.pcguide.com/ref/cd/format-c.html](http://www.pcguide.com/ref/cd/format-c.html)
[http://en.kioskea.net/contents/pc/cdrom.php3](http://en.kioskea.net/contents/pc/cdrom.php3)

---

### Post by melojo on 2008-12-31
> **logos34 said:**
> Sounds to me like the drive is fine, but it's having trouble reading the CD for some reason...a disc may work in one machine/drive and not in another...Try burning another copy really slow, 2x-4x...Or if you burned a cd-rw, try a cd-r next, or a different brand...That's what I'd try.  The next step after that would be to boot from a live usb if the desktop supports it

He could also try burning it from another drive not the one he used before.

---

### Post by logos34 on 2008-12-31
> **melojo said:**
> he could also try burning it from another drive not the one he used before.

+1

---

