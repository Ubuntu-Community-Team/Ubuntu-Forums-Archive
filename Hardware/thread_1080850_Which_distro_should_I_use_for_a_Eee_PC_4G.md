---
title: "Which distro should I use for a Eee PC 4G?"
date: 2009-02-25
forum: Hardware
---

### Post by wtfitsjared on 2009-02-25
Howdy, I really want to install ubuntu on my new netbook, and was wondering which specific distro I should use/can I use?

---

### Post by bgates on 2009-02-25
I am using Eeebuntu Base on mine.  [http://eeebuntu.org/index.php?page=base](http://eeebuntu.org/index.php?page=base)

I have the 16GB SSD but I'm only using 3.5 GB and I've installed a bunch of apps.

All the hardware works great for me but you can of course check it first using the LiveUSB.

---

### Post by sgosnell on 2009-02-25
I like Cruncheee.  It's Crunchbang optimized for the EEE.  It's a minimal desktop, if you can even call it that, being just Openbox, doing everything via menus starting from a right-click on the 'desktop'.  It works out of the box on a 701, and has the smallest footprint I've found, leaving the most room on the small SSD.  If you want to invest a little money, get a larger SD card and install the distro of your choice on that.  I have a 16GB card and have had as many as 3 distros on it at once.  This also has the advantage of leaving the stock SSD intact, and permitting lots of trials of distros easily and quickly.  I settled on Cruncheee on my 701, but I'm running the full Ubuntu on my 900.  I don't use the 701 that often since I got the 900, so a light feature-poor distro that works is good enough.

---

### Post by ShakataGaNai on 2009-02-25
I'm running Jaunty Netbook Remix on my Eee 1000 and it is working great.  Yes, it is still in Alpha but if you don't mind something possibly breaking, or waiting for the release - I'd suggest it.

---

### Post by Sami_Sdata on 2009-02-25
I running Eeebuntu on my 900 on a 4G SSD.  With lots of apps installed I still have 1.6G free.  I keep my home directory on a 16G SDHC.  I've also run Crunchee on the same machine.  With Crunchee I got a little more space left on the drive.  I just switched back to Eeebuntu because my 9 year old uses this machine at times and Crunchee was a little confusing to him.

---

### Post by Hobgoblin on 2009-02-25
I use Ubuntu Intrepid with the array.org kernel on my 701SD.

---

### Post by wtfitsjared on 2009-02-26
> **sgosnell said:**
> I like Cruncheee.  It's Crunchbang optimized for the EEE.  It's a minimal desktop, if you can even call it that, being just Openbox, doing everything via menus starting from a right-click on the 'desktop'.  It works out of the box on a 701, and has the smallest footprint I've found, leaving the most room on the small SSD.  If you want to invest a little money, get a larger SD card and install the distro of your choice on that.  I have a 16GB card and have had as many as 3 distros on it at once.  This also has the advantage of leaving the stock SSD intact, and permitting lots of trials of distros easily and quickly.  I settled on Cruncheee on my 701, but I'm running the full Ubuntu on my 900.  I don't use the 701 that often since I got the 900, so a light feature-poor distro that works is good enough.

So, I could run the full Ubuntu distro off of a 8GB SD Card?  I didn't even know that was possible.

---

### Post by StephenOK on 2009-02-26
> **wtfitsjared said:**
> So, I could run the full Ubuntu distro off of a 8GB SD Card?  I didn't even know that was possible.

Yeah, I think I remember even having a Mandriva distro running on a really small SCSI. Since it was a computer that someone threw away, I just dropped an old SATA drive in it and gave it to my Brother with Ubuntu 8.10 installed - works great!

---

### Post by Sami_Sdata on 2009-02-26
> **wtfitsjared said:**
> So, I could run the full Ubuntu distro off of a 8GB SD Card?  I didn't even know that was possible.

/dev/sda1              3874076   2060456   1616828  57% /

 That's my 4gig with Eeebuntu installed.  I removed the office apps since I don't use them.  I have installed skype, gwibber, audacity, gnome-games, and other apps. Still a good deal of room left. I use a 16gig sdhc for my home so I can download larger files.

---

### Post by Hobgoblin on 2009-02-27
> **wtfitsjared said:**
> So, I could run the full Ubuntu distro off of a 8GB SD Card?  I didn't even know that was possible.

I have the full, normal Intrepid installed and running on an old laptop with a 4GB hard drive with space to spare.

---

### Post by sgosnell on 2009-03-01
Yes, you can run any distro that I know of off an SD card.  You can easily run a full Ubuntu from the SD card.  During the install, at the last step just before you click Install, click on the Advanced button and have it install the bootloader to the SD card.  It's probably (hd1) instead of (hd0), which is the SSD.  If you put it on the SSD, you can't boot without the SD card inserted, unless you reinstall grub to the SSD.  That's not hard, and the instructions are in a thread here, but it can be annoying the first time you face it, especially if you don't have a boot SD handy.

---

### Post by magian on 2009-03-27
I have tried them all and Cruncheee is by far the best.

---

