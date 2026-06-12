---
title: "Installing Jaunty Ubuntu Netbook Remix lpia(Atom optimized)version on a Toshiba NB100"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by sandman652001 on 2009-04-20
Some time ago  I decided to install the Jaunty beta version of UNR on my Toshiba NB100 whilst the install went fine the first thing I noted was a marked drop in battery performance.
I immediately realized that the performance loss was probably due to the fact that contrary to the previous version that I had installed the Jaunty UNR was not optimized for the Atom processor. 
Wile a 10 15% drop in battery duration would have been acceptable in my case I lost almost an hour!

I waited until the Release candidate but battery performance did not improve so I decided to try the Alternate lpia version that is available at [http://cdimage.ubuntu.com/ports/releases/jaunty/rc/](http://cdimage.ubuntu.com/ports/releases/jaunty/rc/)

Since I ran in to some problems I decided to write this post in order to help others avoid the same pitfalls and maybe give them a couple of tips along the way.

**INSTALLING**

Not having an external CD/DVD drive the first problem that I ran into was creating a USB pen from the ISO that is available for download.

Apparently if you create the pen using Unetbootin or the built in USB drive utility on anything other than Jaunty the drive will not boot and it will just throw an error( a bug?).

So the first thing you will need, if you do not have another system with jaunty already installed, is a standard Jaunty LIVE CD and a PC with a CD drive. On that PC download the alternate lpia CD ISO
Then:
boot of the live CD 

insert the USB pen you are going to use(at least 1Gb)

go to the computer menu and click on the drive where you downloaded the lpia ISO in order to mount it

then go to Administration>USB Startup Disk Creator

choose other from the CD drive/image section browse to the downloaded lpia ISO

make sure it is selected as the source and click on make startup disk

unplug the USB pen and transfer it over to your netbook

start your Toshiba and press F2 to enter the BIOS under boot make sure you USB pen is listed as first

and under advanced make sure your SATA controller mode is set to compatibility (you will need to set it back to AHCI after  installing).

From here on it is a pretty standard install follow the prompts and complete the install.

A thing I noted during the install is that the network is not detected simply select do not configure at this time. After the install my network was correctly configured.

**FIXING THE MISSING WIRELESS**

Run  update and install all the available updates
then open synaptic and install 

linux-backports-modules-jaunty

reboot and now  your wireless connection should be working

**ADDING THE UNR INTERFACE**

if you wand the UNR interface

go to preferences > Appearance and >Visual Effects  and set them to none

then open synaptic and install 

ubuntu-netbook-remix

then go to Preferences>Switch Desktop Mode and select Ubuntu Netbook interface and click on apply


**TWEAK FOR BOOTUP SPEED (Optional):**

To decrease boot time, activate concurrency bootup: 

sudo gedit /etc/init.d/rc 

and replace the line: 

CONCURRENCY=none 
with 
CONCURRENCY=shell 

Install preload, it loads in to memory parts of the programs that you use most often[COLOR="Red"](I'm told that people that have less than 1 Gb of ram have problems with this)[/COLOR]

sudo aptitude install preload

no configuration needed

**Maximizing screen real estate in Firefox (Optional):**

To take your screen saving netbook remix to the next level, you can do the following to maximise screen real estate in everyone's most used app - Firefox - 

Install the following addons 
Stop or Reload Button 
Personal Menu 
AutoHideStatusBar ([https://addons.mozilla.org/en-US/firefox/addon/1530](https://addons.mozilla.org/en-US/firefox/addon/1530)) 
Fission it combines address bar and progress bar (Safari style).
Install the following theme - 
Classic Compact 
Configure Personal Menu to include all the standard menus except History and Bookmarks (they get their own buttons) 
Disable the menu toolbar. You can always get it back by pressing Alt 
Use the top-bar icon tabs instead of firefox tabs. (options are in edit > preferences > tabs ) 

**Maximizing screen real estate in Gnome (Optional):**

run gconf-editor

go to desktop>gnome>interface

 set toolbar_icons_size to small-toolbar

and

toolbar_style to icons

close gconf-editor

---

### Post by ekawahyu on 2009-04-22
I cannot see my hardisk. I followed exactly what you wrote there, including changing the AHCI into compatibility. Still, I cannot see my partition. FYI, I am using external DVD instead of USB flash. Is that any different? I don't think so.

---

### Post by sandman652001 on 2009-04-22
To be honest I do not know if it makes a difference, other people have had success with the guide what model NB100 do you have? 
is your hard drive seen if you boot of a standard Ubuntu live distro?

---

### Post by ekawahyu on 2009-04-23
NB100-11R, the one comes with Ubuntu Netbook Remix 8.04.1. Actually, the original UNR boots grub really fast. But after I erased the entire system and recovered it using the given recovery CD, grub waits for 10 seconds before actually load the splash.

My hdd setup is AHCI (by default) and I don't think I changed something else in the BIOS.

FYI, I downloaded Ubuntu Netbook Remix relesase 9.04 and it works like charm :) But still, the grub waits for at least 10 seconds before entering the splash. Did I miss something here?

---

### Post by sandman652001 on 2009-04-24
Just sudo gedit /boot/grub/menu.lst and change the timeout 10 to something more appropriate 5?

---

### Post by ekawahyu on 2009-04-24
Nope, that won't do. I put mine into 3 and it keeps waiting for another 15 seconds to boot. Does this happen to you when you recover your system using the recovery CD? Have you ever done that before?

I tried to install Mac OS X too. Do you think the Mac partition creates problem?

---

### Post by sandman652001 on 2009-04-24
No I have not tried I installed the UNR available from the Ubuntu website since I do not have an external CD drive

---

### Post by Auslegung on 2009-04-28
You said, 

Apparently if you create the pen using Unetbootin or the built in USB drive utility on anything other than Jaunty the drive will not boot and it will just throw an error( a bug?).

So the first thing you will need, if you do not have another system with jaunty already installed, is a standard Jaunty LIVE CD and a PC with a CD drive. On that PC download the alternate lpia CD ISO

This makes it sound like you must be in Jaunty (liveCD or full install) to download Jaunty lpia.  However, your second paragraph there seems to say the first step is to download Jaunty lpia on any computer with any OS.  Which is it?  Oh, and so I don't come off as an ***, thanks for the instructions, they seem great except that one hiccup.

---

### Post by snowpine on 2009-04-28
(edit)
Sorry Auslegung, my bad! :)

---

### Post by Auslegung on 2009-04-28
That's all fine and good, Snow, but we're talking about the lpia alternate .iso, not the UNR .img.

---

### Post by sandman652001 on 2009-04-29
Sorry for may bad explanation, what I did was download the lpia iso on the pc then I booted off the live cd. Some other things have changed since the release of jaunty.
1) the network card is now configured correctly during install
2) the unr interface is missing some applets after install, to correct it I followed the instructions at the bottom of this page [https://wiki.ubuntu.com/UNR#Installation](https://wiki.ubuntu.com/UNR#Installation)

---

### Post by magic_k on 2009-04-29
I installed the lpia release version yesterday. Everything seems to work. The install was a bit complicated as i also had the problem that the disk was not found. Adding "apci=off noapic" to the boot command helped. After the installation finished i changed the bios setting back to ahci and everything works.

btw. in the setup you can select what kind system you want to install and there's an entry called netbook remix.

I didn't see the lpia version anywhere until i found your article. I played a bit with several i386 versions like easy peasy  but the battery perfomance was not satisfying. So thanks.

---

### Post by magic_k on 2009-05-05
I have a bit of a problem with this. There are several processes (e.g. wpa_supplicant writes every few seconds into /var/log/wa_supplicant.log) causing the hdd to wake up which leads to a hard disk almost constantly running and getting hot.

Did anyone investigate into this and has some tips howto optimize hdd sleep an battery usage?

---

### Post by comenzando on 2009-06-04
Hi all
this is my first post, you see. I am a complete newbie...

I have installed lpia version and the nb looks now fantastic. I have dual boot windows xp and ubuntu.

Everything is fine except
- no possible to hibernate or suspend.
- no possible to switch lcd to external monitor

my bios is the last one 1.9 (I updated from windows environment)
I have tried some solution but look no correct for me

Is it working for you?

thanks.

---

### Post by sandman652001 on 2009-06-15
When you installed ubuntu did you create a swap partition?

---

### Post by comenzando on 2009-06-20
> **sandman652001 said:**
> When you installed ubuntu did you create a swap partition?
yes, i did

now, after other format and reinstalling sleep works and hibernate too, but this one takes a long time.

by the moment no solution for external display.

---

### Post by sandman652001 on 2009-06-23
I was reading on another forum and discovered that if you let Ubuntu do the partitioning for you during install, it might create a swap partition that is too small for you to be able to hibernate your computer.
the swap partition has to be at least two times the size of your ram in order for hibernate to work

---

### Post by automatic_jon on 2009-09-15
I've followed the instructions in the first post to the letter but I cannot get anything more than basic functionality from my NB100, no wifi, the battery isn't detected, sound stutters and jumps etc. Has the lpia version changed radically in the last several months to a point where it is no longer compatible with this laptop?

---

### Post by Tuliku on 2009-09-15
First i had a triple boot with Ubuntu, XP, and MacOS.
MacOS was completely not interesting for me, Windows started bugging a lot, so i decided to format the whole disk and do a fresh installation.

For me it worked all perfect without any problem.
Here is what i did yesterday:

**My laptop:**
- Toshiba NB100
- 2 GB Ram
- 320 GB Harddisk
- Intel Atom N270 1.60 GHz

**What i did**
1.
Downloaded the IMG netbook version from ubuntu.com, put it in the thumb drive as described on ubuntu.com.

2.
During installation i chose to create my own partitions (3rd option)
Now it looks like this:
- ext4 - /boot - 1gb
- ext4 - / - 24gb
- swap - 3gb
- ext4 - /home - 271gb
Further i did nothing special during setup.

3.
After installation, everything seems to work, at leats what i tested. Network, WiFi, Webcam, Speakers, Bluetooth

4.
Installed additional packages like Conky, Thunderbird, Audacious, Audacity, Mplayer, Skype, W3codecs, etc, etc

5.
8-) Me is happy linux user 8-)

I did not do anything from this HowTo since i'm happy with the way it is, but i think it is really cool that this howto is made for those who need it. Good work !

---

### Post by zietbukuel on 2009-11-01
My machine is a Toshiba NB100 and I've installed UNR 9.10 but I can't use it! It is REALLY SLOW it takes 20 to 30 sec to do something as simple as moving the mouse cursor, please help!

ps. I was using unr 9.04 with the classic interface because the remix interface was super slow as it is now.

---

### Post by sandman652001 on 2009-11-03
Check your bios version some people have solved  this with an update to bios 2.10

> **zietbukuel said:**
> My machine is a Toshiba NB100 and I've installed UNR 9.10 but I can't use it! It is REALLY SLOW it takes 20 to 30 sec to do something as simple as moving the mouse cursor, please help!

ps. I was using unr 9.04 with the classic interface because the remix interface was super slow as it is now.

---

### Post by project_h20 on 2009-12-08
Did anyone get the zoom and fan control keys working in karmic?

---

