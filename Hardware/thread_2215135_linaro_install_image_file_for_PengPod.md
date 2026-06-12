---
title: "linaro install image file for PengPod"
date: 2014-04-04
forum: Hardware
---

### Post by djheadley on 2014-04-04
I bought a Pengpod 1000 last year on which I dual boot Android and Linaro (Linux).  When I ordered it I thought that an 8GB micro SD card would be large enough, it's not.  I have tried to find a disk image to install on a 16GB micro SD card but every time I download it I get a message when unarchiving it that an unexpected EOF was found.  The file I got was the one listed in the WIKI.

I know the company is closed but I REALLY LOVE my PengPod!

Is anyone out there using a Pengpod 1000 and could you please send me the URL or maybe I could send them the money for a 16 GB micro SD card with either the clean disk image or even one with Linaro installed.  I am getting desperate.

---

### Post by djheadley on 2014-04-08
I've been thinking (dangerous, I know) that maybe I could clone the 8gb MicroSD card onto the 16gb MicroSD card.  How would I go about this.  

The only other working computer that I have is a laptop running 12.04 with a non-working dvd burner, large USB hub and SD card Reader built in to the laptop as well as an external SD card Reader.  There are so many problems with the laptop that I should have scrapped it last year but I'm glad I didn't because my desktop quit a couple of months ago and it might be another couple of months before I can get a replacement.

---

### Post by djheadley on 2014-04-09
bump

---

### Post by XpineX on 2014-09-08
Hi,

I know this is a little late, but just in case you still have not managed to move you linaro to your 16GB card, here is a short howto:

Use your laptop to create an image of your 8GB card:
dd if=/dev/mmcblk0 of=my8GBcard.img bs=1M
where /dev/mmcblk0 is the path to the SD card device, could also be something like /dev/sd[bcd]

When the image is created (it takes a long time and there is no progress indicator) you swap the SD cards in you laptop and restore the image to the 16GB card.
dd if=my8GBcard.img of=/dev/mmcblk0 bs=1M
Again, make sure that you use the correct device name for your SD card.

When the image has been written to you 16GB SD card, you use gparted to extend your partition.

---

