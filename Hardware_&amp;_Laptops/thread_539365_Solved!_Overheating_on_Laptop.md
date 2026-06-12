---
title: "Solved! Overheating on Laptop"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by WhiteHorse on 2007-08-31
I solved the laptop overheating issue for my specific situation. I have an MSI MS-1029 aka Megabook 635 or M635. My laptop never overheated before unless I blocked the vents but once I got 3D games going with online multiplayers over wifi I actually started to utilize my cpu and graphics card simultaneously. It turns out that the CPU and graphics card share the same heat sink and fan. Basically it's a piece of copper that touches both processors and then goes to a fan. Here are the steps I took:

1. Remove the fan/heatsink assembly. Clean the vanes, clean the old thermal grease off, replace the thermal grease with new grease.

2. Add the following to your /etc/modules:
battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace

That's it! I can't overheat my machine for the life of me now...

I think the fact that the GPU and CPU are connected in serial make for a very hot situation during gaming. I dunno, it worked for me. I spent hours looking through bug reports and trying weird settings. Even after I did all the fan cleaning and thermal grease stuff it still overheated. There was no log of anything. It must have been a hardware shutoff from bios. Now the fan is actually quite reactive and it gets loud when I game and is almost silent when I don't. Before it would get a little louder but not as loud as when windows would get hit hard. Hope this helps someone.

Oh and BTW I had to compile all my games to run on amd64, oh yeah baby. 64 bit games on a 64 bit OS. God my electric bill is going to be high for my laptop...

---

### Post by torstenaf on 2007-09-05
I installed Ubuntu around v6.10 and it was _cool._

I upgraded whenever the tool told me it was needed. Something happened....

My **Sony VAIO 505** started running _cooking_ hot with no applications open.
[LIST]
[*]The fan ran at full speed all the time - very noisy
[*]Had to use a towel to shield my legs
[*]Started turning off the machine after even short uses
[*]Constant worry about heat damage
[*]Had to be careful that the desk surface could handle high heat
[*]Laptop would occasionally overheat and shutdown on its own!
[/LIST]

After implementing the changes from part 2) above and then rebooting, the operating temperature change was almost immediate. 
[LIST]
[*]Underneath the processor is only warm to the touch
[*]The fan is running slow and QUIET, nearly inaudible!
[*]No more towel needed to use the machine on my lap
[/LIST]

Thank you very much!

Torsten

---

### Post by vlitzer on 2007-09-06
Part 2 solved my overheated old Presario 900 with Xubuntu Feisty too. Thanks

---

### Post by WhiteHorse on 2007-09-07
Seems this works for more laptops than my own.  Perhaps this solves the historical bug for ubuntu laptops? Maybe someone should notify the developers. I don't know how to tell them but I am sure it t would help them out lots.

Don't forget to clean your fan veins. I know it seems like a pain but after using my laptop for a year the veins were clogged with tiny hairs and dust bunnies. I am a clean guy and keep my laptop free from dust but it still got clogged. It might add a few years to ur laptop to clean it out and replace the thermal grease, especially if it has been overheating due to this bug. I'll let you know in a few years if my laptop fails. :P

---

### Post by MattVort on 2007-09-07
Is it really just adding six blank files to /etc/modules?

Heh. Feisty would overheat and just stop in 20 minutes for me - Ubuntu and Xubuntu on two different laptops - it made them completely unusable. This will really help. Thanks.

Off to reinstall Feisty on my Acer Aspire :)

---

### Post by torstenaf on 2007-09-07
> Is it really just adding six blank files to /etc/modules?

Almost, except no blank files needed.

Edit the text file [FONT="Courier New"]**/etc/modules**[/FONT] and add in the following lines:
[FONT="Courier New"][INDENT]battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace[/INDENT][/FONT]

```
root@torsten-laptop:~# cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod
#apm power_off=1

# added 4 sep 07 by Torsten
battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace

root@torsten-laptop:~#

```

---

### Post by Wiebelhaus on 2007-09-07
sorry if this sounds frank.

But , this is complete rubbish , the OS is not causing your laptops to over heat, anyone that's ever seen the inside of one knows that those small copper heatsinks clog with the smallest amount of lint  and some manufacturers either don't apply thermal grease or don't apply enough , also your ram heats under pressure but mostly the cause of overheating laptops is the daughter card (GPU) or a clogged exhaust system , if your laying the laptop on a towel , doily , shirt , blanket , pillow or your fat mid section your suffocating the cooling system.

Add "System Monitor" to your tool bar then click it and watch it for a minute , this OS consumes less than most intense applications.
 
then a noob chimes in with - "Well it wasn't Happening in winblowz!11!" then the only plausible diagnostic explanation must be that your suffering from a Ide 10 T error.

---

### Post by MattVort on 2007-09-08
sx66gns, it is the OS making them overheat. Consider this: In Ubuntu 6.06, Fedora 4 and 6, Ubuntu, Xubuntu and Kubuntu 6.10; SLAX, Windows XP and Windows Vista, I get absolutely no overheating issues whatsoever. As soon as I upgraded 6.10 to 7.04, I started having problems, **but then deleting 7.04 and reinstalling 6.10, and I had no overheating issues once more.**

The same is true with another computer. Install Xubuntu 6.10 on it, fine. Install Xubuntu 7.04 on it, overheating issues. Remove 7.04 and install 6.10 again, no overheating issues.

There is simply no other explanation. It must be something wrong with 7.04.


@torstenaf, sorry, I misunderstood, I thought /etc/modules was a directory. My mistake.

---

### Post by Didjit on 2007-09-09
I believe I maybe having the same issue. 

What is the symptom of over heating? 

My laptop just shutdowns during heavy disk I/O. No kernel panic, nothing, like the plug was pulled. Is this the symptom?

Dijdit

---

### Post by Onesimus on 2007-09-17
I have a DELL Inspiron 6400 laptop with Feisty 7.04.  I have probably been having overheating problems for some time but not attributed the symptoms to overheating.  Noticed the symptoms on OpenArena 0.7.1 when the game would crash for no apparent reason (it was hard to reproduce the crashes), the screen would even turn white starting from the bottom right hand corner.

I eventually got a temperature sensor installed on the top panel.  This was showing me temperatures of 60 to 70C when I had a few applications running.  On idle I was getting temperatures in the 50 to 60C range.

Implementing the changes has brought temperature down (but still within 40 to 50C range).

When playing an audio CD it can still get to 70C !

What do the changes to /etc/modules actually suppose to do ?

---

### Post by LT1Caprice57L on 2007-09-18
Guys - make sure your fans/heatsinks are CLEAN.

I have a Sony VAIO PCG-K33 - this laptop is NOTORIOUS for running hot - VERY hot - which it did, I had to keep my mini desktop fan blowing on it at all times.  If I went somewhere, (and couldn't use the deskfan) the laptop would be so hot it was unusable/choking to death within 30-45 minutes.

UNTIL I cleaned the heatsinks out, now it barely runs warm.  I'm running Feisty.

Lint is EXTREMELY bad for this.

---

### Post by Z_Cee on 2007-09-18
I have a Toshiba A75-S209 laptop and noticed a big difference when I upgraded to 7.04 (from 6.10). Running sluggish was the primary problem - because I didn't leave it installed long for heat to become an issue. Going back to 6.10 helped.

---

### Post by maxwells_demon on 2007-09-23
I've installed Ubuntu 7.04 on a Sony Vaio VGN-C2Z, and experience the same problems many have described. (i.e. 7.04 runs extremely hot, far hotter than in Windows, leading to unpredictable system lockups). 

The attempted solution in this topic (modification of /etc/modules) seems to alleviate the problem *a little* (in my case), however I notice the CPU temps still regularling hitting 60+, often higher when performing processor intensive activity. 

From browsing the forums, overheating is a widely reported problem in 7.04, yet there appears to be no *general* 'consensus' on its cause and solution.

Is anyone aware of official response from the developers? (This is clearly not a rare phenomenon). Or failing that, a list of theories/attempted solutions?

---

### Post by Z_Cee on 2007-09-24
I agree about with you about a forth-coming (or rather the lack of there being one) consensus about the problem?

It would be good to get 7.04 working properly before attempting 7.10!

Maybe it will be cleared by the time 7.10 arrives??

---

### Post by maxwells_demon on 2007-09-25
I hope so. I may install the latest Gutsy tribe to see if it solves the problem. I'm very surprised by the lack of official acknowledgement; a bug capable of *physically* damaging your hardware (as some have experienced [in [COLOR="Navy"]other posts[/COLOR]]("http://ubuntuforums.org/showthread.php?t=186003")) is not something to be taken lightly. It's problems such as this which makes me realise we *do* need proprietary software (just not in the style of MS). A commercial vendor could not afford the presence of such a liability for so long. 

For all it's poor design, Windows is the lesser of two evils on my laptop. I can recover from a system crash with a reboot. To recover from my system *regularly* overheating, I'll eventually  need to buy a new system!

---

### Post by Linder on 2007-09-25
Actually common knowledge that Ubuntu 7.04 contains a bug that makes most laptops run REALLY hot. Mine does too, and I'm going to try this when I get home to see if it solves the heat problem. It's already cleaned inside and it did squat for temperature.

---

### Post by AnimateDeath on 2007-09-25
Maybe it's not so much a problem with 7.04 in general, as a prob with 7.04 on certain systems.  I have it installed on my Toshiba Satellite A135-S4467 and have left the laptop on for the last 24+ hours and see no heating problems at all. In fact, I am willing to say that it is running cooler now than it did with vista running. Maybe I just got lucky with my laptop brand, but no problems here at all.  \\:D/


Could it be a Bios issue? I know that my brother's laptop, HP, when it was running XP was fine until he installed sp2, and then the fans shut down and stopped running. He had to do a bios update to fix the problem. I don't know if there is such a problem in linux (or even if there could be), but maybe that is the problem with some of them.

---

### Post by Skweek on 2007-09-25
Oh dear, my Dell X300 (Feisty) has been suffering overheat problems too - I managed to convince my wife it was buggered and we've just forked out for a new Dell Insipron 1720!!!  If she ever finds out about this, I'm toast.

It was nice knowing you all...

---

### Post by Z_Cee on 2007-10-01
You're long overdue for a new computer! Now you can use the X300 as a testing unit to install different Linux Distro's.

Remind your wife that with your new computer, you already have your Christmas gift and next birthday gift? :)

---

### Post by dinub1 on 2007-10-01
> **WhiteHorse said:**
> Seems this works for more laptops than my own.  Perhaps this solves the historical bug for ubuntu laptops? Maybe someone should notify the developers. I don't know how to tell them but I am sure it t would help them out lots.

Don't forget to clean your fan veins. I know it seems like a pain but after using my laptop for a year the veins were clogged with tiny hairs and dust bunnies. I am a clean guy and keep my laptop free from dust but it still got clogged. It might add a few years to ur laptop to clean it out and replace the thermal grease, especially if it has been overheating due to this bug. I'll let you know in a few years if my laptop fails. :P

Sorry. I have a HP pavilion ze4145. Since I upgraded from 7.04 to 7.10 I have this CPU heat problem. Fan works continuously and CPU temp goes up to 65F sometimes. No shutdowns however. CPU heat sink and vanes are clean.
Adding devices per chapter #2 of your initial advice in the /etc/modules, saving it and rebooting did not solve the problem.

However what seems to solve the problem is setting the CPU frequency lower than full. Like:
$ sudo cpufreq -selector -g powersave

This reduced my CPU freq from 1.5 GHz (full for AMD XP1800+) to aprrox 662 MHz. Temperature dropped then considerably to approx 42F fan stopped and it fluctuates between 42 F to approx 57F when fan operated again and it brings it back to aprrox 42F when fan stops and etc... Butn then Applications run visibly slower than when CPU operates at full frequency. This is the operation I have seen with previous Ubuntu versions on the same laptop. Only with this last version (7.10 beta) this raise in temp happens. FYI I do not have this problem with Windows XP SP2 that I also run on this laptop. 
 
Typing:
$ sudo cpufreq-selector -g performance
Brings back the CPU to full frequency (approx 1523 MHz) and then the CPU temp stats to climb again towards 60F. 
So therefore this seems definitely a bug with the OS, or OS dependent.

Thanks for your input.

---

### Post by girishv on 2007-10-01
Hi,

In my laptop running Feisty Fawn, these modules are automagically loaded :)
In addition the cpu is actually uses lower voltage (search for undervoltage). Before this, my laptop (thinkpad Z60m) used to run at temperatures of 47-50C when idle and reach 80+ when running simulations. Now, the idle temperatures are reduced by nearly 5C and runs around 40C most of the times.

I also use the following modules in /etc/modules
cpufreq_conservative / powersave /ondemand / stats / userspace
speedstep-centrino

Girish
PS: Is hyphen in cpufreq_* is a typo ? I have underscore in these modules instead

---

### Post by dinub1 on 2007-10-01
> **maxwells_demon said:**
> I hope so. I may install the latest Gutsy tribe to see if it solves the problem. I'm very surprised by the lack of official acknowledgement; a bug capable of *physically* damaging your hardware (as some have experienced [in [COLOR="Navy"]other posts[/COLOR]]("http://ubuntuforums.org/showthread.php?t=186003")) is not something to be taken lightly. It's problems such as this which makes me realise we *do* need proprietary software (just not in the style of MS). A commercial vendor could not afford the presence of such a liability for so long. 

For all it's poor design, Windows is the lesser of two evils on my laptop. I can recover from a system crash with a reboot. To recover from my system *regularly* overheating, I'll eventually  need to buy a new system!

I agree. It is a SERIOUS problem and I am quite confidant its a OS issue. However I am curently running 7.10 from the Live CD and no overheating... I do not know what to say... I may wipe out the old Ubuntu partition and reinstall from scratch. The only thing that helps is reducing the CPU freq... if I run

$ sudo cpfreq-selector -g powersave

 then CPU runs at approx 1/3 of its full frequency and temps return to normal.  But this reduces my processing power and speed.  Other Live CD distros like latest PClinux2007 also run without an overheating problem. Conclusion: this is not hadrware related but software related issue. Windows XP also runs without any overheating issues on this laptop. My CPU heat sink is clean. So :) ?

---

### Post by dinub1 on 2007-10-02
I finally fixed my heat problem with this HP Laptop (which over the years served me extremely well) and Ubuntu 7.10 beta. I was confident this is an OS (software) related issue and not hardware malfunction, or dust, debris or anything else in the ventilation system. Taking into account that the Ubuntu 7.10 Live CD ran without over heating or CPU tasking problems, I wiped out my Linux partitions (after backing up) and reinstalled Ubuntu 7.10 beta from scratch. CPU now shows 5 - 7% load at idle and fan successfully regulates CPU temps between 42 F (fan off) to approx 57 F when fan starts to work and rapidly cools the CPU. Now the CPU frequency monitor show in the system trays and indicates "Dynamic". On low tasks is approx 660 MHz then kicks to full 1.5 GHz when applications need it. This was apparently a software bug as I kept upgrading Ubuntu since version 5 to the current version. I hope this helps.

---

### Post by rhya_n on 2007-10-09
lilyuliuluil

---

### Post by click4851 on 2007-10-09
whats up dinub1, small world..lol

---

### Post by dinub1 on 2007-10-10
> **click4851 said:**
> whats up dinub1, small world..lol

hey, it may be... you in Everett too. Do I know you? :)

---

### Post by jemarroyo@gmail.com on 2007-11-09
Can someone explain what are exactly this modules added to the kernell?.

2. Add the following to your /etc/modules:
 battery
 ac
 thermal
 processor
 acpi-cpufreq
 cpufreq-userspace

The comand:
*sudo cpfreq-selector -g powersave*
doesnt work for me. 
What package I need for using it?
It seem to be working with my laptop. I'm running  KUbuntu Gutsy. 
The laptop is an Acer TM240
Regards

---

### Post by firstcupoffreshpressed on 2007-11-15
I recently bought a used inspiron 5150.  I loaded gutsy into it and away I went until I noticed it seemed hot. I researched this computer and found that it had overheating issues.

Reading posts on how people had handled the issue I blew air into the vents with no luck finally I found a post on how to remove and clean the fan. After this i was poking around near the vent and found a cluster of dog hair clogging the fan grating inside the computer .  I got a good teaspoon full of hair and lint out.

Reassembled the lappy temp doesn't often reach 60 and cools quickly when the now much quieter fan cuts in.

:guitar:

---

### Post by torstenaf on 2007-11-18
I'm back. Life was quiet and cool for awhile after the overheating issues were solved. Well, they're back!

With the last upgrade to 7.10, my fan is pegged again. **cpufreq-info** reports constant _1.6GHz _(max 1.87GHz) and never changes, no matter what governor I select with the **cpufreq-set** command (cpufreq package). So my fan is not pegged as high as when I was overheating, but it runs constantly. After the **/etc/modules** entries, life was good.

So what could it be? I still have the** /etc/modules** entries, without changes. I decided to look at top:

```

top - 09:46:06 up 1 day, 12:45,  1 user,  load average: 2.44, 2.59, 2.73
Tasks: 115 total,   5 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s): 95.3%us,  4.3%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   2074880k total,  1853008k used,   221872k free,   261780k buffers
Swap:        0k total,        0k used,        0k free,   764552k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2654 root      21  -4  318m 317m  412 R 92.8 15.7   2023:55 udevd
23764 torsten   15   0  202m 100m  28m R  3.7  5.0   1:34.14 firefox-bin
 2336 root      23  -2  318m 317m  380 S  0.3 15.7   0:00.01 udevd
 2338 root      23  -2  2052  604  516 S  0.3  0.0   0:00.01 watershed
 7217 torsten   15   0 33528  15m  11m R  0.3  0.8   0:02.91 konsole
29032 root      15   0 18356  920  756 S  0.3  0.0   0:01.37 cpufreqd
    1 root      15   0  2948 1852  532 S  0.0  0.1   0:02.33 init
    2 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd

```

It looks like **udevd** is constantly running at very high cpu loads. Is this my trouble...?

-Torsten

---

### Post by torstenaf on 2007-11-20
Turns out it was udevd, in conjunction with evms (and I think knetworkmanager). I removed evms, and my laptop is running normally again.

-T

---

### Post by KCPokes on 2007-12-07
Mine was working fine, for a while, after upgrading to Gutsy.  I don't recall ever having an issue with Feisty, but perhaps I just never noticed.  After adding the changes for option 2, it seemed my issues with overheating were gone.  Turns out they weren't.  It is not near as common, but my machine will still tend to overheat, with little to no load, occasionally.  I continue to try to find a source to the issue, but for now it is still up in the air. 

In regards to it being a hardware issue and not related to OS, I'm not sure how one could explain how booting into other distros, or even Windows, does not result in the same problems.  Also seems there are a lot of ID 10 T errors taking place as this is not related to any one make or model of laptop.

---

### Post by dinub1 on 2007-12-07
> **KCPokes said:**
> Mine was working fine, for a while, after upgrading to Gutsy.  I don't recall ever having an issue with Feisty, but perhaps I just never noticed.  After adding the changes for option 2, it seemed my issues with overheating were gone.  Turns out they weren't.  It is not near as common, but my machine will still tend to overheat, with little to no load, occasionally.  I continue to try to find a source to the issue, but for now it is still up in the air. 

In regards to it being a hardware issue and not related to OS, I'm not sure how one could explain how booting into other distros, or even Windows, does not result in the same problems.  Also seems there are a lot of ID 10 T errors taking place as this is not related to any one make or model of laptop.

OK. Glad you fix your machine. Mine was overheating after ulgrading from Gutsy to Feisty. Until Feisty I never had any issues of any ind with Ubuntu. I believe the problem is software related and not hardware. This is why, booting into another OS like Windows XP pro or even into another Lin ux distro,  does not exhibit the same overheating phenomenon. So in case of Ubuntu, something tells the CPU tyo work at full speed even if it is not needed. I have to go check and see what "option 2" means in prvious posts to understand the fix. In my case, simply wiping out the Ubuntu partition and reinstalling Festy from scratch, freshly, solved the problem.

---

### Post by laurencemulchrone on 2008-01-24
can someone please help me!

i have a 800 mhz 256mb RAM compaq notebook and after about 20 mins it just dies, i think it overheats!

can someone tell me, step by step, how to do all the changes noted above as i hope this may rectufy the problem.....

i have no expreience with the command line interface and i am not a very good computer user....i would really appreciate someone telling me how to do this easily...step by step :D

---

### Post by laurencemulchrone on 2008-01-25
hello. i am not very good at linux


i have a laptop that gets very hot can anyone tell me step by step how to enter the commands to cool it down

i would really appreciate it

i have no experience with a command line interface

thanks!

---

### Post by utnubuuser on 2008-01-27
Hello - 
total noob here so....
my laptop is running way hotter on gutsy 7.10 too.
Where do I find this cat /etc/modules file to add the lines to?
Is this an actual file somewhere, or do I make the change in the terminal window?
Thanks for any help.

---

### Post by Melf on 2008-01-27
Just write in the terminal window: 
sudo gedit /etc/modules
Then a text editor pops up (gedit), you add the lines (to the end, dont modify anything else) and save the whole thing :)

---

### Post by utnubuuser on 2008-01-27
Hello  I'm having the same problem with my laptop

Is there an actual text-file somewhere to edit, or is this supposed to be done in the terminal?
Thanks

---

### Post by utnubuuser on 2008-01-27
Thanks

---

### Post by utnubuuser on 2008-01-27
thanks again  -- applied the changes, and the machine is running considerably cooler
(IBM X31, Ubuntu 7.10).

---

### Post by utnubuuser on 2008-01-27
hey - 
not sure if my other reply made it through so..

There was a posting in one of the threads claiming that the culprit for overheating issues were minipci wifi cards.
I remember reading about it somewhere, but I can't find the original thread.

Thanks again for your help

---

### Post by gustus on 2008-02-07
Hi. I have an HP pavillion dv1000, with gutsy on it. I`va had it with ubuntu for about two years now, and although it always had an active fan, it was never this critical. Since a few days ago, it just shuts down every time some mildly CPU intensive task is attempted. It reaches critical temperature (or so it says), but this temperature varies: it could be as low as 66C. 
I made the additions to /etc/modules, and it seems to have made things better, at least on battery. 
I`ve also tried to put the cpufreq-selector to powersave. 
But even with all this, is still overheating and shutting down. For instance, visiting a mildly active site, like a newspaper, would shut the computer down. 
Running Mathematica or code is impossible! Please, help!
Thanks.
G.

---

### Post by yippy on 2008-02-07
My laptop just runs hotter in Gutsy than it used to, I'm not sure why.  I added the modules from this thread and generally it helps, but if I run flash video (like YouTube) for a minute or two the CPU temperature still gets above 80C.  If I let it go for a few minutes my machine will shut down (I finally realized it was flash causing my computer to overheat most of the time).

Besides the fact that flash just sucks and should never be using that much CPU for the trivial tasks it does, it makes me uncomfortable that the temperature ever gets so high that my machine has to shut down to cope.

I played by my CPU speeds and I found that in powersave mode the temperature drops, where the CPU is running at the slowest speed all the time.  It's great that it doesn't overheat, but what's the point in having a fast CPU if it's stuck in slow mode?

So my little hack fix for it is this:
I installed the Computertemp app from the universe repository, which shows the current CPU temp in an applet on the toolbar, and has an alarm if it gets too hot.  I set an alarm for 75C and told it to launch a shell script I created.

Here's my script:
```
#!/bin/bash
sudo cpufreq-selector -g powersave
while [ `cat /proc/acpi/thermal_zone/THRM/temperature | awk '{print($2)}'` -gt 63 ]; 
do
  sleep 10;
done
sudo cpufreq-selector -g ondemand
```

On this machine I've disabled the sudo password, so that can run without prompting me.  Basically that just sets the CPU to powersave until the CPU cools to 63C or less, then it turns it back to "on demand" mode where I can get power if I need it.  I'm a little surprised there isn't something doing that already, but maybe there is and it isn't functioning correctly.

I like having the temperature on my toolbar since I've had trouble with it overheating, but you could easily set that script to launch in the background and periodically check the temperature to activate powersave instead of having the applet launch as an alarm.

If someone wanted to use the script they might have to change THRM to the the right thermal zone for their machine, I only have one.  I'm also using ACPI to get temperatures, which you probably are too but there are other options.  If you get the computertemp applet it has the available options and you can just find what works for you and use those options in your script.

Anyway, just thought I'd throw that out as a possible solution to save your computer if you can't find a better one.

---

### Post by mtcycler on 2008-02-07
I am completely new at this, how do I modify /etc/modules ?  It tells me I don't have permission
I don't know how to open it or modify it in the terminal either

Can somebody tell me what to do?

---

### Post by kesman on 2008-02-08
Open it as root user in terminal with:
```

sudo nano /etc/modules

```
after you modify it, hit ctrl+x to exit and answer yes to save

---

### Post by mtcycler on 2008-02-08
Thank you that worked to make the modifications to /etc/modules, 
but my computer's cpu fan still waits to come on till the applet cpu temp read-out is above 60C 
how can I tell it come on at say 40C or so?

I guess you can ignore the above complaint, I think my fan is shot, that may be the problem

---

### Post by utnubuuser on 2008-02-08
I don't suppose there's an explanation available about what these lines actually do?
I made the changes, and my laptop seems to run cooler than before, but still not as coolly as it does when running XP.
I read somewhere that the drivers for the wireless cards in laptops is one of the causes of the higher operating temperatures, but I can't find the original article.

---

### Post by lostone on 2008-02-16
My 1st post here, pretty new Ubuntu user myself.
I had the same problem with Ubuntu, used to overheat my laptop (hp nx9420) and after approx 10 minutes it shuts down.

Found something on this forum about the ATI card, tried it and... it worked like a charm :)

You need to have the propretary ATI drivers (the fglrx stuff, you all know the drill), and run on a terminal:

aticonfig --lsp (this should list all the card's powerstates, and also the current state);

If, for some reason, this gives a message of failure (something about POWERPlay, don't remember exactly), try it again but like this:

DISPLAY=:0 aticonfig --lsp

If this works without errors, the you can run:

DISPLAY=:0 aticonfig --set-powerstate=1

With this, the ATI card will enter in the powerstate #1, using some less hardware resources. This worked for me like a charm, as I said at the beginning of this post.

I hope this helps someone :)

All the best

---

### Post by ohhhchiahao on 2008-02-24
tried the 2nd part of the fix. though i didn't have actual temperature reading before the fix, it didn't seem to have any significant effects on decreasing the temp my laptop runs at =(. still hovers around mid 60s when idle and jumps up to 70s, 80s when running something like firefox.

seems like i just have to invest in one of them cooling pads before i burn my new motherboard out again :confused:

---

### Post by patree on 2008-02-24
hello i was just wondering if i typed it in correctly my /etc/modules now looks like this:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2

# Generated by sensors-detect on Sat Feb 23 02:26:01 2008
# Chip drivers
k8temp

battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace


i restarted my comp but it still seems to be just as hot, with just firefox going, im at 75C
help?

---

### Post by justutkarsh on 2008-03-12
yups still  running at 70 degrees with just the firefox. :(

---

### Post by dinub1 on 2008-03-12
I would suggest that you back up what is important for you  in that Ubuntu partition/folder, wipe the partition out, and reinstall last version (7.10). This is how I fixed mine. This is a glitch. I believe this is related to the dynamic CPU mode which is pertinent to new Ubuntu's. It sometimes get screwed up and it makes processor work at full speed even when it is not needed. That's why it is overheating. 
It happened on mine, but after wiping out and reinstalling, it does not happen anymore.

Give it a try.

---

### Post by philheaton on 2008-05-13
altering the /etc/modules as suggested seems to have worked for me on my Samsung X22 Core2 Duo T7500 2.2Ghz Hardy Heron 32bit. 

Prior to using this fix, I was getting idle CPU temps of around 50-60 degrees and under load it soared to the mid 70s

I am now running 45-49 degrees idle and mid 50s under load. 

no idea how this works, but I'm glad something does as the laptop was burning up and seemed to be in competition with my central heating!

As an afterthought, I am getting temps of mid 40C on AC power, but up to 60C as son as I switch to battery power :| Anyone got any ideas?

---

### Post by WhiteHorse on 2008-06-16
Your power settings are hosed. When you switch from AC to battery, it should scale the cpu down and run cooler. Get 8.04, I haven't seen these problems with 8.04 at all. Power management seems to have been resolved with a kernel update and power settings are managed correctly in 8.04.
:popcorn:

---

### Post by WhiteHorse on 2008-06-16
This issue was resolved with a kernel update. These procedures no longer apply. The original issue was a scale-a-rate run-away condition with CPUs that allow dynamic frequency scaling. 

Thanks to the kernel devs for fixing it upstream: :)

If you still have overheating issues, look elsewhere.

If your laptop has EVER overheated, replace the thermal grease.

If your laptop has been running with the fan at full for long periods of time, clean the vanes.

---

### Post by philheaton on 2008-06-17
have been using hardy since it came out (fully patched, latest kernel). still getting higher heat on battery than on ac. have applied numerous tweaks from powertop suggestions and lesswatts.org also installed the latest laptop-mode package (for debian, not ubuntu).

laptop is 3 months old, but even so have cleaned the fans etc. 

beats me...

---

### Post by AFarris01 on 2008-06-19
Im currently running an Wubi install of 8.04 on my Toshiba Satellite P105-S9312, and i am experiencing an overheating issue, but only in ubuntu.  i just found this and have yet to try the patch, but i know its not dirt/dust in my heatsink...ill post back if this works!

---

### Post by WhiteHorse on 2008-06-28
> **philheaton said:**
> have been using hardy since it came out (fully patched, latest kernel). still getting higher heat on battery than on ac. have applied numerous tweaks from powertop suggestions and lesswatts.org also installed the latest laptop-mode package (for debian, not ubuntu).

laptop is 3 months old, but even so have cleaned the fans etc. 

beats me...

Does it run cool under XP? If not, it could be your thermal grease, a bad fan, bad design, etc. 

If so, then you may have a sysctl thingy that's not getting set right. You'll want to sit down with a kernel dev and walk through all your settings one by one until you find the culprit. It could even be something in the bios or your hard drive spinning up too fast.

---

### Post by philheaton on 2008-07-01
runs fine under vista, normal running temps of around 40-45C. just done a clean install of 804-64bit and have the same issues, it must be a kernel thing though as am getting the same results with suse 11 and fedora 9. ah well...

---

### Post by philheaton on 2008-07-01
> **hannahross said:**
> I have HCL_AX0S2102 laptop. my battery back up is not good. it is one year old laptop. what is the problem in lap anyone help me

It seems to me the problem with laptops is the fact that they are all so very different. The average desktop PC is simply a collection of generic and widely used/interchangeable elements, such as a motherboard, graphics processor, HDD controller, etc and as such are pretty easy for kernel developers to access all the various microcodes and incorporate FOSS versions within the kernel space. Even proprietary hardware such as ATI/nVIDIA can easily be incorporated. 

Laptops on the other hand are different beasts and are custom made to specifications set out by their manufacturers, be they Dell, Samsung, Sony etc. These companies work closely with Microsoft in order to achieve the best compatibility with MS operating systems and go through hardware testing with MS products before inclusion on the MS HCL. This is evidenced by the little "Windows Ready" sticker that comes on the machine. It means that every piece of hardware and its configuration has been specifically tested by MS to be 100% compatible with whatever version of Windows is on the sticker. 

Linux developers on the other hand do not receive the same luxury and so pretty much have to make do with what they've got. You'll therefore find that most (if not all) Linux Distros will work exceptionally well on generic hardware you can find in a Desktop system, but not the same with laptops - its simply impossible to cater for every eventuality. 

For example, in Intel driven laptops (those with integrated graphics processors. Intel are very pro-Linux and are working very closely with the Xserver team to develop better grained controls) such as those that Dell use, laptop performance is clearly superior to so called "high-end" laptops with a lot of different component manufacturers, dedicated GPU chips and graphics RAM. This is because kernel devs aren't privy to the exact configurations and therefore can't write specific micro controller code to deal with issues such as heat dissipation, battery management, fan control etc.

I could go on, this is a deeper issue than I've outlined here, but that's the gist. Until hardware/laptop manufacturers open their doors a little or even go so far as to submit code to the kernel devs, we are going to be stuck with these niggling issues.

That said, if Linux "just worked", there'd be no reason to get your hands dirty trying to fix it and I for one would know a LOT less about computers if I just trusted it to the "experts". This is what Linux is all about, its transparent enough for most people who have an interest to jump into the workings of it, improve it and submit their solutions to the community - thats how Linux evolves.

cheers

Phil.

Mind you, would be nice to have laptop-mode to be turned on by default on a laptop installation! I installed the latest Debian version instead of using the one in the Hardy Repos, configured it and have gone a LONG way to achieving the performance I need on my laptop - temps now a lot better and an extra HOUR battery life as well. I also uninstalled powernowd in favour of cpufreq and life's good!

P.

---

