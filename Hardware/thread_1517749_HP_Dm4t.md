---
title: "HP Dm4t"
date: 2010-06-25
forum: Hardware
---

### Post by Veector on 2010-06-25
I just got the notebook today, the following things do not work
-the track pad (does not recognize that there are two separate areas for right click and left click, it sees the whole thing as a single button)
-The Finger print reader(i cant even find a program that would allow me to login with the finger print reader, but i think that the OS cant see the fingerprint reader ether)
-I have an SSD and i don't think that that there is a TRIM feature in ubuntu, if there is how could i enable it.

---

### Post by jediborger on 2010-06-25
Hey, I just ordered one as well almost as impulse since the specs on this laptop looked so nice. Although now I am seeing several issues but I'm game for working on them once I get mine. 

Anyways perhpas these pages will help with the trackpad as I was reading it was taken from the ENVY line.

[http://ubuntuforums.org/showthread.php?t=1406691]("http://ubuntuforums.org/showthread.php?t=1406691") Thread on getting the ENVY 15 to work
[http://www.spinics.net/lists/linux-input/msg06333.html]("http://www.spinics.net/lists/linux-input/msg06333.html") A patch for the trackpad, not sure if it's the same but I would bet it is.

---

### Post by Veector on 2010-06-25
I don't understand how i would install this patch, I'm not that goo with these things

---

### Post by Veector on 2010-06-26
Do you guys think that there will ever be a driver written for this touchpad?

---

### Post by jediborger on 2010-06-26
I will try to make this driver for you. Mine is coming Friday hopefully :)

I presume you are running 10.04 but I need to know if you have 32 or 64 bit installed. If you don't know you can run the following in the terminal and paste the output back here.
```
uname -a
```

As for you last question, yes there is a driver being worked on with all the goodies, gestures and such. [http://www.synaptics.com/solutions/technology/gestures/touchpad-linux]("http://www.synaptics.com/solutions/technology/gestures/touchpad-linux") Unfortunately I did not see an ETA on when it might be ready.

---

### Post by jediborger on 2010-06-27
I did some browsing and it seems the above patch was applied to the synaptics driver for the next version of Ubuntu, maverick.

So if you're game, go ahead and install one of these two files, first one is the 32 bit version and the second is the 64 bit version.
[https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-synaptics_1.2.2-2ubuntu1_i386.deb]("https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-synaptics_1.2.2-2ubuntu1_i386.deb")
[https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-synaptics_1.2.2-2ubuntu1_amd64.deb]("https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-input-synaptics_1.2.2-2ubuntu1_amd64.deb")

There is a possibility they may not work, since they were made for the next version but it should be pretty low. Otherwise you're next option would be to try the livecd of Maverick alpha 1.

---

### Post by Veector on 2010-06-27
I'm running 64 bit and when i run the installer i get this message "Error: Dependency is not satisfiable: xorg-input-abi-9.0", I'm not sure what to do now.
Thank you so much for your help, i really appreciate it.

---

### Post by jediborger on 2010-06-28
Hey I just got mine today. Don't take this the wrong way but you did notice that the lower corners of the trackpad "click" and depress. Running Lucid on my machine the buttons work, albeit it seems that half the time I need to do multiple clicks before it registers. Also that button between the right alt and ctrl keys does the same as a right click.

My next set of advice would be test the maverick livecd since that abi package doesn't exist in the Lucid repositories. You can get the alpha one images of maverick [here.]("http://cdimages.ubuntu.com/releases/maverick/alpha-1/")

This is just my first impression of an hour but I have to say Ubuntu runs a lot snappier than Windows 7 on this machine. A few outstanding issues:
-fingerprint reader
-switchable graphics, both cards are on, killing battery (hopefully will have a better estimate in the coming days)
-buttons on trackpad are inconsistent, but working
(Veector, can't comment on SSD issues as I got a platter hdd)

List of working things, (it's always nice to look at the bright side :)
-microphone
-keyboard
-wireless (I opted for the intel with bluetooth)
-webcam
-cd drive (I have to use my fingernail to press the button)

Still to test:
-vga and hdmi output

---

### Post by Veector on 2010-06-30
I´m wondering if there is ever going to be finger reader support for the dm4t, hopefully it comes before Ubuntu 11.04

---

### Post by jediborger on 2010-07-01
I know you aren't a developer and I am just a hopeful college student. But this page documents the progress of the fingerprint reader in this line of laptops. [http://www.reactivated.net/fprint/wiki/Unsupported_devices#Validity_VFS101]("http://www.reactivated.net/fprint/wiki/Unsupported_devices#Validity_VFS101")

Although the fprint project doesn't look like it has had any activity in two years based on the latest posting to the site in 2008. Maybe someone knowledgeable would find this useful to take up. I wish I knew something about writing kernel drivers but I am just now getting over the acpi calls. Which btw if you are interested I think I found a way to turn off the ATI card under Ubuntu, so at least it's not sucking power. I haven't found a way to use the card though. Proprietary fglrx doesn't do the trick and I haven't looked that much into setting up the radeonhd driver.

Any luck on the touchpad for you, Veector?

---

### Post by Veector on 2010-07-01
The touch pad still does not work properly, to left click i need to touch the very lover left corner of the touch pad and to right click i must touch the very lower right corner of the touchpad. And about the fingerprint reader, the only thing we can do now is just wait, right?

---

### Post by Veector on 2010-07-13
Is there a way to add more 'steps' to the brightness button, what i mean by this is that when ever i press it i only get 5 different brightnesses, is there a way to add more.

---

### Post by Prominence on 2010-07-16
Hey guys, I've been looking at this series of laptops and I like what I see in them, but would you recommend me getting one?

---

### Post by lazurrpewpew on 2010-07-18
Hey dm4t buddies!

I've been looking for a solution to the touchpad problem basically for the past month (ie for as long as I've had this computer.) Unfortunately, I've had no luck. The fingerprint reader not working is not such a big deal for me, but the touchpad issue is such a downer. Not being able to click and drag drives me crazy! Anyway, I'll keep looking around and we can all keep our fingers crossed that there will be solution soon!

Btw, jediborger, when I first got this laptop, I was so upset because I thought the touchpad buttons didn't work. I didn't notice that they actually depressed. I even called the hp support line and subsequently felt like a total idiot.

---

### Post by jediborger on 2010-07-21
I have an interesting issue with the battery charge state. Just wondering if anyone else has this issue.

After charging the battery fully and unplugging it to use, Ubuntu continues to state that the battery is fully charged. It never realizes that it is discharging unless I plug the cable in and pull it out.

Interestingly if I look at the Power Statistics, it shows the correct battery Percentage but the Rate is always 0.0 Watts. Might this be an acpi problem?

---

### Post by tmfs on 2010-08-07
So did anyone figure out how to make the touchpad work well? I installed kcm-touchpad but I've had to disable edge scrolling (it's horrible when you are typing code), and two finger tap for things to work smoothly and even now the multitouch doesn't work so the cursor still jumps around if I place my second finger on the touchpad.

---

### Post by borsato.luca on 2010-08-14
hi guys
i'm new to the forum, but I use Ubuntu for some time.
I bought the HPdm4t and I found the same problems:
- touchpad, click only in the below corners and problem with drag (cursor change position with the second finger)
- battery that lasts a very short (less the 2 hours, that's a big deal!!!)
- stop one of the two graphics card
- fingerprint doesn't work (not a big deal)
Has anyone found any solution?
Thank you

If you need some information tell me
(Sorry for my English, i'm Italian)

---

### Post by jediborger on 2010-08-14
Hi borsato.luca,

Great to see some interest in this laptop. Overall I like this laptop a lot but it does have some sort comings on Linux. The biggest right now is the battery life which is downright terrible in comparison to Windows 7 on this machine. While there are a few things you can do to increase the life and I have gotten to about 3 hours by turning off the second graphics card and running powertop. Unfortunately the power consumption issue is more of a linux kernel one which can't be fixed very easily.

If you're curious about turning off the graphics card check out this page: [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html]("http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html")

And powertop can be found in the repositories.

---

### Post by polo29 on 2010-08-17
Has anyone tried more recent distributions like OpenSuse 11.3 or Mandriva 2010.1 (both are very easy to install and test)? These distributions have more recent kernels and dont necessary handle hardware the same way as Ubuntu.

---

### Post by Veector on 2010-09-21
I sent a message to the company that makes the fingerprint reader and they said > We plan to release Ubuntu support package by the end of the year. It will include proprietary sensor daemon with sample for fprint. We do not have plans for Fedora, but the same package might work (no guarantee).

---

### Post by lazurrpewpew on 2010-10-02
that's good news, veector!
10.10 comes out in about a week...does anyone know if there are any improvements that will address trackpad/battery life issues?

---

### Post by jediborger on 2010-10-11
Sadly I have to report that upon booting the maverick iso I get a blank screen. I get the boot splash for a little bit then the monitor seems to just shut off. Unfortunately that doesn't leave me much in the way of figuring out what is going wrong. Any one else have good/bad news on maverick?

---

### Post by goinglinux on 2010-10-13
jediborger,

When I installed Ubuntu 10.10 my monitor was shut off as well. I noticed that I could see a "shadow" of the objects on the screen. On a hunch, I tapped the button that turns the screen brightness up. Problem solved!

---

### Post by domino1241 on 2010-12-25
I know this thread has been dead for a few months, but is anyone having better luck with the touchpad?  I tried Mint instead of Ubuntu because of the problems, but they seem to be identical to what you are all reporting.  In short:
[LIST=1]
[*]Right click broken
[*]Can't drag/drop with the button and touchpad
[*]The buttons seem to also be part of the touchpad (can this be turned off?)
[/LIST]
I haven't tried a whole lot of solutions, but if the touchpad problem can't be fixed I'm going to return it for another computer  :-(

I hope someone has the answer out there!

---

### Post by Veector on 2010-12-26
Yeah I'm still having the same problems, I tried Linux mint debian 64bit and the touchpad is in usable even worse than ubuntu 10.10 so that's I'm just sticking with 10.04. I am hopefully that this will not be and issue in ubuntu 11.04 I'm gonna have to give the live image a try, I'll get back to you guys on that.

---

### Post by ElSlunko on 2010-12-26
So many HP dm* threads about the touchpad.

This worked for me :

> **uppertoe said:**
> Not sure it's been mentioned in this thread, but [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) has a nice bit of advice that worked for my hp 210.

Installing the package at 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/167](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/comments/167)

worked like a dream - no two finger scroll, but click and drag is working nicely; something I think is a little more important.

---

### Post by gregalynch on 2011-01-15
I finally have the touchpad on mine working (pretty much) they way I want it to.  Here's what I did:

1. I followed the advice in post #54 of this thread: [http://ubuntuforums.org/showthread.php?t=1388164&highlight=hp+mini+210+touchpad&page=6](http://ubuntuforums.org/showthread.php?t=1388164&highlight=hp+mini+210+touchpad&page=6) 

This makes it so the cursor doesn't jump around and enables most of the features.  You can do everything w/ the touchpad, just not always in the way you expect.

a. Left click with physical click or single tap
b. Right click with a two-finger tap (physical right-click is still recognized as a left click)
c. Scroll with two fingers
d. Click and drag by double-tapping and holding down the second tap then dragging

2. The touchpad is in an irritating location relative to the keyboard, which is probably why hp put the little dot in the upper left corner to turn the touchpad on and off.  That doesn't work with ubuntu, but there's an easy workaround.  The script here: [http://ubuntuforums.org/showthread.php?t=1656478](http://ubuntuforums.org/showthread.php?t=1656478)  will toggle the touchpad on and off.  

You can then assign a custom keystroke to execute the script and voila.  Just as easy as double tapping the little dot.

---

### Post by Marc128000 on 2011-01-18
I'm using a HP Envy 14 right now and it has the same issue with the clickpad. The post above is the right way to go. 

I made it a bit easier and made a tutorial on my blog.
Hopefully you find it helpful.
[http://linuxenvy.blogspot.com/2011/01/touchpad-fixed.html](http://linuxenvy.blogspot.com/2011/01/touchpad-fixed.html)

---

### Post by gregalynch on 2011-01-18
has anybody been able to get the HDMI output to work?  I can detect the TV when its attached (it shows up in the monitors manager) but can't get any picture or sound to appear on/from the TV

---

### Post by asdir on 2011-01-26
@HDMI: Same problem here, no solution yet.
@Graphics in general: Has anyone got the proprietary ATI driver working? (got dm4 here, not dm4t; just for clarification)

---

### Post by MaskdParader on 2011-04-17
I just got a new dm4-1273ca, I'm having the same touchpad issues (no left click, sporadic movement when I try to click or tap and drag a window, or when the touchpad just doesn't like me) as everyone else in here.

I've used ubuntu off and on for years, I usually just give up and go back to Windows or OSX because I often can't find a solution for one or two nagging compatibility issues. This time, I want to try and use ubuntu exclusively, eventually. 

I was wondering if there are any new advancements with the trackpad drivers, battery life, ect.

Sorry if I sound like a jerk or an idiot, I never know how to act on forums.

---

### Post by Veector on 2011-04-21
I went distro-hopping and when i installed openSUSE 11.4 i found that i had the best hardware compatibility, all right, middle and left click work properly, the only thing that does not work in openSUSE 11.4 is the fingerprint reader(but this only works on windows). Just thought i would let you guys know.

---

### Post by cbennett926 on 2011-04-21
I have heard that there are new drivers that make the finger print reader work!

---

### Post by gregalynch on 2011-05-17
On the HDMI front.  I had to downgrade back to Maverick after Natty crashed my system, and the first time I plugged in the HDMI it worked, audio and video.  However, it worked for about 2 minutes and then the screen went black again.

Edit:
Nevermind.  It turned out the HDMI cable I bought at Big Lots was not good.  Who'd have thought?  HDMI actually works OOTB.

---

### Post by gregalynch on 2011-09-06
Is anyone running Oneric on this yet?  Natty was unstable and crashed all the time; I'm wondering whether they have that bug fixed in Oneric

---

### Post by deku_nut on 2011-10-14
> **gregalynch said:**
> Is anyone running Oneric on this yet?  Natty was unstable and crashed all the time; I'm wondering whether they have that bug fixed in Oneric


I'm running 11.10 (I was running 11.04). My dm4 is chugging along pretty swell now (I did both an upgrade and then later decided to wipe/fresh install.) CCSM runs fine and as far as I can tell everything is supported OOTB.

My reccomendation: install ubuntu from a flash drive, full wipe/fresh install in under 10 minutes.

**ONE ISSUE** : the "two finger scrolling" doesn't seem to work. However the option is in the sys prefs

---

### Post by gregalynch on 2011-10-14
I just upgraded to 11.10 yesterday.  Its works fine now, but on the fist install I added CCSM and it completely wrecked unity.  When I opened CCSM and clicked the 'preferences' tab, Unity crashed (meaning I lost the launcher, indicators, and lots of other things) and wouldn't come back on a restart.  I didn't realize it was CCSM that did this, but the exact same thing happened again after a reinstall of the OS.  Now I'm on #3 (and I've learned my lesson)

Does anyone know what is causing this?  Its about as violent a crash as Ubuntu has ever thrown at me.

---

