---
title: "TP 600E BIOS flash problem"
date: 2008-10-22
forum: Hardware
---

### Post by ed_209a on 2008-10-22
I have a hand-me-down Thinkpad 600E (2645-55U) that I want to run Xubuntu. 

It has 64MB RAM, a 3-400mhz CPU and enough HDD to do the little things I want it to, once I get it running on Xubuntu.

I bought 256mb of OEM RAM certified for that model, but it won't accept the RAM. POST counts to the right total, but go past that point.

I figure that since the BIOS had never been updated, 128mb RAM chips were just some engineer's dream when that BIOS was written. 

I get the most current BIOS flash disk from the OEM and make it into a boot CD (no FDD). I get into the BIOS flash app. It tells me that because I don't have a fully charged battery (I was on AC power at the time) it cannot continue. The battery will not charge, at all. 

Where can I go from here? I looked for an executable on the boot CD, but both Ubuntu and XP say there are no files on the CD. It is the kind where you stick it in the PC and reboot.

---

### Post by TubaTodd on 2008-10-23
I've managed to flash the BIOS of a 600E and bypass the battery error. I forgot how I did it. I may have it written down. Stay tuned...
:KS

---

### Post by TubaTodd on 2008-10-23
I believe I followed these instructions...

[http://www.wimsbios.com/phpBB2/topic7229.html](http://www.wimsbios.com/phpBB2/topic7229.html)

---

### Post by ed_209a on 2008-10-24
Thanks! 

I am making headway on those instructions, I'll let you know how it went.

---

### Post by ed_209a on 2008-11-10
Sorry about the delay, I was alternately busy or distracted.

Those tips worked great!

Once I flashed the BIOS, the TP600 took the 128mb chips without a hitch. I just booted into Win98 and verified that it reports 294MB, as intended.

Now I can welcome it to the 21st century with Xubuntu!

---

### Post by lswb on 2008-11-10
There's a great website with all kinds of info about running linux on older (and newer) thinkpads

[http://www.thinkwiki.org](http://www.thinkwiki.org)

type your model number in the search bar. I installed dapper on a 600E some time ago and IIRC had to tweak a few settings to get the sound and display working properly.



type

---

