---
title: "&quot;Unable to mount SD card&quot;"
date: 2021-07-19
forum: Hardware
---

### Post by juntjoo2 on 2021-07-19
Unable to mount SD card [https://imgur.com/a/tsx38Mj](https://imgur.com/a/tsx38Mj)

I was able to mount another though. What gives? 

I'm using a live disc, 16.0.4 on my old laptop

---

### Post by coffeecat on 2021-07-19
Did you read the error message?

> unknown filesystem type 'exfat'

Exfat is not supported out of the box in Ubuntu 16.04. When it was possible to install packages in 16.04 - before it became end of life - you probably could have installed those packages needed to support exfat. That's all theoretical though. Don't use 16.04. It went end of life at the end of April last. If you use 20.04 you'll get native support for exfat without having to install anything.

> **juntjoo2 said:**
> I was able to mount another though. What gives? 


Presumably another filesystem - probably FAT32. Yes/no?

---

### Post by juntjoo2 on 2021-07-19
So how do I install it?

I tried from a suggestion elsewhere and got "could not open lock file /var/lib/dpkg//lock - open (13: permission denied)"
Then:
"unable to lock the administration directory (/var/lib/dpkg/), are you root?"

---

### Post by ajgreeny on 2021-07-19
> **juntjoo2 said:**
> So how do I install it?

I tried from a suggestion elsewhere and got "could not open lock file /var/lib/dpkg//lock - open (13: permission denied)"
Then:
"unable to lock the administration directory (/var/lib/dpkg/), are you root?"
You don't!
You simply need to download an .iso image of a supported version of Ubuntu (20.04 suggested by coffeecat), write that image onto a USB flash drive as you presumably did for 16.04, and without installing anything you should be able to mount and read the exFat filesystem on the SD card.
Installing anything on 16.04 is almost impossible now as the repositories have all been closed and moved to EOL URLs; it's simply not worth the hassle to continue using 16.04, nor is it safe and secure to do so.

---

### Post by juntjoo2 on 2021-07-19
No I didnt. I put it on disc. So this is my first time awe that I'm "burning" to an SD card so be gentle on me

Yeahx I just don't know if it's worth trying to do any "burning" with this old laptop and external disc drive. Plus I'll be using this old Ubuntu disk

---

### Post by ajgreeny on 2021-07-19
> **juntjoo2 said:**
> No I didnt. I put it on disc. So this is my first time awe that I'm "burning" to an SD card so be gentle on me

Yeahx I just don't know if it's worth trying to do any "burning" with this old laptop and external disc drive. Plus I'll be using this old Ubuntu disk
No you didn't what? And what did you put on disk?
And please explain what you mean by *"this is my first time awe that I'm "burning" to an SD card"* as I do not understand; are you trying to burn an iso image file to the SD card?
If that is what you did in order to create a live bootable OS, you will need to check with your hardware that it can boot from an SD card; in many cases that used to be possible only if the card is put in a USB card reader rather than an SD card port on the machine.

---

### Post by juntjoo2 on 2021-07-19
[https://websiteforstudents.com/how-to-enable-exfat-filesystem-support-on-ubuntu-16-04-18-04/](https://websiteforstudents.com/how-to-enable-exfat-filesystem-support-on-ubuntu-16-04-18-04/)

I used the above and got:

Exfat installed in Ubuntu 16.0.4 [https://imgur.com/a/0tm8maz](https://imgur.com/a/0tm8maz)

Wutcha gonna say now?

---

### Post by juntjoo2 on 2021-07-19
Anyone want to send tips in exchange for my Ubuntu 16.0.4 expertise pm me I'll give you my PayPal

No I'm kidding. I just needed to unload my phone before I figure out how to get this OS installed on my laptop. 
It's moving like molasses though

I explain in another thread I have a CD.

Prob is external disc drive might be causing even the old 16.0.4 install to fail.

---

### Post by juntjoo2 on 2021-07-19
So now I'm learning how to put it on a SD card. But honestly at this copy to hdd rate it's currently going idk that it will be any better than my CD drive. I think it'd stuck at 1.6gigs copied of 28gigs and it's been 20 min at least

---

