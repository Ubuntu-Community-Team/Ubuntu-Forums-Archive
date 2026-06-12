---
title: "Help Please. P4 CPU Running hot."
date: 2008-10-03
forum: Hardware
---

### Post by skynux on 2008-10-03
Hi there. I have been working on putting together a dual-boot XP/Ubuntu box. This is my first build as far as assembling a complete computer from components.

 I had a Dell Dimension 2400 with a bad MoBo, and decided to fix it up and play with a Linux distro. I Replaced the Mobo with a Foxconn 661MXPlus. I added a Pentium 4  Prescott 3.2GHZ CPU, which came with a pretty decent heatsink and fan. I was having problems with the video driver (on the windows side), and rather than spend a bunch of time F'ing with it, I bought an NVIDIA GeForce FX5500 video card. Of course the crappy 200 watt Dell power supply that was in the computer wasn't going to work very well with all this, so I got an Antec 550 watt power supply. So here's the problem:

After installing the new power supply and video card, I booted into BIOS and looked at the temp, and realized that it was running at 60 C while idling. I thought maybe I had just done a bad job with the thermal grease, so I pulled off the heatsink, reapplied some arctic silver, and put it back together. It was running slightly cooler (54 C), but not where it should be. I then tried replacing the heatsink and fan again, this time with the generic junk that came with the MoBo. This only made it louder, and hotter.(It went up to 63 C within minutes). Satisfied that its not a problem with the fan, I reinstalled the Intel fan and heatsink again. I tried removing the video card and re-checked it, but it made no difference. What could cause the CPU to get so hot with no load on it? The MoBo is brand new, and I got the CPU on eBay. It seems to be running okay, other than the high temp. 

One thing that I'm a little unsure about, is that the MoBo says it supports FSB 800(overclock)/533/400. The P4 has a 800MHz FSB. I don't really understand about overclocking. Do I need to change any settings to make this CPU work better with the MoBo? could this have anything to do with why my CPU is running at 55 C ? I had heard that these CPUs would just shut off before they burned up. Is this true? Should I just keep it running and see what happens, or is this an issue that I should resolve before I actually use this computer?

Lots of questions, I know. Any help would be much appreciated. I want to get this box running well in windows before I start playing around with Ubuntu. (insert sarcastic comment about Windoze here) Thanks!

---

### Post by SteelWo1f on 2008-10-03
Those temperatures don't sound unreasonable to me. Especially for a 3.2Ghz. These chips usually get pretty hot even when their idling. Read the CPU you got with your manual but I'm pretty sure your are still well under critical temperatures.

I do have one suggestion though. It sounds like you are still using your Dell case. This is probably going to be... well, not the greatest for heat. Before you buy a crazy new $300 antec liquid cooling solution, there is one very cheap solution to see if your case is doing its job. Go get the biggest fan in your house and put it next to your computer, take the side panel off your case, aim the fan inside, and viola! That 500mm beast should beat out your 80mm dell one.

---

### Post by skynux on 2008-10-03
Thanks. I haven't even put the side back on the case yet. Its been running open so I can troubleshoot the problems, and i was thinking this would help keep it cool. Will I get better results with the side panel on? Will that provide better airflow or something?

I didn't get a manual with the CPU as it was used. You really don't think that is too hot for this CPU? I saw a lot of posts on various forums where people reported 30-40 as being normal for a similar CPU. Are the 3.2 Prescotts supposed to run that much hotter than the  Northwoods? Also, I am running it with 2GB of RAM, if that makes any difference.

---

### Post by SteelWo1f on 2008-10-03
Having the side panel on may help with the front to back airflow, but not with the vertical air flow which is what you want for the CPU. Some cases come with a hole in the side panel right about where the CPU is so that the air can escape above the fan on the CPU.

I think that 54 should be fine.

Here is a post that might help
[http://www.techspot.com/vb/topic13759.html](http://www.techspot.com/vb/topic13759.html)

And here is one where someone got basically the same processor down to 40, but he had to use liquid cooling to achieve this.
[http://www.techspot.com/vb/topic19365.html](http://www.techspot.com/vb/topic19365.html)

---

### Post by skynux on 2008-10-03
Yikes. Putting the side on the case did NOT help. The temp quickly climbed into the mid 60s and the fan started making a very loud unusual noise.

---

### Post by SteelWo1f on 2008-10-03
Hmm. Is the CPU fan ok? It should never make any strange noises. It may be that you need a new CPU fan.

---

### Post by skynux on 2008-10-03
It seems to be, now that I pulled the side panel off again. It was rev'ed up really high because of the temp increase, but after removing the panel, it went to lower RPMs and the noise stopped.
As I said before, I tried a different HS and Fan, and the temp actually went UP, so i don't think the fan is causing the overheating problem. Thanks for the link BTW. That is the forum that I was reading about other folks operating temps.

---

### Post by VMC on 2008-10-03
Apparently the Prescott is normally hot. Compared to the Northwood core. Look at this comparison:
[http://www.digit-life.com/articles2/p4-throttling/index.html](http://www.digit-life.com/articles2/p4-throttling/index.html)

---

### Post by SteelWo1f on 2008-10-03
I found that too. Here is an excerpt of one I found:

Upon release, many reviewers mistakenly concluded that the Prescott generated approximately 40% more heat clock-for-clock than the Northwood, and almost every review of it was negative, earning it the sobriquet PresHot. In reality, the core temperature sensor of the Prescott gives higher readings than the Northwood core temperature sensor, meaning that the increase in heat generated for CPU work done is believed to be around the 10% range

---

### Post by skynux on 2008-10-03
Very interesting article. Though, they were getting those high temps with NO FAN connected, and the CPU running at 100%. I guess I can run ok at these temps (seems to at 62 now, after trying to close the side panel), but I was wanting to possibly use this box as media server and have it on all the time, but I'm a little more wary with it running so hot.

---

### Post by skynux on 2008-10-03
I may try and get a Northwood instead. I might be willing to sacrifice half of my cache to keep it running cooler and not have the fan going so high all the time.

So, anyone have any insight on the FSB query that I posed in my OP? Could this be why its running hot, or is there likely no connection?

---

### Post by rmjohnson144 on 2008-10-03
I'd suggest checking your CPU temps in Windows.  I use HWMonitor or coretemp to check the temps myself.  I tend to not worry a lot of the temperature as usually the CPU chip has an auto shutoff feature that will prevent harm, but excessive heat can wear a CPU down over time and shorten its life.  I prefer HWMonitor as it keeps track of both high and low temps over time.  Just download Prime95 to stress test your CPU.  Run it for at least 1hr as it takes a while for your CPU to hit max. temps.

HWMonitor
[http://www.cpuid.com/hwmonitor.php](http://www.cpuid.com/hwmonitor.php)

Prime95
[http://www.mersenne.org/freesoft.htm](http://www.mersenne.org/freesoft.htm)

You may want to invest in a quiet fan if it's too loud.  I usually get heatsink/fan combos.  If you decide to get both, make sure you get an all copper heatsink as they cool best.  also, you may want to get a higher flow fan for the rear of the computer case to help with getting cool air into your case.  Just remeber that the fan will pull more air into your case which means more dust and you may have to clean inside more often.  I usually get canned air as it is safest.

Also, make sure you have good thermal paste applied to the heatsink so it will help keep it cooler.  I use Arctic Silver 5, but any will work just fine.  Remember, it doesn't take much.  usually 2-3 tiny dots about the size of a grain of rice will work.

Also, go to FoxConn's website and install the latest BIOS file as they can help on temps and readings.  The BIOS temp readings are most often the most inaccurate readings of them all.

If you have any question about how to accomplish these tasks let me know and I can walk you through.

-=Mark=-

---

### Post by skynux on 2008-10-05
RMJ,

Thanks. I installed HWmonitor, but I'm a little unsure which temp reading its giving me is actually the CPU. If its the one I think, its showing that its running still a bit hotter than it should be, but better than the readings in BIOS. I have the latest BIOS installed. I'm a little confused as to how a third party app would be giving a more accurate reading than the BIOS? 

I think the fan and heatsink combo that I have should be sufficient. Its an intel with a copper core HS, and the fan seems pretty quiet, at least when the thing isn't having a meltdown. I also used Arctic Silver 5, and applied it very carefully (3 times in fact!), so I am confident that is not my problem.

I am wondering if there are some settings in the BIOS that I can adjust that might help. As  I stated in my OP, the MoBo is spec'd to run at "FSB 800(overclock)/533/400MHz". The CPU is a Prescott 3.2Ghz with a 800MHz FSB. I don't really understand "overclocking" as regards the FSB. Is there something I have to do to get it to run properly? I have enabled "overclocking" in BIOS. But I did not see anyplace to change other settings, such as voltage, or the frequency(?). Tho, the voltage that its running at is within the range spec'd for this CPU.

Anyway, I found some Northwood 3.2 Ghz CPUs for a decent price, and from what I've been reading, I might get better performance out of them due to the cooler running temps. I just need to know if getting another 800MHz FSB CPU will actually do any good, or am I going to have the same problem?

If anyone can point me in the right direction with this issue, I'd really appreciate it. Thx!

---

### Post by skynux on 2008-10-05
I have also found some P4 2.8GHz CPUs that are 533Mhz FSB with a 512 cache. Anyone have any advice on which way to go with this? 

I am not going to game on this box. I just want the best performance I can get while still keeping the temp reasonable enough to not need a bunch of fans or a fancy cooling system. I would like the temp to be somewhere between 30-40 C at idle. The most I would like to do with this box is run P-Shop and rip some DVDs in windows, use it as a media server and get familiar with the basics of Ubuntu.

---

### Post by rmjohnson144 on 2008-10-06
> **skynux said:**
> RMJ,

Thanks. I installed HWmonitor, but I'm a little unsure which temp reading its giving me is actually the CPU. If its the one I think, its showing that its running still a bit hotter than it should be, but better than the readings in BIOS.


What was the temperature readings?  Also, post the load reading with Prime95 running to get a better idea of the temperatures.

>  I have the latest BIOS installed. I'm a little confused as to how a third party app would be giving a more accurate reading than the BIOS?

BIOS usually don't have the most acurate readings since it is a minor issue compared to getting all the other motherboard settings configured properly.

> I think the fan and heatsink combo that I have should be sufficient. Its an intel with a copper core HS, and the fan seems pretty quiet, at least when the thing isn't having a meltdown. I also used Arctic Silver 5, and applied it very carefully (3 times in fact!), so I am confident that is not my problem.

A solid copper high quality heatsink will lower temp 10c-25c over stock.  Stock ones are very low quality in comparison.

as for problem, I'm not sure this is actually a problem but more of an issue.  Unless of course you actually need lower temps for a specific reason.  These Prescotts all run hot.

> I am wondering if there are some settings in the BIOS that I can adjust that might help. As  I stated in my OP, the MoBo is spec'd to run at "FSB 800(overclock)/533/400MHz". The CPU is a Prescott 3.2Ghz with a 800MHz FSB. I don't really understand "overclocking" as regards the FSB. Is there something I have to do to get it to run properly?

The BIOS seems to be setting things up properly. It seems to be running properly as you haven't report any real problems with the system.

> I have enabled "overclocking" in BIOS. But I did not see anyplace to change other settings, such as voltage, or the frequency(?). Tho, the voltage that its running at is within the range spec'd for this CPU.

I looked at the online manual from FoxConn and it shows a "Frequency/Voltage Control", but it doesn't show what's inside the menu.  A couple of things you can try if you get in there is first lowering the stepping rate from 16 to 15.  It will slow your chip from 3.2GHz to 3.0GHz.  I know the older Foxconn boards have very few options for overclocking so I'm not even sure that will be possible.

> Anyway, I found some Northwood 3.2 Ghz CPUs for a decent price, and from what I've been reading, I might get better performance out of them due to the cooler running temps. I just need to know if getting another 800MHz FSB CPU will actually do any good, or am I going to have the same problem?

Actually, they should run exactly the same but a lot cooler.  There may be a slight speed increase (unnoticable) from a more efficient chip design.

> **skynux said:**
> I have also found some P4 2.8GHz CPUs that are 533Mhz FSB with a 512 cache. Anyone have any advice on which way to go with this? 

This would run cooler, but slower.  I'd personally go with what you have if you can live with a little heat.  Just run some more tests and make sure it is with the side panel on as it will be hotter this way and you'll get a better idea of the temps you'll be facing.

> I am not going to game on this box. I just want the best performance I can get while still keeping the temp reasonable enough to not need a bunch of fans or a fancy cooling system. I would like the temp to be somewhere between 30-40 C at idle. The most I would like to do with this box is run P-Shop and rip some DVDs in windows, use it as a media server and get familiar with the basics of Ubuntu.

The Prescott definately won't run that cool without at least a really good cooler and more airflow through that case.  but if you can get by with a little more heat then the prescott will work.  they are tough and can tolerate the heat.

Maybe try a few more test to find out what you want vs what you need.
-=Mark=-

---

### Post by skynux on 2008-10-10
Here's an update:

I bought a P4 Northwood 3.06 GHz 512k cache 533Mhz FSB. I got it on eBay for $26. I installed it, and ran HWMonitor with Prime95 running, for an hour. The temp started out at 35C, and climbed up into the low 50s in about 15 minutes. I put the side of the case on, and the temp went up to 55C and stabilized. The fan however, went from 2300 to 3500 rpm at which point it started to make a loud noise. This was the same noise that I heard before when I put the side of the case on. I guess the fan just can't handle the RPMs. The temp was stable though. I took the side back off, and the noise almost immediately stopped, and the temp started dropping, leveling out at about 46C. Prime95 was only pushing the CPU usage up to about 52%, so I opened up photoshop, and moved some really big images around to keep the CPU usage right around 100% for the next half hour. The temp was still hanging at 46. After the hour was up, I quit Prime95, and 20 minutes later the CPU temp has stabilized at 36C at idle. This is more than acceptable for what I need. I will get a different fan that won't freak out under load, and either add a case fan, or just splurge and get a nicer case.

Anyway, thanks a lot for the help on this Mark. I am going to put in this baby's 500GB hard drive that I bought, and load up Ubuntu for real this weekend.:grin:

---

### Post by rmjohnson144 on 2008-10-10
Yeah, if I remember right that 3.06 has hyperthreading that makes the cpu act as a dual core so you can run two programs at the same time and not lose much speed (20% if I remember).  If it passes with 1 prime95 running then I doubt you'll ever put as much stress as that program does on your cpu.

If you keep that case just make sure you get a good exhast fan to pull ait through the case.  I am coincidentally working on my uncles Dell 2400 and it is small.  anyway, you'd have to toss the curreent exhaust fan with the shroud on it, but since you have a fan on your cpu it shouldn't matter any more.  it looks like it takes a standard 80mm fan, just get the highest CFM and lowest db. I recommemd lower than 30db.  Under 20 db would be awesome, but usually they have low flow rates(cfm).  I like newegg.com for window shopping.  They have lots of different fans and reviews to see what others think about them.

[http://www.newegg.com/Store/SubCategory.aspx?SubCategory=573&name=Case-Fans](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=573&name=Case-Fans)

Also, most cpu fans are 92mm with some 80mm.

Have fun with your new toy
-=Mark=-

---

### Post by skynux on 2008-10-12
Well. I got Ubuntu installed, and got Compiz working. Also figured out how to configure a bunch of the effects, ie rain, cube, windows bursting into flames when I close them. 

Sweet! 

I know its silly, but I'm having fun. 

The effects seem a little slow and choppy. I guess 256MB of video memory isn't quite enough. Should have went for 512MB.

I also got VLC to play a DVD, which seemed like an amazing feet by the time I figured it out. Totem will play the DVD, but only in French! 

??

Connecting to the shared files on my MacMini was automatic, but the file transfer rate is extremely slow, considering I have both computers hooked up to a Gigabit ethernet Airport Extreme Base station. Anyone know if there's a way to speed up the transfer rate within the Ubuntu settings somewhere?

I also installed GOS Space, but it seemed a little buggy. I couldn't enable the proprietary drivers for my NVIDIA card for some reason. It said it was enabled, but when I tried to turn on the desktop effects, it would just say "desktop effects not enabled". I gave up and installed Hardy, and the same steps for enabling the 3d effects on my NVIDIA worked right away. 

Anyway, I'm having a blast, and I look forward to showing off Ubuntu, and GNU/Linux in general, to my curious friends.:)

---

### Post by rmjohnson144 on 2008-10-13
Glad to hear it working for you.  

As for the video, I have the same issues.  I think it may be just immature drivers stills.

Not sure on the networking as I don't use it much.   But I did notice my eSATA drive was extrememly slow so maybe maore driver issues there as well.

It is very fun.  I instaled it on my uncles computer last week and I haven't heard from him yet so it must be working for him or he definitely would have called by now.

-=Mark=-

---

### Post by 4ebees on 2009-01-24
> **skynux said:**
> Well. I got Ubuntu installed, and got Compiz working. Also figured out how to configure a bunch of the effects, ie rain, cube, windows bursting into flames when I close them. 
<snip>
The effects seem a little slow and choppy. I guess 256MB of video memory isn't quite enough. Should have went for 512MB.


Hi there,
If the effects are slow and choppy I'd say it's more like your video card needs tweeking.

I have two PCs for my eldest children (a 1.6Gh P4 and a 2.0Ghz P4) each has an nVidia 128Mb card and neither machine has problems with the effects in compiz.

If this is still a problem, you might want to take a look at the settings for the card.

HTH

Regards,

4ebees.

PS ...I agree with you that the effects are fun :)

My kids love 'em and the rels and neighbours are surprised that machines which are home-built from scavenged-parts (the nVidia cards are the only parts I've bought!) can do so much and with such amazing style...for FREE!

Roll on Gnu/Linux!!

---

