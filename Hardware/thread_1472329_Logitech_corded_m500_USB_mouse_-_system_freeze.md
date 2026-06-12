---
title: "Logitech corded m500 USB mouse - system freeze"
date: 2010-05-04
forum: Hardware
---

### Post by eurik on 2010-05-04
On my new installation od Ubuntu 10.4 (64 bit, desktop PC), the system  randomly freezes when I use my new Logitech corded m500 USB mouse.

It doesn't happen with my old ps2 genius mouse (which is ancient and  half broken already), only with the new USB mouse.

All buttons work properly, the mouse is recognised correctly as a  device, and everything seems just shiny up until the system freezes  randomly after a few minutes of work (usually, but not eclusively while  browsing the web). The cursor stops moving and unless I immediately kill  X, the whole system freezes (incl. terminals, ctrl+alt+bcsps, nothing  but hard restart works...)

I'm pretty sure that is is not a PC performance problem (1G RAM, 3+GB  swap), also since I'm dualbooting with Win, I know the mouse is not  faulty as it works fine in WinXP.

Any ideas?

P.S.: I googled and tried all the common stuff (noapic setting in grub,  compiz off) but it still happens. Can somebody help, please? :confused:

---

### Post by winecurmudgeon on 2010-05-04
I have a Logitech cordless keyboard and mouse (Wave), and I get random mouse freezes in 10.04 as well. Did not happen in 9.04. I'm wondering if it's a Logitech problem.

---

### Post by eurik on 2010-05-04
No idea. I'm running in the most minimalistic mode I'm able to set up and it crashed yet again a moment ago :(

---

### Post by youoh on 2010-05-04
MX 5000 here. Keyboard lags, key's ignoring @ fast typing, mouse lag when kys are pressed.

---

### Post by Zunino on 2010-05-05
I'm also struggling with this mouse cursor freeze problem. Fiddling with acpi settings did improve the situation significantly, but the freezes still occur. Some other things I've tried include disabling compiz and removing nVidia's proprietary driver. To no avail.

So, my Ubuntu 10.04 experience has been nothing like what I expected. Unfortunately. It's so bad that I'm going back to 9.10 tonight (tired of spending evenings trying to get the problem sorted out instead of doing something productive or just having fun.)

In any case, if anybody finds something new about this issue, be sure to keep others informed, by posting here on the forums.

Regards,

---

### Post by eurik on 2010-05-06
It's kind of a shame that this doesn't seem to be too uncommon a problem, I've seen quite a few questions about USB devices and yet no suggestions, advice or attempts to fix the bug :/

---

### Post by Zunino on 2010-05-06
Hi there!

Last night, before going back to 9.10, I decided to give 10.04 another try. I reinstalled it from scratch and chose not to activate the nVidia proprietary graphics. The only packages I did install were sun-java6-jdk and thunderbird. I also chose not to add the acpi option to the /etc/default/grub file. I browsed the Web, edited some files and did some other stuff. Surprisingly, no freezing had occurred to that point.

Then, just as I updated the package information from the sources, I noticed a lot of updates available, including acpi, linux-image etc. I installed all of them and restarted. Next, I decided it would be all or nothing and installed the proprietary nVidia driver, rebooted and enabled the full range of visual effects. I also installed the Compiz settings manager. And everything kept working like I had never had any problems.

In the end, I'm still not sure whether the updates got rid of the issue or if it was something else. The bottom line is that I was able to use the system normally for some 3 hours, flawlessly. Before last night, the system would consistently hang (the mouse pointer, that is) within 10 to 20 minutes.

That's it. I'm sorry if I can't be of much help by giving detais on possible solutions. I just thought I should get back to you and report what happened. If anything new comes about, I'll let you know.

Wishing you good luck.

---

### Post by eurik on 2010-05-20
I reinstalled, even downgraded. It doesn't seem to happen in the .14 kernel, but happens with the .21 kernel no matter what I try.

---

### Post by eurik on 2010-08-11
"BUMP"

This problem is still on. No amount of googling enabled me to run Ubuntu with this mouse without the system freezing after a few minutes.

Any solutions yet?

---

### Post by circuitz on 2010-09-21
I am running ubu 10.04 with latest updates.  I just bought an m500 mouse.  For a few (10) seconds it works fine, then the buttons quit working.  The cursor never actually freezes and I can hit alt-f2 to get a menu but moving the mouse to the top bar does not cause it to unhide.  I tried it on my eee900 running 10.04 no compiz and got the same thing. Then I tried it on my other eee900A running 9.10 with compiz and got the same thing. So on Windows XP it works fine.  Any help would be appreciate, I can post dmesg and syslogs if requested.

---

### Post by littlewing on 2011-09-02
Hello,
do you know if the logitech m500 works now on ubuntu 11.04 ?

Thanks 

Alexandre

---

