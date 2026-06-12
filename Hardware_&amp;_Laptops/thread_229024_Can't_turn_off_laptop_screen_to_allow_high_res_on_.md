---
title: "Can't turn off laptop screen to allow high res on external monitor"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by grahams on 2006-08-03
Hi


I have a Compaq n610c which is working great on Ubuntu 6.0.6 with one hitch. At need to use an external LCD monitor at my desk which looks horrible at any resolution except it's native 1600x1200. 

I've entered this resolution into xorg.conf, but X will not exceed the 1450x1050 limits of my laptop's LCD screen, which I don't appear to be able to turn off. From var/log/Xorg.0.log "(WW) RADEON(0): Mode 1600x1200 is out of range."

I can use Fn F4 to turn off the laptop's screen during boot up, but the screen is turned on when xstarts. Any one know how to stop that or how to get fn F4 working so I can change screens without restarting X?

---

### Post by cantormath on 2006-08-03
> **grahams said:**
> Hi


I have a Compaq n610c which is working great on Ubuntu 6.0.6 with one hitch. At need to use an external LCD monitor at my desk which looks horrible at any resolution except it's native 1600x1200. 

I've entered this resolution into xorg.conf, but X will not exceed the 1450x1050 limits of my laptop's LCD screen, which I don't appear to be able to turn off. From var/log/Xorg.0.log "(WW) RADEON(0): Mode 1600x1200 is out of range."

I can use Fn F4 to turn off the laptop's screen during boot up, but the screen is turned on when xstarts. Any one know how to stop that or how to get fn F4 working so I can change screens without restarting X?

What kinda of video card do you have?

---

### Post by beerfan on 2006-08-03
I have the same laptop and the same issue. I'd like to get a projector working but the Fn F4 key does nothing for me.

The video card is a radeon mobility M7.

---

### Post by cantormath on 2006-08-04
k first of all, you both need to realize that this is why ATI is the $h1test company.  They intentionally make it a total Bi@tch to use there hardware with linux.  I have an ATI card and I have been down this path.

I have two thoughts on this.
[first here is my xorg.conf file]("http://cantormath.com/xorg.txt")

1st) the way I have my dual head working is each screen is a separate instance. That mean, I attach a second monitor, via s-video or regular monitor cable, start my computer, login on the LCD(laptop screen) and then both monitors show a different instance of ubuntu. I can scroll the mouse and short cut from one screen to the other, but I cannot drag program windows. I can start a program in either screen from either screen, and the resolution looks great on both screens.

I did this:
open synaptic
search:
radeon
install:
fglrx-control
radeontool
xorg-driver-fglrx
xserver-xorg-driver-ati
aticonfig
atitvout

reboot

run in terminal(you can change this to stretch screen, look at help)
sudo  aticonfig --initial=dual-head --screen-layout=above

shutdown, connect other screen or s-video out....
two terminals views should appear.


Here is something I did before I did the above, but Im not sure if that make the difference. If you have problems with above, you could try this then attempt above.
************************************************** **
HOWTO: TV-out for legacy ATI cards using GATOS
Purpose:

Enable simple TV-out functionality for legacy ATI Radeon cards with Rage Theater 100 (RT 100) or Embedded Rage Theater (ERT).

Scope:

The driver used has successfully enabled TV-out for the following cards (other legacy cards may also work):

* Radeon 7200 / European model
* Radeon 9000 
* Radeon 9100  (MY CARD!)
* Radeon 9200SE
* Radeon 7000
* Radeon QD
* Radeon Mobility M7 (your card)

Means:

We will compile and install a GATOS patched ATI driver for X.org, the X Window System used by Ubuntu.

Prep Work:

First, install some basic compilation tools, as well as various required X libraries.

Code:

sudo apt-get install build-essential sudo apt-get install xserver-xorg-dev sudo apt-get install x11proto-xinerama-dev sudo apt-get install x11proto-xf86misc-dev sudo apt-get install x11proto-gl-dev sudo apt-get install mesa-common-dev

Fetch Driver and Patch:

You may want to create a directory in which to store the temporary files we'll be using.

Code:
mkdir atidrivers cd atidrivers

You can now download driver and the patch.

Code:
wget [http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.5.8.0.tar.bz2](http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.5.8.0.tar.bz2) wget [http://megahurts.dk/rune/stuff/xorg7-6.5.8.0-tv_output.patch.gz](http://megahurts.dk/rune/stuff/xorg7-6.5.8.0-tv_output.patch.gz)


The latest patches can be found here.
[http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html)

Decompress the Driver Source and Apply the Patch:

Code:

tar xjvf xf86-video-ati-6.5.8.0.tar.bz2 gunzip -c xorg7-6.5.8.0-tv_output.patch.gz | patch -p1 -d xf86-video-ati-6.5.8.0



Configure and Compile the Driver:

Code:

cd xf86-video-ati-6.5.8.0 export XORG_PREFIX="/usr" export 

XORGCONFIG="--prefix=$XORGPREFIX --sysconfdir=/etc --localstatedir=/var" 

./configure $XORG_CONFIG --with-xorg-module-dir=/usr/lib/xorg/modules make


Install the new Driver:

Code:

sudo make install

reboot
**************************

2nd)
In response to your resolution comment is you probably need to enter the resolutions for each monitor(device) individually(and different) if you are gonna do it through changing the xorg.conf file.

Here are some howto's on the topic.
[http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+head](http://ubuntuforums.org/showthread.php?t=221174&highlight=dual+head)
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

---

### Post by grahams on 2006-08-04
thanks for the great responce. I'll give it a go early next week (working at home today) and I'll report back.

---

### Post by grahams on 2006-08-09
Good news, bad news. 

I now have both screens working at their best resolution and it looks like a very good solution. However I've hit a bug were my system hangs intermittantly when the firefox browser is refreshing. 

Without running firefox everything seems stable (after 45 mins of testing) with the 2 screens. If restart X with my old xorg.conf (single monitor), everything appears to be fine even with Firefox (need more time to be sure).

I've trying reloading firefox, but still get hangs. My guess is the ATI driver is the cause, but I'm stumped on how to fix it.

---

### Post by grahams on 2006-08-09
I'm also getting system hangs running other apps (vmware server), from the 2nd screen. No hangs when running apps from the main screen. Seems to be the ATI driver.

---

### Post by grahams on 2006-08-15
After updating to the latest graphics driver using ATI's install tool this setup seems to be working fine.

---

### Post by grahams on 2006-08-16
Unfortunately I made my last update too quickly. I'm still getting system hangs with this approach, although it now appears to be less frequent. It however is not something I can live with at work.

---

### Post by pau on 2006-08-17
**[SIZE="5"]THE SOLUTION:[/SIZE]**

I had the same problem, but found the solution...

1- shut down laptop

2- plug in the external screen

3- start laptop

4- DURING BOOT (quickly!) press the combination of keys to switch to the external screen (in my case "fn" + F10)

5- That's it... enjoy

---

### Post by grahams on 2006-08-24
I'm afraid it's not as easy as that, althought that approach worked with Mandrake (my previous distro).

I can hit Fn+F4 to divert the video to the external monitor and the laptop screen does turns off. However the laptop screen is turned on again as soon as X11 starts, even it I close the lid.

---

### Post by grahams on 2006-09-14
DSL also allows you to turn off the laptop screen and keep it off. Anyone know why dapper turns it back on and how I can stop this bahaviour? Thanks.

---

