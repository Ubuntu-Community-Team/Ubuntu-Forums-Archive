---
title: "Toshiba Satellite M505 overheating problem"
date: 2009-10-04
forum: Hardware
---

### Post by almikul on 2009-10-04
I purchased new Toshiba Satellite M505-S4945 laptop and installed 64-bit Jaunty. Everything works great except that the fan cannot be turned on due to broken ACPI tables from Phoenix BIOS. The fan makes a big difference (40C vs 70+C). 

I found an omnibook module from sourceforge that is supposed to fix some issues with Satellite laptops, but I was unsuccessful compiling it, probably because the types of supported laptops do not include Satellite M505. I am not a developer nor a programmer, so I cannot fix the source code of omnibook module myself to add my specific model nor can I find it from terminal.

I was wondering if someone has M505 and could resolve this ACPI issue or if someone had to modify the omnibook driver (attached below) to include a specific laptop model (I believe, it is in *laptop.h* file). I would greatly appreciate any advise.

P.S. After my laptop woke-up from the sleep, the fan started working immediately, but now it just runs continuously (at least temp fell to 44C).

---

### Post by almikul on 2009-10-06
bump

---

### Post by almikul on 2009-10-19
I guess this Toshiba model is not very popular in Ubuntu community? :(

---

### Post by wafflemelon on 2009-11-12
I have this same problem. I nearly fried my brand new laptop with Linux Mint 7 (Ubuntu-based). This is stopping me from using Linux. I simply cannot install any distro where this problem is not addressed.

---

### Post by almikul on 2009-11-12
> **wafflemelon said:**
> I have this same problem. I nearly fried my brand new laptop with Linux Mint 7 (Ubuntu-based). This is stopping me from using Linux. I simply cannot install any distro where this problem is not addressed.
What I do in Karmic is wait until it gets warm and then put it to sleep for a second. Upon wake-up, the fan starts working and then works continuously. It doesn't bother me much because once the fan starts working in Windows, it also keeps it running non-stop to keep the temperature around 40-50 degrees.

---

### Post by cubdukat on 2009-12-13
> **wafflemelon said:**
> I have this same problem. I nearly fried my brand new laptop with Linux Mint 7 (Ubuntu-based). This is stopping me from using Linux. I simply cannot install any distro where this problem is not addressed.

Unfortunately, it appears that this is an issue in every distro. I am currently running Fedora 12 (I'm waiting until they iron out some of the kinks in 9.10 before I go back to it), and I nearly burnt up the CPU before I remembered this.

So the problem isn't just with Linux Mint and/or Ubuntu--it's with every distro out there.

BTW, I've heard quite a bit about Linux Mint. What differentiates it from regular Ubuntu?

---

### Post by wafflemelon on 2009-12-28
I think their goal is ease-of-use. Also, it seems lighter and has it's own set of system apps.

---

### Post by derekmbarnes on 2009-12-30
Strange - I have the same model and my fan seems to work fine. Although the left side of the main unit does get a little hot...what do you use to check things like temperature?

---

### Post by almikul on 2009-12-30
> **derekmbarnes said:**
> Strange - I have the same model and my fan seems to work fine. 
What is your exact model? Mine is M505-S4945.

Has it always worked fine or it started after some update? Mine is still not working properly after the latest updates for 32-bit Karmic. 

> Although the left side of the main unit does get a little hot...
It is normal when the fan is working. 

> what do you use to check things like temperature?
Install acpi and then do: ```
acpi -t
```

---

### Post by derekmbarnes on 2009-12-31
Okay, I stand corrected. acpi reads as follows when I run it:

```

Thermal 0: active, 76.0 degrees C

```

So I guess I have the same problem!

---

### Post by derekmbarnes on 2009-12-31
Okay; I think I have a partial solution. To do this you need **acpi** and **powersaved**, both installed from Synaptic; it is assumed you are running Karmic 9.10. Once installed, proceed as follows:

**1)** Open Terminal and enter the following code:

```
/proc/acpi/thermal_zone/*/trip_points
```and compare with

```
sudo powersave -T
```This will tell you your "trip points," the Celsius temperatures where the fan kicks in ("active"), where the processor slows itself down ("passive"), and where it gets so hot it shuts down the system completely ("critical"). The simple solution would be to lower all these variables by at least 10 degrees; unfortunately, if you have the same luck I did acpi won't let you do that.
[B]
2)[/B] Whether you're able to override the trip points or not, first check the following:

```
/proc/acpi/thermal_zone/*/cooling_mode
```If this document exists, then you can alter Cooling Mode in powersave. If not, skip to step 6.

**3)** Next type:

```
sudo gedit /etc/powersave/thermal
```When gedit opens the document, find the non-hashed line that reads ENABLE_THERMAL_MANAGEMENT="" and alter as shown below:

```
ENABLE_THERMAL_MANAGEMENT="yes"
```Exit gedit.

**4)** Repeat of step 3 with a different document:

```
sudo gedit /etc/powersave/scheme_powersave
```Scroll down to the non-hashed line COOLING_POLICY="passive". Change to:

```
COOLING_POLICY="active"
```Exit gedit.

**5)** Reboot the system to enact changes.

I have no idea how well this will work; honestly it doesn't seem to be doing much for me. My processor reads in the ninety-degree range (about 200 Farenheit!) either way.

**6)** Open this document (this will only work if powersave is installed):

file:///usr/share/doc/powersaved/html/Thermal.html

This is a chapter of the powersave manual; it basically tells you how to do everything I just said, *except* it also tells you how to override the trip points. That said, I couldn't find a line anywhere in powersave's /scheme_* files with THERMAL at the beginning. I don't know if you're supposed to add it in yourself or what; they don't explain it very well. It does say to e-mail your vendor for the trip point settings used by BIOS -- which is sensible since in most of these cases the fan worked a lot better with Windows.

-----

If anyone figures out step 6, kindly add what you did on to this thread; it means you had better luck than I did. I know those trip points are the key; I just can't figure out how to get the system to let me change them. Good luck to all of you!

---

### Post by wafflemelon on 2009-12-31
According to [http://lwn.net/Articles/244595/](http://lwn.net/Articles/244595/) as of kernel 2.6.22, trip points cannot be overriden. Why? Because It's not an actual override: Linux disables the BIOS trip points, and sets software trip points for the hardware to poll.
If for any reason Linux failed to inform the hardware of the 'soft' trip points, Linux would be blamed for melting people's laptops. So they take that away from us.

Smells to me like political bull.

---

### Post by wafflemelon on 2009-12-31
Also: [http://fedoraforum.org/forum/showpost.php?p=1251902&postcount=2](http://fedoraforum.org/forum/showpost.php?p=1251902&postcount=2)

I think this means we're pretty much screwed.

---

### Post by derekmbarnes on 2009-12-31
> **wafflemelon said:**
> Also: [http://fedoraforum.org/forum/showpost.php?p=1251902&postcount=2](http://fedoraforum.org/forum/showpost.php?p=1251902&postcount=2)

I think this means we're pretty much screwed.

There is another option: we can appeal directly to the Ubuntu developers and inform them of our problem. If they can lower the trip point settings with a system upgrade, it might resolve the issue.

So does anyone know how to contact the developers?

---

### Post by wafflemelon on 2010-01-01
I believe the only way is to report it as a bug at [http://bugzilla.kernel.org/](http://bugzilla.kernel.org/) .

There is a recent bug report for a Portegé M900 laptop, but I'm not sure it's related.

I suppose in this case it should be reported as a Phoenix Bios problem.

---

### Post by derekmbarnes on 2010-01-01
Update: other users report resolving fan issues by switching to an older kernel of Ubuntu through GRUB -- version 2.6.28-16 was specifically mentioned. (I am currently using kernel 2.6.31-16; terminal command "uname -r" displays this.) I don't recommend trying to make this alteration, but it could be a vital clue to what's going on. If downgrading to an older kernel "solves" the problem, what changed in the newer kernels to cause it?

---

### Post by wafflemelon on 2010-01-01
I'm currently away on vacation and have no linux installed on my laptop. So will someone please test this out for us?

Try loading the kernel each time with one of the following parameters:

*   pnpbios=off
*   acpi_osi=Linux
* acpi=force

Also, take a look at [http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/fan-acpi-problems-insyde-h20-bios-toshiba-satellite-pro-l300-x-716924/page2.html](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/fan-acpi-problems-insyde-h20-bios-toshiba-satellite-pro-l300-x-716924/page2.html)
There are some very interesting tips there.

Please share results!

---

### Post by derekmbarnes on 2010-01-02
> 
Try loading the kernel each time with one of the following parameters:

*   pnpbios=off
*   acpi_osi=Linux
* acpi=force


Tried all three; none of them worked. But according to the link this tactic is only helpful if equipped with BIOS 1.8; I checked my BIOS via

```
sudo dmidecode
```

and it turned to be version 1.2. (So no wonder.) I'm assuming this is the case for all Satellite M500's, in which case we need to figure out how to update it if this is going to be of any use.

Other solutions we haven't tried yet:
-In the above link, disabling APCID seemed to solve several issues at once. Unfortunately, the user who discovered this accomplished it through a menu option that no longer exists. (He was running 9.04.) And I don't know how to do the same thing in Terminal. He also posted what appears to be an alternate version of modifying APCID; will try it out later...
-Elsewhere I saw a post where a user solved the problem by updating his kernel to 2.6.32. I don't know if we can do that, because I'm not sure this kernel is even officially out yet...will check Update Manager and keep everyone posted.

---

### Post by wafflemelon on 2010-01-02
Toshiba has a bios update app for Windows on their website. Version 2.30 is already available (and I already flashed mine).
If you can't update, I'll be home thursday and will try them out.

---

### Post by derekmbarnes on 2010-01-02
Update: Found this on Ubuntu wiki - [https://wiki.ubuntu.com/BIOSandUbuntu#BIOS%20checking%20tools]("https://wiki.ubuntu.com/BIOSandUbuntu#BIOS%20checking%20tools")

> If you suspect your BIOS is not behaving correctly, then it is worth  using the Linux Firmware Kit [http://www.linuxfirmwarekit.org/](http://www.linuxfirmwarekit.org/) to automatically check for incorrect BIOS behaviour. Some issues we have found with this are as follows:



-Incorrectly set thermal trip zone values (ACPI spec 11.1) and Linux /proc/acpi/thermal_zone/THRM
...

Does this sound familiar to anyone? Keep reading...

> BIOS issues can cause suspend/resume to fail...Huh. I'm having that problem too...

I think this link, combined with results of the previous link, pretty much confirms that our problem is rooted in a BIOS/ACPI conflict. I haven't figured out how to update my BIOS yet (not the mention the very prospect of doing so scares me), and Toshiba doesn't list an update for the M500 anyway. Meanwhile I'll be checking other threads for more information; I'll get back to you if I find anything.

---

### Post by almikul on 2010-01-03
> Try loading the kernel each time with one of the following parameters:

* pnpbios=off
* acpi_osi=Linux
* acpi=force 

Guys, sorry for the dumb question, but how can I pass these parameters in GRUB 2? 

I have tried adding the following entry to **/etc/grub.d/40_custom**:
```
echo "Adding custom entries on sda1 (2.6.31-16-generic)" >&2 
cat << EOF
menuentry "ACPI testing on latest kernels" {
        set root=(hd0,1)
        linux /vmlinuz root=/dev/sda1 pnpbios=off
	initrd /initrd.img
}
EOF
```
However, I am not sure it actually affects the booting options. How can I check it really adds *pnpbios=off* at the booting?

---

### Post by derekmbarnes on 2010-01-03
Weird; I made those alterations in /etc/default/grub. It was my understanding from other threads that you were supposed to do it there...was I mistaken?

Also, I noticed something that might throw us for a loop; you and wafflemelon seem to be equipped with Phoenix BIOS on your Satellites. Mine uses AMI BIOS, so...maybe the BIOS upgrade is a red herring? (I would be overjoyed if it is; I don't want to brick my brand new laptop.)

I'm going to try calling Toshiba tech support tomorrow and see if they can give us any insight; it's something I need to do anyway. (For some reason my computer is registered in their database without me registering it.) I know they're Windows-oriented, but it's worth a shot.

---

### Post by almikul on 2010-01-03
> **derekmbarnes said:**
> Weird; I made those alterations in /etc/default/grub. It was my understanding from other threads that you were supposed to do it there...was I mistaken?
No, you were correct. I finally did the same way as you by editing /etc/default/grub. However, none of these three parameters made any difference :( 

What would you make of the fact that the fan starts working at certain temperatures only after resuming from suspend? Maybe the hint is there?

---

### Post by wafflemelon on 2010-01-03
almikul, is your BIOS version at least 1.80 ?

---

### Post by derekmbarnes on 2010-01-03
**MacGyver fix:** I've discovered that placing a conventional fan near the laptop on low speed will keep the temperature down - instead of heating up to 95 C before the CPU fan kicks in, I am now maintaining a temperature roughly between 35 and 40 C. (For reference, 37 C is body temperature.) Until we get the actual problem resolved, this is a useful workaround. Be sure to place the fan on the same side as the cooling vent.

And while I'm here, I recommend installing GKrellM on your systems and configuring to read CPU temperature. No more having to use Terminal to figure it out.

---

### Post by wafflemelon on 2010-01-03
> **derekmbarnes said:**
> **MacGyver fix:** I've discovered that placing a conventional fan near the laptop on low speed will keep the temperature down - instead of heating up to 95 C before the CPU fan kicks in, I am now maintaining a temperature roughly between 35 and 40 C. (For reference, 37 C is body temperature.) Until we get the actual problem resolved, this is a useful workaround. Be sure to place the fan on the same side as the cooling vent.

And while I'm here, I recommend installing GKrellM on your systems and configuring to read CPU temperature. No more having to use Terminal to figure it out.

Where do you point the fan? Facing the vent? Perpendicular to the vent?

---

### Post by derekmbarnes on 2010-01-03
Facing the vent. Having the cold air blowing on the laptop in the first place is helpful on its own, but if you actually point the airflow into the machine it's much more effective.

---

### Post by derekmbarnes on 2010-01-03
Info on using lm_sensors to control the fan: [http://movingtoubuntu.technicalbloke.co.uk/cpu_temperature_and_fan_speed](http://movingtoubuntu.technicalbloke.co.uk/cpu_temperature_and_fan_speed)

This one's easier to decipher than the how-to thread here, but if sensors-detect doesn't give you any useful results it doesn't help much.

---

### Post by almikul on 2010-01-04
> **wafflemelon said:**
> almikul, is your BIOS version at least 1.80 ?
Yes, it is 1.90

However, I was wondering whether your fan kicks in when you resume from suspend? This is the only way I can keep my laptop cool. When you laptop is hot (50C-60C), try to suspend it for a second and then resume. If you have Phoenix BIOS, I think it should work for you. Much better than putting external fan next to the vent anyway ;)

---

### Post by derekmbarnes on 2010-01-04
> **almikul said:**
> 
I was wondering whether your fan kicks in when you resume from suspend? This is the only way I can keep my laptop cool. When you laptop is hot (50C-60C), try to suspend it for a second and then resume. If you have Phoenix BIOS, I think it should work for you. Much better than putting external fan next to the vent anyway ;)

I have AMI BIOS, and suspend doesn't resume properly. (Besides, 50 C is still about 120 F and liable to shorten the CPU's lifespan.) Which brings me to my next question: are BIOS versions not universal? Because my dmidecode says my BIOS 1.2 was released last September and is ACPI-compatible. So I'm starting to think that BIOS isn't the problem after all.

Next suspect on my list: the DSDT table for acpi. According to [this how-to thread]("http://ubuntuforums.org/showthread.php?t=318789&highlight=upgrade+bios+ubuntu+howto") ACPI issues with an up-to-date BIOS can be caused by bugs in this file. The average user can no longer edit their DSDT file (perfectly reasonable since the code is indecipherable to mortals), so it must be reported as a bug instead. And given the luck we've been having these past few days, I think this is probably the best course of action. (We probably should have done this in the first place, but on the bright side our information will be a little more comprehensive as a result of our work.)

I start school again tomorrow, but I'll see if I can find time to pull together a useful draft report. In the meantime, keep that fan running.

---

### Post by almikul on 2010-01-04
> **derekmbarnes said:**
> Info on using lm_sensors to control the fan: [http://movingtoubuntu.technicalbloke.co.uk/cpu_temperature_and_fan_speed](http://movingtoubuntu.technicalbloke.co.uk/cpu_temperature_and_fan_speed)

This one's easier to decipher than the how-to thread here, but if sensors-detect doesn't give you any useful results it doesn't help much.
I tried it and it did not work. Here is the output of *sudo pwmconfig*: ```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

---

### Post by calis1981 on 2010-01-04
ive got a medion akoya mini e1210, flash with a msi u100 1.09 bios, everything works, camera, mic, wifi, bluetooth, sound, only the fan doesnt cool the cpu
it doesnt start at all when i turn on my laptop, once it hit around 69C it kicks in and drops it to around 64-65C but at a very low speed, ive installed the eeepc applet to try and control the fan, and most of the time it does start it up, but it only runs at low speeds, i know it runs fast because it made a low nosie when it did run while i had xp installed
i checked that howto out and ii had everything installed that was said, but no sensor detected, but i get a temp reading in gkrellm, plus i feel it heating up under my hand
the only way ive found to keep it cool is to have it sitting in front of my aircon
it can get the temp down to 35C-cpu 37C-hdd, it ok rite now coz its summer, but when winter comes around im not looking forward to it!

---

### Post by derekmbarnes on 2010-01-05
> **almikul said:**
> I tried it and it did not work. Here is the output of *sudo pwmconfig*: ```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

I'm not surprised; I got the same result.

Haven't had time to work on a bug report yet; I'll see what I can get done today. And on a personal note: this problem is getting *really *annoying.

---

### Post by almikul on 2010-01-05
Derek, I would then recommend to buy the cooling pad with the fan. It really helps reducing the temperature. It costs $25, but it's worth the price. 

On a side note, I was wondering if it was possible to suspend and then immediately wake-up the system automatically? Sometimes, I leave my laptop unattended, and the temperature rises to ~70-75 C. I think I would be able to make a script that polls the temp and suspends the system. However, resuming it without a user action is not that easy.

---

### Post by trash on 2010-01-08
I just installed 9.10 a few days ago and I think this is a problem on my Toshiba as well... L305.
I first noticed today the fan ran all day, so i did a search and came across this thread, after which I restarted and the fan has not come on since and i am hitting 67-69C not doing anything intensive.

EDIT: just hit 70C and the fan went on.. i'll see if the fan shuts off at all or if it will just keep running.. I guess thats better than no fan at all.
EDIT: almost 2 days later and the fan has not shut off once.

---

### Post by derekmbarnes on 2010-01-09
Ack, I keep running in circles with this problem. First I think it's the BIOS, then I think it's the kernel, then I wonder if there's a suggestion posted that I haven't tried yet only to find the proposed solutions still don't work, and then I start over again.

Please forgive the rant, I just needed to vent...anyway, I think I mentioned before that a user said he fixed this problem downgrading to a different kernel of the system. If that works, then it's probably a problem with the kernel, right? So, we should file a bug report with the Linux developers...except the process for doing so confuses the heck out of me. I'm not even sure if the bug has already been reported or not - link: [http://bugzilla.kernel.org](http://bugzilla.kernel.org)

Melon: any luck after the BIOS upgrade?

---

### Post by derekmbarnes on 2010-01-09
Cancel my last post; I found the report we're looking for.

[http://bugzilla.kernel.org/show_bug.cgi?id=14695](http://bugzilla.kernel.org/show_bug.cgi?id=14695)

I'm going to add to this tonight with the info we've collected and see if it's of any use. Will update as events unfold.

---

### Post by wafflemelon on 2010-01-10
To be honest, I haven't gotten Ubuntu installed here yet. Also, Almikul has the correct bios version and it hasn't worked for him.

By the way, your report at kernel.org says we use AMDs... I have a Core 2 Duo on mine.

Also, I noticed this on your post:

> $ cat /proc/acpi/thermal_zone/*/trip_points
critical (S5):           108 C
passive:                 101 C: tc1=30 tc2=30 tsp=50 devices=CPU0 CPU1 
active[0]:               94 C: devices=FAN0 
active[1]:               82 C: devices=FAN1 
active[2]:               72 C: devices=FAN2 
active[3]:               52 C: devices=FAN3 
active[4]:               42 C: devices=FAN4 

I have a hunch that active[0] is the only one that works because only FAN0 actually exists. Is it possible link the other FAN#s to FAN0? This way, the other trip points will activate FAN0.

My first guess would be to use 'ln', but I doubt it's that simple.

EDIT: What's the /dev/ for the fans?

Also, putting a fan didn't help much. I got to 76 C within minutes.

---

### Post by derekmbarnes on 2010-01-12
Well, it seems we have to file a separate bug report anyway. The guy in charge says our problem is different from the one I linked to...also I was wondering if any of this might come from running a 32-bit system (which was the default download) on a 64-bit processor; but if your Intel chips are 32-bit then the obvious answer is no.

I'll be re-installing Windows 7 in a couple of days; hopefully that will better enable me to keep track of the problem, since a properly cooled CPU means I can take my machine anywhere I go. I'll work on filing a new report and keep researching; I read in another thread that fan operation runs through the graphics card, but I haven't confirmed it yet.

Let me know if any of you find anything.

---

### Post by Paul Dufresne on 2010-01-14
According to [https://bugs.launchpad.net/bugs/500666](https://bugs.launchpad.net/bugs/500666), the fan would start when suspending, then resuming.


Can you confirm this?

---

### Post by almikul on 2010-01-14
> **Paul Dufresne said:**
> According to [https://bugs.launchpad.net/bugs/500666](https://bugs.launchpad.net/bugs/500666), the fan would start when suspending, then resuming.


Can you confirm this?
Yes, it is true for M505.

---

### Post by wafflemelon on 2010-01-26
My fan is finally working, with the following boot option: acpi.power_nocheck=1

Unfortunately, it only turns on, at a low speed, when approaching 70C.

So still no problem solved.

Of course, acpi=off does wonders for the fan, but in turn, I have to run X at lo-res and have no wifi.

---

### Post by wafflemelon on 2010-01-26
OK, I got the fans to work rather reasonably. I will see how it goes, but for now, here's what I did on 9.10 :

* boot with option
acpi.power_nocheck=1

* Install & configure powersaved: [http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480) 

* Toshiba U500 users found that having the graphics drivers installed has helped. Try that also.

In the end, all that I managed is to have the trip points upheld. The ideal is setting our own trip points, but I have no idea how we can do this.

Currently posting this from Karmic, at 53 C :)

---

### Post by wafflemelon on 2010-01-27
I fiddled around with DSDT today, and I might have got it right. Unfortunately, it seems the kernel devs once more burst our bubble: Custom DSDT support has recently been disabled.

The only solution is to recompile the kernel with the DSDT.
I spent the last hour and a half compiling the kernel on this laptop which already has thermal problems, to have the whole process fail.

If anyone is willing to try it and perhaps make a patch for all of us, I'll gladly submit the custom DSDT.

Funny thing is, Windows allows me to fiddle with my trip points AND use a custom DSDT (two solutions for our thermal issues). Since when does Linux treat it's users like children?

---

### Post by almikul on 2010-01-28
> **wafflemelon said:**
> OK, I got the fans to work rather reasonably. I will see how it goes, but for now, here's what I did on 9.10 :

* boot with option
acpi.power_nocheck=1

* Install & configure powersaved: [http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480) 

* Toshiba U500 users found that having the graphics drivers installed has helped. Try that also.

In the end, all that I managed is to have the trip points upheld. The ideal is setting our own trip points, but I have no idea how we can do this.
Did not work for me. Here is the output of thermal trip points:
```
critical (S5):           108 C
passive:                 101 C: tc1=30 tc2=30 tsp=50 devices=CPU0 CPU1 
active[0]:               98 C: devices=FAN0 
active[1]:               82 C: devices=FAN1 
active[2]:               72 C: devices=FAN2 
active[3]:               62 C: devices=FAN3 
active[4]:               57 C: devices=FAN4 
active[5]:               37 C: devices=FAN5 
```
I tried to put custom trip points using powersaved, but it does not seem that anything is affected at all. I still have to suspend and resume to make my fan working.

---

### Post by wafflemelon on 2010-01-29
Yes, powersave doesn't override the trip points. But somehow after configuring it, the fan started to work.

Also, your trip points are different from mine. I also get different trip points for different kernel acpi options.

The DSDT on our laptops has different configurations according to the OS it detects. It discriminates the following strings:

"Linux"
"Windows 2001"
"Windows 2001 SP1"
"Windows 2001 SP2"
"Windows 2006"
"Windows 2006 SP1"

I hope this situation isn't another [foxconn scandal]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249").

---

### Post by wafflemelon on 2010-01-29
ACPI can be fully loaded except for the thermal functions. I've had some success with kernel option:

thermal.off=1

Almikul, what are your current kernel opts?

---

### Post by almikul on 2010-01-30
> **wafflemelon said:**
> ACPI can be fully loaded except for the thermal functions. I've had some success with kernel option:

thermal.off=1

Almikul, what are your current kernel opts?
My current options are 
```
quiet splash acpi_osi=Linux acpi.power_nocheck=1
```

Do you know what exactly changed when you loaded *thermal.off=1*?

---

### Post by derekmbarnes on 2010-01-31
> **wafflemelon said:**
> I hope this situation isn't another [foxconn scandal]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=869249").

Interesting find...I'm especially curious about this since my BIOS comes from AMI. While I  don't want to falsely accuse anyone of wrongdoing, it would not surprise me at all to discover this apparent rigging process is still taking place. (For those who haven't clicked the link yet, do so.)

Which brings me to this question: could the problem ultimately be solved by installing [Coreboot]("http://www.coreboot.org/Welcome_to_coreboot")? I understand it's still a work in progress, but having a BIOS specifically built to support Linux systems would be a major boost to its freedom and functionality, not to mention possibly eliminating problems like those with Foxconn.

So armed with this knowledge, I'm going to reinstall Ubuntu on a virtual machine and see if I can isolate any specific problems with the DSDT. If I find it's biased against anything that isn't Windows, I'll call it out here, and then I'll start talking to the Coreboot developers to see if they're in a position to assist us. (This may take me several weeks as I'm shorter on free time.) Anyone else who's more prepared than I am is welcome to do the same.

Hope to return soon.

---

### Post by wafflemelon on 2010-01-31
I just had a chat with one of the guys at #coreboot @ freenode. Here's an excerpt:

> [00:00] <CareBear\> Waffle : the shortest path to delivery is to get something already supported, or something identical to something already supported, or something as close as possible to something already supported 
[00:00] <CareBear\> at the moment that means a ruggedised mil-grade laptop from Roda 
[00:00] <Waffle> from what I've seen, the only laptops you have are olpcs 
[00:00] <Waffle> not so much alike : ) 
[00:00] <CareBear\> I have a Samsung netbook which is getting old now, which is also likely to become successful at some point 
[00:01] <CareBear\> Roda is a laptop as well, but not consumer-grade 

So it seems it's unlikely that Coreboot will be a solution for us. It's a very interesting project, too bad it's difficult to include more mainboards.

I believe we only have the following options:

* Get Toshiba/Phoenix/whomever to create a GOOD version of their BIOS. *It does look fishy to me*. The Foxconn guy did it, so can we. Also, look him up, he has a [blog]("http://izanbardprince.wordpress.com/category/foxconn/")

* Fix the DSDT file ourselves, recompile the kernel (custom DSDT is no longer supported) and create a patch for M500 owners. It takes some getting used to, but with some clever reading you can figure out how it works. Don't let the 14000 lines of code scare you ; )
By fixing, I mean either making the fan work exactly like it does for windows, or lowering all trip points by 10 C while making the fan work.

* Get the Linux/Ubuntu devs to do something about it. Don't ask me what. I believe this would be the longest and most unlikely alternative.

* Load the kernel with different options. I've ran out of ACPI options to feed to the kernel. I believe we already spent this one. If you feel like hitting this old nail, here's a list of options: [http://redsymbol.net/linux_boot_parameters/](http://redsymbol.net/linux_boot_parameters/)
Reading the DSDT may help understand what you have to do.
Also, I find it very strange that acpi_os_name="Windows *" seems to have no effect for me.

It's a lot of work! If someone feels like going for either option 1 or 3, do tell us! Cramming some inboxes goes a long way : )

Derek, please share your views on the DSDT with us when you can!

---

### Post by almikul on 2010-02-10
After updating the kernel to *2.6.31-19-generic* the fan started working correctly (turns on after the temp reaches certain point). So, I don't have to suspend and resume my laptop anymore :)

---

### Post by wafflemelon on 2010-02-10
awesome! but what is this 'certain point'?

How did you do it, did you follow any tutorials?

EDIT: It didn't work for me. Suspending and Resuming does do the trick, though I haven't tried it before.

Also, do you have any special kernel options on?

---

### Post by almikul on 2010-02-10
Actually, I did not do anything except updating the kernel. No special options and no other attempts to fix the situation after the update. It just started to work. However, the acpitool does not show any thermal devices anymore, and *acpi -t* does not show temperature anymore. The new kernel does not have thermal trip points anymore as well, so I do not know what points it follows now. It seems that the fan kicks in at ~35-37 degrees, but I do not know where they are defined now.

---

### Post by estherios on 2010-02-17
Guys, 

I had this issue with my computer a month ago then I had to roll back to Windows, then I wonder if someone could share with me how to update the kernel, I ran some google searches but I could not find the instructions. 

Thanks ;)

---

### Post by almikul on 2010-02-17
estherios, you just install Ubuntu and make sure to enable recommended updates in the software sources (they should be enabled by default). After that, run "sudo apt-get update" and you should get a pop-up window with the latest updates. Make sure that kernel 2.6.31-19-generic is among them. However, keep in mind that some people still have the same problems after installing this kernel.

---

### Post by davesmith on 2010-02-17
Toshiba laptops are notorious for having overheating issues. This is usually a hardware problem associated with the main CPU heatsink radiator vanes getting clogged with dust.
 
The cooling fans suck air in at the bottom of the casing and blow it over the heatsink vanes from the inside. Unless you keep the bottom of the laptop casing on a hard surface or run your m/c in a cleanroom this will deposit dust and crapite on them and eventually clog them up. 
 
Tosh hard-wire a temperature sensor in the CPU, this changes the fan speed incrementally and cools it down acording to the CPU temperature as set by the BIOS. Until the h/s vanes are so clogged it won't cool properly that is, then the fans go into overdrive and/or the m/c will suddenly shut itself down to prevent damage.
 
Here is a simple solution. Turn the m/c off completely and turn it upside down. Get a can of air and a vacuum cleaner. Put the vacuum cleaner nozzle up against the fan covers and switch the suction on. This will get the fans running in reverse, then blow air using the can's thin tube through the rear casing slots over the heatsink vanes. With a bit of luck the accumulated dust will detach and get sucked out. Be carefull not to contact the vanes with the thin tube.
 
If the dust is well and truly caked on, more drastic means are called for. This procedure will invalidate your guarantee, be carefull....!
 
With the m/c switched off, unscrew the base plate cover over the CPU and expose the heatsink etc from the inside. Very carefully blow air over the dust mat and dislodge it, gently use a fine paintbrush if necessary. Suck the dust out. Then replace the cover. Boot up, and hope for the best!
 
 
Good luck:smile:

---

### Post by estherios on 2010-02-17
Almikul, thank for replying my request. I will try to install Ubuntu again on my laptop this weekend and will share the results.

---

### Post by estherios on 2010-02-20
Folks, 

I tested today the new kernel but yes problem remains on my pc, I guess I will have to wait till someone finds a way to avoid  the overheating. 
:(

---

### Post by estherios on 2010-03-03
Guys,  Does this issue happen on other Linux flavors?

---

### Post by wafflemelon on 2010-03-04
I have tested this on Linux Mint, but I believe it's the same for every distro.

---

### Post by derekmbarnes on 2010-03-14
> **davesmith said:**
> Toshiba laptops are notorious for having overheating issues. This is usually a hardware problem associated with the main CPU heatsink radiator vanes getting clogged with dust.

Didn't we go over this? The problem has nothing to do with dust buildup or hardware layout; we're talking about brand-new, straight-out-of-the-box laptops that haven't been used enough to have such issues. Also, we don't have this problem in Windows.

Anyway, I haven't checked on the DSDT issue; it is at this point that I admit I'm a lazy half-wit who has a habit of not following through on stuff like that, even if I have every intention of doing so. Fortunately spring break starts soon, so I might have better odds of motivating myself to investigate over the next two weeks.

Almikul, you said updating the kernel fixed the problem for you. When did the 23.19 update come in? I'm trying to remember if I already had that installed or not when I last had Ubuntu installed. (I think I might have been up to 23.17, but I don't accurately recall.) Also, we should figure out what happened to the ACPI data when you installed that update; might be a question for the devs.

---

### Post by davesmith on 2010-04-02
I think if this is happening with out-of-the-box new tosh machines then you might consider talking to the developers. A number of ppl have overheating probs with toshibas, it might be worth it

I run hardy heron on a Tosh A30 Satellite, the h/s vanes are always getting blocked.

---

### Post by c00lwaterz on 2010-04-03
I have same issue (high temp). I tried debian 5.04, freebsd 8, linuxmint8, ubuntu 9.1, etc but no luck.

until now i am looking for solution and waiting hoping to be fix.

currently using windows vista to avoid high temp.

---

### Post by beebuntu on 2010-04-18
I, also, have a Toshiba Satellite M505 with Intel Core2 processor, and have the non-working fan heat problem when running Linux for the last 7 months (since it came out of the box).  Having just discovered this thread, I am interested in a permanent fix.

When awakening the computer from the sleep mode, the fans works fine.  I am not sure of the temperatures involved, but there is never a problem in Windows VISTA  with the machine even getting warm.  Linux just has this problem.

I would be interested on anything new discovered about this problem.

Thanks,
bob

---

### Post by wafflemelon on 2010-04-18
beebuntu,

Everything we know is covered here. However, one thing that could work is installing and configuring the omnibook module, experimenting with different ectypes. If you (or anyone else) is willing to try, this is the procedure:

1. Install omnibook module: [http://andrewm.info/software/guides/27-bluetooth-support-for-toshiba-laptops-on-ubuntu](http://andrewm.info/software/guides/27-bluetooth-support-for-toshiba-laptops-on-ubuntu)
(ignore the bluetooth business)

2. Load the module with ectype=1
sudo modprobe omnibook ectype=1 && dmesg | grep omnibook && hcitool dev

3. If your fan doesn't start:
$ sudo make unload   # alternatively try $ sudo modprobe -r omnibook

4. Repeat. Go back to step 2, but increment ectype (ectype=2, then ectype=3 and so on). Until the fan starts working, repeat until ectype=16.

If this doesn't work, then I guess it's up to the Ubuntu devs or Toshiba/Phoenix.

---

### Post by Druke on 2010-05-03
has anyone made any progress? I also have the AMI bios, not Pheonix.

I was working on this around February and got it slightly use-able by setting a boot option to make the fans run all the time. I gave up when I read something about the issue being related to the ATI card inside and interactions with the ATI drivers. I can't find the source anymore :( . Hope thats helps a bit.

---

### Post by estherios on 2010-05-03
[FONT=&quot]Has anybody tested this on 10.04?  Or there is no hope yet?:confused: [/FONT]

---

### Post by Druke on 2010-05-03
I have wifi working in 10.04, but fans are still funny.

---

### Post by Druke on 2010-05-03
actually.... that was on 64 bit.

Fans seem to work on 32. (I think it's getting the bad trip points though, because it seems like it is still getting to hot)

---

### Post by wafflemelon on 2010-05-05
> **Druke said:**
> actually.... that was on 64 bit.

Fans seem to work on 32. (I think it's getting the bad trip points though, because it seems like it is still getting to hot)

Have you tried playing with acpi_osi (as explained earlier in the thread)?

---

### Post by cis.ash on 2010-05-05
i have Toshiba satellite pro l300,,, i found that if i removed "Acpid" from the package manager and install "toshutiles" and "toshset" will fix the problem, after having a very high temperature (it was like 80 sometimes ) now it's stable on (50-60) degree.
i think i'ts solved :D

---

### Post by Druke on 2010-05-05
I have fiddled with them, but I'm kind of mish-mashing posts. Could you make a list of options to try?

To be more clear, I did acpi_osi=Linux, acpi_osi="Windows 2006" . I'm not sure how to do Multi-word entries, based off this post [http://ubuntuforums.org/showpost.php?p=8743692&postcount=46](http://ubuntuforums.org/showpost.php?p=8743692&postcount=46) . Anyways all the trip points where the same I pipped them to a text file so I could compare the default "Linux" and ""windows 2006"". I am pretty sure I messed up the windows 2006 one though.

I'm slightly curious if certain trip points are targeting fans that do not exist. It seems the longer I work on it, the more it starts to work (yay!), but at the same time, it could just be that the laptop is getting hotter, setting higher trip points that actually work. Because when I come back to it I am at square one.

while writing this and doing some tests, there was post #71. I'm going to give it a try, though from what someone said earlier, 50 degrees is still a bit hot.

also: powersaved is no longer in the repos, so I couldn't try that.

---

### Post by Druke on 2010-05-05
toshutils is for apm, and not acpi. It says that it will work on older model laptops.

I bought mine in December, so I don't think the m505 qualifies.

However, toshset is in my install by default! and reading it's detaisl says:

> Toshset is a command-line tool to allow access to much of the
Toshiba laptop hardware interface developed by Jonathan Buzzard. It can do
things like set the hard drive spin-down time, turn off the display
and set the fan speed without the help of the kernel.Toshset requires an experimental version of the toshiba_acpi kernel module
with an ACPI-enabled kernel. Otherwise it works only if the laptop supports
the old APM BIOS. (The last of these was produced something like 5 years ago)
Please read README.Debian how to install the experimental version of the
toshiba_acpi kernel module. (Ubuntu users don't need it)

yet when running "toshset" it says  "required kernel toshiba support not enabled"

to be clear, this toshset appears to be doing nothing.

---

### Post by cis.ash on 2010-05-05
to post #72 
i think that the crit degree is 110 or something close to that, so 50 degree is cool enough :D

---

### Post by cis.ash on 2010-05-05
toshutils will also not fix ur problem 

This is a collection of utilities to control a Toshiba laptop. It includes
programs to turn the fan on and off, to view the power mode, and to set
the supervisor password.

Note that these utilities work with APM features in the Toshiba BIOS.
If your laptop's BIOS only supports ACPI and not APM, then toshutils will
probably not work for you. [B]Toshiba's newer models tend to support ACPI
only, and therefore toshutils will not work with them.[/B]

---

### Post by Druke on 2010-05-05
I got that, I'm looking more closely at the '*toshset*' package. It **does** work with acpi if the kernel is configured right. And at the bottom of the package details it says

> Please read README.Debian how to install the experimental version of the toshiba_acpi kernel module. (Ubuntu users don't need it)

Perhaps there is a boot-up flag that makes the kernel work with toshset.

---

### Post by Druke on 2010-05-05
That may be a dead-end. Trying to enable the toshiba_acpi stuff gives an error
> FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.32-21-generic/kernel/drivers/platform/x86/toshiba_acpi.ko): No such device


This may mean that newer toshiba models don't use that system, or that something in newer ubuntu versions breaks that module.

I'm not qualified to say either way.

So moving on...

We seem to have to different camps of experiences with the m505. There are people who can get fans working by suspending and resuming. And then there are people who can't get the laptop to resume and thus check if the fans work(me). This also seems to correlate to the people with the AMI bios(me), and the Pheonix bios.

Has anyone else noticed this?

---

### Post by cis.ash on 2010-05-05
> **Druke said:**
> I got that, I'm looking more closely at the '*toshset*' package. It **does** work with acpi if the kernel is configured right. And at the bottom of the package details it says



Perhaps there is a boot-up flag that makes the kernel work with toshset.
  

i wonder how did it work with me :P

ps : i also removed acpid package, maybe the BIOS is controlling the fans rights now not the OS it self

---

### Post by Druke on 2010-05-05
I also removed apcid, but I think our laptops may be to different to compare experiences.

---

### Post by Druke on 2010-05-05
For the omnibook stuff, do I need to reboot after each modprobe?

---

### Post by wafflemelon on 2010-05-06
> **Druke said:**
> For the omnibook stuff, do I need to reboot after each modprobe?

Supposedly it has an instant effect.

[QUOTE=cis.ash]to post #72 
i think that the crit degree is 110 or something close to that, so 50 degree is cool enough
[/QUOTE]

Windows runs between 35-45, so I think this should be our goal. Especially since Ubuntu normally uses less resources :)

---

### Post by wafflemelon on 2010-05-12
Tested omnibook with all ectypes, no immediate results.

However, acpi_osi="Linux" on Lucid Lynx (32 bits) works. BUT, the trip points are still too low, idling at 60C, which still isn't good.

---

### Post by derekmbarnes on 2010-05-16
Personal update: I thought you guys might like to know that I am now experiencing what is essentially the same problem...in Windows 7. Yeah, for some reason the system that was made to run PCs and that PCs are made to run is now getting just as bad. Fortunately the cooling pad I got seems to be helping somewhat. (I also discovered my left hand is about half as sensitive as my right and can barely detect the heat. :P )

Since at least one of you seems to be working with Lucid now, I wouldn't mind an overview of everything we've tried in Karmic being tried again. I'd especially like to know if user control of ACPI has been restored.

---

### Post by strikoo on 2010-05-16
try
sudo gedit /etc/default/grub

Find this line:
GRUB_CMDLINE_LINUX=""
and change it to:
GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"

Save

sudo update-grub
sudo reboot

It should work now after reboot.

---

### Post by badrra on 2010-05-26
Mine is an old Toshiba A70 Phoenix bios. Just like you, CPU temperature used to go up to 80 and then it turns off automatically. 

Now, it only stays at 40, slightly cooler than my HDD temp of 41. Since I have a Phoenix bios, i had to download and install the omnibook module. At first i thought that by controlling cpufrequency (ondemand) or fixing the cpu frequncy to a certain limit will do the trick. Well it didn't. it will just stay on a little bit longer. 

When I downloaded the latest version of omnibook, I noticed one of the modules includes "Cooling" so i turned that on and since then my cpu temperature stayed at 40 what ever i do. Even if i play games. 

There is a cooling system\preference that needs to be turned on for it to work so i guess omnibook did the trick.

---

