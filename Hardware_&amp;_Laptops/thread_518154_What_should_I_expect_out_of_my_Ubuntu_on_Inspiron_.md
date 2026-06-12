---
title: "What should I expect out of my Ubuntu on Inspiron 1100?"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by hunt.topher on 2007-08-05
I have a four-year-old Inspiron 1100 - not top of the line, but I want it that way. I want to demonstrate - to myself and to others - that Linux can run more full-featured, as fast, and more reliably than XP, without needing a supercomputer like Vista does.

My problem is, I'm actually a bit disappointed in some aspects of my Ubuntu's performance.

I'm dual-booting XP and Xubuntu. I tried Ubuntu with GNOME and while it worked OK (even got Beryl running), everyday tasks (like surfing, word processing) were unbearably sluggish compared to my highly-tweaked XP install. That's my problem: I know how to tweak XP pretty well, and I don't have enough experience with Linux to know how to improve my performance.

So now I'm using Xubuntu. I got through some initial frustrations (touchpad disabling, autoconfig network, video resolution, finding an alternative to Nvu, music converting) by experimenting and referring to the massive Ubuntu support community, smoothly enough to keep my spirits up.

But there are still two things that really bug me - mainly based on principle: because I know that XP performs better in these things on the same machine, and because I can't help feeling like other Ubuntu users with similar hardware are also having a much better experience - and I can't figure out what I'm doing wrong!

1) Firefox is extremely slow on some pages - like Google Page Creator, Google Docs, and (especially) Google Notebook. I use the entire "Google suite" so I won't just "work around" this issue! When I reboot into Windows on the same computer, comparable "heavy" pages zip along. Same hardware! When I disable all of my Firefox extensions, it's a bit better... but I kind of don't want to get rid of my extensions just to work on my webpages. I had hoped it was just my slow wireless connection; no such luck.

2) 3D is a joke on this system. My gaming world is restricted to Pingus and NeverBall. The more complex screensavers preloaded with Xubuntu will nearly freeze up my system, Xfce's built-in desktop effects slow to a crawl after five minutes of use, and my foray into more graphical games (Podman Balazar, even LinCity) came to a very sad end. And yet XP has run Zanzarah, Black & White, and even Entropia surprisingly well!

I have an Inspiron 1100 with 2GHz processor, 512 MB RAM and an Intel 82845G graphics card.  I've considered the possibility that I don't have the Intel graphics driver properly installed - but everything I have read indicates that this line of graphics drivers are auto-included with the system. I've also considered that maybe the Linux driver for this graphics card isn't up to snuff with the Windows driver - but by this point I'm in over my head; after all, I'm still a Linux newbie.

So can anyone suggest anything? I've read comments from other Inspiron 1100 Ubuntu users that indicated that they were very happy with their system's performance. Can anyone point-blank tell me, from direct experience, that their Ubuntu runs faster and smoother on their computer than XP did on the same? Am I being unreasonable in expecting Ubuntu to perform as responsively as XP did? Does anyone have pointers about what I might try, or if you need extra info (if it means using the terminal, please mention the commands I'll need), ... any help would be appreciated. Thanks!

 - Topher Hunt
Inspiron 1100, 2GHz, Intel Extreme Graphics 82845G, 512MB Ram
Xubuntu Feisty dual-boot w/ XP, hoping to get rid of XP ASAP but not entirely happy with Ubuntu so far...

---

### Post by tgm4883 on 2007-08-05
do this in terminal, post the result

glxinfo | grep direct

---

### Post by hunt.topher on 2007-08-05
topher@thannus:~$ glxinfo | grep direct
direct rendering: Yes

That means that the 3D graphics are "working as they should be", right? That's what I was afraid of - because the gaming performance I've tried doesn't come close to what I could do in XP. Is that because of DirectX versus OpenGL? I don't really know much about graphics rendering.

---

### Post by tgm4883 on 2007-08-05
sorry, can you do this too

glxinfo | grep OpenGL

---

### Post by hunt.topher on 2007-08-05
topher@thannus:~$ glxinfo |grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:

Thanks for the guidance... I don't mind command line but I definitely wouldn't be wading through this info on my own.

---

### Post by avik on 2007-08-05
Okay, so you're using the mesa drivers,which don't have 3D acceleration.  You'll need the appropriate drivers, but unfortunately, I don't know which ones they are.

---

### Post by tgm4883 on 2007-08-05
> **avik said:**
> Okay, so you're using the mesa drivers,which don't have 3D acceleration.  You'll need the appropriate drivers, but unfortunately, I don't know which ones they are.

Yea, i'm thinking thats not the issue.  My Inspiron E1505 has an intel 945 and runs the MESA also.  3D works fine on mine.

---

### Post by hunt.topher on 2007-08-05
> **avik said:**
> Okay, so you're using the mesa drivers,which don't have 3D acceleration.  You'll need the appropriate drivers, but unfortunately, I don't know which ones they are.

I just want to say - if this is the reason my performance sucks sometimes, I'll be satisfied just knowing that Linux can do more. I just can't stand the constant feeling that I would be *more productive if I were still using Windows* in some ways.

Does that mean that I am **not** using the [Intel-supported]("http://support.intel.com/support/graphics/sb/CS-010512.htm") drivers? Is there a way I can find out what 3D driver works with my system? I'm registered on the Ubuntu device database as 8498230d2008b932c59cdaa470713ce5 if that helps. Man, I'd really love to see this old machine revived, that would make my year.

From what I understand, if I'm not using the Intel drivers, I can just download, compile, and plug them in, right? Or am I being naive? ;-)

Thanks for the responses so far, guys.

---

