---
title: "Laptop runs really hot"
date: 2010-04-14
forum: Hardware
---

### Post by D.horse on 2010-04-14
My laptop runs at 67.8 degrees C in an air conditioned apartment with nothing running other then the os.  When i start using it (playing videos / browsing) it shoots up to around 79 degrees C.  I noticed lately that the fan does not speed up with increased temperature lately.  Is there anything i can do to have it start doing this again?

Also it overheats and shuts itself off playing the simplest games (starcraft / diablo II) in wine.  Am i doing something wrong?  Can i scale back my CPU somehow or does Ubuntu just make these Laptops work harder then Windows? (battery life is 3.5 hours when reviews said i should get 6 +)

Ubuntu 9.10
Lenovo T400
Intel Duo 9600 CPU
4 gigs ram
Intel x-25 SSD 80 gb HD
Radeon 3400HD


Do you think it is hardware issue?  It is still under warrenty.

Please let me know if you need anymore information,  I mostly stumble around ubuntu so i may have disabled something somewhere, I just don't know where to look.

---

### Post by norseman-has-a-laptop on 2010-04-14
ok this worked for me 

its going to be really low tech but if your at home and you have a small fan put it behind your laptop and turn it on high lol

it works but its low tech but if you move around alot see if you can get a new cooling system for you laptop

---

### Post by iponeverything on 2010-04-14
If this is a new issue, try using compressed air to clean cpu heatsink and fan. Also run "top" in terminal when laptop is idle but running hot.  See if you problem process.

---

### Post by SnickerSnack on 2010-04-14
Aside from hardware issues, here's something you can try:

[QUOTE=synaptic]PowerTOP is a Linux tool that finds the software component(s) that
make your laptop use more power than necessary while it is idle. As of
Linux kernel version 2.6.21, the kernel no longer has a fixed 1000Hz
timer tick. This will (in theory) give a huge power savings because
the CPU stays in low power mode for longer periods of time during
system idle.

However... there are many things that can ruin the party, both inside
the kernel and in userspace. PowerTOP combines various sources of
information from the kernel into one convenient screen so that you can
see how well your system is doing, and which components are the
biggest problem.[/QUOTE]

This

[http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html](http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html)

may also be useful.  Go down to the section titled "Task: Find out who is monopolizing or eating the CPUs".

edit: Do you have Compiz on?  That could be a source of power usage.

---

### Post by rogerpittman on 2010-04-14
You might also want to try a laptop 'cooling pad' - I bought one last year (Targus model with 4 USB ports) and it works great - completely silent, too.

---

### Post by SnickerSnack on 2010-04-14
> **rogerpittman said:**
> You might also want to try a laptop 'cooling pad' - I bought one last year (Targus model with 4 USB ports) and it works great - completely silent, too.

Does it shorten battery life?

---

### Post by IcarusR on 2010-04-14
Get yourself an airduster aerosol &, as iponeverything says, blow air in the air intake (with laptop switched off) to blow any dust out of the air exhaust vent.

---

### Post by dave2001 on 2010-04-14
Unfortunately, it may not  be as simple as a bit of dust on your fan housing. Ubuntu seems to have developed some problems over the last several versions (especially karmic) concerning power and fan management.  Do some searches on the subject and you'll turn up a slew of people with the same issue. There doesn't seem to be an easy fix. Some people resolve it this way, others that way, and some never get it working well at all.  I have a Thinkpad T60 and A20 myself, and have found this very frustrating.  I hope the dev's are looking into the laptop situation for lucid lynx. I have seen precious little comment from them on any forums about this problem.

---

### Post by PRC09 on 2010-04-14
I also ran into this on my Acer laptop and when I updated to the latest bios the problem was resolved so maybe check for that.....

---

### Post by norseman-has-a-laptop on 2010-04-15
> **rogerpittman said:**
> You might also want to try a laptop 'cooling pad' - I bought one last year (Targus model with 4 USB ports) and it works great - completely silent, too. dude nice hey can yu buy those sepreate and install them by yourself 

also so link please i would like to check this out

---

### Post by D.horse on 2010-04-15
Fixed the issue..........sort of

I was not having any issues while i had the computer running off of battery but once i plugged it in my computer overheated within 10 minutes.  I poked around in Ubuntu and there was not really and way to change CPU or anything else based on being plugged in vs. battery that i could find so i checked in the BIOS.


in the bios there is a BIOS->config->power options
 
Adaptive Thermal management
Scheme for AC      [Maximize Performance]
Scheme for Battery [Balanced]  

I switched the Scheme for AC to [Balanced] and it runs nice and cool without any real changes in FPS.  Weird


Apparently running it under max performance doesn't work so hot in Ubuntu.

---

### Post by norseman-has-a-laptop on 2010-04-15
> **D.horse said:**
> 


Apparently running it under max performance doesn't work so hot in Ubuntu.

wow pun

---

### Post by D.horse on 2010-04-15
lol, wasn't even think about it.

---

### Post by Yellow Pasque on 2010-04-15
[http://www.thinkwiki.org/wiki/Save_power_with_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_ThinkPad_T400](http://www.thinkwiki.org/wiki/Save_power_with_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_ThinkPad_T400)

Also, you might want to update the BIOS. I see fan/cooling fixes listed in the changelog(s): [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-72858](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-72858)

---

### Post by norseman-has-a-laptop on 2010-04-15
> **D.horse said:**
> lol, wasn't even think about it.

lol its all good

---

### Post by D.horse on 2010-04-15
> **Temüjin said:**
> [http://www.thinkwiki.org/wiki/Save_power_with_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_ThinkPad_T400](http://www.thinkwiki.org/wiki/Save_power_with_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_ThinkPad_T400)

Also, you might want to update the BIOS. I see fan/cooling fixes listed in the changelog(s): [http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-72858](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-72858)

Thank you,

I checked Lenovo yesterday and the only bios update i found was from 5/29/2009.  I must not be looking in the right places.

---

### Post by norseman-has-a-laptop on 2010-04-15
i want to check out the cooling pad
i need one of those

---

### Post by D.horse on 2010-04-15
> **norseman-has-a-laptop said:**
> i want to check out the cooling pad
i need one of those

They have a bunch at amazon.  Wouldn't work for me since i have my laptop actually on my lap allot.  Don't need another piece to bulk it up

Link to Amazon results : [http://goo.gl/vDmL](http://goo.gl/vDmL)

---

### Post by norseman-has-a-laptop on 2010-04-15
> **D.horse said:**
> They have a bunch at amazon.  Wouldn't work for me since i have my laptop actually on my lap allot.  Don't need another piece to bulk it up

Link to Amazon results : [http://goo.gl/vDmL](http://goo.gl/vDmL)
ha i feelstupid lol um i thought it was some awesome mat that had like coolint in it but its just some fans lol

---

### Post by Grakul on 2010-04-15
I have the same problem on my HP Omnibook xe4500 (see [this thread]("http://ubuntuforums.org/showthread.php?t=1454427")). I actually can't test it running only on battery, as my battery doesn't hold any charge whatsoever (it's an old notebook, so not sure when, if ever, the battery worked).

I also see a BIOS upgrade on HP's site, but there's only a Windows installer. Does anyone know where I can find a Linux one?

Cheers
Graham

---

### Post by D.horse on 2010-04-15
There may be an .iso file somewhere on the site that you can use to update the bios. You would just need to look.

Can you check in your bios settings though to see if there is possible a thermal setting of some sort?  That is what solved my problem is switching it from performance to balanced

---

### Post by Grakul on 2010-04-16
I'll check again, but I don't think there's an iso file.

I did check my BIOS, but there are no power management settings whatsoever (a firmware upgrade will probably add those settings :P).

Thanks for the response!

I bought a cooling pad last night--should get it by the weekend. Hopefully that helps. :)

Cheers
Grakul

---

### Post by SnickerSnack on 2010-04-16
> **D.horse said:**
> I was not having any issues while i had the computer running off of battery but once i plugged it in my computer overheated within 10 minutes.  I poked around in Ubuntu and there was not really and way to change CPU or anything else based on being plugged in vs. battery that i could find so i checked in the BIOS.

My computer (thinkpad x61) also runs a little hotter when charging the battery, but that's just a matter of thermodynamics, especially since there may be no fans near the battery.  On mine, the battery runs along the whole back of the computer, so the main fan is near one end, so bat1 is usually a bit cooler than bat2 (thermal sensors).  x61 tablets have at least 24 thermal sensors (why so many?).

I've actually found that my battery last longer under linux (about 50% under gnome and 60% under xfce) than under windows vista, and it also runs cooler most of the time.

---

### Post by D.horse on 2010-04-16
> **SnickerSnack said:**
> My computer (thinkpad x61) also runs a little hotter when charging the battery, but that's just a matter of thermodynamics, especially since there may be no fans near the battery.  On mine, the battery runs along the whole back of the computer, so the main fan is near one end, so bat1 is usually a bit cooler than bat2 (thermal sensors).  x61 tablets have at least 24 thermal sensors (why so many?).


When my computer was overheating it was when i had it plugged in without a battery inserted.  This is the way i have my computer most of the time because having a fully charged battery inserted while the computer is plugged in significantly reduce the life of the battery (and the charge it can hold eventually)

---

### Post by malmomma on 2010-04-16
> **D.horse said:**
> When my computer was overheating it was when i had it plugged in without a battery inserted.  This is the way i have my computer most of the time because having a fully charged battery inserted while the computer is plugged in significantly reduce the life of the battery (and the charge it can hold eventually)

Huh?  It can reduce battery life??  I've had my Dell XPS M1530 for 2 years.  The battery, at this point, sucks.  With Windows, it only held on for 30 minutes to 45 minutes, depending on what I was doing.  After reading this thread, I'm curious how it would be with Linux.

And now to try checking out the BIOS setting...  Mine has been running hot since I installed Linux and I had just had the heat sync replaced a few months ago.

---

### Post by Yellow Pasque on 2010-04-16
> **D.horse said:**
> I checked Lenovo yesterday and the only bios update i found was from 5/29/2009.  I must not be looking in the right places.
So did you look at the links I posted and/or upgrade your BIOS?

---

### Post by D.horse on 2010-04-16
> **Temüjin said:**
> So did you look at the links I posted and/or upgrade your BIOS?

Yes i did check the links and i did install the update.  I did not however switch back the power settings on my computer.  I will switch them back to the settings they were at when i was experiencing the overheating issues when i get home.  I am also going to buy a can of compressed air (always good to have around)


Thank you for all the help man!

---

### Post by Grakul on 2010-04-16
> **Grakul said:**
> I'll check again, but I don't think there's an iso file.

I found a floppy image on [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=83757&swItem=ob-26177-1&prodNameId=83759&swEnvOID=1093&swLang=8&taskId=135&mode=5]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=83757&swItem=ob-26177-1&prodNameId=83759&swEnvOID=1093&swLang=8&taskId=135&mode=5"). Going to try and find a PC in this house with a floppy drive, and a floppy disk! Will let you guys know. :P

---

### Post by norseman-has-a-laptop on 2010-04-16
off topic

i am in class and i am really bored

---

### Post by dave2001 on 2010-04-16
Like several of you, I found an option in my bios which regulates the cpu while on A/C and battery. I changed the A/C setting from performance (Fixed Max), to balanced (Auto Medium). This made only a small amount of difference in heat, and slowed my computer significantly. So i put it back on performance.  This got me thinking however, and after looking at some posts regarding cpu scaling, I tried enabling powernowd in ubuntu, with appropriate options. It now seems to me, that not only is less heat generated, but the fan comes on more often, which is great. I have had major problems getting the fan on my thinkpad to run often enough. I'll see if I can get some more objective evidence verifying this. Thank for the posts everyone.

---

### Post by D.horse on 2010-04-16
> **dave2001 said:**
> Like several of you, I found an option in my bios which regulates the cpu while on A/C and battery. I changed the A/C setting from performance (Fixed Max), to balanced (Auto Medium). This made only a small amount of difference in heat, and slowed my computer significantly. So i put it back on performance.  This got me thinking however, and after looking at some posts regarding cpu scaling, I tried enabling powernowd in ubuntu, with appropriate options. It now seems to me, that not only is less heat generated, but the fan comes on more often, which is great. I have had major problems getting the fan on my thinkpad to run often enough. I'll see if I can get some more objective evidence verifying this. Thank for the posts everyone.


That is very interesting to me.  I will try running that as well to see if it makes any significant changes.  I didn't think i noticed any changes when switching to balanced cpu but i did notice that Southparkstudios video i watched last night was choppy in full screen with my new settings.  I will switch it back and see if there really is a difference or not.

---

### Post by SnickerSnack on 2010-04-16
> **malmomma said:**
> Huh?  It can reduce battery life??  I've had my Dell XPS M1530 for 2 years.  The battery, at this point, sucks.  With Windows, it only held on for 30 minutes to 45 minutes, depending on what I was doing.  After reading this thread, I'm curious how it would be with Linux.

Yes: [http://www.thinkwiki.org/wiki/Maintenance#Battery_treatment](http://www.thinkwiki.org/wiki/Maintenance#Battery_treatment)

My current battery is about 13 months old, and for the first 6 months or so, I followed those directions, but then I got lazy.

Under windows, the battery (8 cell) lasted between 6 and 8 hours depending on how I was using it.  Then after about 6 months of following the linked directions, it still lasted between 5 and 7 hours, which is pretty good.

Then I got lazy, and within a couple of months of leaving the full battery in while the ac was connected, it was down to 3 to 4 hours.  The battery life degraded much more in that 2 month period than in the previous 6 months.  It may be that that's simply the way batteries degrade, though.

At about the 12 months (total) point, it was down to about 2 to 2:30.  Now that I've switched to linux, it lasts about 2:30 to 3:30, depending on usage, and window manager (gnome+compiz takes more power than xfce).

Right now, under gnome-compiz, it says it's at 73% with 2:20 left.

---

### Post by shaka_zulu on 2010-04-16
I have XPS 1530 also with 9 cell battery. SInce i have it i was using both AC and battery because when you remove this big battery laptop can not stand normal... Really stupid from Dell but anyway. It is not some hidden info that Linux generally do not have that good battery manager like Windows. In the begin on Vista my battery lasted for about 4 hour and on Kubuntu it was about 3. After year and a half now it can lasts for only hour and half. Ubuntu says that my battery has 49.7% of original power...

---

### Post by malmomma on 2010-04-16
> **SnickerSnack said:**
> Yes: [http://www.thinkwiki.org/wiki/Maintenance#Battery_treatment](http://www.thinkwiki.org/wiki/Maintenance#Battery_treatment)

My current battery is about 13 months old, and for the first 6 months or so, I followed those directions, but then I got lazy.

Under windows, the battery (8 cell) lasted between 6 and 8 hours depending on how I was using it.  Then after about 6 months of following the linked directions, it still lasted between 5 and 7 hours, which is pretty good.

Then I got lazy, and within a couple of months of leaving the full battery in while the ac was connected, it was down to 3 to 4 hours.  The battery life degraded much more in that 2 month period than in the previous 6 months.  It may be that that's simply the way batteries degrade, though.

At about the 12 months (total) point, it was down to about 2 to 2:30.  Now that I've switched to linux, it lasts about 2:30 to 3:30, depending on usage, and window manager (gnome+compiz takes more power than xfce).

Right now, under gnome-compiz, it says it's at 73% with 2:20 left.

Thanks for the explanation.  Never knew that.  If I remember correctly, I believe Ubuntu told me that my battery only had about 40% of it's charge ability left.  Err, not sure if that's the appropriate terminology, but you get my drift.  I unplugged it to see what would happen just a few minutes ago.  Already down 5% from full charged.  Says I have 1 hour left, when initially I had 1 hour 5 minutes.  Time to save for a new one, eh?  :)

---

### Post by malmomma on 2010-04-16
Well, you learn something new every day.  Your link to the ThinkWiki made me google Dell battery health.  Turns out, there is a button with LED lights on the bottom of my laptop where the battery is.  Press & let go, and the lights (or lack of) indicate the amount charged.  Press & hold for 3 seconds or more and all 5 lights come on, then black out, and then depending on your battery's health, a light will come on.  If your battery has excellent health, no lights will come on.  If 5 lights come on, your battery has less than 60% charge capacity and is obviously not in good health.  Yeah.  All 5 lights came on for me...  Bugger.

---

### Post by SnickerSnack on 2010-04-17
> **shaka_zulu said:**
> 9 cell battery ..........4 hour and on Kubuntu it was about 3. After year and a half now it can lasts for only hour and half. Ubuntu says that my battery has 49.7% of original power...

That's some serious hardware to use up 9 cells in 3 to 4 hours.

> **SnickerSnack said:**
> Right now, under gnome-compiz, it says it's at 73% with 2:20 left.

By this I meant that it was at 73% of its current capacity, not 73% of its design capacity.

My battery's current capacity appears to be about 87% of its design capacity: it holds 57.9 watt-hours and was designed to hold 66.2.  That's not too bad for a year of constant use (this is my work *and* home computer).  But, it used to last more than 6 hours, now it's at about 3, and that's 87%? :confused:  I think that maybe this results from a sort of "over-filling" of the batteries initially so as to allow the manufacturer to report long charges times.  So, maybe they operate at 150% of their "design capacity" for the six months?

(Yes, I know that a battery cannot really be "over-filled", but what I mean is that they take the battery's actually capacity, and refer to ~70% of that as the "design capacity"?  Maybe?)

> **malmomma said:**
> Says I have 1 hour left, when initially I had 1 hour 5 minutes.  Time to save for a new one, eh?  :)

You could just have the cells replaced.  It should be considerably cheaper, but I don't know if it's the sort of thing where you take it in and it's done a couple of hours later, or if you have to mail it in.  BatteriesPlus replaces cells afaik.

---

### Post by Grakul on 2010-04-18
> **Grakul said:**
> I found a floppy image on [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=83757&swItem=ob-26177-1&prodNameId=83759&swEnvOID=1093&swLang=8&taskId=135&mode=5]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=83757&swItem=ob-26177-1&prodNameId=83759&swEnvOID=1093&swLang=8&taskId=135&mode=5"). Going to try and find a PC in this house with a floppy drive, and a floppy disk! Will let you guys know. :P

I did find a PC with a floppy drive (my wife's), and a floppy disk. I created the disk from the image, and stuck it in my laptop's floppy drive... but there's no option on my laptop to boot from floppy! :(

Anyway, I received my shiny new [laptop cooling pad]("http://www.bidorbuy.co.za/jsp/item/Item.jsp?Trade_TradeId=20479508") yesterday, and tried it out. It worked beautifully! I hammered the laptop with everything I had for several hours, and the hottest it got was 47 degrees, and no shutdown! :)

Cheers
Grakul

---

### Post by norseman-has-a-laptop on 2010-04-20
like said in my early post it really low tech but it works take a desk fan and put it behind your laptop

---

### Post by malmomma on 2010-04-20
> **SnickerSnack said:**
> You could just have the cells replaced.  It should be considerably cheaper, but I don't know if it's the sort of thing where you take it in and it's done a couple of hours later, or if you have to mail it in.  BatteriesPlus replaces cells afaik.

Hmm, that's good to know.  I'll have to check it out.  I just unplugged & Ubuntu told me that at a "full charge" it's at 38.7% capacity.  Yikes!

---

### Post by norseman-has-a-laptop on 2010-04-20
i think just getting a new battery is less hassle in my opinion

---

### Post by zodiac09 on 2010-04-20
My Gateway laptop use to run really hot with ubuntu, and consume a lot of power as well on the battery. For the overheating, it was full of dust from ashes, and what not. If you smoke they can get dusty fast, if the ash tray is near! So i took her apart and cleaned it. That made the fan work bettter. Doesn't overheat anymore. 

Also i got a cooling pad to help out when for mass CPU consumption while playing games and what not. Those are worth looking to
 
As for power consumption, u just have to turn off the crap u don't need when ur on batttery, make your own scripts to turn off services u don't need running, and dim the backlight.

---

### Post by Grakul on 2010-04-20
> **norseman-has-a-laptop said:**
> like said in my early post it really low tech but it works take a desk fan and put it behind your laptop

Indeed! That's basically what the cooling pad is, anyway, except it's far quieter and doesn't need external power. :)

---

### Post by D.horse on 2010-04-20
From my original post i have dramaticly decreased the running temperture even with the thermal setting set to max performance in the BIOS.

The solution?  The obvious one.  I bought a can of compressed air and used it generously to clean out the fan.  This brought the idle operating temperature down from 67 degrees to 38.  This was the single most affective thing i attempted.

Even though it sounds obvious i neglected to believe that the dust was actually the problem.  This was usually what everyone would say try first and i would be like  "yeah, yeah, i think it is still pretty clean already." Nah!!  Try it!  I think you will be suprised.  (NOTE:  Air from an actual aircompressor may work even better.)

---

### Post by norseman-has-a-laptop on 2010-04-20
> **Grakul said:**
> Indeed! That's basically what the cooling pad is, anyway, except it's far quieter and doesn't need external power. :) good point but most cooling pads dont blow enough and then they run off your laptops power if you have a crappy battery its pretty much silly to use one lol so i use my desk fan because it keeps me and my laptop cool lol

---

### Post by norseman-has-a-laptop on 2010-04-20
> **D.horse said:**
> From my original post i have dramaticly decreased the running temperture even with the thermal setting set to max performance in the BIOS.

The solution?  The obvious one.  I bought a can of compressed air and used it generously to clean out the fan.  This brought the idle operating temperature down from 67 degrees to 38.  This was the single most affective thing i attempted.

Even though it sounds obvious i neglected to believe that the dust was actually the problem.  This was usually what everyone would say try first and i would be like  "yeah, yeah, i think it is still pretty clean already." Nah!!  Try it!  I think you will be suprised.  (NOTE:  Air from an actual aircompressor may work even better.) i feel that use i have to reduse something on my laptop i feel like im jipping myself off and im not getting all i need you know

---

### Post by Grakul on 2010-04-21
> **norseman-has-a-laptop said:**
> good point but most cooling pads dont blow enough and then they run off your laptops power if you have a crappy battery its pretty much silly to use one lol so i use my desk fan because it keeps me and my laptop cool lol

Good point, but I never run my laptop off the battery, and it's actually a bonus that the cooling pad uses the laptop's power. ;)

---

### Post by dave2001 on 2010-04-21
If you have a Thinkpad, like the OP, you might want to check out TPfan. It's a gui application that uses acpi to control your fan. You can use preset profiles for your specific model, or (at your own risk) make your own settings. I have it running on my laptop, and it has helped the overheating problem dramatically. I don't think anyone's mentioned this here, sorry if they have.  I know there are packages for 8.04 through 9.04, not sure if they work with karmic. You can download or get resository info here:
 [http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control#Download_prebuilt_packages](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control#Download_prebuilt_packages)

---

### Post by norseman-has-a-laptop on 2010-04-23
> **Grakul said:**
> Good point, but I never run my laptop off the battery, and it's actually a bonus that the cooling pad uses the laptop's power. ;)

true lol

---

### Post by mexlinux on 2010-05-10
could it also be this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156)

---

