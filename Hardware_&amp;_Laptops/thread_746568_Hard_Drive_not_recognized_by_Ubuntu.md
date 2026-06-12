---
title: "Hard Drive not recognized by Ubuntu"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by uberben on 2008-04-05
Hello all,

A couple of weeks ago I installed Ubuntu Studio on an old computer I had lying around and it installed perfectly and ran fine for a few days. Then I decided to add an IDE PCI card to the computer so that I could use it as a disc duplicator. After adding this card and extra CD-RWs, the computer takes much longer to post and then it gives me an error when it tries to boot from the hard drive. I tried popping in the installer disc again to fix the issue (thought that it just needed a driver for the new card) but the disc couldn't access the drive either and gave me a list of about 100 drivers to choose from to access the drive. I tried about 20 of them before I decided it was a waste of time. Next I tried removing the IDE card to see if I could get the system back to the way it was, but no dice. It still takes a while to post and still cannot boot from the hard drive. At this point I decided I would try to reformat and see if that helped at all, but the same issue as the repair option came up again: list of hard drive drivers. The bios is recognizing the drive fine and it was working previously. Does anyone have any ideas? 

The only other thing i changed when i had the thing open was I unplugged a DVD-ROM drive from the IDE cable the hard drive was plugged into because that DVD drive was not being detected in Ubuntu (but I could boot from it). The way I have the drives plugged in now is the hard drive as the primary master, a DVD-RW as the secondary master, the DVD-ROM as the secondary slave (it was the primary slave), and 2 CD-RWs each with their own IDE cable attached to the IDE PCI card, both with jumpers set to master.

Thanks,

Ben

---

### Post by uberben on 2008-04-07
No ideas?

---

### Post by bigbudz on 2008-04-11
I seem to be having a simalar problem. Here's my post. 

[http://ubuntuforums.org/showthread.php?t=751883](http://ubuntuforums.org/showthread.php?t=751883)

Wish I could help...

---

### Post by uberben on 2008-04-11
I meant to post this earlier, but since the thread was inactive I forgot. Anyway, I got it fixed. Turns out that when I had the DVD-ROM and hard drive on the same IDE cable, it wanted the drives jumpers set to slave and master, respectively. Once I took the DVD-ROM off the cable, however, it slowed the post down to a crawl. After several futile attempts at fixing it, I just tried setting the hard drive's jumper to cable select for the heck of it. Booted up fine right away. Unfortunately, I am now having an issue with graphics. I decided to reinstall Ubuntu Studio since I had a fairly blank install on there previously and wanted to make sure that the new disc drives (and more importantly their add-on IDE card) were recognized and installed properly. 

Unfortunately, after the install when I boot into the new system, I just get a bunch of randomized green pixels at the top third of the display. I did everything basically the same as the last time I installed Ubuntu except that last time I had a different monitor plugged in during the install (last time was an old CRT and this time I had it plugged into the display it will be left on; my Samsung HDTV). I booted back into the Ubuntu Studio disc and went to the "repair broken system" setting, or whatever it is called, and got to a point where I had a terminal from my installed system, but there was no X11 folder where I could go and edit the xorg.conf file manually. I haven't had a lot of time to try and get stuff working again, but I will probably try booting into a live CD and copying that folder over (provided the live CD can get a display) and if that still fails, I'll try reinstalling again with the CRT and then transferring over. I know that I had to put a custom resolution into xorg last time so that it would display properly on my tv, but without that resolution it was just a shifted image, not a bunch of garbage. 

If anyone has any other ideas for the display issue, let me know.

Ben

---

### Post by uberben on 2008-04-12
Well, I figured out my display issue. Turns out I had one of the CD burners plugged into the IDE PCI card wrong; pin one on the CD drive was in pin 20 or w/e on the card and vice-versa. Swapped it around and it booted up without a hitch and all drives are able to read discs now! I haven't tested to see if any of them burn yet and I'm too cheap to burn discs with no purpose, so the next time I need to burn something, we'll hope it all works flawlessly.

---

