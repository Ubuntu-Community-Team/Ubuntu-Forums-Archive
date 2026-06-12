---
title: "dual booting an Compaq Presario CQ60"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by cpoole2005 on 2009-09-01
[COLOR=black][FONT=Verdana]Let me start of with i am new to Linux and know extremely little about it but want to learn[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]First question will a Compaq Presario CQ60 (laptop) even run Ubuntu?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Second how would set it up to dual boot to either windows or Linux preferably with out a timer before the pc boots to the OS at the top of the list?[/FONT][/COLOR]

---

### Post by SoftwareExplorer on 2009-09-01
Well, you can download and burn a ubuntu cd or ask for them to ship you one if you are patient, and then boot into Ubuntu without messing with your hard drive. That way you could see how Ubuntu does on your computer. I have a Compaq Persario F500. Short answer:Yes it will probably run.

As for the second question:It will let you choose which one to boot, but it will also boot a default one after a certian amount of time.

---

### Post by SoftwareExplorer on 2009-09-01
By the way, Welcome to Linux, Ubuntu, and the ubuntu forums :P

---

### Post by cpoole2005 on 2009-09-02
> **SoftwareExplorer said:**
> Well, you can download and burn a ubuntu cd or ask for them to ship you one if you are patient, and then boot into Ubuntu without messing with your hard drive. That way you could see how Ubuntu does on your computer. I have a Compaq Persario F500. Short answer:Yes it will probably run.
 
As for the second question:It will let you choose which one to boot, but it will also boot a default one after a certian amount of time.
 
[COLOR=black][FONT=Verdana]I already have the CD however the pc I do not i have a dell that is dying a slow and painful death when i get my tax return i plan on purchasing a newer laptop and am doing some research right now[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]as far as the pc booting to the default OS. i think i seen something @ CNet or on Techtv (before it became G4) that allowed you to for lack of better words remove and or adjust the timer[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3]     [/SIZE][/FONT]

---

### Post by SoftwareExplorer on 2009-09-03
> **cpoole2005 said:**
> [COLOR=black][FONT=Verdana]I already have the CD however the pc I do not i have a dell that is dying a slow and painful death when i get my tax return i plan on purchasing a newer laptop and am doing some research right now[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]as far as the pc booting to the default OS. i think i seen something @ CNet or on Techtv (before it became G4) that allowed you to for lack of better words remove and or adjust the timer[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3]     [/SIZE][/FONT]

As far as the timer, that's pretty easy to do, once you get ubuntu installed, you can change the timeout to whatever you want. As far as hardware support, let me get this straight: You are saying that you are asking about the compaq because you want to find out how compatible it is before you buy it, right?

---

### Post by mick55 on 2009-09-03
There are over 300 models in the [COLOR=black][FONT=Verdana]Compaq Presario CQ60 series.
my guess is you are refering to the one on sale at Walmart [/FONT][/COLOR][COLOR=black][FONT=Verdana]for $298.00.
That one is the [/FONT][/COLOR]Compaq Presario CQ60-419WM.

If that is the case then, yes it is Ubuntu compatible.
It also works great with Linux Mint and PC-BSD in a 4 way boot
with Vista.(Although PC-BSD insists on using a primary partition,
unlike Linux which will install on Primary or logical)

Ubuntu installs flawlessly, detects all devices including wireless,
and the graphics are perfect after you enable restricted drivers
for the Nvidia video card.

The hardest part of the install will be partitioning the hard drive.
Do not use a third party partitioning tool, use Vista's built in
partition tool.

The Vista loader tends to self destruct any time you change anything
on the hard drive, so expect Vista not to boot after you 
install Ubuntu.

Google for the Vista Recovery Disc.It is a really useful boot CD
to fix the Vista loader.I had to use it each time i changed the
partitions or added an OS.

I hope this helps.Make the Vista restore DVD's just in case.

Cheers 
Mick
[COLOR=black][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by lkraemer on 2009-09-03
I'd suggest you try the LiveCD of the Distro you are wanting to install.
If everything works then here is what I have done before on a couple of
Compaq's.

I booted my CQ50-139NR in Vista and enabled the Wifi.  Then I quit Vista.
I booted the LiveCD, and ran gparted and resized the Windows partition to
60 Gig.  Then I moved the RECOVERY Partition to immediately after the Windows
partition.  Then I created my linux-swap, which was 2 times my RAM.
The remainder was for Ubuntu 8.04.3 LTS.  It worked fine. 
(Max of four Primary Partitions and all were used.)

If your LiveCD doesn't run ok, you can always install from the Alternate
Install LiveCD.  Once it is up and running you can load any drivers you
need.

In fact my CQ50-139NR has PCLinuxOS, sidux, and Ubuntu 8.04.3 LTS as
triple boot.

[http://ubuntuforums.org/showthread.php?t=988691&highlight=CQ50-139NR](http://ubuntuforums.org/showthread.php?t=988691&highlight=CQ50-139NR)

[http://ubuntuforums.org/showthread.php?t=996311&highlight=CQ50-139NR](http://ubuntuforums.org/showthread.php?t=996311&highlight=CQ50-139NR)

[http://ubuntuforums.org/showthread.php?t=1142199&highlight=CQ50-139NR](http://ubuntuforums.org/showthread.php?t=1142199&highlight=CQ50-139NR)

I've also installed PCLinuxOS on a CQ60-210US.  It wouldn't run 8.04.3 or 9.04
because of the Nvidia drivers.  The Alternate Install CD most likely would have
fixed that problem.

lkraemer

---

### Post by cpoole2005 on 2009-09-03
[COLOR=black][FONT=Verdana]To answer SoftwareExplorer yes that is correct i want to make sure what ever system I end up purchasing will run Ubuntu[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]To answer mick55 actually the 206us @ microcenter for $400[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]The basics of how I plan to do this is to create a recovery CD or DVD then us fdisk on a USB flash drive to partition the drive to 50/50 then reinstall vista so it is default then install Ubuntu as the secondary as there are a few programs that only run windows that I&#8217;m not willing to give up [/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

---

### Post by mick55 on 2009-09-03
Hi [cpoole2005]("http://ubuntuforums.org/member.php?u=904573")

There is a quicker way to do what you want.

How to Shrink a Partition in Vista:
1. Press **Win+R** to open the run box
2. Type in **diskmgmt.msc **and click **OK**
3. Press the **Continue** button if you need to grant permission
4. Right-click on the partition you wish to shrink
5. Select [B]Shrink Volume…
[/B]6. Select your settings and click the **Shrink** button

Then boot the Ubuntu CD and select to install in unused space.
After Ubuntu installs you will be able to select Vista or Ubuntu
from the boot menu.

The method you choose of course is entirely up to you, and
good luck either way.

Cheers
Mick

---

