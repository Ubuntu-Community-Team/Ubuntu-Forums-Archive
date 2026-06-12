---
title: "What I do? (it wouldn't boot)"
date: 2010-03-18
forum: Hardware
---

### Post by gillbates10 on 2010-03-18
I decided to put a hd4850 video card in my system.  It was so long I had to move my three HDDs.  Once in I just randomly plugged them back in and then cycled the cables until I got the system HDD in the right place and it booted.

I removed my old nvidia drivers, loaded my ATI drivers and everything worked great.  Then I even loaded all of the updates for the system (I'm running Jaunty).  It wanted to reboot so I let it.  While it was rebooting I jumped into the bios and tried to up the host frequency (ie overclock it).  That's when the fun began.

As it came up it could see my memory, hard drives, and DVD.  Then it asked me if I wanted to start from the CD.  That was as far as it would go.  After a few cycles it stopped asking if I wanted to boot from the CD.  I zero'd the CMOS.  Removed an old ATI TV card.  Installed my old video card.  Flashed the BIOS.  Ran the memory 1 stick at a time.  Started looking for a new MB/CPU at Newegg.  Finally I unplugged the two non-system HDDs and up it came.

I noticed that the system HDD was in a slave position so I moved it to the open master slot (DVD has the other one).  Eventually I put both memory sticks, the new video card, and the other two HDDs back in and everything seems to work fine.  

I still would like to OC this box but I'm a little gun shy now.  Can anyone see where I went wrong in this writeup?

It's a gigabyte 945gzm-s2 MB with a D 805 processor.

---

### Post by Flareside on 2010-03-18
When you have a hard drive and DVD/CD drive on the same IDE cable, the hard drive should always be the master. Thats the only thing wrong I can notice

---

### Post by gillbates10 on 2010-03-18
I was basing the master/slave relations by what the BIOS was telling me as it loaded.  All of the drives are SATA so I'm not sure how that actually works.

---

### Post by Flareside on 2010-03-18
The hard drive should still be the master because the sata is pretending to be IDE in that case and the same rules apply.

---

### Post by gillbates10 on 2010-03-19
Here's where I suspected the problem was.

At first I thought that changing the host frequency had fried something.  Once I got it working by unplugging the non-system HDDs I figured that the order of the HDDs had caused the problem.

What I couldn't figure out is why it booted in the first place.  Perhaps one of the Jaunty updates changed something.  

Any hardware/linux guys out there have an opinion?

---

### Post by cascade9 on 2010-03-20
I'm guessing that you've overclcocked, and while you had it right enough to boot, the overclcock was too high, or the voltage to low for it to work under any load at all. (its not uncommon for overclcocked settings to boot fine, but then refuse to load an OS). 

As for what you did 'wrong'- always play with one thing at a time. Trying to overclcock + installing a new card at the same time as asking for trouble.....and makes it a lot harder to troubleshoot if things go wrong. 

I would have done the updates, then restarted. shut it back down, then installed the new card, which probably would have sodded things up anyway witht he drive order, but thats not such a hard thing to diagnose. Then after you had sorted that lot out, then tried to overclock. 

BTW, the 805D is pretty good at overclocking.  They have been know to go over 4Ghz (not a good idea though IMO, and they will suck power like you wouldnt believe at those levels). Stock they are 133x20, 2.66Ghz. At 4Ghz thats 200x20...166x20 for 3.32Ghz shouldnt be that hard to do. For the chip....the motheboard is a pretty poor overclocker from the quick look I had.  

> **Flareside said:**
> When you have a hard drive and DVD/CD drive on the same IDE cable, the hard drive should always be the master. Thats the only thing wrong I can notice

That wont matter much with anything newer than, ohh, 1998-99 or so. The worst that will happen is slower reads/writes.

---

### Post by gillbates10 on 2010-03-20
Thanks Cascade,

Ironically I purchased that MB/CPU combo so I could OC.  It comes with software to OC, but the software only runs under winders so it doesn't help me.  Since I'm not a gamer I never really needed to OC until I downloaded this train ride from Norway.

[http://multemusic.com/2009/12/21/7-hour-video-that-most-of-norway-viewed/](http://multemusic.com/2009/12/21/7-hour-video-that-most-of-norway-viewed/)

It's a 21 gigabyte file in 720p HD and it maxes out one of my cores and then gets jerky.  I was hoping the hd4850 would help but it didn't.  The BIOS on the 945gzm-s2 MB has very few OC options and when I tried to play with them it didn't work out to well for me as you noted.  So now I'm considering getting a e5300 to upgrade the CPU but I haven't been able to figure out if it would improve my performance any.

Do you have any suggestions for a 775 MB upgrade or CPU upgrade to boost this machine.  I can get the e5300 in a retail box from microcenter for $60.  I hate to upgrade the whole thing to another 775 while the 1366/1156 MB/CPUs are still more expensive than my level of parsimony will allow.

Oh and I agree totally with your one thing at a time upgrade theory.  But my hands just don't care what i think. :)

---

### Post by cascade9 on 2010-03-21
A e5300 should have more performance than a 805D. Its not 100% sure it will run in that board though. I think it should, but 'think' doesnt help if if it doesnt. 

I tried going to microcenters website, but for some reason I can never view the processor list, I just get 'product not avaible' :| 

I'd try XvBA (ATI hardware video acceleration) before going and buying new parts. It might (should, really) just help your HD playing enough to avoid spending any money at all. ;) 

This thread should help with doing that-

[http://ubuntuforums.org/showthread.php?t=1385896](http://ubuntuforums.org/showthread.php?t=1385896)

---

### Post by gillbates10 on 2010-03-21
Yeah, microcenter kind of sucks when it comes to browsing their web page from ubuntu.  You would think a geek store would figure it out but if you don't run winders, stuff like that happens.  But they do happen to have a store about 10 miles from my house so they get my drive in/ hard drive business (did you know UPS will routinely drop your boxes 6 feet) and newegg gets the rest.

The Gigabyte doc says that the e5300 will run on my board.

For some reason, I didn't figure out that you had updated this until just now.  So I went out a few hours ago and picked up a e5300.  I'll give the XvBA thing a shot before putting it in.

---

