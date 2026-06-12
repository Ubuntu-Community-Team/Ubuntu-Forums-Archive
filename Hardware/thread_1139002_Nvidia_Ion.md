---
title: "Nvidia Ion"
date: 2009-04-26
forum: Hardware
---

### Post by solitaire on 2009-04-26
Does anyone know if the new "[Nvidia Ion]("http://www.nvidia.com/object/sff_ion.html%5DNvidia%20Ion")" Graphics chipset works well within Ubnutu?

I'm picking up the Acer Aspire Revo nettop box in a couple of weeks and i'd love to find out if i can use the Ion chipset to it's full (e.g. 1080p playback).

---

### Post by The Cog on 2009-06-14
Re-awakening an old thread, but I have just got the answer.

I am using Jaunty. The default install didn't even really recognise that the card was a nvidia card. The mesa drivers worked in 800*600 but the system->Administration->Hardware Drivers utility didn't offer to install the nvidia drivers. I installed by hand and they didn't recognise the card either. 

But the version 185.18.14 drivers from the nvidia website work beatifully. Google for nvidia driver download.
To install them, do this:
```
sudo aptitude install build-essential
chmod +x NVIDIA-Linux-x86-185.18.14.pkg1.run
sudo ./NVIDIA-Linux-x86-185.18.14.pkg1.run
```
Let it reconfigure your xorg.conf file. Then reboot.

P.S.
I ordered the Linux version, and was surprised to find it had a 160G HDD instead of the expected (and ordered) 8G SSD. Result!

To get the revo to boot from the Ubuntu USB stick, I had to go through the Revo-Build utility as though to install windows, and leave the product key form blank. Then it says "formatting disk". Until you have done this, it will not attempt to boot from either the HDD or a USB stick, regardless of the BIOS settings. That took me a while to figure out!

My Revo had 4 partitions. I wasn't sure what the first 3 were, so I left them alone and just replaced partition 4 (the big one) with an extended partition, and put all my Linux partitions in there.

I'm **very** happy with it.


P.P.S.
It's not all sweetness and light. I haven't yet figured out how to make sound come out through the HDMI lead to the telly - currently using the headphone output to drive the stereo. If anyone can figure that one out, I'd be grateful.

---

### Post by fuzzmo on 2009-06-14
> **The Cog said:**
> Re-awakening an old thread, but I have just got the answer.

I am using Jaunty. The default install didn't even really recognise that the card was a nvidia card. The mesa drivers worked in 800*600 but the system->Administration->Hardware Drivers utility didn't offer to install the nvidia drivers. I installed by hand and they didn't recognise the card either. 

But the version 185.18.14 drivers from the nvidia website work beatifully. Google for nvidia driver download.
To install them, do this:
```
sudo aptitude install build-essential
chmod +x NVIDIA-Linux-x86-185.18.14.pkg1.run
sudo ./NVIDIA-Linux-x86-185.18.14.pkg1.run
```
Let it reconfigure your xorg.conf file. Then reboot.

P.S.
I ordered the Linux version, and was surprised to find it had a 160G HDD instead of the expected (and ordered) 8G SSD. Result!



Thanks for posting the guide.  BTW where did you order it from and how much did you get it for?  I heard that once the 8gig SSD versions had sold out they would be supplying the units with 160gb for the same price....

---

### Post by The Cog on 2009-06-14
I ordered it from here:
[http://www.simplyacer.com/Acer_Aspire_Revo_625111.html](http://www.simplyacer.com/Acer_Aspire_Revo_625111.html)
I don't know if the 160G disk was a mistake. I'm not complaining though. The Acer part-number sticker on the box says 160G disk and has the same part number as the web site - 92.G1DYZ.UF0. If I could be sure of getting a disk next time too, I'd order another one tomorrow.

P.S.
Free delivery for orders over £150, so I ordered another mouse, too,

---

### Post by solitaire on 2009-06-14
> **The Cog said:**
> I ordered it from here:
[http://www.simplyacer.com/Acer_Aspire_Revo_625111.html](http://www.simplyacer.com/Acer_Aspire_Revo_625111.html)
I don't know if the 160G disk was a mistake. I'm not complaining though. The Acer part-number sticker on the box says 160G disk and has the same part number as the web site - 92.G1DYZ.UF0. If I could be sure of getting a disk next time too, I'd order another one tomorrow.

P.S.
Free delivery for orders over £150, so I ordered another mouse, too,

They did say that only the first batch of Linux Revo's would have the 8Gb SSD's once they were sold out, they would all get 160Gb Drives instead.

---

### Post by The Cog on 2009-06-17
I just found this excellent guide, so I thought I'd add it to this thread:
[http://www.greenhughes.com/content/how-install-ubuntu-and-boxee-acer-aspire-revo](http://www.greenhughes.com/content/how-install-ubuntu-and-boxee-acer-aspire-revo)

I'll try to fix the HDMI sound as soon as my wife gets off the telly.

---

