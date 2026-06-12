---
title: "Having Issues with a Dual Boot"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by Asphalt404 on 2009-08-24
I am wanting to fall in love with Linux after being an avid microsoft fanboy for years.  I have had enough of Vista but can't completely get rid of it for work reasons.  My current configuration of hard drives consists of 2 hd's in a mirror of os and 2 more in a stripe.  I was wanting to do a dual boot for linux onto a new drive.  I added a new hd and preceeded to load unbuntu onto the new HD.  Now I can still boot into windows and in the disk manager i can see the new hd i added but when i go into the boot manager in my bios and change my new hd to the top of the bootlist and try boot into linux It stops on a black screen with a underscore flashing.

I hope I explained this well enough, I could really use some help as i look forward to my first wonderful experience with linux

My system is

intel core i7 2.66GHz
Asus p6t deluxe
sapphire radeon hd 4870 x2
6gig corsair ram
2x 80 gig hd's in mirror (sata)
2x 250 gig hd's in stripe (sata)
and a new 150 gig hd I just added (sata)

Current os is vista 64 ultimate :^(

---

### Post by jtravnick on 2009-08-24
OK now this is the way I do it don't know if its the right way or not but it works for me.

First thing I do is make sure windows is installed where I want. From what you say sounds like you have that all set.

Next I pull all power from my windows hardrive and plug in the harddrive that I want to install Ubuntu to. So you should only have the one harddrive with power. Go to Bios and make sure it sees only that harddrive. Also at that time set DVD drive to boot. 

Boot to the cd and install Ubuntu putting grub on that harddrive. Once its done you should be able to boot to Ubuntu 

Once you know Ubuntu will boot plug your windows drive back in.

Now doing it this way has a couple of problems first the drive with Ubuntu has to be the drive the bios is booting to first. I usaly have that as my master drive anyway so no big deal to me.

Second you will have to go in and edit menu.lst to boot into windows.

Hope this helps if you get this far than post back and we can help you edit the menu.lst to get you into windows.

Jim

---

