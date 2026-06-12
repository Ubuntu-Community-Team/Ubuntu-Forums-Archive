---
title: "toshiba compatibility"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by ktanaya on 2006-07-26
im just about to attempt to install dapper drake on my toshiba satellite m50. it was recommended unofficially by toshiba (i sent an email and they said we dont officially support any linux product but the guy said he was running ubuntu, and it worked fine)
i was wondering what to expect in the way of problems. also cant find a live cd download on the site, is it packaged in with the actual install cd??
thanks muchly
KT

---

### Post by ahallubuntu on 2006-07-27
If you got the Desktop CD, then yes, you got the Live CD too.  In Dapper the Desktop CD boots "live" first and you can then install from there if you wish from the same CD.  It's a good way to try out your system first to make sure the hardware will work.

Some people use the Alternate CD to install instead.  I had an issue when I tried installing from the Desktop CD with installing Grub (boot loader) as the almost-last-step.  When I used the Alternate CD to install it worked better.

---

### Post by sm0ke on 2006-07-27
I have a Toshiba Satellite A10 S-177 and everything seems to be running pretty well. I installed Ubuntu about 3 days ago. Though I am having and issue with the touchpad mouse wanting to select random stuff though. Other than that I am quite happy with Ubuntu.

---

### Post by Atomic Dog on 2006-07-27
I have a Toshiba M55-A135 and Ubuntu works fine.  I use it as my primary OS and Win as a secondary through vmware mostly (though I still have XP in a pertition for certain occasions).

Everything seems to work fine.  Wireless works good with most wireless routers except my $10 Airlink Fry's special (works but flakey).  Thankfully my neighbor has a Linksys router :)

Like people said, Boot the live CD, test, and install.  If you want to keep the OS that is on your laptop fire up Hirens boot CD and shrink the ntfs partition to make room for Ubuntu.  Grub will allow you the option to boot either OS.

I am very happy with Ubuntu.  I love to bash my Mac enamoured boss over the head with my free and fully functional OS.... that does about everything his $1800 macbook pro does. ( I'm talking about at work in out IT dept).

---

### Post by uwoluke on 2006-07-27
I have had both 5.1 and 6.06 running on my Toshiba Tecra A6 with no issues.  Got all my hardware right the first time and hasn't give me a problem.

---

### Post by Metacarpal on 2006-07-27
Running on a Tecra 8200, everything autodetected and life was happy.

(Well, the internal wireless didn't autodetect, but that's because it was hardware-dead before I bought it...)

---

### Post by ThrobbingBrain66 on 2006-07-27
I'm running a toshiba 105A-2716 and everything works fine...although I'm having troubles getting the toshiba acpi enabled when I build a custom kernel so my battery only lasts about 1:40

---

### Post by dewbie on 2006-07-28
My Toshiba Satellite P105-S6014 has had quite a few problems these past few days. Sound may never work, I can't seem to get 1440x900 either out of the box, messing with xorg.conf, 915resolution, or anything else. The SD card reader wasn't even detected. 3-D drivers for this chipset are nearly impossible to find... unless I write them myself. Oh yeah, ACPI works though.
Whatever you do, wait a while before you buy one of these notebooks if your looking at one, so that the hardware might possibly be better supported.

---

### Post by dafut on 2006-10-16
> **dewbie said:**
> My Toshiba Satellite P105-S6014 has had quite a few problems these past few days. Sound may never work, I can't seem to get 1440x900 either out of the box, messing with xorg.conf, 915resolution, or anything else. The SD card reader wasn't even detected. 3-D drivers for this chipset are nearly impossible to find... unless I write them myself. Oh yeah, ACPI works though.


I've got a P105-6084.  By turning off acpi, I was able to get sound working.  Hope that helps.

---

### Post by ashleycrue on 2006-10-16
I'm running 6.06 on my A40-151 and everythings runs OK apart from the cd/dvd rewriter but thats due to the laser dying and not software issues which I first thought.

---

### Post by jsgotangco on 2006-10-17
Toshibas are pretty much supported out of the box and the usual issues involved are hibernate/suspend and the wireless drivers, but usually it works

---

### Post by xyz on 2006-10-17
I love that one:
> it was recommended unofficially by toshiba (i sent an email and they said we dont officially support any linux product but the guy said he was running ubuntu, and it worked fine)
Anyways...I have Dapper on a Toshiba Satellite A 40 bought 2 years ago.

I don't use wireless so I can't speak for or against it. See my sig for Suspend/Hibernate...all I can say is that it worked for me.

One last thing: I was not able to install Dapper from any of the available install Cds. Things got all messed up when I upgraded Breezy/Dapper via the net.

But that failure may have been hardware related as my (22-months old) HD passed away around that time. However, I then tried installing from various Dapper Cds; to no avail!

So I picked up my Breezy install CD and updated/upgraded from there. Since it works, I've not tried to install Dapper from its own Cds despite a brand-new HD.

I've had no particular configuration to make in order to get things to work. (fingers crossed!)

Good luck.

---

### Post by abu3abdalla on 2006-10-17
Hallo Everyone I Am Using 6.06 On My Toshiba A110-195 And Almost Nice 
Its Need Some Config. For Dual Core But Now Every Thing Is Gooooooooooooood

Mohammad Nashaat Abuhammad " Abu3abdalla"
Regards:)  ](*,)

---

### Post by Dale61 on 2006-10-18
I went the (6.06) live cd route on my desktop before taking the plunge on my Satellite A30.

Played around with it for a couple of days, and as everything was going well on my desktop (dual boot w/XP), I tried the live cd on my laptop.

It took a couple of attempts to get any sense out of it, but it eventually loaded.  Had sound, had internet access, had pretty much everything, but also still had XP.

Took the plunge on a clean Ubuntu 6.06 install on my laptop (Satellite A30), and this is when all my troubles started.  It actually took the best part of two days to complete the installation, and when it did, I didn't have any sound or internet.

Managed to get sound working, but still no internet connection.  Have asked on several forums here, and the only suggestions I have gotten are to download this or download that.

HELLO, I don't have an internet connection!  All I have been able to determine is that the modem is an AC97 type internal modem.  Have downloaded to my desktop (and copied to CD) the drivers from the Linmodem site, and followed the how-to on how to install, but to no avail.

No internet makes my laptop relatively useless now as I can't re-install Windoze (only have the factory install back-up CD).  I did try and install with my desktop XP disc, but it didn't have the drivers needed for the laptop.  When I did try to use the factory back-up disc, it came up with an error (unable to access disc) and I couldn't even explore the contents of the disc.

I'm now looking at installing a wireless card into the laptop in the hope this will give me internet access, but I won't be holding my breath.

I'm fully expecting to now use my laptop as an (expensive) file storage facility as it's pretty much useless as it is now.

---

### Post by bluetoad on 2006-10-18
Dale61,

You've probably already been through this - any chance of hooking the desktop up to the internet and networking the 2 computers. Or a USB stick?

I googled for the A30 and someone that had one with an AC97 and that led me to this

[http://website.lineone.net/%7Ebryanrpoole/atiixp-modem.html](http://website.lineone.net/%7Ebryanrpoole/atiixp-modem.html). You can check the pci numbers by do an 'lspci -vv'

For network cards and to check the compatibilty see [http://linux-wless.passys.nl/index.php](http://linux-wless.passys.nl/index.php)

Be careful because some manufacturers change chipsets in cards and keep the same model numbers.  In other laptops I've used Netgear WG511T, Netgear WG511U and Netgear WG511 without problems.  I was lucky on the WG511 - there are many versions of that.  The T & U models use the Mad-WIFI driver.

---

### Post by xyz on 2006-10-18
Hi Dale61,
Are you sure you can't?
> as I can't re-install Windoze (only have the factory install back-up CD)

My box also came with XP Home pre-installed. And I got 2 CD's.

The first one's only goal is to format to NTFS...and it gives NO other choice, of course!

Then I'm asked to insert the 2nd CD to proceed with the installation. Obviously, doing it this way erases everything + I'm left with a NTFS HD which I then have to resize and so on.

So I make regular backup-to-restore of both.

---

### Post by Dale61 on 2006-10-18
bluetoad, I went to the how-to your supplied, but I had already tried that the last time I fired up the laptop.  In fact, I even saved it as a OpenOffice document so I could refer to it whenever I decided to try again.

xyz, my mistake, but I actually have three re-install CD's, but as I have Ubuntu as the only OS on the laptop, for some reason it won't recognise the fact I want to reboot off the CD.  Whenever I request it to boot from the CD/DVD drive, it starts up in Ubuntu.

I'm going to attempt to re-load Window$, then if I can get everything back to wher eit was, I'll re-install Ubuntu re: dual boot.

---

### Post by xyz on 2006-10-18
Yeah I forgot I also have a 3rd CD to install drivers and such.

Hey...good luck and let us know how it goes!!

---

### Post by Dale61 on 2006-10-18
Just to update my progress.

Still no go re: laptop modem.

I attempted a Windoze factory re-install without luck (no sound, no modem, no display adapter), so went back to a bog standard, as installed off the LiveCD installation of 6.06.  Just need to spend time getting the sound up and running again, but that's a job for whenever I decide to get around to it.

However, I do have some tar.gz files that I've downloaded and copied to CD that are supposed to make the modem work, but they didn't last time so I honestly can't see them working this time.

Looks like the laptop gets put away and only used as a file storage unit.  Shame really, as it was a good machine.  Now, it's basically junk.

It could be worse!  At least I've still got my internet accessible desktop pc.

---

### Post by windowskilla on 2008-01-30
alright well with 7.10 my video drivers work. more or less. don't get the 1440x900 I was hoping for, but 1280x800 is better than nothing. sound still doesn't work and I can't disable acpi (no option to in the bios)
wireless won't work either. says there aren't any usable interfaces installed.

---

### Post by davis2k on 2008-04-22
> **Metacarpal said:**
> Running on a Tecra 8200, everything autodetected and life was happy.

(Well, the internal wireless didn't autodetect, but that's because it was hardware-dead before I bought it...)


Everything auto-detected for me except the graphics card and the screen resolutions on my Tecra 8200 was wondering if you could PM me your xorg.conf? I can't get anything higher than 800x600 on my Tecra 8200.

---

### Post by petebarchetta on 2008-04-22
what version of ubuntu would be better suited to a tecra 520cdt?
i have version 7, but am experiencing errors when i try to load up the live CD. which version of ubuntu would dapper be? if that has been seen to work on the 8200 machines then there is hope yet

---

### Post by windowskilla on 2008-04-22
Alright here's an update on my progress.

I got 1440x900x32bpp working. Shame that adding another monitor really screwed everything up and now it won't show the 1440x900 anymore and I can't get it back.

Second, Sound is so elusive on this machine Ive given up all hope.
Unless Im using Windoze naturally.

Third, I did get my wireless card working just fine with a few tiny tweaks.

Fourth, 3D games and such did work until I broke X11 when I added that other monitor.

Still no option to turn off ACPI however Im not even sure I wanna give up all my battery/suspend/resume limited compatibility for sound.

---

### Post by windowskilla on 2008-05-07
> **windowskilla said:**
> Alright here's an update on my progress.

I got 1440x900x32bpp working. Shame that adding another monitor really screwed everything up and now it won't show the 1440x900 anymore and I can't get it back.

Second, Sound is so elusive on this machine Ive given up all hope.
Unless Im using Windoze naturally.

Third, I did get my wireless card working just fine with a few tiny tweaks.

Fourth, 3D games and such did work until I broke X11 when I added that other monitor.

Still no option to turn off ACPI however Im not even sure I wanna give up all my battery/suspend/resume limited compatibility for sound.

Edit : Absolutely everything is now working out of the box due to a Hardy dist-upgrade. all except for two things.

1: No support for the fingerprint reader (its all good anyway)

2: Dual monitor support is sketchy at best and at this time doesn't work.

---

### Post by Tecra_8100 on 2008-05-07
Toshiba tecra 8100 running ubuntu 8.04 with a few problems but it runs like ubuntu 5.10.:biggrin:

---

### Post by dimk1 on 2008-05-25
I use a Toshiba Tecra A4 and i have to admit i'm completely frustrated. I installed Gutsy and i got a black screen after rebooting. Obviously it couldn't recognize my Ati graphics card. I entered in recovery mode and graphics were there but no wireless no ethernet! So frustrating...
I installed hardy and recognized my ATI card but still no ethernet no wireless. I tried several things i found in the internet but nothing seems to work. No plug-unplug the ethernet cable and reboot, no switching off the wireless and rebooting, no ipw2200 (error messages all the time).

The most frustrating is that i'm writing from a windows session right now :mad:

---

