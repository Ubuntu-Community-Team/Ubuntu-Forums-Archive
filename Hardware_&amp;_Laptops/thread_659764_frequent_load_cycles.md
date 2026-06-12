---
title: "frequent load cycles"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by eeerik on 2008-01-06
Hey.
I remembered reading about the headlines on slashdot about "ubuntu killing hardrives" (as it seems to be so elegantly put across the tubes).

Anyway, I was bored, I decided I would check to see how my box was doing.
Installed smartmontools and did a smartctl for sda3, my only hard drive.
This laptop is three month old (HPdv6000) and I'm already at 60,000 cycles (though I've been running Vista for the majority of this time) at 1032 hours on. That puts it at roughly 60 per hour, mixing the two OS's. I don't know how often windows cycles it, but I checked in ubuntu and with the power in it ran 60 cycles in just under 20 minutes. I unplugged it and it seemed to keep doing it at the same rate (I could hear it, like three times a minute.) I was surprised to find this since I was basically convinced I was unaffected when I did the command to show if the laptop is running in laptop mode enabled, and it came back =false. 

This comes at a really bad time since I finally ndiswrappered my bcm43xxs which took a long time, got my graphics drivers working, configured everything to my liking, etc - two afternoons of work - and I couldn't have been happier with the result. Booting back up into windows (vista, bleh) for fear of my hard drive hitting max cycles (guessing 600k) by next week wasn't exactly what I wanted to do, but here I am.

I've looked around and found fixes that seem sketchy at best (hdparm setting to 254), but that seems to just keep the hard drive spinning, and various people have noted concern over heat issues - various people have also said its nothing to worry about).
Hasn't the Ubuntu team come up with a patch? Something to just space the cycles further apart?

I was sure I would find a sticky here, I was surprised I didn't.
Have I missed something? :P

Thankful for any insight to this matter
don't want anything nasty happening to my beautiful laptop :)
eeerik.

[I]Specs: 
hp pavillion dv6000
Amd Athlon/Tk-55 Dualcore 1.8ghz
Nividia Mobile Go 7150 (nvidia restr.)
1024mb ram
bcm43xx wireless (ndiswrapper)
Ubuntu stable 7.1
[/I]

---

### Post by solar george on 2008-01-06
There has been a lot of discussion (most of it inconclusive, repetitive and not well informed) on this subject.

If you use the hdparam fix you hdd will run hotter and be more at risk of damage from shocks - I belive that some one suggested setting it to around 100 on battery and 255/254(depending on your laptop).

Also there was a suggestion that some laptops do not give accurate values as the raw data.

I've tried to give a summery of all the useful information that came out when this made the various blogs ect. 

I'm personally leaving the settings alone for now - unless there is an official fix I don't plan to mess around as my laptop seems to be unaffected (or maybe it is but its not telling me).

---

