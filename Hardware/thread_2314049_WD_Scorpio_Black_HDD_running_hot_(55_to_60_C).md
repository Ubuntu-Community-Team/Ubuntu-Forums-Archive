---
title: "WD Scorpio Black HDD running hot (55 to 60 C)"
date: 2016-02-18
forum: Hardware
---

### Post by tadd2 on 2016-02-18
Hello.  I recently revived an old Dell Inspiron 6400.  I had Ubuntu 12.04 LTS on it a couple years ago with an old 320 Gb WD Scorpio Black.  When the HDD failed, I shelved the laptop.  To get it going again, I ordered a new WD Scorpio Black, 500 Gb, 7200 rpm, and installed Ubuntu 14.04 LTS.  While I have no use for a performance drive, I am rough on computers and I like the 5 year warranty.  When on AC power, the HDD will run at about 52 to 55 C.  It doesnt seem to matter whether I am just browsing the internet or watching a video, etc...  It has reached 61 C (max operating temp) while on my bed or lap.  I know WD black HDDs run hot but this is ridiculous.  I use a 90 Watt Dell AC adapter and a new battery.  Here is the interesting part: when I run the laptop on just battery, the HDD runs in the mid to upper 30's C.  I assume that the drive must be in a lower performance mode while on battery.  Is there a way I can force Ubuntu to run in this mode all of the time?  Like I said, I don't need the performance, just the warranty and not to burn my lap.   Note:  The old 320 Gb drive was running this hot before it failed, I assumed it was just a sign of a failing drive.

---

### Post by Bucky Ball on 2016-02-18
Welcome. Beds and laps are not good places for laptops. Tends to block airflow (never leave a laptop on a bed).

Have you put it on a solid desk top or flat surface, let it run for an hour then checked?

Your explanation re. battery power seems logical. Why not check the power manager and confirm your suspicions then tweak your power settings where necessary?

If the other drive was also running this hot, then something is going on with your power manager settings I'd say.

(Please use paragraphs. Black walls of text with no paragraphs may deter potential helpers.  :))

---

### Post by weatherman2 on 2016-02-18
I've had a couple of Inspiron 6400s, and all the hard drives I've had in them run hot in Linux.   One was in use for years by a distant relative - a 160GB WD Blue drive.  It would gradually heat up to 50C after about a half hour of use and I was worried about the heat.  But it was fine for years.  I just replaced the HDD with an SSD but the HDD never failed.

I think it was related to the idle3 timer - this:

[https://apps.ubuntu.com/cat/applications/quantal/idle3-tools/](https://apps.ubuntu.com/cat/applications/quantal/idle3-tools/)
[http://idle3-tools.sourceforge.net/](http://idle3-tools.sourceforge.net/)

I was worried about the high Load Cycle count that was developing on my drives; the heads were parking too often at ldle which could put undue wear on the drive heads.  The parking saves power.  I used this idle3ctl to disable the parking but that also caused the drive to heat up.  If you aren't worried about the head parking and would prefer cooler operation instead, you could use this to set the timer value to a low number.  Some studies (e.g. Google) have shown that the high heat might not really be that bad for modern hard drives.

Or, do what I wound up doing and replace the HDD with an SSD.

---

### Post by tadd2 on 2016-02-19
Thanks for the formatting tip.  Most of the time it is on a solid desk, that it when it reaches the low to mid 50s C temp.  Thanks again for the reply!

---

### Post by gordintoronto on 2016-02-19
Are you sure there's no dust buildup in the vents and fans?

My desktop has a 7-year-old WD Black drive that consistently runs at 38 C. Mind you, there's a fan blowing fresh air right across it!

---

### Post by weatherman2 on 2016-02-19
This is a laptop, not a desktop, and the slot for the 2.5" hard drive isn't particularly well ventilated by design, unfortunately.  There isn't really anywhere for dust to build in near the hard drive on the E1505/6400.

---

