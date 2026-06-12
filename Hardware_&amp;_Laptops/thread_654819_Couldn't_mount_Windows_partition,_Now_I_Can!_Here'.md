---
title: "Couldn't mount Windows partition, Now I Can! Here's the story."
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by irv on 2007-12-31
This pertains to my laptop with a 60gig Hard Drive. A few months ago I was running low on Hard Drive space on my Ubuntu 7.10 install so I need to capture some space from my XP partition. I did this using gparted. It was simple to do I just booted with gparted live CD and resized my XP partition. Then I made my Linux partition larger. I now have 40gig for Linux and the rest for XP.
Now after doing this I found that Linux did not see my NTFS XP partition. I saw a “fail” at boot time when it tried to mount the Windows partition (NTFS). Well, I never really need it so I just ignored the fail message.
Today I was thinking about just deleting the NTFS partition because I never go into window any more. Before doing this I had to move my boot flag from NTFS to Linux partition. I booted with gparted again and move the flag. I thought I better try booting again to see if everything would work right. I first booted into winXP and then Linux. Everything worked great and now I don't get the “fail” error when mounting the windows partition. Maybe just going into widows for the first time since resizing it did the trick. I don't really know, I just know it works again. I even got my windows icon back on my Linux desktop.
I just thought I would pass this information on in case someone else has had this problem.
Irv

---

