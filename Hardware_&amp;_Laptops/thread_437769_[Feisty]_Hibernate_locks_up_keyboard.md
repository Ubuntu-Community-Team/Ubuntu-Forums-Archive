---
title: "[Feisty] Hibernate locks up keyboard"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by Stefan Björk on 2007-05-09
Hibernate only works occasionally. When it does not, the screen is locked and the keyboard does not work at all. The only thing to to is to power off or reboot (using Ctrl-Alt-SysRq-B). There is a bug filed on this ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/100087](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/100087)), but I wonder if there is anyone else experiencing this problem, if there is any solution or what I can do to track this problem myself?

Stefan

---

### Post by whayong on 2007-05-09
Are you sure it's hibernate cause the keyboard lock up?  My laptop was doing the same thing when I did a few "tweaks."  I found out it was the "sleep" function under power management cause my keyboard to stop functioning.  Actually, my wireless card was also affected.  Go to your power management and check your settings, make sure you have "sleep" set to "never."

Hope that helps........

---

### Post by spier on 2007-05-09
Is it a usb keyboard? There may be issues in unmounting/mounting usb devices in suspend/wakeup scripts

---

### Post by Stefan Björk on 2007-05-09
It is no USB keyboard. Actually, the only thing that works is the USB mouse.

Also, the computer never hibernates. All that happens is that the screen locks (xlock) and keyboard locks up completely. Log files indicate that hibernation failed, but for no particular reason.

Stefan

---

### Post by jjordan on 2007-05-10
Hmm... Little confused, hibernate usually requires you to press the power button to come out of hibernation, the keyboard does nothing.  Are we talking about "suspend" or "hibernate?"

A common problem with hibernate is having a swap partition that is too small.  Your swap partition must be large enough for everything in RAM to be written to it plus anything that was already there.

Check to make sure your swap partition is working and large enough.

In the terminal type:
**swapon -s**

to see your swap device(s) and usage.

-j

---

### Post by Stefan Björk on 2007-05-10
Ok, I'll try to make things as clear as possible:

Hibernation - either selected from the power-button drop-down menu, or automatically by closing the lid (I have configured Ubuntu to do so) - only works occasionally. When it works, the laptop hibernates as expected. When it does not work, something fails along the process and the keyboard ends up locked (that is, nothing except Ctrl-Alt-SysRq-B is recoqnized, which probably indicates that Linux knows about the keyboard, but X11 does not).

See [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/100087](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/100087), especially the log entries. Something fails during hibernate, but I don't know what, and I don't know why it sometimes work, sometimes not.

Stefan

---

### Post by Stefan Björk on 2007-05-10
I should mention that hibernation worked without problems in Edgy. Something has changed when I upgraded to Feisty.

There is also another behaviour that has changed: With Feisty, the laptop sometimes starts up when opening the lid. This happens even if the computer is shut down, not only hibernated.

Stefan

---

### Post by afaflix on 2007-05-13
while not a keyboard lockup I have following issue with hibernation .. or simply folding up my laptop.

If I fold up my laptop while the power is plugged in, I have no issues.
If I fold up a laptop while on battery power, I open up a shut down computer. When I try to restart the computer I get "kernel panic" errors and not much is happening.
As it happened the first time I thought I'd have to re-install, but once I had the power plugged in again, it started up and acted as if nothing has happened. 
I then passworded my screensaver and sure enough, if I tried it again, on powered up re-boot after a kernel panic, it tries to resume my session and ask for my password .. it crashes again, but the following startup is clean.

I run 7.04 on a Dell XPS.

cheers

---

### Post by insibato on 2007-05-14
Confirmed: I also have this problem on a TravelMate 290 laptop. Instead of sleeping, it will display the screensaver and completely disable the keyboard (sysreq's still work though).

It worked fine under Edgy. What changed in Feisty?

---

### Post by Stefan Björk on 2007-05-14
Don't know. New kernel?

Installing the 'hibernate' package and hibernate using 'sudo hibernate' works for me. However, the computer still has the bad habit of powering up on closing the lid...

Stefan

---

### Post by ariel on 2007-05-16
I'm also having the exact same problem, but in my case it occurs after a Suspend 2 RAM as well...

No solution yet I guess? :(

I have a dell latitude d820 running feisty

---

### Post by insibato on 2007-07-08
It would appear that it may be somehow linked to the wireless networking stuff (wifi). When I am using the wifi, the laptop is never able to sleep. When the wifi is disabled (hardware switch) and I am using the ethernet network, sleep works fine. Bug is still present in 2.6.20-16-generic.

---

