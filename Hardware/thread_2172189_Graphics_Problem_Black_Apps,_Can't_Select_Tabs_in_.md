---
title: "Graphics Problem: Black Apps, Can't Select Tabs in Chrome, etc."
date: 2013-09-03
forum: Hardware
---

### Post by wyth on 2013-09-03
**Proviso:** I'm not assuming I'm posting this in the right forum (Hardware), nor that anyone has the answer. I'm mostly hoping to narrow down the issue so I can' find a solution.

**Issue:** There is a problem with one desktop installation with nvidia GeForce 8600 GT graphics card. Apps raised out of the Unity launcher will be blacked out -- everything within the border of the app is black -- until I either minimize it and raise it again, or maximize the app. 

Similarly, Chrome becomes unresponsive until I do the same thing -- minimize to the launcher and raise it again, or maximize the app. It happens more often with Chrome/Chromium and usually makes itself known when I try to open a link in a new tab and it looks like nothing has happened. So I click again, and again and again, then minimize/maximize, and the same link is now present in four new tabs (because I tried opening it four times with no result). I'm not certain if this also happens in Firefox, simply because I haven't used Firefox enough on this machine to rule it out.

This usually happens when coming out of an inactive screen state, but not always -- it can happen after using an application for 3 minutes, or after 3 hours. But it happens regularly.

I don't know if this is related to the graphics card or not. I've never had an issue with the card before, and it's only started happening since 12.04, but has been happening more regularly since then. I'm currently using the nvidia-310 driver, but have had the same results with nvidia-310-updates, nvidia-313-updates, and the nouveau driver (which doesn't seem to work well anyway -- can't get the right resolution with nouveau). I'm not having any other graphics-related issues -- the card works beautifully -- so I'm not certain it's necessarily a gfx card issue.

**So:** Has anyone encountered something like this? If so did you have any luck addressing the problem, or tracking down its source?

**Edit: **Crap. Minutes after I post this question -- after weeks of randomly poking around -- I find [an actual bug report]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1072206") that seems related. I'll let the question stand in case someone has a good response.

**Another Edit:** If anyone else is experiencing this issue, try disabling Animations in CCSM (compiz config settings manager). That seems to be one work-around.

(Not sure if I should marked this as "solved" or not, since it's just a work-around that I'm now posting for others to use if they need it; the actual issue -- most likely with compiz -- is not solved.)

**Yet Another Edit:** Yeah, those fixes I noted above? They don't work. I just spent 30 minutes digging up some photos of the Isle of Staffa, and had to minimize-maximize to see every tab for every image. The number of the images were in the double-digits, and that got old, fast. I tried using Firefox for a few days, and it doesn't have the *same* problems, but it has problems nonetheless; it can really gag on YouTube.

---

### Post by scido2 on 2014-02-16
Hi wyth,

I'm writing here 'casue I've got the same issue as you have, first time in ubuntu 13.10 (no issue like this in previous versions). I've got an old laptop (Dell M65) with a Nvidia Quadro FX 350M. I thought it was a problem with my legacy nvidia driver (I can only use the 304), but your post changed my mind. I've made a video to show the problem, everybody can watch here: [URL="http://youtu.be/5_R055Tt__Y"]http://youtu.be/5_R055Tt__Y 
[/URL]Someone on the web pointed out the same problem, like here: [http://bit.ly/1bvlMEX](http://bit.ly/1bvlMEX). He said the cause is about the xcompmgr, but I think it did't apply to ubuntu/unity (or not?).

So, can someone help us to resolve the problem? has anyone else the same issue? Any idea?

Thank you,
Scido

---

### Post by wyth on 2014-02-20
I don't think it's anything to do with xcompmgr -- that's a lightweight compositing manager that you can use in place of compiz (I don't even have it installed).

So you're using Chromium; I've had the same issue on Chrome-beta and Chrome-stable, so it's clearly something in the Chrome family. I don't have any answers yet, and it still happens (I've just gotten used to it). I'm guessing either compiz is having an issue with Chrome, or unity is, or it's some combination thereof.

For what it's worth, [the bug report identifies it as a compiz issue]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1072206"), and one that's still not been addressed.

---

### Post by soum_axetuirk on 2014-02-20
install graphics driver

---

### Post by wyth on 2014-02-20
> **soum_axetuirk said:**
> install graphics driver

Yeah, that's installed.

---

### Post by scido2 on 2014-02-27
It's definitely a GPU hardware acceleration issue. I tried to disable the option in chromium (settings->advanced settings->uncheck "Use hardware acceleration when available") and everything is ok. Already using last Nvidia driver (304.119), but nothing changes. Waiting for a compiz update...

---

### Post by wyth on 2014-05-29
> **scido2 said:**
> It's definitely a GPU hardware acceleration issue. I tried to disable the option in chromium (settings->advanced settings->uncheck "Use hardware acceleration when available") and everything is ok. Already using last Nvidia driver (304.119), but nothing changes. Waiting for a compiz update...

I turned off hardware acceleration with some success, but not total. It's also happened a couple times with Firefox. Since the latest Chrome was released with the Aurora interface, I tried re-enabling hardware acceleration, and that seems to make it more stable than it was with it off. Still, it shouldn't be happening at all.

The things that seems consistent are: It happens more often if I go to YouTube, especially if I open more than one YouTube tab; it's more likely to happen if I have more than five tabs open in a browser; it's more likely to happen on the Google Images page; and it's likely to happen with Gmail, but not as much as with YouTube or Google Images. 

Which blows my mind, because you'd think Google's own browser should be able to properly browse their own properties without crashing an entire operating system.

Three questions:

[LIST=1]
[*]If this is a compiz thing, I'd love to know where the issue is.
[*]These problems didn't start happening until maybe the second distro released with the unity interface. So at first I thought it was something to do with unity, but I haven't been able to track any of that, either. It used to be a lot easier to check the logs and see what may have caused a crash, but since unity came along, I haven't found anything in those logs. (Tips?)
[*]Is there something about the way Unity utilizes compiz that could be causing an issue when a browser is open?
[/LIST]

Gah, this is annoying. At least with my laptop, for more than a year now, I average about six hard lock-ups a week, sometimes multiple lock-ups a day. The only reason I haven't switched to something else yet is because of inertia and I tend to prefer unity over the new gnome interface. 

Still, I'm looking elsewhere more and more often.

---

