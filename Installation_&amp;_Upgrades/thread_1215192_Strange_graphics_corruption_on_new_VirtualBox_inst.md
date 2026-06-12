---
title: "Strange graphics corruption on new VirtualBox install"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by cpressland on 2009-07-16
Hey guys,

Long story short, I use Windows 7 for most of my work but my girlfriend prefers Ubuntu, so I decided to setup a Virtual Machine of Ubuntu for her so she could do all her Facebook and Pidgin tasks while not interrupting any of my work flow (don't you just hate it when somebody minimises everything).

So anyway, I used a Net Install image as I like to make sure everything is nice and up-to-date after a clean install, after the install I installed the VirtualBox 'Guest Additions' in terminal the usual way and then doublechecked everything was up-to-date, installed a few apps, etc etc etc.

After a reboot I noticed that the image displayed was garbled, and not the prettiest thing in the world. Now, I'm the first person in the room to protest about how bad X11 is but alas we do what we can with it.

If I resize my VirtualBox Window then the corruption fixes itself, same applies for if I fullscreen it.

I was basically just wondering if anyone had run into anything like this in the past and knew how to fix it, and if not, had any theory's on fixing it. I can clone the VirtualMachine so it's hardly a problem if something goes horribly wrong.

Anyway, See attachment.

Thanks Guys

cpressland

---

### Post by starcraft.man on 2009-07-16
A weird problem, I've been running vbox for a long while and I don't think I've run across this. A few things pop into head.

First, install the latest version for win 7 please. They just released 3.0 .

Second, I see that this only happened after you installed the additions and rebooted (i.e. began using the drivers). Maybe some error occurred but didn't report. I assume you installed the build-essential package and then used the Devices > Guest install additions and ran the script.

One thing I could think of, is if your using the closed source version for Windows and you installed the OSE guest additions from the repo, maybe it wouldn't work exactly right.

I can't think of much else that'd give trouble. My Ubuntu guest installed to VBox 3.0 on Vista works without any such glitch. Maybe go to the preferences of the VM and tinker with the graphical settings? Enable and disable acceleration, increase graphics ram... tinker!

When in doubt, I'd do a clean install and then make a copy. Then apply all updates and build essential and everything but the drivers and reboot. You can snapshot then in this clean state and try to install the additions again, see if it repeats.

Edit: If all else fails, you might be better served by the [VBox forums.]("http://forums.virtualbox.org/") Maybe this is a bug with 7?

---

