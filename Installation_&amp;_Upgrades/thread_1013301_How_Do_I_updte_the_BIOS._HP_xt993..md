---
title: "How Do I updte the BIOS. HP xt993."
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by Dwiman89 on 2008-12-16
Hey, Im trying to get upunto on a friends computer, and im encountering a lot of issues. im drawing the conclusion that its a BOIS issue. I have herd mention of updating a systems BIOS(I didnt know you could do that) 

So how would I do it for a HP pavillion xt993? i have no clue where to find the update or how to do it... please help. If its not my issue then at least it will rule it out as a possible issue.

I have drawn the conclusion from this...
[http://ubuntuforums.org/showthread.php?t=1012650](http://ubuntuforums.org/showthread.php?t=1012650)

---

### Post by oilchangeguy on 2008-12-16
> **Dwiman89 said:**
> Hey, Im trying to get upunto on a friends computer, and im encountering a lot of issues. im drawing the conclusion that its a BOIS issue. I have herd mention of updating a systems BIOS(I didnt know you could do that) 

So how would I do it for a HP pavillion xt993? i have no clue where to find the update or how to do it... please help. If its not my issue then at least it will rule it out as a possible issue.

I have drawn the conclusion from this...
[http://ubuntuforums.org/showthread.php?t=1012650](http://ubuntuforums.org/showthread.php?t=1012650)

doing a bios update, or flashing the bios is not going to help your problem. it's most likely a hardware issue. there's no way to know what you've changed in the bios. so go into the bios and set it to use the default settings. then only change the boot order. and set the cd drive as first. also is the computer using the proper ram? just because it fits, does not mean it's correct for the computer.

flashing the bios is not something a novice should attempt. done incorrectly you'll turn the computer into a large door stop.

---

### Post by philetus on 2008-12-16
> **Dwiman89 said:**
> Hey, Im trying to get upunto on a friends computer, and im encountering a lot of issues. im drawing the conclusion that its a BOIS issue. I have herd mention of updating a systems BIOS(I didnt know you could do that) 

So how would I do it for a HP pavillion xt993? i have no clue where to find the update or how to do it... please help. If its not my issue then at least it will rule it out as a possible issue.

I have drawn the conclusion from this...
[http://ubuntuforums.org/showthread.php?t=1012650](http://ubuntuforums.org/showthread.php?t=1012650)


Go here:

[http://h10025.www1.hp.com/ewfrf/wc/product?product=62776&lc=en&cc=us&dlc=en&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/product?product=62776&lc=en&cc=us&dlc=en&lang=en&cc=us)

Be careful

---

### Post by philetus on 2008-12-16
This seems to be yoir motherboard

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07292&lc=en&dlc=en&cc=us&lang=en&product=62776](http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07292&lc=en&dlc=en&cc=us&lang=en&product=62776)

---

### Post by robert shearer on 2008-12-16
from the symptoms described in your other post it may just be the bios battery needs replacing.

Check your earlier post for other suggestions.

[http://ubuntuforums.org/showthread.php?t=1012650](http://ubuntuforums.org/showthread.php?t=1012650)

---

### Post by Dwiman89 on 2008-12-16
Welll from exploring that site there doesn't seem to be a BIOS update, or at least I cant find one...

---

### Post by philetus on 2008-12-17
> **Dwiman89 said:**
> Welll from exploring that site there doesn't seem to be a BIOS update, or at least I cant find one...

You have to search better than that.

Use at your own risk.

[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

1. motherboard
2. socket A
3. A7V(MB)

---

### Post by Dwiman89 on 2008-12-17
> **philetus said:**
> You have to search better than that.

Use at your own risk.

[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

1. motherboard
2. socket A
3. A7V(MB)

Thank you for your help philetus. there are still a lot of optional downloads. I dont want to sound like an idiot but can you help me pick the right one. Considering the consequences of picking the wrong one I would like guidance. Although the way I see it this thing is going to be bricked ether way if no solution is met...

[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

---

### Post by Dwiman89 on 2008-12-17
I did find this just now....

[http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&lc=en&softwareitem=pv196en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&lc=en&softwareitem=pv196en&jumpid=reg_R1002_USEN)

from cross referencing with this..


[http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07292&lc=en&dlc=en&cc=us&lang=en&product=62776](http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07292&lc=en&dlc=en&cc=us&lang=en&product=62776)


Although its for XP....

---

### Post by Dwiman89 on 2008-12-17
OKAY!!!!!!!!!! I got it booting right up ever time, although its VERY weird..... 


im using two hard drives to get it booting. the first master hard drive has nothing on it. its jut a blank 10gm unformated HDD....

The second slave HDD has Ubuntu on it.... it boots every time quickly...

so the questiion here is WHY does this stupid way work?????? I need to know so I can figure out where the REAL issue is...

---

### Post by philetus on 2008-12-17
I take it you upgraded your bios to the 3.17 bios?

I read somewhere that the HP xt993 is supposed to run XP.

Is your system setup set to boot from the slave HD?

It sounds like that or you have both set and when it doesn't find a OS on the master it boots from the slave.

---

### Post by Dwiman89 on 2008-12-17
No, I never upgraded the bios. It is still set to default. I couldn't find an upgrade... its working fine now with the dummy HDD. its like you have to give it someting to do before it gets the the HDD with the OS... Why does this work? the HDD with ubuntu is the slave drive.

---

### Post by philetus on 2008-12-17
Have you tried unplugging the slave and see if it will reboot?
If it won't, I bet your grub is on the slave.

---

### Post by philetus on 2008-12-17
Sorry, you said the master HDD is blank.Right?

---

### Post by Dwiman89 on 2008-12-17
yeah its got some files on it, but nothing relavent to an operating system. but oyther then that the master hard drives got nothing.

---

### Post by philetus on 2008-12-17
Here's a good thread on dual boot 2 HDD

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

and here's a bunch more.

[http://search.earthlink.net/search?q=dual+boot+2+HDD&area=earthlink-ws&FD=0&channel=narrowband&numadult=2&numroom=1&numchild=0&abtcgid=87&abtli=1](http://search.earthlink.net/search?q=dual+boot+2+HDD&area=earthlink-ws&FD=0&channel=narrowband&numadult=2&numroom=1&numchild=0&abtcgid=87&abtli=1)

I would completely reformat both drives before starting.
Let me know how it turns out.

---

### Post by robert shearer on 2008-12-17
> **Dwiman89 said:**
> yeah its got some files on it, but nothing relavent to an operating system. but oyther then that the master hard drives got nothing.
Well it can't be an "unformatted drive'" and have " some files on it"

That's like being 'a little bit pregnant"

Maybe you have found the problem?  What are the "some files"?

---

### Post by philetus on 2008-12-17
I think, possibly, his grub.

---

### Post by Dwiman89 on 2008-12-17
yeah, im starting to think that to. Im thinking somehow grub us getting put in the wrong place... Maybe its at the wrong mount point or partition... My theory is that by adding the dummy master HDD its buying enough time for grub to be loaded up while the dummy master HDD is being checked. of course I really don't know much about the inter workings of it all...

see when I would have a disk in the disk drive, I would have more sucessful boots...(usually subergrub, although I never tried using supergrub...)

I also tried manual partitioning;

    *  /boot - 300mb - ext3 - primary - beginning
    * / - 20gb - ext3 - primary - beginning
    * /home - 20gb - ext3 - primary - beginning
    * /swap - 5gb - swap - logical - beginning 

I put the boot loader(grub) on the /boot partition, but this also didnt work...

---

### Post by philetus on 2008-12-18
I would let install put boot on hd0
Put Windows on the Master HD
Wait until windows installs before partitioning the slave
Put root as first on the slave
Hit escape when the comp starts to boot up after the Ubuntu install

---

