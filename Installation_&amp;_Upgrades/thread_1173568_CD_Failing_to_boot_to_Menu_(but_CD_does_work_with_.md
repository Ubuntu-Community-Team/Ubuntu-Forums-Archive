---
title: "CD Failing to boot to Menu (but CD does work with other computers)"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by S7even0 on 2009-05-29
Greetings! Sorry for coming here with my problems.

Basically there is a long story which requires me to do a reformat due to broken OS, the OS is broken in that the language file broke and it had trouble rebuilding it as it just hangs. I was directed to Ubuntu by a friend as the solution of allowing me to access my harddrive through another OS without a reformat/clean install, so I plug in my external harddrive so I can back up important documents before planning to reformat it.

Anyway, what happens is this. When I put in the CD and the computer loads up the CD, then it goes to a black screen with a table in the corner full of numbers and letters which make no sense to me. If I press a key, the numbers/letters in the table change a bit the computer reboots (obviously, ends up running into same situation)

Thought it might have been the CD, so I tried it on my laptop, the CD worked brilliantly, using the try function, was able to use my external harddrive and tested backing up a file. So it seems this is the idea solution to the problem with this in theory.

As it worked, I thought there might be some dirt on the CD or something, so I made sure it was clean and put it in the computer I want to use it on. However, it is the same problem happening as earler. Black screen, half a table or something in the top left corner, some nonsensual numbers and letters in what is visible.

I cleared CMOS and I removed 4 gigs of my ram (was 8gig total) to see if it was any settings or having too much ram being a problem. However, exact same error is occuring.

For computer specification if that assists -
IP35 Pro Motherboard
Q6600 Quad-Core  2.4Ghz
4 gig DDR2 ram
Nvidia GTX8800 Graphics card
On-board Sound

---

### Post by merlinus on 2009-05-29
You might try the Knoppix live cd.  It generally is more forgiving of various video and other conflicts, and once running will give access to your drives and data.

---

### Post by S7even0 on 2009-05-29
I did a search and from a mirror from the Knoppix website, I choose to download the "KNOPPIX_V6.0.1CD-2009-02-08-EN.iso" presuming that is the latest .iso for the CD. (If not, could you please direct me to the right way?)

I will see how that works and hopefully fairs better.

---

### Post by S7even0 on 2009-05-29
Good news and bad news.

Good news, it loaded and even the external harddrive is working, that is great.

However...

I can't access my hard drive. When I click the volume it comes up with "Error org./freedesktop.Hal.Device.Volume.UnknownFailure"

(apologise if error in above text, the text is small and hard to disguish)

So I am unable to back-up my harddrive as I am not sure how to resolve this.

---

### Post by vpnm_87 on 2009-05-29
I think u too cud hav came to the following two conclusion..just thought of givin some suggestion..

1) try to use ur harddisk with some other Desktop PC as a slave drive..
(or)
2) go to ur HD manufacturer site or do some googling with the exact error u get when u try to access ur HD..

also provide some more details about ur HD partition,file system u used before..that might provide some clue for others..

---

### Post by S7even0 on 2009-05-29
> **vpnm_87 said:**
> 
1) try to use ur harddisk with some other Desktop PC as a slave drive..

Unfortunately, I don't have one and I don't forsee anyone allowing me to rip apart their computer any time soon either.

> 
also provide some more details about ur HD partition,file system u used before..that might provide some clue for others.

Since it is Windows, it uses NTFS. Most the results of google are either from 2005 period, though [http://www.knoppix.net/forum/viewtopic.php?t=2961](http://www.knoppix.net/forum/viewtopic.php?t=2961) seems to have a solution, however, it speaks about the hard drive having something like sda1, except, all it says in the GUI is "465.5 GB Volume" which isn't very clear at all.

---

### Post by vpnm_87 on 2009-05-29
I havent tried Knoppix before..i have used Puppy Linux from my USB Pen Drive to view my entire hard disk..

I dont know how u tried to access ur HD..
In puppy linux i access my HD just by clickin icons on desktop..

But i think u can use QTparted(partition editor) or some other partition editor in knoppix to view ur HD partitons..

---

### Post by S7even0 on 2009-05-29
I tried what a post in that link said which allowed me to mount the HDD, I will see if it all works with the copying. Thanks for all the replies though, I am very grateful.

---

