---
title: "Ubuntu and tablets"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by malfist on 2007-09-11
I just bought Gateway's CX190 (I think 190) convertible laptop. I was wondering how well it did with ubuntu. I abhor vista, and would rather not use XP but I want to keep the advantages of a tablet with the screen rotation and wacom pen usage.

Does anyone have any experiences with it?

---

### Post by frith on 2007-09-12
Well, I am running Ubuntu on my toshiba m200 tablet. It was a pain to install, but it picks up everything okay. I might suggest you check out [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam) to see what works and doesn't, but here are my experiences:

Straight after installing, it picked up the stylus.

After a bit of messing around I got screen rotation to work, but I have not yet invested the time to get the stylus to rotate when the screen is rotated. I'm pretty confident its possible though.

Usign dual monitors is a total PITA. This feature works okay sometimes and in some cases (it seems to work better using the nvidia binary drivers and TwinView), but its not great. It is usable - in my case you must have the monitor plugged in when you turn on the laptop, then it will divert everything to the external screen. But I fried my KVM switch by hot plugging the monitor, and once the computer is on I couldn't find a good way of diverting the display. For me this is only really an issue when I want to use a projector (projector must be plugged in before turning on laptop, can't see laptop screen and projector at the same time). This is an area that is seeing a lot of attention it seems, so I don't think it should be a show-stopper.

Something has happened and I don't know what it is, now the stylus doesn't work. I have posted here and done a lot of googling, but no one seems to be able to help me yet. The problem is described here:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/66646](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/66646) I'm still hoping there is someone knowledgeable on these forums who can weigh in on the issue... And its possible its specific to my laptop - otherwise there would be a flood of questions and answers on the issue.

Suspend is dodgy at best - suspend to disk works okay after a few (very simple) tweaks. Suspend to ram doesn't work. But it 'almost' works, so maybe it will work proper soon.

Out of the box there was no support for cpu scaling resulting in short battery life. A simple install of a package (sudo apt-get install toshutils) fixed that problem. There are other packages that also do the same thing more generically (ACPI etc.)

Software doesn't integrate as well - its a bit more challenging (although not impossible) to do easy tasks like sending files via IR to my phone/PDA or Bluetooth. The support is there, but its not as simple as 'right click, send to phone'.

Those are the problems. Here are the good things for me:

Windows XP - minimum 5 min and 5% battery to start up. Plus at least another minute for wireless.
Ubuntu - Less than 1 min and connects to the wireless network in that time too.

Never seems to crash. Everything is a bit faster. I feel like I can do *anything* I want with the OS if I'm prepared to learn how.

Being designed by hard-core programmers etc, There is always a shortcut to accomplishing almost any task, and always a tool that will change almost anything in almost any fashion. With great power comes great responsibility though :)

All in all, I still dual boot (for Flash authoring mainly), but I am very attached to Ubuntu now - getting it installed gave me a real sense of accomplishment, and everytime I find a new way to bend it to my will I feel a little more in control of my PC. YMMV though. But its definitely faster at some things...

Oh, and if you like the handwriting recognition stuff (I never really used it) then don't even bother with Ubuntu or Linux just yet - Microsoft has spent a lot of time and money on handwriting recognition software and it really shows. I expect Linux to catch up, but not this year...

Hope that gives you some food for thought.

Frith.

---

### Post by malfist on 2007-09-12
I think I'll test with a dual boot and see how it works. Can I still do the handwriting stuff with it on linux?

---

### Post by frith on 2007-09-12
Hmm... I'm not exactly sure what you mean. In linux, you can use the stylus for various things (navigating, drawing, taking notes, etc.) and there is software that does handwriting recognition under linux, its just not as good as the inbuilt support for winXP.

I think dual boot is a good way to go - you get the best of both worlds that way :) I have found that now I have Ubuntu installed, its so painful to wait for windows to start up.

---

