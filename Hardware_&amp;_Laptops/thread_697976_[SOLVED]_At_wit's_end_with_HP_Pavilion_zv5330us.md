---
title: "[SOLVED] At wit's end with HP Pavilion zv5330us"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by Brian4 on 2008-02-15
Let me first start by saying that this is a P4 with hyperthreading and an ATI Mobility Radeon 9000 IGP graphics card.

First in my journey, I had much fun with trying to resize the original Windows XP that was on it due to Gparted saying there were bad sectors.  After a is said and done, I used 'ntfsresize --bad-sectors' and used Window's checkdisk to adjust the partion itself.

I then installed Gutsy on the second partition.  Everything - and I mean EVERYTHING worked just fine after installing the restriced drivers.  I then got some more memory - a 1-gig module.  I had problems with the 1st brand, so I had to get another brand, Kingston.  After this things were fine.  I installed ALL updates without any problems whatsoever.
  I then tried getting the laptop to do a suspend and hibernate without much success.  Mind you, there are still no problems yet.  In my quest to work out hibernation and suspend, I figured that maybe I should try to re-install Ubuntu in an effort to change the swap partition size.  (At the time, I didn't know how to do that without re-installing.)  HERE is where my quest to try out Linux goes South!

I cleared the Linux partitions using Parted Magic and was able to reinstall Ubuntu.  However, while doing updates, it would keep on 'disappearing'...  As if I somehow quit the program.  I would start it up again and it would continue downloading where it left off until it happened again (and again and again).  This has turned out to be a theme throughout this WHOLE ordeal.

This 'disappearing' program effect happens with everything Linux now...  A terminal, Thunderbird, Mozilla, name-your-program.  I was able to start and run XP and not have ANY problems.

I tried another Ubuntu-based distro - Linux Mint.  I've tried both older AND newer versions of each of these.  I've also tried OpenSUSE 10.3 with exactly the same symptoms, and am currently downloading Fedora to see what happens with that.  I was still able to run XP just fine, though.

I have also just tried to install Linux Mint on the entire Hard drive - wiping out XP, to no avail.  (I was hoping it might have wiped anything wrong with, for instance, a bad MBR or something.)

Does anybody know what in THE hell is going on??  Could it be that a hard drive with bad sectors causes such strange symptoms?


Help disparately needed.  I bought an Ubuntu book and everything for my adventure into Linux. :-/

---

### Post by Brian4 on 2008-02-27
Trying to make this show as "solved" like many threads show...  In case others have had these problems with zv5330.

It turned out to be bad memory.  I let memtest86 run for a half-hour which showed nothing..

However, after letting it run for about 38 minutes - at test #5, it showed numerous errors.
I returned the ($64 - 1GB module Kingston 'value ram') to best buy, but was unable to find any more 1GB modules for ~$64.  I ended up having to buy a "K-Byte" module for $149.  The had others, but I was afraid to buy Kingston again..

Anyhoo, I made SURE to let it go through the whole memtest - with positive results this time.

The funny thing was that I had the strange 'quitting' phenomenon even when I put back the original module.  The only thing I can believe that would account for that was that I installed all the various Linux flavors while using that bad module.  So, I guess while copying files to the hard drive, bits were not reproduced precisely and therefore didn't work when I had the good memory in..  At least, that's the best I can figure. ;)

So after this, I installed Linux Mint only to find that I couldn't get my Wireless to work at all, even after installing the restricted drivers.  I reinstalled Ubuntu 7.10 and everything then worked flawlessly.  I can remove the ethernet cable and it'll automatically switch to wireless!! =)

This experience does lead me to one question though..  Why does windows seem to tolerate bad ram better than Linux??  Does the kernel automatically map out bad sections, or what?

---

### Post by Yellow Pasque on 2008-02-27
> Trying to make this show as "solved" like many threads show... In case others have had these problems with zv5330.

At the top-right of the page is a menu called "Thread Tools". It's an option under there.

> This experience does lead me to one question though.. Why does windows seem to tolerate bad ram better than Linux?? Does the kernel automatically map out bad sections, or what?
If I had to guess, I would say it's because Windows is allergic to RAM and likes to use the hard disk for virtual memory regardless of how much RAM ones has. That's just one of the multitude of reasons I don't use Windows anymore :)

---

### Post by Brian4 on 2008-03-01
I think the virtual memory thing is one of the reasons..  With my 'main' machine, I used turn off all virtual memory to get it to use the real memory - until I started to play around with VirtualPC, then VirtualBox to experiment with Linux and FreeBSD.

Vista, IMO,is going the opposite direction in what I want an OS to do by requiring so much processing power and memory just to run the kernel.  Although, OTOH, it's requirements will boost low-end system specs and make highly powerful Unix systems VERY cheap.

I have to say I already love Linux for the speed it gives.  And free software to boot!  What's not to like?? ;)  Just takes a bit to find alternate ways of doing things, but I'm steadfast determined to use Linux - despite my recent laptop woes.

I have to admit that I'm surprised it works flawlessly, given the many troubles I see people having with graphics cards and the exact same wireless card I'm using (Broadcom 43xx)..  But I shouldn't look a gift horse in the mouth! =)

---

