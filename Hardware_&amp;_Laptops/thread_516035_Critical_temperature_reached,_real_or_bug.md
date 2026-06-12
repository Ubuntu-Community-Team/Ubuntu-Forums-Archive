---
title: "Critical temperature reached, real or bug?"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by alzaf on 2007-08-02
I have been converting a number of flac files to MP3 using a python transcode script but when it has been running for a while, my laptop shuts-down. 

I checked out the kern.log and noticed the following message about the time my laptop shuts down.

> 
[ 1081.088000] Critical temperature reached (105 C), shutting down.


I have read a few threads in this forum and it was mentioned that this is a bug. Is this true?

---

### Post by afaflix on 2007-08-02
> **alzaf said:**
> 

I have read a few threads in this forum and it was mentioned that this is a bug. Is this true?

I had my laptop heat up my room whenever I 
- tried to import anything into KMail
- tried to watch videos, DVD, youtube ... (I get about 7 minutes on a cold start computer)
- had amarok scan my drives for mp3's

really anything that involved cpu work

a week ago I installed **xubuntu gutsy tribe 3** and none of the heat related problems have reared their ugly head yet.
While I can't tell you what's wrong, I can tell you that it got adressed.

---

### Post by alzaf on 2007-08-04
Thanks.

From the other comments it does sound like a bug but it does concern me that the processor temperature can be misjudged as they could potentially reduce the life of my laptop.

---

### Post by walkerk on 2007-08-04
> **alzaf said:**
> Thanks.

From the other comments it does sound like a bug but it does concern me that the processor temperature can be misjudged as they could potentially reduce the life of my laptop.

Are you using Feisty Fawn? You could always give upgrading you kernel a try.. It's solved quite a few laptop issues with other Ubuntu users.. See my signature for the link..

---

### Post by alzaf on 2007-08-09
sorry for the delay in replying to this, I've been busy with things and will attempt to update kernel to see if it fixes problem.

---

### Post by alzaf on 2007-08-09
I've updated to Gusty Kernel and same thing is happening.

---

### Post by bapoumba on 2007-08-09
You say this is a laptop. Mine failed on me some time ago, due to over heating. It had to go back for repairs, and a good cleanup (I did not clean it myself, because of the warranty, I cannot open it yet).
So I bought one of these usb fan things you put the laptop on (giving you an additional 4 usb spots in the process). All good now.

---

### Post by alzaf on 2007-08-12
I've got a feeling that laptops aren't designed to do heavy 'number crunching' that entails with the likes of what I'm doing.  I had amended the transcoding script where it paused for a minute after each album was transcoded.I was able to get more albums processed but it still shutdown with overheating.

Thanks for the tip. I've seen a few of the laptop coolers on amazon. I'll be buying one when payday comes.

---

### Post by bapoumba on 2007-08-12
Laptop cooler, yes that's it (sorry, I did not remember the proper term for it and did not look).
Mine failed in the middle of feisty install (I'm now running gusty on this one). After it cooled down, I managed to run a minimal text install for it to boot up before it goes on repairs.
Anyting that was taking up resources was making it overheat. There was a problem with the CPU (warranty applied, ouf!).

Now, with the cooler, temp is around 40-50°C, never more, even if I use lots of CPU. I think a good cleaning from time to time helps too.
Good luck, have a live CD handy and up-to-date backups, just in case ;)

---

### Post by alzaf on 2007-08-12
Thanks for the tips bapoumba, much appreciated :-)

---

### Post by alzaf on 2007-10-20
I was put off by the laptop coolers as I read they push the expelled hot air back up into the laptop.

I found a novel way of getting round the critical temperature issue with laptops. Since the fan is located on the bottom of the laptop and that bottom is lying flat on a surface. it makes sense to elevate the laptop above the surface so that the fan can circulate air around the area of the cooler. 

I did this by putting cassette tapes cases under my laptop so that there was enough space betwen the it and the table surface I have it placed on. I've ran my transcoding script about 3 or 4 times, each with an interval of about an hour with no problems.

Sounds wacky but recommended if you are going to do anything that is CPU intensive.

---

### Post by Felipe_U on 2007-10-21
I installed Gusty on my mother desktop and I'm having the same issue, it says the processor reaches 98 degrees and it shutsdown. I think this is a misreading sin in XP she never has this problem. Any way to ignore the temp readings in Gusty???
I've tried to boot with noapic and nolapic but I still have the same problem
Regards,
Felipe

---

### Post by alzaf on 2007-10-22
I'm not an expert on this but AFAIK, this is built in the kernel but I could be wrong.

Gnome and KDE are resource hoggers even for high spec machines which is the reason why I use Xubuntu. It might not be so pretty but It does the business and is light on resources.

---

### Post by c!co on 2007-12-05
Hello!
I believe I have found a cause for this annoying problem. I used google for search and this came out as a solution:

[http://www.lm-sensors.org/ticket/2072]("http://www.lm-sensors.org/ticket/2072")

As it is mentioned above, it seems that lm-sensors and acpi are in some sort of conflict when they are reading temperature value. I removed lm-sensors completely and now it seems that problem is gone.

---

### Post by CarstenA on 2007-12-09
Hi 

I got kind of same problem, can you explain how you removed "lm-sensors" ? ( I am rather new to ubuntu and I _think_ that would solve my problem aswell... :)

---

### Post by PokerFacePenguin on 2007-12-09
My laptop is an Dell Inspiron 5100 series.  I have taken it apart on 2 occasions for cleaning.  The placement of the fans and the use of the regular ole P4 processor in that thing is notorious for heat.  It's an easy thing to take apart and put back together.  The first time I took it apart I cleaned and reapplied the thermal grease (Arctic Silver 5) and blew the dust out of everything.  Worked wonders for me.  Not sure what brand you have, etc, but chances are it is dirty.  The old thermal pad/grease whatever it was looked terrible (cooked on).  Try it.

---

### Post by CarstenA on 2007-12-11
Sorry I should have defined my question more :) I got a acer aspire AMD 3000 64bit

I allready did take it apart and really cleaned the fans, it is not getting as hot as before but now ubuntu is still closing down when it hit 53 degrees sometimes... as oposed to 70-80 before...

I upgradeded the kernel (guide from this thread) [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)
and gave more uptime, but it is still doing it...

I did poke more around though, and it dosent look like I got IM-sensors installed, I am thinking about installing it and then just modify settings that it shouldnt do anything until it hit those 70-80 degrees again but has anyone tried that ?

---

### Post by CareyB on 2007-12-11
This problem has to do with the acpi setup.  Search the forums for "acpi temperature" and you'll find the issue.  It's not simple, and so far there seems to be no fix.

---

