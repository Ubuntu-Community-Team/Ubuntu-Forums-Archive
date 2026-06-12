---
title: "Screen Freezes Please Help!!"
date: 2005-04-05
forum: Hardware &amp; Laptops
---

### Post by i-tech on 2005-04-05
Hi all;
I updated system from Warty ot Hoary after my update system started to freeze. Keyboard and mouse freezes and left me no choise but reset  ](*,) 
Possible reasons for me can be;
1. 2.6.10 kernel? 
2. I tried to put 10 Gigs of mp3 to rhythmbox library and every time when I tried it died.
3.Gaim ??
 
I said these two because it did not gone bad for now thanks

---

### Post by vnbuddy2002 on 2005-04-05
I am experiencing the same thing and waiting for some solutions.

It seems to me that the causes might come from either  Xorg or the 2.6.10 kernel

---

### Post by sMell on 2005-04-06
If you're running on 440BX, you may benefit from disabling acpi
I was getting guaranteed crashes in X until I disabled it

---

### Post by wolovids on 2005-04-06
I've been getting screen freezes today also.  I never had X lock up on me like this before.  This happened twice tonight (April 6th) in an hour's time.  Both times I was in Gnome and using Firefox.  I'm in Xfce right now.  I'll report back if I find anything else out.

EDIT:  Okay, Hoary locked up once again very easily.  I was in Xfce and only running Firefox.  I downloaded an official build from mozilla.org to see if it is the latest Hoary Firefox package.

---

### Post by Whiffle on 2005-04-06
Been doing it to me too.  I reset my bios and cleaned the dust out of my computer and it seems to be better.  It still crashes if I use xcompmgr, I blame the newest nvidia drivers because xcompmgr used to work just fine.

---

### Post by kuleali on 2005-04-07
I have the same problem. I belive a update will come soon, because this is not exeptable in the stable release that will be released Apri 8.

---

### Post by wolovids on 2005-04-07
Well, it isn't the Hoary Firefox package.  I downloaded an official build and it also locked up.  It was a very recent change that is causing this.  It never happened to me before.  The only way to unlock Xorg is a reset.  I hope it is fixed soon or my wife will kill me for being on the bleeding edge!

---

### Post by vnbuddy2002 on 2005-04-08
I've connected my laptop to my Ubuntu Box. I've found that Xorg is taking up 99.9% of the CPU and caused the screen locked up. Many claim it is caused by the video driver from nvidia.

I've tried some of the solutions:

1. Change the AGP Speed setting ( 4x - > 2x )
- It helps but not a 100% solution. The percentage of getting locked up is lower.

2. Disable HDParm
3. Disable APCI (pci = noapci ) 
3. Manually compile nvidia driver with some changes in the source code ( seems like does the job )


There is two things you might want to try.

1. Use the Xorg default driver
or
2. Manually compile the video driver.

Good luck'

---

### Post by hamster2k3 on 2005-04-08
Hey Guys!

I was a Gentoo user on my Desktop PC, and I was getting these same damn freeze. I thought at first it was only with Gentoo because of all the customized CFLAGS...  But no... doesn't seems to be.

There was and there's still a long long 17 pages thread of posts in the Gentoo forum about this mysterious freezes.

A lot of stuff was tried and some worked for some people, and other stuff worked for other ppl. Really weird! And it also happens to Nvidia users, and ATI users.

Sometimes disabling ACPI works, and APM.
Sometimes lowering AGP in bios to 2x works... etc etc...
Sometimes using external AGPGART works... 

Also, when the computer is frozen(basically its only X) you can still access it via ssh, and see that X is using all the CPU!

Also, another note, some ppl might blame Firefox, but its not its fault!
The problem is that Firefox, asks a lot of stuff to be done by X, because of rendering and such... so that's why eventually X will freeze.

And the problem happens even more with 3D stuff, because well, there's more work to be done... duh! So well... guess the rest! heh

Also I remember seeing some posts from the Xorg folks, saying that basically the problem is not in Xorg, because the problem won`t happen if you use the plain standard vga driver....

But we want to use the 3D drivers...

Anyway I thought that Ubuntu could probably ease my life, well more than with Gentoo, actually I get less crash than with Gentoo. Which is good, but still cannot run 3D stuff like screensavers and cedega... 

I could disable the screensavers, but it won't fix my prob...

Anyway, I've tried almost all solutions that was posted by other users, but they all failed for me. So if anyone has an idea! ;)

---

### Post by André on 2005-04-17
Hi guys,

it been some time since you posted but did you find a solution?

My system is getting unstable too. Right now i think it only happens when my power calbe is not plugged in and my notebook runs with battery.

Any help is appreciated to solve this annoying problem.

Greetings
André

---

### Post by André on 2005-04-18
Hi,

i am still getting these problems. Could someone guide me on finding the error?

How can i find out what went wrong after a total freeze? Are there some logfiles where i can take a closer look??

I am not having the nicest time workng with a hard locking notebook but maybe i can learn some new stuff. So could please give me an advice about error finding?

Greetings
André

---

### Post by NaplesBill on 2005-04-18
I was having the same problem until I changed my driver from "nv" to "vesa."  The nvidia driver wouldn't work at all.  I have since upgraded my motherboard and processor and no longer have the problem.  The new motherboard has an S3 video chipset and is using the "via" driver.

---

### Post by André on 2005-04-18
Mmmmhhhh... a friend of mine is also having these problems.

I have a Radeon 9600 mobility with fglrx driver right now. I will try the "ati" one.

My friend has a Radeon 9000 and is using the ati drivers.

I think i have to search a bit more. Any other ideas????

Please help.

---

### Post by lee_connell on 2005-05-23
I have the mobility 9200 fglrx driver and i had just locked up i also tried the normal ati driver and it also locked up, i'm lost?????   anyone?

---

### Post by bhanja_Trinanjan on 2005-05-24
@Tux fans: Never dare to say again that Linux is more stable than Windows XP Pro! [-X   :)

---

