---
title: "Gutsy Suspend - does it work for anyone?"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by jsully1 on 2007-10-23
Hi all,

I can't get my laptop to suspend - it's a Thinkpad T60 with an ATi Mobility X1300.  The screen shuts off but then the power button just flashes indefinitely.  I've applied various tweaks to /etc/defaults/acpi-support, including whitelisting fglrx, hoping to fix it like it did in Feisty - no luck though.  Anyone have any ideas where to start?

Sully

---

### Post by TabletUbuntu on 2007-10-23
Neither suspend to disk nor to RAM work for me on Toshiba Satellite R25.  Did not work in Feisty either.

---

### Post by Pierre Lourens on 2007-10-23
It works intermittently on my Macbook.  It always goes down rightly, but when I try to return from suspend is when it gets iffy.

---

### Post by chameleonkid on 2007-10-23
Doesn't for me.   Fixes?

---

### Post by oofnik on 2007-10-23
Ughh, I was hoping suspend was going to receive major improvements Gutsy and this thread is not encouraging at all... :mad:
I hope you guys find solutions to your problems, sorry I am of no help!

One idea though, have you tried uswsusp? [This site]("http://luke.no-ip.org/x60tablet/") offers a pretty good explanation of how to install it. I had mixed results in Feisty with this (i.e. broke some things, fixed others). Good luck.

---

### Post by dmz17 on 2007-10-23
Not for me. IBM/Lenovo T61p with NVIDIA.

On OpenSuSE I go 's2ram -f' as root, and it goes to sleep nicely. Don't know what to do on Ubuntu.

This is a real showstopper. I tend to suspend 10-15 times a day, Not being able to costs me 20 minues in boot time, when it should cost me ~45 seconds total.

---

### Post by jsully1 on 2007-10-23
uswsusp gives a strange error message on install about not finding a valid swap space, which is kind of worrying.  It also doesn't have s2ram anymore, it's got one called s2disk, and one called s2both.

---

### Post by ravenon on 2007-10-23
This might all relate to the bug posted at
[https://bugs.launchpad.net/bugs/121653](https://bugs.launchpad.net/bugs/121653)

Seems that the Gutsy kernel now uses SLUB for a scheduler; SLAB was used in the past. Apparently, and at least for ATI cards using fglrx, this exposes a bug in the driver. ATI cards with fglrx tend not to suspend at all, let alone resume. I do not know if this is causing problems more globally.

---

### Post by Canalzo on 2007-10-23
There is a bug with the ATI closed driver (fglrx) and the new kernel memory allocator (SLUB)  that breaks suspend.  

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653")

> uswsusp gives a strange error message on install about not finding a valid swap space, which is kind of worrying. It also doesn't have s2ram anymore, it's got one called s2disk, and one called s2both.

try ```
sudo dpkg-reconfigure uswsusp
```

s2both first writes an image to disk and then suspend to ram so if your laptop runs out of battery you can still resume.

Hope this helps,

C.

---

### Post by jsully1 on 2007-10-23
A dpkg-reconfigure yields the same warning:
```
The swap file or partition that was found in uswsusp's configuration file is not active. In most cases this means userspace software suspend will not work for you and you will need to choose (or let uswsusp choose) another swap space. In some corner cases however, this can be what you want.
Continue without a valid swap space?
```

Here is my uswsusp.conf:
```
#/etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = UUID=818a9249-0e0e-41bf-bfc4-dc6134ecd427
splash = y
compress = y
early writeout = y
image size = 977310023
RSA key file = /etc/uswsusp.key
shutdown method = platform
```

Any ideas?  That's the UUID of my swap partition.

---

### Post by FrancoNero on 2007-10-23
doesn't work on hp compaq nx7400. used to work a little bit somwhere around herd4. hibernate never worked.

time to get the basics right, ubuntu. please? keep it up

---

### Post by #Reistlehr- on 2007-10-23
This has NEVER worked on my hp dv9000z, AMD64 kernel. The one thing that i need to fix in order to get Linux 100% on this laptop.

---

### Post by ColombianGold on 2007-10-23
I have a T60 and CANNOT suspend/hibernate in Gutsy. I have gutsy installed but rolled back kernel so I could suspend. 

I thought this would be fixed too, but ati is crappy in linux. They should just release the drivers to open source, making an announcement doesnt help. Knowing ati the drivers will be ready in 6 months!

---

### Post by cow_racer on 2007-10-23
I have thinkpad t60 with ati x1400.  I can suspend using vesa driver intead of fglrx.  It is nice to have special effects, but if you need to be able to suspend your laptop, you may have to use vesa.

---

### Post by fargle on 2007-10-23
Well, apparently I'll be the only one to say yes so far, sorry all...

My Latitude X1 absolutely LOVES Gutsy!  Finding out that XP was keeping track of every single file I open or close in the registry with no UI to tell it to stop was the final straw, and it's gone.

Anyway, everything worked perfectly out of the box - Bluetooth, graphics, wireless, Ethernet, sound, everything.  I haven't tried suspend-to-disk yet because I'm not terribly interested in that, but suspend-to-ram works great - the only thing I have to do is hit function-uparrow to get the screen back on, and I'm sure there's a workaround for that somewhere.

And believe me, it's hilarious to show Compiz effects including the cube running great on a 1.2 GHz Mobile Pentium M machine with 1.25 GB of RAM.  Take that, Vista losers!

---

### Post by Pierre Lourens on 2007-10-23
Update: I tried to replicate the problem.  The only time I could was when I closed the screen very quickly (I set it to suspend when screen was closed).  Suspend through the Gnome interface works fine, and closing the laptop lid works fine on my Macbook.

---

### Post by pgmer6809 on 2007-10-24
> **jsully1 said:**
> uswsusp gives a strange error message on install about not finding a valid swap space, which is kind of worrying.  It also doesn't have s2ram anymore, it's got one called s2disk, and one called s2both.

Maybe this is because by default Gutsy does not create a swap space big enough for all of ram.
I have a 1GB machine, and Gutsy only created 512MB swap space.

When I try to suspend I get a very quick flash, that I think says something about swap.
I am trying again using Feisty, and a manually allocated swap partition of 2GB.
Will let you know if this works. 
BTW I am on a vanilla desktop at the momment, not a lapttop. Nothing fancy at all about it. Old, std Hardware.
pgmer6809

---

### Post by Chipesh on 2007-10-24
My Acer AMD64*2 with an NVidia card doesn't suspend. Fiesty would sometimes fail.
So it's not just an ATI problem 
Various mods to Xorg and acpi don't work.

Bob

---

### Post by jespdj on 2007-10-24
It works without any problems on my Dell XPS M1330.

---

### Post by Lambert on 2007-10-24
There are problems with the ati driver and suspend. might be with networkmanager also.

I don't use the fglrx driver and got suspend to work after uninstalling networkmanager.

I did many other things prior to uninstalling so to test this I did a clean gutsy install and did nothing but remove nm on a r50p and immedieatly had success with suspend.

---

### Post by Pierre Lourens on 2007-10-24
> **Lambert said:**
> There are problems with the ati driver and suspend. might be with networkmanager also.

I don't use the fglrx driver and got suspend to work after uninstalling networkmanager.

I did many other things prior to uninstalling so to test this I did a clean gutsy install and did nothing but remove nm on a r50p and immedieatly had success with suspend.

On what computer?

---

### Post by srt4play on 2007-10-24
Compaq v6000 with intel graphics - no problems with suspend to RAM.

Toshiba satellite A135-s4666 with intel graphics - no problems with suspend to RAM.

We don't use suspend to disk so that hasn't been tested.  Also we used [these]("http://ppa.launchpad.net/asac/ubuntu/pool/main/n/network-manager/") network-manager packages to fix the problem of network-manager sometimes being unresponsive after resume from suspend. Those packages are referenced in [this]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/153769")    
bug report.

---

### Post by Lambert on 2007-10-24
> **Pierre Lourens said:**
> On what computer?

thinkpad r50p

---

### Post by #Reistlehr- on 2007-10-24
Well i was up till 5 messing around with suspend and i sort of got somewhere. 

What i did:
> 
gksudo gedit /etc/default/acpi-support 

```

MODULES="ndiswrapper"
POST_VIDEO=false
ENABLE_LAPTOP_MODE=true

```


But now when i suspend the screen saver comes on, and the screen is locked.

It's closer sort of. Also, i heard a boot option with nosmp worked on some machines.

---

### Post by #Reistlehr- on 2007-10-24
I THINK I GOT IT!!!!!!!!!!!!

WOOOTTTT

i am using ndiswrapper, so i had to add it to the acpi-support MODULES list. Read my post above

I also had to add nosmp to the boot line. Once i added nosmp, hit suspend. Took a few seconds for it to come back, but it was there!!!

---

### Post by val67 on 2007-10-24
Is it OK to use nosmp even if working with a SMP kernel ??

---

### Post by Faust Arp on 2007-10-24
I have a thinkpad T61.  When I suspend, it goes into sleep, but when I try and reactivate it the screen becomes extremely dark, almost black, and I can't brighten it until my laptop is reset.

---

### Post by #Reistlehr- on 2007-10-24
> **val67 said:**
> Is it OK to use nosmp even if working with a SMP kernel ??

Probably not. lol. But i can say i got it working. I need to see if i can figure another work around for this because of that.

---

### Post by bbqsandwich on 2007-10-24
> **jsully1 said:**
> A dpkg-reconfigure yields the same warning:
```
The swap file or partition that was found in uswsusp's configuration file is not active. In most cases this means userspace software suspend will not work for you and you will need to choose (or let uswsusp choose) another swap space. In some corner cases however, this can be what you want.
Continue without a valid swap space?
```

Here is my uswsusp.conf:
```
#/etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = UUID=818a9249-0e0e-41bf-bfc4-dc6134ecd427
splash = y
compress = y
early writeout = y
image size = 977310023
RSA key file = /etc/uswsusp.key
shutdown method = platform
```

Any ideas?  That's the UUID of my swap partition.

Hi, 

You can fix that by following these instructions:

[http://ubuntuforums.org/showpost.php?p=3573566&postcount=12](http://ubuntuforums.org/showpost.php?p=3573566&postcount=12)

I did that and used uswsusp to fix my hibernate; my suspend still doesn't work though.

---

### Post by Lambert on 2007-10-24
> **#Reistlehr- said:**
> Probably not. lol. But i can say i got it working. I need to see if i can figure another work around for this because of that.

quick suggestion.

Look to see if you have any of these modules loaded.

tifm_sd, tifm_7xx1, and tifm_core

the z series thinkpads use a controller that uses these drivers and there was a known suspend issue in 2.6.22rc with smp and tifm and suspend.

Some more info here
[http://www.thinkwiki.org/wiki/Tifm](http://www.thinkwiki.org/wiki/Tifm)

a search also showed a few other areas where smp and suspend didn't work well together.

---

### Post by #Reistlehr- on 2007-10-24
Noope, none of those are loaded (But i have an HP dv9000z)..

One quick observation. 99% of the people with suspend issues are running the AMD64 kernel.. lol.. 

can everyone who hasn't stated what kernel they are using please post it?

EDIT:

Does anyone know where, other than the sessions window, where i can completeley disable bluetooth? I don't use it, so it's just wasting threads.

---

### Post by blazercist on 2007-10-24
I have this problem with x1600 and 32 bit gutsy so its not just 64 bits... the link to the launchpad bug that was posted earlier in this thread points to SLAB/SLUB  thats the problem, its a kernel issue.

---

### Post by Jukka-Pekka on 2007-10-24
Hp nc8430 with ATI mobility x1600  (1680x1050 display) and ndiswrapper in use for wlan (broadcom 4311 -based)
-> Does not suspend/hibernate. Just a cursor is left blinking on the screen. As the lappy does not suspend/hibernate, it cannot resume either :)

I also tried without the restricted drivers. Did not work.

---

### Post by sneax on 2007-10-24
Suspend/hibernate work great for me. It's a standard centrino laptop, 3 years old, intel integrated graphics 855 (clevo barebone).

Note: since 5.10, ACPI has never worked in Ubuntu, 7.10 is the first version and they did it right coz it seems everything works!

---

### Post by dashnak on 2007-10-24
Not working on an Inspiron 1501

---

### Post by #Reistlehr- on 2007-10-24
Someone wanna check the bugs, and see if it was posted yet?

---

### Post by James Paige on 2007-10-24
DOES NOT WORK Using gusty (from feisty using update-manager)

The computer is a Thinkpad R52
The R52 uses an Intel 915 graphics card, so this is not the oft-mentioned ATI/fglrx problem

Hibernate and Suspend seem to work, but very slowly (about 8 minutes to hibernate)

Resume looks as if it is starting to work, but hangs. Resume from hibernate hangs on the ubuntu slash screen with a thin horizontal white bar obscuring the middle of the screen. Resume from suspend hangs with a frozen mouse cursor on a black screen with some garbage pixels in the bottom 10% of the screen. (both of those graphical glitches were present when resuming in feisty, but there was no hang in feisty)

Feisty was able to hibernate & resume only after I installed a fixed kernel (if I can find the thread on this forum that directed me to the hibernatable feisty kernel, I will edit this post and put the link here)

I tried booting gusty with my old feisty kernel, and hibernate/resume works, but it leaves the wireless networking in a broken state after resume.

***Hibernation is a *really* big deal for me. Fast reliable hibernation is the one and only feature I miss from Windows XP***

[COLOR="Green"]----(Much Later)---

Finally [got hibernate working]("http://ubuntuforums.org/showpost.php?p=3756567&postcount=119"), but only by compiling my own kernel with the tuxonice (suspend2) patches and committing manual hackery on my restricted modules.[/COLOR]

---

### Post by cow_racer on 2007-10-24
You might want to look at this.  

[http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

---

### Post by subvertigo on 2007-10-24
> **cow_racer said:**
> You might want to look at this.  

[http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

I hope that the new ATI proprietary driver recently released yesterday (8.42.3) will resolve the issue. It should be compatible with 2.6.22 kernel (not with .23 yet). I'm waiting fpr the repository availability of that packet.

I think that it a worst idea to downgrade to 2.6.20 kernel on Gutsy... to temporary fix the problem would be better downgrade to Feisty...

---

### Post by NilsE on 2007-10-24
Working fine for me on a Dell Latitude D620 with Gutsy.

---

### Post by ColombianGold on 2007-10-24
Subvertigo...good point...but how do you downgrade too Feisty without installing everything?
Is it possible?

I currently downgrade my kernel to have suspend/hibernate but have thought of reimaging back to feisty...but all that tuning lost, no way too much work!

This is really frustrating, the good thing is that I will never purchase any junk form amd/ati...Its like going back to windoze.

CG

T60/x1300

---

### Post by #Reistlehr- on 2007-10-24
Ya'll need to remmeber that ATI fixes wont fix nVidia suspend problems too. The SLUB/SLAB rproblem was a bug in the fglrx drivers as stated in the bug report, but this is a little more deep.

What i have found:

nosmp in the bootline, seems to enable suspend/hibernate. It only worked about 50% of the time. also, i added ndiswrapper, since its what i use, as a module, in the acpi_support file. It's not 100%. I don't think nosmp is healthy on an smp kernel.

---

### Post by dimeotane on 2007-10-24
Since installing gutsy on my XPS M1210, the machine doesn't respond to wakeup after being put to suspend.  The screen stays dark and it won't wake up, although the power lights come on and hard drive light starts to show activity.

---

### Post by prismatic7 on 2007-10-24
> **dimeotane said:**
> Since installing gutsy on my XPS M1210, the machine doesn't respond to wakeup after being put to suspend.  The screen stays dark and it won't wake up, although the power lights come on and hard drive light starts to show activity.

Similar here, with my m1210 - only the lights stay on during the supposed 'suspend' activity and nothing happens on 'resume'

---

### Post by xi0nic on 2007-10-24
Works OK, had the same problem with Feisty.

Running a Thinkpad R60. Intel Mobile 945GM chipset. Intel PRO/Wireless3945 card.

Suspends fine, but wireless does not work after resume. Have to reboot machine (restarting networking doesn't work -- presuming that it's a driver crash) to get it to come back.

---

### Post by chris_v on 2007-10-24
I'm running the AMD64 version on a Compaq Presario R3000 notebook with nvidia graphics.  The computer will go into suspend, but has a black screen upon resume.  I've tried just about all the fixes I can find on these forums, including using generic drivers, restricted drivers, and those installed by Envy, and nothing seems to work.  I'm new to Ubuntu and love it except for this one little issue which is mildly annoying.  I would appreciate any advice.

---

### Post by djuniah on 2007-10-25
This is a problem related to the ATI drivers and the SLUB.  The bug has been reported for a LONG time now and noone has really had a solid fix for it that does not involve rolling back to an older kernel or back to SLAB.

Also, since noone in this thread has noted it yet, I installed the brand new drivers from ATI that were released the other day (its not an auto update yet, it has to be done manually) and while the performance boost is HUGE, I can confirm that it does NOTHING for the suspend/hibernate issue.

Hopefully we'll see another update soon that addresses this.

---

### Post by charles.figura on 2007-10-25
> **NilsE said:**
> Working fine for me on a Dell Latitude D620 with Gutsy.

NilsE -

Looks like I've got the same machine you have (except for the bluetooth), but my suspend doesn't work AT ALL.  It worked 50% of the time under Feisty, but since I've upgraded to gutsy I think it worked once or twice when the system suspended due to a low battery, but nothing else.  The machine seems to suspend all right, rather, but won't resume - and in a variety of waves.  Sometimes I get the light-flashing kernel panic, other times the display just won't come up (sometimes w/ the backlight on, others not).
And sometimes it will start to wake up then go back to sleep.

Did your suspend work out of the box?  Did you modify anything at all?
Are you using the i810 driver or the intel driver?
Do you have the 1440x900 display?

Thanks for any information you can provide.

---

### Post by ROBarber on 2007-10-25
On Lifebook C series, Fujitsu Siemens with Gutsy OS it seems to work in some way. When it is suspended after I close and open up the display of the laptop, it prompts (on a black screen) me for the root password (or user, I don't know exactly because there are the same) and after I type it for a few seconds (maybe 10) I see the image before the suspend process to occur. After that the system shuts down. When I press the on button the kernel is loaded (with GRUB menu) also with all the application running before the suspend process to take place. anyway, I did this without thinking to much:guitar: :D, so maybe I just did something wrong.

---

### Post by buddhadba on 2007-10-25
No joy on my Inspiron 8500 (nVidia, 1GB RAM, Intel) to either disk or RAM. Goes out okay, but won't come back.

---

### Post by drachenstern on 2007-10-25
> **djuniah said:**
> This is a problem related to the ATI drivers and the SLUB.  The bug has been reported for a LONG time now and noone has really had a solid fix for it that does not involve rolling back to an older kernel or back to SLAB.

Also, since noone in this thread has noted it yet, I installed the brand new drivers from ATI that were released the other day (its not an auto update yet, it has to be done manually) and while the performance boost is HUGE, I can confirm that it does NOTHING for the suspend/hibernate issue.

Hopefully we'll see another update soon that addresses this.

Seconded, and I am in the same boat as you

So now that I've totally de-Ubuntu'ed (hey, palindromic) my configs, I don't expect them to work for future upgrades, so with all of that work, I'm thinking about reformat.  What do you think?  Not worth it or worth it?

---

### Post by James Paige on 2007-10-25
A few people have mentioned hibernate working 50% of the time. I had the same experience when I was using Edgy, and I solved it by increasing the size of my swap partition.

***Gutsy is a sad, sad gibbon without hibernation... do gibbons hibernate in the wild?***

---

### Post by misfitpierce on 2007-10-25
Think its a ATI problem... Friend has 7800GTX in laptop and it works on his.

---

### Post by carac on 2007-10-25
> **fargle said:**
> Well, apparently I'll be the only one to say yes so far, sorry all...

My Latitude X1 absolutely LOVES Gutsy!  Finding out that XP was keeping track of every single file I open or close in the registry with no UI to tell it to stop was the final straw, and it's gone.

Anyway, everything worked perfectly out of the box - Bluetooth, graphics, wireless, Ethernet, sound, everything.  I haven't tried suspend-to-disk yet because I'm not terribly interested in that, but suspend-to-ram works great - the only thing I have to do is hit function-uparrow to get the screen back on, and I'm sure there's a workaround for that somewhere.

And believe me, it's hilarious to show Compiz effects including the cube running great on a 1.2 GHz Mobile Pentium M machine with 1.25 GB of RAM.  Take that, Vista losers!


Also my X300 now works great - only problem seems to be when closing the lid ... no matter what is selected in gnome-power-manger closing the lid when the system is running will hang the system :(    Unusual is that suspending in other ways (FN+Esc, or from applet/menus), closing the lid and then opening it will restore things just fine ...

However please note that bcm43xx (wireless) can create huge problems on suspend/resume (in my case it was also not working, but ndiswrapper works and suspends OK).

---

### Post by amphoterous on 2007-10-26
I have this problem with a Gateway MX 6453 (ATI Xpress 200m series). Mine will go to sleep but is unable to wake up after that.

---

### Post by #Reistlehr- on 2007-10-26
@misfit: It's not an ATI problem. People with nVidia, like myself, also have this problem

---

### Post by kingkookie on 2007-10-26
I'm with you on that.  My laptop is an HP Pavilion ze4547wm.  It's an older laptop, but despite the fact that it's been around for a while, I've never been able to get suspend to correctly wake.  Usually the screen stays blank and there is no sign that the computer is doing anything else.  The pcmcia wireless card doesn't show any activity, the hard disk shows no activity, even the touchpad stays off.  (This laptop model has a light that signify's that the touchpad is enabled.  It can be disable by clicking a button above the touchpad.

Honestly, that doesn't seem to be caused by any graphics card drivers.  Right now, I am running generic VESA drivers, and suspend still doesn't wake.

This problem is not just limited to Ubuntu, but to other distros also.  But, I hope that the issue will be taken care of soon.  I think, however, that the resolution of this problem may be different from computer to computer, as there was no real sleep standard on early systems.  It may be some time before this is completely resolve on all systems.

---

### Post by vaxius on 2007-10-26
I think I saw some in this thread say that using the "nosmp" boot option usually works to correct the problem.  It seems to me then that ATI (and apparently a few people with nVidia) drivers don't like being thrown into a single processing queue being shared by multiple CPUs/cores.  Lacking further knowledge about the inner workings of SLUB, that's as far as my reasoning goes.  Anyone care to run with it?

Also, I'll be watching this post and adding anything relevant in my little article concerning this issue.

[http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

---

### Post by #Reistlehr- on 2007-10-26
Well, it doesnt work on my desktop either, running nVidia video cards (SLI) and the i386 kernel. It would sleep quick, but wouldnt awake. And it will never awake again..... When i was bringing it back from sleep, the PSU took out itself, and the mobo in one shot. Apparently it's been happening with a lot of the PC Power And Cooling 1kw PSU's (Not during suspend, but randomly)

I am going to start looking more into the suspend on my laptop. But, an alternate fix, so far, if you are 100% desperate:

Add nosmp to your bootline

```
gksudo gedit /etc/default/acpi-support
```

make these changes:
```

POST_VIDEO=false
MODULES="ndiswrapper"
MODULES_WHITELIST="ndiswrapper
ENABLE_LAPTOP_MODE=true

```

Replace ndiswrapper with your wireless driver. Ie, bcm43xx or whatever may apply..

---

### Post by marvlush on 2007-10-26
I have a T60 with an ATI X1400 and have the same sleep problem, namely that it seems to get stuck to the point where the moon light is flashing and there is a blinking cursor on the screen, but it never gets past that and is totally unresponsive, requiring power-cycling.

going back to Fiesty's kernel fixed the sleep problem for me, only it broke the all my sound. Anyone know how to fix the sound after going back to the old kernel?

---

### Post by vaxius on 2007-10-26
marvlush:

Try re-installing the older kernel.  If that still doesn't work, you can try building the alsa modules yourself.

First off, get alsa-source and the tools you'll need.
```

$ sudo apt-get install linux-headers-$(uname -r) build-essential gcc-3.4 module-assistant debconf alsa-source

```

Then select the correct driver for you sound card.
```

$ sudo dpkg-reconfigure alsa-source

```

Now install and reboot, and you should be good to go!
```

$ sudo module-assistant auto-install alsa-source
$ sudo shutdown -r now

```

Note: this mini-howto is a slightly edited version of the one over on Ubuntu's community documentation.

[https://help.ubuntu.com/community/HowToConfigureSoundBlasterAudigySEinBreezy](https://help.ubuntu.com/community/HowToConfigureSoundBlasterAudigySEinBreezy)

---

### Post by DyDx on 2007-10-27
Gutsy is running great on my 700m except that I cannot resume from suspend either.  I get the login screen and login and then I am stuck with either a black screen and a cursor or a rainbowed screen with a cursor, but nothing happens.  

A resolution to this would be *great* so I will keep monitoring this thread...

---

### Post by Strelock on 2007-10-28
hp Compaq nw8440 - also got suspend problem after upgrading to Gutsy. 

Haven't tried booting into old kernel, but would try next time I start up the system...

---

### Post by victorgreen on 2007-10-29
I have an X61 Lenovo. Suspend/Hibernate were shot in Fiesty. 

I just did a clean gutsy install and have same problem. Fn f4 is supposed to suspend to ram, and instead it takes about 30 seconds and takes a ton of hdd activity, so I think its trying to hibernate instead [which isnt cool at ALL]. Upon resume... no backlight. 

There are tons of fixes to solve this no backlight, adding acpi_bios=3 to various grub menus. Ive done it all, and still no backlight. I can upon resume hit cntrl alt f1 to get to non graphical terminal logon and from there hit cntrl alt f7 and get to normal locked screen, enter my password and be back on my desktop, but its a pain and it doesnt seem to always work. 

I NEED suspend to work correctly and QUICKLY. People are used to being able to shut their laptops move to another place and open them again all flawlessly. 

I need to be able to do that too... 30 seconds to suspend/hibernate [I cant tell what its trying to do at this point] doesnt cut it.

---

### Post by DyDx on 2007-10-29
If you still can't get this problem figured out try turning off Compiz with the command:
metacity --replace &
and then go into standby and attempt to resume.  If it works, then try to turn Compiz again with:
compiz --replace &

For me, this causes my 700m to freeze in the exact same manner as it does when I go into standby with Compiz on and try to resume.  I can still move the cursor, but all icons are gone or I have a black screen and no keyboard shortcuts work (I cannot stop X or switch virtual terminals).

So it's a problem with Compiz starting again.. for me at least.

---

### Post by mikeize on 2007-10-29
I have this problem on my desktop.  Nice new box, with nice fresh gutsy install.  I have the screensaver kick in after 23 min, and the display to sleep at 44 min, and the computer to sleep after 1 hour of inactivity.  When I wake up in the morning, I can't get the comp to wake up.  ctrl alt bkspace, esc, opening and closing cd drives, mouse clicks...  I end up having to hold the power button, and restart the system.  I'm running compiz, and my specs are below.  I just wanted to add my voice to the chorus.

-mike

---

### Post by vaxius on 2007-10-29
At this moment in time, I believe reverting to the older kernel is the most viable option.  I've been chugging along with 2.6.20, ATI's new driver (8.42), and AIGLX/Compiz for a while now with fully functioning suspend/hibernate.

I really do hope this gets fully figured out.  I'd like to be using the shiny new SLUB in the latest kernel.

[http://blog.vaxius.net/?p=19](http://blog.vaxius.net/?p=19)

---

### Post by Adahn on 2007-10-30
Suspend/hibernate both borked for my AMD64 Gutsy install.

desktop, Biostar Tforce550 mobo, nvidia 7900GS

Suspend puts it almost to sleep (but fans, water pump still active) but I can't wake it....cold reboot only.

Hibernate will save/shut down, but I can't wake it.  On wake, it makes it to Ubuntu splash, and then goes dark.   Cold reboot to get it started again.

---

### Post by skier on 2007-10-30
> **victorgreen said:**
> I have an X61 Lenovo. Suspend/Hibernate were shot in Fiesty. 

I just did a clean gutsy install and have same problem. Fn f4 is supposed to suspend to ram, and instead it takes about 30 seconds and takes a ton of hdd activity, so I think its trying to hibernate instead [which isnt cool at ALL]. Upon resume... no backlight. 

There are tons of fixes to solve this no backlight, adding acpi_bios=3 to various grub menus. Ive done it all, and still no backlight. I can upon resume hit cntrl alt f1 to get to non graphical terminal logon and from there hit cntrl alt f7 and get to normal locked screen, enter my password and be back on my desktop, but its a pain and it doesnt seem to always work. 

I NEED suspend to work correctly and QUICKLY. People are used to being able to shut their laptops move to another place and open them again all flawlessly. 

I need to be able to do that too... 30 seconds to suspend/hibernate [I cant tell what its trying to do at this point] doesnt cut it.

victorgreen, i have the exact same situation with my x61.  i just upgraded from feisty to gutsy.  the backlight worked fine with the workaround you suggested above for feisty but not for gutsy.

anyone????

---

### Post by #Reistlehr- on 2007-10-30
try adding nosmp to the grub line or try the following:

```

gksudo gedit /etc/default/acpi-support

```
Make these changes:
```

SAVE_VBE_STATE=false
POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=false
USE_DPMS=true

```

---

### Post by phelin4 on 2007-10-30
Perhaps this might help someone...

I got suspend to RAM working with following steps:

1. Download latest suspend (0.7 at the moment) from [https://sourceforge.net/project/showfiles.php?group_id=45483](https://sourceforge.net/project/showfiles.php?group_id=45483)
2. Compile it
3. Copy the s2ram to /sbin
4. Modify the /etc/acpi/lid.sh to contain only this:

#!/bin/bash
sudo s2ram -f

5. Use visudo to allow users to call "sudo s2ram" without being asked for password.

After that my Compal HEL80 suspends perfectly to RAM when I close the lid.

For some reason s2ram was replaced in Gutsy with an awfully complicated acpi solution, which at least in my case always resulted in black screen. Acpi is also broken in other ways - I had to modify the  brightness scripts too to get the brightness keys to work. No acpi related modifications were needed in Feisty.

---

### Post by #Reistlehr- on 2007-10-30
Im trying your way now phelin.

Cant compile on x64, even when forcing architecture.

---

### Post by aysiu on 2007-10-30
Works fine for me in Ubuntu 7.04 and Ubuntu 7.10 on my Dell Inspiron 500m. No extra tweaking necessary.

---

### Post by James Paige on 2007-10-30
> **aysiu said:**
> Works fine for me in Ubuntu 7.04 and Ubuntu 7.10 on my Dell Inspiron 500m. No extra tweaking necessary.

What video card, wireless, and other hardware does the Inspirion 500m have? Would you mind posting the output of lspci?

---

### Post by phelin4 on 2007-10-30
> **#Reistlehr- said:**
> Im trying your way now phelin.

Cant compile on x64, even when forcing architecture.

Did you try  "make BACKEND=x86emu"?

---

### Post by sgsax on 2007-10-30
Just wanted to confirm suspend fails for me too.  System spec:
model: Thinkpad T43
kernel: 2.6.22-14-generic
video: ATI Technologies Inc M22 [Mobility Radeon X300]
chipset: Intel 82801 (ICH6 Family)
xorg-driver-fglrx version: 7.1.0-8.37.6+2.6.22.4-14.9

Note suspend was working great for me with Feisty.  All other ACPI functions seem to work fine.  I'll revert to the older kernel until this gets resolved.

---

### Post by touser on 2007-10-30
Broken for me as well.
X61, intel graphics.
2.6.22-14-generic

---

### Post by aysiu on 2007-10-30
> **James Paige said:**
> What video card, wireless, and other hardware does the Inspirion 500m have? Would you mind posting the output of lspci?
Here it is: ```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/
O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor
 to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor
 to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Grap
hics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics De
vice (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) U
SB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) U
SB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) U
SB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Co
ntroller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (re
v 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 0
1)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH
4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Mode
m Controller (rev 01)
01:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Con
troller
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connec
tion (rev 05)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet
 Controller (rev 81)
``` By the way, all the hardware works without tweaking. Sound. Video resolution. Suspend. Screen dimming.

---

### Post by njparton on 2007-10-31
Has anyone tried the following?

[http://www.winterdom.com/weblog/2007/10/23/FixingSleepInUbuntu710.aspx](http://www.winterdom.com/weblog/2007/10/23/FixingSleepInUbuntu710.aspx)

or

[http://koon.fr/wiki/suspend_to_ram_on_the_dell_d820_proprietary_nvidia_drivers_under_ubuntu_gutsy](http://koon.fr/wiki/suspend_to_ram_on_the_dell_d820_proprietary_nvidia_drivers_under_ubuntu_gutsy)

It worked for me in that I can suspend to ram using the button on the gnome taskbar but it won't suspend automatically after 30 mins (as set in power settings).

I also can't wake on lan via magic packet when in S3 suspend although I can after a 'sudo halt'.  This is probably unrelated though?

---

### Post by Strelock on 2007-10-31
Well, reverting to older kernel didn't work for me and turning off compiz didn't help either.

I'l try later on today #Reistlehr setting for acpi-support and if that wouldn't work go for suspend 0.7 as by phelin4.

---

### Post by cow_racer on 2007-10-31
> **phelin4 said:**
> Perhaps this might help someone...

I got suspend to RAM working with following steps:

1. Download latest suspend (0.7 at the moment) from [https://sourceforge.net/project/showfiles.php?group_id=45483](https://sourceforge.net/project/showfiles.php?group_id=45483)
2. Compile it
3. Copy the s2ram to /sbin
4. Modify the /etc/acpi/lid.sh to contain only this:

#!/bin/bash
sudo s2ram -f

5. Use visudo to allow users to call "sudo s2ram" without being asked for password.

After that my Compal HEL80 suspends perfectly to RAM when I close the lid.

For some reason s2ram was replaced in Gutsy with an awfully complicated acpi solution, which at least in my case always resulted in black screen. Acpi is also broken in other ways - I had to modify the  brightness scripts too to get the brightness keys to work. No acpi related modifications were needed in Feisty.


Did you read the README?  You have to install two additional packages to compile it.

---

### Post by cow_racer on 2007-10-31
> **phelin4 said:**
> Perhaps this might help someone...

I got suspend to RAM working with following steps:

1. Download latest suspend (0.7 at the moment) from [https://sourceforge.net/project/showfiles.php?group_id=45483](https://sourceforge.net/project/showfiles.php?group_id=45483)
2. Compile it
3. Copy the s2ram to /sbin
4. Modify the /etc/acpi/lid.sh to contain only this:

#!/bin/bash
sudo s2ram -f

5. Use visudo to allow users to call "sudo s2ram" without being asked for password.

After that my Compal HEL80 suspends perfectly to RAM when I close the lid.

For some reason s2ram was replaced in Gutsy with an awfully complicated acpi solution, which at least in my case always resulted in black screen. Acpi is also broken in other ways - I had to modify the  brightness scripts too to get the brightness keys to work. No acpi related modifications were needed in Feisty.

Didn't work for me. I will just lock up the computer.  I'm sure it probably will work on some computer not using gutsy and flgrx.

---

### Post by #Reistlehr- on 2007-10-31
I got it working perfect without any 3rd party apps. So i'm happy.  Too long enough to find the perfect config

---

### Post by chris_v on 2007-10-31
> **#Reistlehr- said:**
> I got it working perfect without any 3rd party apps. So i'm happy.  Too long enough to find the perfect config

What did you do that ended up working?

---

### Post by Strelock on 2007-10-31
Yeah, I'm curious too :) your solution for tha acpi config file didn't work for me. btw can you post your entire /etc/default/acpi-support?

---

### Post by firecat53 on 2007-10-31
Similar issues as many people:  it will suspend to ram fine, but will never wake up again (lights come back on, but screen never turns on and computer is locked up -- caps lock doesn't turn on or off).

HP dv6000 (6058cl) with nvidia card (using stock nv driver), compiz off, ndiswrapper (same effect with bcm43xx).

Things I have tried --- all unsuccessful in various ways
1. Recompiled stock kernel with suspend2 (tuxonice) patch
2. Recompiled vanilla 2.6.22, 2.6.23, 2.6.21 kernels with (and without) suspend2 patch.
3. Every combination of options in /etc/default/acpi-support
4. Installed hibernate and uswsusp from repositories
5. Compiled and install hibernate .7 from the tuxonice website.
6. Installed Mandriva 2008, Linux Mint (ubuntu based), opensuse 10.3 (2?)

Driving me crazy!!!!

The only thing that worked was installing Sabayon 3.4f. That comes with its own set of issues, and I've been with Ubuntu since 5.04! I guess the other good thing with Sabayon was booting without the 'noapic pci=routeirq' for a change. Wonder what's different and if we could clone their solution for Ubuntu?

Scott

---

### Post by Didjit on 2007-10-31
Try installing the Debian uswsusp package.s2ram -f works for me. [http://packages.debian.org/unstable/admin/uswsusp](http://packages.debian.org/unstable/admin/uswsusp)

 s2ram was removed from the Gutsy version (for some reason). If running s2ram -f works, then look here to force s2ram as your default "suspender" [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

Though recently (last week or so) now my keboard does not wake from suspend, I have to soft press the "sleep/power" button to resume.


HTH

Didjit

---

### Post by strawman on 2007-10-31
in order to get it working on my hp nc8000 i get rid of splash in defoptions line from /boot/grub/menulst.  this is all i do to get resume from suspend-to-ram working and i believe this will work for other laptops also.

a side issue is that i would like to resume without unlocking the screen with my password.  i have marked /etc/default/acpi-support in the appropriate place but it still asks for password to resume.  anybody know how to resolve this?

cheers,
strawman

---

### Post by eewbergeek on 2007-10-31
jsully1,

FYI, same issues, vaio sz430, using nv driver.

---

### Post by netlogic on 2007-11-01
Anybody had success for Toshiba A135-S4656? The suspend worked with Feisty Fawn, but it no longer works with Gutsy. I am thinking about rolling back. Suspend function is really important to me. I tried with both i386 and generic kernel.

---

### Post by firecat53 on 2007-11-01
I tried the debian uswsusp package w/ s2ram -f and I still get the same result.
Also tried the 'nosplash' option when booting and got the same result (with both my generic kernel and a suspend2 enabled kernel).

Thanks for the suggestions. I think something is freezing the computer and preventing the video from restarting. It goes to sleep just fine....never wakes up!!

HP dv6000 (6058cl) with nvidia card (using stock nv driver), compiz off, ndiswrapper (same effect with bcm43xx).

Any other ideas? I don't even know what bug to report!
Thanks, Scott

---

### Post by James Paige on 2007-11-01
[COLOR="Red"]I got suspend *sort of* working on my Thinkpad R52. I edited /etc/default/acpi-support and replaced ACPI_SLEEP_MODE=mem with **ACPI_SLEEP_MODE=standby**

I understand that the power savings with =standby are inferior to the ones I would be getting with =mem, but hey, it is better than nothing.[/COLOR]

EDIT: The above worked for one day, but when i tried it again the next day, I could not get it to work anymore.

No love on hibernate, of course, which is what i really need.

I also notice that the LOCK_SCREEN option in /etc/default/acpi-support seems to be totally ignored. It always locks no matter how I configure it.


[COLOR="Red"]Also, I tried s2disk from uswsusp. It appears to suspend-to-disk correctly, but when I boot, my swap device is corrupted, and unusuable (I have to reformat it with mkswap before I can try again)[/COLOR]

EDIT: Actually, I got hibernate working with s2disk after a few tries. Apparently my **/etc/initramfs-tools/conf.d/resume** Had the wrong uuid in it. I am also using uswsusp 0.7 from Debian unstable rather than 0.6-cvs from gusty, but I don't tknow if that makes a difference or not.

Hibernate/resume is depressingly slow, but at least it works. If anybody has an attack of the curiousneses I will time it precisely.

EDIT: so depressingly slow that it is useless... it seems to get slower each successive time I use it. I clocked it at 13 minutes for a full  hibernate/resume cycle before it stopped working entirely :P

EDIT: later got it working with [tuxonice]("http://www.tuxonice.net/")

---

### Post by Didjit on 2007-11-01
> **James Paige said:**
> 
Hibernate/resume is depressingly slow, but at least it works.

If you want to go to disk (and faster then out of the box hibernate), take a look a suspend2 Tervino has it in his Repo.

Didjit
****

---

### Post by James Paige on 2007-11-01
> **Didjit said:**
> If you want to go to disk (and faster then out of the box hibernate), take a look a suspend2 Tervino has it in his Repo.

Didjit


Hmm... I remember tinkering with suspend2 years ago. It worked well, but I wasn't happy about having to manually rebuild a patched kernel.

Were you referring to [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/) ?

---

### Post by Didjit on 2007-11-01
> **James Paige said:**
> Were you referring to [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/) ?

Yeah, you can follow this post if you are still interested [http://ubuntuforums.org/showthread.php?t=284994&page=33&highlight=suspend2](http://ubuntuforums.org/showthread.php?t=284994&page=33&highlight=suspend2)

Didjit

---

### Post by bluedragon436 on 2007-11-02
The issue I am having is my computer won't susepnd or hibernate when I want it too...and the only way it does is if I let it sit for about 10mins then it goes to sleep and it won't wake back up till I unplug the power and remove the battery....and then have to restart the computer...it is almost more like it locks up then doing anything else...this is rather annoying....  That is the only real complaint I have with Gutsy thus far...

---

### Post by Strelock on 2007-11-02
> **strawman said:**
> in order to get it working on my hp nc8000 i get rid of splash in defoptions line from /boot/grub/menulst.  this is all i do to get resume from suspend-to-ram working and i believe this will work for other laptops also.

a side issue is that i would like to resume without unlocking the screen with my password.  i have marked /etc/default/acpi-support in the appropriate place but it still asks for password to resume.  anybody know how to resolve this?

cheers,
strawman

can you post your acpi-config?

---

### Post by bluedragon436 on 2007-11-02
Yeah this no suspend issue is a pain in the butt...whenever I leave my laptop setting for a long period of time it decides to suspend on its own...and then won't wake back up until I unplug it and pull the battery out and restart it completely...Talk about a pain in the butt....  I Hope either I can figure this out or someone comes up with a fix for it....

---

### Post by strawman on 2007-11-02
here it is for what it's worth but for me getting rid of the 'splash' option in defoptions from /boot/grub/menu.lst is what i believe allows for resume from suspend.

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=platform

# Comment this out to disable screen locking on resume
# LOCK_SCREEN=false

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12

---

### Post by Strelock on 2007-11-03
> **strawman said:**
> 
# Comment this out to disable screen locking on resume
# LOCK_SCREEN=false


I think that default for LOCK_SCREEN is true so since yours is commented out the system asks you for the password each time you restart.

I'll try your config and see if my system can go to standby with it.

---

### Post by Jaxilian on 2007-11-03
Suspend/Hibernate still doesn't work. Is it never gonna be fixed?

---

### Post by chris_v on 2007-11-03
> **strawman said:**
> in order to get it working on my hp nc8000 i get rid of splash in defoptions line from /boot/grub/menulst.  this is all i do to get resume from suspend-to-ram working and i believe this will work for other laptops also.

a side issue is that i would like to resume without unlocking the screen with my password.  i have marked /etc/default/acpi-support in the appropriate place but it still asks for password to resume.  anybody know how to resolve this?

cheers,
strawman

The defoptions line in my menu.lst file is commented out by default it seems.  Would it be possile for you to post your menu.lst file so I can compare it with mine?  Thanks!

---

### Post by sipickles on 2007-11-03
Works on my ASUS A6000 Laptop.... once I'd set it up in power management

---

### Post by #Reistlehr- on 2007-11-03
> **Strelock said:**
> Yeah, I'm curious too :) your solution for tha acpi config file didn't work for me. btw can you post your entire /etc/default/acpi-support?

I reinstalled another clean copy. And somehow, by the powers vested in me, i was touched with a miracle! hehe.

My ACPI file is default now. But, it seems that what works for one person won't work for another person, (duh, lol). This is quite annoying and confussing.

I have two laptops exactly the same, HP Dv9000z CTO's, and one can work perfect without any mods, and the other needs tweaking out the wazu. =/ Such a shame it's so consistently inconsistent.

---

### Post by strawman on 2007-11-03
i've tried it each and every way with the screen_lock line and it asks for password everytime; not a huge deal but would like it to resume without asking to unlock.

try removing the splash from your grub

---

### Post by strawman on 2007-11-03
chris_v,

in your /boot/grub/menu.lst the defoptions line has only one # so this will be passed to the kernel.
mine is 
# defoptions=vga=834
and that is the vga for my screen, yours might be different.  i've taken out the splash option along with quiet.  remember after making changes in grub to do a "sudo update-grub"

---

### Post by chris_v on 2007-11-03
> **strawman said:**
> chris_v,

in your /boot/grub/menu.lst the defoptions line has only one # so this will be passed to the kernel.
mine is 
# defoptions=vga=834
and that is the vga for my screen, yours might be different.  i've taken out the splash option along with quiet.  remember after making changes in grub to do a "sudo update-grub"

Thanks for the info on # vs ##, I'm new to linux and assumed that any # just commented out that line.  In any case, I tried the changes to the menu.lst file and it still does not work.  It's not too big of a deal for me, just a minor annoyance on an otherwise great OS.

---

### Post by strawman on 2007-11-03
sorry to hear it did'nt work.  and yes normally # in a file means that line is not parsed but in that part of /boot/grub/menu.lst it is.

i installed the propietary ati drivers and suspend quit working so i switched back to the radeon driver.

---

### Post by James Paige on 2007-11-05
> **chris_v said:**
> The defoptions line in my menu.lst file is commented out by default it seems.  Would it be possile for you to post your menu.lst file so I can compare it with mine?  Thanks!

That line in /boot/grub/menu.lst is commented out, but it actually gets used by update-grub when it re-builds your menu.lst file after a kernel install or kernel upgrade.

So go ahead an edit the commented-out defoptions line, and then run **sudo update-grub**

---

### Post by dimbulb1024 on 2007-11-05
It sort of works on my Inspiron 6000. On around the 5th or 6th return from suspend my networking goes haywire and I have to reboot.

---

### Post by njparton on 2007-11-05
I've just switched to 32 bit Gutsy and suspend now works for me.

I also increased the size of my swap partition from 2048 to 4096MB - coincidence?

---

### Post by mwacky on 2007-11-06
Doesn't work on HP Pavilion zv6000, ATI Radeon Xpress 200M, Gutsy AMD64.

Tweaked with the /etc/default/acpi-support for hours with no luck.

Work great on Feisty 32 bit, but had to tweak a little for Google Earth to work after suspend,

---

### Post by romeyde on 2007-11-09
This thread has been quiet for a few days.   Just wanted to add my name to the noise.  This is really the only thing that isn't working for me but it's a biggie.   Hate leaving my computer on 24 hrs and it's a pain to have to shut down and restart all the time.

Running a shuttle xps with an AMD 3500 and a agp nvidia card.  Nothing fancy at all.  Suspend/Resume works fine in XP.   In Gutsy it suspends just fine, but then I can't seem to get it to wake back up.   It seems to do something, but I end up having to hit reset to get it back completely.


Tried using the 'nosplash' option on boot, didn't help.   Came back to computer and it was suspended.  Wouldn't wake up.  Hit power button and it acted like it was waking up, screen stayed black but there was some activity.  Then a short pause and then the PC shut down completely.   Started it back up, and from power off and now I have all these weird graphic glitches on the screen.   Icons disappear then come back, windows also.   Get what looks like japanese characters in the title bars occasionally.   Just now, this editing window disappeared and I saw the background instead...   This is the 2nd time it's done this and the only fix is to shut down and reboot.

---

### Post by xadder on 2007-11-10
I just got my Thinkpad T43 to suspend with gutsy - by removing the restricted ATI driver using the System/Administration/Restricted..... menu. For everyday work I don't need the ATI driver on my laptop, but it seems a shame to handicap the system in this way. (The driver did help for google-earth and stellarium as far as I could tell).

Anyway, I need suspend more than google-earth, so I'll run driverless until they (ATI?) fix this.

---

### Post by njparton on 2007-11-10
A lot of people seem to be thinking that ATI drivers are the major cause of sleep issues, but in my personal caseI don't have any ATI hardware so I'm thinking there's something fundamentally wrong with Gutsy and sleeping? Especially given the wide range of people experiencing the same problems.

---

### Post by mwacky on 2007-11-10
Is it with Gutsy or is it only AMD64 Gutsy?  I'm considering going back to 32 bit because of suspend issues, same system with Feisty 32bit system suspend worked well..

---

### Post by MarttiTheFinn on 2007-11-10
Same symptoms on my laptop.

After installing 7.10 I had the "usual" wlan and sound and 3d  issues, but those were well explained in the forums and I got them working quite painlessly.

Suspend/Hibernate worked like:
- suspended nicely, but never wakes up, bit of hdd activity, few led flashing..that all..the only way to recover is reboot

Hibernate did not work at all, always returned back right away.

After trying tons of different hints..I tested the uswsups (s2disk). Bingo, hibernate started to work, suspend is still dead.

I agree with those who say that this is a major flaw in gutsy. Suspend/hibernate is a must on a laptop.

---

### Post by Auslegung on 2007-11-11
It's not Gutsy 64 cuz I have 32 and my suspend doesn't work, nor do I have anything AMD

---

### Post by James Paige on 2007-11-12
I noticed that tuxonice (suspend2) has [a version of their kernel patch]("http://www.tuxonice.net/downloads/") intended specifically for Ubuntu Gutsy (thanks Didjit, for pointing me in that direction)

I am building a patched kernel right now, and I'll report how it works for me later...

-----(Later)-----

Okay, with much kernel-compiley and oops-better-do-that-again-with-initrd-support fun, I got a tuxonice (suspend2) gutsy kernel compiled and installed. It hibernates beautifully. Very fast. Even autodetected my swap partition. Restores beautifully. And fast.

[COLOR="Red"]But my wireless is totally broken in this new kernel. I know my wireless card is an Intel IPW2200BG card, and **sudo modprobe -v ipw2200** does nothing at all :([/COLOR]

:(

-----(Even Later)-----

Yay! Got it working. Turns out that my wireless card is one of those that requires "restricted" binary firmware blobs, which my self-compiled kernel was missing. My quick-and-dirty fix was:
```

sudo mkdir /lib/firmware/2.6.22.9-tuxonice-1
sudo cp -pr /lib/firmware/2.6.22-14-generic/* /lib/firmware/2.6.22.9-tuxonice-1/

```
Which copied all the firmware blobs from the stock gutsy kernel to my new self-compiled tuxonice (suspend2) kernel

So now I have fully functioning hibernate and restore, without losing any other functionality (wireless, sound, compiz all continue to work fine across hibernation)

-----(Much Later)---

I discovered recently that my tuxonice hibernation fails to resume if I leave a CD disk inserted in the CD drive when I hibernate. If I take the CD out first, hibernate works fine.

---

### Post by bankrupt on 2007-11-12
Suspend only half "works" for me.  My computer will suspend, but when I try and resume, nothing happens past the fans turning on and the keyboard blinking at me.  This is on a  desktop with an AMD 3200+ processor, an EVGA 7800 GT video card, running the 32 bit version of Gutsy.  

I've tried various things from messing with the acpi settings, removing the nvidia restricted drivers, etc., with no success.   It's quite aggravating as I use suspend quite a lot when Win XP is booted.

---

### Post by romeyde on 2007-11-13
That seems to be the same issue with most in this thread.   Suspends just fine but then won't wake back up or seems to kinda wake back up but screen just stays dark.   I end up having to power off and back on.  Sometimes, when I power back on I get weird graphic glitches in the desktop and end up having to restart again.  I also tried various "fixes" that I've come across via web searches but none seem to make a difference.

Seems to be a pretty common problem and effects a wide variety of hardware.  Hopefully someone figures it out soon and lets us know how they fixed it.  Really do miss suspend.

---

### Post by borobudur on 2007-11-14
Same for me: dark screen after the suspend.
(with Gutsy AMD64 version)

---

### Post by tahitiwibble on 2007-11-14
so Feisty was all around bettter?

---

### Post by KhaaL on 2007-11-14
Suspend and even hibernate never worked on neither my desktop nor my laptop... the former has nvidia and the latter ATI. I really hope to see suspend work someday, It's such a nifty feature that I want to use :(

---

### Post by john_brown_jr on 2007-11-14
In Feisty, suspend to ram did not work on my Hewlett Packard nx7400, but after I recompiled the kernel and applied a couple of patches, it started working all-right. 

In Gutsy, suspend to ram works better (or at least, different), but still is far from perfect. Believe it or not, to wake up from suspend, one needs to constantly hold down a button (for example, left arrow) for some 10 seconds. To shutdown, the button is needed as well. What kind of magic is that? Seems that someone has somehow damaged the kernel by adding a patch incompatible with the laptop.

In my opinion, it would be **very, very, very** important to get suspend working correctly in the next Ubuntu version. The ACPI woes are the only reason why I can't yet recommend Ubuntu to my tech-naive friends. After all, I can't suggest them to recompile kernel just to (damn) suspend the laptop! I'm sure it can be done, but the last time I tried it it worked on my 12th attempt of custom-patched kernel. Each took at least half an hour to compile. Who on the world has that much spare time?

(I now feel better)

---

### Post by kay_rus on 2007-11-14
i tired everything on this forum.
altering acpi-default, compile new kernel with the tuxonice support - nothing helps me with the acer 6292.

default acpi suspend works 50/50
the same with the tuxonice.

laptop suspends fine, but sometimes doesn't wake up:
1) screen is off
2) screen is blank with the freezed mouse

do you have any other suggestions what can help me?

---

### Post by spier on 2007-11-14
This may not be related to the issues in this thread!

I just got the blank screen behaviour after installing hibernate package thru Synaptic. Removing it and reinstalling gnome-power-manager fixed it.
 
I tried hibernate to fix a minor, strange behaviour when resuming from a idle time suspend. Every time, after resuming, my laptop instantly start hibernating. Interesting, alter this last power manager reinstall (I tried it many times before) I got it fixed!

---

### Post by Macchi on 2007-11-14
On my laptop Sony Vaio VGN-B1XP neither suspend nor hibernate worked in Gutsy.
Everythig  worked nicely in Feisty, thus I had to revert to the previous version.

---

### Post by dracker on 2007-11-14
Both worked perfect for me in Gutsy with a Radeon Xpress 1100 but only BEFORE activating the ati restricted controler... I've compiz thought.

---

### Post by kay_rus on 2007-11-15
> **spier said:**
> 
I just got the blank screen behaviour after installing hibernate package thru Synaptic. Removing it and reinstalling gnome-power-manager fixed it.

I didn't install the hibernate package

---

### Post by jimmy the saint on 2007-11-15
Check out my newbie friendly guide to enable suspend.   It works to enable suspend, but hibernate is still not functional.

[http://ubuntuforums.org/showthread.php?t=614106]("http://ubuntuforums.org/showthread.php?t=614106")

---

### Post by jonathanhowell on 2007-11-16
I got hibernate working on my T42 Thinkpad with Gutsy 7.10.

I edited /boot/grub/menu.lst with my swap partition info. I removed quiet & splash as well.

# defoptions=resume=/dev/hda5

Then I installed s2disk as per this article:
[http://ubuntuforums.org/showthread.php?t=471855&highlight=s2disk+feisty]("http://ubuntuforums.org/showthread.php?t=471855&highlight=s2disk+feisty")

I may have disabled Compiz somewhere back there. I'll have to check.

Still testing. 
- Jonathan

---

### Post by kay_rus on 2007-11-16
this solution helped me:
[http://ubuntuforums.org/showpost.php?p=3785681&postcount=20](http://ubuntuforums.org/showpost.php?p=3785681&postcount=20)

---

### Post by chris_v on 2007-11-20
After searching around for a while, I found this site:  [http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/install-gutsy/view](http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/install-gutsy/view)

I made sure that all of the options in my /etc/X11/xorg.conf and /etc/default/acpi-support matched the values shown, and all did already except for the line in xorg.conf:  Option          "NvAGP"                 "1"  This line didn't exist in my file, and after adding it, I could resume from suspend without any issues.  However, I do need to enter my password to unlock the laptop, which is no big deal to me.  I'm just glad that it is finally working.

For reference my laptop is a Compaq R3000Z with AMD Athlon 64 3400+ processor, Nvidia graphics, and running Gutsy 64.  I hope this info helps!

---

### Post by bkhull on 2007-11-25
I discovered I had this problem after an upgrade to Gutsy too.

I looked at /proc/swaps and discovered that my system did not consider itself to have any swap space.  I don't know why, or care to guess, but here are the steps I took that corrected it:

1) In case you are not sure what swap partitions you have, cat /etc/fstab and find the comments above the lines marked as swap:

> 
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# Entry for /dev/sda4 :
UUID=f3b3018c-162d-4fdc-ab47-6138f805d630 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdc1 :
/dev/hdc1 /media/hdc1 ext3 defaults 0 2
# Entry for /dev/sda1 :
UUID=632b72cf-c0c8-4bfc-9652-a2151eed3356 /media/sda1 ext3 defaults 0 2
# Entry for /dev/sda3 :
UUID=bdcbea1a-14ec-459d-a9c1-08a67556d263 /media/sda3 ext3 defaults 0 2
# Entry for /dev/hdc5 :
/dev/hdc5 none swap sw 0 0
# Entry for /dev/sda2 :
UUID=45303ac6-8568-4c95-ab83-82a42ebd1137 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto 0 0

In this case, the comments "Entry for /dev/hdc5 and # Entry for /dev/sda2" are the swap areas.

WARNING: Make absolutely sure you get the names right, because step 2 below destroy all content in those partitions, and if you accidentally name your music collection or your OS install, you will destroy it!!

2) sudo mkswap /dev/hdc5
3) sudo swapon /dev/hdc5
4) repeat as needed for any other swap areas
5) Fix /etc/fstab by removing the UUID= entries on the swap device lines and replace them with
the actual /dev/hdc5 instead.  mkswap actually reports a UUID, but I wasn't able to work with
it successfully.

Then I checked /proc/swaps, and they show, and s2disk works.

Please excuse the overly cookbook style of this answer, but I've read too many answers in the past that assumed I knew stuff like this, and I decided it would help more people if I don't make that assumption.

---

### Post by Auslegung on 2007-12-03
Very thorough response and I need the "cookbook style" as I'm a noob to Ubuntu.  So much so that I did not understand:

 5) Fix /etc/fstab by removing the UUID= entries on the swap device lines and replace them with the actual /dev/hdc5 instead. mkswap actually reports a UUID, but I wasn't able to work with it successfully.

What exactly do I delete and what do I replace it with?

---

### Post by TrinitronX on 2007-12-05
> **#Reistlehr- said:**
> I reinstalled another clean copy. And somehow, by the powers vested in me, i was touched with a miracle! hehe.

My ACPI file is default now. But, it seems that what works for one person won't work for another person, (duh, lol). This is quite annoying and confussing.

I have two laptops exactly the same, HP Dv9000z CTO's, and one can work perfect without any mods, and the other needs tweaking out the wazu. =/ Such a shame it's so consistently inconsistent.

 hmm.... strange.  Maybe this has something to do with a **timing** issue of some sort?

---

### Post by Clag64 on 2007-12-06
> **jimmy the saint said:**
> Check out my newbie friendly guide to enable suspend.   It works to enable suspend, but hibernate is still not functional.

[http://ubuntuforums.org/showthread.php?t=614106]("http://ubuntuforums.org/showthread.php?t=614106")

Hi everyone.  Long-time reader, first-time poster.  Ubuntu is my first experience with linux, but the learning curve was much easier thanks to everyone on this forum.

I'm running Gutsy amd64 on a Dell M1210 and I've now got hibernate working.
I installed uswsusp a while ago.  The man page for s2both says that it should put you into suspend, but it hibernates for me and then resumes fine.
I'm not sure if following jimmy the saint's instructions above made this work.
But if i try to use s2disk, it seems to hibernate fine but then when I power up again it just boots normally instead of resuming from hibernate.  Odd.
I'm happy though, s2both makes it hibernate, and that's the only thing I wanted ubuntu to do that it wasn't.  I don't miss suspend anyway, I never used that in XP anyway.
The resume device in uswsusp.conf is set to my swap partition.  No dramas there.  Haven't tried all this with desktop effects yet.  Also haven't tried it with second monitor plugged in, which i often use.
Has anyone had similar experiences with s2both hibernating instead of suspending?

---

### Post by vanadium on 2007-12-07
Could you post your uswsusp.conf? I was able to use s2disk under Feisty on my Dell Latitude with an ATI Radeon X600, proprietary drivers. It does not work anymore on Edgy. My swap is working and active, though. However, the swap-offset utility reports:

```

 sudo swap-offset /dev/sda5
[sudo] password for ftack:
Swapfile header is not contiguous and cannot be used for suspension.

```

Anyone has an idea how to correct this issue?

---

### Post by JSchoeck on 2007-12-07
> **bkhull said:**
> I discovered I had this problem after an upgrade to Gutsy too.

I looked at /proc/swaps and discovered that my system did not consider itself to have any swap space.  I don't know why, or care to guess, but here are the steps I took that corrected it:
I looked at /proc/swaps and it was empty (but it also wanted to reload in the text editor because it said the file changed on the harddrive every time I opened it, so not sure if it's REALLY empty or just didn't display it).
When I tried your recipe I was told that the swap partition is in use - so do I have one, and does it work? Or how could I check? In my fstab it's listed with the UUID.

I can't suspend/hibernate on my Acer 5020, it doesn't even go into that mode but remains with a blinking cursor forever.

---

### Post by Clag64 on 2007-12-07
> **vanadium said:**
> Could you post your uswsusp.conf? I was able to use s2disk under Feisty on my Dell Latitude with an ATI Radeon X600, proprietary drivers. It does not work anymore on Edgy. My swap is working and active, though. However, the swap-offset utility reports:

```

 sudo swap-offset /dev/sda5
[sudo] password for ftack:
Swapfile header is not contiguous and cannot be used for suspension.

```

Anyone has an idea how to correct this issue?

Sure, here goes.

```

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/sda7
compress = y
early writeout = y
image size = 970039050
RSA key file = /etc/uswsusp.key
shutdown method = platform

```

I also get the "swapfile header is not contiguous" output, yet it hibernates fine with s2both.  Odd.
I've noticed that sometimes when I resume from hibernate i get a blank screen (with a mouse cursor) and need to ctrl-alt-backspace, but it's still quicker than a full reboot.

Nvidia proprietary drivers, btw.

---

### Post by Z_o-s-o on 2007-12-07
No problems with suspend or hibernate here.

HP DV6215, Amd with Nvidia.

---

### Post by vanadium on 2007-12-08
I gave up. I also tried creating an additional swap file for s2disk to use. In all of the cases, starting s2disk shows one message line in text mode. From Feisty, I know I should then see progress messages about the writing of the data. Currently under Gutsy, nothing else happens and I only can power off and reboot the machine. Strange that it worked on Feisty, and not here. My hibernation issues are certainly related to the proprietary ati drivers. With the open source driver, I can hibernate "right out of the box". Inder Feisty, I could hibernate with ATI proprietary ddrivers and s2disk. Currently, nothing works anymore.

---

### Post by merike on 2007-12-08
Works on Thinkpad X60s with Intel's 945GM chipset.

---

### Post by Steenmeijer on 2007-12-08
Works on Acer Aspire 9305ASWLMi with Nvidia chipset&GPU, both suspend and hibernating no problem out of the box.

---

### Post by mahousaru on 2007-12-08
I have suspend working on an EeePC and a FS Amilo Pro 2010.  Both fully encrypted so no access to swap.  Both have 2 GB ram. Since Gutsy my network cards wake up fine from suspend.

 Hibernate doesn't work for obvious reasons.

---

### Post by Clag64 on 2007-12-10
Ok a bit of an update:
  It works.  Sometimes.  Occasionally i'll hibernate and it seems fine, but then it just boots up normally instead of resuming.  Might try increasing the size of the swap and see if that makes a difference.
  I can leave USB things plugged in too, and it resumes fine (which is impressive because XP didn't like it if I hibernated with usb hdd or audio stuff plugged in...mind you XP is not the benchmark for things-working-well, that's what lead me to ubuntu and this forum), but occasionally it won't.  Not sure what the pattern is here..:confused:

---

### Post by l0rd0falchemy on 2008-01-04
On my x61 with Gutsy I was having the black screen on resume problem. The suggested fix of appending "acpi_sleep=s3_bios" to the kernel options caused resume to fail occasionally. Switching out of X and back with CTRL ALT F1 then CTRL ALT F7 turns the backlight back on. To have the computer do this automatically on resume uncomment  DOUBLE_CONSOLE_SWITCH=true in /etc/default/acpi-support .

---

### Post by ooglyboo on 2008-01-04
Hibernate works on my computer but suspend doesn't. I have to power-cycle after using suspend.

---

### Post by sasquatch74 on 2008-01-05
> **l0rd0falchemy said:**
> On my x61 with Gutsy I was having the black screen on resume problem. The suggested fix of appending "acpi_sleep=s3_bios" to the kernel options caused resume to fail occasionally. Switching out of X and back with CTRL ALT F1 then CTRL ALT F7 turns the backlight back on. To have the computer do this automatically on resume uncomment  DOUBLE_CONSOLE_SWITCH=true in /etc/default/acpi-support .

I have a r61 and had tried the first solution as well, with no luck.  Editing the acpi-support file worked for me.  Finally!!!
Thanks a bunch.

---

### Post by HuBaghdadi on 2008-01-06
I have DELL Inspiron 1520 (707), Intel Accelerator X3100
Hibernating isn't working, Suspend does.

---

### Post by James Paige on 2008-01-08
Although I got hibernate to work by compiling my own tuxonice patched kernel, I noticed that resume always freezes if I had a CD in the CD drive when I hibernated. Strange, no?

---

### Post by alladnsane on 2008-01-08
> **James Paige said:**
> [COLOR="Red"]I got suspend *sort of* working on my Thinkpad R52. I edited /etc/default/acpi-support and replaced ACPI_SLEEP_MODE=mem with **ACPI_SLEEP_MODE=standby**

I understand that the power savings with =standby are inferior to the ones I would be getting with =mem, but hey, it is better than nothing.[/COLOR]

EDIT: The above worked for one day, but when i tried it again the next day, I could not get it to work anymore.

No love on hibernate, of course, which is what i really need.

I also notice that the LOCK_SCREEN option in /etc/default/acpi-support seems to be totally ignored. It always locks no matter how I configure it.
]

My PC wouldn't go into suspend at all.  Would start, go black, go directly to unlock and when unlocked a message popped up saying "failed to sleep". I have changed to ACPI_SLEEP_MODE=standby and it seems to work on my ASUSP5GC-MX 1.8g celeron with integrated intel video.  But it still wakes to locked screen no matter what I do.

---

### Post by kamjagin on 2008-01-13
I couldn't bring my laptop from suspend either. My laptop gave me a blackscreen and froze  when resuming from suspend. I spent nearly a full week :) trying to get it to work, trying all the solutions available on different forums.

The thing that finally solved it was changing POST_VIDEO to false in /etc/default/acpi-support AND
doing the same thing in my bios. (Took a couple of days before I by chance noticed that the bios also had a POST VIDEO option and it was set to "linux")

I have the proprietary 169. driver (latest one 09/01) for nvidia. All the other drivers are "straight out of the box" with Gutsy.
System: Santa Rosa platform with iwp4965, 2GHz core2duo, 2Gb RAM and GeForce 8600M GT.

---

### Post by steveneddy on 2008-01-13
I fixed my suspend by installing 32 bit util-linux on my 64 bit gutsy.

This installs the 32 bit hwclock, also.

:popcorn:

---

### Post by peabody on 2008-01-16
The following is the /etc/default/acpi-support that I use for my Compaq Presario C571NR with Gutsy.  Suspend worked, but had lots of intermittent failures.  I have yet to have suspend/resume fail on me with this config.  Suspend fails once in a blue moon but never resume from suspend.  I noticed that when suspend seems to fail that dmesg posts something about a process failing to freeze.  I also noticed that I seem to have a zombie process or two when this happens.  This is with using ndiswrapper for the network card.

File is below.  You may want to take out the samba part if you don't have samba installed.
```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
# use 'mem' for the other mode
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
# Sam: modified to false...testing...
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
#POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="networking samba"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12

```

---

### Post by Porch on 2008-01-16
Suspend to RAM always worked fine on my Macbook Core2D running 64bit Ubuntu 7.10. However, this past week, it stopped working. If I suspend and resume within a few minutes, it's fine. But if I leave it suspended for a few hours, It kernel panics when it wakes up. Or just shows a blank screen after a few seconds. Anyway I can debug this?

---

### Post by OldCodge on 2008-01-26
Hi all,

Dell Inspiron 1300 laptop, Gutsy.

Suspend to RAM works fine, Hibernate fails with a quick error about swap space, but I am not using a swap partition, so that is probably why! :)

Steve.

---

### Post by motin on 2008-01-26
> **James Paige said:**
> I noticed that tuxonice (suspend2) has [a version of their kernel patch]("http://www.tuxonice.net/downloads/") intended specifically for Ubuntu Gutsy (thanks Didjit, for pointing me in that direction)

I am building a patched kernel right now, and I'll report how it works for me later...

-----(Later)-----

Okay, with much kernel-compiley and oops-better-do-that-again-with-initrd-support fun, I got a tuxonice (suspend2) gutsy kernel compiled and installed. It hibernates beautifully. Very fast. Even autodetected my swap partition. Restores beautifully. And fast.

[COLOR="Red"]But my wireless is totally broken in this new kernel. I know my wireless card is an Intel IPW2200BG card, and **sudo modprobe -v ipw2200** does nothing at all :([/COLOR]

:(

-----(Even Later)-----

Yay! Got it working. Turns out that my wireless card is one of those that requires "restricted" binary firmware blobs, which my self-compiled kernel was missing. My quick-and-dirty fix was:
```

sudo mkdir /lib/firmware/2.6.22.9-tuxonice-1
sudo cp -pr /lib/firmware/2.6.22-14-generic/* /lib/firmware/2.6.22.9-tuxonice-1/

```
Which copied all the firmware blobs from the stock gutsy kernel to my new self-compiled tuxonice (suspend2) kernel

So now I have fully functioning hibernate and restore, without losing any other functionality (wireless, sound, compiz all continue to work fine across hibernation)

Yeah The Gutsy TuxOnIce patch worked for me as well! They have a nice toturial for Gutsy: [http://wiki.tuxonice.net/DistroAndHardwareSetup/Ubuntu_Gutsy_Gibbon](http://wiki.tuxonice.net/DistroAndHardwareSetup/Ubuntu_Gutsy_Gibbon)

Don't forget to set the resume=swap:/dev/swappartition in /boot/grub/menu.lst for all kernels, for instance:
```
# defoptions=quiet splash resume=swap:/dev/sda5
```

I still have some issue with the touchpad turning out turned off sometimes after a restore, and I have yet to configure the progress/usplash parts (to get nice looking suspend and resume...), but apart from this it is nice to finally have a working hibernation!

---

### Post by ultimatt on 2008-02-02
I think I have a similar problem, but it's not really a problem with suspend. My problem is this:  When  I leave my laptop idle for a while, I have it set to turn off the screen after 20 minutes.  If I try to come back to the laptop after the screen has gone idle (it is set not to suspend or hibernate ever when it is plugged in), the screen will be corrupt.  It is all black and just shows screen tearing and weird artifacts, no desktop whatsoever.  Some times resetting X with a cntl+alt+backspace will resolve it.  Other times it won't come back and a reboot is in order.  

I have an HP dv9428 laptop.  It's a dual core AMD, and I recently installed gutsy.  Everything was fine, I got wireless working with the ndiswrapper HOW-TO's on this site (thanks for all the help). And the nVidia drivers that came with Ubuntu via the Restricted Drivers Manager worked fine.  No problems with the screen coming back from idle.  However, I thought getting the newest drivers for the video would be best (its a Geforce Go 6150 chipset), so I installed Envy and updated.  That's when this issue reared it's head.  I compared the backup Xorg.conf file with the current one, and even replaced the new and booted with the back up to no avail, only made things worse.  Any ideas would help?  I tried reenabling the Restricted Drivers in Ubuntu but I would get a configuration error when I rebooted and it wouldn't recognize the video chipset, and no settings changes helped.  If there's no way to make it work with the newest drivers via Evny, is there a proper way to reenable the default restricted drivers?

---

### Post by odysseusjak on 2008-02-02
IBM ThinkPad R50 -- Suspend used to work when I closed the lid then it stopped.  I really liked that feature.  I can still get it to suspend when I do it manually and it resumes just fine.  But, as I stated, when I close the lid, nothing happens.

---

### Post by peabody on 2008-02-02
> **odysseusjak said:**
> IBM ThinkPad R50 -- Suspend used to work when I closed the lid then it stopped.  I really liked that feature.  I can still get it to suspend when I do it manually and it resumes just fine.  But, as I stated, when I close the lid, nothing happens.

Might seem obvious, but have you checked the power management control panel to see what it's programmed to do on the lid close.

---

### Post by neurostu on 2008-02-03
I don't know if you are still trying to solve this problem. But I got suspend to ram to work by following this site.  

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#How_to_Suspend_with_nVidia_140m.2F570m]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#How_to_Suspend_with_nVidia_140m.2F570m")

Also for further note I have found the site thinkwiki.org to be very useful for getting Linux working on thinkpads.

---

### Post by darrenrxm on 2008-02-08
On a acer 3680 laptop you can get suspend to work by pressing the power button several times. Do not hold down the power button.

---

### Post by dasunst3r on 2008-02-08
Suspend has a 90% probability of working on my Dell Inspiron E1505 with an nVidia GeForce Go 7300.  I had to install the latest driver using Envy, though.

---

### Post by schierly on 2008-02-08
Can you try the following please!

I have an Acer TM 800 with the ATI XORG driver running, and had a problem with suspend to RAM after updating from feisty to gutsy. It went to suspend to RAM (standby) successfully. Resuming from Standby ended up in a black screen. Which I guess is related to the video card.
So my idea is to change the ACPI values for the video card.

My Kernel is 2.6.22-14
  
Today I found a solution to fix it for me.

1. Edit /etc/default/acpi-support

```
sudo nano /etc/default/acpi-support
```

2. Find the lines and change it to

```
SAVE_VBE_STATE=false

POST_VIDEO=false

```

---

### Post by odysseusjak on 2008-02-13
> **peabody said:**
> Might seem obvious, but have you checked the power management control panel to see what it's programmed to do on the lid close.

Yeah, that was the first thing I check.  I changed the settings and tried it.  Nothing.  I changed them back, still nothing.

---

### Post by justleen on 2008-02-15
Packard Bell Easynote GN45-100 with Intel 915 GPU -- worked out of the box

HP (Compaq) NC8430  with  ATi X1600 Mobility:  Works, but only with VESA, not with the FLGRX drivers..

---

### Post by HDave on 2008-02-22
Dell XPS M1210 Laptop with nVidia Geforce Go 7400 card.

Like many other, I could suspend, but got the dark screen coming out.  I got it working perfectly with one change to my acpi-support file:

```
POST_VIDEO=false
```

That's it.  I've disabled swap and hibernate for security reasons, so I can't comment on those.

I see many folks here trying to get hibernate to work on there laptops, I hope everyone realizes that if   a hibernated laptop is stolen it is a simple matter to crack any/all encyrption, etc. and get access to all the data.

---

### Post by steveneddy on 2008-02-23
Suspend works. And it wakes, too.

---

### Post by kml.krk on 2008-03-02
> **schierly said:**
> Can you try the following please!

I have an Acer TM 800 with the ATI XORG driver running, and had a problem with suspend to RAM after updating from feisty to gutsy. It went to suspend to RAM (standby) successfully. Resuming from Standby ended up in a black screen. Which I guess is related to the video card.
So my idea is to change the ACPI values for the video card.

My Kernel is 2.6.22-14
  
Today I found a solution to fix it for me.

1. Edit /etc/default/acpi-support

```
sudo nano /etc/default/acpi-support
```

2. Find the lines and change it to

```
SAVE_VBE_STATE=false

POST_VIDEO=false

```

this soultion worked for me either. My Computer is  ASUS F3S with Ati Radeon HD 2600
Thanks very much!!!!

---

### Post by danbuter on 2008-03-18
I have an Acer Aspire 3680 with intel 915 graphics. Suspend and hibernate both worked great in Feisty, and are both broken in Gutsy. I switched to OpenSUSE, and everything worked fine. LinuxMint is also broken (but it's based on Gutsy, so no surprise).

---

### Post by danbuter on 2008-03-18
Also, has anyone who has suspend issues in Gutsy tried the Heron alpha to see if that fixes the problem? I will be giving the Beta a whirl once it's released, and am hoping that will solve the problem.

---

### Post by DaV|d on 2008-03-18
I found a good fix for gutsy (only suspend to ram works for now though):

My specs:
GeForce FX5700Le
Asus motherboard - P4S800-MX

installed the drivers with [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

renamed /usr/sbin/vbetool

In /etc/X11/xorg.conf added:
```
Option      "NvAGP"     "1"
```
to the "Device" section

in /etc/modprobe.d/blacklist add all other modules displayed by
```
lsmod | grep agp
```
except for agpgart. 

example: I added 
```
blacklist sis_agp
```
to /etc/modprobe.d/blacklist

don't know what I changed in  /etc/default/acpi-support.. It's attached here if anyone is interested.

Don't remember how many different methods I tried, in order to get my computer to suspend, but all failed (including the one with uswusp)

Anyway, good luck anyone who is still trying to get suspend to work!!

I'll try to get suspend to disk working another time.

---

### Post by danbuter on 2008-03-21
Just a note that Hardy Heron Beta fixes the Suspend black screen on my Acer Aspire 3680 with Intel 915.

---

### Post by oldsmobile_mike on 2008-03-22
+1 to the list of "Doesn't work for me"

Sager 5600P with ATi 7500M.  It goes to sleep okay, but when I try to wake it back up it gives a bunch of crazy messages (sorry I don't recall of the top of my head, but a bunch having to do with  USB, acpi, etc.), and - while it usually eventually wakes back up - it takes so long to wake up, that it would be faster for me to just turn it off and turn it back on again.  :confused:

---

### Post by lunar_shuttle on 2008-03-22
It works on my hp/compaq nc6320 (I've only tried it like 5 times though) - and it never worked in feisty! On the other hand I never did a clean install on my feisty - which I did on my gutsy install. :) On the other hand, it doesn't work on my wife:s newly arrived Zepto 3215W.

---

### Post by kiisu on 2008-03-23
Awwww Crap ... I tried the 'nosmp' on the bootline mentioned earlier in the thread and now my laptop doesn't boot. I see a flash about some errors in the beginning and then the ubuntu splash freezes just a fraction of the way in.
Can someone give me a quick lesson in recovery mode? It takes me to a command prompt and I have no idea where to go from there, still pretty new here ...

---

### Post by DaV|d on 2008-03-23
You don't even have to enter recovery mode to fix the bootline :) 
While in grub, highlight the entry you want to change and press 'e' to see the commands executed by grub for that entry. 
Then press the down arrow until the line beginning "kernel  /vmlinuz...." is highlited and press 'e' again to edit that line. Press 'End' to go to the end of the line. Erase the 'nosmp' option from the line (with backspace), press enter to save the changes and then press 'b' to boot.

Since the editing you did is temporary, when you boot, execute to following to edit the grub menu file **permanently**. [COLOR="Red"]Be careful, incorrectly editing the following file might make your system unbootable again![/COLOR]
That said, execute the following to edit the menu file:
```
gksu gedit /boot/grub/menu.lst
```
and remove the 'nosmp' option from the file. Save and exit.
Note: if you're on KDE, write 'kate' (without quotes) instead of 'gedit'

Hope this helps :)

---

### Post by kiisu on 2008-03-23
Raising a cup of coffee to you this early Sunday morning, I'm back into my system. 
Out of curiosity, after having had this little adventure ... what exactly does 'nosmp' tell it?

---

### Post by DaV|d on 2008-03-23
Glad everythings ok :)

> **kiisu said:**
> Out of curiosity, after having had this little adventure ... what exactly does 'nosmp' tell it?

Don't know about that though, as I never had to use it.

---

### Post by Giacecco on 2008-03-23
Fresh install of 7.10 x86 on HP G6000 laptop, featuring NVidia GeForce 7000M and Ubuntu nvidia-glx-new drivers.

Suspend works out of the box but kills the wifi network connection (MadWifi 0.9.3.3 r2756 + AR5007 patch).

Hibernate worked but resumed to black screen. After installing uswsusp it stopped hibernating at all.

Giacecco

---

### Post by crjackson on 2008-03-25
> **DaV|d said:**
> Glad everythings ok :)



Don't know about that though, as I never had to use it.

No Syemtrical Multi-Processing....

nosmp tells an SMP kernel to act as a UP kernel (UP Uniprocesor or single processor)  When booted to this mode it disables the IO APIC

---

### Post by kiisu on 2008-03-25
Interesting. Didn't seem to give a hand on my system though.
Is there any decent way to go at this problem? Any truth to the idea that Hardy is going to solve it?
It's really the last thing left to do on my laptop, to have Ubuntu doing everything I want it to.

---

### Post by drfranktate on 2008-03-27
I JUST got hibernate to work. I'll try suspend in just a sec, but I wanted to update the thread with my progress.

I'm using Gutsy amd64 on a T61p with the NVidia 570m, and I had to do several things to finally even get hibernate to work.

The short story: the default vesa driver is what I'm using, because it would NOT resume while using the nvidia drivers (version 169.12, from nvidia's site). But somehow, it only uses the vesa driver correctly if I manually run 'startx' (when you get the error about running in low graphics mode, click Continue, then when you see the login screen, click Ctrl-Alt-F1 to get to a command prompt, login and run 'sudo killall gdm' to kill that low-res login, then you can run 'startx'). Now that you're in X, you can run 's2disk' from the command line and it might work - read on if it doesn't.

The longer story: 
After installing uswsusp, and running 'sudo s2disk' I got the error: "suspend: Could not stat the resume device file". I found that I needed to run 'swapon /dev/sda5' (and I have to run this every time after reboot, otherwise the swap device is not active). Once I got that fixed, I found that the nvidia drivers didn't work at all with suspend and resume, sooo:

After installing the nvidia drivers and finding that they didn't work, the uninstall didn't update xorg.conf, so I had to copy xorg.conf.backup to xorg.conf. 

So I'm now gonna try "s2both" and see how that works.

-- Frank

---

### Post by drfranktate on 2008-03-27
Woohooooo! It works! It's not too much faster, but it works.

So it's a bit of a kludge, but I don't care. It's what works, and it works well for me.

The reason it's a kludge is that I *do* have to go through the part in my post above each time I reboot (break into terminal and run 'startx' manually), but that's OK by me, since now I shouldn't have to reboot often at all.

Whew!

-- Frank

---

### Post by soccerdog8 on 2008-04-01
Hey guys. It doesn't work for me either. I've heard the open-source radeonHD driver works, since it goes around using the fglrx driver. Has anyone had any luck with that? I can't figure out how to install it.

---

