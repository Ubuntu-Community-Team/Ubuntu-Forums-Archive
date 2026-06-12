---
title: "Turn old Laptop into a Desktop"
date: 2011-02-03
forum: Hardware
---

### Post by Madonkadonk on 2011-02-03
Hi, I have an old HP Pavilion dv2000 with a broken monitor and ubuntu installed. I don't want to get rid of the thing and I don't want to buy a new screen for it, so I want to turn it into a desktop computer, only problem, i don't know how to do this. I want it to run while it is shut and to use the external monitor as the only monitor, I also want these settings to save if I have to turn it off and if I open the laptop, I don't want the screen to turn on at all, is this at all possible, and I know this seems like a lot to ask at once, but it seemed better than making a bunch of different threads ;)
Thank you in advanced.

---

### Post by dabl on 2011-02-03
That's just a notebook, but it does have a 1.8GHz CPU, so it could do some reasonable desktop work, if you had the memory and the drive capacity.  Does it still have the stock 1GB memory?  What kind of "desktop" are you envisioning, in terms of work capability?

It seems to me the biggest challenges are not the monitor, but instead are:

(a) puny GPU
(b) puny HDD and no external SATA or firewire connectivity
(c) needs a memory upgrade to do any serious desktop work

So, it looks like a tough problem, to me -- it's not designed to take a serious graphic card, and the only effective way to add drive capacity would to put a SATA hdd into an external enclosure, with power, and then cut a hole in the case to run a SATA cable inside to the port connector.  You could use a USB keyboard and USB mouse, so that's easy.  I'm sure it has an external VGA video connector, so you can hook your monitor in that way.

---

### Post by Madonkadonk on 2011-02-03
> **dabl said:**
> That's just a notebook, but it does have a 1.8GHz CPU, so it could do some reasonable desktop work, if you had the memory and the drive capacity.  Does it still have the stock 1GB memory?  What kind of "desktop" are you envisioning, in terms of work capability?

It seems to me the biggest challenges are not the monitor, but instead are:

(a) puny GPU
(b) puny HDD and no external SATA or firewire connectivity
(c) needs a memory upgrade to do any serious desktop work

So, it looks like a tough problem, to me -- it's not designed to take a serious graphic card, and the only effective way to add drive capacity would to put a SATA hdd into an external enclosure, with power, and then cut a hole in the case to run a SATA cable inside to the port connector.  You could use a USB keyboard and USB mouse, so that's easy.  I'm sure it has an external VGA video connector, so you can hook your monitor in that way.

I don't plan on doing that much with it, I just want to salvage the laptop as a non-moving desktop, not to do desktop related things, I have another desktop computer for that that I run my media and web server off of, and I have another laptop (HP DV6) That i do most of my regular computing and gaming for, I just want this thing as another computer that I can write some quick, simple programs on and word processing, it would be my school desktop. Also I have a plethora of external hard drives to compensate for the lack of hard drive memory in the computer and can always buy more memory if needed. And it does have firewire. Also if there is any other problems with power, i could use xubuntu.

---

### Post by realzippy on 2011-02-03
*I want it to run while it is shut*

..then the lid switch would send it to sleep.depending on your skills
you could disassemble it and disable the switch,but then the display would
be powered on...and some laptops have the cooling air inlet on the top.
So suggest to unscrew the display totally.

---

### Post by Dragonbite on 2011-02-03
Trust me, it looks good enough to handle most stuff. Are you compiling 3D, large programs and/or games? If not, then it should be fine. If you ARE compiling, then make sure you have enough deli meats to make sandwiches with while compiling.

I'm running Ubuntu on a 1.8GHz Pentium M w/1GB Ram Dell D400 laptop and the previous version before it took a "shower" was 1.4GHz. My primary desktop is a P4 at 2.4GHz with 2.5 GB Ram but before that it was a 2.0 GHz w/512 MB Ram.  They work fine.

In most of my systems, if the external monitor is on when the machine boots up, I get a cloned image on the monitor.

To not shutdown or suspend when the lid is closed, look in the Power Settings.  You should be able to set it so when the lid is closed for the monitor to continue.

You could try, after you know the external monitor will work when booting up, to open the laptop and see if you can unplug the monitor and boot it up with the external monitor on.  If this works, then why not remove the entire screen?  Gives you unfettered access to the On/Off button, plus the system will continue and not try to use the built in screen because during bootup it should determine it isn't there.

More knowledgeable people might be able to bring up some settings in X configuration to handle what you are looking for.

---

### Post by Madonkadonk on 2011-02-03
> **Dragonbite said:**
> Trust me, it looks good enough to handle most stuff. Are you compiling 3D, large programs and/or games? If not, then it should be fine. If you ARE compiling, then make sure you have enough deli meats to make sandwiches with while compiling.

I'm running Ubuntu on a 1.8GHz Pentium M w/1GB Ram Dell D400 laptop and the previous version before it took a "shower" was 1.4GHz. My primary desktop is a P4 at 2.4GHz with 2.5 GB Ram but before that it was a 2.0 GHz w/512 MB Ram.  They work fine.

In most of my systems, if the external monitor is on when the machine boots up, I get a cloned image on the monitor.

To not shutdown or suspend when the lid is closed, look in the Power Settings.  You should be able to set it so when the lid is closed for the monitor to continue.

You could try, after you know the external monitor will work when booting up, to open the laptop and see if you can unplug the monitor and boot it up with the external monitor on.  If this works, then why not remove the entire screen?  Gives you unfettered access to the On/Off button, plus the system will continue and not try to use the built in screen because during bootup it should determine it isn't there.

More knowledgeable people might be able to bring up some settings in X configuration to handle what you are looking for.

I would love to be able to do that, but I think my wireless antenna is in the monitor.

---

### Post by realzippy on 2011-02-03
> **Madonkadonk said:**
> I would love to be able to do that, but I think my wireless antenna is in the monitor.

Use another antenna or unsrcew it also and glue it on the back...   :p

...basically an antenna is an unscreened cable with a defined length.

---

### Post by Dragonbite on 2011-02-03
You don't have a wired network option?

---

### Post by Madonkadonk on 2011-02-03
> **Dragonbite said:**
> You don't have a wired network option?

No not really, I'm trying to do this as a "Try not to spend any money" kind of project cause i already have a monitor keyboard and mouse, but what I don't have is an extra ethernet cable.

---

### Post by dabl on 2011-02-03
I missed the firewire (IEEE 1394a) port when I skimmed the specs.

So, yes, you could put a reasonable-sized SATA hdd in one of these: [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6046577&CatId=2780](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6046577&CatId=2780)

and use that for your data, and let the internal drive be for the OS.

I use KDE so I'm not familiar with the current Gnome power management settings, but I'm sure you can, as a rough solution, just turn off the "screen" features of power management, to disable "lid closing" events.  If it were me, I would open the case and figure out how to (a) set the lid switch in "always open" position, and (b) disconnect the video cable from the inside of the case to the LCD. As long as a monitor is attached to your VGA or S-video connector, I think that's the one that will be selected by the system.

---

