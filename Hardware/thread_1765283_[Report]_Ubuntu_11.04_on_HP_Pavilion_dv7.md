---
title: "[Report] Ubuntu 11.04 on HP Pavilion dv7"
date: 2011-05-22
forum: Hardware
---

### Post by Deltik on 2011-05-22
[CENTER][COLOR=Orange][SIZE=6]Ubuntu 11.04 Natty Narwhal[/SIZE]
[COLOR=Black][SIZE=1]on an[/SIZE]
[SIZE=5][COLOR=RoyalBlue]HP Pavilion dv7t[/COLOR][/SIZE]
[/COLOR][/COLOR][SIZE=3]Compatibility Report[/SIZE]
[SIZE=2]by [Deltik]("http://www.deltik.org/")[/SIZE]

_**[SIZE=2][COLOR=Red]UPDATE (02 MAY 2012): Report on Ubuntu 12.04 LTS Precise Pangolin [here]("http://ubuntuforums.org/showthread.php?p=11900678")[/COLOR][/SIZE]**_
_**[SIZE=2][COLOR=Red]UPDATE (18 NOVEMBER 2011): Report on Ubuntu 11.10 Oneiric Ocelot [here]("http://ubuntuforums.org/showthread.php?p=11353243")[/COLOR][/SIZE]**_
[/CENTER]

_**In Short**_
There are a whole lot of new problems in Ubuntu 11.04 that Ubuntu 10.10 did not have when running on my HP Pavilion dv7 laptop computer.


_**Recommendation (issued 22 May 2011)**_
If you feel that the cons of Ubuntu 11.04 (such as increased core temperature, messed-up graphics, increased boot time, missing Compiz effects, and software instability) outnumber the pros (such as Unity, updated software, and new Ubuntu Software Center features), I recommend that you downgrade to either Ubuntu 10.04 or Ubuntu 10.10.

I shall review Ubuntu 11.10 after its release to see if the problems of Ubuntu 11.04 are mitigated.

Finally, everyone should upgrade to Ubuntu 12.04 because it is a long-term support release and is unlikely to be buggy like Ubuntu 11.04 is for HP Pavilion dv7 laptops.


_**What's Wrong Now?**_
Like I mentioned before, *a lot*.  Here's an incomplete list:
[/COLOR][/COLOR]
[LIST]
[*]Graphics Problems
[LIST]
[*]The ATI/AMD proprietary FGLRX graphics driver worked wonderfully in Ubuntu 10.10, but in Ubuntu 11.04, frame rate is significantly lower.  Compiz effects are sluggish.  FlightGear Flight Simulator v2.0.0 is not only noticeably slower; it also doesn't work properly.
[*]Sometimes, when I click on a link, the Mozilla Firefox window opens and there's a gap about 25 pixels high across the screen from the top bar to the rest of the window.  The clicking area remains the same although the display has been shifted downward.  This also happens in other software, like gedit.
[*]My screensaver, which is currently Hypertorus, has performance problems, even though it is a simple screensaver that even my 2006 Toshiba Satellite laptop can run beautifully.  That's not the main concern, though; sometimes when I try to unlock the computer, the screen freezes along with all the controls of the computer.  Processes still run normally, confirmed by continuing a Skype call in the total loss of controls.  To resolve, I have to reboot the computer.
[*]In Ubuntu Classic Desktop, the windows may think that Unity is running and remove the title bar.  With other graphics and performance problems, Ubuntu Classic Desktop doesn't feel like GNOME on Ubuntu 10.10.
[/LIST]
 
[*]Increased Startup Time
[LIST]
[*]Boot time is significantly higher in Ubuntu 11.04 compared with Ubuntu 10.10.  I can now stand up and sit back down and the computer still hasn't started, whereas previously, the login screen loaded much quicker.
[*]Logging in also seems to take a while longer.
[*]Normally, this wouldn't bother me much, but compounded with frequent loss-of-control crashing, it gets quite annoying to wait to get back to work.
[/LIST]
 
[*]Increased Core Temperature
[LIST]
[*]Ouch, hot!  The fan is always spinning at near-full speed, but in Ubuntu 10.10, the fan would only spin like crazy when I was using my laptop intensively.  Now, even when my computer is calm, the fan is screeching like a maniac.
[*]Due to the lack of GNOME panels, I can't conveniently check the core temperature with a widget, but a few days ago, for the first time, my laptop *actually overheated*.  It was sitting on a flat wooden surface, which would have been fine in Ubuntu 10.10, and the screen suddenly flicked off along with the rest of the system.
[/LIST]
 
[*]Decreased Performance
[LIST]
[*]I used to be able to compile big programs on all 8 CPUs, run X-Plane 9 and FlightGear 2.0.0 at the same time and set to the highest quality possible, or run 5 VirtualBox operating systems (including Windows Vista) at the same time *with no performance problems whatsoever*.  That was Ubuntu 10.10.  In Ubuntu 11.04, I often watch System Monitor to make sure that I'm using less than half my 8 GB of RAM and keep the processors calm.
[[IMG]http://img831.imageshack.us/img831/3507/cpuoverwork.th.png[/IMG]]("http://img831.imageshack.us/img831/3507/cpuoverwork.png")
[/LIST]
 
[*]The Good Ol' Compiz Effects... Sacrificed!
[LIST]
[*]I traded my Desktop Cube for Unity.  I miss my cube. :( . 'Nuff said.
[*]Oh, also, my Wobbly Windows feel like Corn Starch Windows.  Graphics performance is poor that dragging windows feels like trying to swim through molasses.
[/LIST]
 
[*]Slow Software
[LIST]
[*]Is it me, or are things in general slow to start up?  I use Firefox, Thunderbird, Pidgin, Skype, GIMP, and more, and all of them seem to be slower than in Ubuntu 10.10.  Even Google Chrome doesn't seem up-to-par.
[/LIST]
 
[/LIST]


_**Not only Ubuntu Natty**_
HP Pavilion laptops have had issues with Ubuntu 10.10 and before.  They are well-addressed in [this guide]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html").


_**General Problems**_
Here are some problems that everybody can experience:

[LIST]
[*]Adding Programs to the Launcher
[LIST]
[*]Have you ever tried adding WINE programs to the launcher?  ...  Yeah, thought so.
[/LIST]
 
[*]Panel Widgets
[LIST]
[*]Why is it so difficult to get my weather indicator?
[*]Or that indicator with my CPU temperatures?
[*]Or that CPU clock throttle?
[*]Or Wanda the Fish?
[/LIST]
 
[*]The Dash for Slow Typers
[LIST]
[*]Some people like Unity but don't like the disorganization of piling all the applications onto one page.  Typing into a search box feels a lot like way back then when you had to type *commands* into the *console* to do anything.  I'm fine with it; others might not be.
[/LIST]
 
[*]"Move to Another Workspace"
[LIST]
[*]Maximized windows no longer have this feature in Unity.  Why?
[/LIST]
 
[/LIST]
Just my two cents. :|


_**Solutions?**_
I was well aware of many problems in Ubuntu 11.04's development iterations.  Initially, I had thought that, knowing Ubuntu's awesomeness, the problems would be worked out.  Nope.  Didn't happen.

The only reason now that I use Ubuntu 11.04 is Unity.  Unity is amazing, and I sacrificed performance, quality, speed, and more for it.

If anyone has solutions for these issues, *please* reply and let me know!  Ubuntu needs to stay as the best operating system ever, and I don't want problems with an HP Pavilion laptop to hinder my opinion.

---

### Post by Deltik on 2011-05-28
This topic got pushed back quite a bit. I broke forum etiquette by double-posting to bump this topic.

So... I contacted the IRC community at [FONT=Courier New]#ubuntu[/FONT], and I have finally decided to reinstall Ubuntu 10.10 Maverick Meerkat.

_**Findings**_

[LIST=1]
[*]The performance problems are caused by the new Linux kernel.
[LIST]
[*]Increased Startup Time — The Linux kernel 2.6.38 series performs worse on HP Pavilion dv7 laptops.
[*]Increased Core Temperature — The new kernel also [increases power consumption]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131") by a lot for this kind of laptop.  It appears that this issue is under high priority investigation by the [Canonical Kernel Team]("https://launchpad.net/%7Ecanonical-kernel-team").
[*]Decreased Battery Life — The new kernel is demanding on the battery and therefore reduces the battery life.
[*]Decreased Performance — Also a kernel problem...
[*]Slow Software — You guessed it: caused by the new kernel
[/LIST]
 
[*]The graphics problem *could* be caused by the proprietary driver being incompatible with Ubuntu 11.04 Natty Narwhal.
[/LIST]


_**What I'm Doing**_
I have faith in Ubuntu 10.10 Maverick Meerkat.  After I reinstall it, I'm going to wait for Ubuntu 11.10 Oneiric Ocelot.  I shall have a compatibility report for Ubuntu 11.10 available to you all when it gets released in October 2011.

I will do an upgrade to Ubuntu 11.10, either by reinstalling or hopping on Ubuntu 11.04.

If the issues are not resolved enough in Ubuntu 11.10, I intend to install Ubuntu 10.04.1 Lucid Lynx LTS and camp on that operating system until Ubuntu 12.04.

No matter what the situation is on Ubuntu 12.04, I *will* be using it and no older release. Ubuntu LTS releases have always been dependable in the 4+ years I've been on Ubuntu.

[LIST]
[*]Ubuntu 8.04 LTS Hardy Heron was a great upgrade from Ubuntu 7.10 and is one of my favorite releases of Ubuntu.
[*]Ubuntu 10.04 LTS Lucid Lynx saved me from leaving Ubuntu as my operating system by the problems in Ubuntu 9.10. I had lived in Ubuntu 9.04 for six months, waiting for Ubuntu 10.04.
[*]Ubuntu 12.04 LTS. ;)
[/LIST]


_**More Information**_
For more information from me or if you have information for me, just ask me either through this forum topic or by my many methods of contact in my Ubuntu Forums profile.

---

### Post by livetobefree on 2011-06-11
I have an HP Pavilion zv5000 and I have been experiencing alot of crashing with Firefox lately, and not being able to update from synaptic for about a month or so.  I have some detailed posts about what the terminal says about why it rejects updating.

 I have been with Ubuntu since 8.04 with a different laptop, and with this laptop since version 9.04.  I also lost my Windows boot option from the boot loader( yes I must dual boot) 3 months ago and have not been able to figure out what to do about it.  I admit I am not at all skilled in code solutions, I can copy paste code into the terminal though if a solution is found.  But who can't? lol

Any advice?

---

### Post by Windwoodtrader on 2011-06-23
.[/QUOTE][U][B]

What I'm Doing[/B][/U]
I have faith in Ubuntu 10.10 Maverick Meerkat.  After I reinstall it, I'm going to wait for Ubuntu 11.10 Oneiric Ocelot.  I shall have a compatibility report for Ubuntu 11.10 available to you all when it gets released in October 2011.

I will do an upgrade to Ubuntu 11.10, either by reinstalling or hopping on Ubuntu 11.04.

If the issues are not resolved enough in Ubuntu 11.10, I intend to install Ubuntu 10.04.1 Lucid Lynx LTS and camp on that operating system until Ubuntu 12.04.

No matter what the situation is on Ubuntu 12.04, I *will* be using it and no older release. Ubuntu LTS releases have always been dependable in the 4+ years I've been on Ubuntu.

.[/QUOTE]

Thanks for the in depth rational. 

I do have a question-

Why would you go back to 10.04 when you say that 10.10 Maverick is what you have faith in? Is the LTS release the deciding factor?
What is LTS anyway?

I am new to UBUNTU and trying to understand.

---

### Post by Deltik on 2011-06-23
> **Windwoodtrader said:**
> Thanks for the in depth rational. 

I do have a question-

Why would you go back to 10.04 when you say that 10.10 Maverick is what you have faith in? Is the LTS release the deciding factor?
What is LTS anyway?

I am new to UBUNTU and trying to understand.
**LTS** stands for **l**ong-**t**erm **s**upport.  So far, all the LTS releases have been amazing, and I am very confident that Ubuntu 12.04 LTS will be the best Ubuntu yet.

---

### Post by flipmatthew on 2011-06-28
This is a very important issue guys, unity should unify the components and hardware, not hinder the performance.

---

### Post by austintexican on 2011-07-10
> **Deltik said:**
> _**What I'm Doing**_
I have faith in Ubuntu 10.10 Maverick Meerkat.  After I reinstall it,  I'm going to wait for Ubuntu 11.10 Oneiric Ocelot.  I shall have a  compatibility report for Ubuntu 11.10 available to you all when it gets  released in October 2011.

I will do an upgrade to Ubuntu 11.10, either by reinstalling or hopping on Ubuntu 11.04.

If the issues are not resolved enough in Ubuntu 11.10, I intend to  install Ubuntu 10.04.1 Lucid Lynx LTS and camp on that operating system  until Ubuntu 12.04.

Hi, I hope you have time to answer this. :)

I just installed Ubuntu 11.04 on my dv7t with the 1GB ATI 5650. I opted to use Gnome instead of Unity because it's just more comfortable for me as an old-school Windows user.

Everything's going more-or-less fine, but unfortunately it doesn't detect my external LCD hooked up to the HDMI port. I installed the ATI/AMD proprietary drivers, but that hasn't helped at all.

So, should I downgrade until 12 comes out? If so, could you tell me specifically which version of Ubuntu 10? Also, should I do a full reformat/reinstall or is it possible to "overwrite" 11?

Thanks!

---

### Post by Deltik on 2011-07-12
> **austintexican said:**
> Hi, I hope you have time to answer this. :)

I just installed Ubuntu 11.04 on my dv7t with the 1GB ATI 5650. I opted to use Gnome instead of Unity because it's just more comfortable for me as an old-school Windows user.

Everything's going more-or-less fine, but unfortunately it doesn't detect my external LCD hooked up to the HDMI port. I installed the ATI/AMD proprietary drivers, but that hasn't helped at all.

So, should I downgrade until 12 comes out? If so, could you tell me specifically which version of Ubuntu 10? Also, should I do a full reformat/reinstall or is it possible to "overwrite" 11?

Thanks!
Hello Austin, my nearby stranger,

Yeah, you should downgrade to Ubuntu 10.04 or Ubuntu 10.10. It's completely up to you.  I've never actually tested Ubuntu 10.04 on my HP dv7t.  If you're waiting for Ubuntu 12.04 and want to skip Ubuntu 11.10,  you should definitely downgrade to Ubuntu 10.04.

There is no way to "downgrade" Ubuntu, actually.  You're going to have to reinstall over Ubuntu 11.04.  The Ubuntu installer should be able to assist you with that.

I'll go over the advantages and disadvantages of Ubuntu 10.04 and Ubuntu 10.10 as far as I know.


_**Ubuntu 10.04 Lucid Lynx LTS**_
_Advantages_

[LIST]
[*]Long-term support.  You can be sure that Ubuntu will be stable for you for a while.
[*]Direct upgrade to Ubuntu 12.04 LTS.  Ubuntu has never messed up an LTS before, and I don't think they will next time.
[/LIST]
_Disadvantages_

[LIST]
[*]Many software will not be the latest.  You need to add apt repositories to update some of the software to the latest version, for example, Mozilla Firefox 5 will not be included in the default updates of Ubuntu 10.04, so you're going to need to run:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
```
to install the latest version of Mozilla Firefox.
[/LIST]

_**Ubuntu 10.10 Maverick Meerkat**_
_Advantages_

[LIST]
[*]The software, although somewhat outdated, is newer than Ubuntu 10.04 LTS by default, and I'm not having issues with any of them except for Eye of GNOME, the image viewer.
[*]It includes the font "Ubuntu", which is a nice-looking font.
[/LIST]
_Disadvantages_

[LIST]
[*]The software is still not the latest.  Ubuntu 10.10 has MuseScore 0.9.6 and FlightGear 1.9.1 by default, although Ubuntu 11.04 includes MuseScore 1.0 and FlightGear 2.0.0.
[*]To upgrade, you'll have to do multiple of them to get to the latest Ubuntu.  When Ubuntu 12.04 LTS is released, you'll have to upgrade to Ubuntu 11.04, then upgrade again to Ubuntu 11.10, and upgrade one more time to Ubuntu 12.04.  It's quite a hassle.
[/LIST]

I don't know.  Ultimately, I think that Ubuntu 10.04 is a better choice for you.

---

### Post by austintexican on 2011-07-12
Thanks Deltik! I think I'll go with 10.04.

Last question: do you think this will solve the issue of my external LCD not being seen on the HDMI port? (I got the Radeon 5650 for my dv7t, btw.)

---

### Post by Deltik on 2011-07-13
It might. After all, the graphics problems I experienced with Ubuntu 11.04 were caused by the changes they made from Ubuntu 10.10.

[A comment in this older post from Ubuntu brainstorm]("http://brainstorm.ubuntu.com/idea/22085/") indicates that HDMI did indeed work on an HP Pavilion dv7 laptop computer.

I would test HDMI on my computer to my TV if I had time, but I'm leaving for a vacation tomorrow.

Besides, even if your external display problem doesn't get resolved, you'll still get the following benefits for going back to Ubuntu 10.04:

[LIST]
[*]Other graphics problems won't be present.
[*]Faster booting
[*]Stabler and cooler internal temperature
[*]Increased performance
[*]If you're fancy, you can also get [cool Compiz effects]("http://www.youtube.com/watch?v=i0iPgHXwpiE").
[/LIST]

---

### Post by austintexican on 2011-07-13
> **Deltik said:**
> It might. After all, the graphics problems I experienced with Ubuntu 11.04 were caused by the changes they made from Ubuntu 10.10.

[A comment in this older post from Ubuntu brainstorm]("http://brainstorm.ubuntu.com/idea/22085/") indicates that HDMI did indeed work on an HP Pavilion dv7 laptop computer.

I would test HDMI on my computer to my TV if I had time, but I'm leaving for a vacation tomorrow.

Besides, even if your external display problem doesn't get resolved, you'll still get the following benefits for going back to Ubuntu 10.04:

[LIST]
[*]Other graphics problems won't be present.
[*]Faster booting
[*]Stabler and cooler internal temperature
[*]Increased performance
[*]If you're fancy, you can also get [cool Compiz effects]("http://www.youtube.com/watch?v=i0iPgHXwpiE").
[/LIST]


Awesome, can't live without my second monitor.

Thanks again!

---

### Post by ninjajl on 2011-07-22
I'm fairly new to Ubuntu as well. My questions are 1- is there any way to fix the problems of the core temp in 11.04 and 2- is there anyway to fix the HDMI connectivity problem?

---

### Post by Deltik on 2011-07-22
> **ninjajl said:**
> I'm fairly new to Ubuntu as well. My questions are 1- is there any way to fix the problems of the core temp in 11.04 and 2- is there anyway to fix the HDMI connectivity problem?
[LIST=1]
[*]The core temperature issue is directly related to a problem with the new kernel that demands additional power use. This is a [high priority bug for the Canonical Kernel Team]("https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/760131"). Hopefully, they will get this resolved in Ubuntu 11.10 Oneiric Ocelot.
[*]From findings by austintexian, the HDMI connectivity problem is caused by AMD not updating their proprietary driver. I believe that he has already contacted AMD to get a fix for the problem, but feel free to contact the company on your own.
[/LIST]

[QUOTE=limzone]can i use it as virtul windows mean on windows xp[/QUOTE]
This thread is not the appropriate place to ask this question. Moreover, I do not understand your question.
Ubuntu does run on VirtualBox on Microsoft Windows XP, and Microsoft Windows XP does run on VirtualBox on Ubuntu.
As for HP Pavilion dv7 laptops, due to a kernel problem, your laptop could easily overheat from running a virtual operating system on Ubuntu 11.04 Natty Narwhal.

---

### Post by weezilla on 2011-07-30
I finally got Ubuntu dual booted. I'm glad I did some research on why 11.04 runs hot on my DV7t. I will be running simulations on it, so I imagine it will get way too hot.

Is anyone running 10.04 on their DV7t? I will reinstall tomorrow if it runs fine (I may just go for it anyways... I can't use 11.04).

Thanks :)

---

### Post by Deltik on 2011-07-30
> **weezilla said:**
> Is anyone running 10.04 on their DV7t? I will reinstall tomorrow if it runs fine (I may just go for it anyways... I can't use 11.04).
There was a guide somewhere on the Internet dedicated to Ubuntu on HP Pavilion laptops. I remember reading that Ubuntu 10.04 works as well as Ubuntu 10.10 does on those kinds of laptops.

---

### Post by weezilla on 2011-07-30
Downloading 10.04 now. *Sniffle* 11.04 was so pretty. Will let you know how well it works first hand.

EDIT: Seems to be working pretty well with 10.04.3 x64 LTS. Definitely a speed difference.

---

### Post by austintexican on 2011-07-31
Hey Deltik

I was just poking around in the BIOS and noticed there's a setting for virtual machines support, which is disabled by default (on my HP dv7t, anyway).

Were you aware of this setting? If not, do you think this might have something to do with the heat issues you were having while running VMs? That is, if you haven't enabled VM support in your BIOS?

Just a thought :)

---

### Post by Deltik on 2011-07-31
> **austintexican said:**
> I was just poking around in the BIOS and noticed there's a setting for virtual machines support, which is disabled by default (on my HP dv7t, anyway).

Were you aware of this setting? If not, do you think this might have something to do with the heat issues you were having while running VMs? That is, if you haven't enabled VM support in your BIOS?

Just a thought :)
I am very aware of that setting, and it has nothing to do with the heating issues while running virtual machines.  I've already checked BIOS, and there's nothing I can do to ameliorate the problems of Ubuntu 11.04.

---

### Post by austintexican on 2011-07-31
> **Deltik said:**
> I am very aware of that setting, and it has nothing to do with the heating issues while running virtual machines.  I've already checked BIOS, and there's nothing I can do to ameliorate the problems of Ubuntu 11.04.

Bummer, but I'm not surprised. It seems that the BIOS in the dv7 barely lets you do anything more complicated then set the clock. I was looking for a way to disable switchable graphics at the BIOS level, but didn't see anything.

---

### Post by Deltik on 2011-07-31
> **austintexican said:**
> Bummer, but I'm not surprised. It seems that the BIOS in the dv7 barely lets you do anything more complicated then set the clock. I was looking for a way to disable switchable graphics at the BIOS level, but didn't see anything.
Typical. Most BIOS are really terrible.

There is something about **pcie_aspm=force** that I found, and I have yet to try it out:
_Basic Information:_ [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/122](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/122)
_Usage:_ [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/127](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/127)
_A Test Result:_ [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/136](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/136)
_Some Pessimist:_ [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/137](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/137)
_Detailed Information:_ [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/141](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/141)

---

### Post by ninjajl on 2011-08-10
I figured out a way to reduce the core temp.

When booting up in 11.04, before you put in the password to login, there is a menu at the bottom of the screen that says what type of Ubuntu you're running. Click on that menu and select the "Ubuntu Classic" option.

The down side to that is your desktop won't be as "pretty," but it will reduce the core temp and extend the life of your comp. Also. Your Windows button won't work in the classic desktop.

---

### Post by Deltik on 2011-08-10
> **ninjajl said:**
> I figured out a way to reduce the core temp.

When booting up in 11.04, before you put in the password to login, there is a menu at the bottom of the screen that says what type of Ubuntu you're running. Click on that menu and select the "Ubuntu Classic" option.

The down side to that is your desktop won't be as "pretty," but it will reduce the core temp and extend the life of your comp. Also. Your Windows button won't work in the classic desktop.
_Status:_ **[COLOR=Red]UNCONFIRMED[/COLOR]**

I've already tried that before I removed Ubuntu 11.04. I did not record a meaningful difference in the core temperature, and the super key was still working (if I remember correctly). "Pretty"? I've used the Ubuntu Classic layout since Ubuntu 7.04.

Ubuntu Classic on Ubuntu 11.04 was also buggy. Frequently, Ubuntu would think that it was running Unity, so it would remove the window borders. It also thought that the bar at the top belonged to Unity, so I had some graphics issues there.

Even if the core temperature problem was resolved by Ubuntu Classic (which it can't be because it's a kernel issue), all the other problems still persist.

---

### Post by mbooma on 2011-09-24
Hi

I have some problems with hp dv7 7177sf

*right click on clickpad doesn't work and multitouch on clickpack doesn't work too.

*hybrid graphique card change ati 5650 / intel HD doesn't work, driver for ati doesn't work correctly, when i open Ati catalyst I have en error

*I must install Ralink driver for wifi card to make it work corectly

*on windows I have 2 or 3 hours batery performance, 30 minutes on uuntu :(

---

### Post by Deltik on 2011-09-24
> **mbooma said:**
> I have some problems with hp dv7 7177sf
"7177sf" isn't a valid model variant. I don't know what HP Pavilion dv7 you're referring to.
Nevertheless:

> **mbooma said:**
> *right click on clickpad doesn't work and multitouch on clickpack doesn't work too.
I just found a [workaround]("http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/") that I think may work: [http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/](http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/)

> **mbooma said:**
> *hybrid graphique card change ati 5650 / intel HD doesn't work, driver for ati doesn't work correctly, when i open Ati catalyst I have en error
My ATI Mobility Radeon HD 5000 Series graphics card driver, installed by "Additional Drivers", works quite well.

> **mbooma said:**
> *I must install Ralink driver for wifi card to make it work corectly
I'm clueless here. My wireless card works out-of-the-box.

> **mbooma said:**
> *on windows I have 2 or 3 hours batery performance, 30 minutes on uuntu :(
Looking at the [power consumption bug]("https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/760131"), it looks like a fix was committed (made, but waiting for release) for this bug.  I hope that battery life improves after installing the fix.

---

### Post by mbooma on 2011-10-03
sorry wrong model 4177sf ^^

any way to use graphique card like windows ?

---

### Post by Deltik on 2011-10-03
> **mbooma said:**
> sorry wrong model 4177sf ^^

any way to use graphique card like windows ?
The HP Pavilion dv7-4177sf comes with ATI Mobility Radeon HD 5650 Graphics.  I have the same type (I think? Unless "[For Quad Core Processors]("http://img530.imageshack.us/img530/4337/hphomehomeofficestoresh.png")" means something different?).

Did you install the restricted drivers for that graphics card on Ubuntu?

In Ubuntu Unity:

[LIST=1]
[*]Dash
[*]Search for and open "Additional Drivers".
[*]Activate the "ATI/AMD proprietary FGLRX graphics driver"
[*]Reboot.
[/LIST]

---

### Post by Deltik on 2011-10-16
[CENTER][[SIZE=7][FONT=Arial Black]UPDATE[/FONT][/SIZE]]("http://ubuntuforums.org/showthread.php?p=11353243")
[/CENTER]

I wrote a report for Ubuntu 11.10 Oneiric Ocelot on HP Pavilion dv7 laptop computers. Click [here]("http://ubuntuforums.org/showthread.php?t=1862284") to see the updated report.

---

### Post by Voluntocracy on 2011-11-04
When I follow your link <http://ubuntuforums.org/showthread.php?t=1862284> I get the error:

vBulletin Message                                                           No Thread specified. If you followed a valid link, please notify the [administrator]("http://ubuntuforums.org/sendmessage.php")

---

### Post by Deltik on 2011-11-04
Thanks for catching that. An Ubuntu Forums moderator deemed my thread a "recurring discussion" and moved it, which invalidated the old link.

This is the new link: [http://ubuntuforums.org/showthread.php?p=11353243](http://ubuntuforums.org/showthread.php?p=11353243)

---

### Post by Deltik on 2012-05-03
[CENTER][[SIZE=7][FONT="Impact"]UPDATE[/FONT][/SIZE]]("http://ubuntuforums.org/showthread.php?p=11900678")
[/CENTER]

I wrote a review for Ubuntu 12.04 LTS Precise Pangolin on computers like my HP Pavilion dv7t-4100 laptop. Click [here]("http://ubuntuforums.org/showthread.php?p=11900678") to see the updated report.

---

