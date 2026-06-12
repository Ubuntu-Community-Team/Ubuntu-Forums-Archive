---
title: "Battery drain while laptop switched off - power modes or some other solution?"
date: 2007-08-04
forum: Hardware &amp; Laptops
---

### Post by iheartmuseums on 2007-08-04
This issue has come up in another thread talking about Toshibas [here](http://ubuntuforums.org/showthread.php?t=321089&page=4), but I don't think it's getting much attention there.

A few of us with Toshiba Satellites (i've personally got an M100) are experiencing a drain of power from the battery when the laptop has been shut down. If I shut down mine and unplug it from any power source, it loses up to 25% battery power during the day while i'm at work (so it's switched off between 8-10 hours at a time).

Solicitous suggested it might be a power mode issue:
> **Solicitous said:**
> Well to add to the power usage whilst the laptop is turn off, I've done a little research and I think I may have come to a possible reason as to why.  I was looking through [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)
and it mentions two power modes of interest, G2 (S5) and G3.
Briefly, the G2 is a soft power off mode, which shuts down the PC yet power is still consumed by keeping devices alive, so it can perform a wake-on-lan option etc.  And G3 state being what is defined as a Mechanical Off, basically no power is run through the computer.  

After reading that, it sounded to me like a good assumption was the laptop is turning off in a G2 state, but not a G3 state, hence the power usage when turned off.

Anyone have any ideas/opinions on what I have just written?

Cheers,


Is this on the right track at all? Is there some way to switch the laptop's power modes so it shuts down completely, or is there some other solution? I'd love to have some suggestion as to how I can avoid this power drain, because losing a quarter of the battery's power while switched off for the day is frustrating as all hell!

Cheers.

---

### Post by Depressed Man on 2007-08-05
Interesting issue. I don't know much about it myself. Though I can say that my Sony VAIO (regardless if Ubuntu or Vista shuts it down) does consume at least 10% of its battery power even if it's completly off and unplugged for a few hours. Maybe it's just a battery issue.

---

### Post by iheartmuseums on 2007-08-06
I still don't understand how the battery could drain *so much*, though. Which makes me think there's something we could tinker with to avoid it.

---

### Post by glrossetti on 2007-08-22
It's not a battery issue. My Vaio VGN-S2XP (Feisty) drains the battery even while hibernated. Nothing happens when I run Windows. I have to remove  the battery in order to avoid the energy drain. I tried removing Usb, shutting down Bluetooth, putting Ati Radeon in deep sleep, changing hibernate mode. Inexplicable!

---

### Post by iheartmuseums on 2007-08-30
So something's accessing power while the system's shut down, and it's not a peripheral... could it be something like the Express Media Player? I am not sure if the Vaio machines have a similar thing, but it's a feature of the Toshiba which means you can access a media player for DVDs without booting your system.

---

### Post by Depressed Man on 2007-08-30
No, at least my VAIO doesn't have that. Though they do have integrated media servers or some junk like that.

---

### Post by iheartmuseums on 2007-08-30
This is driving me SO MAD. Seriously. I'm travelling at the moment and I have to charge my laptop EVERY time I turn it on. I wish there were an obvious answer, something that could be switched off! Blah.

---

### Post by iheartmuseums on 2007-09-15
As a sor tof bandaid solution, if I remove my battery quickly after I turn off my laptop, this stops it draining. A friend has suggested checking the BIOS when I boot up to change the ACPI power mode that it will shut down to - so when I remember that next time i'm booting, i'm going to see if it works!

---

### Post by MrHippocampus on 2007-09-15
Network ports are sometimes left active when a computer has been shut down so wake-on-lan can be used, while this shouldn't take up 25% over the course of a day it might be contributing to it. You might have to use a program called "ethtool" to switch it off or it might be somewhere in ubuntu's init system when ubuntu shuts down. Searching the forums/google might come up with something.

---

### Post by shador on 2007-09-15
Well just read some of the manual on my ne HP dv6521 laptop and it mentions the same issue. 

If you leave the battery in the computer while it's turned of it will slowly be drained. They recomend that you remove the battery. 

This confirms that the problem isn't the batteries. Because they're ok if you take them out. Maybe it has got something to do with what the thread creator said.

---

### Post by glrossetti on 2007-09-30
I think there's some type of configuration enabled by Ubuntu in bios, because I noticed Windows XP now drains energy even on hibernate or shutdown. That was not the case before I tinkered with Ubunutu.  I can't verify bios settings, because my sony Vaio has a crippled Bios interface. No mention of Acpi or power management.

It's similar to setting screen brightness in Xp: when I set this parameter in Xp, every time I boot the notebook with Ubuntu or Windows Xp, the brightness of the screen goes back to that setting, even if I remove the battery, or if I change brighteness with Ubuntu. Only Xp can modify the parameter. 

With energy draining problem instead only Ubuntu can change this setting, but how can we revert to the original setting?

---

### Post by lisati on 2007-09-30
> **iheartmuseums said:**
> This issue has come up in another thread talking about Toshibas [here](http://ubuntuforums.org/showthread.php?t=321089&page=4), but I don't think it's getting much attention there.

A few of us with Toshiba Satellites (i've personally got an M100) are experiencing a drain of power from the battery when the laptop has been shut down. If I shut down mine and unplug it from any power source, it loses up to 25% battery power during the day while i'm at work (so it's switched off between 8-10 hours at a time).

Solicitous suggested it might be a power mode issue:



Is this on the right track at all? Is there some way to switch the laptop's power modes so it shuts down completely, or is there some other solution? I'd love to have some suggestion as to how I can avoid this power drain, because losing a quarter of the battery's power while switched off for the day is frustrating as all hell!

Cheers.

> **glrossetti said:**
> I think there's some type of configuration enabled by Ubuntu in bios, because I noticed Windows XP now drains energy even on hibernate or shutdown. That was not the case before I tinkered with Ubunutu.  I can't verify bios settings, because my sony Vaio has a crippled Bios interface. No mention of Acpi or power management.

It's similar to setting screen brightness in Xp: when I set this parameter in Xp, every time I boot the notebook with Ubuntu or Windows Xp, the brightness of the screen goes back to that setting, even if I remove the battery, or if I change brighteness with Ubuntu. Only Xp can modify the parameter. 

With energy draining problem instead only Ubuntu can change this setting, but how can we revert to the original setting?

Interesting thoughts.
A couple of times recently, I've noticed that the charging light on my laptop has been on, when, as far as I know, the AC power has been plugged in since the last time I used it. It hasn't happened often enough for me to figure out a pattern. And on one occasion my desktop was told "shut down" from Kubuntu, but a couple of hours later the mouse light and the power light were still on..... Hmmmmm, maybe there's some kind of "incomplete shutdown" happening in certain circumstances.

---

### Post by Depressed Man on 2007-09-30
> **glrossetti said:**
> I think there's some type of configuration enabled by Ubuntu in bios, because I noticed Windows XP now drains energy even on hibernate or shutdown. That was not the case before I tinkered with Ubunutu.  I can't verify bios settings, because my sony Vaio has a crippled Bios interface. No mention of Acpi or power management.

It's similar to setting screen brightness in Xp: when I set this parameter in Xp, every time I boot the notebook with Ubuntu or Windows Xp, the brightness of the screen goes back to that setting, even if I remove the battery, or if I change brighteness with Ubuntu. Only Xp can modify the parameter. 

With energy draining problem instead only Ubuntu can change this setting, but how can we revert to the original setting?

I have this problem in Vista and Ubuntu. Sadly I have a crippled BIOS too. :(

---

