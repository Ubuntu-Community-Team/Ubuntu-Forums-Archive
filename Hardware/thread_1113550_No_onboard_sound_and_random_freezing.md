---
title: "No onboard sound and random freezing"
date: 2009-04-01
forum: Hardware
---

### Post by pritcharded on 2009-04-01
I'm attemting to install 8.04 on my daughter's LG LW70 Express laptop (from what I can see an entirely ordinary integrated Intel PC) . The installation seems to be working perfectly except for two issues:
1. With external speakers plugged into the earphone jack I get perfect sound, but using the onboard speaker I can get nothing. It works running under Windows so I conclude it must be a software issue. I have installed the additional software recommended in these pages and have followed Markbuntu's post. The PC is fitted with an Intel 82801FB/FBM/FR/FRW (ICH6 family) High Definition Audio Controller (rev 04). I have even undertaken a complete reinstall but alas without success. I presume the speaker must be muted but if it is I can't find how to turn it on.
2. When the battery is removed and the PC is running off the charger, the PC is stable and works well. When the battery is in place and the charger connected, the PC works OK then suddenly completely freezes for no consistent or apparent reason. Nothing will work - even crt-alt-backspace won't cause exit. It becomes a matter of disconnecting the charger and removing the battery. I've had the PC to the technicians for a complete physical check and they have declared it to be in perfect operating condition.  

Help on these two issues would be much appreciated

Ted

---

### Post by SciB6y on 2009-04-20
I have fixed both these issues (though my problem with freezing doesn't have anything to do with the battery) in 8.10. 

Add the line ```
options snd-hda-intel model=minimal
``` to 
the file ```
/etc/modprobe.d/alsa-base
```

to fix the sound problems.

But before that, you can remove the problems with the freezing by adding the line ```
blacklist pcspkr
``` to the file ```
/etc/modprobe.d/blacklist
```

Problem with that driver is that it crashes whenever the system wants to beep (locks the computer just like you describe). Which might seem random. It occurs for example if you press backspace once to many, or if you use autocomplete (tab in a terminal window), or if you type "shutdown -r now" in a terminal.

With that driver blacklisted, you won't get a beep, but you'll also won't get the crash. :-)

---

