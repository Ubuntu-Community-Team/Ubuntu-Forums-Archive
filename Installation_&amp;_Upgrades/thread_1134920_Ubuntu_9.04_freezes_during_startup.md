---
title: "Ubuntu 9.04 freezes during startup"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Natovr on 2009-04-24
Hello,

I've just installed Ubuntu 9.04 via the update manager, and tried to start it, but it freezes during startup :( I can't start anything, only the mouse moves, and nothing else works. This happens just after I log into Ubuntu and all the startup apps are running.

Does anyone have an idea how to fix this? I can access all my Linux partitions from Vista and can modify configuration files, or I could just use recovery mode.

By the way, the process monitor panel thingy shows high I/O Wait on the processor just before it crashes. At least that got to load...

---

### Post by Sef on 2009-04-24
Can you boot into safe mode?  It is under options at the login screen.

---

### Post by Natovr on 2009-04-24
Yes, that works nicely :D

---

### Post by Black_Wolf_92 on 2009-04-24
try a few of the recovery options first like the dpkg one etc. If your still facing a blank screen, try the following.

Boot like normal (not recovery mode) and hit CTRL ALT F2. This will open up a terminal for you to log into. Type the following lines (usually my general FIX IT UP commands when there are broken packages flying around)

> 
sudo apt-get autoclean
sudo dpkg --configure -a

The chances of these fixing something aren't great but its worth a shot if you still can't get things working lol. Most likely issue is just a graphics card driver screw up, these are touchy to solve, but if you still can't fix, just reply and i'll do my best to help you more.

Also, if your sus on the codes I posted, i'll just do a brief explanation so you don't think i'm trying to fry your system lol.

sudo apt-get autoclean - this cleans out orphaned packages i.e things that may not have installed properly on the upgrade, or packages without a use that are just conflicting with other stuff.

sudo dpkg --configure -a - simply reconfigures the package manager, refreshes preferences etc. Of course its more complex than that, but basically both these commands are just quick checks for package errors and conflictions

---

### Post by ITA003 on 2009-04-24
I have same problem too, also with Ubuntu/Kubuntu (this fresh install)

I have a ATI card RV350 (Radeon9550) (get from command lspci) and don't use proprietary driver.

At this link there is mi Xorg.0.log file: [http://launchpadlibrarian.net/25904888/Xorg.0.log](http://launchpadlibrarian.net/25904888/Xorg.0.log)

I will try the dpkg configure command... but I had the same problem with RC version of Ubuntu and the dpkg command didn't work

---

### Post by binwiederweg on 2009-04-24
Same here with a mobility X600 with ubuntu 9.04

Before the login screen was supposed to start, the screen froze while displaying a mixture (!) of 

[LIST]
[*]my "hp"-logo from the beginning [before the kernel is started !!]
[*]the upper task bar from GNOME, even though i haven't logged in yet !
[*]and the login screen itself
[/LIST]
That is so weird. How can this even happen?! My Xorg.log looks similar to the one above, but I can't paste it because I can't login :-(

I also tried the dpkg-reconfigure-stuff and many other thigns such as changing the display-drivers in xorg.conf, but nothing worked. 

Must be something with graphics-driver ...

Also, ctrl+alt+backspace doesnt work which is why i had to reboot 100x ...
Perhaps it has something to do with this:
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.

I'll install 8.10 again now ...

---

### Post by sub.mesa on 2009-04-24
You have to update your GRUB. Boot into recovery mode then wait for the menu to appear and select the option to update GRUB. Then reboot (choose root shell option and type "reboot") and you should be able to boot fine. The message Starting up... still gets displayed for several seconds, but after that i got the Ubuntu loading screen again (much like XP does).

Hope this is worth trying. It shouldn't erase any grub configuration (which is in menu.lst file), just update GRUB itself.

---

### Post by binwiederweg on 2009-04-24
@sub.mesa: I suppose that wasn't for me, was it?

---

### Post by sub.mesa on 2009-04-24
No, just people having that "Starting up..." message displaying indefinately, after upgrading from 8.10 to 9.04. So the GRUB update may fix those issues, but someone could be having a totally different issue. But if it doesn't load after grub, i don't think any installed packages could affect that. Its before the filesystem is mounted. Right?

Anyway my issues are fixed by the method i described, just wanted to share. :)

---

### Post by Natovr on 2009-04-24
ok :) thanks.. I'll try that

EDIT: Black Wolf, that.. almost worked >_< I did those commands, and started up into normal-mode. It worked nicely and I thought everything was going well, till I tried opening firefox to tell you. It stopped right before I was about to click. I then pressed "ctrl-alt-F2", and my monitor went into a spasm.. it showed up strange colours and squares and kept flashing into different sized rectangles and colours. No, I wasn't on LSD :)

---

### Post by ITA003 on 2009-04-24
> **Black_Wolf_92 said:**
> 
sudo apt-get autoclean
sudo dpkg --configure -a
Doesn't work

Also the GRUB loader update doesn't work. :(

---

### Post by microman777 on 2009-04-24
Got the same problem. Looks like 9.04 is a disaster!!!! 

Guess I'll have to go back to 8.10!!!!!!!

---

### Post by Natovr on 2009-04-24
!!!!!!!!!!!! :)

We could wait for a few bug fixes to come out.. that's how Linux and Open Source works :)

Besides, failsafe mode works fine for me.. for basic tasks at least

---

### Post by ducheus on 2009-04-24
I upgraded my Ubuntu 8.10 in a Dell Latitude D830 and I have the same problem. The screen freezes during boot process.

I restarted it in recovery mode and the behavior is the same but pressing Ctrl-Alt-Del I can get the recovery menu. I run fsck and then xfix and then resume and the boot process ends without problems.

Reading the logs, I found that the file system is marked as bad and mounted as Read only and in that condition the boot process is frozen.
In other machine I have, a desktop, the upgrade process ran flawlessly and it is working very well just now.

If somebody have a clue to solve this issue in my laptop it will be more than welcome. I don't like the idea to reinstall 8.10

Hector

---

### Post by Natovr on 2009-04-25
I'm sticking with Vista now -- the same problem just happened in Failsafe mode :/

I'm thinking about installing Linux Mint in May, when it comes out if I can't get this problem solved

:confused:

PS: I think we're all having slightly different problems here
Just to clarify, my Ubuntu freezes after I logged in, and while my startup programs are starting (Transmission, Thunderbird, and Firestarter)

---

### Post by ro_dm on 2009-04-25
the same problem here: i am trying to install 9.04 and it freezes 10-20 sec after booting (logging in). the machine is a fujitsu - siemens amilo k7600. another problem is that i cannot install 8.1 (iit freezes when booting, when starting hald, i don't know if the cause for these 2 errors is the same)... i wanted to dump win xp...

---

### Post by Natovr on 2009-04-25
I think I'll report a bug on Launchpad, when I have time

Others should too

I'm waiting for Linux Mint Gloria to come out, so it might be a good idea to try another Linux :) you can always go back to another linux -- just copy or keep the home partition and make a list of stuff you installed (I think there is a command for that somewhere)

---

### Post by lucasbmm on 2009-04-25
Hello all

I´ve got the same problem here, but my Ubuntu freezes less than five minutes after login. I just can't use it. I am on Vista now, wich I have installed as a last resource.

I am running a Core 2 Duo and a ATI Radeon X800 GTO graphic card. Also, there's no restricted drivers for ATI avaiable for 9.04. I don't know if this problem is caused by the video card.

Does anyone know if the ubuntu team is working on the problem?

And how about this Linux Mint you were talking about?

thanx

---

### Post by Natovr on 2009-04-25
Hi,

Yeah, I'm using an ATI chip too. ATI 1250, which used to use FGLRX. Since that's a common factor, maybe that's what caused the problem. 

Linux Mint is Ubuntu, but basically it is designed to work more out-of-the-box. The newest version is being released in May, no specific date announced.. It has more programs pre-installed than Ubuntu, but in the US and Japan it releases a patent-friendly version, with less patented products.

---

### Post by lucasbmm on 2009-04-25
Maybe this bug really has something to do with the video card. I was able to run Ubuntu for at least an hour without any problems, just backing up my files (I think I'm gonna try Linux Mint or reinstall Intrepid version).

But my whole system froze just a few seconds after I run Firefox. I'm back on Vista now.

Is there any news on this subject? Any tips?

Thanx
Lucas

---

### Post by Natovr on 2009-04-26
Ubuntu just worked for me.. strange, because nothing changed between 2 days ago and now..

maybe it will freeze again in less than an hour :/

PS: One thing, I left it to start this time.. I didn't close the startup programs while they were busy starting this time. I waited them all to open and closed them when I came back. Wireless didn't work though. It didn't work before sometimes, but I hibernated and started up again, and it worked alright.

---

### Post by ro_dm on 2009-04-26
i cannot report a bug since my installation (amilo fujitsu k7600, video card S3 ProSavage8) freezes 10-20 seconds after booting and the recommended reporting is by using a specific application, run on the ubuntu erroneous installation.

maybe others can do this... i hope a solution for your problem will solve my problem too...

---

### Post by Natovr on 2009-04-26
I just installed an ATI graphics driver which I found here,
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
time will tell if it helps or not

---

### Post by lucasbmm on 2009-04-26
I don't think I can use Ubuntu to download the driver, but I'll give it a try.

And there's nothing to do with firefox, as I said on my last post, 'cause it happened when I was running synaptics. Now it freezes all the time.

To be sure it was not some problem with my machine, I check for bad blocks on both my HD, and they´re all ok.
After that, I reinstalled the whole system but bothing changed.

Anyway, there are a bunch of bugs reported on launchpad about this problem, each one describing a different symptom since, I guess, Alpha 3. 

I can't understand how come they release a so unstable system, so untested. I guess they're loosing control. There are too many users, it became a big enterprise wich they don't know how to manage, and the quality is going down.

It's a major disaster for me. I'm installing Linux Mint today if the driver you suggested does't work.

Thank you.

---

### Post by mialjojo on 2009-04-26
Kernel 2.6.4.24.22 works for me. Kernels 2.6.4.27 and 28 give me a scrambled screen and lockup.

Do you think the GRUB update will fix the problem?

---

### Post by lucasbmm on 2009-04-27
> **mialjojo said:**
> Kernel 2.6.4.24.22 works for me. Kernels 2.6.4.27 and 28 give me a scrambled screen and lockup.

Do you think the GRUB update will fix the problem?

Neither kernel worked for me. Nor did updating grub.

Also, the driver I found for my graphic card seems to have some version issues with my ubuntu and it simply doesn`t install.

I guess this jackalope release is a mistake. By the way, jackalope doesn`t even exist, as far as I know.

I`m done with it. I`m running Mint now, wich looks nice. I just hope Mint 7 won`t have the same mistakes ubuntu team did on 9.04.

Thank you all.

---

### Post by Natovr on 2009-04-27
Ok, I've given up on Ubuntu :( just when I thought it works...

I installed Chromium (or what I thought was) which is supposed to be the open source web browser which Google Chrome is based on.. but it turned out to be a retro-ish game with some 3d effects. I closed it, and suddenly the screen went blank. I forced restart, tried to start Ubuntu, but couldn't even log in, because the weird color thing started... 

A day later I tried Ubuntu again, and it told me to run FSCK "manually" on sda6. I ran it without properties and it started on sda5.. so I stopped it and ran it on sda6 first, then sda5. It asked way too many questions, so I cancelled that and ran with -y. It "fixed" a load of stuff, and I restarted.

Then, it stopped half-way through loading Ubuntu and two LEDs on my laptop side started flashing (I think num lock and caps lock).

I'm confused and angry, and I think that Jaunty is to Ubuntu like Vista is to Windows.

I will download Mint 6 now, and see if Mint 7 has any problems.

I think my home folder is gone :( my coursework is on there! (EDIT: phew.. nope)

---

### Post by hzrunner on 2009-04-27
I've got basically the same problem can get it going by selection ther kernel 2.6.27-11 rather than 2.6.28-11. I don't really want to do this manually every time I start up, how do I change the grub file start-up file or whatever this is called?

Thanks in advance.

---

### Post by frbe0101 on 2009-04-28
Simple lesson, never install the newest version, wait a few months. I learned that the hard way before and I'm sticking with 8.10 until this kind of crap dies down.

---

### Post by DJ_Crash on 2009-04-28
i have a problem with jaunty on my intel pentium 4 2.53ghz machine running 1.52GB ram upgrade from 8.10 -> 9.04 went fine boot time is somewhat 5mins even windows vista dont take that long

anybody know what is causing this very slow boot time or how to fix it?

8.10 loads up in 25seconds ish / same as win vista

just tried same on my AMD 64 X2 Laptop boots fine first time in around 20sec, its using the exact same partitions as my pentium 4  desktop only difference here is my laptop is AMD 64 X2 and 4.0GB Ram

---

### Post by Natovr on 2009-04-28
Yeah, I think I learnt my lesson now, frbe :rolleyes:

---

### Post by hotani on 2009-04-28
I've got freezes on both ATI and NVIDIA systems. On the nvidia machine, the lockups are irrecoverable and require a hard reset. On the ATI box, the lockups last anywhere from a couple of seconds to a few minutes but (so far) the system recovers.

The nvidia system is my work pc, and locks up after a few minutes of use. I originally upgraded from 8.10 to 9.04 using update manager. I then tried a clean install thinking that would alleviate the issue but locked up while setting up the new system just after install.

Now I'm saying "F&^%K it" and clean installing 8.10. There is a [bug open](https://bugs.launchpad.net/ubuntu/+bug/364524) in launchpad, but doesn't look like anything is happening with it. Guess I'll keep checking back.

---

### Post by lucasbmm on 2009-04-30
> **frbe0101 said:**
> Simple lesson, never install the newest version, wait a few months. I learned that the hard way before and I'm sticking with 8.10 until this kind of crap dies down.

It may be true. But then what's the point of releasing a lot of Alpha, Beta, RC1, RC2, editions if the final one isn't ready yet?

That's my point. The pressure to release stable editions every six months with a lot of improvements and updates is not the best idea. Since the last LTS edition, Ubuntu isn't so reliable.

I don't know what happened. I'm disappointed. Really.

Lucas

---

### Post by ledzepjes on 2009-05-16
I also have freezing issues. My laptop, gateway m6809 athlon xp-m 3200+ 512mb 80g 5400rpm hdd with ATI 9600 mobility discrete graphics card and broadcom bcm4306 wireless card. I first started using ubuntu 7.04. I now use 9.04, which boots up really fast. But, it freezes after loggin in, and it seems like it only does so after a min or two after loading firefox. I know that I had to do some fernigaling to get my broadcom wireless bcm4306 to work this go around, which required manually installing the broadcom drivers package bcm43xx from synaptic and restarting a couple times. I also have tried but failed at installing video card drivers for my laptop, however it works fine without them, I would just like to install drivers since it is a disrete card, but when trying to use Enyng, it won't recognize the video card. Should the card need drivers? Is this what is causing my freezing issues after loading firefox? Ubuntu 9.04 has been working fine since I installed it, now just today it starts to freeze and only seems to freeze opening firefox. I have installed adobe flash fyi. I also loaded Opera through ubuntu-tweak since it wasn't in synaptic (gripe) but I was able to load the exact set of web pages and the computer stays running with Opera? Is there a problem with firefox? video card drivers needing installed? me? updates? ufo's? the economy? Oh brother.
 
 Edited: ok, i looked into synaptic, and it says "xserver-xorg-video-ati" and "xserver-xorg-video-radeon" are two installed packages for my video card, it looks like 9.04 just installs them by default. That's nice, no messing with fglrx after all, so I don't think it's an ati driver issue then. back to the economy and ufo's as the culprit :-(

---

### Post by ledzepjes on 2009-05-17
I must say, I did have addon's installed for firefox, (mouse gestures, tabs mix plus, fox tab, tab scope, adblock plus, download status bar) and after uninstalling all of these, ubuntu seems to be stable now. No more freezing and having to hard shutdown by pressing power button. Now I must find which one of them was causing this freezing, and why?

---

### Post by ledzepjes on 2009-06-04
I have to also mention, when installing my Ubuntu on my desktop, I did an upgrade which kept the EXT3 file system, but on my laptop that has frozen in the past (after using it a couple minutes) I installed it into EXT4, and sometimes when it freezes, the screen freezes so I can see everything but I cannot move the cursor and the clock stops, but other times it goes to a screen that looks like it has video card driver issues, (which is probably seperate but it looks likely to have both since I'm using the ATI mobility radeon 9600 card in my laptop and the drivers changed in 9.04) so I think I have two seperate issues, one freezes the screen and the other the screen goes to a yellow and green and black vertical lines. My laptop is a emachine m6809. If I could help the community on fixing my drivers issues for this model laptop, I would like to help, I just don't know how.

---

### Post by dolarsrg on 2009-07-15
Any clue about fixing this issue until now? I am using an Ati mobility and gnome freezes some seconds after booting :(

Thanks in advance.

---

### Post by Jshroud18 on 2009-08-15
I am having problem, and by the looks of this thread, I am goin to need backtrack and a different distro.

but i'll keep looking

---

