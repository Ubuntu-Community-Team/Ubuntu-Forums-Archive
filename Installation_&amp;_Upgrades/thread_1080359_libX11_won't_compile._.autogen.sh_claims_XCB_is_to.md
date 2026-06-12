---
title: "libX11 won't compile. ./autogen.sh claims XCB is too old but it isn't. PLEASE HELP!!!"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by Neo_The_User on 2009-02-25
I spent 2 days trying to compile libX11 from git and I solved many tool chain issues but this time things are different. I am using Ubuntu 8.10 (with a few 9.04 packages to help me compile) and I keep running into this issue.

Requested 'xcb >= 1.1.92' but version of XCB is 1.1

I installed these 2 packages as well:

[http://packages.ubuntu.com/jaunty/libx11-xcb-dev](http://packages.ubuntu.com/jaunty/libx11-xcb-dev)

[http://packages.ubuntu.com/jaunty/libx11-xcb1](http://packages.ubuntu.com/jaunty/libx11-xcb1)

I also compiled and installed libxcb1.2 from git but it still didn't work.

Please help me. Thank you so much in advance.

I know this isn't the "Ubuntu way" but ubuntu doesn't use the versions of everything I want so I HAVE to do it against the ubuntu way.

---

### Post by Neo_The_User on 2009-02-25
bump

I have helped people out on the ubuntu forums. I do not ask things all the time. If somebody would please help me, I would make a guide on installing xserver, xorg, and all those goodies for ubuntu all cloned from git. Want that? well I need libX11 to be solved first.

....Thanks in advance for helping me (if anybody will)

---

### Post by Neo_The_User on 2009-02-26
OK if you do not know the answer, can you direct me to somebody who just might be able to help me?

---

### Post by kerry_s on 2009-02-26
i guess not to many people find the need to compile. :lolflag:

you just want a different version? is there something wrong with the X you have?

---

### Post by Neo_The_User on 2009-02-26
Not exactly. I just like building X from git to get everything really bleeding edge. I'm trying to make a guide for compiling X from source for Ubuntu 8.10+ but I don't have the necessary help to accomplish that. I'm not just doing this for myself. But for anybody who wants to have the latest versions of Xserver, Xorg, and X11.

---

### Post by kerry_s on 2009-02-26
> **Neo_The_User said:**
> Not exactly. I just like building X from git to get everything really bleeding edge. I'm trying to make a guide for compiling X from source for Ubuntu 8.10+ but I don't have the necessary help to accomplish that. I'm not just doing this for myself. But for anybody who wants to have the latest versions of Xserver, Xorg, and X11.

well ubuntu is built on debian sid, so if you grab those sources they should be compatible. its a huge job, so head on over to debian sid and do some searching and downloading, the source link is on the right in the blue area.
example:
[http://packages.debian.org/sid/xorg](http://packages.debian.org/sid/xorg)

the 1's in red are the depends that you'll also need. good luck!

---

### Post by Neo_The_User on 2009-02-27
Those apps are older than the ubuntu 8.10 apps. Experiment seems to have later packages. I don't think people would like to use the debian packages to build LibX11 from source though. I just need the magic combination of git clone repos and my ./configure error is solved. ...I think. btw thanks for your replies. Glad somebody out there cares. The XCB libraries aren't in the debian repos. heh this is going to be difficult. When 9.04 becomes stable, I'll be able to do all this stuff and release ".deb" packages for Ubuntu users. I can't wait until April then I can start commiting and contributing to the 9.04 project (bit late for 8.10 now) so you'll see lots of packages built by me related to X11, DRI, and Mesa really soon. ;)

---

