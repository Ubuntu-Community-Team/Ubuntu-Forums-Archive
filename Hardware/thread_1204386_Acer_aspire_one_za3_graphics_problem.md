---
title: "Acer aspire one za3 graphics problem"
date: 2009-07-04
forum: Hardware
---

### Post by jherskow on 2009-07-04
hi!

i've been running ubuntu on my old laptop for two months now with few problems, just got a AAO ZA3, 
and i impatiently went right ahead, and replaced windows with ubuntu unr.

this was very stupid of me because now the graphics are unbelievably slow
 (like 15 seconds to scroll the menu)
 and the resolution is unchangeable
 (its at 1047 by 768 instead of 1366 by 768 )

, i don't know of any other problems bcz the machine is now unusable. 
i barely managed to update ubuntu, so it has all the patches and stuff. and restarted and everything (still won't work)

 i have no idea what to do.

i am new to ubuntu, i can follow gui instructions, but i need to be walked (typed) throguh terminal stuff.

can anyone help???

---

### Post by jherskow on 2009-07-04
OK, (5 mins later)
i switched to the classic desktop, and the slowness seems to be gone, although id love to know how to fix it so i can use nbr.

the resolution is still unchangeable though....

---

### Post by jherskow on 2009-07-05
UPDATE:

( i know im technically speaking to no-one, but here goes)

-the graphics are still very choppy (window draging, menus and stuff.). very annoying.
-brightness is completely unchangeable

---

### Post by gnssw on 2009-07-20
There is the only one solution at this time is using the psb xorg driver (xserver-xorg-video-psb) from the ubuntu-mobile repo.

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) intrepid main multiverse universe restricted

---

### Post by jherskow on 2009-07-20
yeah, i did that now. so the resolution works.

video playback and graphics is still extrememly choppy tho8ughh

thanks

---

### Post by p.herewini on 2009-08-17
Hello, I just got an Aspire One ZA3 myself and experienced the same problems. After installing the latest Netbook Remix of Ubuntu everything went unbearably slow. I had to install "normal" Jaunty and had a slight improvement in performance. Although the resolution was still stuck on 1024x768, and couldn't change to 1366x768. Video was also unwatchable.

After following this fix I managed to get 1366x768 resolution working:
Enabling 1366x768 Resolution on AspireOne 751h (11.6")
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Although I still cannot get video working and I'm pretty sure this problem is also effecting other performance such as scrolling etc.

@jherskow have you had any luck with your ZA3? I really don't want to go back to windows on my brand-new netbook!?

---

### Post by p.herewini on 2009-08-18
RESOLVED!

After trying all-sorts of bug-fixes including adding *enable_mtrr_cleanup mtrr_spare_reg_nr=1* to grub I finally stumbled onto this ridiculously simple solution:

1. If you haven't got the native 1366x768 resolution working yet, try this:
> Enabling 1366x768 Resolution on AspireOne 751h (11.6")

With this variant (popular because it's available at Costco), the maximum graphics resolution (1366x768) does not work out of the box. To install an updated graphics driver, add the following line at the end of /etc/apt/sources.list:

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

then run the following commands in the terminal:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C6598A30

sudo apt-get update

sudo apt-get install xserver-xorg-video-psb psb-kernel-source

sudo shutdown -r now

If an update to a later version (such as an upgrade from 2.6.28-11 to 2.6.28-14) breaks the graphics driver on your 751h, continue booting to the desktop (select the Run one time session with low graphics option) then run the following commands in the terminal:

sudo apt-get remove psb-kernel-source

sudo apt-get install psb-kernel-source

sudo shutdown -r now

DO NOT use the --reinstall flag to attempt this fix (it will likely crash your session). Use the remove option first, followed by the install option as shown above. 

2. FIXED FULLSCREEN VIDEO PLAYBACK FOR ME:
Applications > Synaptic > Install the following
psb-kernel-headers
psb-firmware
poulsbo-driver-3d
poulsbo-driver-2d
xpsb-glx
psb-modules

I'm not experienced enough to know exactly what each of these packages do, but after installing these and restarting, fullscreen video FINALLY started working smoothly.

---

### Post by jherskow on 2009-08-20
ill try that as soon as i get home. also the kernel thing, the upgrade to the kernel ut me back at sq.1 so iv'e been booting from the old one ever since.

do you have the exact code for the 2and solution? im a bit of a newbie...

thanks!

---

### Post by jherskow on 2009-08-20
ok, it seems to be working, but everytime i boot up i have to either press space or wait 30s for it to load. 
otherwise, thoguh, everything is greast!!! thanks so much, now i can wait till karmic shows up to fix al the little bugs!!!!

---

### Post by p.herewini on 2009-08-25
> **jherskow said:**
> thanks so much, now i can wait till karmic shows up to fix al the little bugs!!!!

Glad you resolved it, what is karmic? Also I just wanted to check we're on the same machine, Acer Aspire One ZA3 with the 11.6" screen?

---

### Post by jherskow on 2009-08-25
yepp, that's the one.

karmic is the next release of ubuntu (9.10), and one of its main goals is to better support netbooks.

btw, have you had any problems with the microphone on yours? because i can seem to get it to work....

thanks, 

jherskow

---

### Post by p.herewini on 2009-08-25
> **jherskow said:**
> yepp, that's the one.

karmic is the next release of ubuntu (9.10), and one of its main goals is to better support netbooks.

btw, have you had any problems with the microphone on yours? because i can seem to get it to work....

thanks, 

jherskow


Oh woops, didn't know the name of the release. Yeah I figured they would fix most things in a future release. The funny thing is that I installed the netbook remix of ubuntu first, and it was much worse.

I haven't tried the microphone yet, are you referring to the mic next to the webcam or the line-in jack?

---

### Post by jherskow on 2009-08-26
>  The funny thing is that I installed the netbook remix of ubuntu first, and it was much worse.

yeah, me too. but i wonder wether it will work now with the fix u gave me

> I haven't tried the microphone yet, are you referring to the mic next to the webcam or the line-in jack?


the mic next to the webcam, i tried some of the stuff on the help page, but no luck.

---

### Post by jherskow on 2009-08-27
now that the graphics problem s fixed, the unr interface works fine!!!
im gonna use the classic nyway, but i figured id let you know

---

### Post by p.herewini on 2009-09-07
My graphics died again!? I'm guessing it happened after a recent automatic update? Have you experience any problems lately?

Basically I start up and after the ubuntu loading screen I just get a blank screen. I'm getting some error message with explains that "the poulsbo driver requires drm". But it looks like the 2 packages (libdrm, libdrm-poulsbo1) are conflicting.

Maybe I need to start a new thread?

---

### Post by jimathy2 on 2009-10-10
> **p.herewini said:**
> RESOLVED!

After trying all-sorts of bug-fixes including adding *enable_mtrr_cleanup mtrr_spare_reg_nr=1* to grub I finally stumbled onto this ridiculously simple solution:

1. If you haven't got the native 1366x768 resolution working yet, try this:


2. FIXED FULLSCREEN VIDEO PLAYBACK FOR ME:
Applications > Synaptic > Install the following
psb-kernel-headers
psb-firmware
poulsbo-driver-3d
poulsbo-driver-2d
xpsb-glx
psb-modules

I'm not experienced enough to know exactly what each of these packages do, but after installing these and restarting, fullscreen video FINALLY started working smoothly.


and this works for the aao za3? i saw evrywhere else that there wont be an update for the video card in this system.. i have the same problem and now im a little hesitant to mess with the problem cause when i did last time it reverted my system to a permanent dev mode terminal and i couldnt access x at all..

---

### Post by flhtguy on 2009-11-16
[FONT=Arial]I too am using an Acer Aspire One 751H and found the following on another forum. Works like a champ!

sudo apt-get update
sudo apt-get upgrade
[restart]
sudo wget [http://gma500re.altervista.org/scripts/poulsbo_ppa.sh](http://gma500re.altervista.org/scripts/poulsbo_ppa.sh) && sh ./poulsbo_ppa.sh

Cheers
Jim
[/FONT]

---

### Post by macachis on 2009-12-04
> **flhtguy said:**
> [FONT=Arial]I too am using an Acer Aspire One 751H and found the following on another forum. Works like a champ!

sudo apt-get update
sudo apt-get upgrade
[restart]
sudo wget [http://gma500re.altervista.org/scripts/poulsbo_ppa.sh](http://gma500re.altervista.org/scripts/poulsbo_ppa.sh) && sh ./poulsbo_ppa.sh

Cheers
Jim
[/FONT]

¡¡GREAT!!!!!

Now I can see videos at full screen without problems, also in youtube, and I can see pictures in their normal proportions (I won't look like a fatty boy any more  ;) )

Thank you very much, Jim!!!

---

### Post by chrismartin517 on 2010-01-18
> **p.herewini said:**
> RESOLVED!

After trying all-sorts of bug-fixes including adding *enable_mtrr_cleanup mtrr_spare_reg_nr=1* to grub I finally stumbled onto this ridiculously simple solution:

1. If you haven't got the native 1366x768 resolution working yet, try this:


2. FIXED FULLSCREEN VIDEO PLAYBACK FOR ME:
Applications > Synaptic > Install the following
psb-kernel-headers
psb-firmware
poulsbo-driver-3d
poulsbo-driver-2d
xpsb-glx
psb-modules

I'm not experienced enough to know exactly what each of these packages do, but after installing these and restarting, fullscreen video FINALLY started working smoothly.

Hey. I am new to ubuntu and am trying to get the hang of entering all this information. I am extremely familiar with windows but the new platform is a bit confusing for me. I've tried adding to the source.list but all I have is source.list.save which is a read only file. I am running the 9.10 version dual boot with the za3 and am running into the slow menu. any help is greatly appreciated. thanks!

---

### Post by chrismartin517 on 2010-01-18
ok i figured out how to add it all in but when i am in the terminal and i enter sudo apt-get install... it comes up with an error message that says 
"The following packages have unmet dependencies:
   xserver-xorg-video-psb: Depends: libdrm-poulsbol but it is not going to be installed"

What does this mean??
thanks

---

### Post by frankasd on 2010-01-25
> **macachis said:**
> ¡¡GREAT!!!!!

Now I can see videos at full screen without problems, also in youtube, and I can see pictures in their normal proportions (I won't look like a fatty boy any more  ;) )

Thank you very much, Jim!!!


Hello the link is currently down, could someone please please please mirror this?

---

### Post by ssuuddoo on 2012-01-25
I have tried to install the psb kernel module together with the xorg-xserver-video-psb stuff on the ubuntu 11.10 oneiric system, but it crushed.

any news about the acer aspire one za3 with ubuntu 11.10? ...or eventually 12.04? 

thnx

---

### Post by overdrank on 2012-01-25
Back to sleep thread. Thread closed.

---

