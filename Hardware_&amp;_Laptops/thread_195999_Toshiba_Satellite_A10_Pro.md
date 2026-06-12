---
title: "Toshiba Satellite A10 Pro"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by The Cosmic Hobo on 2006-06-13
I posted a [similar thread]("http://ubuntuforums.org/showthread.php?t=195715") to this one over in the Absolute Beginners section of the forum earlier in the day, but it occurred to me about ten minutes ago that this would be a far better place to ask!

I've got a Toshiba Satellite Pro A10, 2GHz Intel Celeron processor, 256MB RAM (presumably DDR), 20GB hard disk, onboard graphics and sound.
Earlier in the day I burned a Dapper CD and have had limited success running it in "live" mode (it boots, and the USB mouse, touchpad and sound all work, and I can't see any graphics-related problems) - even the screen brightness keys work all right! The only problem I've had is that the optical drive (CD-RW/DVD) grinds constantly, and Ubuntu runs very slowly, but I suspect that's purely because I'm running it as a live CD with relatively little RAM. I'm quite relieved by this, because last time I tried any live CDs on this machine (a couple of years ago), the optical drive got screwed up and I had to send it off for repairs.

Before I copy all my personal files off XP and pop my freshly-burned [Darik's Boot and Nuke]("http://dban.sourceforge.net/") CD in the drive to scrub all traces of Microsoft off my HD, is there anything I should know, like known issues with the laptop hardware?
Also, are there any special applications, tweaks, configuration settings etc. that I need to be aware of to make my laptop function "normally"? Under Windows, for example, I can't use the normal control panel section for power settings - I have to use Toshiba's own application. I'm also wondering how Ubuntu handles the other function hotkeys, hibernation, and more demanding use of motherboard graphics and sound (gaming, DVD playback and such).

Thanks in advance for any help; I'm off to see what I can find by way of general advice to new users, information on USB floppy drives, or specific tips for my printer (Epson Stylus C62) and digital camera (Canon PowerShot A620).

---

### Post by daller on 2006-09-17
If you run the Live CD with no other issues than the ones you have posted, then I'd go for it!

Nice to see that you are not considering Dual-boot!

As for the hotkeys:

```
Use Keytouch:
 
 [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)
 
 .deb packages are available from sourceforge!

 There's an extensive HOWTO on the site to help you. 
 It worked for me.
```

If any problems whatsoever, please just contact me! (Here, or through a personal message...)

---

### Post by Dale61 on 2006-09-17
I first tried the Live CD on my Satellite A30, and everything was working fine.  Graphics, sound, etc all were as normal, and I could even connect to the internet.

It seemed as though there weren't any problems after running this way for a couple of days, so took the plunge and went the clean install route.  This is when all my problems began.

Overall, it took just under FOUR days to sort out most of the problems I didn't have when running the Live CD.

Finally got sound to work, but I had to read a lot of forums to find the CORRECT fix.

However, I still don't have internet access on my laptop due to modem being inaccessible.  From what I've been able to work out, it is an AC'97 based modem, and there is nothing on the install CD in the way of drivers, etc, for this modem.

I have been advised, on numerous occasions, that I need to download this and download that, but without modem / networking capabilities, how would this be possible?

Hobo, if I were you, if everything is working when you use the Live CD, then I'd suggest you got the dual boot option, or else you could end up like me and have a laptop that's doing nothing but gathering dust.

---

