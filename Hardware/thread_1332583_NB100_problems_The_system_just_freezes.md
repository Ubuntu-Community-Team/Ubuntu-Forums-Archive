---
title: "NB100 problems The system just freezes"
date: 2009-11-20
forum: Hardware
---

### Post by hhboyhh on 2009-11-20
I have a serious problem. I bought a Toshiba nb100 which came with windows xp, so i decided to install the latest(in that time) UNR which was 9.04. Everything worked fine with the jaunty edition. But then when I updated to Karmic, the system started to freeze by not apparent reason. First i thought it was because i didnt updated my bios, so i did it and nothing changed. I made a clean install with my bios fully updated and nothing. I updated the OS and the problem was still there. 

The system freezes between 10 or 20 minutes after startup or after a wakeup. The problem didnt happen in UNR 9.04. Its really weird because when i dont do anything, the system doesnt freeze. I think the problem is related to the wireless driver or something like that because almost 90% of the time it happens when i am surfing on internet or trying to connect to a wireless network.

Please I need help :s It have been a month since i could not use  Ubuntu

---

### Post by EyesOnFire on 2009-11-20
I am also having an issue with UNR 9.10 on an IBM T40. Booting into the Live environment freezes immediately and booting into the installed UNR 9.10 freezes immediately (Hung at a partially loaded UNR desktop).

I tried UNR 9.10 on a Dell Latitude E6500 and it just ran so well, I wanted to see if it could breathe new life into an old dog.

---

### Post by AndyTRX on 2009-11-24
I have the same problem with an NB100. I have just install 9.10 UNR and it is slow to boot and very slow to display menu items.
If i mouse over a menu item then the screen takes 2-3 minutes to update. If you mouse over an icon then the screen takes 2-3 minutes to update.
If you happen to accidentally mouse over any of these items then the screen takes 2-3 minutes to update. Very frustrating.
If you move the mouse in an area of the screen without icons or menus then the mouse performs as expected.
I am dual booting with XP.
If I use a Puppy Linux Live CD or a _PCLinuxOS_[]("http://www.pclinuxos.com/") it works without any problems.
If I use a 9.10 UNR or a 9.10 live disc I have the same problem.
Can anyone give any suggestions on how to fix this ?

---

### Post by fethio on 2009-11-24
Same problem here with Toshiba NB100. The system responds very slowly, mouse and graphics related? I can move between windows with the Alt-Tab switch, but not with the mouse, it takes ages (20 secs - 60 secs, sometimes couple minutes of hangs). Again using a terminal for example, there are no problems with performance, however, when I try going back to the application menu, it refuses to do it. 

Alt-tab works if I want to switch back to the terminal, and then everything seems ok, until I want to switch back to the main menu. screen gets distorted, and all kinds of strange graphical behavior.

I think this is an issue related with the graphics or mouse driver for some reason

---

### Post by hhboyhh on 2009-11-26
Do your OS freezes?? Yours at least run :(

By now I am using  9.04, I gave up with 9.10 U.U

But I think the graphic problem is related to UNR launcher, that is why I prefer using the original desktop.
In my case I had some similar problems but with 9.04 and following this instructions I solved my problem.
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8379588](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8379588)

Hope there someone similar for Karmic too.

---

### Post by Chronos6 on 2009-11-28
Hey Guys,

I dont know if i have the same problem, but i have an nb100 with the latest bios and UNR 9.10, and if i boot up, it sometimes freezez, and in rare cases i have control back in a few seconds. I've tried to bind it to something, but its really random. What i had figured out, but still needs testing: if it freezez up, i plug in a pendrive, and i get the control back immediately. I'll try to figure it out, if i have a soulution or any info i'll share it. 

Cheers,
Dave

---

### Post by hhboyhh on 2009-12-01
Really similar problem to mine, although I have not noticed that about the pendrive(I will try it if I can).

---

### Post by nutcola on 2009-12-01
Hi, I also have a similar problem..
Had 9.04 and it worked great.. last night updated to 9.1 and now it is really slow. For me the problem appears to be the graphics... it takes several seconds to refresh the screen and things dont scroll properly, they are very jerky. 

For example, when trying to scroll through the options in 'System' the screen does not scroll smoothly, it will simply jerk up and down over a few seconds. 
When you have a window open and close it, the background should go from faded icons to normal, but instead of 'fading in' they jerk from faded, to half faded, to normal, and it takes around 5 seconds or more.

I have checked in System, appearance, to make sure the visual effects are set to 'none', but they are already off. Possibly a new video driver might help? 

Unfortunately I'm coming to ubuntu from XP and dont really have any idea where to look or how to load new drivers.. When I go to System, Hardware Drivers, it tells me 'no proprietary drivers are installed on this system'..

Hopefully someone can help, otherwise I will have to go back to 9.04, which I'm not sure how to do either - can 9.1 be uninstalled or do I need to wipe the partition and reload 9.04 from a USB stick?

---

### Post by Tuliku on 2009-12-01
I have had no issue's with my 9.10 unr and normal desktop installation.
You might wannna check:
- Start, System, Preferences,Appearance
- Go to "visual effects" and check if there is "none" selected.

Good luck

---

### Post by hhboyhh on 2009-12-01
> **nutcola said:**
> Unfortunately I'm coming to ubuntu from XP and dont really have any idea where to look or how to load new drivers.. When I go to System, Hardware Drivers, it tells me 'no proprietary drivers are installed on this system'..

Hopefully someone can help, otherwise I will have to go back to 9.04, which I'm not sure how to do either - can 9.1 be uninstalled or do I need to wipe the partition and reload 9.04 from a USB stick?

Is normal the message of "no proprietary drivers are installed on this system", because you are using drivers that have been developed by Ubuntu community itself, for example if you use drivers for ATI or NVIDIA, then you will use drivers that are property of ATI or Nvidia.

For restoring your 9.04..... I think that when you boot, you are given the option to chose between which OS to boot, in that menu you can also boot from some restoration points, I think you can try that out.

Good Luck
Cesar

---

### Post by hhboyhh on 2009-12-01
Sorry if there is some mistakes in my descriptions, I am not an Ubuntu expert(indeed I consider myself an Ubuntu newbie), but I hope some expert came to help us.

---

### Post by nutcola on 2009-12-01
> **Tuliku said:**
> I have had no issue's with my 9.10 unr and normal desktop installation.
You might wannna check:
- Start, System, Preferences,Appearance
- Go to "visual effects" and check if there is "none" selected.

Good luck

Hi Tuliku, are you saying you're using a Toshiba NB100 (netbook) and dont have any problem with 9.1? Or a normal desktop PC - this thread is specifically about an issue with the Toshiba NB100.. ;)

Also, as per my previous post, I have checked the visual effects section and it was already set at none..

Thanks for suggestion though, maybe theres something else I can check?

Does anyone know if there are any 3rd party video drivers, not sure if Ubuntu works like that though (ie like windows were you can install different drivers from the vendor or reference drivers from the chipset manufacturer to try to solve issues)?

---

### Post by hhboyhh on 2009-12-02
Until what I know there are not 3rd party drivers for GMA U.U

---

### Post by AndyTRX on 2009-12-03
Hi Everyone

I have fixed my problem

I updated my Bios to Ver 2.10 and all is well.

[http://uk.computers.toshiba-europe.com/innovation/download_bios.jsp?service=UK](http://uk.computers.toshiba-europe.com/innovation/download_bios.jsp?service=UK)


Why didn't I do this first ????????????????????????????????


I used the WIN XP updater and it was very painless. Well done Toshiba

I hope this helps

---

### Post by hhboyhh on 2009-12-03
I had the problem and my bios is updated to 2.10 too.

I assume that you used the winxp updater in windows, not in wine.

Someone knows if there is a way to recover a previous version after an update?

ie. if I update from 9.04 to 9.10, could I return to 9.04?

---

### Post by Gordonbp531 on 2009-12-03
Interestingly my NB 100 came with 8.04UNR LTS and 1 GB RAM.
I upgraded to 2GB RAM and then to 9.04 and finally to 9.10 UNR.

Had no problems at all - all running perfectly OK and smooth and fast...

---

### Post by AndyTRX on 2009-12-03
Yes I used WIN XP not wine.

My aim with this netbook is to use Linux 95% of the time.
Some of my engineering equipment setup SW has to run in WIN XP.

---

### Post by AndyTRX on 2009-12-03
Hello [gendibal]("http://ubuntuforums.org/member.php?u=22727")

Can I ask what 2GB memory you ordered for your NB100. 
I want to upgrade to 2GB but am lazy to look under the bonnet.

Thanks

---

### Post by Chronos6 on 2009-12-05
I've the newest bios, updated from a cd image ([https://bugs.launchpad.net/netbook-remix/+bug/348198](https://bugs.launchpad.net/netbook-remix/+bug/348198)) and having problems still. I'll try to turn off compiz, i dont think it will solve the problem. MAybe i'll revert back to 9.04. Worked great.

Edit: 
If it freezes i get a message in dmesg: 
[ 1327.055220] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.

Maybe its a touchpad issue?
Should we open a TT?

Edit2:
TT opened: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492853](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/492853)

---

### Post by bjh6 on 2009-12-14
I too experience freezes on NB100, running Ubuntu 9.10. They seem to be connected with wireless networking in that plugging in an ethernet cable at least sometimes overrides the freeze. This did not happen in 9.04, nor does it happen in Windows 7 on the same machine. Wireless networkining is also very slow - a maximum of around 300K compared wioth 2MB in Windows 7. I am now running the latest BIOS (2.10). The evidence seems to suggest that the wireless network driver is the source of the problem.
.

---

### Post by nutcola on 2009-12-15
I updated to BIOS 2.1 (was 1.9) and it is now definitely better, but still not smooth (just barely usable now). Also removed the wallpaper, and that made a noticable difference too. I only have the standard 1GB RAM, so perhaps it needs 2GB RAM for the new ubuntu?

Any other owners with 1 or 2GB of RAM - how is ubuntu9.10 for you?

Seems strange if it needs that much, I thought ubuntu was supposed to need lighter resources than windows! ;)

Think I will remove 9.1 and go back to 9.04, dont have time to mess around with it, i just want it to work. I originally installed it to get a fast & simple OS as a possible alternative to XP, but this new version has messed that up for me..
Will let you know how I get on :-)

---

### Post by Tuliku on 2009-12-27
> **nutcola said:**
> Hi Tuliku, are you saying you're using a Toshiba NB100 (netbook) and dont have any problem with 9.1? Or a normal desktop PC - this thread is specifically about an issue with the Toshiba NB100.. ;)
Only running NB100 with first the UNR 9.10 version, but because fo the crappy desktop, i installed the normal desktop version of 9.10.
But with this some drivers are not loaded for example sound etc.

And the funny thing is, till last week, i had no freezing issue's. Now it sometimes does freeze, after 3 or 4 minutes of running normal.

My specs:
- NB100-111
- 2GB ram
- 320 GB toshiba harddisk
So it definitely can not be a hardware issue, since the upgraded ram is a brand name, and the harddisk is also toshiba.

Thinking now of returning to the 9.04 UNR version as indeed there where less issue's then with this 9.10 UNR

---

### Post by sir_firebrand on 2009-12-27
Same here, NB100 1GB ram, bios 2.1 and Ubuntu Netbook Remix. The freezes are random, seems to be relative to the wireless or the touchpad, apparently both are usb devices, so when you plug a pen drive or a usb mouse, the system control come back. My bet is that the ubuntu's usb control system is broken in nb100 netbooks.

Obs: I had some freezing problems in 9.04 too, but they were far more common in 9.10.

---

### Post by Tuliku on 2010-01-05
I installed 9.04, but got several old issue's back which i forgot about.
Did a clean 9.10 unr install, and tweaked it, and now running already for 2 weeks without any issue (no freezing etc).

Click [**here**]("http://ubuntuforums.org/showthread.php?p=8612793#post8612793") if interested in what i've done with my nb100.

---

### Post by Smiff2 on 2010-01-15
not sure this is on topic but i've just had the pleasure of trying every BIOS version on the NB100 running Karmic (actually Mint8).

BIOS v2.10, 2.00, 1.90 all very slow. compiz unuseable, glxgears about 30 fps. i considered disabling compiz but it's a symptom not the cause.

BIOS v1.60, 1.50 system runs well, compiz is smooth, glxgears around 1300fps

so toshiba seem to have broken something horribly for video performance in their bios updates (or maybe Karmic bug i don't know how to track this down). luckily, all old bios versions are available, just take this URL

[http://cdgenp01.csd.toshiba.com/content/support/downloads/ll10v210.exe]("file:///Z:/Temp/BIOS/ar10x160.fd")
and change the last digits e.g
[http://cdgenp01.csd.toshiba.com/content/support/downloads/ll10v160.exe](http://cdgenp01.csd.toshiba.com/content/support/downloads/ll10v160.exe)
is the one i have rolled back to
(there is no 1.70 or 1.80 for some reason. 1.90 is as bad as 2.10.)

many thanks to the people at [https://bugs.launchpad.net/netbook-remix/+bug/348198](https://bugs.launchpad.net/netbook-remix/+bug/348198) for the suggestion to use usb-imagewriter for making the flash disk (keep extracting till you get to the .ima file and rename this .img, for the imagewriter to accept it!). after you've made the boot usb drive, you can just switch the bios file and edit autoexec.bat to quickly flash a different bios. you can flash older over newer bios no problem.

anyone who has this laptop with bios v1.90+ may be wondering why it's running terribly slow? try bios v1.60.

(I was actually messing around trying to fix random "wireless networking is missing on boot" issue, anyone know about that?)

---

### Post by Thameslink on 2010-01-19
Well I did the upgrade to 10.04 alpha 2, just for kicks and the freezing thing seemed to sort itself out. The mic automatically worked again. X is snappy and responsive (but glitchy and has crashed a few times). There are of course other problems that come with it being in alpha, but I'm optimistic that the nb100 will perform well out of the box when they release Lucid.

---

### Post by Bakken on 2010-01-30
The same problem with Toshiba NB100:

Ubuntu 9.10 UNR freezes randomly;
Ubuntu 10.04 alpha-2 freezes randomly;

Finally I had to install 9.04 desktop which works ok so far.

---

### Post by Chronos6 on 2010-02-11
I'll try to downgrade bios and report back. Hopefully that will solve this nightmare. Does anybody has a history or changelog of those bios'es?

---

### Post by ndmp on 2010-02-11
I've been having the same issues with my NB100.

Actually I'm not massively surprised, my experience of 9.10 has not been pleasant (I had it on my acer aspire 5630 and the poor thing was totally unusable due to frequent freeze crashing).

Is it possible to download 9.04 UNR? I've looked for it but I can't work out how to download it from Ubuntu.com, it only seems to let you download 9.10.

---

### Post by Chronos6 on 2010-02-13
I can recommend to put back the bios with version 1.60, it solved my issues. To revert back Ubuntu is not possible afaik.

---

### Post by ndmp on 2010-02-14
Yeah, downgrading isn't possible. I reinstalled 9.04 from usb and that solved my problems.

---

