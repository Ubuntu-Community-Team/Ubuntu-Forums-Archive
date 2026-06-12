---
title: "frequent hard disk access"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by rit on 2007-08-13
Hello all-

I'll try to keep it short and to the point.

A while ago I added a second drive to my ubuntu box, and I noticed a slow rythmic clicky sound (but not an actual, you know, death-type clicky, this is more like hard disk access chirpy-clicky-something-something...).  It was annoying but it was very soft and sort of fell off the radar.

Fast forward to yesterday, I had the box open for cleaning and decided to connect the LED headers for hard disk access (which were not connected and I had been previously too lazy to open the box up just for that).  Connected, they work, yay... wait...  flash...  flash...   flash...

Yeah every second or so I get a nice flicker of hard disk activity, consistent with the sound.

It's significantly annoying and at this point I'm worried about what all these extra accesses/whatever-they-are are doing to my drive's longevity.  Other than this rhythmic weirdness the drive behaves fine, works like champ.

I'm not an expert but I'm not a computing newbie either, and I've never seen this behavior on any of my linux boxen or any other OS box I've built or worked with in the past.

Nothing crazy is/should be running, this happens on a fresh boot.

Anyone run into anything like this before?

Thanks for reading!

---

### Post by c-shadow on 2007-08-13
Wild guess: Could be thermal recalibration of the disk. Happens when disk temp gets a bit higher...check with hddtemp util. Does it happen imediately after booting a cold disk, or after a while when it warms up?
Also it wouldn't hurt to check SMART status of the disk. Install smartmontools and try something like smartctl -a /dev/hda
Replace hda with your disk. Post both results (hddtemp and smartctl) here.

---

### Post by rit on 2007-08-14
This is a "no matter what" thing, cold, hot, you name it, as soon as ubuntu is up, it starts.  I've read a lot of different posts about old versions of ubuntu and similar problems that seem like they've been cleaned up in later versions such as Feisty but you never know.

here's hddtemp:

/dev/sdb: ST3320620AS: 32°C


here's smartctl:

Device: ATA      ST3320620AS      Version: 3.AA
Serial number:             5QF3YS83
Device type: disk
Local Time is: Tue Aug 14 00:29:09 2007 EDT
Device does not support SMART

Error Counter logging not supported

[GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on']
Device does not support Self Test logging


This honestly "feels" like a polling thing, I mean, it's just too perfectly regular, you know?

Let me know what you think, and thanks for helping!

---

### Post by rit on 2007-08-14
p.s. just for fun based on some stuff I read I killed hald and it definitely had a huge impact on what I see/hear for disk access.  Now instead of a flicker of life every second or half a second I see what looks like normal periods of nothingness with little random accesses here and there, which is what I expect considering how I use this machine.

Not an expert and still trying to muddle through all of this, any help is good stuff!

---

### Post by kozy6871 on 2007-08-14
Both of my IDE drives do that same thing when I have SMART turned on.  They don't do it when it is off.  I have no idea whether they really make noise or not (too much background noise), and I seldom open the case with the power on.

---

### Post by c-shadow on 2007-08-14
> **rit said:**
> This is a "no matter what" thing, cold, hot, you name it, as soon as ubuntu is up, it starts.  I've read a lot of different posts about old versions of ubuntu and similar problems that seem like they've been cleaned up in later versions such as Feisty but you never know.

here's hddtemp:

/dev/sdb: ST3320620AS: 32°C


here's smartctl:

Device: ATA      ST3320620AS      Version: 3.AA
Serial number:             5QF3YS83
Device type: disk
Local Time is: Tue Aug 14 00:29:09 2007 EDT
Device does not support SMART

Error Counter logging not supported

[GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on']
Device does not support Self Test logging


This honestly "feels" like a polling thing, I mean, it's just too perfectly regular, you know?

Let me know what you think, and thanks for helping!

That should be Seagate 320 SATA?
It coud be some "polling thing", temperature is fine, as for the SMART, you'll probably have to fiddle with -T or -d options to get some output out of smartctl. I had the same problem with my Hitachi  320 GB SATA and one of these switches did the trick. But it is a relatively new disk and should be healthy. As for the polling...i didn't experience anything similar on my feisty instalation with 2 SATA and one IDE drive. But it shouldn't affect your drive in terms of longevity. If you are running some older version od ubuntu, why not upgrade? Or at least try to boot live CD and see if it happens there also? Try feisty and then whatever you are using now...

---

### Post by rit on 2007-08-14
Oh I'm sorry if my language was confusing before, I am running Feisty, I was just referencing how I was reading old posts about the same exact symptoms but under much older versions of Ubuntu, and I'd have hoped that they'd be noticed/fixed by now.  I am having a great time with Gutsy on a laptop so I think I'm just going to grab my stuff off the desktop and do a nice clean install of tribe 4 and see what mileage I get.  I'll probably tinker with hald some more before I do that because I am curious as to what is causing this.

And yes to answer your question it is a pretty new seagate 320 GB drive, and this doesn't happen under any circumstances so far other than my installed Feisty...  so so weird.

I might not be able to resist the geekery and just continue screwing with this setup but eventually it will get old to me and I'll try a new install with Gutsy.

Thanks for the help!  If anyone has any further ideas I'm still down to discuss but it might become academic if I blow the install away!

---

