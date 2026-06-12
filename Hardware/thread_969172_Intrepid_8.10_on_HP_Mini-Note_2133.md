---
title: "Intrepid 8.10 on HP Mini-Note 2133"
date: 2008-11-03
forum: Hardware
---

### Post by xjgnsdof on 2008-11-03
I set up my Mini-Note (the specifications of which are in my sig) using the wiki: [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

I upgraded to Intrepid yesterday because the wiki said that it would work. However, when I try to boot into Intrepid and the new kernel (2.6.27-7), I get no splash screen and only a blinking cursor. I tried booting with "xforcevesa" and "acpi_osi=!"Windows 2006" to no avail.

Has anybody gotten 8.10 to work on the Mini-Note? I have an external optical drive, so solutions involving LiveCDs are available to me.

---

### Post by woodp on 2008-11-03
At least two of us have been successful.

[http://ubuntuforums.org/showthread.php?t=965542](http://ubuntuforums.org/showthread.php?t=965542)

The only special aspect of my installation was the "xforcevesa" switch which you also set. I don't know why your installation didn't work, but it's running fine over here.

---

### Post by xjgnsdof on 2008-11-03
I have the higher-end Mini-Note that came with Vista Business. See my sig for the specs. The hardware is slightly different among the Mini-Notes.

---

### Post by brwatters on 2008-11-04
I was able to install v8.10 onto my 2133 KR922UT without issue, Heck it went to darn easy I was suprised .. Way better than the base SuSE v10 that came on the unit, I even have more SDD space now .. Thanks to the Ubuntu folks to making that install painless .. Now to find out how to make te onboard camera to work.

BRW

---

### Post by xjgnsdof on 2008-11-04
> **brwatters said:**
> I was able to install v8.10 onto my 2133 KR922UT without issue, Heck it went to darn easy I was suprised .. Way better than the base SuSE v10 that came on the unit, I even have more SDD space now .. Thanks to the Ubuntu folks to making that install painless .. Now to find out how to make te onboard camera to work.

BRW

Your system came pre-installed with Linux; mine did not. The testbed Mini-Note for which the wiki was written also came pre-installed with Linux. My hardware obviously is different from yours.

Does anybody have the same one that I have in my signature? It was the top-of-the-line model with Vista Business pre-installed.

---

### Post by skipsinclair on 2008-11-05
Yep.  Same mininote, Vista pre-installed.  Same problem.  In fact, various problems.  8.10 acted the same way as you reported.  I could only get it to boot into text mode.  Debian 4.0 didn't recognize the sata controller, but had corruption problems with the ctrl in legacy mode via BIOS.  CentOS 5.2 installed, but I couldn't get it to work with either the C9 drivers or the wifi (broadcom).  So I rolled back to Ubuntu 8.04.1, installed fine (in fact, I'm posting this now from the mininote).  I'll stick with this until someone more savvy than I figure things out...

---

### Post by xjgnsdof on 2008-11-05
> **skipsinclair said:**
> Yep.  Same mininote, Vista pre-installed.  Same problem.  In fact, various problems.  8.10 acted the same way as you reported.  I could only get it to boot into text mode.  Debian 4.0 didn't recognize the sata controller, but had corruption problems with the ctrl in legacy mode via BIOS.  CentOS 5.2 installed, but I couldn't get it to work with either the C9 drivers or the wifi (broadcom).  So I rolled back to Ubuntu 8.04.1, installed fine (in fact, I'm posting this now from the mininote).  I'll stick with this until someone more savvy than I figure things out...

Let's post bugs. The more reports, the better, right?

---

### Post by nickdngr on 2008-11-05
i have it installed on mine. it was kind of a pain in the ***. i did the automatic upgrade and that didn't take, had to reinstall from scratch. i used unetbootin to create a usb-live cd. 

seems to be working well, but i haven't installed the beta video drivers. audio works great, wifi, etc. 

the main thing to remember on the install is to add the xforcevesa to the boot line.

---

### Post by xjgnsdof on 2008-11-05
> **nickdngr said:**
> i have it installed on mine. it was kind of a pain in the ***. i did the automatic upgrade and that didn't take, had to reinstall from scratch. i used unetbootin to create a usb-live cd. 

seems to be working well, but i haven't installed the beta video drivers. audio works great, wifi, etc. 

the main thing to remember on the install is to add the xforcevesa to the boot line.

Is yours one of the models with SUSE pre-loaded?

---

### Post by nickdngr on 2008-11-05
> **elgilicious said:**
> Is yours one of the models with SUSE pre-loaded?

yeah, it came with suse, but i was having a ton of problems with it. being more familiar with ubuntu, i swapped out at the first opportunity.

---

### Post by xjgnsdof on 2008-11-05
Everyone who has gotten Intrepid to run seems to have the SUSE model, not the Vista Business model that I have. I'll have to go without tabbed file browsing and the other refinements of 8.10 for a while.

---

### Post by woodp on 2008-11-25
> **elgilicious said:**
> Everyone who has gotten Intrepid to run seems to have the SUSE model, not the Vista Business model that I have.

You may not be the only one - I started with SUSE and then installed ubuntu (with xforcevesa switch) without a hitch. Later, and just for grins, I installed XP. Didn't like it and decided to go back to ubuntu.

Now I have the experience as you - Basically 3-4 minutes after the ubuntu logo appears, it disappears and leaves a blinking cursor in the upper left hand corner.

The only thing I can guess is that I updated BIOS to F.05F

Did you ever come up with a solution? I don't have a copy of the older BIOS and thus have no way to downgrade. I'm stumped!

---

### Post by luvit on 2008-11-25
> **elgilicious said:**
> ...I get no splash screen and only a blinking cursor. I tried booting with "xforcevesa" and "acpi_osi=!"Windows 2006" to no avail... Has anybody gotten 8.10 to work on the Mini-Note?> **elgilicious said:**
> I have the higher-end Mini-Note that came with Vista Business. See my sig for the specs. The hardware is slightly different among the Mini-Notes.> **skipsinclair said:**
> Yep.  Same mininote, Vista pre-installed.  Same problem.  In fact, various problems.  8.10 acted the same way as you reported.... I couldn't get it to work with either the C9 drivers or the wifi (broadcom)... I'll stick with this until someone more savvy than I figure things out...i had that exact same problem.  the solution you're looking for is detailed in [[COLOR="Blue"]_**this thread**_[/COLOR]]("http://www.hp2133guide.com/forums/viewtopic.php?p=7176#7176")
.

---

### Post by woodp on 2008-11-25
> **elgilicious said:**
> Everyone who has gotten Intrepid to run seems to have the SUSE model.

What BIOS version are you running?

I had installed ubuntu some time ago and it installed and worked fine. Then I flashed the BIOS up to F.05F. Now I was unable to install ubuntu and got the same blank screen you are seeing.

Flashed back down to F.04F and ubuntu installs fine!

[LIST]
[*]F.04F docs: [ftp://ftp.hp.com/pub/softpaq/sp40001-40500/sp40310.html](ftp://ftp.hp.com/pub/softpaq/sp40001-40500/sp40310.html)
[*]F.04F code: [ftp://ftp.hp.com/pub/softpaq/sp40001-40500/sp40310.exe](ftp://ftp.hp.com/pub/softpaq/sp40001-40500/sp40310.exe)
[/LIST]

---

### Post by igor. on 2008-12-26
I've been having this problem too, I can confirm that it works with downgraded firmware. :)

---

### Post by skr on 2009-01-23
I installed Ubuntu 8.10 on my HP 2133 by upgrading the bios to F05,  I kept a note of what I did at [skrblog.blogspot.com]("http://skrblog.blogspot.com/") in case I need to reinstall everything, it may also help someone on this forum.

The most frustrating thing was not being able to get the microphone to work but thanks to ubuntuforums.org this was sorted.

---

