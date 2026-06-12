---
title: "machine is dieing need to plan a rescue"
date: 2015-03-02
forum: Hardware
---

### Post by bryan37 on 2015-03-02
I run ubuntu 14.04 lts on a 5 year old quad core machine. It's a wonderful machine but it's dieing. A couple of months ago the hard drive went taking everything with it. I rebuilt a lot of my data, but now it is locking up on a regular basis. It was a great machine, but it's time to go to the great recycling bin in the sky. I need to plan my transition to a new hardware system. Unfortunately, I'm a user with very little understanding of the ubuntu hardware and software requirements. Is there a proper place to ask these sorts of questions?

Basically what I use my ubuntu system for is 2D graphics in gimp, email, and web browsing. I often have several gigs of graphics open at one time in gimp so I am looking at a powerful machine. Are there any constraints on the maximum number of cores or gigs of ram I can use with ubuntu 14.04? Does gimp need a big graphics card or does it do graphics processing through the processor? Where do I find my browser favourites and my email address book and how do I transfer them to the new machine? Thanks in advance for your time and help.

---

### Post by weatherman2 on 2015-03-02
It's hard to know what you mean by "dying" and "locking up."  Depending on your needs, a quad core 5 year old computer isn't necessarily that old.  A healthy 5 year old computer doesn't start locking up because it's "old."  Something is wrong with it.  Could be a lot of things but maybe not something expensive to fix.  If the CPU fan isn't working or the CPU heat sink is dirty and just needs to be cleaned, it could be a cheap fix.    

Is there a new hard drive?  Is it healthy?  If so, you can probably just move it straight to another system and boot and you are done.  If the hard drive you are now using isn't healthy, it's important to get one that is and transfer you data (again) as soon as possible.  With a good hard drive, you can move it into another system.

For GIMP, mostly you care about RAM and CPU, not about the graphics card .  More advanced edits uses more CPU power, but very large image files (and a number of them open at once) use RAM, so the more RAM you can get, the better.

---

### Post by bryan37 on 2015-03-03
Thanks for the info. My apologies for my lack of technical knowledge and language. The machine is plenty fast enough when it works. It's just that every hour or so of operation the screen just freezes. Neither the mouse nor keyboard get any response on the screen. It just sits there and I can not interact with whatever I was working on. I can see it, but I can not manipulate it. So I have to shut the power off and then start it up again. It was cleaned out just before Christmas when the hard drive was replaced, but I will dust it out again just to be sure. BTW, is there a maximum amount of ram gimp can use? Thanks again for your help.

---

### Post by weatherman2 on 2015-03-03
I don't know the maximum amount of RAM Gimp can use - I'd have to look it up.

Without more direct knowledge of your machine, I'd have to ask you a lot of questions about it.  The "locking up" could be a lot of things.  Some random things that come to mind:

- CPU overheating: because of dirty/clogged CPU heat sink, CPU fan not spinning or not properly, etc.
- poor case ventilation.  Is there a case fan running inside besides the CPU fan?
- failing power supply
- bad RAM.  You can run Memtest by rebooting and choosing Memtest from the Grub boot menu. If you normally don't get a Grub boot menu, you can hold down the Shift key to get a menu while you are rebooting
- failing motherboard
- failing hard drive.  You can test the hard drive's S.M.A.R.T. status with GSmartControl in Ubuntu.  Check the Attributes, look for any that are pink or red.  Even a new hard drive could be failing.
- software/drive issue of some sort (a whole different aspect, could be a million things)

---

### Post by houstonbofh on 2015-03-03
Two points...

I have systems well over 5 years old running well.  You should look into your hardware failing, or you may be repeating this very soon.  Memtest overnight is a good start.  It is a memory tester, but it also works the CPU and power supply a bit.  My thoughts based on your symptoms would be memory or Power supply.

As for system, the limits are well beyond what you need.  I have installed Ubuntu on a Dual CPU (each 8 core hyper threaded, so seen as 32 cores) system with 256 gig or ram.  I have 24 gig in my current desktop because that was the most you could get in a desktop at the time. (2010)

---

