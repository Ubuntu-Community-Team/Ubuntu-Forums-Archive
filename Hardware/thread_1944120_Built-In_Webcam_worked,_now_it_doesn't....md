---
title: "Built-In Webcam worked, now it doesn't..."
date: 2012-03-20
forum: Hardware
---

### Post by helobubba on 2012-03-20
Hello--

I am running Xubuntu 11.10 on an HP Envy 14 Laptop.  My webcam has worked fine without any setup under 11.04 and also on my first install of 11.10.  On my second install, the only thing I did differently was that I was not connected to the internet.  Somehow, I can only guess that this is the reason my built-in webcam is now not detected.

There is no device that I can find listed when I run lsusb or lspci.  There is nothing under /dev/video0 either.  Running a program like cheese is also of no use, since my laptop is behaving as if there is no webcam at all.  Not sure what I have to do to start the webcam recognition process started.  Unfortunately, re-installing with wifi available is not an option I have right now.

Thanks for any help you could provide!

Best,
Bubba

---

### Post by IWantFroyo on 2012-03-20
Could you please post your computer model? We'll be able to find out what type of webcam it has from that, and then we'll be able to hopefully find drivers for it.

---

### Post by helobubba on 2012-03-20
Sorry: HP ENVY 14t-1200 CTO Notebook PC, Beats Edition

To Amplify: on the previous two installs for 11.04 and 11.10, I was connected to the internet during the installs and the Xubuntu install routine had me set up my web cam automatically (by taking my picture, etc.).  This is why I think the internet and the install are linked...

Thanks for your help!

- Bubba

---

### Post by helobubba on 2012-03-25
OK, it is an HP Truevision HD Webcam.  Still having trouble getting it to work.  Appreciate any help you could provide.

Thanks!

- Bubba

---

### Post by helobubba on 2012-04-01
OK, I am pretty sure the webcam is just plain dead.  From trolling other help websites, my particular model should show up on lsusb (vice lspci).  It does not, and since lsusb doesn't care whether a device has a driver or not - only if it is attached - it must mean the webcam is dead.  Incidentally, further proof of this theory was given to me by another of my plug-in usb devices; it also died completely, and whereas before it showed up with lsusb, now it does not.  I guess I'm pretty much talking to myself here, but the whole point of this board is learning, so maybe someone will read this and learn.

Cheers,
Bubba

---

### Post by ahallubuntu on 2012-04-01
How about booting your 11.04 CD again and see if it works/is recognized there?  There is a big difference between 11.04 and 11.10: 11.10 is a leap to the 3.0 kernel which could break (or fix) hardware.

Can we assume you've updated 11.10 to the latest updates (so latest kernel)?

Any chance one 11.10 install was 32 bit and another 64 bit?  That could make a big difference in the kernel drivers.

FYI, it is possible to replace a bad webcam in a laptop.  I recently added a webcam to a laptop that did not have one built in.  That model was originally sold with the webcam as an option; all I had to do was buy the correct webcam and a new screen bezel that had a cam port (I bought both on eBay).  There's also a cable running from the webcam behind the screen down to the motherboard where it plugs in.  Removing the bezel/screen can be tricky (you could crack the bezel), but you could also try removing the keyboard to see where the webcam plugs in - it's also remotely possible it simply came unplugged (from either the motherboard side or the webcam side) or that the cable has frayed or something.  It's also problem you're looking at a motherboard issue and the webcam itself is fine...

But a hardware issue still sounds unlikely to me.  I'd boot up the 11.04 CD again and see if you can get the cam recognized there first with lsusb .

---

### Post by helobubba on 2012-04-06
Ahallubuntu:

Well, that would make good sense (the 11.10 vs 11.04 part), except that the is the *second* time I have tried 11.10 (via the same live USB stick install).  The previous time the webcam did work...and I do have all the updates installed as well.  This is what makes me think it is a hardware issue.

Thank you VERY much for the hardware info.  I think this could be a possibility.  Between when it worked, and when it didn't, I actually did get into the laptop guts to swap out a DVD drive, and reading your reply it dawned on me that maybe in the process I accidentally loosened the webcam connection to the motherboard.  I will have to check that out!!

Really appreciate the help.  I will get the maintenance manual, open up the computer, and report back with hopefully some success.

Cheers,
Bubba

---

