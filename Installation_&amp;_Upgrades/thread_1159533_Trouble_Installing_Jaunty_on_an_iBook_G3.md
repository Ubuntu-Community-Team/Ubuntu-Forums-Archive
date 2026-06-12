---
title: "Trouble Installing Jaunty on an iBook G3"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by Nickel1010 on 2009-05-14
I'm having a heap of trouble installing Jaunty on my friend's iBook G3, and I'm not really sure what's going wrong.

It had an open firmware password on it (It was a school laptop that he bought from his mom, the tech administrator at the school) and I took out some RAM and zapped the PRAM from it to get rid of that. When I put the RAM back in, and zapped it again, the password was back. So I took the RAM back out, zapped it again, and tried to boot from the CD. 

I tried holding down C while it booted, which only resulted in the disk drive spinning, and stopping, and spinning, and stopping over and over again, then eventually going to the Mac boot logo.

I tried holding Option down while booting, which brought me to the drive select. The first time I tried it, the disk spun for a while, then the CD showed up. I tried to load it, but the same thing happened. It kept spinning and stopping and spinning...

I need to install it with the extra RAM in there, because otherwise it only has like 128 RAM...

I'd really like some help soon, because I'd like to get this done by tomorrow so I could give it to him at school before the weekend!
Any help is greatly appreciated!

---

### Post by Nickel1010 on 2009-05-14
Okay, I got the Open Firmware password to go away now, I guess I only needed to zap the PRAM after I took out the RAM, then just put it back in.

I still need help on why the disk doesn't boot though!
Any help is appreciated!

---

### Post by Nickel1010 on 2009-05-14
I don't mean to triple post, but I figured that I would post that the iBook recognized the disk, and it loaded yaboot. 

I typed "boot: live" and it started booting, loaded the kernel, and started loading Rom-something (I can't remember the exact name, sorry) and then I got a message like "Invalid ROM data" or something (Also can't remember the exact name, it was only there for a moment...) Then it got hung up on a black screen.

I had to manually shut down, then I tried again.

This time, I typed "live video=ofonly", and it looked like it was loading without the problems indicated before. It went to a black screen with a white line in the upper left corner, and stayed there for a while. The CD drive was turning and it sounded like it was working so I just left it alone. Then the display changed and I saw the login screen for Ubuntu! I let it automatically login, then it went to the Live CD session! As of right now, it's 99% done installing. I'll post my results so that anyone else has this problem they'll be able to solve it.

---

### Post by Nickel1010 on 2009-05-16
Well, it was at 99% because it got hung up. I shut it down and it doesn't boot as of right now... Not really sure what went wrong. I'm going to try again though. I'll post the results of that attempt also...

---

