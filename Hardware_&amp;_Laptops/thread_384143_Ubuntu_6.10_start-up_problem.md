---
title: "Ubuntu 6.10 start-up problem"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by silent_death on 2007-03-14
hey I just got Ubuntu 6.10 and I am having problems with most linux distros for some reason.

After I got into the main menu for the boot cd, I selected to start and install Ubuntu from the LiveCD. the loading up process started fine and it went fine untill it loaded to 100% because when it did, it tried to boot Ubuntu and switched my screen off... well my laptop screen just went blank.
I tried installing in OEM mode and it installed fine (I am dual booting this with xp... or trying to anyway). the partitioning went fine and so did the installation.

when i restarted my computer and chose the 1st option to boot Linux the load option again came up alright and when it did load, the screen again went blank and wouldn't turn on again (unless i restarted the computer)
I have tried starting in graphic safe mode but again the same problem.
I am not sure whats happening and any help to this topic would be appreciated. I have tried to research lots but to no avail so am getting abit desperate really.
I also tested the cd and did the test and it said my cd is fine to install from.

my laptop spects are:
Intel Pentium M 2.0Ghz
1Gb ram
ATI mobility raedon X700 256 mb video card.

If you cant post for some reason then if u can e-mail me at [email]tushar88@gmail.com[/email] then that would be appreciated as greatly too.

---

### Post by matburton on 2007-03-14
I would guess its your X700 that cause this.

You might want to check this out:
[https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/22985]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/22985")
about LCD switch off with the mobility X700

And you may also find something helpful here:
[http://ubuntuforums.org/showthread.php?t=376013]("http://ubuntuforums.org/showthread.php?t=376013")
Although they may only discuss the desktop version of the card.

I'd guess that the problem is that X is mis-detecting where your LCD is and switching it off as in the bug above!

Hope that helps!

---

### Post by silent_death on 2007-03-15
hey thanks for those links,
I also asked around with my mates and apparantly most linux distros dont have drivers for X700. It might work if i:
a) either open up my laptop and take out my x700 and sell it off (which is not an option for me:P)

b) i go into bios and disable the card and just work through with my integrated card, which would be painful to use.

so now i am trying to research in google on how to install x700 drivers in linux, hopefully ubuntu.

---

