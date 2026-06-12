---
title: "Battery status on Acer Aspire 3002 in Edgy"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by notoriousdbp on 2006-11-06
Since I upgraded to Edgy, the battery status icon is all wrong.  It's only wrong when I'm on battery power.  Basically, it just shows an empty battery with 0% power - yet when the laptop is on mains supply the battery icon is fine (including when charging).  The last time I had any trouble like this was in Breezy - battery status was always fine in Dapper.  Could it be the generic kernel?  I was using the K7 version before and all was well there.  Has anyone else had any similar trouble since upgrading and is there a way to fix it?

---

### Post by notoriousdbp on 2006-11-06
For what it's worth, this is only a problem in Gnome.  I have KDE installed too and the battery status is fine in there.

---

### Post by notoriousdbp on 2006-11-06
sorry to be the only one replying to my own thread, but I would really appreciate any help.  The Gnome battery status monitor is now only saying 0%, 50% and 100% when the battery is charging with nothing in between.  It's a shame cos everything else had been working well in Edgy since I upgraded.  My laptop's not much use without a reliable battery monitor.

---

### Post by skirkpatrick on 2006-11-06
This is the first I've noticed it since I upgraded my laptop to Edgy but I haven't run it on battery since then.

---

### Post by notoriousdbp on 2006-11-07
so has anyone got any answers?

---

### Post by notoriousdbp on 2006-11-07
just rolled back to dapper.  solved.

---

### Post by compuguy1088 on 2006-11-07
> **notoriousdbp said:**
> Since I upgraded to Edgy, the battery status icon is all wrong.  It's only wrong when I'm on battery power.  Basically, it just shows an empty battery with 0% power - yet when the laptop is on mains supply the battery icon is fine (including when charging).  The last time I had any trouble like this was in Breezy - battery status was always fine in Dapper.  Could it be the generic kernel?  I was using the K7 version before and all was well there.  Has anyone else had any similar trouble since upgrading and is there a way to fix it?
I have a similar problem, on a Acer Aspire 3003LCi, the battery reads perfectly when plugged in in Gnome-Power-Manager, though when unplugged, it isn't accurate (100% if greater than 50% battery life; 0% if less than 50%). There was a previous post mentioning this, with a link to a bug report, which mentioned something about a HAL issue...

Edit:

Heres the bug report: [https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/66025](https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/66025)

And here is the other post about an issue that is very similar to this: [http://www.ubuntuforums.org/showthread.php?t=286603](http://www.ubuntuforums.org/showthread.php?t=286603)

---

### Post by Tiede on 2006-11-08
I am having the same problem with my Acer 3003WLMi laptop. The laptop keeps hibernating everytime it passes the 50% line and complains that my battery power is too low. When the battery is charging, it always shows: battery charging (100%)... This is a regression since I updated my DSDT table way back when I was in Hoary, then it worked out-of-the-box in dapper. The problem is thus definitely from edgy... Any ideas why? (I think i was too fast on my attempt to "fire-up the crackpipes!") :D

---

### Post by skirkpatrick on 2006-11-08
Same experience here.  I needed a new DSDT in Breezy and it worked fine out-of-the-box in Dapper.

---

### Post by compuguy1088 on 2006-11-08
Actually Im having hibernation issues as well....though suspend works fine...

---

### Post by notoriousdbp on 2006-11-16
Have any updates been released that solve this problem?

---

### Post by Tiede on 2006-11-20
> **compuguy1088 said:**
> Actually Im having hibernation issues as well....though suspend works fine...
to fix your hibernation issues, try [this solution I found in launchpad ](https://launchpad.net/distros/ubuntu/+bug/66637)(worked for me)... Turns out swap is not used by default in edgy... bug?

---

### Post by Tiede on 2006-11-20
> **skirkpatrick said:**
> Same experience here.  I needed a new DSDT in Breezy and it worked fine out-of-the-box in Dapper.
Do you have a Acer 3002 or 3003 laptop? Mine is a 3003WLCi and the DSDT table (A27 custom) found on sourceforge doesn't seem to work - Don't know why, it worked fine in breezy... if you have a 3003, can you send me a link to the dsdt.asl file you used?

---

### Post by Vaz on 2006-11-24
I'm having a similar issue on my Acer Aspire 5002, after upgrading to Edgy.

Mine will stay at 100%, then suddenly drop to 66%, and I'm assuming it'll go to 33% after that.  I haven't let it run down far enough to see if it'll go into hibernation when it shouldn't or anything.

---

### Post by Tiede on 2006-11-25
In malone : [   Bug # 73266](https://bugs.launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/73266)
hopefully that'll speed things up a bit...

---

### Post by Tiede on 2006-11-26
Ijust noticed that acpi shows the correct status info.
So i'm thinking It is debatable whether hal or gnome-power-manager is at fault...
Strangely, however, acpi -V gives the correct information:
Current output:
tiede@battery_problem:~$ acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 49.0 degrees C
  AC Adapter 1: on-line

And if I unplug it and leave it for a minute or two...
tiede@battery_problem:~$ acpi -V
     Battery 1: discharging, 97%, 00:27:26 remaining
     Thermal 1: ok, 48.0 degrees C
  AC Adapter 1: off-line

NOTE: while acpi said  I was at 97%, gpm showed 0%...
Do acpi and gpm/hal read the battery info in two different places?

---

### Post by notoriousdbp on 2006-11-26
This is the only thing preventing me from going back to Edgy so I would love to hear if they ever get the situation sorted.  To my mind, an upgrade should do everything the previous version did at the very least with a bit more added on.

---

### Post by notoriousdbp on 2006-12-04
Sorry to keep replying to my own thread, but is anyone else having trouble with their battery status in edgy, or was anyone having trouble and has managed to fix it?

---

### Post by Tiede on 2006-12-04
I think we all still are. But, just for the sake of it, go confirm the bug on launchpad, I opened bug #73266 about this recently, don't hesitate to add your 2 cents worth.

---

### Post by skirkpatrick on 2006-12-04
Problem still exists here.  I added my 2 cents to the Launchpad bug.

---

### Post by redsmoke on 2006-12-05
I have an Acer Aspire 5002 and am experiencing the same issue. When I unplug my laptop it occasionally thinks the battery is at 0% and then will shut down. Also it reports the battery level incorrectly from 100% to 50% to 0% rather quickly if anyone knows of a fix I would appreciate it. My batter reported fine in Dapper.

---

### Post by notoriousdbp on 2006-12-06
This is definitely a gnome problem.  I'm writing this in KDE on battery power in Edgy and the battery status is fine there.

---

### Post by Tiede on 2006-12-06
hmm... What model is your laptop. I am on KDE right now myself and the error still exists for me. Are you using a custom DSDT?

---

### Post by notoriousdbp on 2006-12-08
I've got an aspire 3002LMi.  Haven't installed anything special.  Installed standard Ubuntu with Gnome, then installed KDE using apt-get install kubuntu-desktop.  Upgraded to edgy from Dapper.

---

### Post by redoscar3 on 2006-12-11
I have an Acer Aspire 3003LCI and did a clean install of Edgy yesterday.  With a full battery charge, the battery monitor started at 100% and 3 hrs of time remaining.  It stayed there until an abrupt change to 67% and 2 hrs remaining.

Interestingly, the gkrellm battery monitor seems to be keeping perfect tab of the state of charge (I think it was at 92% by the time I got it installed).

So it definitely seems to be a problem with the Gnome Power Monitor application.  I am clueless as to how to fix it, but it seems to be a consistant problem as you guys are all seeing the same thing.  If Edgy shows any more showstoppers like this, I'll have to plug the Dapper drive back into this Acer.

Red

---

### Post by notoriousdbp on 2006-12-12
Have any of the developers seen this thread and are they doing anything about it.  Did they test it before edgy came out.  Like I have said before, it was working fine in Dapper

---

### Post by notoriousdbp on 2006-12-13
Gutted, I thought the kernel update might have fixed it.  But it didn't

---

### Post by chiron69 on 2006-12-19
I have an acer 1640Z and I have the same issue with kubuntu. My laptop will shut down after about 30mn with a fully charged battery.
The only workaround I've found has been to tell power manager to DO NOTHING when battery life is under 5mn.

---

### Post by fbarsoba on 2006-12-20
Hi.. I have an Acer Aspire 5000 WLMI and have the same problem with Edgy.. right now the battery monitor shows 0%, but acpi shows the following:

acpi -V
     Battery 1: discharging, 30%, 00:20:51 remaining
     Thermal 1: ok, 48.0 degrees C
  AC Adapter 1: off-line

This is really bad..

---

### Post by ThomasA76 on 2006-12-23
Anyone found any solution?
I have a HP7400 c2d and having problems with gnome power manager too...it freezes and wont change, 59% for the last 11 hours, doesnt matter if charging the batteries or not...
Would really be happy to find a solution for this...

---

### Post by redsmoke on 2006-12-30
Still waiting on a solution for this as well. i tried install kubuntu since someone mentioned they didn't have the problem with kubuntu but i still experienced the same issue.

---

### Post by Tiede on 2007-01-08
Battery status insight.

I think I know why the battery information is wrong on acer laptops. The battery info is being written in /proc/acpi/battery/BAT1/, while some programs are polling for battery info in /proc/acpi/battery/BAT0/ (I found that reading the output of conky while running in terminal mode). I immediately thought of making a symbolic link to BAT1 from BAT0, but no matter which way I try, the kernel won't let me write to that location. Verily, when I change the polling location in conky from BAT0 to BAT1, my battery info is readily available.
Can anybody else confirm this and/or has an idea (whether it stems or not from this insight)?
acpi -V read the info from BAT1, therefore, it's info is good. I'm thinking gnome-power-monitor is looking for /proc/acpi/battery/BAT0, just like conky is,  and could not find it...

---

### Post by notoriousdbp on 2007-01-09
Drat, another kernel update and still no fix.  I keep saying it but it worked in Dapper.  I'd be interested to know how you change the polling though.

---

### Post by Tiede on 2007-01-10
in .conkyrc, instead of $battery, I use ${battery BAT1}. I don't know how to make it system-wide, though...

---

### Post by notoriousdbp on 2007-01-20
Now here's a thing.  In KDE, klaptopdaemon works fine but if you use kpowersave it doesn't - on mine.  Gnome is still in a mess no matter what you use

---

### Post by Tiede on 2007-01-20
Well, I might as well say somethin' too... In enlightenment, it seems to work just fine. (Using e17)

---

### Post by notoriousdbp on 2007-02-07
Note to developers - I hope this is fixed in Feisty.  It's clearly not going to be fixed in edgy now

---

### Post by otake-tux on 2007-02-23
I have this same problem.  I'm almost positive it is a gnome problem.  Like someone else said, gkrellm displays the battery information correctly.  Hopefully this will get solved.

---

### Post by Jorge on 2007-03-11
This is definitely a problem in Edgy. I had have Dapper, Edgy and now Feisty on the same laptop (Acer TM 3002 WTCI) and the power management was OK on the first and last of those Ubuntu versions. 

Now I had a reliable battery meter and, even more important, a computer not trying to hibernate with 95% of battery left. 

So, do not despair, Feisty is around the corner...

---

### Post by NocturnalDeviant on 2007-05-18
I've just installed Feisty on my Acer Aspire 1642WLMi it shows no battery charge whatsoever.  Whats going on?

---

