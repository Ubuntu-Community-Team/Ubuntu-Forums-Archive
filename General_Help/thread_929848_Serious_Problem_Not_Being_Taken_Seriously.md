---
title: "Serious Problem Not Being Taken Seriously"
date: 2008-09-25
forum: General Help
---

### Post by TheZorch on 2008-09-25
This isn't really a request for help but an attempt to shed light on a serious flaw in Ubuntu 8.04 that needs to be addressed because it is preventing new users form adopting the OS.

This has to do with the problem of using being locked at a screen resolution of 640x480.  Ok, doesn't sound like a big issue to most of you but in reality this is a rather serious problem.  We want Ubuntu to be taken seriously in the mainstream.  This problem threatens that in a very big way.

Normally during the install Ubuntu probes hardware to get information from them in order to determine which drives need to installed or downloaded and installed.  Many times Ubuntu is unable to determine what kind of monitor people are using and the OS falls back on a default monitor setting.  This locks people at a safe resolution of 640x480.

In Ubuntu 7.10 the screen resolution applet allow users to choose what kind of monitor they have.  This was replaced in Ubuntu 8.04 with a screen resolution applet that doesn't let you do this.  Kubuntu 8.04 KDE4 Remix has the same problem.  Users can't change their monitor settings from within X.org.  They're forced to come to this forum and other places to find a solution.

The problem is many people are hearing about how user friendly Ubuntu is, so many people who are computer novices are getting interested in the OS.  They're all familiar with Windows.  When they experience this problem and run into this issue and see what they need to do to fix they're turned off by the fact that they need to all this stuff just to fix a very simple problem.  It making people who would normally give Ubuntu serious consideration a very bad impression and they write off the OS without giving it a fair chance.

Just one simple feature, to be able to change your monitor settings, is having this kind of major affect.  Its often the little things that really have the biggest impact.

We need to let the Development Community responsible for maintaining Ubuntu that this is a serious problem that needs to be address and not ignored.

---

### Post by mikewhatever on 2008-09-25
There is a program hidden in the menu under Other->Screens and Graphics. You can also start it from Terminal with gksu displayconfig-gtk. Anyway, if you feel devs should know, file a bug report on launchpad.net.

---

### Post by TheZorch on 2008-09-25
> **mikewhatever said:**
> There is a program hidden in the menu under Other->Screens and Graphics. You can also start it from Terminal with gksu displayconfig-gtk. Anyway, if you feel devs should know, file a bug report on launchpad.net.

Unfortunately this is just skirting around the issue at hand.  Users shouldn't have to do that, ever, for something this fundamentally simple.  I don't see why its so hard to understanding that taking this option out of the screen resolution applet is a extremely bad decision.  I consider it a bug.

Why is this so hard to understand?

---

### Post by mikewhatever on 2008-09-25
I don't know, nor do I know what were the fors and against for that decision. What's done is done, and we all know Ubuntu is not perfect. What does it help discussing it here.

---

### Post by DrMelon on 2008-09-25
> **TheZorch said:**
> Unfortunately this is just skirting around the issue at hand.  Users shouldn't have to do that, ever, for something this fundamentally simple.  I don't see why its so hard to understanding that taking this option out of the screen resolution applet is a extremely bad decision.  I consider it a bug.

Why is this so hard to understand?

Well, obviously you aren't as aware of other implications are the rest of us are.

Allowing the user to change it right off the bat will also allow unsolicited applications to do the same, don't you understand?

Besides, it's not really a terribly awful issue anyway, it's easily sorted. 

Why is it so hard for you to understand the complicated areas of OS development?

---

### Post by DrMega on 2008-09-25
Doesn't this problem only exist with the generic display driver? When I installed Gutsy (and Hardy on a different machine), the 3rd party driver applet thingy offered to sort out the drivers. I just let it and job done.

Unless of course there is a problem that I'm not aware of with detecting certain hardware.

---

### Post by mikewhatever on 2008-09-25
> **DrMelon said:**
> Well, obviously you aren't as aware of other implications are the rest of us are.

Allowing the user to change it right off the bat will also allow unsolicited applications to do the same, don't you understand?

I don't understand that too. What unsolicited apps would bother tinkering with resolution? Besides, the utility is password protected, same as the rest of admin apps.

> Why is it so hard for you to understand the complicated areas of OS development?

That's because these areas are complicated, as you've kindly mentioned.:lolflag:

---

### Post by SuperSonic4 on 2008-09-25
The exact same thing happens in windows too, only there it's much harder to get the nvidia driver installed

---

### Post by fourthofjuly on 2008-09-25
> **TheZorch said:**
> This isn't really a request for help but an attempt to shed light on a serious flaw in Ubuntu 8.04 that needs to be addressed because it is preventing new users form adopting the OS.

This has to do with the problem of using being locked at a screen resolution of 640x480.  Ok, doesn't sound like a big issue to most of you but in reality this is a rather serious problem.  We want Ubuntu to be taken seriously in the mainstream.  This problem threatens that in a very big way.

Normally during the install Ubuntu probes hardware to get information from them in order to determine which drives need to installed or downloaded and installed.  Many times Ubuntu is unable to determine what kind of monitor people are using and the OS falls back on a default monitor setting.  This locks people at a safe resolution of 640x480.

In Ubuntu 7.10 the screen resolution applet allow users to choose what kind of monitor they have.  This was replaced in Ubuntu 8.04 with a screen resolution applet that doesn't let you do this.  Kubuntu 8.04 KDE4 Remix has the same problem.  Users can't change their monitor settings from within X.org.  They're forced to come to this forum and other places to find a solution.

The problem is many people are hearing about how user friendly Ubuntu is, so many people who are computer novices are getting interested in the OS.  They're all familiar with Windows.  When they experience this problem and run into this issue and see what they need to do to fix they're turned off by the fact that they need to all this stuff just to fix a very simple problem.  It making people who would normally give Ubuntu serious consideration a very bad impression and they write off the OS without giving it a fair chance.

Just one simple feature, to be able to change your monitor settings, is having this kind of major affect.  Its often the little things that really have the biggest impact.

We need to let the Development Community responsible for maintaining Ubuntu that this is a serious problem that needs to be address and not ignored.
i guess the developer community addresses such a wide range of issues that certain things will have to be left for the user...!!! and editing your main menu should not be so difficult...

i really don't know but, how many of windows users can actually install the drivers from the driver CDs on their own?

isn't it for the support guy to manage the screen resolution issue?

---

### Post by mbeach on 2008-09-25
exactly.  install xp and you may not have your display adapter drivers, your sound card drivers, nic drivers etc.  In my case I've always wiped a pre-installed xp clean and started fresh, but quite often without the driver disk that accompanies the new purchase, obtaining those drivers can be quite difficult.  

The solution?  Buy the computer with Ubuntu pre-installed.

---

### Post by fourthofjuly on 2008-09-25
[SIZE="3"]& how often do we change screen resolutions?[/SIZE]

---

### Post by mikewhatever on 2008-09-25
> **fourthofjuly said:**
> i guess the developer community addresses such a wide range of issues that certain things will have to be left for the user...!!! and editing your main menu should not be so difficult...

i really don't know but, how many of windows users can actually install the drivers from the driver CDs on their own?

isn't it for the support guy to manage the screen resolution issue?

> **mbeach said:**
> exactly.  install xp and you may not have your display adapter drivers, your sound card drivers, nic drivers etc.  In my case I've always wiped a pre-installed xp clean and started fresh, but quite often without the driver disk that accompanies the new purchase, obtaining those drivers can be quite difficult.  

The solution?  Buy the computer with Ubuntu pre-installed.


I think it's nice to have a gui tool for configuring resolution, no matter what it's like in Windows. Displayconfig tool was a step in that direction, and I've no idea why it got hidden in Hardy. I think it wasn't in Gutsy, and lived under Preferences .
No matter how you turn it, it's advisable to have that tool available, because, while editing the menu is easy, you have to know it's there in the first place, and new users don't.
Buying Ubuntu pre-installed and pre-configured is the best option, but not every one lives in North America or Western Europe. Ubuntu pre-installed is not available in most countries, and where I live, you are lucky enough to get compatible hardware that can run Ubuntu, without having to buy Windows.

---

### Post by phidia on 2008-09-25
> **mikewhatever said:**
> I think it's nice to have a gui tool for configuring resolution, no matter what it's like in Windows. Displayconfig tool was a step in that direction, and I've no idea why it got hidden in Hardy. I think it wasn't in Gutsy, and lived under Preferences .
No matter how you turn it, it's advisable to have that tool available, because, while editing the menu is easy, you have to know it's there in the first place, and new users don't.
Buying Ubuntu pre-installed and pre-configured is the best option, but not every one lives in North America or Western Europe. Ubuntu pre-installed is not available in most countries, and where I live, you are lucky enough to get compatible hardware that can run Ubuntu, without having to buy Windows.
 
I agree-we shouldn't be comparing Ubuntu to windows and particularly to window's shortcomings. However since this isn't a request for help it is misplaced and belongs in the community cafe and/or launchpad.

For whatever reasons 8.04 seems to have had some big hiccups and it's a matter of opinion how much of a negative effect some of those have been. 

I'm happy to report that intrepid does resolve some of those-IMO.

---

