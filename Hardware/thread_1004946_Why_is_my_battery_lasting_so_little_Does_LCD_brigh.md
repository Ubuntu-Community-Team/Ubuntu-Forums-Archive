---
title: "Why is my battery lasting so little? Does LCD brightness make much difference?"
date: 2008-12-07
forum: Hardware
---

### Post by SlaughterDog on 2008-12-07
I recently bought an Acer Aspire One and loaded Ubuntu onto it. It's my first portable computer.

Acer says the 3 cell battery should last for 2.5 hours, but mine is only lasting for 1.6 hours. I run the screen at full brightness, do you really think that makes that much difference? I am trying it at dim right now but it doesn't seem to be making it last much longer. 

What do you think might be the problem? The fan is constantly on, and I'll try the fix for that, but would that really drain the battery that much?

---

### Post by 2hot6ft2 on 2008-12-07
They always say they last longer than they really do in real life. If you use an optical mouse it will drain it faster, screen brightness sure a light that shines twice as bright shines half as long using the same power or something like that.

Heavy graphic intensive use, there are some things that run in the background that will put a drain on a battery. There are lots of reasons. Using the dvd drive it takes power to spin it right.

powertop might help. Get it from synaptic if it's not already installed.

---

### Post by 2hot6ft2 on 2008-12-07
You may find this helpful it explains various services that run at start up and whether or not it's safe to turn some of them off or not. It's actually a guide for tweaking the system for performance but the fewer things running the longer the battery will last.
[http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html)

And if the fan is on it's probably because it's hot. Make sure you're not covering the vents. Like laying it on your legs and covering them.

---

### Post by SlaughterDog on 2008-12-07
> **2hot6ft2 said:**
> They always say they last longer than they really do in real life. If you use an optical mouse it will drain it faster, screen brightness sure a light that shines twice as bright shines half as long using the same power or something like that.

Heavy graphic intensive use, there are some things that run in the background that will put a drain on a battery. There are lots of reasons. Using the dvd drive it takes power to spin it right.

powertop might help. Get it from synaptic if it's not already installed.There is no optical drive. I've not got very much running on it either, though I do have the special effects turned up.

> **2hot6ft2 said:**
> You may find this helpful it explains various services that run at start up and whether or not it's safe to turn some of them off or not. It's actually a guide for tweaking the system for performance but the fewer things running the longer the battery will last.
[http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html)

And if the fan is on it's probably because it's hot. Make sure you're not covering the vents. Like laying it on your legs and covering them.

There is a guide for this netbook that says it runs all the time until you install a fix for it. I'll do that as soon as I can update the bios, which is required for the fix.

---

### Post by Ayuthia on 2008-12-07
> **SlaughterDog said:**
> There is no optical drive. I've not got very much running on it either, though I do have the special effects turned up.

Having the special effects will most likely use up some of your battery since it is graphics intensive.  It would cause my laptop to run warmer which would make my fan run more.

---

### Post by blackened on 2008-12-07
> **SlaughterDog said:**
> There is a guide for this netbook that says it runs all the time until you install a fix for it. I'll do that as soon as I can update the bios, which is required for the fix.

I seriously doubt that having desktop effects enabled is making much difference in your battery life. The two biggest things killing you right now are going to be the fan constantly running and the screen brightness while on battery.

Also, as previously mentioned, you should install powertop (run it as superuser) to audit what's having the largest impact on power consumption.

There is a power management script at [http://ubuntuforums.org/showthread.php?t=988309]("http://ubuntuforums.org/showthread.php?t=988309") that incorporates alot of suggestions from powertop to increase battery life. 


First things first though, fix the fan and reduce the brightness and you should see a significant difference.

---

### Post by RookieUbuntuUser58 on 2008-12-07
Ive noticed the same thing with my 6 cell Wind. My battery life is rated at 6 hrs, which I wasn't expecting at all. Before installing Ubuntu (dual boot) I was getting a solid 4hrs and 30mins + with backlight all the way down and heavy internet use. Now with the dual boot and same settings Im getting 3hrs and 30mins at most, even with power savings tips (tried them all here).

---

### Post by SlaughterDog on 2008-12-12
I've turned the brightness down but it hasn't really made a difference at all. It's an 8 inch screen so there's not much to light anyway.

I've installed powertop, so now how do I run and use that?

---

