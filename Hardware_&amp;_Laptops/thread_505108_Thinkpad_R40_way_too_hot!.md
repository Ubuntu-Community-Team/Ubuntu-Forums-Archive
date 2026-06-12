---
title: "Thinkpad R40 way too hot!"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by DrMilo on 2007-07-19
Hello all: I can't seem to find anything that addresses my specific problem. After installing a Gig of RAM on my Thinkpad R40 I have gotten a lot of overheating problems. The heat seems to be worse over the access panel for the RAM chips which is why I'm mentioning the upgrade. I think this problem can be solved by having the fan on all the time, it certainly isn't now and when it comes on the air being discharged is nearly hair dryer heat so I don't think it's coping.  

Yes I've had a look at the wiki's and all that but there is nothing that addresses this specific problem. So I'm hoping someone can tell me how to have the fan on all the time. Yes I know my power consumption will go up a lot but that's not a problem as I'm nearly always around AC outlets. The random lock ups I get now are far worse than running low on battery power. 

If this doesn't work I'll have to down grade my RAM which I'll live with if I must but might not work anyway. So I'd rather give software a good try before I do hardware. 

Thanks in advance.

---

### Post by kngunn on 2007-07-20
Upgrading your RAM should NOT be causing your R40 to act this way.

First try removing that RAM and see if the problem goes away.  Also, see if you have any BIOS updates available from Lenovo.  You should make sure you are completely up-to-date.

After that, I would run top to see if I could determine what process is running so hard.  You might also try running from a LiveCD to see if it runs cooler -- if it does, something in your software is confusing things and you may need to reinstall (if you don't want to go digging for the solution in the current installation).

Good luck!

---

### Post by louieb on 2007-07-20
Try asking here These guys seem to know there Thinkpads. I have an old T30 and this is where I go for Thinkpad stuff.   [ThinkPad Forum ]("http://forum.thinkpads.com/") Some are even Linux savvy too.

---

### Post by Sunflower1970 on 2007-07-20
If you're using Feisty, I've found the same thing with my R40. I also have 1 gig of RAM in it. Edgy worked beautifully with it...Since I don't have anything too important on it, I'm going to be testing Gutsy to see if this problem goes away (along with whether or not suspend/hibernate works with Gutsy), and if not, I'm downgrading (again!) to Edgy. :(

I do have a cooling pad for it, which helps out tremendously, but it would be nice if it still wouldn't get so hot...

---

### Post by DrMilo on 2007-07-21
Thanks all. The irony is that this laptop was a gift! It's the gift that keeps on taking! I can't believe there's nothing in the BIOS or direct hardware to fix this! I'll be fighting with it tomorrow again...

---

### Post by DrMilo on 2007-07-21
> **Sunflower1970 said:**
> If you're using Feisty, I've found the same thing with my R40. I also have 1 gig of RAM in it. Edgy worked beautifully with it...Since I don't have anything too important on it, I'm going to be testing Gutsy to see if this problem goes away (along with whether or not suspend/hibernate works with Gutsy), and if not, I'm downgrading (again!) to Edgy. :(

I do have a cooling pad for it, which helps out tremendously, but it would be nice if it still wouldn't get so hot...

Dapper Drake for me, if things improve with another distro let me know, thanks!

---

### Post by jboeke on 2008-01-16
Same problem with mine.  VERY hot in the location of the memory access panel.  I'm running Gutsy (7.10).  

I originally configured my system to match the testing team recommendations ([https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadR40-2681]("https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadR40-2681")) including the minimum CPU speed hack:

```
cpufreq-set -d 600MHz -g ondemand
```

I'm going to try and undo this change tonight.  

I'm also going to make sure I'm running the latest BIOS:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-50321]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-50321")
or
[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-46061]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-46061")

Finally, there is a hard drive firmware update as well.
  [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-62282]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-62282")


I'll report back here with my results.

---

### Post by jboeke on 2008-01-16
> **jboeke said:**
> 
I'll report back here with my results.

Baseline
--------
Uptime:  32 min
CPU:  59 C
HDD:  45 C

Post HDD firmware upgrade
-------------------------
Uptime:  22 min
CPU:  59 C
HDD:  46 C

cpufreq-set changes
-------------------
Uptime:  21 min
CPU:  59 C
HDD:  46 C


I was unable to update the BIOS.  This required a Floppy Drive.  Not available on my system.  I'm still running an old BIOS version.  Should be 1.27 but I'm running ~1.15?

---

### Post by TeoK on 2008-03-08
same here. R40. Running Gutsy and upgraded to 1 GB. the ram panel and WiFi panel get Very hot at times..and worse, I think my fan is dying - i can hear the bearing making noises at times.
I may need to go eventually to some external cooloing solution.

---

### Post by mperry on 2008-03-08
As far as the bios upgrades go, I don't have floppy drives for any of my thinkpad T43s and I use the bios upgrade path that is suggested on thinkwiki.org.  Works pretty well for me.  I can burn the power management and bios update to CD, reboot and select the boot option to boot the CD drive and the bios update goes on.  Only poblem I have had is that my second T43 requires a different bios/power management revision so I have to find two completely different releases on lenovo's website.

Otherwise, building small iso images from the non-diskette installers (I think) and booting them have worked for me on everything from T23s forward.  You may want to read on thinkwiki's website for success stories for the various ways to upgrade a bios on thinkpads running Linux.

---

