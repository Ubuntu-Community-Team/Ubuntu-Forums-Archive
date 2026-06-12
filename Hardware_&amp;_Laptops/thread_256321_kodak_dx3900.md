---
title: "kodak dx3900"
date: 2006-09-12
forum: Hardware &amp; Laptops
---

### Post by dogeatery on 2006-09-12
I have a Kodak DX3900 point-and-shoot digital camera that has always worked fine with Ubuntu.  One day it decided that it didn't want to work.  Ubuntu used to recognize the camera was plugged in and automatically start a program to receive the photos from the camera.  Now I have to do it manually.  But there's more-- It will bring up thumbnails of all of my photos but will not allow the photos to be transferred to my computer.   

I get this error message when I try to transfer:

Could not get 'DCP_1715.JPG' from folder '/store_00010001/DCIM/100K3900'.

PTP Protocol error, data expected

I have tried going in through my terminal but when I bring up /dev and list everything it doesn't seem to recognize that there's a camera connected.  Anybody know what this is about?  I think it has been going on since I upgraded to dapper.](*,)

---

### Post by ricardisimo on 2007-09-09
I'm getting the same errors with my Kodak EasyShare C310. I'm having to upload them with my wife's Mac and transfer them from there. Pretty awkward and embarrassing. Any idea what's to be done about this? Thanks in advance.

---

### Post by ricardisimo on 2007-09-10
Here's a bump, by way of a screenshot. The images never do load, not in gThumb, Digikam, showFoto or even F-Spot. In Windows and on my wife's Mac they upload immediately. I've already tried editing etc/udev/rules.d/45-libgphoto2.rules as suggested in several other threads. No result. Others recommend downgrading libgphoto2, but I have no clue as to how one would do that. Thanks again.

---

### Post by ricardisimo on 2007-12-31
The issue is still not resolved. Someone elsewhere said to make sure that my camera is in PTP mode and not USB. What does this mean, and how would I change this? Thanks in advance.

---

### Post by ricardisimo on 2008-01-04
<bump>

---

### Post by ricardisimo on 2008-01-22
It appears that this problem isn't going away anytime soon. In the meantime, is there a way for me to manually mount the camera as a USB mass-storage device, instead of PTP? Thanks.

---

### Post by dogeatery on 2008-03-04
have you upgraded to Gutsy yet?  I finally gave up on the camera and pawned it off on my girlfriend... 

As far as PTP/USB modes, I'm not sure this camera differentiates between the two...

I hate myself for saying this but the best option is probably purchasing a card reader... Or a printer with a card reader

---

### Post by ricardisimo on 2008-03-04
There's no menu option on the camera itself to select USB or PTP, as was suggested to me in an IRC channel. There are, however, two different types of input on it, although I only received one type of cable with the camera. Theoretically, the other one might be to mount it as USB... although honestly I think it's just a remote shutter control connection. Oh, well...

---

### Post by dogeatery on 2008-03-09
The weird thing about it is that it DID mount as USB previously, in the case of mine... and then it stopped

---

### Post by prshah on 2008-03-09
If your camera uses a memory card such as SD or MMC or MemoryStick, it may have lost clusters. Take out the card, stick it into a USB card reader, plug it in to your computer, and run fsck on it.

Maybe, immediately after you plug it in, you can also post the result of the terminal command "dmesg |  grep -15"

Cheers,
PRShah

---

### Post by dogeatery on 2008-03-09
Thanks!  I'll try this later on tonight and post back with results

---

