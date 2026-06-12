---
title: "Acer Aspire 5315 Shuts Down"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by nvance on 2007-11-05
Good Evening,

I have installed 7.10 (32 bit) on my Acer Aspire 5315 (dual boot with Vista).  One of the nagging issues is that the laptop just shuts down.  It does not appear to shut down at any specific time frame.  I am thinking that it possibly shuts down after a few minutes without activity???  I am not convinced that this is a heat issue.  I have checked the power settings and they appear alright.  I thought that this was an issue with the 64 bit so I installed the 32 bit also and I am still seeing the issue.  
If there is any information that someone could provide me it would be much appreciated as I am trying to migrate from a smaller Dell Latitude D600 and would love to use the new laptop.  I have been using Ubuntu for almost a year and love it.  

Thanks,
nvance

---

### Post by mcauley on 2007-11-08
I am having the same issue with my Aspire 5315. The fan is definatly not running when this happens and the case is rather hot. This usually takes about 40 min of web surfing to occure. I have observed some times when the fan operates normally. The last time I noticed the fan working I was running on the battery, but I don't know if this is related. My wife has the machine on a business trip at  the moment so I can't check anything until the weekend. Do you know if this is an issue in Windows? I wiped off the Vista partition on mine the day I brought it home.
Scott.

---

### Post by joetrizeo on 2007-11-10
I too have a 5315 (-2153) and am having the SAME exact problems.
hopefully we all can describe our problems, circumstances and possible solutions to  get to the bottom of this.
here's mine.
first of all i am dual booting between Vista and XP and have seen the problem in BOTH OS's.
first time my daughter was playing the game "purble place" that comes with vista, random shut down (turn off)
it boots right back up again no problem.
the next few times i was just surfing the web with firefox
last time i was watching a 20 min video clip.  about 15 min into it it shuts off.
then i boot it back up and watched the last 5 min and it shut off again.
this is the most interesting time because the laptop was on cushion-y leather so i suspect a heat issue.

right now i am running prime 95, firefox and a video.  prime95 has my cpu maxed at 100% for the last 10 min.  my fan is running (it is quiet tho) and i have not experienced failure.

i will try to narrow this problem down and report back here if i find more consistency.

anyone try acer tech support? I'd assume the responses are across the board from "its the fan" to "bad battery" or "bad MB"

-Joe

---

### Post by joetrizeo on 2007-11-10
well i ran mine at 100% cpu for like 2 hrs and nothing happened.
the fan was running constantly and 'speedfan' said my cpu was at 50c the whole time.
i did have the laptop on a smooth flat surface.  when my cpu isn't under load 'speedfan' says it is at 45c and the fan is very low and or off.

if i get balls-ey i might try running 100% cpu and blocking the fan ports and seeing what happens...

does anyone else have a temp/fan monitoring program? i dont trust speedfan since it doesn't recognize the fan (doesnt display rpm's) and the cpu temp only switches between 45 and 50, no in between.

---

### Post by mcauley on 2007-11-10
Mine is still shutting down. Once I reboot after a shutdown the fan starts working. i have the phonne number for tech support. 
Contact the technical support line at 1-800-816-2237. Hours of operation for live support are from 7am-9pm CST Mon-Fri and 8:00am - 5:00pm CST Sat & Sun, excluding holidays.

---

### Post by trunkster on 2007-11-11
I'm having the same problem, Acer Aspire 5315-2153. It's the model from the Walmart sale that was about a week ago. It's coming to the 15 day return policy so I hope we can find the problem. I am having random shutdowns only about once a week. It's a little strange, it sounds like others are having issues with random shutdowns within minutes of booting. I tested the memory and everything is fine. It's running a clean copy of Vista Home (without all the Acer software/trailware). I was wondering if it was Vista but it looks like XP and even Ubuntu has the same issues. Most likely then it's a hardware issue, I'll try to dig into it a little more and post up any info I find.

---

### Post by mcauley on 2007-11-11
This morning I called Acer support and they said to send it in for repair. I'll report back how this goes....
I bet it comes back with Vista reinstalled. :(
Scott.

---

### Post by mcauley on 2007-11-11
Does anyone think it could be BIOS related? The bios on mine is 1.17 and the acer site shows an upgrade to 1.19.  Has anyone tried flashing the bios in an attempt to fix this issue?

---

### Post by joetrizeo on 2007-11-11
Has anyone confirmed this only happens either on battery or plugged in power only?
I'm not sure but I'm leaning towards this only happening when it is NOT plugged in.

It did it again for me this morning.  It was on battery power and playing a movie.  About 10 min into it it shuts down.  I could not confirm whether or not the fan was running.

I booted back up and ran it hard 100% cpu for 40 min on battery power and it did not shut down.  It seams to do it when I'm not looking for it.

I have bios 1.9 and can say it is NOT BIOS related.

Everyone check your power settings for plugged in vs battery and see what times it shuts off the hard disk.  I'm thinking it could be sensing idle and turning off the hard drive after a period of time.  but this doesn't make complete sense to me.

For the record, it is a HARDWARE issue, not a OS (or software) issue.

for my next test i'm going to leave it sit off for a long time and then utilize 100% cpu on battery power and see if the fan kicks on.

i too have experience a warmer than usual keyboard/underside when it kick off.

---

### Post by mcauley on 2007-11-11
I have observed this behavior on battery power and plugged into the supply. The cooling fan is definitely not running when this occurs. I think it's interesting to note this happens on both versions of the bios. This almost certainly makes it a hardware problem or manufacturing defect. 
Scott.

---

### Post by joetrizeo on 2007-11-11
Well I made it do it, I know whats going on.

100% sure that these acer 5315's are OVER HEATING because the fan is not kicking on when it need to be.
You are right, the fan is NOT running when it happens, the computer over heats and shuts down to save itself.

WHY or what causes the fans to NOT kick on i do not know but Acer definitely needs to fix this.

here's how i made it do it.  I shut my lid and put my computer into stand by for a  few hours.  I came back and woke it up.  I unplugged the power (so it was running on battery) and loaded the processor to 100%.  I felt the temp of the underside and keyboard get hot, and never once felt or heard the fan running.  Then like clock work at 13min into it the comp shut down.

I booted back up and ran my temp monitor and it said the cpu was at 95 deg C!
The fan kicked on (automatically) now and the temp went down.

the fan is now keeping it between 45 and 55c.

next i will see if this does it also when it comes off a cold boot (not from standby) and verify for Scott that it does it irregardless of plugged in or not.

---

### Post by mcauley on 2007-11-11
Have you noticed that after it overheats,  the fan will run continuously after the next boot, and you can then use the machine normally for hours, but the fan doesn't shut down even after you close the lid and let it sit idle for an hour or more? I let it sit last night with the lid closed for over an hour and the fan was still running at full speed blowing cold air.

I hope acer service can fix it.

Scott.

---

### Post by joetrizeo on 2007-11-11
interesting scott, no i have not noticed this, but will watch for it.

mine operates normally after the next boot, meaning the fan will be low or off between 40 and 50c.  if i were to load the cpu, the temp goes to 50-55 and the fan kicks on.  it goes off again once the cpu idles and temp drops.

but you are right, after it overheats (what i call 'bad boot mode') the next boot is 'good boot', i can use the machine for hours with no problems what so ever, even if i stress it.

---

### Post by joetrizeo on 2007-11-12
well the problem is definitely a shut down due to overheating caused by the fact that our fans are not coming on no matter how hot or how much load the cpu is under AFTER they are awoken from 'stand by'

i suggest everyone install this util

[http://www.diefer.de/i8kfan/index.html](http://www.diefer.de/i8kfan/index.html)

it's a fan and temp monitor but designed for dell so the fan capabilities do not work but it DOES accurately display your cpu temp.  the normal cpu operating range should be between 45-55 deg C.  I have witnessed it go up to 70deg C without the fan kicking on when the problem is triggered.

a software level fan monitor would be nice to manually control the fan, since whatever acer uses isn't working.

it does happen irregardless of batter or plugged in state as Scott said.

next i will try to make it happen coming off of cold boot and hibernation.

---

### Post by joetrizeo on 2007-11-13
Another observation:

It doesnt matter how long the computer is in standby.  As soon as it goes to standby, the fan shuts off, and never comes back on after it is woken up. (until reboot)

I ran my processor to 55deg, then put it on standby for 30  seconds, then brought it back up, ran my cpu to 100% and the temp kept climbing (60, 70).

point being, dont put your computer into standby. (which is what laptops do best)

---

### Post by panda156 on 2007-11-13
intresting i have the same problem as you all and i think it is a bios problem
this is how i conclude this:

when my acer overheat i runwhindows  biosflash aplication and my fan imediatly start?!? whery strandge

---

### Post by .mark on 2007-11-13
I played with my laptop one week as it was. No changes was made to BIOS or to system. I did not install any additional software. I did not see any problems that was mentioned here on the forum. One week later I upgraded BIOS and reinstalled OS to Vist@ Enterprise edition. It was clear install. I wiped drive "C" before installation of other OS. The Int@l chipset drivers was installed properly. After that shutdown problem have begun. If I work with the computer continuously it is fine. No overheating, no shutdowns, fan works fine. But when I live the laptop for 30 minutes or so it goes to screensaver and than to sleep mode. When I started to work with the laptop after 30 minutes pause fan did not wake up. And when the CPU riches 95C (203F) and system itself 70C (158F) computer shutdown appeares. After startup (reboot) computer is working fine, fan is too. But after 30 minutes pause all the problem repeats.

After that , I did clean install of Win XP SP2 with all necessary drivers. The same problem with shutdowns after standby but not if I work continuously.

Any ideas?

---

### Post by joetrizeo on 2007-11-13
.Mark, you are having the same problem we are all having.  this is clearly a hardware issue acer needs to solve.  *why* it is happening is clear, whatever controls the fan isn't doing its job.  how to fix it, we don't know.

THIS IS INDEPENDANT of the OS that is installed.  I noticed this problem BEFORE i upgraded my bios and it happens with the factory install of Vista.

i'm on the phone with  acer right now, the first person i came to had no idea of the problem.  we'll see what happens next.

---

### Post by joetrizeo on 2007-11-13
Everyone call Acer Tech support 1-800-816-2237 and tell them you are having a problem with these machines.
Make it be heard because...

I just got off the phone with acer and they haven't heard of this problem.  So I gave them my SN and name and stuff and they are forwarding my problem to the engineers or 'elites' as my tech support guy put it.

Once they have a solution if it is a major problem with the model (this appears to be) they will post it here.

[http://www.acerpanam.com/synapse/forms/portal20.cfm?website=AcerPanAm.com&siteid=7117&areaid=2&formid=3390](http://www.acerpanam.com/synapse/forms/portal20.cfm?website=AcerPanAm.com&siteid=7117&areaid=2&formid=3390)

interesting to note is my tech kept trying to talk about about acer's proprietary software "ePower Management" as a tool to put the computer into sleep and wake it up etc.

i kept asking him if that controlled the fan and he did not give me a straight answer.

i am no expert on laptop design but i fail to believe that you would need a proprietary third party software to control hardware aspects of your system automatically.

never the less, I'll see what i can dig up.

---

### Post by joetrizeo on 2007-11-13
Well you're not gunna like this guys.
I put two and two together and realized everyone had reinstalled their own OS.
So that got me thinking that maybe it is something that comes bundled with acer that you have to run.

Well here's the "answer".  It's not a solution because you shouldn't have to do this to make the computer run right.

You have to run ePowerSvc.exe, Acer's ePower Service which runs as a WMIService.
Whatever the hell that does, it makes the fan come back on after stand by.
I know I know, this is a Ubuntu forum and I know nothing about or even if you could run a windows service on Linux.  Sorry guys, but this is the 'fix'.

It works in vista, I'll see if it works in XP.

Again, it answer the problem but it is totally bassackwards.

Anyone else verify?

Anyone want to program a Linux or windows program that will control the fan?

---

### Post by arjnav on 2007-11-13
As soon as I got the laptop I uninstalled all the acer proprietary software, including the power management component. I'm waiting for the weekend to find some time to install ubuntu. So far I haven't had this fan issue yet. It's actually remained pretty cool so far. 

I'm going to download software to monitor the cpu temp etc. Post back if I find anything!

---

### Post by JonathanSteenbrugge on 2007-11-14
I also have the same acer laptop as you guys.

As soon as I received mine, I killed the windows partitions, and reïnstalled vista with the bootable cd's one can make with the tools provided by Acer. I'm running vista now an because of your problems trying to figure out if I have the same problem.

The only thing I can see is that if the CPUtemp always goes up till 55°C, than the fan goes on, dropping the temp to 52°C. Than the fan stops and heating begins. So the fan always goes on and off.

I cannot remember if I had the sam thing when computer first started, without right out of the box. 

I nuked the acer empowerment **** as it does alll the same things Windows can do.

I am planning to install Ubuntu on my pc but I am still waiting for my official install CD. It should be here soon.

Does anyone know if I can do CPUscaling with ubuntu? This is very usefull when running small applications on battery, so that it lasts longer. I know in Gentoo it was possible, but I'm into Ubuntu now...

---

### Post by joetrizeo on 2007-11-14
> **arjnav said:**
> As soon as I got the laptop I uninstalled all the acer proprietary software, including the power management component. I'm waiting for the weekend to find some time to install ubuntu. So far I haven't had this fan issue yet. It's actually remained pretty cool so far. 

I'm going to download software to monitor the cpu temp etc. Post back if I find anything!

try letting or putting your computer into sleep or standby, bring it back up then test your cpu to 100% and see where the temp goes.  then see if the fan is on or not.  you may have to put your ear or cheek by the fan outlet on the back.

---

### Post by joetrizeo on 2007-11-14
> **JonathanSteenbrugge said:**
> I also have the same acer laptop as you guys.

As soon as I received mine, I killed the windows partitions, and reïnstalled vista with the bootable cd's one can make with the tools provided by Acer. I'm running vista now an because of your problems trying to figure out if I have the same problem.

The only thing I can see is that if the CPUtemp always goes up till 55°C, than the fan goes on, dropping the temp to 52°C. Than the fan stops and heating begins. So the fan always goes on and off.

I cannot remember if I had the sam thing when computer first started, without right out of the box. 

I nuked the acer empowerment **** as it does alll the same things Windows can do.

I am planning to install Ubuntu on my pc but I am still waiting for my official install CD. It should be here soon.

Does anyone know if I can do CPUscaling with ubuntu? This is very usefull when running small applications on battery, so that it lasts longer. I know in Gentoo it was possible, but I'm into Ubuntu now...

ya it's clear that nuking the acers Empowering technology bloat ware causes this problem
hopefully they will have a firmware update for this problem and not say 'oh well you must run this to make it work'  BS!

ya the fan goes on and off like a normal laptop, keeping it betwen 45ish and 55 ish.  but after standby w/o ePower, it keeps  climbing, 60, 70, 80, 90, shutdown...

---

### Post by joetrizeo on 2007-11-14
I haven't gotten it to work in XP yet.  Primarily because i haven't found an 'empowering technology' program that is for XP (not that i want to run it)

---

### Post by mcauley on 2007-11-14
Well, I took mine back to WalMart this evening and they issued a full refund. It's a shame too, because I really liked it, and thought it worked nicely with linux except for the overheating problem. Anyone have any suggestions on a laptop solution?

Scott.

---

### Post by .mark on 2007-11-15
> **joetrizeo said:**
> Another observation:

It doesnt matter how long the computer is in standby.  As soon as it goes to standby, the fan shuts off, and never comes back on after it is woken up. (until reboot)

I ran my processor to 55deg, then put it on standby for 30  seconds, then brought it back up, ran my cpu to 100% and the temp kept climbing (60, 70).

point being, dont put your computer into standby. (which is what laptops do best)

I agree with the quote. Why it happens? I found a reason. I installed Win XP SP2 and all drivers for hardware. But I did not install any acer's additional software. Than a put the laptop to standby mode, the fan shut off and never turned on again. But when I run CPUCooL program fan emediately started working. It means that the program was searching for CPU and for the fan status so the program turned on the fan. If I do not use CPUCool software computer shuts down after\ because of overheating. Conclusion: OS can not take care of fan. It should be run with some peace of additional software. May be I will find what peace of acer software will take care of it. And I will look for Linux solution because I like Ubuntu more than vista or XP

---

### Post by joetrizeo on 2007-11-15
excellent info .mark.  Actually, i'll go as far to say that HARDWARE should control the fan, not the OS or crappy acer software

---

### Post by Malekish on 2007-11-15
> **joetrizeo said:**
> Well you're not gunna like this guys.
I put two and two together and realized everyone had reinstalled their own OS.
So that got me thinking that maybe it is something that comes bundled with acer that you have to run.

Well here's the "answer".  It's not a solution because you shouldn't have to do this to make the computer run right.

You have to run ePowerSvc.exe, Acer's ePower Service which runs as a WMIService.
Whatever the hell that does, it makes the fan come back on after stand by.
I know I know, this is a Ubuntu forum and I know nothing about or even if you could run a windows service on Linux.  Sorry guys, but this is the 'fix'.

It works in vista, I'll see if it works in XP.

Again, it answer the problem but it is totally bassackwards.

Anyone else verify?

Anyone want to program a Linux or windows program that will control the fan?

That's a very good analysis of the problem, Joe, and you're probably right.  It sounds like we're going to need to find some existing fan-control program and adapt it to be able to handle this specific laptop.

I'm a linux noobie, what fan control / cpu temp monitoring software is out there?

---

### Post by Malekish on 2007-11-15
Figured out how to add applets to the bar up top (Ding!  You have leveled,  you're now noobie2) and added a CPU temp but it seems stuck at 40c

I tried installing the CPU / Fan monitor that Joetrizeo linked but it threw up during the make process, I'm guessing it's because I installed the 64-bit version of Ubuntu.

Off topic, should I have stuck with the plain old 32 bit version, it seems as if more things work there and based on my mad linux skillz simple = better for now.

---

### Post by kameleon25 on 2007-11-21
I too am having this same exact problem. I shall call acer support friday as I won't be able to call today or tomorrow. Thanks to all that have put time in on pinpointing the problem.

---

### Post by joetrizeo on 2007-11-21
lemme know if they have a solution.  the fan on the computer should be hardware controled no matter what OS you use.  terrible.

i'm called acer and told them to look at this issue and gave them a couple weeks to figure it out.  i'll call them next week myself.

---

### Post by Moey on 2007-11-23
hopefully we can get this figured out, because this is also frustrating.  I have a temp monitor running in my taskbar, and there is nothing more frustrating than when you are tring to do something, whatching the temp rise, and knowing its going to shut down soon.:mad:

---

### Post by joetrizeo on 2007-11-24
exactly.  I've mitigated the problem by setting my settings to never go to standby.  still not a solution.

---

### Post by joetrizeo on 2007-11-25
I found this in another forum asking about how to control the fan manually.

*"Okay, it seems that Acer  control  the fan  speed with some proprietary hardware/software combination and settings that doesn't allow third party access."*

Well this is bul$hit.  I dont have to run any software to get hardware to work properly.

Looks like you have to run ePowerManagement bloatware.

I'll call Acer next week and see if they have a fix.

---

### Post by nvance on 2007-11-26
UPDATE!!!

I have been still playing with this issue and it appears that it might be related to 64 bit as opposed to 32 bit.  I have tried 2 other distros (32 bit) and no problem with the laptop shutting down.  I also tried the Ubuntu and Kubuntu live DVDs (also 32 bit) and I am not getting the laptop to shutdown or freeze.  When I originally posted this thread I was having the issue with 64 bit, not thinking that I should try 32 bit.

I am not 100% that this is a solution, but for the meantime it appears to work and I am able to have the laptop go to sleep mode and when it wakes it still functions properly.

I will update as necessary.  Hopefully this helps some others out.

Thanks,
Nate

---

### Post by vonWoland on 2007-11-28
I have had the exact same problem, and though I don't want to belive it, the problem may be using a 64-bit versus a 32-bit system.  So far this has been my experiance:

32-bit Vista:  no problems (other than having to run Vista)
64-bit Ubuntu (install and on LiveCD):  no fan, shuts down
64-bit  Gentoo (install and LiveCD): no fan, shuts down.

I am installing 32bit Ubuntu now, and will post back here with results.  Meanwhile, I would love to hear if anyone else had the same experiences.

---

### Post by monte48lowes on 2007-11-28
I had the same issue with mine. It is caused by going into 'hibernation' or 'sleep' mode. When the system is restarted the fan does not come on. Additionally, I had a CPU temperature applet running with super karamba to monitor the temperature. The applet merely polls ACPI temperature with 
```
cat /proc/acpi/thermal_zone/TZ01/temperature
```. I ran that code in a terminal and it came back blank. I am thinking there is a bug in the acer_acpi package, possibly.

Mike

Can you guys try this when the fan fails to start?

```
sudo /etc/init.d/acpid restart
```

---

### Post by monte48lowes on 2007-11-28
Well, I just ran the test I posted earlier today. No luck. The fans don't start and I cannot poll the temperature. It is stuck at 45C.

Mike

---

### Post by MarttiTheFinn on 2007-11-29
Same problem here, running 5315 with 7.10 version. I installed uwsusp to get both sleep and hibernate work. I got hibernate to work with s2disk, and it looks that s2both also stores data to RAM.

Coming back from either of them..machine heats up and shuts down. I haven't noticed this behaviour in Vista and after cold boot also not in 7.10 either.

I upgraded to .19 version of BIOS -> no change in behaviour.

I was unable to get any temperature readings..shows always 0.

---

### Post by monte48lowes on 2007-11-30
Well, taking a closer look at the ACPI part of this, I decided to install the acer-acpi package from the repositories. Now ndiswrapper refuses to load. Please do not load this package, unless it was already loaded. I am going to reinstall this weekend...

Mike

I want to document the step-by-step installation process as well.

---

### Post by gerbazio on 2007-11-30
Hi guys, is acer aspire (or the other models mentioned in this thread) mounting some amd athlon xpm processor?

I've an issue similar to yours with my asus laptop (L3000D), which has an amd athlon xpm2500+, see:
[http://ubuntuforums.org/showthread.php?t=627482](http://ubuntuforums.org/showthread.php?t=627482)

It seems others had similar problems  and it appears this problems started with the 7.10ubuntu version which perhaps is no more working properly with powernowd cup frequency scaler, see for example:

[http://ubuntuforums.org/showthread.php?t=525063](http://ubuntuforums.org/showthread.php?t=525063)

and maybe also this could be related:
[http://ubuntuforums.org/showthread.php?t=627540](http://ubuntuforums.org/showthread.php?t=627540)

all of these are still not solved...

---

### Post by monte48lowes on 2007-11-30
Thanks for the reply. I do not have CPU frequency scaling working either. That's not a problem since the laptop stays cool, when the fan is able to run. For some reason the fan shuts off and does not restart after going into hibernation and coming out again. It does the same thing in windows if Acer's ePower services are not installed and running. I think Acer has implemented a different way of communicating with the CPU and fan. I had posted earlier about how I can poll the temperature of the CPU when running from a fresh boot, however after restoring from hibernation I can no longer do so.

Mike

---

### Post by vonWoland on 2007-12-01
Switching to the i386 from the 64 bit version of Ubuntu did solve all these problems for me after all.  "Suspend" locks up the display, but I think this may be an X.org problem.

On the whole, running Ubuntu in 32-bits on this system feels much less buggy.  I wonder if the problem is with this Celeron chip, or perhaps this laptop has hardware controllers that are 32-bit, and thus are not able to work with a 64-bit system.

I am, however, no CPU engeneer or kernel hacker, so I don't really know what I am talking about other than the 32-bit Ubuntu seems to work.

---

### Post by pet2000 on 2007-12-06
I don't believe this problem is related to an OS. I have owned other acer laptops and this problem always accurred when I did not run the acer ePower application. I only realised this after I had bought another acer laptop, the aspire 5315 :(. Acer must have altered (intentionally or not) their motherboards so the fan is regulated by their ePower software rather than by the hardware (or bios). The fan problem occurs with Linux, Windows XP and Windows Vista, the symptoms are the same, the fan will not come on after sleep/hybernation mode. Because this also happens with Windows Vista, I am trying to get acer service to give me a solution because I believe that I was sold a computer to run with Windows Vista, which it clearly doesn't unless I run additional software, i.e. acer ePower. The problem with ePower is that it uses a large chunk of system resorces which slows down the running speed of my computer. I don't need their software and prefer to work without it but can't because of this problem with the fan. I suggest that everybody here complain to acer about that, but please only refer to Windows Vista in your  argument, so acer can not refuse and say they do not support your OS (as they already did with Windows XP enquiries). In future I will stay clear of acer unless they supply a solution for this fan problem without having to run their bloatware.

---

### Post by MarttiTheFinn on 2007-12-07
Did some testing with Vista only and I can confirm that the fan does not start after suspend/hibernate if the Acer empowering "services" are not running.

I don't recall that the manuals say that those services must be active..acer should fix this.

On the other hand..ubuntu still refuses to return from suspend..black screen, hibernate wake-up works (using s2disk), it is a bit slow to go sleep compared to Vista. This makes ubuntu still a bit unusable, I'd prefer to use s2ram. Vista performs nicely with suspend, very fast wake-up and go-to-sleep times.

---

### Post by pet2000 on 2007-12-12
Addenda: A forum member has contacted Acer about the overheat and shut down issues and Acer has confirmed that when the ePower software is not active, the fan will not function properly (overheating after sleep or hibernation mode). This applies to ALL of Acer's notebooks sold with Windows Vista (ePower is only available for Windows Vista). Acer has NO INTENTION to fix this problem because they do not consider this a fault. ePower has also a massive impact on the speed of the computer especially on low spec Celeron machines. What this means is that if you want to  run your Acer notebook faster by disabling ePower and other bloat ware or if you want to install Ubuntu or Windows XP, you need to live with those shortcomings. There maybe other issues but I have tested my 5315 extensively with Windows XP and have not come across any so far. Drivers for Windows XP are all available, albeit you need to search for them  from the manufactures web sites (when I have time over the holidays I will upload all drivers and publish the link for people to download). Conclusion: If you want to run Ubuntu or Windows XP on your notebook or want to run your notebook faster, DON’T BUY ACER! However, I will probably not return my 5315 because for the same price I cannot find one with all the specs important to me (1x1GB DDR, S-Video, 2.5hrs battery life). To avoid overheating I set the power setting to “shut down” when lid is closed and NEVER use sleep mode or hibernation mode. I also urge everybody to spread the message about the shortcomings of Acer notebooks on forums and especially on user feedback sites such as ciao, yahoo, etc., because I believe this may help Acer to change their mind and come up with a fix.

---

### Post by joetrizeo on 2007-12-12
that's bullsiht.

then WHY does the fan and computer function properly off a cold  boot no matter what you do.
no problems no matter what you do when it's turned on from a power off state.
the problem is only present AFTER the first instance of setting it into standby mode.

---

### Post by MarttiTheFinn on 2007-12-13
> then WHY does the fan and computer function properly off a cold boot no matter what you do.
no problems no matter what you do when it's turned on from a power off state.
the problem is only present AFTER the first instance of setting it into standby mode.

Agree with joetrizeo, but I'm still a bit uncertain whether this happens everytime. After a cold boot the fan works always, but sometimes (not always, I think) after either sleep or hibernate the fan never starts again. Have you found out does this relate to sleep or hibernate or both?. I scanned the vista system logs if the epower service could have died but logs looked quite ok.

---

### Post by Batinse on 2007-12-13
I have had this same problem, but I have the Acer Aspire 1640 Laptop.  The freeze does not happen in Windows XP, and it has been happening with increasing frequency under Linux (7.10 GG).  It's a cheap, crappy box, so it doesn't surprise me that the problem is some piece of lousy software--I mean, why would you want to run anything else besides XP, right?  I should also add that I have this problem whether I start from a cold boot or from hibernation/standby mode.  At this point, after fifteen minutes or so, it's game over.

Would it be advisable not to hold my breath for an Acer ePower manager emulator for Ubuntu?

Also, some posters were saying that under 32-bit ubuntu the problem didn't surface (as much?)  How do I know what bittage of ubuntu I'm running?  Was FF 32-bit and GG 64? (*Embarrassed at the rookie question*)

---

### Post by joetrizeo on 2007-12-13
Batinse - can you link, supply, or upload the service or ePower managment for the 1640?
maybe it'll work for xp on the 5315

---

### Post by pet2000 on 2007-12-14
> **joetrizeo said:**
> that's bullsiht.

then WHY does the fan and computer function properly off a cold  boot no matter what you do.
no problems no matter what you do when it's turned on from a power off state.
the problem is only present AFTER the first instance of setting it into standby mode.

This is exactly what I said. This happens only after sleep/hibernation mode. You need to make sure that you switch off those modes in the Power Options so your computer does not go into sleep mode automatically..

---

### Post by joetrizeo on 2007-12-15
> **pet2000 said:**
> This is exactly what I said. This happens only after sleep/hibernation mode. You need to make sure that you switch off those modes in the Power Options so your computer does not go into sleep mode automatically..

I know....what I'm saying is it is clear that the computer will function normally WITHOUT these services running (only on the first boot). You need the service running for it to come back on after sleep/standby. 
but WHY are they required since it's proven it *can* work fine without them.

---

### Post by Batinse on 2007-12-16
> **joetrizeo said:**
> Batinse - can you link, supply, or upload the service or ePower managment for the 1640?
maybe it'll work for xp on the 5315
Hi Joe.  I'd love to, but unfortunately, my laptop just quit, it seems.  I might have a fried card or two, but if I get it back up and running, I'll uplaod the software.

---

### Post by kung foo priest on 2007-12-16
To anyone who couldn't fix this yet and is using an ***amd_64 kernel** on an **acer aspire 5315** (Celeron M 530 in my case).
It appears that the problem lies with (possibly ACPI and) the temperature sensor of the processor.

I've just bought the thing and installed debian testing amd64 on it; with the result that everything would work fine for some hours but then the heat would eventually rise (the quicker the more i stressed the system) and shut down because of the safety measures the bios obviously provides.

After playing with it for 2 days i figured out that when i would turn the thing on after it had just crashed from overheating, sometimes the fan would be running. The fancy temperature applet that i installed for gnome (the packages name on deb is computertemp btw.) showed 55 when the fan was running and the whole thing kept cool no matter what i did. And that was when it hit me; the temperature was not updating. Somehow the senor stopped reading new results after bootup (or did it only once).
And since neither upgrading to sid nor reloading the appropriate kernel-modules helped i settled for a 32 bit install. (which i had to do anyways since dist-upgrading to sid somehow f***ed up gnome :)

so.. long story short: "somehow the 32bit version of debian testing does let the bios do it's job at updating the temperature and it only seems to be a software problem. (hang up your phones to acer ;)

I'd suggest loading some live-cd's and figuring out which distro works..

so long..

---

### Post by Batinse on 2007-12-19
> **joetrizeo said:**
> Batinse - can you link, supply, or upload the service or ePower managment for the 1640?
maybe it'll work for xp on the 5315

Ok, it seems you can download the ePower Managment tools from this site:

[http://www.driverstock.com/Acer-Aspire-1640-driver-download/4-21-12838-93460/index.html](http://www.driverstock.com/Acer-Aspire-1640-driver-download/4-21-12838-93460/index.html)

I don't know if this helps, but voila.

---

### Post by Darksword on 2007-12-20
These guys seem to have fixed the various (numerous) problems with the 5315 in XP.

Perhaps we can bang our heads together.  They seem to know of our plight.

---

### Post by iXneonXi on 2007-12-21
I got the laptop for Christmas and am dual booting XP and Ubuntu 7.10. I have not noticed the issue in Ubuntu (I'm running x86) but that is because I can't come out of sleep mode without blanking the screen. In XP I have noticed the issue after coming out of sleep. I have Speedfan installed.

I will try to help as well, but since currently there are 57 posts, will anyone help me get up to speed on the issue?

PS. I'm also looking for ePower Management for XP on the 5315 if it exists...

---

### Post by joetrizeo on 2008-01-04
SOLUTION FOR XP!!!

download this and install

[http://www.acerpanam.com/synapse/data/7117/documents/as1640_epower.zip](http://www.acerpanam.com/synapse/data/7117/documents/as1640_epower.zip)

[https://www.synapsenow.com/synapse/data/7117/documents/AS1640_ePower.zip](https://www.synapsenow.com/synapse/data/7117/documents/AS1640_ePower.zip)

acer epower managment 1.5.6 (version 1.6.8 will work too)

[http://www.acerpanam.com/synapse/data/7117/documents/as1640z_epm.exe](http://www.acerpanam.com/synapse/data/7117/documents/as1640z_epm.exe)

what they do is install two drivers you need and run them when xp starts with other services
EpmPsdAcer EPM Power Scheme Driver	Acer Value Labs, USA	C:\windows\system32\drivers\epm-psd.sys
EpmShdAcer EPM SHD ECV-TO	Acer Value Labs, USA	C:\windows\system32\drivers\epm-shd.sys

---

### Post by nalimilan on 2008-01-15
Hello all! I've the same problem, and I reported it on the Linux kernel bugtracker here:
[http://bugzilla.kernel.org/show_bug.cgi?id=9754](http://bugzilla.kernel.org/show_bug.cgi?id=9754)

A developer asked me informations I can't give because I don't have Windows installed on my computer. Could any of you check for that? It would really help to solve this issue. Thanks in advance.

Here's what he would like to know:
"What happens on Windows when the platform-specific tool
is not present or disabled -- does the fan
behave the same way as on Linux?  What if the tool
is started only after the resume, does the system get better,
or is it necessary for it to be running before suspend?
How about if the tool is stopped after resume, does
the system continue to update temperature without it?
The more you can tell us about how the tool works
the better chance we have of figuring out exactly
why it is needed and what Linux can do about it."

Hope I can give you more infos soon... ;-)

---

### Post by tensop on 2008-01-24
I believe it has something to do with an improperly implemented ACPI system - the Laptop is always reporting the incorrect CPU temperature - it may be that acer are getting around this issue by switching it on at timed intervals or using another temperature diode on the bus.

---

### Post by emerald2dragon on 2008-01-27
Hey, i think i found a way to fix it :) ...or at least it works for me

heres how i did it:

go into terminal (or whatever you use) and type:

su root  <-- it didnt seem to work with the sudo stuff, it kept saying your not root blah blah blah and thats the only way it didnt complain about it

cd /proc/acpi/thermal_zone   <-- This will get you into the right folder.

gedit cooling_mode  <-- make sure that its this file your editing.

and then add this into it when it opens up in a text editor:

cooling mode: active


save the file, then restart the computer.

before i did all this, my computer would become unbelievably hot, and shut down right when im trying to install software :mad: but now its still warm, but nowhere near as hot as it was before, and its been on for about 2 hours since i did that and it hasnt shut down, so thats good so far.


i hope this helps people :)

---

### Post by zado717 on 2008-01-27
cd /proc/acpi/thermal_zone 
[COLOR="Red"]The colling_mode file is by me in /proc/acpi/thermal_zone/TZ01[/COLOR]

gedit cooling_mode 
cooling mode: active
save the file, then restart the computer.

When I use the file /proc/acpi/thermal_zone/TZ01/cooling_mode I cant save it because I become a error Message: wrong parameters. What can I do?

Sorry for my bad english.

---

### Post by emerald2dragon on 2008-01-28
oh, sorry, my mistake. to change the contents of the file successfully i had to log in as root, via the login screen. no matter what i did in my normal account it didnt want to let me change it no matter how much i gave it the administrator password.

AND, on a more depressing note, it turns out changing that file didnt fix my fan :( it worked for quite a few hours and the beginning of the next day, but then it started overheating and shut down again.

from what i can gather from other forums and posts, it seems that the fan doesnt work after you bring it out of hibernation or suspend. therefore i reccomend shutting it down (unlike me, where i was too lazy to do it the long way and just shut my laptop lid and put it into hiber :) )

well today im going to go down to the shop and try to get one of those fan stands for the laptop, and im hoping that this will compensate for the internal fan. that seems to be the only thing that might work, short of buying a sh*t load more ram so that vista doesn't lag like theres no tomorrow.

---

### Post by tensop on 2008-01-29
starting to sound like the only real solution is to solder in a temperature controlled circuit for the fan :(

---

### Post by osmoTR on 2008-02-01
new bios avabilable v1.25

from bios readme

[Fixed History]
BIOS:
  1). Update new solution for Penryn CPU.(Processor May Unexpectedly Assert False THERMTRIP# After
      Receiving a Warm Reset)

i think this bios solve cpu fan problem

i didn't test yet


:guitar:

---

### Post by zado717 on 2008-02-01
Work the fan with the bios update?

---

### Post by zado717 on 2008-02-01
The biso flash fix not the problem.

---

### Post by csim on 2008-02-10
hi,

i figured out there are various types of 5315 avaliable, mine is 5315-050508Mi, BIOS version 1.25, OS Ubuntu Gutsy 7.10, 2.6.22 kernel that came with the installation.
there also seems to be a 5315-2153, and perhaps other models. 
therefore it would be good if everyone here would precisely state his model and operating systems he's running.

[SIZE="4"]**Please state your 5315-model, BIOS version and your operating system(version, 32/64 bit, kernel version) on which you're experiencing the shutdown/overheating problem[/SIZE]**

[SIZE="4"]64-bit version:[/SIZE]
I was experiencing the shutdown/overheating problem. The computer would suddenly switch off, and the bottom was very hot. 
Version 1.25 of BIOS did not solve the problem.
Also, the temperature indication was stuck at the temperature it got first, and did not show anything else, which indicates that it didn't work at all, not even after installing lm-sensors, and modprobing the correct module corresponding to 82801-H/ICH8 chipset(i2c-i801 module). Lm-sensors didn;t detect any sensor at all.

[SIZE="4"]32-bit version:[/SIZE]
So i decided to reinstall, and it seems to work now, i haven't experienced a shutdown since.
However, suspend doesn't work, after suspending the computer doesn't seem to wake up.
The temperature is between 45 and 55 degrees, but i suspect there might be something wrong as it's showing the temperature in +5 degrees steps. The lm-sensors modules don't seem to affect that, they don't seem to be used at all.


[SIZE="4"]**BIOS**[/SIZE]

**For those who want to flash BIOS and don't have windows installed**, i have flashed the bios using  DOS bootable  USB key with FreeDOS installed. A couple of resources, please read them carefully before you proceed.
[http://gentoo-wiki.com/HOWTO_Create_a_DOS_boot_USB_flash_drive](http://gentoo-wiki.com/HOWTO_Create_a_DOS_boot_USB_flash_drive)
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)
[ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios](ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios)

[SIZE="4"]**ACPI**[/SIZE]

I noticed the following message during boot:
```

ACPI: Looking for DSDT ... not found! 

```

So i went on installing **IASL** and looking at what's wrong with the DSDT, when i compiled the resulting dsdt.dsl file,  it gave me 9 errors and 23 warnings.
[http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)
I found out that by replacing all _T_0 with T_0, _T_1 with T_1 and _T_2 with T_2 would fix the errors and it did! Now i only had 23 warnings, i was only able to fix 2, since i wasn't sure about the other ones.


This yields the following warning:
```

dsdt.dsl   860:             Method (_OSC, 5, NotSerialized)
Warning  1075 -                        ^ Reserved method has too many arguments (_OSC requires 4)

dsdt.dsl   876:                             And (CAPB, 0xFFFFFFFC)
Warning  1104 -                                     ^ Result is not used, operator has no effect

```

After looking up the ACPI specification, i found out that the OSC stands for Operating System Capabilities and takes 4 arguments:
```

          Arg0 (Buffer):    Universal Unique Identifier (16 Byte Buffer) used by the platform in conjunction with Revision ID to ascertain the format of the Capabilities buffer.
          Arg1 (Integer):   The revision of the Capabilities Buffer format. The revision level is specific to the UUID.
          Arg2 (Integer):   Count - Number of DWORDs in the Capabilities Buffer in Arg3
          Arg3 (Buffer):    Capabilities Buffer containing the number of DWORDs indicated by Count. 

```

Also, the And operator has the following syntax:
```

Syntax
   And (Source1, Source2, Result) => Integer

```

So i went on fixing it:


```

Method (_OSC, 5, NotSerialized)      /* take only 4 arguments */
            {
                Store (Arg3, Local0)         
                /* Is Arg2, which is the Number of DWORDs in the Capabilities Buffer */ 
                Multiply (Local0, 0x04, Local1)
                /* Local1 = Count * sizeof(DWORD) */ 
                Name (BUF1, Buffer (Local1) {})
                /* Create BUF1 with the size of Count * sizeof(DWORD) */
                Store (Arg4, BUF1)
                /* Store the Capabilities buffer in Arg3 into BUF1, hence this should be Arg3 */
                Store (Zero, Local1)
                Store (Zero, Local2)
                While (Local0)
                {
                    Multiply (Local1, 0x04, Local2)
                    /* Local2 is the pointer in BUF1 - current_count*sizeof(DWORD) */
                    /* Local1 gets increased until Local0 = 0 */ 
                    CreateDWordField (BUF1, Local2, CAPB)
                    /* CAPB holds the value of BUF1 pointed to by Local2 */
                    If (Arg2)
                    {
                        If (LEqual (Local1, Zero))
                        {
                            And (CAPB, 0xFFFFFFFC)
                            /* assume that the value in CAPB needs to be && with 0xFFFFFFFC */
                            /* we store it in CAPB, which should be equal to BUF1[Local2] */
                            /* And(CAPB, 0xFFFFFFFC, CAPB) */
                        }
                    }
                    Else
                    {
                    }

                    Increment (Local1)
                    Decrement (Local0)
                }

                Return (BUF1)
                /* Return the altered Capabilities Buffer */
            }

```

Here's the hopefully fixed code:

```

Method (_OSC, 4, NotSerialized)
            {
                Store (Arg2, Local0)
                Multiply (Local0, 0x04, Local1)
                Name (BUF1, Buffer (Local1) {})
                Store (Arg3, BUF1)
                Store (0x00, Local1)
                Store (0x00, Local2)
                While (Local0)
                {
                    Multiply (Local1, 0x04, Local2)
                    CreateDWordField (BUF1, Local2, CAPB)
                    If (Arg1)
                    {
                        If (LEqual (Local1, 0x00))
                        {
                            And (CAPB, 0xFFFFFFFC, CAPB)
                        }
                    }
                    Else
                    {
                    }

                    Increment (Local1)
                    Decrement (Local0)
                }

                Return (BUF1)
            }

```

What it probably does is just altering the first DWORD value of the Capabilities Buffer by applying  AND 0xFFFFFFFC to it.

All other warnings were related to the fact the the function did not always return value where it should be returning one(pseudocode):

```


return_value function()
{
   if(condition)
   { 
      do something;
      return resulting value;
   }
/* --> it should also return a value here */
}

```

Most people solved it by just returning 0 or a "package(){}", an array  of 0s. However in most cases the DSDT function might be returning some other value.

I compiled the DSDT.dsl file and went on inserting it into initrd:
```

sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
sudo dpkg-reconfigure linux-image-$(uname -r)

```

After that i still get the msg, no matter whether 32 or 64 bit version of Ubuntu:
```

APIC error on CPU0: 40(40) 

```

[SIZE="4"]**Temporary conclusion**[/SIZE]

I suspect it might be buggy ACPI, here are some places we should be checking:

[http://bugzilla.kernel.org/show_bug.cgi?id=9754](http://bugzilla.kernel.org/show_bug.cgi?id=9754)

We probably need to fix the DSDT file, i have read somewhere that there are Intel engineers hanging out on the Linux-ACPI mailing lists which helped to solve some issues with DSDT.
I have read that ACER does provide support for their Linux based machines, so they might be able to give some information and advice on the matter. Did anyone ask if they provide support for Linux, since they are selling Linux based machines?
The AcerACPI guys might be able to help since this doesn't seem to be a 5315 specific acer problem. 

[http://acpi.sourceforge.net/](http://acpi.sourceforge.net/)
[http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

Also it would be definitely helpful if the Lm-Sensors guys would be able to fix the issue with detecting the sensors in ICH8 and controlling them

[http://www.lm-sensors.org/](http://www.lm-sensors.org/)

I found an implementation for ASUS notebooks which controls the fan RPM. The links seem to be broken, but i have the file stored locally somewhere in case someone's interested.
"The main idea is to export the entire ACPI to sysfs. For this we can use acpi_sysfs the author of which is Alex Williamson. The original patch was meant for 2.5.x,so it's not easy to patch. If everything works out fine, you should end up with module acpi_sysfs, which you should load with parameters "dangerous and nonstd". This will make all ACPI objects available for userspace processes. It is therefore possible to work with objects as files /sys/firmware/acpi. Communication protocol can be found here [http://lkml.org/lkml/2004/9/21/120](http://lkml.org/lkml/2004/9/21/120) and is different for 32bit and 64bit systems. For controlling the RPM you should use: /sys/firmware/acpi/namespace/ACPI/_SB/PCI0/SBRG/EC0/WMFN 
7th bit for automatic mode (default) 4 other bits (6th - 3rd bit) for manual mode, increasing RPM (0x0 - 0xf)."

Also, an interesting discussion which claims you should switch of sleep/hibernate and you should be fine, and also, quoting:"I talked to Acer Tech Support about it. They basically said they do not support XP on this model, only Linux and Vista"  
[http://soulpass.com/2007/11/10/installing-windows-xp-professional-sp2-on-acer-aspire-5315-2153-laptop/](http://soulpass.com/2007/11/10/installing-windows-xp-professional-sp2-on-acer-aspire-5315-2153-laptop/)


That's it for now, hope it helps! :)

---

### Post by kikke on 2008-02-21
You submitted this to Launchpad?
I tried the hibernation on Hardy alpha with latest updates and it's freeze because overheating.

---

### Post by shawnmos on 2008-03-11
Hi all, Acer has released another Bios update, 1.29a. [Here is the link.]("ftp://ftp.work.acer-euro.com/notebook/aspire_5315/vista/Bios")

> BIOS:
  1). Update Tj85 cpu fan-table for Thermal request.
  2). Fix Pci Express LAN card can't used.
  3). When run camera AP, camera image will lag.
  4). update Chipset code.
  5). Support engineer sample Merom CPU CPUID:06FB
  6). Update Micro code CPUID: 6FD version ID: A3.
  7). Update Panel ID Table.

EC:  
  1). Update new Thermal Control Table.
  2). Add Linux Flag for brightness hotkey with no SCI under linux OS.
  3). Add new panel list follow 
      15" = "ICL50 BrightnessContorlTableV1.2"
      17" = "Acer_17inch_BrightnessControlTableV1.1"
  4). Add work around for S4 RTC wake issue.

It looks like the problem has been fixed. No overheating yet, but I haven't throughly tested it yet. Can anyone else confirm?

---

### Post by kikke on 2008-03-11
There is a v1.31 too,
File: v1.31.zip  	2231 KB  	2008.03.11.  	12:55:00


BIOS:
(1.31)
  1). Improve BOBO sound when play music. (?)
  
(1.30)
  1). Implement SATA LPM workaround.
  2). Update MRC V1.04.
  3). Support new nVidia VGA. (NB8P-SE, NB9P-GE1, NB9M-GE1, NB9M-GS, NB9P-GE2, NB9M-GE)

EC:
  1). None.

---

### Post by kameleon25 on 2008-03-11
I would love to try it but cannot get to the acer server. Connection keeps resetting. Anyone care to send me the BIOS and I can host it on my server for those that have issues with acer?

---

### Post by shawnmos on 2008-03-11
Guess it's not fixed. My laptop just shut off. I am using Vista and the ePower managament software too. Even with their software sometimes it works from resume and sometimes it doesn't. Really frustrating. I hope they get this fixed soon. I doubt the constant overheating is good for the processor or the motherboard for that matter.

I haven't been able to access their ftp to download the new bios. Maybe their server is getting flooded?

---

### Post by kikke on 2008-03-11
[http://rapidshare.com/files/98801209/v1.31.zip.html](http://rapidshare.com/files/98801209/v1.31.zip.html)

---

### Post by Marski69 on 2008-03-11
Hello Acer fans,

I'm using:
[LIST]
[*]eFramework_v2.5.4006_Vista
[*]ePowerManager_v2.5.4014_Vista
[*]with BIOS V1.31
[/LIST]
On:
[LIST]
[*]Vista Ultimate.
[/LIST]

NO crash for few hours.:popcorn:

Without ePowerManager & eFramework its No Go....!:confused:

I hope ACER is doing something about it.
After speaking with helpdesk (dutch)i'll lost all hope because,
the  guy didn't even know there was a problem with the:
[LIST]
[*]Acer 5315 and
[*]Powermanagment.:lolflag: ->not really:(
[/LIST]

So lets all pray that after 8 bios updates maybe the 9th will fix
the POWERMANAGMENT issue so that we all can use are hardware
Bill Gates intended PLUG an PRAY?

Stupid Empowering Sj!t from ACER:mad:

---

### Post by kikke on 2008-03-12
I'm using it with XP without any empowering stuff. Hibernation works well. Never crashed.

---

### Post by Marski69 on 2008-03-12
Dear Kikke,

Some background information
[LIST]
[*]S0 - the run state. In this state, the machine is fully running. 
[*]S1 - the suspend state. In this state, the CPU will uspend activity  but  retain its contexts. 
[*]S2 - sleep states. In these states, memory contexts are held but CPU contexts are lost. The differences between S2 and S3 are in CPU re-initialization done by firmware and device re-initialization. 
[*]S3 - (see S2)
[*]S4 - a sleep state in which contexts are saved to disk. The context will be restored upon the return to S0. This is identical to soft-off for hardware. This state can be implemented by either OS or firmware. 
[*]S5 - the soft-off state. All activity will stop and all contexts are lost. 
[/LIST]

So if i don't use the S2 & S3 states (sleepstates) then the problem isn't there.
It isn't depending on the operating system u using its just the sleepmodes in
combination with FAN control that makes him CRASH!
Acer uses a special set of dll's (framework) en a Widget (Empowering manager) to make it work.
Sounds like BAD PROGRAMMING to me ACER...:lolflag:

I hate to use ACER widgets because it looks like sj!t on my Vista desktop (i can't minimize it or whatever):(
I hate to use ACER wigets because the use my MEMORY!:(
I hate to use ACER wigets because the NEED a special FRAMEWORK:confused: (Set of DLL's):(

I'll love to use Vista because i can close my laptop whenever i want...
And go on whenever i like....
It works great
Its just a shame for the ACER widget on my desktop thats all!:guitar:

---

### Post by kikke on 2008-03-12
But I can hibernate with XP, without any problem. I don't need any framework for this.

Under Ubuntu, the temperature doesn't updated correctly after resuming from hibernate or suspend. After hibernate it's seems to 40 C degree, after suspend it's seems to 50 C. 
Maybe it's a shame of acer's linux support, and shame of the acpi team.
I like this acer modell because it's cheap, it works well with xp. The Ubuntu and the Vista is too overbloated and unstable for real work.

---

### Post by shawnmos on 2008-03-13
I am having problems with this thing overheating even with the empowering software in Vista. Not sure why. I don't think I had this problem before.

I resumed from suspend and noticed that my fan wasn't spinning. It started getting really hot and I knew it would crash soon so I opened up Sisoft Sandra and pulled the CPU information to see what the temperature was. It was 79C. What's weird is as soon as I did that the fan kicked on and has been working since. The temperature is now 51C. It's almost as though the laptop had no idea how hot it was until Sandra requested the temperature.

---

### Post by jimmyridge on 2008-03-14
was the battery dead?

---

### Post by kikke on 2008-03-14
> **jimmyridge said:**
> was the battery dead?

Why? :shock:

---

### Post by shawnmos on 2008-03-14
> **jimmyridge said:**
> was the battery dead?

No, fully charged.

---

### Post by zado717 on 2008-03-18
Bios version 1.31 fix not the problem. I thing that acer never will fix the problem they want that we must use Vista and not any other operating system:mad:

---

### Post by pp77 on 2008-03-20
New bios 1.32 released (without a readme). Don't know if it will fry our laptops.

[ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios/]("ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios/")

---

### Post by Darkchef on 2008-03-20
hmmmm i have the acer aspire 5050 laptop, never had this problem, although ive always had the epower management widget installed with vista. i know this might sound stupid but could it be possible to emulate the widget in wine at all ?

UPDATE : The Acer Aspire 5050 has the exact same problem, i booted ubuntu on a live boot and the fan didnt even kick in once WITHOUT using suspend or hibernate. Im sure this could be argued against acer that this is a health and safety issue with the risk of fire and damage to property. I sure wont be buying a new acer laptop in the near future. And emulating the widget in wine is a stupid and dumb idea, it was late at night lol.

---

### Post by kastel on 2008-03-22
Hello,
I'm using an Acer Aspire 5315-101G08Mi (BIOS version 1.23), with an Intel
Celeron 540 (32 bits) and have experienced the same problems: the fan does not
start when resumed from hibernation, leading to overheat.

After trying some random solutions, I found that adding "noapic nolapic
acpi_osi=!Linux" to the kernel parameters solves the problem completely, with
no keyboard/mouse problems. Moreover, there aren't APIC errors anymore.

This is surely not the ultimate solution, but I hope this will be useful for you.

---

### Post by zado717 on 2008-03-23
> **kastel said:**
>  I found that adding "noapic nolapic
acpi_osi=!Linux" to the kernel parameters solves the problem completely,


Stupid question but how can I add 
```
noapic nolapic acpi_osi=!Linux
```
to the kernel parameters?

---

### Post by kastel on 2008-03-23
Before changing the parameters in the configuration file, you may want to test them. To do so, when the GRUB menu appears, select the line with Ubuntu, press 'e', down, 'e' again and you can edit the kernel parameters once.

If that works, type "gksudo gedit /boot/grub/menu.lst" in a shell, or, if you use kubuntu, type "kdesu kwrite /boot/grub/menu.lst".
Then append the parameters to the first uncommented (that is, without leading #'s) line beginning with "kernel", and to the line beginning with "# defoptions" as well.
Reboot the system and the new parameters will be applied.

---

### Post by kikke on 2008-03-29
sudo update-grub is required, I think so.
But...
Doesn't work with Hardy beta.

---

### Post by kastel on 2008-03-30
There is no need to run update-grub. Instead, you may cancel your customizations.
As regards me, I tested disabling local APIC (see previous posts) on Gutsy only.

---

### Post by zado717 on 2008-03-30
I have not test the ACPI fix yet but there is a new BIOS 1.33 
:lolflag:

---

### Post by kastel on 2008-03-30
> **zado717 said:**
> I have not test the ACPI fix yet but there is a new BIOS 1.33 



Interesting... Hope it'll work!
Version 1.32 did not fix it

---

### Post by mirage on 2008-03-31
Hi All,

 i have an acer aspire 5715z, and i tried these:
* bios upgrade (->1.33)
* kernel parameter setting

but this actually solved this problem:
[http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg14582.html](http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg14582.html)
(or here: [http://bugzilla.kernel.org/show_bug.cgi?id=9167](http://bugzilla.kernel.org/show_bug.cgi?id=9167))

I think it can do the job for many other acer models.

>  ------- Comment  #69 From David Edwards  2008-03-19 02:59:49  [reply] -------

Created an attachment (id=15344) [details]
([http://bugzilla.kernel.org/attachment.cgi?id=15344&action=view]("http://bugzilla.kernel.org/attachment.cgi?id=15344&action=view"))
Archive containing Acer 5720 Fan Control Script + Binary Patcher 

This is the fix I sent to Davis Cabral. It is an archive containing a script
and binary for controlling the CPU fan on an Acer 5720 or similar under a 64
bit Linux. Apologies in advance if this is considered an abuse of the Kernel
Bug Tracker.

To use it:
-    Unpack with tar xjf acer5720_fan_64.tar.bz2
-    Adjust tunable parameters in acer5720_fancontrol.sh to your taste.

Copy mempat and acer5720_fancontrol.sh somewhere convenient, bearing in mind
that acer5720_fancontrol.sh needs to find mempat in its PATH.

Arrange for acer5720_fancontrol.sh to be executed at start-up, eg. (as on my
Ubuntu) kicking it off in the background from /etc/rc.local.

Hope this helps, no liability accepted for bringing about the end of the world
etc. etc.



---

### Post by kameleon25 on 2008-04-01
I will definatley have to check this out when I get home. Sounds promising. I have recently switched to this laptop as my primary computer and am about to be upgrading the cpu, ram, hd, and optical. If only I can get it to do properly with the cooling fan I will be set. I will post my results.

---

### Post by kameleon25 on 2008-04-01
On second thought... I am using the 32-bit version. Wonder if thsi wil lmake a difference or if there is 64-bit specific stuff in there. Any ideas?

---

### Post by kikke on 2008-04-03
> **mirage said:**
> Hi All,

 i have an acer aspire 5715z, and i tried these:
* bios upgrade (->1.33)
* kernel parameter setting

but this actually solved this problem:
[http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg14582.html](http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg14582.html)
(or here: [http://bugzilla.kernel.org/show_bug.cgi?id=9167](http://bugzilla.kernel.org/show_bug.cgi?id=9167))

I think it can do the job for many other acer models.

Please read the topic title: Acer Aspire **5315** Shuts Down!!!
It's not 5715z or anything with dual core and 64 bit.

But this is the right way. I'll try contact the patch's author.
Thank you!

---

### Post by Bookman on 2008-04-03
Right I know this is not the model number in the topic title but I do have the dual core 64 bit 5715z as mentioned in the bug tracker....BUT

> Arrange for acer5720_fancontrol.sh to be executed at start-up, eg. (as on my
Ubuntu) kicking it off in the background from /etc/rc.local.

Means absolutely nothing to me!

Can anyone take the time to post what this means and show how to do it.

Thanks in advance

---

### Post by kikke on 2008-04-04
I wrote a mail to Mr. David Edwards for help me out with an 32bit version of his patch.
He send me the compiled patch with good helping attitude, so the best is if I share this with you:

---
[FONT=Courier New][SIZE=2] Dear Kikke
[/SIZE][/FONT] [FONT=Courier New][SIZE=2]
> I have an Acer Aspire 5315 with same overheat problems as with 5720, but it's only have an Pentium processor (32bit).
> The 64bit mempat will works in Linux 32bit?
> Where can I download the mempat's source or 32bit binary?
>
[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]The 64 bit mempat won't work. Use the attached. You don't say you have programming skills, so I have compiled it.

You will certainly need to change the patch address. To find it, you will need to proceed as follows.

Decompile the DSDT using iasl.

Establish that the _TMP method code is essentially the same as it is on the 5720.

            Method (_TMP, 0, Serialized)
            {
                If (ECON)
                {
                    If (DTSE)
                    {
                        Store (DTS2, Local1)
                        If (LGreaterEqual (DTS1, DTS2))
                        {
                            Store (DTS1, Local1)
                        }

                        Store (Local1, \_SB.PCI0.LPC.EC0.SKTA)
                        Return (Add (0x0AAC, Multiply (Local1, 0x0A)))
                    }
                }

                Return (0x0BB8)
            }
        }

Find the address of the of the NVST. It will look something like the following.

    OperationRegion (NVST, SystemMemory, 0x7F6BCE88, 0x00000062)
    Field (NVST, AnyAcc, Lock, Preserve)
    {
        SMIF,   8,
        PRM0,   8,
        PRM1,   8,
        BRTL,   8,
        IGDS,   8,
        TLST,   8,
        CADL,   8,
        PADL,   8,
        CSTE,   16,
        NSTE,   16,
        SSTE,   16,
        LCDA,   16,
        LIDS,   8,
        PWRS,   8,
        BVAL,   32,
        CMPF,   8,
        CSTF,   8,
        GTF0,   56,
        GTF2,   56,
        IDEM,   8,
        DTS1,   8,
        DTS2,   8,
        DTSF,   8,
        PPMF,   32,
        TSTE,   8,
        KBTP,   8,
        MIRT,   8,
        OTHR,   8,
        DI00,   320
    }

To compute the correct address, you need to work out the offset of DTS1 and DTS2 from the start of the NVST. The field lengths are in bits, not bytes, so divide by 8.

Use mempat to check you have the correct address, using

mempat -l 2 your_hexadecimal_guess /dev/mem> guess.dat

od -x guess.dat

DTS1 and DTS2 will be reversed.

The higher value should match the temperature in /proc/acpi/thermal_zone/TZ01, when converted from the hexadecimal.

Good luck

David Edwards[/SIZE][/FONT]

---

### Post by Bookman on 2008-04-05
Can anyone help with this:

> Copy mempat and acer5720_fancontrol.sh somewhere convenient, bearing in mind
that acer5720_fancontrol.sh needs to find mempat in its PATH.

What does it mean the PATH, I can figure out where they are meant to go

Thanks in advance

EDIT

After a great response From David Edwards my fan now runs perfectly. For those that want to know here is how:
> 
Start a terminal session.

Become root. Depending on your distribution, the syntax would be:

su

and provide your root password when prompted

or

sudo bash

and provide your own password.

Unpack the archive.

tar xjf acer5720_fan_64.tar.bz2

Copy the files to a suitable directory.

cp acer5720_fancontrol.sh mempat /usr/bin

Edit /etc/rc.local to insert the fan control command. The following sequence should put it in towards the end before the exit.

ex /etc/rc.local << EOF
$-3 << EOF
i << EOF
acer5720_fancontrol.sh & << EOF 
.<< EOF
w << EOF
q<<EOF

Reboot and the fans should work properly. I also noticed the the Gnome panel Temp sensor which had been reading either 0 degress or 40 degrees and not moving now works!

Many thanks to David for his assistance. Long live the Wildebeest!

---

### Post by kikke on 2008-04-06
> **Bookman said:**
> Can anyone help with this:



What does it mean the PATH, I can figure out where they are meant to go

Thanks in advance


[http://tldp.org/HOWTO/Path-4.html](http://tldp.org/HOWTO/Path-4.html)
I think so /bin is a safe place for it.

---

### Post by harvester on 2008-04-07
I have an acer laptop, its a 5720z, but I have the same issue...

Ubuntu ran on this laptop fine with no problems ever.  Gentoo is giving me a hard time with the shutting down, I never bothered looking at the temprature but I am pretty sure its the exact same issue you guys are having.  adding acpi=off and noapic does stop this problem on my laptop.

At first I only had noapic  and I thaught it fixed it, but it started crashing today, untill I added acpi=off.. Maybe it was the other way around, ive been wrestling this issue for a while now.


Anyway... If you add both, I think it will fix your issues.

---

### Post by Bookman on 2008-04-08
If you read my edited post on page 10 the solution is there!

---

### Post by harvester on 2008-04-10
Sorry!  after testing and testing, it doesnt matter what boot options i pass.. if the computer starts hot the fan stays on.. if it starts cold it stays off .

I have tried that script, but its not working! Am I missing kernel options ? is my acer5720z different enough for that script to not work ?

I would really apreciate some help.

I tried manually running commands in the script to turn that fan on or off but i couldnt get it to do anything... Im not very good at this so I may not be doing things right.

---

### Post by Malekish on 2008-04-10
It's working!

I'm using 64-bit version so I was able to use the original mempat and acer file mentioned from the bug-tracker and my fan control is working again.

Try the fan control thing instead of passing the command during bootup, that might work for you.

---

### Post by Bookman on 2008-04-11
> **harvester said:**
> Sorry!  after testing and testing, it doesnt matter what boot options i pass.. if the computer starts hot the fan stays on.. if it starts cold it stays off .

I have tried that script, but its not working! Am I missing kernel options ? is my acer5720z different enough for that script to not work ?

I would really apreciate some help.

I tried manually running commands in the script to turn that fan on or off but i couldnt get it to do anything... Im not very good at this so I may not be doing things right.

When you add the CPU temp gnome applet to the tray does it give and reading at all? Also if you right click and select preferences there should choices of where to collect the info from.

---

### Post by pp77 on 2008-04-12
New bios again (1.34) [ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios/]("ftp://ftp.support.acer-euro.com/notebook/aspire_5315/vista/Bios/"). I'm getting suspicious of these constant updates, they really don't fix anything, and Linux support is getting worse (tried the latest 8.04 beta, and it's getting worse). This bios version supposedly enables the  "execute disable bit".

---

### Post by kikke on 2008-04-12
ex /etc/rc.local << EOF
$-3 << EOF
i << EOF
acer_fancontrol & << EOF 
.<< EOF
w << EOF
q<<EOF


I use **5315** with **512 MB** of RAM.
If you have other amount of RAM, change the offset in the acer_fancontrol script.

The attached mempat is 32bit only!

The script and binary is created by David Edwards.

Copy the attached mempat and acer_fancontrol files to /usr/bin and chmod it to 755, and owner to root:root.
Place the quoted lines to /etc/rc.local, before the exit 0 line.

Its turn on the cooler after resuming from hibernated or suspended state but doesn't turn it off. So the real temperature values remains unknown.

[COLOR="Silver"]Anybody knows about how to read out correct values? In windows the i8kfan control works well, and shows integer values, the current Linux ACPI shows only 45-50-55-66 C degree. Something is wrong with it.
[/COLOR] (solved)

--
edit:
Everything works for me. I changed the on/off temp values in the script and removed the comment from /etc/rc.local because it's causes errors.

After hibernating and resuming the script turn on/off the cooling fan.

If you want to show the CORRECT temperature values, write "coretemp" to /etc/modules and install computertemp and lm-sensors:
sudo apt-get install lm-sensors computertemp

Or you can use isparkes's conky (see upcoming posts)

---

### Post by isparkes on 2008-04-13
Sorry guys that I got onto this thread so late - I had the some problem on a 5720z. I spent quite a bit of time chasing it down. It really sounds like the same thing as on my laptop.

I know that things have probably moved on since I looked at it back in Feb, but I just wanted to give a positive identification to the problem to try and cut down on people speculating that the bios or *their particular* hardware was at fault. (One guy was talking about sending it back to Acer under warantee). The low down ion what I found out is this:

After a **RESUME** from HIBERNATE or SUSPEND the hardware does not re-initialize properly, and the fan control does not work. The CPU overheats and goes into thermal shudown. This is a problem with the hardware, and is a documented kernel issue. (I don't have the reference to the thread any more, but if anyone really needs it I can dig it out). On Windows, Acer provides a driver to re-initialise the hardware after a resume.

My workaround: I don't suspend or hibernate. I always reboot. It costs very little extra time if you are resuming from hibernate and have 2GB RAM.

I'll try this script and report back, I'm hoping that this will do the trick.

---

### Post by isparkes on 2008-04-15
Just a very quick update. It certainly seems to work fine on my 5720Z. Much kudos to DE...

---

### Post by isparkes on 2008-04-16
Just a little extra thing: I used conky to monitor the temperature of the cores. It's also pretty cool. I have set it up to run on the right side of the desktop. There are a couple of issues running it at launch with compiz, so I have added a script that launches conky after 2 minutes, which means it works fine even with compiz.

You need to have the sensors package installed, and of course conky:

sudo apt-get install lm-sensors
sudo apt-get install conky

To use the .conkyrc file, just put it in your home directory and launch conky.

Edit: when you first use this, you might find that the CPU temp does not show up. In this case it is likely that you have to initialise the sensors (it has to gather the information of what it can monitor). In this case, run the command:

sudo sensors-detect

And follow the on-screen prompts. At the end of the procedure, it will ask if you want to add the module to the file /etc/modules. Say "yes" to this.

---

### Post by kikke on 2008-04-17
An interesting package for correct cooling:
sudo apt-get lm-sensors computertemp

The computertemp installs gnome panel applet for showing actual temperature, not only from ACPI thermal zone thermal zones, but kernel i2c sensors / hwmon0, which is better because it shows integer values, the ACPI TZ01 shows only with 5 steps between values.

Don't forget to load the coretemp module (/etc/modules).

It works for me.

I updated the archive with my temperature values and corrected sample of /etc/rc.local, you can download it in #108 post ([http://ubuntuforums.org/showpost.php?p=4702613&postcount=108](http://ubuntuforums.org/showpost.php?p=4702613&postcount=108))
Thanks for help, everybody! :)
Thanks David Edwards! :)

---

### Post by gcastell on 2008-04-26
OK, I just upgraded to Hardy and I started having this problem with my acer 5315-2153, Kikke thanks for your post, that seems to have fix the problem but I have a question, it seems that the fan is always on after suspend or hibernate, is this the correct behavior?

---

### Post by hunfalu on 2008-05-03
Hello!
I bought a new aspire 5315 for my daughter. I'm very sad, because I have the same problem: the note book shuts down. I read all letters in this forum, from the beginning. My note book do this:
It shuts down, but I can restart only if I plug out the AC power. It starts immidiatley. If I do not plug out the AC power, I have to wait about 5 minutes. I use XP SP2. 
I'm not a computer guru, I'm only a sad fother...
Can anybody help me, exactly what to do to solve this problem? 
I don't want to use any other OS, - I'm not in love with Bill Gates, but all the family knows this OS, it should be very very difficult to learn for example a Linux OS.
Thank you very much!!
Gyuri

---

### Post by kikke on 2008-05-03
> **gcastell said:**
> ...it seems that the fan is always on after suspend or hibernate, is this the correct behavior?

No but I can't resolve this problem. Something wrong happened everytime the system returned from suspended/hibernated state. Maybe a frozen kernelmodule generate load and heating the CPU. If you change the temperature values in the script, you'll hear the switching, but over 55-60 C degree, so it's not so correct like a freshly rebooted state.
I'll try to figure out which module(s) turns things wrong after hibernation..

---

### Post by lemoutonvert on 2008-05-06
Hello everyone,

All of this is giving me a hard time, as it's a bit more than I can understand. Newbie ever, newbie forever :)

I have a 5315 as well, and my cooling is a ON/OFF device at the moment.

I got the script from bugzilla (Post #99) and the 32b binary from here. Dropped them in the /usr/bin directory.

But I didn't understand the *ex* code. I guess vim (it's vim, ain't it?) is not for kids...:)

What's /etc/local.rc supposed to look like after editing? 
I wish I could *gksu gedit* it... cause at the moment mine is just an empty file (heavily commented and *exit 0*, that's it).

Hope you forgive my english,

See you,

LMV

---

### Post by isparkes on 2008-05-10
Just to recap for newcomers to this thread - there still seems to be some confusion:
 - It is nothing to do with BIOS updates
 - It is fundamentally an Acer hardware problem/flaky design issue
 - On Windows it does not appear to happen, because there is a pre-installed driver that does the same thing as the script I'll mention in a minute
 - The shut down is due to a thermal protection in the processor
 - The fan control on the Acer is generally a bit flaky, but does not work at all after a resume from hibernation or suspend

OK; that said:   

Lemoutonvert:

OK, there are some things you need to do to get this going. Please bear with me.

1) Install the script that controls the fan

Download the script in the attachment in the post: [http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg14582.html](http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg14582.html)

I have also attached it below.

2) Unpack the script

tar xvfz acer_fancontrol.tar.gz

3) IMPORTANT Modify the script to match your hardware (It is set up for a 2GB 5720Z as it is).

gedit acer_fancontrol

Pick the memory size which matches your memory size

4) Try it out

sudo ./acer_fancontrol

If you used the slightly modified script attached to this post, you should see that it prints some messages out like "Ignition Off", "Clutch down" or something. These correspond to the fan speeds, and you should be able to hear the fan working for anything above "Ignition Off".

5) If it works you can install the script

sudo cp acer_fancontrol /usr/bin
sudo cp mempat /usr/bin

6) Make it run automatically

sudo gedit /etc/rc.local

Insert "acer_fancontrol" before the final "exit 0"

After this, it will look like:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

acer_fancontrol

exit 0
```


That should be it. After you reboot, the problem should be gone forever.

---

### Post by Prompt24 on 2008-05-10
Hello 
I have faced the same problem. 

**[COLOR="Red"]I have installed new BIOS v1.34 I run my notebook under XP SP2.[/COLOR]** 
I have tried to send my notebook to standby note  many times.A fun started to cool CPU everytime I woke it up.

 I played games use the net and at least five programms (CPU was charged 100% and temp was no more than 60'C). Then I sent my notebook in standby mode and after a long period of time a woke it up and immediately started to play game and use the progs and charge my notebook but [COLOR="red"]temp was still no more than 60'C[/COLOR]What I want to say that  I think  that perhaps I solved this problem with a help of the lates version of BIOS from official site.

I will test it for some time and if I meet that problem again I will send another post here otherwise it works for me.

all the best!  I hope not to visit this topic anymore.

Sorry for my english I hope you understand my post.

P.S. People it work perfectly. It was a problem with BIOS. The latest version can solve the problem. I think everyone should try this first! it is the easiest way to start to solve this problem. Then you can try other ways. 
In service they say that my notebook is not able to run under OS XP but it works just perfectly.
Good luck!

---

### Post by chipdrive on 2008-05-12
Okay, I have read through nearly every post and it seems that the only solution was to Ubuntu. I have tried Linux in the past, and just compatibility issues that were too time consuming for me at the time to deal with.

I have an Acer Aspire 5315-2153.
I contacted Acer about the problem, but they said all they could do was have me send it in for repairs. I called back and had them send me a fan, which I thought was the problem at the time. Obviously, I was wrong when I replaced the fan, and the same problem occurred.

I noticed today without reading up on anything that my fan worked fine after a fresh shutdown and startup, operating at various intervals to maintain a cool temperature. I let the computer sleep and I logged back in to find that the fan no longer turned back on after sleeping. Then I found this forum.

My problem is that it is running Vista and the only apparent solution was for ubuntu. I was wondering if anyone has found a viable solution for Windows Vista OS(I believe 32bit). I just find the shut offs to be quite annoying and time consuming, considering whatever I was working on was lost since the last auto or manual save.

If anyone has found a solution or is working on one, please either message me or reply to this post. Thanks for any help you can offer.

Edit: The only thing I found so far was this program called I8kfanGUI. It was made for Dell by a third party, but has some functionality with Acer. It allows you to manually run the fans in your laptop so as to keep it around a max of 50 degrees Celcius. So far so good. I have put the computer to sleep, and when I got back on, the program/fan worked wonderfully well. I actually can use my laptop without worry of shut off now. Hope this helps, but if anyone finds a Bios or software solution I am still open for it. But for now, this is working quite well. Thanks again.

---

### Post by kikke on 2008-05-13
FYI: [http://ubuntuforums.org/showpost.php?p=4933853&postcount=154](http://ubuntuforums.org/showpost.php?p=4933853&postcount=154)

---

### Post by kikke on 2008-05-13
1. Download the scripts from here: [http://kikke.hu/linux/acer_fan_x86_1.2.tgz](http://kikke.hu/linux/acer_fan_x86_1.2.tgz) 

2. Extract it: sudo tar -C / -xzvf acer_fan_x86_1.2.tgz
 
3. Add the coretemp module to /etc/modules for loading at system startup.

4. Modify the PATCH_ADDRESS value in /usr/bin/acer_fancontrol for your needs. The default value is for 512MB models.

5.  Add the acer_fan service to default runlevels:
 sudo update-rc.d acer_fan defaults

6. Edit the /etc/default/acpi-support, add the acer_fan to STOP_SERVICES.
 
 "gedit /etc/default/acpi-support"
 
Replace
 STOP_SERVICES=""
to 
 STOP_SERVICES="acer_fan"
 
7. start the service:
 sudo /etc/init.d/acer_fan start
 
8. Try out the service with "sudo /etc/init.d/acer_fan start"
 
In the /usr/bin/acer_fancontrol there is a new command, at the end of file:

echo 4 > /proc/acpi/acer/brightness
This change the brightness to medium. Comment it out if you don't want this.

---

### Post by OldAlgis on 2008-05-28
> **kikke said:**
> 
1. Download the scripts from here: [http://kikke.hu/linux/acer_fan_x86_1.2.tgz](http://kikke.hu/linux/acer_fan_x86_1.2.tgz) 


But is that not the same as given by isparkes in #117?  His download address is closer. Had a quick look at the script and what a fine piece of detective and programming work it is!  I am puzzled by the reference to the duo section.  It looks as if it is meant for a much superior pc than my Acer Aspire with 512 MB RAM.

I am confused by what seems like two parallel suggestions: one by you and the other by isparkes in #117.  I am inclined to follow the suggestions of #117, though it probably is a case of "all roads lead to Rome".

I am a very old man (over 83!) and need a guru to lead me, but please do not be offended if I choose the author of #117 post.

A Big Thank you, to both of you and all other posters in this thread.  Though I mostly use SUSE, I learned a lot from this ubuntu thread.  

BTW, I do feel rather foolish having purchased a brand new el-cheapo ACER!

---

### Post by OldAlgis on 2008-05-28
> **isparkes said:**
> Just to recap for newcomers to this thread - there still seems to be some confusion:
 - It is nothing to do with BIOS updates


First of all, a big THANK YOU for the very useful information on this puzzling problem. IMHO Acer should have fixed that up in the BIOS. It would be more useful to start the fan at full speed on power on and then let the software take a better control of it.  Currently it seems that by default at the power on the fan is off. I regret having bought that nice looking and inexpensive  Aspire 5315. It turns out to be - well, cheap...

Are we really sure that the BIOS upgrades have not solved the problem? There has been a reply, claiming that BIOS upgrade 1.34 has actually solved the overheat problem.

Thank you again and "thank you" to kikke for detailed outline how to install the fan controlling script.  

Actually, I prefer to run openSUSE10.3 on the laptop for historical reasons and would very much like to have suggestions how to solve this heat problem on a suse Linux OS. It should be very similar, but is it the same?

Kind regards and thank you for your good work!

---

### Post by emerald2dragon on 2008-05-31
Hey, this is great that someone finally found a way to fix this :)

...however im having some problems :(
Im using the solution in post #117

when i try to run the acer5720_fancontrol.sh (which is what i downloaded from the link provided) it came back with this:
[I]
FATAL: Error inserting coretemp (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/coretemp.ko): No such device
You must have module coretemp to monitor the CPU temperature[/I]

i just looked at that and drew a mental blank :P i know a **bit** about linux, but not a whole lot about all that shizz.

so any help would be greatly appreciated ^_^


... that, and what am i supposed to edit in the shell? i have an aspire 5315 with 512mb of ram, but i cant see the bit i am meant to change :S

---

### Post by OldAlgis on 2008-06-01
> **emerald2dragon said:**
> Hey, this is great that someone finally found a way to fix this :)

...however im having some problems :(
Im using the solution in post #117

Unfortunately for you and me, we came to this discussion rather late. I read most of the posts here and have been waiting for someone to respond.  As it is, I am responding to you...

You picked up an informative post (#117).  Another one well worth looking at is #121.

> 
when i try to run the acer5720_fancontrol.sh (which is what i downloaded from the link provided) it came back with this:
[I]
FATAL: Error inserting coretemp (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/coretemp.ko): No such device
You must have module coretemp to monitor the CPU temperature[/I]

Any module with the extension ".ko" is part of the kernel. What Linux distribution do you use? I use openSUSE10.3 and get exactly the same message.

The message simply says that the kernel module coretemp.ko is not installed in your computer.  I stayed shy of the kernel- it is for far more knowledgeable users than I. I have a couple of times compiled the kernel for suse, but I suspect that suse handles that somewhat differently to ubuntu.  Actually, I have a mind to change to ubuntu for Linux on my laptop.

Also, I should upgrade the BIOS on my laptop, laptop which I bought in OfficeWorks in Canberra. 

Also, the first task and test and at least an interim solution would be to start the fan by invoking the script manually. Speed could be anything reasonable.  It would not require to poll the tempearture and then decide what to do, so it should be much simpler than the more elaborate, more complex and, of course, a better script, given in the references of this list.  I hope we can get some interest and help for the simpler interim solution.  

In the meantime, tell everyone you can reach that Acer "designed" a laptop in which the fan is controlled not by BIOS, but by a program that runs only in Windows Vista...

Good luck,
OldAl.

---

### Post by kikke on 2008-06-01
> **OldAlgis said:**
> 
I am confused by what seems like two parallel suggestions: one by you and the other by isparkes in #117.  I am inclined to follow the suggestions of #117, though it probably is a case of "all roads lead to Rome".


The #117 post is based on David Edward's binaries and the script which shown here, first time published by me in the "Ubuntu 7.10 on a Acer Aspire 5315 Gemstone" topic. I don't mind about (getting) credits (by isparkes), but this kind of duplicating makes you confused.

My version is good for resolving hibernation/suspend issues via /etc/default/acpi-support STOP_SERVICES method, after I created simple initscript for controlling acer_fancontrol script at suspend(or hibernate)/resume. Better than nothing and it works for me.

I don't want to ASPIRE to honour ;) so Rome is David Edwards and there is a road: [http://bugzilla.kernel.org/show_bug.cgi?id=9167](http://bugzilla.kernel.org/show_bug.cgi?id=9167)
You will find there a 64bit binary attachment of mempat and David's e-mail address too. :)

I am happy to see you here as Linux user :)

---

### Post by emerald2dragon on 2008-06-02
ok, i got the right file that matches my laptop, but now i cant get the coretemp.ko thingy. Ive tried to compile it how another site told me (some ubuntu site i found off google) but it didnt work! i dont know whether to cry or punch the screen (nothing like this seems to like me :P )

annyyyyway my point is, anyone know an EASY way to get it? one that explains EXACTLY what to type into terminal? cuse when #117 said now load coretemps i was like ... O_o ????

^_^ 

thanks in advance if anyone bothers to reply to this

edit: from what i can gather my acer aspire 5315 reckons coretemp stuff aint supported O_o?

---

### Post by pwilli on 2008-06-02
I tried to install Linux some time ago on my "**ACER Aspire 5715z**" (Intel DualCore, 2GB Ram) and ran into the exact same problem of never updating temperatures and therefore shutdown after some minutes because of overheating. The temperature was only updated once at boot time and therefore the fan kept the same speed for the whole time.

Finally the problem seems to be fixed for me with **BIOS-Version 1.34**

I have a dual-boot setup of Windows Vista 32-bit (was preinstalled) and a fresh install of **Kubuntu 8.04 (KDE 3.5.9) 64-bit Version**. The temperature in proc/acpi/thermal_zone/TZ01/temperature now gets updated automatically (allthough still only in multiples of 5) and the fan acts accordingly to keep the system on ca. 60 degrees if under full load (i tested it using a distributed computing project that has CPU usage of ca 95% all the time) and about 45 degrees when idle.

Allthough everything seems to work now, the fan still doesn't show up in thermal zone and can't be controlled directly.

---

### Post by isparkes on 2008-06-02
Firstly, OldAlgis:

Kikke and I have just wrapped up a piece of (as you say) fine hacking work. I prefer the slightly more "steam driven" approach, whereas Kikke has made it more "natively" integrated with the Linux philosophy. I was happy just to have the problem solved, so for me, that was the pot of gold and I stopped there. No credit goes to me - I just come back onto this thread every now and again, because there seems to be so much confusion around the subject.

I'm also going to try the BIOS update to 1.34 and will report back whether Acer have finally solved this (for them, embarassing) problem.

---

### Post by kikke on 2008-06-05
> **isparkes said:**
> 
I was happy just to have the problem solved, so for me, that was the pot of gold and I stopped there.


I am happy with this laptop, and now we have a .deb here:

[http://kikke.hu/archive/pool/misc/a/acer-fan_1.4.deb](http://kikke.hu/archive/pool/misc/a/acer-fan_1.4.deb)

Use it, I hope you'll like it. :)

---

### Post by ontherooftop on 2008-06-06
Ok I bought this laptop (acer aspire 5315-2153) and it has been hell
but this might work for you , it worked for me. This laptop came installed
with the crappy vista operating system and made my laptop slow, so I got
rid of it with all those ridiculas partitions and installed xp and then
had to get drivers for xp, then I installed ubuntu 8.04 using wubi 
on xp and now I dual boot. Basically acer wants you to only use vista 
those assholes , even on the phone they say vista is the best, My laptop
kept on shutting down  every 10 mins with no fan running, but On xp , 
I think its best you u dual boot ubuntu with xp for this issue , because
using xp I went to acers website and got the latest bios flash V 1.34 
for vista ( but it worked on xp)  and then it rebooted after unziping and
installing it and when I booted ubuntu 5 seconds later the fan just kicked
in and has been working great without my laptop turning off , I think acer decided to fix this issue with the bios update because enough ubuntu people
are complaining and I doubt they want a bad rep with people saying linux
wont work on acer , also the wifi was not working and I had to buy a linux compatible adapter,  anyways  this is working for me so just update 
to bios v 1.34.

---

### Post by Petr Jakes on 2008-06-08
My configuration: Acer Aspire 5315, 1MB RAM, Ubuntu 8.04 Hardy Heron. After with shutdowns caused by overheating of processor (described earlier in this thread) I have upgraded to BIOS 1.34. Now everything is working OK (no more CPU shutdowns after suspend or hybernation).

Concerning WiFi I am using patched madwifi-nr-r3366+ar5007 driver which works without any problem. 

HTH

Petr

---

### Post by isparkes on 2008-06-12
I confirm that also for me BIOS 1.40 has solved the fan problem. I have a nice FreeDOS boot CD ISO image for anyone that might find this useful. It has been tested on an Acer 5720Z. This boots to DOS mode, and is license free.

It's too big to attach to the post, so I have put it here:

[http://www.openrate.de/Downloads/FlashBIOSV140.ISO.bz2](http://www.openrate.de/Downloads/FlashBIOSV140.ISO.bz2)

---

### Post by OldAlgis on 2008-06-15
> **isparkes said:**
> I confirm that also for me BIOS 1.40 has solved the fan problem. I have a nice FreeDOS boot CD ISO image for anyone that might find this useful. It has been tested on an Acer 5720Z. This boots to DOS mode, and is license free.
It's too big to attach to the post, so I have put it here:
[http://www.openrate.de/Downloads/FlashBIOSV140.ISO.bz2](http://www.openrate.de/Downloads/FlashBIOSV140.ISO.bz2)
You have done a great job in wrapping it into an iso package. For me, actually, it is quite important, because through the "blackouts" of overheating CPU my ms Vista Home Basic does not boot anymore. I had the backup DVD disks made by carefully following "Acer" instructions.  So I was able to re-install the part1 (partition 1) and part2 (partition 2) - no problems.  Actually, I don't think there is anything wrong with part2, just the mbr, as it fails to boot looking for "BOOTMGR".  I am looking into it without much enthusiasm as I no longer care about Vista - ubuntu 8.04 (32 bit) seems to do a very good job, anyway. 

For BIOS flashing I will need a windows-like OS and did not think of Free DOS. That is "isparkes" brilliant idea that allows the likes of me to do flashing without having to restore Vista OS!

I have downloaded your *.iso and had a good look at it.  What puzzles me is that the BIOS patch v 1.40 on your *.iso differs from the BIOS patch v 1.40 that I had downloaded some time ago.  It seems very much like Acer teams are continuing to work on the patch without changing its version number, something that would not happen in the Linux community (different version without changing version ref.) It is only my guess, however. 

"isparkes", would you be so kind and let us know the url from which you downloaded the patch, please.  Actually, it would be nice to "talk" to you direct by email. Would you email me direct (akabaila[at]pcug[dot]org[dot]au), please? It would be greatly appreciated. Of course, it would also be useful if the url was posted here on the list, too. 

Thank you for your continued interest in and work on this subject - it is greatly appreciated.  With a bit of luck, I might be able to add a few words on this list about restoration of the "factory defaults" on this laptop. Would this be of interest to somebody?

All the best from wintery Canberra - I think Canberra is one of the coldest inhabited places on this dry, dry, very dry continent...  Actually, Canberra is surrounded by the mighty Snowy Mountains that reputedly have more snow than all of the Austrian Alps. :-)

---

### Post by isparkes on 2008-06-16
I got the BIOS by using the pull-down in the "BIOS and Guides" section on the page.

[http://support.acer-euro.com/drivers/notebook/as_5720.html](http://support.acer-euro.com/drivers/notebook/as_5720.html)

However, it's really easy to update the "payload" (the BIOS updater in this case) if you want to be sure that it's not tainted or been fiddled with, or just need to have one that is suitable for your PC.

You'll need an ISO file editor (I used the "ISO Master" package from Add/Remove Applications), with which you can open the ISO image, and replace the files that appear in the lower part of the window (screenshot). You can then save and burn the updated ISO image, knowing that it has something reliable and useful on it. The boot files themselves do not show up in the lower part of the ISO Master app, only the payload files.

The only thing to remember is to unzip the DOS version of the BIOS updater so that you'll have access to something you can run from the tiny FreeDOS system. The first time I did it, I had a Zip file on the CD, and no way of opening it in FreeDOS. Doh! Obviously the windows updater won't work, either.

What makes the updater different? Honestly I don't know. It could be that the BIOS for the 5315 is slightly different from the 5720 one that I used. It could be that there is some slight regional difference between Europe and Oceana, or it could be that they are still fiddling with it.

I have sent you a mail, please feel free to ping me if you need anything.

---

### Post by underarmour2012 on 2008-06-26
i installed that Dell CPU Controller Software and now with sleep or hibernate mode ( on vista home premium) i got no problems.  the fan turns on at 60 deg C.:):):):):)

---

### Post by Mirakov on 2008-07-11
I also had spontaneous shutdown issues with my Acer Aspire 5110. I tried every trick imaginable. I opened up the laptop as far as I could, tried different memory chips, did a repair installation of windows etc. I also checked that the fan was clean and blew the loose dust away from it.

Since the problem seemed to occur mostly when I'd had the computer on for a while and when it happened, it usually happened soon again. So I was quite sure it was a heat issue. The fan, however, was working fine and at times it blew like hell. After not even being able to turn the computer on anymore, I even put it in the fridge for a little while and after that it worked fine for almost an hour. So that confirmed my suspicion about it being a heat issue.

Finally, I opened up the fan (Sunon) and **I noticed that a big chunk of dust was clogging the other air flow grill and the other one partially**. So I guess the fan tried to cool down the system as hard as it could, but since the exits were completely stuffed, the system overheated quicker all the time. The dust wasn't visible from the surface of the fan or from the outside of the computer, which is why I didn't suspect it at first.

After the cleaning I installed Speedfan and the temperature has been under 50C all the time. I also haven't had a single unwanted shutdown after that.

And btw. I registered just to post this message and to say that if anyone has heat issues or shutdowns, open up and clean the fan before you do anything else. Thanks also for the hint someone posted about dust! :)

---

### Post by kazobon on 2008-07-16
heat problem still here - acer aspire 5315 , intel celeron 530 (1,73 GHz, 533 MHz FSB, 1 MB L2 cache) 2 GB DDR2
BIOS 1.34 does not slove this mashine's terrible CPU drama!
though 1.34 seems to be the best one, couse i've already tried to fix the issue with 1.40 and even the latest 1.42. 
nothing! 
there is something in the 1.34 that makes fans kick in more properly, but still not good enough to sink temp under 60-65 degrees. 
i also tried to deal with ePower menager, prevent from hybernation and all.. though nothing changes. 

sometimes fan kicks in, sometimes not. usual CPU temp is between 60   and 70 degrees. when it starts to get higher i usualy reboot or shut down the machine

speedfan does not detect the fans. i've tried to use some similar programmes, but nothing seems to work against this hellish heat. 
as a matter of fact, almost cooling prog reconises the stupid motherboard on this nasty wite aspire beauty! it's called "acadia" or something like that i guess.. 

the .iso procedure you're talkin about, you think it can help sink the temp? :confused:

by the way, .iso link is not available 
oh, yes. i don't think dust c&#1072;uses heat problem in my case, couse the machine is brand new. have it for less than 6 months 

will appreciate any advise! 
i suppose it's obvious i have nothing to do with software or hardware professionaly :lolflag:

---

### Post by kioftes on 2008-07-17
Hi all! Great job done first of all...Now, i have an acer aspire 9302 and after hardy installation fan stopped working properly. I tried the fix but i am unable to load coretemp

kioftes@Soula:~/Documents/acer_fancontrol$ sudo modprobe coretemp
FATAL: Error inserting coretemp (/lib/modules/2.6.24-19-rt/kernel/drivers/hwmon/coretemp.ko): No such device

any ideas...?

P.S. coretemp.ko exists in the specified directory...

---

