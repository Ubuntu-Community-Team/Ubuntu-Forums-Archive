---
title: "ATI Radeon HD 5770 support by ubuntu 10.04?"
date: 2010-04-27
forum: Hardware
---

### Post by northfly on 2010-04-27
What does that mean ubuntu 10.04 picked catalyst 10.4?
does these support ATI HD 5770? Thanks.

---

### Post by pbacount on 2010-04-29
Wondering as well!

---

### Post by northfly on 2010-04-29
really urgent actually, 

does anybody try out ubuntu 10.04 and catalyst 10.4 and your 5770, how is it going?

I am planning to get one card!!!

---

### Post by cdude42 on 2010-04-30
how about the 5470? does that work in 10.04?

---

### Post by cascade9 on 2010-04-30
All the ATI 5XXX (desktop, the mobile versions are a different kettle of fish) cards should work fine with 10.04

Catalyst 10.4 is the latest release, and if your card is supported (all the newer desktop cards are) there should be no problems.

---

### Post by lurchx on 2010-04-30
I got an ATI 5770 card and it doesn't work at all with 10.04 :confused:

Burned the install image to a dvd and booted, gets a distorted screen for awhile
but then the screen goes blank..

---

### Post by dfreer on 2010-04-30
I tested 10.04 using the AMD64 Desktop Live CD. After installing the ATI drivers using the restricted driver manager and restarting GDM, everything seemed to be working fine. Really sluggish though, but that's probably partly due to using the Live CD.

---

### Post by ttfung on 2010-05-01
I just get my ubuntu upgraded to 10.04 today, after updated to catalyst 10.4 everything seems to be working fine...and the old problem of slow resizing and restoring windows is solved by using the Direct2D option. 

but I notice that the plymouth is er.. not playing too nice with ati's driver. Also, i did discover some screen rendering problems (some black lines)with google chrome, don't know if it is caused by the driver or chrome..

---

### Post by MrStark on 2010-05-01
I have an ati 5750 and after the upgrade i'm having video issues as historically have happened with nearly every ubuntu relases (that's consistency!).
On 9.10 the card was working perfectly.
During the upgrade fglrx was not updated (i had the ati latest installed, guess the upgrade rpocess didn't like it).
Now i'm trying to reinstall fglrx&co but nothing seems to work, conflicts between the 10.04 driver and the ati one, packages are not being removed, when i seem to got it working 2d is slow as hell and compiz don't enable enhanced effects...

Just a brief summary of the issue i'm experiencing:

ATI Drivers: SystemError: installArchives() failed
[http://swiss.ubuntuforums.org/showthread.php?t=1450040](http://swiss.ubuntuforums.org/showthread.php?t=1450040)
10.04 broke my fglrx, how do I fix
[http://ubuntuforums.org/showthread.php?t=1466085](http://ubuntuforums.org/showthread.php?t=1466085)
Video Card upgrade - driver issues
[http://ubuntuforums.org/showthread.php?t=1461976](http://ubuntuforums.org/showthread.php?t=1461976)
etc...
(Sadly some post are related to the RC but i found the same issue with the final i'm using, and i have other issue too that were reported in different situations...)

So, i don't suggest to upgrade to 10.04 with an 5xxx, in the best case you should notice a general slowdown (gnome unusable) of the interface and compiz should stop working.

UPDATE: Ok, i fixed it.
See [http://swiss.ubuntuforums.org/showthread.php?t=1466085&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1466085&page=2)

---

### Post by sinbad#1 on 2010-05-02
I can't even install Ubuntu 10.04, the live cd boots up but once it goes past the purple loading screen the output to my display stops and it turns itself off.

Has installing Ubuntu 9.10 and then doing the upgrade worked for anyone with this card?

CPU: AMD Phenom II X4 955
GPU: Radeon 5770
Motherboard: Asus M4A78T-E
Display: Samsung Sync Master 2494

---

### Post by ezra1964 on 2010-05-02
> **cascade9 said:**
> All the ATI 5XXX (desktop, the mobile versions are a different kettle of fish) cards should work fine with 10.04

Catalyst 10.4 is the latest release, and if your card is supported (all the newer desktop cards are) there should be no problems.

I have one of the newer Radeon 5770 HD, monitors go black partway during boot, going to try single user mode and see if I can get it working from there.

---

### Post by naomarik on 2010-05-03
I'm having the same issue of screen going completely blank when trying to boot live mode or selecting install with a Radeon HD 5770.

---

### Post by ezra1964 on 2010-05-03
> **lurchx said:**
> I got an ATI 5770 card and it doesn't work at all with 10.04 :confused:

Burned the install image to a dvd and booted, gets a distorted screen for awhile
but then the screen goes blank..

I had exact same issue, finally solved it by installing 9.10, and then downloading and installing the very latest ATI driver from the ATI site. The latest came out just a few days ago and has support for X.org 7.5. This seems to be key. From that point I upgraded from the net and then had to re-install that same driver again to get it working correctly, but at least I was not presented with a black screen.

Good luck, spread the word, I really like the upgrade, glad I gave it another go

---

### Post by duckwhistle on 2010-05-04
My Asus 5770 cu core was working fine with 10.04 before the card failed (curently being sent back for replacment under warrenty) but had a big ati logo in bottom right hand cornor of the screeen with the words "unsuported hardware" beneath it!

Can't find a refrence anywere to anyone else having that problem, if anyone has an idea on how to get rid of it I'd love to know.

---

### Post by mitchewr on 2010-05-04
I also have an ati 5750 (less than a year old).  I just tried to upgrade from 9.10 and after the installation I rebooted and the log-in screen was there (I could hear it) but I couldn't see it.  I typed in my password and it logged in, but there was absolutely no image at all, just a black screen.  Anyone else have this problem??

UPDATE:  Ok so I tried unplugging my HDMI monitor (acer 23 inch) and just running with my 19 inch tv/monitor DVI converted to VGA and I finally got the screen to appear.  I logged in and downloaded the proprietary driver for the ati 5750 right off of ubuntu "hardware drivers" and it works perfectly.  Once I installed that, I was able to go into Catalyst and configure my display for 2 monitors and all that jazz.  There is no "screen vibrating" (I used to get that with ubuntu 9.10 and the ati drivers) and all the "effects" work fine.  One problem though, if I set my resolution to 1920X1080 then the screen gets really really small and it leaves about a quarter of an inch of "black" around the edge of the monitor.  So I set my resolution on my HDMI acer monitor to 1680X1050 and it fills out the screen.

I'm glad ATI finally got working drivers for the 5XXX series cards....it was driving me nuts.

---

### Post by davidtuti on 2010-05-05
> **lurchx said:**
> I got an ATI 5770 card and it doesn't work at all with 10.04 :confused:

Burned the install image to a dvd and booted, gets a distorted screen for awhile
but then the screen goes blank..

Hi,

I have the same problem but booting with usb and unetbootin.
Someone could it works with live cd to can install 10.04?
Do you know if there is a but open?

Many thanks and sorry for my english!

---

### Post by xykivo on 2010-05-06
Tested the following so far
ATI 5770
ATI 5570

Ubuntu 10.04 - live CD & USB key

In any combination screen turns black middle of loading.
From sound it seems that the boot process reached the start installation phase, but screen remains black.
(Moving mouse of using keyboard doesn't help)

In a similar system I tested Ubuntu 10.04 liveC CD & USB key work with ATI 3450.
(No problem to test or install).

---

### Post by lokojones on 2010-05-08
I found out what the problem is, and it has to do with what someone posted before: Outputs. On my brothers 5770 (Gigabyte branded), the main output is DVI, so when you have a DVI monitor plugged, it works perfectly. In my Asus branded 5770, the main output seems to be the VGA one, so all I had to do is switch to a VGA monitor for install, and then just install the catalyst drivers.

Default open source drivers should check what output the monitor is attached to, instead of asuming its the primary out... I guess they'll fix it soon.

---

### Post by cosdal on 2010-05-11
i have the same problem with 10.04 when i start with livecd i can see nice a screen "logo" and one is going black "no signal" i have 5770 ati with 9.10 ubuntu working well but if i install the drivers and i restart my pc, it doesn't start.
I wait the new version of ati drivers.

---

### Post by cosdal on 2010-05-11
> **lokojones said:**
> I found out what the problem is, and it has to do with what someone posted before: Outputs. On my brothers 5770 (Gigabyte branded), the main output is DVI, so when you have a DVI monitor plugged, it works perfectly. In my Asus branded 5770, the main output seems to be the VGA one, so all I had to do is switch to a VGA monitor for install, and then just install the catalyst drivers.

Default open source drivers should check what output the monitor is attached to, instead of asuming its the primary out... I guess they'll fix it soon.


i have dvi monitor but doesn't work for me.

---

### Post by ezra1964 on 2010-05-12
> **davidtuti said:**
> Hi,

I have the same problem but booting with usb and unetbootin.
Someone could it works with live cd to can install 10.04?
Do you know if there is a but open?

Many thanks and sorry for my english!


put the cd in and wait for the boot menu
hit the escape key to get to the command line
type:
live-install xforcevesa

:D

---

### Post by drreed on 2010-05-13
> **cosdal said:**
> i have dvi monitor but doesn't work for me.

So which is the primary output on your video card, vga or dvi? If it's dvi then that sounds like it negates that workaround for booting (at least for some people). I'm thinking of buying one of those cards, I need something that will do OpenCL and is reasonably priced.

---

### Post by yozgoesdigital on 2010-05-13
> **drreed said:**
>  I need something that will do OpenCL 

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

As this  links shows it is not suported (yet) for this card

---

### Post by SeePU on 2010-05-16
I'm bumping this since I'm considering the 5770 and maybe... (though, a longshot)...the 5850.

I think the 5770 would suit my needs but with the open source driver not ready yet, one has to use the fglrx driver.

In Lucid, I think one has to go through quite a process to have the binary drivers working and the subsequent features working?  I want to know what to do if there's any issues coming up.  I've read stuff like tearing, colours going strange (slight tints?) or flickering?  The screen going black could just be the driver not optimized?

Comments?

---

### Post by jhonnyas on 2010-05-22
Here's my Experience with the Sapphire ATI Radeon HD5770:
 
Ubuntu 9.10 works out of the box on low resolution using D-sub or DVI or HDMI.
I upgraded to 10.04 my whole system crashed. New version of GRUB2 got ****ed up badly, I was not able to boot my Win7 nor I was able to repair it with LiveCD or USB.
 
Trying to boot 10.04 off from a CD gives blank screen.
I downloaded the alternative install Disk, i could finally install ubuntu with that.
For Login, there was no screen, so i started it in single mode. Downloaded ATI catalyst Driver 10.2 (back in the day) I just don't have time right now to play with it, made it executable and installed it with more or less success. Next time I tried to log in, I finally got a nice login screen, with a whopping resolution of 640x480 with the drivers and I was unable to change to a higher resolution. Got rid of Ubuntu 10.04 and went back to 9.10 no problems there. Honestly I think you should wait till it gets fixed.
 
One more Wonder for those who use ATI 5xxx Series on Linux. Support is NULL. The FLDRX drivers are useless if you want to run Direct3D apps in WINE, they will crash due to an FBO bug (which has not been fixed for god knows how long. See EVE Online and others on wineHQ.)
 
Any1 whos trying to buy an ATI 5750/5770 and is a Pure Linux Fundamentalist and wants to play some games on WINE, that person maybe should go to hell for some R and R before he finally gets it right. Took me 2 sleepless nights to figure out how EVE Online can be made to work without crashing it, but that reduced the cards computational power.
 
My Advice is this: If you are dual booting Windows / Linux and do some Gaming you should be fine with this decision, as long as you don't mind rebooting to Windows to play some games. 

If you wanna use purely Linux, go with NVIDIA.

---

### Post by SeePU on 2010-05-22
Thanks for your perspective, jhonnyas.  Sorry to hear you've had so much trouble.  I do hear you.  I tend to feel that ATI/AMD want to support Linux but just can't or won't invest enough into it.  I don't know whether that means enough money for developers or to test drivers or what.

Have you been to the 'Phoronix' site?   It seems like the best place to go for ATI owners.  Especially for the newest Evergreen cards.  Ubuntu is supposed to be one of the few 'official distros' supported but it sounds like there's still major problems.  Is there a 'safe mode' one can boot up to avoid the black screens?   I have read a few reports that seems to indicate you should download and install the flgrx drivers directly from the ATI/AMD site and install those ones.  Why the Ubuntu graphics drivers installer can't accomodate the newest drivers, I don't know.  

It seems that some users install a 'beta' driver (aka newest but unreleased binary driver) and some versions work and some don't.  Trial and error?

I'd like to get an Evergreen card but I am not sure whether I want to tolerate these issues/problems.  I'm familiar with the process to get Nvidia cards to work so this ATI/AMD process sounds like another can of worms.  Not sure whether it's a new experience I want to know. :)  The Evergreen cards seem to be a good deal, price/performance-wise, though.  But, I use Linux as well as Windows. :-/

---

### Post by jhonnyas on 2010-05-23
> **SeePU said:**
> Thanks for your perspective, jhonnyas. Sorry to hear you've had so much trouble. I do hear you. I tend to feel that ATI/AMD want to support Linux but just can't or won't invest enough into it. I don't know whether that means enough money for developers or to test drivers or what.
 
Have you been to the 'Phoronix' site? It seems like the best place to go for ATI owners. Especially for the newest Evergreen cards. Ubuntu is supposed to be one of the few 'official distros' supported but it sounds like there's still major problems. Is there a 'safe mode' one can boot up to avoid the black screens? I have read a few reports that seems to indicate you should download and install the flgrx drivers directly from the ATI/AMD site and install those ones. Why the Ubuntu graphics drivers installer can't accomodate the newest drivers, I don't know. 
 
It seems that some users install a 'beta' driver (aka newest but unreleased binary driver) and some versions work and some don't. Trial and error?
 
I'd like to get an Evergreen card but I am not sure whether I want to tolerate these issues/problems. I'm familiar with the process to get Nvidia cards to work so this ATI/AMD process sounds like another can of worms. Not sure whether it's a new experience I want to know. :) The Evergreen cards seem to be a good deal, price/performance-wise, though. But, I use Linux as well as Windows. :-/
 
Yea, there is a safe mode in Ubuntu. When you boot up (assuming you only have ubuntu installed) press Esc after POST, and then select the second menu option called safe mode. If you have more than Ubuntu installed then GRUB by default should appear and you can select safe mode  (or single mode) i am not sure how its exactly called. You can also edit your current boot option and remove at the end the stuff called : quiet splash and replace it with single. That way you can get safe mode too.
There is no GUI in safe mode. All you got is a nice terminal or command console. But everyone who is trying to get to know any linux has to have some proficiency at using the command line. From the command line you can use Lynx to go to the ATI/AMD site and download the driver or use wget if you have the exact address.
AFAIK there is no way to install ubuntu 10.04 in graphical mode, at least i tried on all 3 ports and i got no screen. So I used the alternative installer instead. If you installed a Debian before you shouldnt have any problems with it.
As I have said before if you are gonna use 3D apps like on a workstation it would probably work out, but as for games its a nogo.

---

### Post by SeePU on 2010-05-27
Thanks for the info/update!

'Just thought I'd bump this.  I read that Catalyst/Fglrx driver 10.5 is out now.  Did you try the update/upgraded driver?   If so, any better????

When you boot up, which ATI drive is installed by default?  Maybe this is one source of the problems?  Obviously, the open source ATI driver, if installed by default, will NOT WORK yet with Evergreen cards.  I assume you CAN'T have BOTH types of drivers installed or at least, activated.

So, there must be steps for using ONE driver.  

I only know the nuances or should I say nuisances (lol) of using the Nvidia driver... sorry, for my ignorance regarding the ATI stuff...

---

### Post by Anunnaki on 2010-05-27
> **SeePU said:**
> Thanks for the info/update!

'Just thought I'd bump this.  I read that Catalyst/Fglrx driver 10.5 is out now.  Did you try the update/upgraded driver?   If so, any better????

When you boot up, which ATI drive is installed by default?  Maybe this is one source of the problems?  Obviously, the open source ATI driver, if installed by default, will NOT WORK yet with Evergreen cards.  I assume you CAN'T have BOTH types of drivers installed or at least, activated.

So, there must be steps for using ONE driver.  

I only know the nuances or should I say nuisances (lol) of using the Nvidia driver... sorry, for my ignorance regarding the ATI stuff...

I just installed it myself, and the screen tearing is still pretty bad. This is very frustrating. I shouldn't have to boot up Windows just to watch a damn video. Don't think I'll be buying ATI again.

---

### Post by JoePits on 2010-05-30
> **ezra1964 said:**
> put the cd in and wait for the boot menu
hit the escape key to get to the command line
type:
live-install xforcevesa

:D

worked for me thanks!

---

### Post by dadie11 on 2010-05-30
> **northfly said:**
> What does that mean ubuntu 10.04 picked catalyst 10.4?
does these support ATI HD 5770? Thanks.

....for what it's worth..... , I was only able to install 'Mint' 9, 'Isadora' with my old 3450 card fitted. Install the restricted drivers, then reboot with a nice new shiny 'Hawk'......! Great, we're in business. Install Catalyst 10.4 and I'm a happy Bunny. So, Yesterday, I updated to 10.5. and that's when things started to go wrong. No Fancy bits, nothing. So, uninstall atifglrx and amdcccle, then refit the 3450 to get basic functionality back, hoping to revert to 10.4. Zilch. So, a clean install of 'Isadora' then faff about swapping cards again to revert to the 10.4 drivers. No joy. So I'm off to work now, and hopefully I'll get to look at it next week. So I suppose, yes it does support a 5770, but could be a bit fragile.

---

### Post by jinx748 on 2010-07-25
I am having this same issue with ATI Radeon HD 5570 on my desktop with Ubuntu 10.04

It shows the Ubuntu splash screen then goes blank and my monitor tells me its disconnected. I tried it with my HDTV and my dinky lil 19" monitor that it used to work on until I upgraded my video card.

So should I just take this card back and get a Nvidia or will there be a fix for this anytime soon? I am kinda new to Linux.

---

### Post by BinaryBulge on 2010-08-03
If using the Live CD, press the spacebar when you first see the Keyboard + Person logos at the bottom of your screen.  Select your language, then press F6 and back out of the menu (Esc).  Type "xforcevesa" without the quotes.  It will append to the kernel/boot options.  Hit enter to boot.  No more black out.

If using an installed version, when Grub loads, hit Esc.  Choose Ubuntu (recovery mode).  Eventually you will be given the choice to boot with failsafe graphics.  Do so.

Once you get into your desktop/Gnome, go to ATI, and install their latest 10.7 driver.  

I have a Radeon HD 5670. I had no luck installing the fglrx driver directly from Ubuntu/proprietary hardware drivers, but the one from AMD/ATI works fine.  I also had no luck making a package for the installation.  Choose automatic mode.  It's easier.

Reboot when you're done, or just log out and back in.

---

### Post by slow photon on 2010-08-06
Has anyone successfully installed OpenCL on 10.04 with a 5770 HD card?

---

### Post by Beigeman on 2010-08-23
I managed to get Ubuntu 10.04 installed on my computer thanks to tips in this thread, starting the liveCD using "xforcevesa"

Then on the first startup, I told grub to start with the "xforcevesa" tag, downloaded the official ATI drivers from their site, and installed them - after which, no problems at all.

Except one - every time I get a kernel update, it means I have to reinstall the drivers again. Generally I just boot into recovery mode, find the installer and run it from the command line, which works fine - except that it's a pain in the neck to do every time.

Is there any way to make the driver installation persistent between Kernel updates?

Edit: Also, apologies for bringing up a kind of old thread, but I figured it was better than creating another topic on the same issue.

---

### Post by jamessnell on 2010-08-27
This is mega-lame... Seriously.

I'm at least functional as I was adding my 5770, as I already have a ghetto 2600. I was thinking maybe in this decade I'd be able to quad display in Linux without having to spend real time on it.

Ohh well, guess this is what I get for buying an ATI card. I miss the good ol ATI days when they sucked just as hard, but they were independent and Canadian. :\

I just installed the latest ATI drivers right off their site. I rebooted and opened up their catalyst control centre. Suffice to say, my 5770 is listed as an unknown device.

/fail

---

### Post by jamessnell on 2010-08-29
Superficial update: I just checked the ATI website to see if the drivers have been updated to at least now identify my 5770 as such... Suffice to say, a picture is worth 1000 words.
[URL="http://farm5.static.flickr.com/4136/4939849224_ea9ac3c08c_o.png"]
[IMG]http://farm5.static.flickr.com/4136/4939849224_38ca404163.jpg[/IMG][/URL]

/facepalm

---

### Post by jamessnell on 2010-09-14
I just had another go at this, still no luck. :'(

---

### Post by polarbear10 on 2010-09-20
Dear BinaryBulge,

Thank you SOOO much, with your instructions, I got my Sapphire ATI Radeon HD5570 working with Ubuntu Lucid 10.04 - I spent forever searching for Radeon HD 5570 and general ATI / purple screen, lock up etc until I stumbled across your post.  I hope that by inserting my card's name in this thank-you message, it saves others some grief!

You rock - it's contributions like yours that make this all worth while.

PB10

---

### Post by savastux on 2010-11-08
> **polarbear10 said:**
> Dear BinaryBulge,

Thank you SOOO much, with your instructions, I got my Sapphire ATI Radeon HD5570 working with Ubuntu Lucid 10.04 - I spent forever searching for Radeon HD 5570 and general ATI / purple screen, lock up etc until I stumbled across your post.  I hope that by inserting my card's name in this thank-you message, it saves others some grief!

You rock - it's contributions like yours that make this all worth while.

PB10

Hi, I could't find BinaryBulge's response on this thread. Could you please write here what he have told you?

Many thanks,
Savastux

---

### Post by sunnynice on 2010-11-09
> **savastux said:**
> Hi, I could't find BinaryBulge's response on this thread. Could you please write here what he have told you?
 
Many thanks,
Savastux
much details??

---

### Post by savastux on 2010-11-13
> **sunnynice said:**
> much details??

Nevermind.


I've downloaded ATI's driver and installed here.

Now my card is working as it should. (although, I'm no gamer)


Att,
Savastux

---

