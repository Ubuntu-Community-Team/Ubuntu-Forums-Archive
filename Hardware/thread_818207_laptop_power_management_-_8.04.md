---
title: "laptop power management - 8.04"
date: 2008-06-04
forum: Hardware
---

### Post by philheaton on 2008-06-04
Hi

Sys specs:

Samsung X22 Laptop 
Intel Core2 Duo T7500 2.2GHz
Intel 4965AGN WiFi
ATI Radeon HD 2400 128MB Dedicated
2GiB RAM

Ubuntu 8.04 Kernel 2.6.24-18-generic

Full lshw text attached.

Problem seems to be with the power management features. This has been a consistent problem since Hardy's debut. I was hoping the new kernel released into the repos yesterday might have helped - but no. 

The specific issues are:

** - Laptop Panel Brightness**

Neither the Gnome applet or my function keys can alter this in any way. Gnome applet states that it "Cannot Get Laptop Panel Brightness" and Ubuntu doesn't even seem to recognise the Fn/Up Fn/Down keypresses. Consequently the screen brightness is set to 100% all the time.

** - Battery Time    **

The battery isn't great at the best of times, its a 4-cell thing, nevertheless it can attain life of 2:45hrs under Vista but I'm lucky to get 1hr from it under Ubuntu.

** - Heat**

The processing cores consistently reach 50C-60C idle and up to 80C whilst web browsing, checking emails etc (menial load). Again under Vista I need to be playing Doom3 or HL2 to get anywhere near these temps. Under normal usage (with Vista) I reach about 40c-45C. Strangely enough, under Ubuntu, the laptop also gets hotter when running under battery power.

I have searched around the forums and the web for some weeks now in order to find solutions to these problems, but have so far had limited success. The system is fully patched, I have run "top" from the cmd line in order to see if there was any resource hungry apps chewing through the system, but no.

I'm at a loss. Do I need to file an official bug?

Cheers.

Phil.

---

### Post by FreakTech on 2008-06-04
I am having the almost exact same issue.  I am getting a little better battery life, but it is a 6 cell battery.

---

### Post by omycron on 2008-06-06
I bought almost the same Notebook - a Samsung X22 - few weeks ago and i've got exactly the same problem ...

I tried download other Power-Management-Tools, but they don't work either ... :(

---

### Post by sdennie on 2008-06-06
These sorts of problems are sometimes caused by BIOS issues.  If the machine was previously working with a previous version of Ubuntu and it no longer is then, certainly, Hardy is probably to blame.  Unfortunately it's possible to compile a DSDT (more or less the functionality that the BIOS exports to the OS) in a non-standard way (this is especially common for vendors that don't care at all about linux (e.x. Toshiba)) and so sometimes it's simply not possible for linux to do the right thing.  

If the machine has not worked with any version of Ubuntu, I would see if there is a BIOS update available for your machine.  If that still doesn't work, there are more extreme measures you can take (fix the bugs in the DSDT).

---

### Post by philheaton on 2008-06-13
yeah, i thought it might be a bios issue too, but i have the latest phoenix bios installed. 

after much digging around on the forums and web, i did this:

1. installed powertop. this gave me some indications of cpu wake up events that were detrimental to power saving

2. implemented the changes by editing the /etc/rc.local file and adding new files to /etc/acpi/battery.d directory

3. installed and configured the most recent version of laptop-mode (for debian - not ubuntu - seems to work better).

all this has given me an extra HOUR battery life.

cheers

phil

---

### Post by sdennie on 2008-06-13
Another site you'll want to check out for power savings on linux is [www.lesswatts.org](www.lesswatts.org).  It has the same sorts of tricks that powertop tells you about but, a lot more of them and better explanations.

---

### Post by philheaton on 2008-06-14
cheers vor. i have briefly checked out that site before, maybe its time to revisit and go through it in a little more depth. 

about my panel brightness - keys still don't work, but managed to implement a script and link it to a couple of custom applets in the gnome panel, so i now have full controll over panel brightness again.

also managed to shave a few degrees C from the heat by adding a few missing lines to the /etc/modules file. now laptop running comfortably at 45-50C.

i guess its all there if you look, would be nice to have these tweaks implemented in the install process, but until vendors start to actually converse with kernel developers, i guess we'll have to write the scripts ourselves. 

bring on open-source hardware i say!

cheers.

phil.

---

### Post by molochi on 2008-06-15
Under windows most recent notebooks have a bit of software (usually written by the manufacturer) that limits the maximum speed of the processors, when using a battery, to 600MHz(P-M) or 800MHz(C2D). Even Speedstep was a PIII thing. This software can also select other speeds and can often even turn off parts of the CPU or reduce the voltage supplied to the CPU to maximize battery life. Without CPU throttling and voltage regulation we won't see the 3+hrs of notebook uptime found on most windows notebooks.

Ubuntu, as evidenced by Powertop, allows the CPU to run at max frequency whenever any program "wants" more speed. It also shows that the newer Linux kernals are allowing CPUs to enter lower power states when the power isn't needed. Unfortunately, the middle ground (strictly limiting cpu frequency and voltage) isn't there by default yet. 

There are efforts being made to provide throttling software for linux like cpufreqd (search for it in your package manager) that will enable you to get more precise control of your power usage. But they do require editing of .conf files. I haven't found anything really simple to use.

---

### Post by philheaton on 2008-07-01
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

### Post by sdennie on 2008-07-01
> **molochi said:**
> 
Ubuntu, as evidenced by Powertop, allows the CPU to run at max frequency whenever any program "wants" more speed. It also shows that the newer Linux kernals are allowing CPUs to enter lower power states when the power isn't needed. Unfortunately, the middle ground (strictly limiting cpu frequency and voltage) isn't there by default yet. 


Which is the most efficient behavior for battery life on newer CPUs.  Limiting the CPU frequency is not as efficient as "race to idle" regardless of whether or not you are using undervolting.  The difference in power usage between the CPU C0 and C3/C4 states is so extreme that the only way it makes any sense to run the CPU is to run as fast as possible so that you can get back into the deepest sleep state as soon as possible.

---

### Post by waapwoop1 on 2008-07-02
Whenever a thread like this pops up, people try to blame everyhting but hardy.

Almost everyone has stated that under windows it runs cooler. Even with powertop etc, its not good enough. On ac power i could keep it cool running at half processor speed, but that is really ridiculous.

I bought a laptop cooler in the end that keeps it as cool as XP, because i want to use Ubuntu to learn it, etc. But don't want to fry my laptop.

Ubuntu, or something in it is to blame. Everyone couldn't have a faulty fan only when ubuntu is running, that suddenly fixes itself under XP.

---

### Post by Hurrz88 on 2008-07-02
Is there a possibility that the internal cooling fan is not being registered, or that the fan doesn't turn up higher? My laptop has been getting increasingly warmer, and when I boot into Windows I clearly hear the fan whirring, but in linux I can hear the fan but it is not nearly as loud as in Windows.:confused:

---

### Post by philheaton on 2008-07-02
fan control is something i've been working with on my laptop. i tend to run at about 10C higher in hardy than in vista, unfortunately, the phoenix bios coupled with proprietary microcode is apparently preventing me from accessing the bits of the laptop that i need to access. refer to my previous post.

---

### Post by philheaton on 2008-07-02
> **waapwoop1 said:**
> Whenever a thread like this pops up, people try to blame everyhting but hardy.

Almost everyone has stated that under windows it runs cooler. Even with powertop etc, its not good enough. On ac power i could keep it cool running at half processor speed, but that is really ridiculous.

I bought a laptop cooler in the end that keeps it as cool as XP, because i want to use Ubuntu to learn it, etc. But don't want to fry my laptop.

Ubuntu, or something in it is to blame. Everyone couldn't have a faulty fan only when ubuntu is running, that suddenly fixes itself under XP.

you've not been listening.

---

### Post by Hurrz88 on 2008-07-02
So then what you are saying, or rather what most people are saying, is that the problem lies in Hardy? So, would there be a bug to fix in the updates in the future? Like Waapwoop said we can't all have faulty fans. So until then we just wait and hope the updates fix it?

---

### Post by philheaton on 2008-07-02
> **Hurrz88 said:**
> So then what you are saying, or rather what most people are saying, is that the problem lies in Hardy? So, would there be a bug to fix in the updates in the future? Like Waapwoop said we can't all have faulty fans. So until then we just wait and hope the updates fix it?

the problem isn't with hardy, its with laptop vendors and the linux kernel. this is a problem you'll experience with all linux distros. i refer you to my previous post: [http://ubuntuforums.org/showpost.php?p=5300470&postcount=9](http://ubuntuforums.org/showpost.php?p=5300470&postcount=9)

---

### Post by Chopdoc on 2008-07-22
I found this while researching my own (mild) notebook power management problem in 8.04. Hold on for the ride:

The problem is multifactorial.

As you know, most notebook "vendors" do not manufacture notebooks...they outsource the to the ODMs.

They do, however, add some things to BIOS...often incidental things like splash screens...or more malicious things like memory and CPU limitations.

That being said, there is more "standard" in the BIOS and hardware and less "proprietary" than many would have you believe.  In fact, that is so much the case that people will even these days tell you that you cant upgrade certain hardware or change the BIOS.  In many cases that simply isn't true, it's just the propagation of misinformation.  Sad to say that there are still businesses charging $30 to change a BIOS splash screen.

Notebooks, for the most part, are very very much like desktops.  It is where the exceptions to that statement are that we have problems.  The fact that there is nothing in the way of cross reference for parts and a great deal of technical info is difficult or impossible to get and the problems are compounded.

We need to place some blame on the "community" (us).  In researching my problem (and others in the past) I find issues.

1.  People on message boards giving incomplete information: Make, model, BIOS revision, etc.
2.  People ("experts") writing articles that they leave UNDATED.  And worse than that, often disseminating misinformation regarding notebooks.

3.  The perpetuation of the notebook myths: "OMG!....that's a notebook....you can't do that (overclock, upgrade CPU, properly run Linux, etc.) with a notebook!"  Like it's some kind of magical device running on etherial mojo juice.

Yes, the problem lies with the Linux kernel.....and the OEM.....and the ODM....and the BIOS writer....and the firmware writers.....and the chipset/CPU manufacturers.....heck we can even blame Bill Gates.....and, in part, us.

Where does that leave me?

Three places:

1.  Please support Coreboot (LinuxBios), and open design.
2.  I still have power management issues with my laptop.
3.  Please excuse the long post, I am frustrated.


Oh, and for the record,  am dealing with a Compaq M2108US, BIOS F.21, Ubuntu 8.04 with updates current as of this date.  In general it works very well on Ubuntu, easier and faster installation than Windows of course...with everything working.  Power management has issues though.  It does not run hot, but battery life is too short.  The processor does not seem well controlled.  No software seems to be the issue (nothing is hogging), the main thing seems to be processor control.  In addition there is the screen brightness issue previously mentioned in this thread.  The buttons controlling brightness do work, but the software does not "find" my screen....so it does not dim automatically.

There is always hope:  'Ol Mikey Dell runs Ubuntu on his personal notebook, and has for years.

I build, modify, upgrade, hotrod, and otherwise mangle laptops old and new as a hobby.  I have more of them than I care to say, running various operating systems.  I like them not only to be fast and powerful but I want everything to work.  Generally I achieve that.  I will fix this problem if I have to use a hammer to do it. Any help would be great.

---

### Post by medley on 2008-07-22
> **philheaton said:**
> It seems to me the problem with laptops is the fact that they are all so very different. The average desktop PC is simply a collection of generic and widely used/interchangeable elements, such as a motherboard, graphics processor, HDD controller, etc and as such are pretty easy for kernel developers to access all the various microcodes and incorporate FOSS versions within the kernel space. Even proprietary hardware such as ATI/nVIDIA can easily be incorporated.

Laptops on the other hand are different beasts and are custom made to specifications set out by their manufacturers, be they Dell, Samsung, Sony etc. These companies work closely with Microsoft in order to achieve the best compatibility with MS operating systems and go through hardware testing with MS products before inclusion on the MS HCL. This is evidenced by the little "Windows Ready" sticker that comes on the machine. It means that every piece of hardware and its configuration has been specifically tested by MS to be 100% compatible with whatever version of Windows is on the sticker.

Linux developers on the other hand do not receive the same luxury and so pretty much have to make do with what they've got. You'll therefore find that most (if not all) Linux Distros will work exceptionally well on generic hardware you can find in a Desktop system, but not the same with laptops - its simply impossible to cater for every eventuality.

For example, in Intel driven laptops (those with integrated graphics processors. Intel are very pro-Linux and are working very closely with the Xserver team to develop better grained controls) such as those that Dell use, laptop performance is clearly superior to so called "high-end" laptops with a lot of different component manufacturers, dedicated GPU chips and graphics RAM. This is because kernel devs aren't privy to the exact configurations and therefore can't write specific micro controller code to deal with issues such as heat dissipation, battery management, fan control etc.

I could go on, this is a deeper issue than I've outlined here, but that's the gist. Until hardware/laptop manufacturers open their doors a little or even go so far as to submit code to the kernel devs, we are going to be stuck with these niggling issues.

That said, if Linux "just worked", there'd be no reason to get your hands dirty trying to fix it and I for one would know a LOT less about computers if I just trusted it to the "experts". This is what Linux is all about, its transparent enough for most people who have an interest to jump into the workings of it, improve it and submit their solutions to the community - thats how Linux evolves.

cheers

Phil.

Mind you, would be nice to have laptop-mode to be turned on by default on a laptop installation! I installed the latest Debian version instead of using the one in the Hardy Repos, configured it and have gone a LONG way to achieving the performance I need on my laptop - temps now a lot better and an extra HOUR battery life as well. I also uninstalled powernowd in favour of cpufreq and life's good!

P.

Wow, this is a very interesting discussion. I had just installed Hardy last week on my Dell m1330, replacing Vista, and it seemed to me that I had all of a sudden lost about an hour of battery life but thought I must have been imagining things.

---

### Post by sdennie on 2008-07-22
> **medley said:**
> Wow, this is a very interesting discussion. I had just installed Hardy last week on my Dell m1330, replacing Vista, and it seemed to me that I had all of a sudden lost about an hour of battery life but thought I must have been imagining things.

It seems most people are reporting a difference in power between Windows and Ubuntu around what you are seeing.  This is generally due to the vendor tweaking the laptop for Vista however, with not much work, your particular laptop can be tweaked to equal or exceed Vista battery life: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

---

### Post by bakarocket on 2008-07-25
I am thoroughly enjoying having Xubuntu Hardy on my Panasonic CF-W5, but I also have the same problem with the hot keys. I found a link that describes how to do it, but it involves a whole lot of newbie brain melting instructions, and the advice above with ```
sudo echo -n "some number here" > /proc/acpi/video/VID/LCD/brightness
``` just didn't work.

I'd rather learn it than have it taught to me, but I'm not sure if I should start at kernels or scripts or just by banging the laptop against my head until one of us dims.

---

### Post by sdennie on 2008-07-25
> **bakarocket said:**
> I am thoroughly enjoying having Xubuntu Hardy on my Panasonic CF-W5, but I also have the same problem with the hot keys. I found a link that describes how to do it, but it involves a whole lot of newbie brain melting instructions, and the advice above with ```
sudo echo -n "some number here" > /proc/acpi/video/VID/LCD/brightness
``` just didn't work.

I'd rather learn it than have it taught to me, but I'm not sure if I should start at kernels or scripts or just by banging the laptop against my head until one of us dims.

When you use sudo like this, you have to use it slightly differently than normal so that the redirection works.  Try:

```

sudo sh -c "echo some_number_here > /proc/acpi/video/VID/LCD/brightness"

```

---

### Post by bakarocket on 2008-07-25
> **vor said:**
> When you use sudo like this, you have to use it slightly differently than normal so that the redirection works.  Try:

```

sudo sh -c "echo some_number_here > /proc/acpi/video/VID/LCD/brightness"

```

Thanks for the quick reply! I tried the above, and it doesn't break, but it doesn't do anything either. The first command just gave me an invalid argument, but the code below (matching my folder structure)

```

sudo sh -c "echo 50 > /proc/acpi/video/GFX0/LCD1/brightness"

```[/QUOTE]

Just seems to run and then do nothing. I wonder if I should just try the kernel patch thing? Maybe it would help with the heat problem.

---

### Post by philheaton on 2008-08-12
Just as a sideline, the brightness Fn key thing appears to be an APCI problem. If you boot with the acpi-off option, the Fn keys regain control over the screen brightness. Not a usable solution though as you lose all other power saving features.

---

### Post by bakarocket on 2008-08-18
As a sideline to philheaton's sideline, I installed gnome and just use xbacklight from the command line. It was a very simple solution, though it would be nice if the Fn keys worked.

---

