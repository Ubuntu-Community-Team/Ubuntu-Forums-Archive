---
title: "Notebook overheated, now permanent damage =("
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by faswad on 2006-06-01
I've been using Ubuntu for over a year now and everything has been great. I just received a new laptop:

Dell Inspiron 9400\E1705,
Intel Core Duo
17" UWXGA screen,
NVIDIA 7800GS.

I installed Ubuntu on 20gb partition, and everything ran great for about a week. A week later, while I was compiling code, the latop crashed. Reboot again into Ubuntu it crashes again. The time before crash was proportional to how long the laptop was off, so I concluded it was a heat issue. 

After 3-4 crashes the screen began having artifacts and it kept getting worse. I turned the machine off for about 1 hour, tuned it on again and more artifacts appeared, even in Windows the artifacts were there. The artifacts were even there at POST, so its def not a driver issue.

The notebook is permanently damaged. I believe the video card is damaged from overheating... Its not the LCD because the artifacts are not there in the BIOS for example (4 colore mode).

I didnt encounter any heat issues or crashes in Windows XP, these issues only happened in Ubuntu.


Has anyone encountered this?
I received a replacement from Dell, but i'm hesitant to run Ubuntu again. 
Does anyone have any advice? I think that allowing the fans to turn on at a lower temperature may help the situation, but i'm still not sure. Also, what controls the video card fan, bios, os, other?

thanks for any help!

---

### Post by johnc4510 on 2006-06-01
I have read a few posting about problems with duo core processors only using one of the cores and not the other. Don't know if this is the case or not, but it would contribute to overheating if only one was in use.

---

### Post by faswad on 2006-06-01
[QUOTE=johnc4510]I have read a few posting about problems with duo core processors only using one of the cores and not the other. Don't know if this is the case or not, but it would contribute to overheating if only one was in use.[/QUOTE]

Good point, but I was using the 686-SMP kernel. 2 processors were showing in cpuinfo.

---

### Post by TheDocMan on 2006-06-01
I have a Compaq Armada M700.  The fan on it never runs under Ubuntu, but happily works under windows.  Luckily I guess the 700Mhz processor in mine never has cooked yet.  I've never really found a reason why the fan wont work.    But I feel your pain.  I wouldnt load ubuntu back on that until a fix is found.   Or at least if you do, dont run it much. :???:

---

### Post by johnc4510 on 2006-06-01
If i remember correctly, both were showing up, but only one was computing. Check the threads via the search engine for duo core. Maybe that will help.

---

### Post by norman_h on 2006-06-01
Its a problem with the ACPI.

---

### Post by David Corrales on 2006-06-01
I would stay away from Ubuntu since this bug will kill your video card again. Try another distro and see if the problem persists then report back.

---

### Post by faswad on 2006-06-01
[QUOTE=David Corrales]I would stay away from Ubuntu since this bug will kill your video card again. Try another distro and see if the problem persists then report back.[/QUOTE]

I really want to, but its so hard. I'm thinking there may have been something wrong with the video card in the first notebook...

i'll give ubuntu another shot. i'll update.

---

### Post by croc on 2006-06-04
hi,,

I have a DELL inspiron 6400 with ATI 1400
since my last ubuntu upgrade from 6.06 RC to 6.06 LTS release i have same problem: after some time (2-3minutes) system freeze and laptop is hot around the mediadirect button. Roll back to 2.6.15-22 kernel but same problem. 

Perhaps it's the lasted ATI driver.

I'll post here if i found anything.

---

### Post by xanthorrhea on 2006-06-04
[QUOTE=David Corrales]I would stay away from Ubuntu since this bug will kill your video card again. Try another distro and see if the problem persists then report back.[/QUOTE]

This  is  interesting in as  much  as  I have an ACER 2046 [P4 2.0GHz] can  you  or  anyone else confirm  that running  Ubuntu is a serious risk  with regards  to  cooling.
I haven't seen any  problems even after using the  machine  for  a couple  of hours, but  touching the  underside it does  seem  hot ... hotter than when using  XP I don't  know.

rgds
Roberto

---

### Post by zahidism on 2006-06-04
actually, i've experienced the same w/ ubuntu.  albeit my graphics card is a whole lot weaker (mobility radeon 9000...actually i think it's an IGP) but my CPU (pentium M 2 ghz) runs hotter than on windows because the fan is always on.  I was wondering if there were any fan monitoring or temp monitoring software for ubuntu.

---

### Post by NiksaVel on 2006-06-04
hey.. I was about to ask the same question...  I installed ubuntu to my lap yesterday and was quite worried when I saw this post...  wouldn't want to burn my baby :)


anyways, I browsed a little through synaptic for some temperature sensor progs and found that lm-sensor prog. However, since if I figured it out okay, it's a terminal only prog, I got lost trying to figure out how to use it...  

can some1 pls explain how to see the temp of my lap or perhaps recommend an alternative temp monitoring program, perhaps with gui support?

thnx!

---

### Post by .t. on 2006-06-04
Use i8kutils to monitor and maintain fan speed, but it only works (I think) on Dell laptops. I find, on my Inspiron I6k, that the area just below the screen, where it says Dell, get's very hot. However, that is where the WiFi aerial is connected.

---

### Post by faswad on 2006-06-04
Note from my original post that:

a) i have another laptop thats been running Ubuntu stably for over a year.
That laptop is a Centron 1400Mhz, ATI video card. Generates very little heat in general.

b) new laptop is a desktop replacement. The video card, intel wifi card, core duo cpu, and hard drive all generare considerably more heat than my old laptop.

So for those who are worried, i think the worry is only warranted if you are using a notebook that's really pushing the heat limit due to hardware (ie Geforce7800/7900, ipw, core duo).

---

### Post by NiksaVel on 2006-06-04
still, I wouldn't mind an easy to use gui program that will show me the temps if I feel like checking them out...  :mrgreen:

---

### Post by microsome on 2006-06-05
[QUOTE=NiksaVel]hey.. I was about to ask the same question...  I installed ubuntu to my lap yesterday and was quite worried when I saw this post...  wouldn't want to burn my baby :)


anyways, I browsed a little through synaptic for some temperature sensor progs and found that lm-sensor prog. However, since if I figured it out okay, it's a terminal only prog, I got lost trying to figure out how to use it...  

can some1 pls explain how to see the temp of my lap or perhaps recommend an alternative temp monitoring program, perhaps with gui support?

thnx![/QUOTE]

I totally have the same concerns. I run 6.06 on a Dell 600M and the fan is way more often running than under XP. I checked the senors and they are not working, beside of the CPU sensor. In the booting procedure Ubuntu states that it can't set the sensor limits.

---

### Post by NiksaVel on 2006-06-05
same thing here...   (the boot up failed error for sensors)... but I also still don't know how to get any info from the lm-sensors program... help?

---

### Post by faswad on 2006-06-05
[QUOTE=microsome]I totally have the same concerns. I run 6.06 on a Dell 600M and the fan is way more often running than under XP. I checked the senors and they are not working, beside of the CPU sensor. In the booting procedure Ubuntu states that it can't set the sensor limits.[/QUOTE]

[QUOTE=David Corrales]I would stay away from Ubuntu since this bug will kill your video card again. Try another distro and see if the problem persists then report back.[/QUOTE]

Just fyi, my old notebook is a 600M, been running Ubuntu solid for over a year.

---

### Post by Jason_25 on 2006-06-05
I would demand the laptop manufacturer give you one that does not overheat.  If it is placed on a hard surface with nothing blocking the vents and a decent ambient temperature it should **not** overheat.  Even if the ACPI was not enabled in ubuntu the fans should run full speed, not the other way around.  That's retarded design.  So many laptop manufacturers try to get away with using marginal hardware/cooling systems.

---

### Post by linuxworld on 2006-06-05
[QUOTE=NiksaVel]hey.. I was about to ask the same question...  I installed ubuntu to my lap yesterday and was quite worried when I saw this post...  wouldn't want to burn my baby :)


anyways, I browsed a little through synaptic for some temperature sensor progs and found that lm-sensor prog. However, since if I figured it out okay, it's a terminal only prog, I got lost trying to figure out how to use it...  

can some1 pls explain how to see the temp of my lap or perhaps recommend an alternative temp monitoring program, perhaps with gui support?

thnx![/QUOTE]

I use this for my temperature on my laptop
[http://computertemp.berlios.de/](http://computertemp.berlios.de/)
there is a deb. file for dapper
check it out :D

---

### Post by NiksaVel on 2006-06-06
I installed it from the deb package, but how do you start it?

---

### Post by mikeytag on 2006-06-06
[QUOTE=NiksaVel]I installed it from the deb package, but how do you start it?[/QUOTE]

Just right click on your panel and click the "Add to Panel" button. You should find an entry for Computer Temperature Monitor under the System & Hardware section.

BTW, I just installed it on my Sharp laptop. It runs a P3 at 1.13Ghz and I am running consistently around 113F (45C). I noticed my laptop gets much hotter than when I boot to XP and as such the battery drains much faster. In fact, I have been keeping it on a laptop cooling pad because it gets uncomfortable on my lap. :) I love Ubuntu and use it on more than this laptop but would love to tackle and fix this heat issue as well as many of the other posters here. I will post here if I find anything interesting out.

Mike

---

### Post by mikeytag on 2006-06-06
I posted previously that my system is running consistently at 45C but after researching more into how hot laptops are supposed to run I don't think this is all that bad. Most people are reporting crashes and overheating at 70-80C Which is a lot hotter than mine runs. I think overall my laptop is actually operating normally. Does anyone know for sure what recommended operating temps are for a laptop? I know cooler is better but I wonder what are acceptable ranges.

---

### Post by mikeytag on 2006-06-06
Once again another post to my other posts. You know it would be more efficient if I did it all in one shot. :)
One thing I did to see exactly what my processor was doing was to enable the CPU Scaling Frequency Monitor to my panel. I then watched what my Ubuntu system did as I ran different apps and things. Sure enough, when the cpu needed to be used the monitor showed the system scaling the processor up to the full 1.13 GHz and then back down to around 731 MHz when it was done.
This little monitor may help a lot of people determine if their system is actually running as it should. 
I think it is especially important that a laptop scale down performance during idle times to preserve the internal electronics and battery life. Hope this helps anyone who happens on this thread.

---

### Post by blip on 2006-06-06
[QUOTE=NiksaVel]same thing here...   (the boot up failed error for sensors)... but I also still don't know how to get any info from the lm-sensors program... help?[/QUOTE]
If you're still looking for lm-sensor help, check out this thread: [http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors) . It worked for me.

More generally, I've been running xubuntu on my rather ancient laptop for a while now with no problems.  I've seen anywhere from 45-65 C temps on it, but thus far it hasn't had any problems that I can conclusively identify as heat related.  Interestingly enough, it seems to run significantly cooler under linux than it did under windows. (Perhaps explaining why it is so much more stable now.)

I'm not sure what counts as acceptable laptop temperatures, it probably varies from model to model.  However, from what I've seen anything sub-60 C is good and higher temps are certainly not unusual.  That said, I haven't had much experience with higher end laptops which (perhaps) are more vulnerable to heat damage... 

Just as an FYI too, I ran across this site which chronicles Intel based Mac laptop temperatures... Interesting patterns: [http://www.intelmactemp.com/list](http://www.intelmactemp.com/list)  Some of those are pushing into the 90s when they are put under load  IEEE!  That's a spicy laptop!  It would scorch your lap.

---

### Post by zahidism on 2006-06-06
my dell 600m runs about 8 deg C hotter under ubuntu than in windows.  i love ubuntu but it's becoming unbearable.  the avg temp under windows is 42 w/ fan tweaking and the average is about 50 w/ fan tweaking under ubuntu.  this is dissappointing :( 

ps. i do have fglrx installed...though my IGP graphics card (mobility radeon 9000) shouldnt produce much heat as compared to windows.

---

### Post by crashtest on 2006-06-18
Oh man, I can't believe this!  I just got my Dell Inspiron 9400 yesterady, and I'm already having overheating problems.  It seems to me that the fans never run on high when I'm running Linux.  AFter a couple of hours the notebook becomes sluggish, and then locks up.  If I do a quick reboot, the POST fails with this message:

DST Short Test Fail - error code 1000-0141 No hard drive detected.  

If I allow it to cool down the notebook starts properly and seems OK again.  My 9400 has the Go 7900 Nvidia card, 1.83 Ghz duo core, and a 7200 RPM drive.  There does not appear to be any damage so far, and I've just installed the temperature monitor mentioned earlier in ths thread.

What should I do next?  What temperature should be accepted as normal?  I've been running for just 15 minutes, and the temp has risen from 28 to to 44 degrees C, which I think is still quite low.

---

### Post by NiksaVel on 2006-06-18
well... my temperatures reported are between 50-55 which should be okay, but I am quite confused as the part where I put my hands on below the keyboard is so hot that it's uncomfortable to work... didn't have this happening with windows...  ever. :mad:


the part where the battery is seems to be the hottest, almost too hot to hold my hand on and it's running on ac power

---

### Post by zahidism on 2006-06-18
yup, same deal w/ my 600m.  i cant figure out why it runs hotter because using the fan control tool w/ i8k and gkrellm i have the fans running at the same speed as in windows...yet the temp is 10 degrees C hotter.

---

### Post by crashtest on 2006-06-18
Mine doesn't get hot on the top surface, but is very hot to the touch underneath.  Yesterday I was running for a long time with the notebook on my lap, and I guess this blocks the ventilation holes on the bottom.  There are still two ventilation holes on the back, and one on each side that were never blocked.  It seems strange to me that the fans never spin up to high speed. I've hardly had it running in Windows so I don't know if there is anything different.  Right now I don't feel any air movement at all - temperature is currently 41 C.  I'm working on my Windows desktop machine now, and letting the notebook idle.

I ran the Dell diagnostic (downloaded and burned a CD because I can no longer boot into the diag or restore partitions).  The diagnostic reports that everything is ok.

---

### Post by NiksaVel on 2006-06-18
hehe.... mine is hell underneath...  and uncomfortably hot on top...  this was after it was idle and with the shut lid for some 30 min.

when it's open I don't think it gets to that "uncomfortable" levels....   been working with it periodically under linux for some weeks now...

---

### Post by faswad on 2006-06-18
UPDATE
-------------------------------

I received my new E1705 (9400) from Dell. I couldnt deal with Windows XP so I've decided to install Kubuntu again.

The temperature kept rising to 45-50 again, while just sitting there, fan would not even come on.

After a couple hours of fidling, i made some changes which seem to have so far fixed my problem. My temperature has remained around 29-30 while idle. During hard processing sometimes goes up to 45 or so, and above that the fans seem to work properly. SO far, its been about two weeks, no issues with overheating.

I am under Kubuntu, so settings may differ for your setup:

1.
Under System Settings > Laptops & Power > Laptop Battery > ACPI
ACPI was turned OFF by default! SO first step was to turn ACPI on.
I also enabled suspend, hibernate, and CPU throttling from this menu.

2.
Under System Settings > Laptops & Power > Laptop Battery > Power Control
Not Powered: System performace: userpsace
Powered: System Performance: userspace

3. 
Under System Settings > Laptops & Power > Laptop Battery > Default Power Profile
Not Powered: System performace: userpsace
Powered: System Performance: userspace

CPU throttling i did not mess around with. i like having 100% of my cpu available (if requested by the os) under battery mode.

so far things have been awesome. its been great having linux on my notebook again.

good luck!

---

### Post by xp_newbie on 2006-06-18
Guys, I don't know if any of you noticed but I posted a few days ago a message about what I believe to be the same problem. I only phrased it differently. Read here:

[http://ubuntuforums.org/showthread.php?t=197911]("http://ubuntuforums.org/showthread.php?t=197911")

From the lack of ideas it doesn't look good.  :-(

---

### Post by nobodysdarling on 2006-06-18
I am scared as hell now to install on my new Vaio Duo Core

---

### Post by PG Wingrove on 2006-06-19
Hi I have Ubuntu 6.06 LTS running on my old Dell Inspiron 3800...same problems: machine overheats, shuts off, reboots, etc.

Previously installed 5.10 Breezy with "-noapci" switch...did not get the overheating problem!

Problem must be with ACPI in 6.06.

---

### Post by RandomJoe on 2006-06-19
I can't say anything for the newer hardware specifically, but I have had the overheating issue with one Dell model before.

My "old faithful" laptop is a C840, which has been running various versions of Linux for several years.  If I don't have the i8k module loaded on it, the BIOS presets some worryingly high setpoints for the fans.  Indeed, it appears they ONLY run high speed, then shut off completely when below a certain temp.  If I have i8k loaded and the i8kutils running, then with one fan on low speed the computer sits at around 56C for the most part.  Heating up, of course, under load and switching the fans on/higher.

I recently got a C640 from work, and it doesn't do the above.  Without the i8k module and program running, the fans don't come on AT ALL!  I was ripping a DVD on it and got the nice "melting plastic" smell.  Fortunately, as soon as I loaded the i8k module and program the fans kicked in and it cooled down and survived...

Right now, with 6.06, I have the i8k module loaded, i8kmon running as a daemon, and Gnome Sensors Applet running in the systray showing the temp.  I also have the CPU Frequency Scaling Monitor beside the Sensors applet showing the frequency.  All of these are in the repository (I use Synaptic).  The i8k stuff is, as mentioned before, for Dell only.  Perhaps other brands don't need them?

---

### Post by morgengenuss on 2006-06-19
uuuuarrgh. i have a dell inspiron 9400 as well and i don't want to burn it!
fortunately it seems a lot better with the ati x1400 i got from dell instead of the ordered geforce... (actually the temp drops a bit if i switch my ati with aticonfig --set-powerstate=1 to low voltage)

still my cpu has around 52°C most of the time and actually the whole thing seems warmer than in xp. anyone a clue what to do?
(i tried to install lm sensors but actually didn't work.)

---

### Post by vayde on 2006-06-20
I have an Inspiron 9300 that has been running Ubuntu since January.  

I have been a little worried about heat, as the machine does get pretty hot.  Some research online yielded a maximum temperature rating for the cpu (pentium M 2Ghz) at 100 c.

This thing sits on my desk plugged in to ac current all day long, and at idle it runs somewhere between 116 F and 127 F.  under a heavy load it will jump up to around 140 F.  Even playing NWN doesn't push it past that (about 138F) Sorry about the F, I think in F, setting it to C wouldn't help me keep an eye on the temp.

I was worried about the fans, as the larger fan on the left did not seem to come on at all.  I even went so far as to call Dell and ask them about it, they promptly sent me replacement fans- which I didn't turn out to need (thanks Dell, I guess).

Under some experimenting I found that the large left fan comes on religiously when the cpu is loaded (running 3-10 instances of glxgears for example).  The smaller right fan comes on and goes off at strange intervals, without me being able to tie them to any specific behavior.

Im just throwing this info out there in hopes that it might be of use to someone.  Like I said, the box runs hot, but that's not too uncommon from what I hear.  I have a couple of toshiba tecra 8000's running Xubuntu and they get toasty too.

---

### Post by NiksaVel on 2006-06-20
Hey all,

this is what I noticed...  the most heat seems to come from the part of my laptop where the battery is located... and it seems to be only when it's connected to AC.

The part where the proc is does not get all that hot...  and the temp monitor doesnt show it as going above 54 C, which is close to windows stats (approx. 51 C)...

---

### Post by NiksaVel on 2006-06-20
Here is what I realised

when my laptop really starts getting hot is when the battery is full and it's connected to AC power. When it's charging or discharging it's totally okay...

anyone have any idea why is this happening?


oh...  and this does NOT happen under windows

---

### Post by zahidism on 2006-06-20
maybe it is an ACPI issue?  anyone look into this for Ubuntu?

---

### Post by faswad on 2006-06-20
[QUOTE=zahidism]maybe it is an ACPI issue?  anyone look into this for Ubuntu?[/QUOTE]


Well ACPI was shown to be "OFF" in Kubuntu. Once ACPI was turned on from the Power and Laptops interface, the temperature of CPU seems to have stabilized around 30C (compared to 50 before).

---

### Post by crashtest on 2006-06-20
I found that the Windows version of the i8k fan control software does not work with dual core notebooks - support will be added for the i9k version.  I had installed i8k in Ubuntu, and found that while the temperature senosrs worked the fans did not turn on.  I;m guessing this is for the same reason.

I think my next move is to buy a Chill Mat, which I've heard is very effective.[http://www.targus.com/us/product_details.asp?sku=PA248U]("http://www.targus.com/us/product_details.asp?sku=PA248U")

---

### Post by crashtest on 2006-06-20
OK, this gets more and more strange.  I'm running my notebook right now from the live CD, and the fans are working perfectly.  The CPU temp is ranging between 26 and 33.  I'm not doing anything beyond reading the forums so the notebook is staying quite cool, and in fact the CPU is scaled back to 1 GHZ most of the time.  Whenever the CPU gets up to around 32 the fans kick in on low speed and the temp drops back below 30. I could swear this was not working when I had Ubuntu installed on the hard drive, and updated to June 17th.  Could something in a recent update have broken ACPI?  I wonder if someone else who is having fan problems could test with the live CD?

---

### Post by morgengenuss on 2006-06-21
shit, you're right... when i start xubuntu with the live cd "acpi -t" shows me 35°C, when i start the installed version i got 48°C.

any suggestions what to do with the acpi?

(actually lm_sensors is installed on my xubuntu, but each time i boot it fails... the sensors command says that it doesn't detect any. or will this be resolved by i9k?)

edit: is there a way to downgrade to the initial version of acpi?

---

### Post by faswad on 2006-06-21
Hmmm...

[Dell laptop explodes during Linux conference...]("http://www.theinquirer.net/?article=32550")

---

### Post by faswad on 2006-06-21
[QUOTE=crashtest]OK, this gets more and more strange.  I'm running my notebook right now from the live CD, and the fans are working perfectly.  The CPU temp is ranging between 26 and 33.  I'm not doing anything beyond reading the forums so the notebook is staying quite cool, and in fact the CPU is scaled back to 1 GHZ most of the time.  Whenever the CPU gets up to around 32 the fans kick in on low speed and the temp drops back below 30. I could swear this was not working when I had Ubuntu installed on the hard drive, and updated to June 17th.  Could something in a recent update have broken ACPI?  I wonder if someone else who is having fan problems could test with the live CD?[/QUOTE]

Good observation. Thats two confirmed. I will download Xubunut and give it a shot.

---

### Post by faswad on 2006-06-21
UPDATE:

I've been playing around with the ACPI settings.

The default Dapper 6.06 install seems to come with ACPI THROTTLING OFF.

When I keep the option OFF, my CPU temperature goes up to 45C when idle. Within about 1 minute of turning the option ON, the temperature drops to 29-30C (1.88ghz intel core duo).

Can someone whose CPU is running hot idle, confirm this information?

To check ACPI Throttle Status:
```
cat /proc/acpi/processor/CPU0/info
```

Under Throttling Control, it should say Yes or No. Check CPU1 as well if you have core duo:
```
cat /proc/acpi/processor/CPU1/info
```

---

### Post by vayde on 2006-06-21
[QUOTE=faswad]

Can someone whose CPU is running hot idle, confirm this information?
[/QUOTE]

What are we talking about in terms of 'hot'?  Sure,   cooler is better, but where are we thinking 'too hot' is?

My Pentium M 2Ghz is idling arount 120F or 50C.  
cat /proc/acpi/processor/CPU0/info yields:

processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes

---

### Post by morgengenuss on 2006-06-21
weird weird...

ok, i can give you an update on my situation:
today in the afternoon. my cpu had around 50° being idle.
i tried the live-cd and my cpu had around 35°.
i tried winxp with a temp control prog and it had around 40°.

now that i switch it on again in winxp, it says 30°.
and actually after reading this thread i went back to ubuntu and now it says 29°...
throttling is on.

i really don't understand what's goin on. maybe i'll just be careful and monitor the cpu temp...

---

### Post by zahidism on 2006-06-21
[QUOTE=vayde]What are we talking about in terms of 'hot'?  Sure,   cooler is better, but where are we thinking 'too hot' is?

My Pentium M 2GZ is idling arount 120F or 50C.  
cat /proc/acpi/processor/CPU0/info yields:

processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes[/QUOTE]

I have the same processor (Pentium M Dothan 2 Ghz) and I have the same specs for cpu info.  my CPU also idles at 50 degrees C and that's even when it's running at 600 mhz spec! woe is me.

---

### Post by vayde on 2006-06-21
Does anyone know what spec is for any of these processors?  I have found maximum ratings, but I can't find 'normal' data.

I'd like to know what normal is before I get too worried.

Btw, my girlfriends dell i1000 2Ghz is idling out at 52 C too.

---

### Post by TheCross on 2006-06-21
Hello all,

Recently upgraded to 6.06 and been having problems with overheating since then.

Running a HP zd7200 3.2 GHz

cat /proc/acpi/processor/CPU0/info outputs:

processor id: 0
acpi id: 0
bus mastering control: yes
power management: yes
throttling control: yes
limit interface: yes

Idel temp is 68-70!

Any ideas for how I can get this down?

thanks!

---

### Post by faswad on 2006-06-21
I have a 1.8ghz Intel Core Duo.

Idling at 29C.


What is the output of:

```
cat /proc/acpi/processor/CPU0/power
```

---

### Post by TheCross on 2006-06-21
Output

active state:            C1
max_cstate:              C8
bus master activity:     129a78a5
states:
   *C1:                  type[C1] promotion[C3] demotion[--] latency[000] usage[00732283]
    C2:                  <not supported>
    C3:                  type[C3] promotion[--] demotion[C1] latency[085] usage[04548222]

---

### Post by jmr on 2006-06-21
This is a worrying issue.

There might be a combination of factors contributing to this.  One of them is a possible bug introduced in SMP kernels in Ubuntu 6.06, which is related to ACPI and CPU throttling states.  (See [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557").)  It could be that it only shows on some CPUs.

Aparently this bug keeps the CPU busy even during idle periods.  Naturally this contributes to heating and reduced battery time.  I believe the fans should work even if ACPI is not supported in the OS.  I'm quite sure that's what happened when I had no acpi in previous versions of ubuntu on my Acer Aspire  1692WLmi (Pentium M 1.73GHz + ATI X700).  So the overheating may occur only on some laptops that have some weird management of the fans.

In order to test the hypothesis that Bug 30557 may be partially responsible, you could try a few things while keeping an eye on CPU frequency (use CPU frequency scaling monitor), CPU usage (you can use "System monitor" found in the System->Administration submenu) and temperature (on my system i can check it with "acpi -t" on a terminal).

1) Boot with a -386 kernel.  (All -686 kernels are compiled with SMP and seem to show this problem.)  Does the problem go away?  (I guess this is what happens when you boot from the live CD.)
2) Boot with a -686 kernel and 
```
sudo echo 1 > /sys/module/processor/parameters/max_cstate
```
Any better?
3) Still with -686 kernel,
```
sudo echo 2 > /sys/module/processor/parameters/max_cstate
``` 
Back to old behaviour?

If you answer yes to these 3 questions, then you confirm the bug.

On my laptop, with max_cstate=1, I get typically 5% CPU usage when idle and CPU down to 800MHz, with max_cstate>=2, CPU usage varies more but frequently around 30-50% and CPU freq seldom below the max 1.73GHz.

If you can confirm this, it would be a good idea to add a comment to the Bug page, and possibly open a new bug report stating the overheating issue.

João Rodrigues

---

### Post by crashtest on 2006-06-21
So how do you manually turn ACPI throttling on?  My hard drive was damaged on day one when I installed Ubuntu.  Now granted, I ran the thing for 10 or 12 hours, and a lot of the time I had it on my lap, so perhaps the vents where partially covered.  I got a replacement hard drive from Dell and reinstalled Windows today, and now I'm getting ready to install Ubuntu.  I plan to run Linux most of the time, but I'm very scared about causing more damage.

I was planning to buy a Chill Mat but I've heard from a few people that it would be a waste of money.  Does anyone know if the same problems exist on other distros running on the core duo notebooks?  I picked this notebook specifically because it should work well with Linux.  I ordered the Nvidia card and the Intel wireless because I found they were well supported.  Damn!  Now what to do???

---

### Post by faswad on 2006-06-21
[QUOTE=TheCross]Output

active state:            C1
max_cstate:              C8
bus master activity:     129a78a5
states:
   *C1:                  type[C1] promotion[C3] demotion[--] latency[000] usage[00732283]
    C2:                  <not supported>
    C3:                  type[C3] promotion[--] demotion[C1] latency[085] usage[04548222][/QUOTE]


aah this might be your problem then. mine reads:

active state:            C2
max_cstate:              C8
bus master activity:     100001f0
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[09331219]
    C3:                  type[C3] promotion[--] demotion[C2] latency[057] usage[18504821]

C2 is my active state which is the mid-idle state; mid-power usage. C1 means your CPU is throttled to 100% (most usage). It should drop to C2 or C3 when idle or when little usage is going on. According to ACPI4Linux documentation, C1 should only be used during bootup, shutdown, and high activity "working state". I noticed mine drops to C3 when the computer sits there for a few mins with no use. WIth moderate use, it goes to C2. I have not seen it at C1 yet.

---

### Post by vayde on 2006-06-21
686 kernel: idle bounces between 26%, 34%, 56%  constantly.

386 kernel: idle 0% to 5%.

Heat stays about the same either way, 48 -51 C  at idle, up to 60C under heavy load.

Ill stick with the 386 until the bug is taken care of I guess.

What's the difference between the 686 and the 386 anyway?  Is there a short answer?

---

### Post by zahidism on 2006-06-21
i found no performance diff between them in my 2 ghz pentium M.  heat-wise is the same.  this is really a horrible problem i hope to get fixed otherwise i'm scrapping ubuntu once again.  the first time it was the wireless and my broadcom card.

---

### Post by misha680 on 2006-06-21
I have had the Dell 600m for three years now, ran windows xp until two weeks ago and now have Ubuntu Dapper Drake. I leave my laptop on continuously although I put it in suspend mode when I am not using it. From what I have read of the Dell Forums over my time owning the notebook, it getting hot during use is a common issue and is not unique to Ubuntu. I have experienced this quite a bit in Windows when using it on my lap for a while, it gets unbearably hot. I have not had any problems with Ubuntu for the past two weeks in terms of this, and have not noticed it getting any hotter. I installed i8k and have a sensor monitor that is right now reading a 43 C which seems reasonable to me.

I think that there may be a genuine problem with the kernel based on the posts here but also from my experience with the Dell Forums I feel that this notebook (and perhaps other Dells) is known to run hot (also another problem that I noticed people have had in Ubuntu, with the system not coming out of standby mode sometimes, is something that I have had with the notebook with Windows XP since I bought it and was only fixed in BIOS update A16).

Just my two cents.

Misha

---

### Post by vayde on 2006-06-21
[QUOTE=zahidism]i found no performance diff between them in my 2 ghz pentium M.  heat-wise is the same.  this is really a horrible problem i hope to get fixed otherwise i'm scrapping ubuntu once again.  the first time it was the wireless and my broadcom card.[/QUOTE]

Im probably too much of a noob to appreciate it, but what's the problem?  Like I said earlier, I can't seem to find any data telling me what these things are *supposed* to run at.

Is hanging around 50C a bad thing?  Yeah it would be cooler if it was cooler- certainly  nicer on my lap, but laptops run hot.  Isn't that a given?

---

### Post by TheCross on 2006-06-22
[QUOTE=faswad]aah this might be your problem then. mine reads:

active state:            C2
max_cstate:              C8
bus master activity:     100001f0
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[09331219]
    C3:                  type[C3] promotion[--] demotion[C2] latency[057] usage[18504821]

C2 is my active state which is the mid-idle state; mid-power usage. C1 means your CPU is throttled to 100% (most usage). It should drop to C2 or C3 when idle or when little usage is going on. According to ACPI4Linux documentation, C1 should only be used during bootup, shutdown, and high activity "working state". I noticed mine drops to C3 when the computer sits there for a few mins with no use. WIth moderate use, it goes to C2. I have not seen it at C1 yet.[/QUOTE]

Is there any way I can get C2 supported? 

And by the way, thanks for your help so far. Much appreciate!

---

### Post by faswad on 2006-06-22
[QUOTE=vayde]Im probably too much of a noob to appreciate it, but what's the problem?  Like I said earlier, I can't seem to find any data telling me what these things are *supposed* to run at.

Is hanging around 50C a bad thing?  Yeah it would be cooler if it was cooler- certainly  nicer on my lap, but laptops run hot.  Isn't that a given?[/QUOTE]


While there are no set standards on what a proc should idle at, i think that there are a few points worth noting:
1. the lower the idle temperature, the longer the life of a proc (theoretically).
2. if the idle temp is 30C instead of 50C, then when heavy usage occurs, theoretically again, the core running at 30C will rise to say 60C, while the 50C will rise higher, at which point problems may start occuring (including premanent damage, which happened to my last laptop under Ubuntu).
3. But back to the argument, what many people are pointing out is that the laptops are just running hotter in Ubuntu (6.06) than in Windows. That should not be the case.
4. Recent reports show that the laptops run cooler in Xubuntu and using the 386 kernel compared to 686 kernel (6.06).

From these notes, I would say that a notebook running at X temperature may not be the problem. But a notebook running a X temperature under one kernel or one distro and X+Y temperature (Y being positive) in another distro probably means that the second distro could be doing a better job to drop the temperature. 

Its strange that my core duo is now running at 29-30C idle, while before I activated CPU throttling it would idle around 45C.

Anyhow my 2cents if it makes any sense.

---

### Post by TheCross on 2006-06-22
[QUOTE=faswad]
Its strange that my core duo is now running at 29-30C idle, while before I activated CPU throttling it would idle around 45C.

Anyhow my 2cents if it makes any sense.[/QUOTE]

How can I activate/deactivate throttling? This might be a good test.

Thanks!

---

### Post by Hopelessness on 2006-06-22
my old twinhead has hardware sensing for the fan, so it runs the same in windows, ubuntu and whatever else you want to throw at it 8)

---

### Post by morgengenuss on 2006-06-22
@faswad: what exactly did you do to get your cpu at 30° when idle? did you just switch on throttling? (is switched on already, but still mine is idle at 50°; actually this seems to change every day...)

---

### Post by TheCross on 2006-06-22
It looks as though I might have solved the problem.  Opened her up and gave the fans a good clean.  She is now ideling around 40 and up to 70 while ripping a CD (this use to make her crash).  Very quickly drops down to sub 60 once complete.

I would like to give the fans a very good clean, but did not have all of my screw drivers.

Will post another update when I've done that.

Even though it seems to have fixed it, there still seems to be some underlying probelm with Ubuntu. So I will continue to investigate.

Thanks for all the help.
TC

---

### Post by faswad on 2006-06-22
[QUOTE=morgengenuss]@faswad: what exactly did you do to get your cpu at 30° when idle? did you just switch on throttling? (is switched on already, but still mine is idle at 50°; actually this seems to change every day...)[/QUOTE]

Please give output of:

```
cat /proc/acpi/processor/CPU0/power
```

and

```
cat /proc/acpi/processor/CPU1/power
```

---

### Post by faswad on 2006-06-22
[QUOTE=TheCross]Is there any way I can get C2 supported? 

And by the way, thanks for your help so far. Much appreciate![/QUOTE]

I do not think you can activate\disactivate these states. These states are processor specific (though from what I understand most processors have 4 available states, but C0 is the working state and so remains hidden from the OS).

What processor do you have?

---

### Post by TheCross on 2006-06-22
[QUOTE=faswad]I do not think you can activate\disactivate these states. These states are processor specific (though from what I understand most processors have 4 available states, but C0 is the working state and so remains hidden from the OS).

What processor do you have?[/QUOTE]

Intel P4 3.2HT

---

### Post by faswad on 2006-06-22
Quick explanation of the output from:

```
cat /proc/acpi/processor/CPU1/power
```

---------------------------
active state:            C2
max_cstate:              C8
bus master activity:     00000000
states:
    C1:   type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:  type[C2] promotion[C3] demotion[C1] latency[001] usage[00783415]
    C3:   type[C3] promotion[--] demotion[C2] latency[057] usage[02855502]
---------------------------

C0 is the highest power state (using more power, also known as the "working state"). C1 is the next highest, followed by C2 and C3. In other words, in C3, the CPU is utilizing the least amount of power, and therefore should be coolest.

Now in the C1 line you acn see that when my power gets "promoted" it goes to C2, which means uses less power. From C2 it goes to C3, when even less power is needed. That is what "promotion" means. 

Demotion is the opposite. As CPU usage increases, so does the power the CPU uses and thus, the state goes from C3 to C2 to C1. 

The most important number here is "Usage".

Note that my C1 usage is 00000010. This is the number of times my CPU has called the C1 state. Compare that to C3 which has a usage of 02855502. A ratio of these shows that my CPU has been called into the C3 state many more times than the C1 state. Which probably means my CPU is being held fast in check by ACPI to stay in the lowest state.

Again, I am not sure this info is pertinent, but it would seem to me that this info gives insight on the idle temperature of a CPU.

---

### Post by morgengenuss on 2006-06-22
that's the output of my /proc/acpi/processor/CPU0/power:
```
active state:            C3
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[01211363]
   *C3:                  type[C3] promotion[--] demotion[C2] latency[057] usage[05442924]
```


actually this looks quite good. (note: i gave dell a call today and they said that temps up to 70°C are normal for the intel dual core 2400 [1,8ghz].)

"acpi -t" gives me (right now; only firefox is open. nothing else going on):
```
Battery 1: charged, 100%
Thermal 1: ok, 49.0 degrees C
```

one more thing: my sensors couldn't be detected. that's the reason i only have the cpu-temperature and can't really control the fan activity (furthermore, my /proc/acpi/fan dir is empty but i assume that's what it's supposed to be...)

---

### Post by vayde on 2006-06-22
[QUOTE=faswad]While there are no set standards on what a proc should idle at, i think that there are a few points worth noting:
1. the lower the idle temperature, the longer the life of a proc (theoretically).
2. if the idle temp is 30C instead of 50C, then when heavy usage occurs, theoretically again, the core running at 30C will rise to say 60C, while the 50C will rise higher, at which point problems may start occuring (including premanent damage, which happened to my last laptop under Ubuntu).
3. But back to the argument, what many people are pointing out is that the laptops are just running hotter in Ubuntu (6.06) than in Windows. That should not be the case.
4. Recent reports show that the laptops run cooler in Xubuntu and using the 386 kernel compared to 686 kernel (6.06).

From these notes, I would say that a notebook running at X temperature may not be the problem. But a notebook running a X temperature under one kernel or one distro and X+Y temperature (Y being positive) in another distro probably means that the second distro could be doing a better job to drop the temperature. 

Its strange that my core duo is now running at 29-30C idle, while before I activated CPU throttling it would idle around 45C.

Anyhow my 2cents if it makes any sense.[/QUOTE]

Makes sense to me. 

In my limited experience, Im finding that temperatures are pretty much unchanged regardless of whether Im using the 386 or 686 kernels.  This is in Dell Inspiron 1000, 1100 and 9300.

With the 686 kernel, the processor is definitely working harder, and the UI tends to lag a bit.  Processor at idle is bouncing between 30% and 50% give or take.  This is again with all 3 machines.  However in each case, the heat ranges seem unaffected.

Thanks for the info! :)

---

### Post by zahidism on 2006-06-22
the point was my idle of my 600m at 43 degrees in windows whereas the idle in ubuntu is 50 degrees which is confusing.  heat = bad.

---

### Post by NiksaVel on 2006-06-22
I'm not much of a hardware expert and am even newer to the whole linux experience, but I would like to point out once again that the hottest part of my laptop is the battery part...  while proc usually hangs constantly at 50-55 C (which I consider okay)...

And also the strange part that the battery part gets warmest when the computer is connected to AC and not charging the battery...


The article about that dell laptop exploading game me more to think about this as I believe that the most likely part to blow up is the battery if there is something wrong with it...

---

### Post by NiksaVel on 2006-06-22
I get the following from 
cat /proc/acpi/processor/CPU0/power


active state:            C2
max_cstate:              C8
bus master activity:     88844484
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00244378]
    C3:                  type[C3] promotion[--] demotion[C2] latency[085] usage[00000000]




if I was following this thread right, my comp never ever went to C3 stage...  why, how do I solve this?....

it's a Pentium M at 1.6

and monitors show it's at some 10% usage or 600MHz during idling...

---

### Post by vayde on 2006-06-22
Niksavel: Good question.  Im not having that problem, but Ill be interested in the answer.

faswad: what's the time frame on that output? 
(cat proc/acpi/processor/CPU1/power)  Is it since the last reboot?

---

### Post by TheCross on 2006-06-22
[QUOTE=morgengenuss]that's the output of my /proc/acpi/processor/CPU0/power:
```
active state:            C3
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[01211363]
   *C3:                  type[C3] promotion[--] demotion[C2] latency[057] usage[05442924]
```


actually this looks quite good. (note: i gave dell a call today and they said that temps up to 70°C are normal for the intel dual core 2400 [1,8ghz].)

"acpi -t" gives me (right now; only firefox is open. nothing else going on):
```
Battery 1: charged, 100%
Thermal 1: ok, 49.0 degrees C
```

one more thing: my sensors couldn't be detected. that's the reason i only have the cpu-temperature and can't really control the fan activity (furthermore, my /proc/acpi/fan dir is empty but i assume that's what it's supposed to be...)[/QUOTE]


Holy mother of GOD! Mine runs in state 1 3 times as much as 3! Something must be wrong.  Sadly she shut down because of overheating again. :(

---

### Post by faswad on 2006-06-22
For those having power state issues:

Please see this [article]("http://acpi.sourceforge.net/wiki/index.php/WhyMyCxPowerStateIsNotUsed?PHPSESSID=5195f08a2c678bf4b697b6ac03663f62")

The article seems to mention that certain USB controller are constantly polling for the presence of new hardware and therefore keep the cpu from going into C2 or C3 state. I suggest some of you look at the article and see if it helps.

TheCross: yes your CPU being in C1 most of the time is probably not a good thing. Please see if the article above helps.

Vayde: I usually just let my notebook sit for about 10 minutes while in linux and then check the idle temp and check the power state levels.

---

### Post by vayde on 2006-06-22
[QUOTE=faswad]

Vayde: I usually just let my notebook sit for about 10 minutes while in linux and then check the idle temp and check the power state levels.[/QUOTE]

I follow you there, I did pretty much the same.  Luckily my machine spends most of its time at C4.

What I meant was: the number listed after the power state, I assume it's some sort of time factor.  

When did the counter for any given state start at 0?  Does it refresh on every reboot?  Is it counting from the beginning of time?

In the following:
active state:            C4
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[03542520]
    C3:                  type[C3] promotion[C4] demotion[C2] latency[085] usage[01528196]
   *C4:                  type[C3] promotion[--] demotion[C3] latency[185] usage[04910225]

it's 04910225 WHATS since WHEN spent in mode C4?

Thanks again, I appreciate the info.

---

### Post by jmr on 2006-06-23
For explanations of prcessor states, thermal management, why c3 is not being used, etc, take a look at [ACPI4Linux Documentation]("http://acpi.sourceforge.net/documentation/index.html").

João Rodrigues

---

### Post by morgengenuss on 2006-06-23
i think up to now no-one has really answered how to adjust acpi-settings.

if i try something like "echo -n "110:0:90:60:0" > trip_points" (as suggested here: [http://acpi.sourceforge.net/documentation/thermal.html](http://acpi.sourceforge.net/documentation/thermal.html)) i always get:
"bash: trip_points: Permission denied"

(same with sudo echo)

any suggestions?

---

### Post by NiksaVel on 2006-06-23
here's a direct link to the link from post above regarding low usage of c3 state

[http://acpi.sourceforge.net/wiki/index.php/WhyMyCxPowerStateIsNotUsed?PHPSESSID=1ac994c3bb93f371b4ebb399cc24edc1](http://acpi.sourceforge.net/wiki/index.php/WhyMyCxPowerStateIsNotUsed?PHPSESSID=1ac994c3bb93f371b4ebb399cc24edc1)


all I have to say is CRAP, since in my case I really do need USB support and don't plan to manually start and stop it every time I use a mouse or a usb stick...


btw... can anyone approximate the battery lifetime difference when using mostly c2 compared to c3?

---

### Post by morgengenuss on 2006-06-23
sorry to keep digging out new stuff, but what do you say to this:


> Any ACPI (advanced configuration and power interface, the successor of
	APM) kernel option *DOES NOT WORK* and is almost always the cause of
	random crashes.  APM works completely - so use it. [It can be checked
	by invoking the battery status with - - but don't forget to
	sync before this test. With ACPI functionality Linux *WILL* crash.]
	Also, some have reported that APIC (advanced programmable interrupt
	controller; note the difference, it's not ACPI) support (found in the
	Processor-Types menu) has caused conflicts and problems with random
	crashes & power management.

	NOTE: Dr. Jochen Braun notes that, from his experience, on the
	Inspiron 2500, ACPI works while APM is what causes crashes.
source: [http://www.whacked.net/ldl/faq/](http://www.whacked.net/ldl/faq/) (6.  Power management)

so, since this was started by a dell inspiron 9400 user: does acpi just not really work on dell laptops (or did i get something completely wrong)?

---

### Post by Devrdander on 2006-06-23
I just got my 9400/e1705 this week and I was going to load Dapper this evening I'll let you know how I fair aswell.

Specs:
DuoCore 2400
2gb DDR 667
100gig SATA HD
Nvidia 7900GS (w/ 1920x1200 display)
SB Audigy
Bluetooth/Wireless
DVDRW

---

### Post by vayde on 2006-06-23
[QUOTE=morgengenuss]sorry to keep digging out new stuff, but what do you say to this:



source: [http://www.whacked.net/ldl/faq/](http://www.whacked.net/ldl/faq/) (6.  Power management)

so, since this was started by a dell inspiron 9400 user: does acpi just not really work on dell laptops (or did i get something completely wrong)?[/QUOTE]

I have had problems with APIC.  Basically if I'm running on battery, and I'm too impatient, and I hit enter as soon as the grub screen comes up I will end up with 'APIC not syncing' and  kernel panic.  But if I let it timeout and boot automatically (timeout is set to 5 seconds) it's fine.  

That was a problem in Breezy anyway, I haven't tested it in Dapper yet.  I'll check on next reboot. EDIT: Problem seems to be solved.  I haven't been able to make it break under dapper

It may just be the Inspiron 9400's with their duo core processors that are having problems, as I have had no real issues with inspiron 1000, 1100, and 9300.

---

### Post by crashtest on 2006-06-23
I reinstalled on my Inspiron 9400 last night.  So far I'm sticking with the i386 kernel which I've heard runs cooler.  (I didn't buy the notebook for the Core Duo, but rather for the huge screen and Nvidia card.)

Another thing just occured to me - the day I burned up my hard drive, I had been messing around with XGL / Compiz for quite a while.  This must make the GPU run very hot, right?

So the bottom line for me is this:  I bought a "hot rod" notebook with Core Duo and 256 MB video card, and I need to run single CPU only and no fancy eye-candy....  :-(  At least it's staying cool so far.

---

### Post by rozojc on 2006-06-23
Sorry if this sounds completely naive... How do you turn throttling on?
I have an Acer laptop and it also seems to go a little bit hot when idle, 
 I tried this:
rozojc@dorothy:~$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no


It's a Sempron processor, does that even have throttling? And if it has, how do you turn it on? I have no idea...

---

### Post by zahidism on 2006-06-23
Pentium M 2.0 Ghz on a dell 600m

active state:            C2
max_cstate:              C8
bus master activity:     220401ff
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[01049190]
    C3:                  type[C3] promotion[C4] demotion[C2] latency[085] usage[00000112]
    C4:                  type[C3] promotion[--] demotion[C3] latency[185] usage[00000000]

grr...that's not good is it.  never goes into C3.  what's up with my busmaster activity?

---

### Post by jmr on 2006-06-23
crashtest,

Earlier today I checked a friend's Asus laptop, with a Core Duo (but intel graphics) and both CPUs seemed to run pretty idle (2-3%) with the -686 kernel.  I didn't work more than 10-15 minutes with it, but temperature didn't rise above 50 C.

I reported this in [bug#30570]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30570").

---

### Post by jmr on 2006-06-23
[QUOTE=morgengenuss]sorry to keep digging out new stuff, but what do you say to this:



source: [http://www.whacked.net/ldl/faq/](http://www.whacked.net/ldl/faq/) (6.  Power management)

so, since this was started by a dell inspiron 9400 user: does acpi just not really work on dell laptops (or did i get something completely wrong)?[/QUOTE]
That info seems to be a bit dated.  Maybe you can try to contact the author to see what he has to say about this.

My experience with ACPI began a year ago when I bought my laptop, and it has endured 3 versions of Ubuntu, from 5.04 (briefly), through 5.10, to current 6.06.  The first two versions did not boot correctly unless I disabled ACPI.  I had to customise the DSDT (a table in the ACPI firmware) to make it work.  6.06 worked right away.  I have also noticed improvements in the detection of special keys, wireless support and other stuff.  All of this in one year.  So, a lot of info in that page may no longer aply.

Check the LaptopTestingTeam pages in the Ubuntu Wiki.

---

### Post by morgengenuss on 2006-06-23
@ vayde: thanks. maybe the dual core is the reason, but since other laptops seem to work ok i would rather say it's the sensors (that i haven't been able to detect correctly up to now).

@ jmr: thanks a bunch. i'll try to contact the author. and regarding the laptop-testing-wiki: already had a look there, nothing regarding my problem.

and actually thanks to all of you, who are trying to solve this problem (whatever it is).

---

### Post by Devrdander on 2006-06-24
I installed a fresh copy of Dapper 6.06, upgraded to the 686 (2.6.15-25) kernel, and so far no problems.  I did notice imediately after installing Dapper the first of the 60 or so updates it downloaded was ACPI-SUPPORT 0.85.

I'm idling between 29-30C and things are running smoothly.

---

### Post by rozojc on 2006-06-24
Sorry to say this again, but I noticed not only I asked this but another user and still no answer... Can someone please tell me how can I turn processor throtling on?
I have the ACPI support mentioned in the previous message, but idle I'm running at 48 degrees, which is way higher than the 20 something other people are reporting...

---

### Post by Devrdander on 2006-06-24
First off, dont  compare it to other users, each laptop is different, I would suggest comparing it to how your system runs under its OEM supported OS (Windows).  

Just check and make sure in your Synaptic Package Manager that you have:
acpi, acpid, and powernowd

do a: ps -aux | grep powernowd 
That will verify your powernowd is running.

To see your available modes:
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors (or scaling_available_freq to see the clock speeds)

To see your cur freq:
cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq 

To see your time in each state:
cat /sys/devices/system/cpu/cpu0/cpufreq/stats/time_in_state

If you have a dual core processors do the same for cpu1.

powernowd (which is what ubuntu uses by default) doesnt depend on APM or ACPI from my understanding.

---

### Post by crashtest on 2006-06-30
OK - here's something new.  (At least I haven't read about it anywhere)

My Inspiron 9400 idles 10 degrees hotter when using the proprietary Nvidia drivers.  I installed all the multimedia stuff yesterday using Easy Ubuntu, so whatever driver is being installed with yesterdays version of the script is the one I've got.  Idle temperature is 40 degrees.  After switching back to the "nv" driver I get an idle temperature of 30 degrees or less.  This seems like a huge difference for a system at idle.  Has anyone else seen this?

---

### Post by m94mni on 2006-06-30
[QUOTE=faswad]
Dell Inspiron 9400\E1705,
Intel Core Duo
17" UWXGA screen,
**NVIDIA 7800GS.**[/QUOTE]

Going off in a different direction, it's well known on some Dell boards that the 7800GS which was in the 9400 had **serious** heat issues, and was therefore thrown out by Dell within two months of the initial release, never to return.

They now offer the 7900 as replacement to those who have heat issues (which does not have those issues at all).

faswad, I believe you simply had a bad GFX card. Make sure you now have the 7900, and you should be fine.

---

### Post by dmb on 2006-07-02
I have a dell instirot E1705 Intel core duo 2.1 ghz 17 inch nvidia 7900 , and my cpu ranges between 30 and 50. Basically, once the temp gets up to 50, the fan turns on until it goes down to 29, where it turns off. Is this normal? Also, the GPU gets really hot, at like 72 c, is that normal? I just want to know if everything is OK.  Also, the area where it says dell on the LCD is very hot. Is that ok? Is that normal? 

I do a lot of compiling an am going to me moving to gentoo soon so i need to know if this is ok.

---

### Post by m94mni on 2006-07-02
[QUOTE=dmb]I have a dell instirot E1705 Intel core duo 2.1 ghz 17 inch nvidia 7900 , and my cpu ranges between 30 and 50. Basically, once the temp gets up to 50, the fan turns on until it goes down to 29, where it turns off. Is this normal? Also, the GPU gets really hot, at like 72 c, is that normal? I just want to know if everything is OK.  Also, the area where it says dell on the LCD is very hot. Is that ok? Is that normal? 

I do a lot of compiling an am going to me moving to gentoo soon so i need to know if this is ok.[/QUOTE]

The CPU ranges certaily seems OK. The GPU at 72 seems a bit hot unless you are gaming... but certainly not dangerous (when you reach 90C or more you have problems).

The heat on the Dell logo is probably the LCD lamp, not much you can do about it...

You should have *no* problems compiling gentoo if your CPU temps behave so nicely.

---

### Post by dmb on 2006-07-03
Just another quick question. Are the fans in the E1705 controlled via the operating system or the computer/bios itself? If via the operating system, is it possible to control what temparatures click on that fans?

---

### Post by Jhodytropical on 2006-07-03
Hi,

 I think I have the same Fan Problem since I installed Ubuntu my on laptop (Gateway 7326 GZ - Pentium 4; 3.6GZ etc.
I do have a 'Sensor limit failed' at Startup also. I wonder if there is a way to fix that and I am kind of afraid not to ruin the Laptop altogether.

---

### Post by vayu on 2006-07-03
[QUOTE=faswad]Well ACPI was shown to be "OFF" in Kubuntu. Once ACPI was turned on from the Power and Laptops interface, the temperature of CPU seems to have stabilized around 30C (compared to 50 before).[/QUOTE]

Does anyone know a way to set ACPI and CPU Throttling from the command line rather than from KDE?

---

### Post by m94mni on 2006-07-03
[QUOTE=dmb]Just another quick question. Are the fans in the E1705 controlled via the operating system or the computer/bios itself? If via the operating system, is it possible to control what temparatures click on that fans?[/QUOTE]

The BIOS does the controlling, but I think you an override it... Try installing the i8kutils and i8kfan, or the gkrellm-i8k plugin to gkrellm. You also would need to load the i8k kernel module (I think with param force=1). It does work for me, even though I find that the BIOS mostly does a good job itself.

---

### Post by dmb on 2006-07-03
The i8k plug for gkrellm- does that control fan speed? Also, how do you get that module to start up automatically? I don't think you can hae force=1 in /etc/modules .

---

### Post by m94mni on 2006-07-03
[QUOTE=dmb]The i8k plug for gkrellm- does that control fan speed?[/QUOTE]

IIRC, yes it does, and it allows for manual control as well (left click).

---

### Post by doog on 2006-07-03
Very interesting thread here. ATI just released  their driver with an event process that will monitor the GPU temp and throttle down the GPU frequency to bring the temp to 'acceptable' levels. Intel is already doing this with their CPUs so soon, we can expect HP/Compaq, Dell, Sony, Apple, etc touting super fast CPUs and GPUs but when in use, actual 'performance' will probably be far less than advertised.

I already see this in how Cable Modems work. They'll burst tons but try to stream and bang, you get throttled back.

Maybe it's getting to be the time for externally attachable heat pipe cooling systems for laptops.

---

### Post by edemark on 2006-07-03
I just cannot get it well I have a ho nx9010 that heats up and switches off around 72 c. I partly suppose that is a dirt issue as well though this switch of issue never happened with me while using suse. First i get it with hoary than get more in breeze (had to stop playing games) and now it happens in drapper quite oftenly and without any apparent reason. 
I got these to the tests:
mark@supernova:~$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no
mark@supernova:~$ cat /proc/acpi/processor/CPU0/power
active state:            C2
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00353260]
   *C2:                  type[C2] promotion[--] demotion[C1] latency[099] usage[02520412]

I cannot test my machine with windows as i do not have one on my laptop and just for this testing i would not isntall one.

From the other side I would really like to solve this problem as i do not want to destroy my worktool.

I would love to find some answers but so far no luck
could not even find out how to enable Throttling

Any help would be usefull as today it switched of twice (my only luck that open office is able to recover my works)

thanks in advance

pd I had to disable all screensaver because it almost switched off my machine again 
pls help me have screensaver please

---

### Post by the_blue_pill on 2006-07-04
Thought this might be relevant: I downloaded the xorg-driver-fglrx module and switched the xorg.conf display mode from radeon to fglrx in my dell 8600. 

I haven't made a rigorous audit but since then the laptop runs noticeably cooler and the fans activate a lot less. Perhaps direct rendering by the video ram reduces monitor/cpu load? So if you have an fglrx compatible card you might try that. Don't forget to backup your xorg.conf first!

---

### Post by cheuschober on 2006-07-04
If anyone's curious... I've been idling at 64C on my Toshiba 2.8 Celeron based system (intel 855)... and 15 minutes of load takes me up to 83C.

This is only symptomatic of linux. Any geniuses know what the quick fix is to just get the fans to run more often or throttle the cpu?

---

### Post by morgengenuss on 2006-07-04
@ doog: are you talking about the [fglrx 8.26.18]("http://ubuntuforums.org/showthread.php?t=204910")?
if yes, i will instantly try to install it...

---

### Post by doog on 2006-07-04
[QUOTE=the_blue_pill]Thought this might be relevant: I downloaded the xorg-driver-fglrx module and switched the xorg.conf display mode from radeon to fglrx in my dell 8600. 

I haven't made a rigorous audit but since then the laptop runs noticeably cooler and the fans activate a lot less. Perhaps direct rendering by the video ram reduces monitor/cpu load? So if you have an fglrx compatible card you might try that. Don't forget to backup your xorg.conf first![/QUOTE]

After my discussions with HP on the Sideport issue with ATI's Linux driver and hearing of how they have had heat issues with video chips, it got me wondering if the Sideport/DRI/3D problem has not been a heat issue and the reason ATI has left this issue broken for so long. Now that it seems they have an event process to help monitor GPU temp and throttle it accordingly, maybe we'll see some performance fixes coming down the pike.

There will come a point where they just can't put THAT much 'performance' in these laptops without heat issues.

---

### Post by doog on 2006-07-04
[QUOTE=morgengenuss]@ doog: are you talking about the [fglrx 8.26.18]("http://ubuntuforums.org/showthread.php?t=204910")?
if yes, i will instantly try to install it...[/QUOTE]

yup, the 8.26.18 driver. Check out what's said about it here:
[http://www.phoronix.com/scan.php?page=article&item=501&num=1](http://www.phoronix.com/scan.php?page=article&item=501&num=1)

---

### Post by insanedc on 2006-07-04
I had overheating problems with my Dell Inspiron 8600. I determined that this was due to the faulty ACPI implementation in the Dell BIOS. My new Asus V6J has had no problems at all. In many machines a relacement DSDT can be compiled to override faulty values in the BIOS. I found out about this after I sold my 8600. Search the net on ACPI and DSDT for more info.

---

### Post by afilonov on 2006-07-05
[QUOTE=NiksaVel]still, I wouldn't mind an easy to use gui program that will show me the temps if I feel like checking them out...  :mrgreen:[/QUOTE]

Try gkrellm. Also, acpi -V gives you current CPU temperature. You might be able to use lm-sensors on some laptops, but be careful! Never user lm-sensors on Thinkpads, you can kill the laptop.

---

### Post by insyzygy on 2006-07-23
I believe I have duplicated this problem twice on my laptop. I have an inspiron 8500 with an nvidia card. About a month ago after installing ubuntu. The display started being corrupt (shaky vertical bars of color) in ubuntu, windows, and even on the bios screen. I ran a dell diagnostic disk and it found an error reading and writing to video memory. Dell kindly replaced the video card and things were fine, for while. Yesterday after only a month the same problem started up and the same error is found during the diagnostic. I run i8kmon and normally the temperatures it reads are around 45 C. I don't think its a problem with the gpu or cpu overheating, they can tell well up to 100 C, it seems they are generating heat which is killing the video ram.


I ran fedora core for around a year with no problem so this is kind of frustrating. Is it certain this is an ubuntu issue? I don't know yet if dell will replace it again but I don't think they will do it a third time.

---

### Post by scameronde on 2006-07-24
Hi,

i had also problems with my Dell Latitude D800, which i think are related to heat. The first time, main memory module A had a defect 6 month after i bought that baby, then one month later memory module B had a defect, then 2 weeks later, the video memory was defect. You should have seen the face of the Dell technician :-)

Oh, by the way: i had the defects running WinXP Pro. After the laptop had been repaired the third time, i decided to switch to Ubuntu 6.06. No problems so far. But it is running Ubuntu only for a few weeks now ...... ;-)

scameronde

---

### Post by insyzygy on 2006-07-24
Interesting. I know that the problem is hardware and will show up in linux or windows (for me it happens at bios sometimes). I'm just wondering if it was really linux that caused it to overheat and actually damage the hardware. Were you funning windows and linux when the problems started or just windows.

---

### Post by xenon2000 on 2006-07-28
> **johnc4510 said:**
> ... but it would contribute to overheating if only one was in use.

This is not true. I have a fair amount of testing experience with the Core Dual Pentium D and Conroe which is now called Core 2 Duo cpus working from within Intel (though with all the cuts, maybe not much longer).

At least for the Intel motherboards, you can choose to run the cpu in 1 core mode. This does not cuase more heat. It also makes no sense that running 1 of 2 cores would cause more heat. Running both cores at 100% will cause more heat that 1 core running at 100%. The clock rate remains the same for each core. So a 2ghz dual core cpu will not run at 4ghz if you put it in single core mode.

Anyways. Like it was mentioned, it sounds like the onboard video got overheated. I have seen this with desktop video cards. And anyone that has overclocked a video gpu has run into this as well.

Sadly Ubuntu video drivers probably did not have the gpu thermal drivers that Dell had installed, if there are special drivers for any specific thermal issues that Dell may have. Especially as Dual Core is still fairly new to laptops. The new Merom (the Core 2 Duo Mobile chip) you will see huge power reductions just like how Core 2 Duo is about 40% more power effecient than the Core Duo cpu. Due to a much smaller die size and all new architecture.

Anyways. Unless Ubuntu developers can find the issue and solve it before you try again, I would stick with Windows with the Dell drivers for now.

---

### Post by wthww on 2006-07-29
THis isnt just a dell issue; i have just set and read this thead (yes the whole thing!) and my cpu tempuatue went from kinda hot 49 C to 58 C and its teifying. Also, to note, not once have my fans come on in ubuntu... (dappr has only been installed for maybe 6-7 hours.) but they did in XP... heres my out puts of  /proc/acpi/processor/CPU0/info and */power

```
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no

```

```

wthww@wthww-laptop:~$ cat /proc/acpi/processor/CPU0/power
active state:            C2
max_cstate:              C8
bus master activity:     200001ff

```

THe laptop does get noticably hotter while on ac, with battery full, and noticably hotter under ubuntu than XP... this is kinda scary. temp at time of this post is : Thermal 1: ok, 60.0 degrees C :| THis is a Hp dv4230us 1.6ghz celeron... shouldnt be getting that hot i think. all that i have open is firefox.

---

### Post by insyzygy on 2006-07-30
Its seems that most people report that for some reason or other their laptops run somewhat cooler in windows. Does anyone know why this would be.
Does windows have built in fan control for laptops? 

There is lots of power management for the cpu built into the linux kernel, is there something comparable for gpu's in either windows or linux?

Also does anyone have any experience with different distributions running cooler or hotter. Does fedora core run cooler than debian. I really need to run linux on that laptop since I run it on all my other systems. I think I might try fedora on this system, I had run it for the last year (fedora core 3) with no problem whereas ubuntu killed a new video card in a month (I'm still running ubuntu on all my other systems though).

Dell doesn't believe the video card is overheating. Their argument was that since the cpu wasn't overheating, the video card couldn't be sustaining thermal damage. The tech I called is convinced that the month old video card is defective, in the exact same way as the previous one it replaced . . ., at least they will replace it again.
Its actually kind of funny, if the problem was only happening in linux they would say, oh we don't support linux. But since it occurs even at bios (the video is messed up in the bios screen), they say oh its not operating system we'll just replace the hardware.

---

### Post by finn on 2006-07-31
Ok, I've done a bit of digging around, and it seems the reason people are seeing overheating Dell laptops is that the DSDT data is not compliant with the ACPI standard (Microsoft's way of interpreting the data is less than rigorous, and thus sloppy work by OEMs gets through to consumers, while Linux expects the DSDT to be correct).

Here's my symptoms:
Dell Inspiron 9400 with a centrino duo t2400
geforce 7900 gs (unrelated to the heat issue)
Dual boot windowsxp/ubuntu

In windows the two fans come on occasionally and keep the temperature under control. In Ubuntu they don't and the idle temp sits at about 40 to 45, under load starts approaching 55.  Nvidia core temp reported at 74 (slows down at 102 according the nvidia-settings).  In windows idles at about 30 to 35, under load sometimes gets to 40 but then cools down again.

In dmesg I found the following interesting message:
 dmesg |grep DSDT
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 INTL 0x20050624) @ 0x00000000
[17179571.364000] ACPI: Looking for DSDT ... not found!

That can only be bad.  DSDT is how the bios tells the OS how to run the fans etc (well, that's what I gather from my reading so far).

Bad DSDT's are a known problem, here are some sites to help you hammer Dell's customer support desk:  [http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)
[http://www.suseforums.net/index.php?showtopic=13893&st=0](http://www.suseforums.net/index.php?showtopic=13893&st=0)
[http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php)

I don't expect dell will do much besides tell you to run Windows.  I'm going to play around and see if I can't get my DSDT to work under linux. (I'll post updates, but don't expect anything until the weekend cos I'm busy at work this week)

finn

Edit:
ok, so while i'm working on this, here's how to get those fans spinning anyway:
  sudo apt-get install i8kutils
  sudo modprobe i8k force=1

run i8kmon,

the number is your system temp, the two boxes cycle through fan speeds (couple of seconds delay, hit them both until they go on 1 and you should be ok when not under heavy load).  I can't remember which repository i8kutils was in... probably multiverse or universe.

---

### Post by Mach1US on 2006-07-31
I`v ran ubuntu for days with no diffrence to xp and no heat issue.
I have dell inspiron 6000 p730m 1.6mhz with integrated intel video so it may be driver problem with more advanced cards rather then ubuntu itself.

---

### Post by punkybouy on 2006-07-31
I say go ahead an use it.  As long as its under warranty Dell will replace no matter how many times it breaks.  I am not a big fan of being a beta tester which is what you are with the Core Duo.  I suspect its a hardware issue that Dell will address at some point.  Its too early for Vista stuff anyway.  Get Dell to replace it the next time around with a nice P4 or even AMD.  Tried and true hardware. It will also give the Linux community time to write software.

---

### Post by vayde on 2006-07-31
Hey guys, I don't know if this is a useful option for anyone, but Ill throw it out there just in case.  

I have been following this thread mostly out of paranoia, my Inspiron 9300 must have been the last of the good ol' single processors thrown out by dell.  It runs kinda hot, but not enough to have caused any damage. (Idles around 50, jumps up to 60-65 under load).

Anyway, as someone pointed out to me earlier in the thread, cooler is better, and I stumbled across the following:

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Setting_custom_temperature_thresholds_for_your_system_fans](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Setting_custom_temperature_thresholds_for_your_system_fans)

I haven't set up mine to run this way automatically yet, but in playing with the fan speeds and settings, I have my box idling at around 37.

Hope that's helpful for someone.

EDIT: I'm now set up to run i8kmon as a daemon on startup.  Fan thresholds are set per my preferences, laptop runs 10- 12 degrees cooler on average.  No more thigh-bake during coding sessions!:D

---

### Post by Galactus on 2006-08-01
I would recommend getting a cooler for your laptop. I just put Ubuntu on my laptop about 2 weeks ago and noticed immediately that the machine was getting much hotter than when I was running Win XP. I went out this weekend and picked up a chill pad by Targus. Has 2 fans in it and works off of USB power. Just set the laptop on it when in use. Works great... Antec also makes something similiar...Good Luck ;)

---

### Post by oliwally on 2006-08-01
> 
Edit:
ok, so while i'm working on this, here's how to get those fans spinning anyway:
  sudo apt-get install i8kutils
  sudo modprobe i8k force=1

run i8kmon,

the number is your system temp, the two boxes cycle through fan speeds (couple of seconds delay, hit them both until they go on 1 and you should be ok when not under heavy load).  I can't remember which repository i8kutils was in... probably multiverse or universe.

This worked well for me on my d820. Fans are spinning niceley (just as a precaution. I didn't have any overheating probs so far)
But the monitor itself doesn't display very nicely - it's very plain and simple. Is it supposed to be like that? There is a way to also run the whole i8kutils through GKrellM (read something like that in Synaptic). There was also a mention of i8k.o kernel module to be installed for gkrellm & i8kutils to work. How is this done? All seems to work when your suggestion is done first.
Finally - Will I need to run your suggestion every time I boot the computer or does it somehow 'stick'?

---

### Post by vayde on 2006-08-01
Here's how I did it:

sudo vim /etc/i8kmon
```

# Run as daemon, override with --daemon option
set config(daemon)      1

# Automatic fan control, override with --auto option
set config(auto)        1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
# These were tested on the I8000. If you have a different Dell laptop model
# you should check the BIOS temperature monitoring and set the appropriate
# thresholds here. In doubt start with low values and gradually rise them
# until the fans are not always on when the cpu is idle.
set config(0)   {{- 0}  -1  40  -1  45}
set config(1)   {{- 1}  40  50  40  50}
set config(2)   {{- 2}  45  55  45  55}
set config(3)   {{- 2}  50 100  50 100}

# end of file

```

That will set up i8kmon to run as a daemon.  Put whatever temp thresholds you like.  The above is slightly modified from the link I posted previously.

To make it load at startup:

sudo vim /etc/init.d/i8kmon
```

#!/bin/sh
#
# i8kmon        initscript to control i8kmon daemon
#               This file should be placed in /etc/init.d,
#               and linked to /etc/rcX.d directories using command update-rc.d
#
# Author:       nanotube <nanotube@users.sf.net>
#
# Version:      @(#)i8kmon  1.5  31-May-2006  [email]nanotube@users.sf.net[/email]
#

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="Hardware Monitoring for Dell Inspiron daemon"
NAME=i8kmon
DAEMON=/usr/bin/$NAME
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

# Read config file if it is present.
#if [ -r /etc/default/$NAME ]
#then
#       . /etc/default/$NAME
#fi

. /lib/lsb/init-functions

#
#       Function that starts the daemon/service.
#
d_start() {
    start-stop-daemon --start --quiet --background --make-pidfile --pidfile $PIDFILE \
        --exec $DAEMON
}

#
#       Function that stops the daemon/service.
#
d_stop() {
    start-stop-daemon --stop --quiet --pidfile $PIDFILE
}

case "$1" in
  start)
    log_begin_msg "Starting $DESC: $NAME..."
    d_start
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Stopping $DESC: $NAME..."
    d_stop
    log_end_msg $?
    ;;
  restart|force-reload)
    #
    #   If the "reload" option is implemented, move the "force-reload"
    #   option to the "reload" entry above. If not, "force-reload" is
    #   just the same as "restart".
    #
    log_begin_msg "Stopping $DESC: $NAME..."
    d_stop
        log_end_msg $?
    sleep 1
        log_begin_msg "Starting $DESC: $NAME..."
    d_start
    log_end_msg $?
    ;;
  *)
    echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
    exit 1
    ;;
esac

exit 0
#End of file

```

Make sure to set /etc/init.d/i8kmon executable!  (Caused me a bunch of head scratching).

then run the following:

sudo update-rc.d i8kmon defaults

After that, you should be set, though you will probably want to play with the temp thresholds in /etc/i8kmon till it suits your fancy.

---

### Post by CGW on 2006-08-01
> Edit:
ok, so while i'm working on this, here's how to get those fans spinning anyway:
sudo apt-get install i8kutils
sudo modprobe i8k force=1

run i8kmon,

the number is your system temp, the two boxes cycle through fan speeds (couple of seconds delay, hit them both until they go on 1 and you should be ok when not under heavy load). I can't remember which repository i8kutils was in... probably multiverse or universe.Will the fan speed still change from high to low using this method?  Or do we have to manually change it?

---

### Post by vayde on 2006-08-01
> **CGW said:**
> Will the fan speed still change from high to low using this method?  Or do we have to manually change it?

I don't know for sure, but changing them *seems* to stick the fans in that state until something else changes them.  

At least, when I bumped them up while working the processor (the hufo's tunnel screensaver),and then shut down the program that was causing the load, the fans shut down.  I did not monitor changes over a long time though, I just went ahead and got the daemon version running.

---

### Post by CGW on 2006-08-01
I've never thought twice about any of this until I read this thread.  I have a Dell 6000 and have no overheating probs.  I don't notice any heat difference between WinXp and Ubuntu.  I get no error messages from dmesg.  My laptop's temp pretty much hangs around 35-40C.  Should I even worry about this at this point?

Also, I did run your code through the terminal.  So would that permanantly change any 'factory' settings that I 'wasn't' having trouble with in the first place?  You read all of this and start freaking out.  I don't want to cause a problem when there was no need to ever worry in my case.

---

### Post by vayde on 2006-08-01
> **CGW said:**
> 
Also, I did run your code through the terminal.  So would that permanantly change any 'factory' settings that I 'wasn't' having trouble with in the first place?  You read all of this and start freaking out.  I don't want to cause a problem when there was no need to ever worry in my case.

Assuming I understand what is going on (which may be a big assumption I grant you) configuring i8kmon will only affect it's own settings.

Installing i8kutils does not seem to install the kernel module- you seem to have to do that manually by adding it to /etc/modules. 

Once i8k is loaded, whether automatically or by the command line, i8kmon can control your fans, whether by pushing buttons on it's crude display, or automatically by setting up the conf file.

I do not believe you are actually 'changing' anything fundamental on the machine, you are just giving it different orders.  If you found you didn't like what was happening, you would need to remove the kernel module, and then remove the script from /etc/init.d (and presumably update the rc.d's).  Then your system would go back to using whatever it's using now to control your fans.

Someone please correct me if I have this wrong.

---

### Post by insyzygy on 2006-08-01
You are correct, installing i8kutils doesn't mean i8k is active. You first have to either modprobe i8k manually or edit /etc/modules and add it to make it load automatically. Even then the fans still won't be controlled unless you run i8kmon either manually or as a daemon in auto mode (so it controls them automatically). 

After dell replaced my video card (for the second time) I set i8kmon to have both fans always on at the lowest level and then go full blast if the temp jumps over 50. At the lowest level the fans are fairly quiet so this isn't bad. Before I did this the temp was idling at around 50 or more. Now  the temp is maintained at between 36 and 42 under normal load (browsing and idle). I don't know if this is necessary but I think the fans can take the abuse of being on constantly better than the video card is able to take higher temps.

Note to get i8kmon to control the fans without user interaction you have to run it with the -a option or edit the configuration file so it automatically controls the fan, for a while I thought it was controlling the fans when it was just monitoring them.

I also noticed that configuring the frequency scaling to always run at half speed (no matter what the load is) keeps the temperatures down a lot as they only seem to jump when the processors goes to its maximum frequency. This kind of sucks since whats the point of having a 2.4 ghz processor if you can only run it at 1.2 ghz without burning things up, but oh well.


On a unrelated note, I was mystified why my video card failed a month after being replaced for the same problem, but I realized it was a refurbished part. It doesn't surprise me so much that it failed so quickly. Maybe it only overheated the first time and the refurbished card was just crap.

---

### Post by CGW on 2006-08-01
This is quite odd.  I've been running Dapper on my Dell 6000 laptop since the UPS man dropped it off 6 months ago and I've never had any heat issues.  :confused:

---

### Post by oliwally on 2006-08-03
> Here's how I did it:...

Thank you vey much for all that. 
Should I later decide to reverse all that, would I simply remove the two added i8kmon lines/files?
Would I have to somehow reverse the "sudo update-rc.d i8kmon defaults"?

---

### Post by oliwally on 2006-08-03
> Here's how I did it:...

Thank you vey much for all that. 
Should I later decide to reverse all that, would I simply remove the two added i8kmon lines/files?
Would I have to somehow reverse the "sudo update-rc.d i8kmon defaults"?


Edit
ooops...sorry about double post - had computer issues.

---

### Post by vayde on 2006-08-03
> **oliwally said:**
> Thank you vey much for all that. 
Should I later decide to reverse all that, would I simply remove the two added i8kmon lines/files?
Would I have to somehow reverse the "sudo update-rc.d i8kmon defaults"?

Yes.  Take a look at the man page (man update-rc.d) and it lists a 'remove' option.  

Mind you, I haven't tried removing it, and probably won't because I'm happy with how its working on my system, but theoretically you would use: 'sudo update-rc.d i8kmon remove' to pull it from all the  init scripts.

---

### Post by insyzygy on 2006-08-03
I'm curious what settings people using i8kmon are using. When have you set your fans to do on and what temperatures do you report.

I have an inspiron 8500. I have both fans set to be on all the time at the lowest level (fairly quiet). The fans go full blast if the temp rises above
46C. The average temp after being on for a while seems to be 41C on both the cpu and gpu.

---

### Post by oliwally on 2006-08-03
I have also just found that gkrellm with the i8k plugin is a very tidy option for controlling the fans automatically or manually. All installed with synaptic and works very well on my d820. This then allows for fan speed adjustment through a nice gui (if you dont mind having gkrellm displayed on your desktop). Just have to remember to put make i8k start at boot:

In /etc/modules put the line:

i8k force=1

---

### Post by vanilla.gorilla on 2006-08-03
I just got my new Dell 1505 T2400 and have not noticed this problem.  I had it on for a few hours to see how hot it might get. Seemed a bit hotter then when I ran XP.  HOWEVER, After I rebooted it into Ubuntu again the color was kinda messed up.  I waited for about 2 minutes and rebooted into Ubuntu again and it was back to normal. 

Obviously I need to get those fans spinning from what others said in this thread, but was my computer damaged? Is there even a way to tell?

Thanks for the help!

---

### Post by insyzygy on 2006-08-03
Someone else had mentioned that dells often have defective DSDT's. I just did a 

```
dmesg | grep DSDT 
```

and found the wonderful line

```
  ACPI: Looking for DSDT ... not found! 
```

I found this page about DSDT's 
[http://acpi.sourceforge.net/dsdt/index.php]("http://acpi.sourceforge.net/dsdt/index.php")

I guess they are suppose to encode system information so the OS can manage acpi but many manufacturers can't actually followed the specification correctly (cough cough dell cough cough).

Has anyone played with fixing these, supposedly you can modify them.

I'm not sure if this is really the problem as I found the same line running dmesg on a gateway laptop that has had no overheating problems.

---

### Post by hardyn on 2006-08-04
any official resolution on this before in install on my notebook?

---

### Post by vayde on 2006-08-04
I get the same 'not found' with DSDT.  Haven't messed with it though.  Better fan control was all I needed.

---

### Post by hardyn on 2006-08-04
finding same thing with P-M, cooling does a resonable job of keeping things in check, but the CPU load meter bouces all over the place with the 686 kernel.  the 386 settles down nicely at 3% usage when idle and actully have better video performance with 386 kernel?!?!

gotta be something up with the 686 kernel.

---

### Post by vayde on 2006-08-04
It's a bug with SMP.  If you check earlier on this thread some people were discussing it.  Personally Im sticking with the 386 for a while

---

### Post by incandenza on 2006-08-04
> **vayde said:**
> It's a bug with SMP.  If you check earlier on this thread some people were discussing it.  Personally Im sticking with the 386 for a while

There's a new kernel that was just released today that contains some bugfixes for this.  You might want to try it out.  I was having problems with the 686 kernel (strangely high load average, keyboard input laggy, etc.), and this one is a lot better.

The version is 2.6.15-26.46.

Here's the bug:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557")

and here's the changelog that mentions it:
[http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-source-2.6.15/linux-source-2.6.15_2.6.15-26.46/changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-source-2.6.15/linux-source-2.6.15_2.6.15-26.46/changelog")

---

### Post by gesho on 2006-08-04
i8 package working fine on my dell when loaded with insmod from command line.

but when included in /etc/modules (with all the above instruction about running i8kmon as daemon) I am getting 
0%-volume flash screen when KDE loads and can't increase master volume by any means.

any clue about this conflict?

appreciated :)

---

### Post by vayde on 2006-08-04
> **incandenza said:**
> There's a new kernel that was just released today that contains some bugfixes for this.  You might want to try it out.  I was having problems with the 686 kernel (strangely high load average, keyboard input laggy, etc.), and this one is a lot better.

The version is 2.6.15-26.46.

Here's the bug:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557")

and here's the changelog that mentions it:
[http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-source-2.6.15/linux-source-2.6.15_2.6.15-26.46/changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-source-2.6.15/linux-source-2.6.15_2.6.15-26.46/changelog")

Cool!  Ill give it another try, thanks!

EDIT: Works like a charm!  Processor idles at 0% most of the time, jumping to 5% occasionally.  Temps 40 to 42 at idle.  Processor load pegged at 100% and fans locked at full bore until I recompiled fglrx for the 686 kernel, but I guess that's to be expected.

---

### Post by ethan961 on 2006-08-04
Hey,
Is there anyone here with an AMD proc? If so, what are your temps at idle and working hard? This might be something with how Ubuntu treats Intels vs AMD. Im not a linux expert so I may be wrong, as this is just a guess.
Hope I can help!

---

### Post by finn on 2006-08-04
Just an update on my adventures with DSDT decompiling with my inspiron 9400.  It may be that the "Looking for DSDT ... not found!" message is not actually that bad (seems to be that the initrd does not contain a custom DSDT, rather than that the kernel cannot find the DSDT in the bios), and the /proc/acpi filesystem seems to have most of information I expect to find there.  However, the Dell DSDT is tailored towards windows platforms, with great lines such as these:
```
    Name (W98S, "Microsoft Windows")
    Name (NT5S, "Microsoft Windows NT")
    Name (WINM, "Microsoft WindowsME: Millennium Edition")
    Name (WXP, "Windows 2001")
    Name (WLG, "Windows 2006")
```
It seems the bios is all ready for Vista (2006?  teehee)  Interestingly default behaviour of the kernel in the recent past is to send the string "Microsoft Windows XP" to the bios to identify itself as an ACPI/DSDT aware OS, but the dell seems to to expect "Windows 2001" instead.  You can change what the kernel sends by using the boot option acpi_os_name="Windows 2001" (for example), however none of those strings I found in the DSDT seemed to make any difference to the fan control.  It seems Dell are relying on non-bios fan control in windows to keep temperatures nice and cool.  The DSDT file under /proc decompiles with the intel ASL decompiler, and recompiling the file only gives one remark:
```
iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20051216 [Jan  9 2006]
Copyright (C) 2000 - 2005 Intel Corporation
Supports ACPI Specification Revision 3.0

dsdt.dsl  3318:                     Return (Package (0x00) {})
Remark   3069 -    Effective AML package length is zero ^

ASL Input:  dsdt.dsl - 4359 lines, 131739 bytes, 1425 keywords
AML Output: DSDT.aml - 13639 bytes 546 named objects 879 executable opcodes

Compilation complete. 0 Errors, 0 Warnings, 1 Remarks, 531 Optimizations
```
And this isn't too dangerous from what I can gather.  Hmm. ... well, for now I'm just using the i8kmon stuff posted by others in the last few pages, and have no worries about permanent damage to my laptop, though I am still annoyed the bios control of fans doesn't seem to be very good. perhaps a bios update in the future will fix it.

---

### Post by vayde on 2006-08-04
Wow!  Thanks Finn!

---

### Post by gesho on 2006-08-05
**vayde, incandenza**

> Here's the bug:
 [https://launchpad.net/distros/ubuntu....15/+bug/30557](https://launchpad.net/distros/ubuntu....15/+bug/30557)
 
 and here's the changelog that mentions it:
 [http://changelogs.ubuntu.com/changel...6.46/changelog](http://changelogs.ubuntu.com/changel...6.46/changelog)

how do you implement these bug fixes? do you wait till they are somehow included in repositories?

and how this numbering *-26.46 work? 46 is the number of patch? how do you know if you implemented it or not?

what are those keys people talk about in change log? 

I searched wiki and launchpad a bit for this but couldn't figure any guide

---

### Post by vayde on 2006-08-05
As far as I know, the fix is in the new version of the kernel.  In my case, I just installed it from the command line (sudo apt-get install linux-image...686 linux-restricted-modules...686) and everything went fine.  

If there is more to do than that, Im lost.  The original problem that caused me to downgrade to the 386 kernel doesn't seem to be an issue anymore.

---

### Post by incandenza on 2006-08-05
> **gesho said:**
> **vayde, incandenza**

how do you implement these bug fixes? do you wait till they are somehow included in repositories?


Those changes are already in the currently released kernel.  If you just update to the latest version of linux-image-686 (or whichever package is appropriate) you will get it.

If you do 'dpkg -l | grep linux-image' you can see what version you have.  2.6.15-26.46 is the full version number, but the '.46' part doesn't show up most places (uname -a, etc.)

---

### Post by drewdavis1 on 2006-08-05
OK, here is a question for you. When I do a: ```
cat /proc/acpi/processor/CPU0/power
``` i get the following:

active state:            C2
max_cstate:              C8
bus master activity:     08410840
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[01084093]
    C3:                  type[C3] promotion[C4] demotion[C2] latency[085] usage[00000000]
    C4:                  type[C3] promotion[--] demotion[C3] latency[185] usage[00000000]

Here is the output from the info just in case:

processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes


Notice that only C2 is being used. Now, my processor throttling is working correctly according to the Frequency Scaling Monitor in GNOME but, things just seem a bit slower that they did in MS XP. Any ideas?

---

### Post by Tsukino on 2006-08-06
I'm a pretty fresh newbie in the ways of Linux, but my laptop is also generating a fair bit more heat than it would in Windows.

dmesg | grep DSDT
[17179569.184000] ACPI: DSDT (v001 GATEWA 450ROG   0x20031005 MSFT 0x0100000e) @ 0x00000000
[17179572.472000] ACPI: Looking for DSDT ... not found!


cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no

=( Now, is there any way I can enable throttling and the limit interface? At the moment this laptop makes me hands sweat from the heat just idling. It's cool to the touch in Windows. It's a Gateway notebook with an old 1.4GHz P-M on it.

---

### Post by ShinjiLeery on 2006-08-06
I have to understand why i have the bus mastering control not enable. Here my acpi info:

```
xxxxxx:~$ cat /proc/acpi/processor/CPU1/info
processor id:            0
acpi id:                 1
bus mastering control:   no
power management:        yes
throttling control:      yes
limit interface:         yes

```

And only two C state:

```
active state:            C2
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[--] demotion[C1] latency[001] usage[01645410]

```

Here my dmesg | grep ACPI.
Why I have CPU0 and CPU1 in this print? I have a laptop with a Dothan 1.6GHz and in the ACPI cat i read only CPU1....


```
[17179569.184000]  BIOS-e820: 000000001ffc0000 - 000000001ffcf000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ffcf000 - 0000000020000000 (ACPI NVS)
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f71b0
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x10000513 MSFT 0x00000097) @ 0x1ffc0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x10000513 MSFT 0x00000097) @ 0x1ffc0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x10000513 MSFT 0x00000097) @ 0x1ffc0390
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x10000513 MSFT 0x00000097) @ 0x1ffc03f0
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x10000513 MSFT 0x00000097) @ 0x1ffcf040
[17179569.184000] ACPI: SSDT (v001    AMI   CPU1PM 0x00000001 INTL 0x02002026) @ 0x1ffc92b0
[17179569.184000] ACPI: DSDT (v001  0AAAA 0AAAA000 0x00000000 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179573.520000] ACPI: Looking for DSDT ... not found!
[17179573.688000] ACPI: bus type pci registered
[17179573.688000] ACPI: Subsystem revision 20051216
[17179573.752000] ACPI: Interpreter enabled
[17179573.752000] ACPI: Using IOAPIC for interrupt routing
[17179573.752000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.756000] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[17179573.756000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.764000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179573.764000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[17179573.768000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[17179573.772000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 12 13)
[17179573.772000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 12 13)
[17179573.772000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 7 12 13)
[17179573.772000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 12 13)
[17179573.772000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 12 13) *0, disabled.
[17179573.772000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 12 13) *0, disabled.
[17179573.772000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 12 13) *0, disabled.
[17179573.772000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 12 13)
[17179573.772000] ACPI: Power Resource [GFAN] (off)
[17179573.772000] pnp: PnP ACPI init
[17179573.780000] pnp: PnP ACPI: found 16 devices
[17179573.780000] PnPBIOS: Disabled by ACPI PNP
[17179573.780000] PCI: Using ACPI for IRQ routing
[17179573.788000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179573.788000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179573.788000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.204000] ACPI wakeup devices:
[17179574.204000] ACPI: (supports S0 S3 S4 S5)
[17179575.448000] ACPI: Fan [FN00] (off)
[17179575.452000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.452000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179575.616000] ACPI: Thermal Zone [THRM] (43 C)
[17179576.000000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 201
[17179578.220000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 209
[17179578.324000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 217
[17179578.428000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 201
[17179578.532000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179578.636000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 209
[17179578.744000] ACPI: PCI Interrupt 0000:02:01.1[B] -> GSI 16 (level, low) -> IRQ 169
[17179593.636000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179594.212000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 201
[17179594.220000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179594.220000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179594.876000] ACPI: PCI Interrupt 0000:02:01.2[C] -> GSI 18 (level, low) -> IRQ 201
[17179628.440000] ACPI: AC Adapter [AC0] (on-line)
[17179628.504000] ACPI: Battery Slot [BAT0] (battery present)
[17179628.504000] ACPI: Battery Slot [BAT1] (battery absent)
[17179628.536000] Asus Laptop ACPI Extras version 0.29
[17179628.564000] ACPI: Power Button (FF) [PWRF]
[17179628.564000] ACPI: Sleep Button (CM) [SLPB]
[17179628.564000] ACPI: Lid Switch [LID]
[17179628.760000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179628.760000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179632.904000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179675.040000] ACPI: PCI interrupt for device 0000:02:02.0 disabled
[17179708.480000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169

```

I have allready read every post in this forum... ](*,) 
Can anyone help me? Tnx

---

### Post by hardyn on 2006-08-06
im still seeing the old trouble with my P-M, as well with extremely doggy video performance; the subsequent fix expected for the single proc. people?  or should another bug fix be requested?

back to i386 for me.

thanks.

---

### Post by hardyn on 2006-08-06
quick question, a little new to linux...

can somebody in few words explain why bus mastering is not available on my notebook?  it is something that is plain not present in my notebook, or is there some funny software configs. that must be performed to accomplish this?

is bus mastering what the windows intel .inf drivers accomplish?

any ideas on getting it enabled?

thanks for the help.

---

### Post by gesho on 2006-08-06
**vayde**, **incandenza**:
right, I checked dpkg -l
> gs@129-79-147-19:/proc/acpi/processor/CPU0$ dpkg -l | grep linux-head*
ii  linux-headers-2.6.15-26                2.6.15-26.46                            Header files related to Linux kernel version
ii  linux-headers-2.6.15-26-686            2.6.15-26.46                            Linux kernel headers 2.6.15 on PPro/Celeron/
gs@129-79-147-19:/proc/acpi/processor/CPU0$ dpkg -l | grep linux-k*
ii  linux-686                              2.6.15.24                               Complete Linux kernel on PPro/Celeron/PII/PI
ii  linux-headers-2.6.15-26                2.6.15-26.46                            Header files related to Linux kernel version
ii  linux-headers-2.6.15-26-686            2.6.15-26.46                            Linux kernel headers 2.6.15 on PPro/Celeron/
ii  linux-image-2.6.12-10-686              2.6.12-10.32                            Linux kernel image for version 2.6.12 on PPr
ii  linux-image-2.6.12-9-686               2.6.12-9.23                             Linux kernel image for version 2.6.12 on PPr
ii  linux-image-2.6.15-23-686              2.6.15-23.39                            Linux kernel image for version 2.6.15 on PPr
ii  linux-image-2.6.15-25-686              2.6.15-25.43                            Linux kernel image for version 2.6.15 on PPr
ii  linux-image-2.6.15-26-686              2.6.15-26.46                            Linux kernel image for version 2.6.15 on PPr
ii  linux-image-686                        2.6.15.24                               Linux kernel image on PPro/Celeron/PII/PIII/
ii  linux-kernel-headers                   2.6.11.2-0ubuntu18                      Linux Kernel Headers for development
ii  linux-restricted-modules-2.6.12-10-686 2.6.12.4-11.1                           Non-free Linux 2.6.12 modules on PPro/Celero
ii  linux-restricted-modules-2.6.12-9-686  2.6.12.4-11                             Non-free Linux 2.6.12 modules on PPro/Celero
ii  linux-restricted-modules-2.6.15-23-686 2.6.15.11-1                             Non-free Linux 2.6.15 modules on PPro/Celero
ii  linux-restricted-modules-2.6.15-25-686 2.6.15.11-2                             Non-free Linux 2.6.15 modules on PPro/Celero
ii  linux-restricted-modules-2.6.15-26-686 2.6.15.11-3                             Non-free Linux 2.6.15 modules on PPro/Celero
ii  linux-restricted-modules-686           2.6.15.24                               Restricted Linux modules on PPro/Celeron/PII
ii  linux-restricted-modules-common        2.6.15.11-3                             Non-free Linux 2.6.15 modules helper script
ii  linux-sound-base                       1.0.10-4ubuntu4                         base package for ALSA and OSS sound systems

headers update is there, but C3 state still remains elusive
> gs@129-79-147-19:/proc/acpi/processor/CPU0$ cat power
active state:            C2
max_cstate:              C8
bus master activity:     66665ddc
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00392460]
    C3:                  type[C3] promotion[C4] demotion[C2] latency[085] usage[00000014]
    C4:                  type[C3] promotion[--] demotion[C3] latency[185] usage[00000023]
gs@129-79-147-19:/proc/acpi/processor/CPU0$  

---

### Post by vayde on 2006-08-06
gesho: I don't know why you are having touble reaching the C3 state.  There are a number of people who are having the same trouble.  I don't recall if anyone came up with a fix.  

Check back along this thread to be sure, but I don't know of one.  I'm just fortunate that I'm not having the problem.

You might just need to let the machine sit quietly for a couple minutes before repeating the 'cat /proc/acpi/processor/CPU0/power' command.  Sometimes it takes a couple minutes for things to throttle down.

Sorry I can't be more help.

---

### Post by gesho on 2006-08-06
**vayde**: yeah, no clue indeed... fan's are kinda working and temperature is not too high, but still, worse then under 2.6.12 kernel. Always C2 state and 10C degrees more.

---

### Post by vanilla.gorilla on 2006-08-06
OK, my temps are still low to mid 40's, but I still read where people are in the upper 20's and low 30's when idle. But my CPU enters C3 quite a bit, so thats ok. I don't think my fans are working correctly, but I get the following error when I try to install i8kutils

E: Cannot find package

I also do not understand how to 'update' my kernal.  I did succesfully get the 686 kernal working on my intel core duo(nivida card btw).  But that is the most advanced thing I have done since I am a linux newbie. 

Any help is appreciated guys.

One other quick thing, how do I turn on ACPI in gnome?

---

### Post by vayde on 2006-08-06
gesho:  Have you tried just going back to the 386 kernel?  Im not sophisitcated enough to know what all you would lose, but it might be an answer.

Other than the fact that I can now play around with xgl and compiz, I don't really see where the 686 kernel is really helping me out much.  In fact, my screensavers run LESS smoothly on the 686.  If it's a question of sucking your battery life or melting something, I'd just downgrade for a while.

---

### Post by hardyn on 2006-08-07
the 686 kernel will employ all those media instructions that came out after the devopment of the original i386, such as mmx, sse1/2/3 etc.  by using the i386 kernel the software has no access to these advancements.

the fact that things are running slower, just suggests that things are broken.

---

### Post by gesho on 2006-08-07
**vayde**
> Have you tried just going back to the 386 kernel?
nope, and tomorrow I will. better be safe, probably some fix will appear. in fact 2.6.12-686 is good enough.

**hardyn**
> by using the i386 kernel the software has no access to these advancements.
bummer... but I hope eventually this 686 problem will be fixed.

---

### Post by sco1984 on 2006-08-07
Hello,
 Heating problem is one of the all time hot topic which is not
 just topic..But a serious issue. I have **IBM** ThinkPad
 R50e laptop. Which is Centrino 1.5, Intel 855 GME motherboard,
 I use several distro of linux and LIVE CD's as well. I figured
 out, if i run a LIVE CD, my laptop fan starts throwing little extra heat. But i m using Mandriva from last 9 month's. I watch
 DVD version movies in it, i play games too i found no problem
 with heating. May be it's not a problem of ** UBUNTU** , but
 the architecture of laptop built by the vendor. IBM has pretty
 good heat vantilation system and thats why i always recomand
 my friends to buy IBM ThinkPad laptop. One issue could be >
 If your already running your laptop on battery power and using
 Linux, but i can say if power system inside ur laptop is good,
 then such problem wont hurt you, or option is buy external colling fan for your laptop which is available everywhere. Blaming UBUNTU is not a right thing.[-( , check out article's
 at DELL laptop user forum, there is a forum for ThinkPad users
 , [http://forum.thinkpads.com]("http://forum.thinkpads.com") . Hmm .>ALright then,

 Regard's,
 Amey Abhyankar.

---

### Post by insyzygy on 2006-08-07
I don't think anyone is blaming ubuntu, I blame dell. I think the purpose of this thread is to help ubuntu users mitigate dells poor design choices with regards to heat. Aside from the physical design of the laptop, it seems one problem is (and this may be wrong), that dell made the (stupid?) decision of requiring fan control be done at the software level (OS or user) for most of their laptops.According to 
[http://www.diefer.de/i8kfan/faq.html]("http://www.diefer.de/i8kfan/faq.html")
the dell bios (on certain inspirons) won't intervene in fan control unless the temp reaches around  85C, and even then only will turn the fan on its low setting. 

Its hard to figure out what problems are due to hardware failing due to normal use, or due to overheating, and whether that problem is the OS fault, or that of the laptops. All  can say is I had the following experience.

I have an inspiron 8500. I ran suse for 6 months and fedora core 3 for a year. (I had had occasional overheating problems in fedora the system would shut down, but after cooling and rebooting, would be fine.) Then my video card died (the computer was around 2 and a half years old, a year and a half on linux). It was a replaced, after it was replaced I installed ubuntu. A month later the video card died, immediately after installing a large amount of updates which pegged the processor and got it pretty hot. I believe the kernel was controlling my fans (the fans went on but at a somewhat high temp, 55C i think). This is probably fine to protect the CPU which can take up to 100C, but it wasn't being agressive enough to protect the video card on my system which appears to have a lesser ability to withstand thermal damage.

I now use i8kmon to control the fans aggressively and things seem fine, and I recommend anyone with an inspiron use it.  For all I know the first video card was killed by fedora and maybe also windows due to overheating and the second was just a refurbished piece of crap that had already died and just didn't really die until a month in.

Regardless of the actual causes, based on my experiences I worry that if I installed (probably) any linux distrubtions on this computer and did something very processor intensive for a while without explicitly modifying the fan behaviour, I would permanently damage the video card. This might even be true if you installed windows and didn't use dells specific drivers? This is a problem for people who don't know, and if your not under warranty is expensive to learn about by accident (luckily I was covered for both video cards) The thing that would push new users away from linux faster than anything is to have linux appear to damage their hardware, even if its not linux's fault. If you search you will find people using every linux distro as well as windows have issues with these dells overheating so it probably isn't linux's fault, but if your using linux you need to know how to deal with it and if anything in the ubuntu kernel can be modified to mitigate the problem thats good for everyone.

---

### Post by ShinjiLeery on 2006-08-08
All of you have a bus mastering activity and a C3 state? Why, in my laptop there is not any C3 state? 

in some forum in the net I read that the problem can be releated with the audio card (alsa) that block the system in the C2 state... Anyone have same information reguard "no bus mastering" ?

Tnx

---

### Post by gesho on 2006-08-08
**ShinjiLeery **
> All of you have a bus mastering activity and a C3 state? Why, in my laptop there is not any C3 state? 

in some forum in the net I read that the problem can be releated with the audio card (alsa) that block the system in the C2 state... Anyone have same information reguard "no bus mastering" ?


this is interesting...
I can't get C3 state under 2.6.15 kernel. Many people had same problem here but after recent release of 2.6.15-26.46 bug fix most of them fixed it.

but my dell 600m still have troubles.

now that you mentioned sound card, my i8kmon fan control gets into conflict with kmix sound. so that could be reason. do you have some link of that discussion?

---

### Post by aceracer24 on 2006-08-08
> **faswad said:**
> I've been using Ubuntu for over a year now and everything has been great. I just received a new laptop:

Dell Inspiron 9400\E1705,
Intel Core Duo
17" UWXGA screen,
NVIDIA 7800GS.

I installed Ubuntu on 20gb partition, and everything ran great for about a week. A week later, while I was compiling code, the latop crashed. Reboot again into Ubuntu it crashes again. The time before crash was proportional to how long the laptop was off, so I concluded it was a heat issue. 

After 3-4 crashes the screen began having artifacts and it kept getting worse. I turned the machine off for about 1 hour, tuned it on again and more artifacts appeared, even in Windows the artifacts were there. The artifacts were even there at POST, so its def not a driver issue.

The notebook is permanently damaged. I believe the video card is damaged from overheating... Its not the LCD because the artifacts are not there in the BIOS for example (4 colore mode).

I didnt encounter any heat issues or crashes in Windows XP, these issues only happened in Ubuntu.


Has anyone encountered this?
I received a replacement from Dell, but i'm hesitant to run Ubuntu again. 
Does anyone have any advice? I think that allowing the fans to turn on at a lower temperature may help the situation, but i'm still not sure. Also, what controls the video card fan, bios, os, other?

thanks for any help!

Have not bothered to read all the posts but it sounds like your blaming Ubuntu for your over heating. That would be doubtful. I won't say it's impossable however since there is alot you can do in linux and of course any kind of overclocking can damage a computer, but if it was a default install, I seriously doubt Ubuntu was the culprit. More like coincidence if anything.

---

### Post by CptSkippy on 2006-08-09
> Have not bothered to read all the posts but it sounds like your blaming Ubuntu for your over heating. That would be doubtful. I won't say it's impossable however since there is alot you can do in linux and of course any kind of overclocking can damage a computer, but if it was a default install, I seriously doubt Ubuntu was the culprit. More like coincidence if anything.

Have bothered to investigate this issue and it sounds like you think Ubuntu is infallible.  That would be doubtful.

I'm currently running a Compaq Evo N600c that consistently overheats when running Ubuntu without the acpi=off switch.  How do I know it's overheating?  Well the fan hardly ever runs, it gets so hot that it will burn your bare legs, and the ambient temperature and heat disipation qualities of environment greatly affect how long it runs.  When acpi is disabled the fan runs 80% of the time at the lowest setting, the thing still gets hot but not nearly as hot andit never EVER locks up.

My lappy is only a 1ghz machine, so it's TDP is much lower than that of a 2ghz dual core machine with a GPU so if there is a bug/misconfiguration in ACPI that cause the fans not to run frequently enough or at high enough speeds then it's entirely possible that the CPU, GPU or other components could be damaged.  Considering what's involved in getting the LMSensors modules to work and the guess work involved, it wouldn't suprise me if ACPI had to do the same trickery and that the settings might not work for all laptops.

---

### Post by insyzygy on 2006-08-09
ACPI has two parts the OS and the hardware it interacts with. Ubuntu's acpi implentation could be rock solid, completely adhering to the specifications and I'm quite confident that ubuntu's acpi implentation is perfect. However laptop vendors probably only test if their acpi works with windows (which, lets be honest, likely doesn't quite exactly adhere to the standard if their general approach to say html is any indication. In fact thats a good example, lots of web sites have to be made incompatible with the 
html standard so ie will work with them, who knows if the same doesn't happen for acpi).

Consequently a laptop may well function differently thermally under linux than windows, is this Ubuntu's fault, no (its the laptop manufacters and windows maybe as well). It is a problem for the user if they don't find out how to address it, hence this thread.

---

### Post by Tsukino on 2006-08-09
Another interesting piece of information. It seems my laptop runs cooler while the battery is charging, which I believe I recall someone saying in this thread before. Wonder why? The heat generated is actually on the side opposite the battery, so the battery itself isn't even getting hotter.

---

### Post by NiksaVel on 2006-08-10
I mentioned the thing with battery....  my lap gets hottest when it's battery is full and it's working on AC power :confused:   but in that state the most heat is produced from the part where battery is located...

---

### Post by 454redhawk on 2006-08-10
> **oliwally said:**
> I have also just found that gkrellm with the i8k plugin is a very tidy option for controlling the fans automatically or manually. All installed with synaptic and works very well on my d820. This then allows for fan speed adjustment through a nice gui (if you dont mind having gkrellm displayed on your desktop). Just have to remember to put make i8k start at boot:

In /etc/modules put the line:

i8k force=1


I put i8k in modules and upon kde startup get a volume display on the screen that is unmoveable and constantly displayed.
It seems I can only load it manually with modprobe and then run gkrellm.

That being said it is a nifty little interface for fan control.

I dont really need it. My Dell Inspiron 1150 Celeron 2.6 seems to run the fans reasonably well all by itself. They are on low around 50c and come on high at 58c I think they turn off around 47 (when I came in this morning it was idle at 47 and the fans were off). This is when its plugged in. I have not paid attention enough to see how it is when running on battery.

Edit:

It seems to have the same profile on battery.

Edit#2
Forgot to mention that I am running Mepis 6

Edit#3
I used the manual control for the fans and left it on high for a bit and it seems it wont go any lower than 43c at idle. That seems reasonable to me. YMMV

Edit#4

Further testing with a CPU stess utility

Results from using the command acpi -V 
Low on at 52c
Med on at 56c
Hi  on at 66c

Transition from 
Hi to Med  61c
Med to Low 55c
Low to Off 51c

---

### Post by CREEPING DEATH on 2006-08-11
> **Tsukino said:**
> Another interesting piece of information. It seems my laptop runs cooler while the battery is charging, which I believe I recall someone saying in this thread before. Wonder why? The heat generated is actually on the side opposite the battery, so the battery itself isn't even getting hotter.

Many time the BIOS is set to let it run hotter on bsttery power to conserve the battery - less fan usage = longer user time.

CD

---

### Post by gesho on 2006-08-11
**454redhawk**
> I put i8k in modules and upon kde startup get a volume display on the screen that is unmovable and constantly displayed.
 It seems I can only load it manually with modprobe and then run gkrellm.
 
 That being said it is a nifty little interface for fan control.
 
 I dont really need it. My Dell Inspiron 1150 Celeron 2.6 seems to run the fans reasonably well all by itself. They are on low around 50c and come on high at 58c I think they turn off around 47 (when I came in this morning it was idle at 47 and the fans were off). This is when its plugged in. I have not paid attention enough to see how it is when running on battery.

exactly, all the same here on dell inspiron 600.

but /proc/acpi/pro*/CPU0/power
still lower power states are not obtained and processor remains unnecessarily loaded.

---

### Post by oliwally on 2006-08-11
> Originally posted by 454redhawk
I put i8k in modules and upon kde startup get a volume display on the screen that is unmoveable and constantly displayed.
It seems I can only load it manually with modprobe and then run gkrellm.

Yes, I have the same problem. I didn't realize the two are related!

> Edit#3
I used the manual control for the fans and left it on high 

How do you use the manual control? Is that as described in post 128 of this topic (p 13)? And even when this daemon is set, can the fan speed be controlled other than by tweaking /etc/i8kmon?

---

### Post by 454redhawk on 2006-08-11
> **oliwally said:**
> Yes, I have the same problem. I didn't realize the two are related!



How do you use the manual control? Is that as described in post 128 of this topic (p 13)? And even when this daemon is set, can the fan speed be controlled other than by tweaking /etc/i8kmon?

It seems that its a plugin for GKrellM call i8Krellm Dell plugin
It allows manual and automatic control of the fan or fans and has 2 nifty little fans that spin according to the speep mode you fans are in.
 
Open the main screen for GkrellM and scroll down the left side and you will see a plugin section. I cant remember if I added it or if it came with it. Either way its in the repositories.

Do a search for i8k in synaptic. There is 2 that show up.

---

### Post by jeremiebergeron on 2006-08-11
Hmmmm... I've had the same problem on both my laptop and desktop described in the first post in the last 3 days. Graphical artifacts in both the laptop and desktop in everything including the bios. In fact I can't actually boot kubuntu on my desktop anymore as my monitor says display mode not supported when it boots of X and CTRL-ALT-BKSP doesn't seem to kill X. And my kubuntu install on my laptop got messed up when I tried to re-install (I died half way through). I haven't looked into the issue much since I've been busy lately but I have a feeling that my video cards are both burned up. All that I'm going to say is watch out for overheating...

---

### Post by j.bunce on 2006-08-11
This may not be an Ubuntu problem, as for a few years now Dell Laptops have had issues with over heating. [http://en.wikipedia.org/wiki/Dell_Inspiron]("http://en.wikipedia.org/wiki/Dell_Inspiron")

Just a thought.....

Jake

---

### Post by cgray on 2006-08-11
I have just used the i8kmon daemon setup as posted about 6 pages before. Cheers for that setup.

In my case, I have two fans on a Dell Inspiron 8200.

So I need to remove the - and add as follows:
set config(0)   {{0 0}  -1  45  -1  45}
set config(1)   {{1 0}  40  50  40  50}
set config(2)   {{1 1}  45  55  45  55}
set config(3)   {{2 2}  50 100  50 100}

With each of the {LHS, RHS} being the number for the left or right fan. When in doubt check man i8kmon.

I basically have it in state 1 most of the time, then sometimes it goes into state 2.

---

### Post by fuzzybabybunny on 2006-08-11
I've got a Compaq x1000, P-M 1.6, Mobile Radeon 9200, and I'm having the same overheating issues. 

1. My CPU fan turns on LESS in Ubuntu than under Windows.
2. My video card is what's getting blisteringly hot. Windows must intelligently throttle down the video card clocks when it's not under load, because my video card feels cooler under Windows than Ubuntu (yes, I can physically open up my lappy and check).

Is there a utility for Ubuntu and ATI that will allow me to at least manually downclock my video card? The best case would be a utility that does it on its own based on load.

I'm particularly concerned because I know from experience that heat WILL harm my 9200 (this is my second card).

---

### Post by kno712 on 2006-08-12
This is not only a Dell's laptop problem. I have a Toshiba Satellite M30 (centrino 1.5Mhz, Nvidia Gforce Fx) and today, after a couple of hour of use, temp read 52ºC (it started with 32ºC).

---

### Post by Melcar on 2006-08-12
Seems that everybody is having thermal problems.  For me it's the other way around.  When I had WinXP on my V2000Z the fan hardly turned on, making the notebook incredibly hot.  Now with Ubuntu, the fan turns on full blast like every 2 minutes or so making the laptop rather cool.  The thing is that while the little fan is not that loud it is noticeable, and in quiet environments (libraries) it gets rather annoying.  Does anybody know of temperature monitoring programs for Linux so I can control the fan; there are tons for Windows so I would imagine there must be at least one for Linux.

---

### Post by 454redhawk on 2006-08-12
> **kno712 said:**
> This is not only a Dell's laptop problem. I have a Toshiba Satellite M30 (centrino 1.5Mhz, Nvidia Gforce Fx) and today, after a couple of hour of use, temp read 52ºC (it started with 32ºC).

Thats a VERY reasonable temp. I would not sweat it unless it STAYS above 65c.
Its very unlikely your laptop is overheating or even hot at 52c.
32c is about 89 fahrenheit, VERY low for an electronic component. You are lucky to get that temp in a standby status let alone while running under a load.

Its no big deal to go up to 65 under a heavy load and the have the fans come on HI then the temp go back down. Normal operation.

Edit:I take it back. Please look up the specs for your CPU. Some are able to run MUCH hotter than others.

---

### Post by BoomAM on 2006-08-13
When is this expected to be fixed then?

---

### Post by kno712 on 2006-08-13
> **454redhawk said:**
> Thats a VERY reasonable temp. I would not sweat it unless it STAYS above 65c.
Its very unlikely your laptop is overheating or even hot at 52c.
32c is about 89 fahrenheit, VERY low for an electronic component. You are lucky to get that temp in a standby status let alone while running under a load.

Its no big deal to go up to 65 under a heavy load and the have the fans come on HI then the temp go back down. Normal operation.

Edit:I take it back. Please look up the specs for your CPU. Some are able to run MUCH hotter than others.

Thanks for your help. I've tried with Intels website, but it is not easy. Do you know of any other place where to look for this info?

I don't think my trip points are not good at all. They are as follow:

critical (S5):           119 C
passive:                 118 C: tc1=9 tc2=2 tsp=1800 devices=0xdffeaa20
active[0]:               118 C: devices=0xdffeaea0
active[1]:               118 C: devices=0xdffeaea0


Does anybody know how to change them? I've tried with

echo -n "100:0:90:80:58" > /proc/acpi/thermal_zone/THRM/trip_points

but I get a message of permission denied (even if I do sudo!)

Please help me!!!!

---

### Post by vayde on 2006-08-13
> **kno712 said:**
> 

Does anybody know how to change them? I've tried with

echo -n "100:0:90:80:58" > /proc/acpi/thermal_zone/THRM/trip_points

but I get a message of permission denied (even if I do sudo!)

Please help me!!!!

You'll have to be logged in as root to do that.  Sudo won't cut it.    Just type:
sudo bash
and then you will truly be god.

I can't say if doing what you are trying to do is a good thing or not, but that's how you can do it.

---

### Post by kno712 on 2006-08-13
454redhawk, vayde, thanks for your help.

I found a similar post in [http://www.linuxquestions.org/questions/showthread.php?t=426494]("http://www.linuxquestions.org/questions/showthread.php?t=426494")

I changed the rc.local at /etc/rc.local and added the 'echo' command above. My first impresion is that the laptop is running cooler now (50 C, stable; I used to have 52 C and even 56 C). I'll play with other figures and I'll post the results here.

Please, I'm a bit new to linux. Would you mind to tell me your views (pros and cons) of this approach for solving this problem? Thanks a lot.

---

### Post by vayde on 2006-08-13
> **kno712 said:**
> 

Please, I'm a bit new to linux. Would you mind to tell me your views (pros and cons) of this approach for solving this problem? Thanks a lot.

Im fairly new myself.  I manage my fans with i8kmon, but I'm running an inspiron 9300, so that's fine for me.

I don't know if your method is good, bad or ugly.  Might be the best thing going.  Manually changing things by echoing into /proc scares the willies out of me, but that's because I haven't had to do it.  It could well be a perfectly harmeless thing to do.  I really don't know enough to say.  

I just knew how to accomplish what you were asking about, so I piped up, but I didn't want anyone to take the fact that I knew how to do it as an endorsement of the method.  Don't know enough to do that.  :)

---

### Post by kno712 on 2006-08-13
> **vayde said:**
> I just knew how to accomplish what you were asking about, so I piped up, but I didn't want anyone to take the fact that I knew how to do it as an endorsement of the method.  Don't know enough to do that.  :)

Do not worry, I won't blame you! All these forums is just about that: to collect the bits that all we know to understand and solve a common problem. From your reply, today I have learnt something new and may be some one else out there too.

Best regards

Sorry everybody for this un-productive post.

---

### Post by slipperhead on 2006-08-13
i am new to linux as of yesterday (ubuntu live cd)and have noticed that my acer 2200 2.66 ghz laptop seems to be overheating and freezing.

i'm back on xp as i was getting quite concerned about the heat,definately runs hotter on ubuntu than windows, so as mentioned in previous threads, it can't just be a dell problem. i possibly now have some fan damage now as the fans ran at full tilt for the few hours i was on ubuntu and now they appear to be running only at their lowest speed after quite a few hours of use on xp which is unusual with this laptop. (although the laptop still seems cooler than when using ubuntu)

so being a total newbie who only just worked out how to change the ubuntu desktop picture, i will be watching this with interest.

---

### Post by 454redhawk on 2006-08-13
> **kno712 said:**
> Thanks for your help. I've tried with Intels website, but it is not easy. Do you know of any other place where to look for this info?



Go here
[http://www.intel.com/products/laptop/processors/index.htm]("http://www.intel.com/products/laptop/processors/index.htm")

Then pick your processor by clicking the link.

Then click the "Technical documents" tab.

Then click "Data Sheets.

Then choose the proper sheet for your processor.

Search in that PDF for "TEMP" you should find the operating temptures for your processor.

---

### Post by groberts1980 on 2006-08-14
For what its worth, I installed Dapper on my Dell Inspiron E1705 on Saturday, and the temps are actually lower than they are in XP. In XP it was running around 45-55c, In Ubuntu it typically runs around 35-45c. Average around 42c. Occasionally it'll bump over 50. I do have i8k running.

Here's my question though. I only have one case fan at the back of the machine. There is a cpu fan. Do the two fan graphics in gkrell refer to those two fans, or is i8k set up to only deal with two case fans, in which the other fan graphic doesn't change anything? I only get an rpm readout on one fan. Strange thing about that is the fan is on the left side of the case, and the right side graphical fan controls it.

---

### Post by kno712 on 2006-08-14
> **kno712 said:**
> 454redhawk, vayde, thanks for your help.

I found a similar post in [http://www.linuxquestions.org/questions/showthread.php?t=426494]("http://www.linuxquestions.org/questions/showthread.php?t=426494")

I changed the rc.local at /etc/rc.local and added the 'echo' command above. My first impresion is that the laptop is running cooler now (50 C, stable; I used to have 52 C and even 56 C). I'll play with other figures and I'll post the results here.

Please, I'm a bit new to linux. Would you mind to tell me your views (pros and cons) of this approach for solving this problem? Thanks a lot.

Hello. Update: the changes to the trip_points did not mean any changes to the temperature control. What is more: the trip points changed to their orignal values at some point. I've read somplace that the BIOS instruct the OS what the real values are. 

I have no idea what the temp for my laptot is in windows (i swithched completely to linux and I never worried about this before I read this post). I have a Toshiba M30. Anyone with a Toshiba M30 can give me its readings of temp?

---

### Post by ÄlveKatt on 2006-08-18
I have an Asus A6JM laptop, and it gets very hot. So I would really like a solution to this problem.

I found something strange. 

Doing cat /proc/acpi/processor/CPU1/power returns differently whether i Have external power inserted.

Without external power I get c3, and it works mostly there as this thread says it should. But plugged in I don't get c3 at all.

Should this be reported as a bug?

I would really like to see better support for laptop heat management in the next update. I beg you! It never runs below 60 degrees celcius as it is now. I will try the fan controlling program, as a temporary fix.

Edit: I would also like to request a how-to for setting up i8kmon. Edit2: A real userfriendly one would be nice. With explanations of what you are doing and what you should do different depending on what machine you have.

---

### Post by insyzygy on 2006-08-19
i8kmon is a utility for the dell inspiron family of laptops, the i8k stands for inspiron 8000 which is what the guy who wrote was using, though it actually works on most of the inspiron laptops.  If you have an asus this won't work. I don't know of anything comparable to i8k for other laptop brands as far as fan control goes.   Anyone else?

I also found this article illuminating as far as C1,C2,C3
[http://acpi.sourceforge.net/wiki/index.php/WhyMyCxPowerStateIsNotUsed]("http://acpi.sourceforge.net/wiki/index.php/WhyMyCxPowerStateIsNotUsed")

My simplistic understanding is that the difference between the different C* states is the amount of time the CPU is allowed to rest between "doing things". If you have a program (sensors like gkrellm perhaps) or certain drivers (usb) that require the cpu to constantly poll devices very frequently then the CPU will never reach the C3 state because if it did, it would rest to long and couldn't keep up with polling the devices it needs to.

---

### Post by ÄlveKatt on 2006-08-20
Thank you for the information insyzygy. I will continue my search for a fix.

I found something strange. As I said the computer claims there is no DSDT. I have been surfing around for info about fixing DSDT and I found out where the files controlling it are. The files exists in the file tree, but when I try to edit them they are all empty. It seems that the reason it can't find the DSDT really is that there are none. 

Question: How do I install DSDT?
Question: Why are the files empty, is it perhaps a matter of this feature not being included in the 686 kernel? Can I somehow copy the DSTD from the 386 kernel if that is the case?

Please help me find answers. I used do a lot of writing on my old computer but in this one the heat is too damn distracting. I don't really fancy the idea of needing to use the other computer every time I want to write.

---

### Post by tiffany on 2006-08-20
Those of you running this on the Dell E1505, what version of the BIOS are you running?  I just picked up my laptop yesterday and was thinking about dual-booting w/ Ubuntu and I noticed BIOS update A08 on Dell's web site. 

"Enhancements
------------
1. Updated Intel processor support, Processor ID: 06F6.

2. Support Owner Password feature.

3. Update Intel bitmap logo.

4. Add support for 64-bit Windows flash program.

5. Update NVIDIA GeForce Go 7300 Video BIOS version to 5.72.22.42.B2.

**6. Update thermal control.**"

Perhaps this could help with the problem?

---

### Post by garrye on 2006-08-20
Using network manager perchance?  I saw 100% CPU load on an Acer Aspire 3003 WLCI which features a Sempron 3000 on SiS silicon using Network Manager.  Also suspect ACPI issues.  Had to ditch Network Manager and invoke wpa_supplicant via /etc/network/interfaces stanzas and config supplicant manually.

---

### Post by esorcc on 2006-08-20
I just heard last week that dell was recalling thousands of laptops because of the Lithium Ion batteries overheating and even causing fire. You should contact them to see if your model is affected.

---

### Post by kuriharu on 2006-08-21
It's funny you mention this. I have a P4 Hyperthreaded laptop and mine overheats, too. It runs fine when Ubuntu is running, but if I reboot screen goes black and I have to let the laptop sit for 5-8 minutes before I can boot it again.

My Windows partition has been fine for 2 years on the same laptop. I never really suspected Ubuntu until now.

---

### Post by ÄlveKatt on 2006-08-26
It's funny. If anyone remembers that I reported that the laptop runs warmer than comfortable I can now report that it got a lot better after the latest  update.(The fixed one, luckily I didn't have any internet when the one that broke X was about.)

It could still get better though, and my question about how to fix DSDT still stands.

Thank you.

---

### Post by LyubinVadim on 2006-09-04
I want to buy ABS Mayhem F22 R40 Intel Core Duo T2400(1.83GHz) bought [here](http://search.stores.ebay.com/Costupdate_notebook_Laptops-Notebooks_W0QQcatrefZC12QQfcdZ2QQfciZ4QQfclZ4QQfromZR10QQfrtsZ30QQfsnZCostupdateQQfsooZ2QQfsopZ2QQftsZ2QQrefidZstoreQQsacatZ51148QQsaselZ3743435QQsbrsrtZdQQsofpZ0) on costupdate store on eBay. My last notebook overheated permanently so how about Mayhem?
[IMG]http://thumbs.ebaystatic.com/pict/320018116760_0.jpg[/IMG]

---

### Post by mihalisla on 2006-09-04
hello I read recently that dell called back 400000 computers for heat issues from the core duo line....maybe this is the problem..contact to your supplier

---

### Post by BoomAM on 2006-09-04
I had the overheating problem yesterday.
I put my laptop into standby, and closed the lid. Or so i thought.

I came to use it 4 hours later, opened the lid, which was v.hot, and then looked at the temperature gauges, both the CPU & GPU were hitting 65*c+. Ubuntu hadnt kicked the fans into gear. :-k

---

### Post by Surgeon General on 2007-04-20
I'm using a Dell Inspiron 6400 and to address the temperature issue, I installed gkrellm with the i8kutils plugins. This nifty tool allows one to set the temperatures of when the fans would kick in. It also has temperature reading of the CPU. This works for me as I don't have time to spend on making DSDT and all that work.

---

### Post by YetAnotherNoob on 2007-06-07
I see a lot of discussion about CPU temprature but wasn't your problem a graphics card problem?  I also have Inspiron 9400 and had all sorts of crashes Feisty (may be temprature related), that never occured under windows.

Monitoring the tempratures I found the CPU's rarely went over 30-40 degrees C.  But the graphics card: Nvidia 7800GO was running about 70C. under windows.  And when running linux for a while, then quickly rebooting to windows saw the temprature drop from ~80 to ~70C.

---

### Post by ykaerflila on 2007-12-26
hi folks,

got a LENOVO 3000 N100 with GF7300 Go and i have the same heatproblems. graphics card overheats and notebooks hangs up. this used to happend with and without compiz/beryl, so i dont think it's a "graphics card is overheating due to high gpu-usage"-thing. i guess it's a acpi-problem like others mentioned before...
i switched to debian (unstable) till there is a solution for this.

---

