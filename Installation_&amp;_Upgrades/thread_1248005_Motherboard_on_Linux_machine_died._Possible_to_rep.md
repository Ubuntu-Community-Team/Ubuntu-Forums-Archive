---
title: "Motherboard on Linux machine died. Possible to replace without kernal panic?"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by Clade on 2009-08-23
Hello everyone,

I have spent quite a bit of time with my Ubuntu machine, making it it my web dev server, virtualization server, etc. I love it so much, and I seriously can't believe I got along in windows without it for as long as I did!

However, my motherboard died. I need to replace it. I have a vibe that this is going to result in a kernal panic.  This could also be an opportunity for a fun challenge.

1. Would this be the case?
2. What would be my options/is this doable?
    A. Using some sort of recovery method off the Ubuntu CD
    B. Recompiling the Ubuntu kernal to work with my hardware
    C. Disabling and enabling certain modules

I'd really be interested in getting my hands dirty. I have no sensitive data here to save, but instead, an opportunity to learn.

Thanks, guys.

---

### Post by ajgreeny on 2009-08-23
You may well be disappointed if you are expecting this to be a big challenge, as I fear it will all go without problem, particularly as it sounds as if you are running a server without gui.

If you do run it with gnome, the biggest likelyhood of a problem could be with graphics drivers for a changed on-board card, but even that may well be accommodated now that xorg is better at detecting hardware.  Otherwise I think everything is likely to just carry on working without problem.  Just do a bit of homework on the best motherboard to use and you should be good to go.

---

### Post by stlsaint on 2009-08-23
yes i agree with above...it would be even better if you had a backup of your old system just to cover all basics but considering that kernel doesnt load itself to your MOBO than you should be good! now the hdd would be another story in which you may want to do a backup just in case you dont have one!!

---

### Post by SunnyRabbiera on 2009-08-23
Usually Linux does well compared to windows when concerning making changes to the motherboard.

---

### Post by Clade on 2009-08-23
lol, guys. I appreciate the information!

I will give it a go, then. I'm shocked it's going to be this easy. 

[ajgreeny]("http://ubuntuforums.org/member.php?u=27747"): For the record, I'm using Blackbox as of this writing.

[stlsaint]("http://ubuntuforums.org/member.php?u=814785"): I have no sensitive data so it shouldn't be a problem, but thank you.

[SunnyRabbiera]("http://ubuntuforums.org/member.php?u=23967"): I figured Ubuntu would have built a kernel specific to my specs; I guess that's more of a broader thing than I figured?

Thanks so much guys. I preach about Ubuntu all the time not cause of it's awesome OS, but cause of some awesome people on here who really share what they know.

---

### Post by jpope on 2009-08-30
Earlier this year, I had to replace the motherboard in my desktop pc. I went from a xfx mobo to a msi mobo. At the time I was triple booting with Ubuntu 8.10, XP Pro & Win7 beta. Ubuntu was the only one of the three that had 0 issues with the change, Win7 wasn't bad as it just updated a few drivers and XP was never quite right after until I reinstalled it. 

You will have more of a challenge with actually changing the mobo than starting Ubuntu up after the change... ;)

---

### Post by inobe on 2009-08-30
i to swapped a motherboard and was amazed that nothing with software needed to be done.

it booted up to the desktop as if nothing ever happened.

---

### Post by Bartender on 2009-08-31
A few weeks back I installed Linux Mint Gloria (a variant of Ubuntu) to a PATA HDD on a Pentium 4 desktop.  Yesterday I plugged that drive into an old Pentium III PC.  Nothing's the same - video chipset, northbridge/southbridge, old PC100 RAM instead of DDR, etc.  

Mint did a system check, said there was some kind of error and wanted to reboot, then came up on the Pentium III like nothing had happened.

---

