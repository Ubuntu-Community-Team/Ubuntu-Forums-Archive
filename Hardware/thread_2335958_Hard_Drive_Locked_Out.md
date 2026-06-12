---
title: "Hard Drive Locked Out"
date: 2016-09-02
forum: Hardware
---

### Post by jakeolantrn87 on 2016-09-02
So a few weeks ago, I made the switch from Windows 10 completely over to Ubuntu. I had done a lot of homework, then made a Live USB using Rufus. I partitioned my HDD and went to install Ubuntu and got Input/output error during read on /dev/sda. The Laptop I'm using is a Dell Latitude D830, with a Toshiba 1TB HDD. So I id some research and ran my drive through test disk to figure out what was going on. Test disk said my drive Failed and would be failing soon. which I found hard to believe because its only 5 months old. So after running it under DBAN and letting it sit for two weeks I decided to see what was wrong. Ran Revitalize off Hiren's Boot and it pulled 67 Bad sectors. Of course being a trial it only repaired one. I went to reboot the next day only to find out it was locked out using Dell's Built in Security from Bios. I checked my Bios to find there was no master password. So after doing so various research via Google I tried setting a Master Bios Password thinking it would over write the HDD. Of course it didn't work. I've tried using various software on my desktop to see if I could crack the password or at least remove it and nothing has helped. I use my laptop far more often than my desktop, and It would be great and a huge money saver to not have to order a new drive. If possible I'd like to revive the one I have currently by at least unlocking it and being able to repair the remaining bad sectors if repairable. The HDD is a Toshiba 1TB if that helps.

---

### Post by Bucky Ball on 2016-09-03
This really has nothing to do with Ubuntu, but take the CMOS battery out for a minute or two then reinsert. The password will be gone. You can also short the jumpers by moving the little bit of metal over to the opposite jumper pins. You need to check how to do that on your machine if you go that way. Removing battery easiest. You'll find it on the motherboard somewhere. Small, silver, round, lying flat in a battery bracket on the motherboard.

PS: A full explanation of how to remove the battery will no doubt be [found somewhere here]("https://duckduckgo.com/?q=reset+bios+password&t=h_&ia=web").

---

