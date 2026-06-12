---
title: "Powerplay?"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by nolongerlivecd on 2006-06-09
How do I get PowerPlay to enable itself by default? I mean that when I change from battery to AC and vice versa, how do I get it to change automatically?

---

### Post by toaste on 2006-06-09
Seconded.

For that matter, how can I get ATI Powerplay to enable at all?  Is it part of the proprietary fglrx drivers?

---

### Post by Aurelias on 2006-06-09
I'm in the same boat.  You need the proprietary fglrx drivers, but beyond that I don't know.  Running aticonfig --lsp just says "Error: Unable to obtain POWERplay information.", despite having a card that I know has powerplay.

---

### Post by crumja on 2006-06-09
If aticonfig --lsp doesn't work, you're tough out of luck (bios or firmware issue). If it gives you the states, you're in luck.

aticonfig --set-powerstate=1 gives you the lowest power state for one session.

To get it to automatically change, manually edit the acpi files (events) so that when you switch into ac power, it calls aticonfig by itself and changes to another powerstate. I think they're in /proc/acpi or /etc/acpi

Yes, it's part of the fglrx proprietary drivers.

---

### Post by spotman on 2006-06-09
oh boy...

I have spent the last 2 weeks solid trying to get my new lenovo t60 to play nice.   

I have the x1400 ati card in there.

I have installed suse 10.1, and powerplay works flawlessly.  As a matter of fact I can get FIVE hours of battery life in suse and the system is still very usable.  In ubuntu, im LUCKY to get 3.  I have narrowed this down to many things, but ultimately suse is just ahead of us when it comes to power.

Upon further investigation, Suse uses "powersaved", (kpowersave, powersave), and it has a running daemon and some scripts that manage this for them.  When you use the ATI installed on a suse system, it installed whats called "atieventsd".  What this does, I have NO clue, but it is NOT installed by either ubuntu or ATI on an ubuntu or debian system.

moving along, I have tried every combination of manual set power scripts with ubuntu's default acpi system, and I have tried to install the powersave daemon (its in the universe repository), and no dice.  I have tried to do this in kubuntu and ubuntu both with fresh and not-so-fresh installes.  In the past 2 weeks I have installed suse, ubuntu, and kubuntu 11 times.

Every time I either automatically or manually set aticonfig --set-powerstate=1 --effective-now I get a distorted ugly screen and 7/10 times the system shortly after locks up, and im screwed.

I have tried: 2.6.16.18, 2.6.16.20, 2.6.17rc5, and 2.6.17rc6...

Im currently running 2.6.17rc6.  

As a sidenote, anyone that has a tpad t60 or similar, you should probably disable ahci unless you want more headaches.  The disk speed is exactly the same, it still shows up as /dev/sda to the OS, but ahci mode is very buggy when it comes to power management.  As a matter of fact, it hasnt been natively built into the kernel till 2.6.17rc6, anything that claims to have it before hand (such as ubuntu's default kernel) has done so with a customized patch.

If anyone can shed any light on this acpi/power management situation.. it would be greatly appreciated..

I know all we all want is a stable system, with good battery life and good package management.  It's a good thing suse has rpm's or I would've switched ;)...  don't even mention yast.

---

### Post by nolongerlivecd on 2006-06-09
I don't really know, I just set aticonfig --set-powerstate 1

That's all I do.

---

### Post by sean on 2006-06-19
I am in the same boat as yourself.  I have been battling on and off issues with aticonfig --set-powerstate=X.  For a while, it seemed that the display
corruption upon execution of that command was purely random.  However,
it now appears that I can get the ati X1300 in my Thinkpad T60 to go
into a lower power state <<if I first suspend2Ram and then awaken
it>>.

So there is something about either going into suspend2ram or the
wake-up process that makes it possible to set a powerplay powerstate.

machine:  Lenovo Thinkpad t60
video:       x1300
distro:     Ubuntu dapper drake

Not sure yet, why that is the case or how I can get further in
resolving this issue.


Sean



[QUOTE=spotman]oh boy...

I have spent the last 2 weeks solid trying to get my new lenovo t60 to play nice.   

I have the x1400 ati card in there.

I have installed suse 10.1, and powerplay works flawlessly.  As a matter of fact I can get FIVE hours of battery life in suse and the system is still very usable.  In ubuntu, im LUCKY to get 3.  I have narrowed this down to many things, but ultimately suse is just ahead of us when it comes to power.

Upon further investigation, Suse uses "powersaved", (kpowersave, powersave), and it has a running daemon and some scripts that manage this for them.  When you use the ATI installed on a suse system, it installed whats called "atieventsd".  What this does, I have NO clue, but it is NOT installed by either ubuntu or ATI on an ubuntu or debian system.

moving along, I have tried every combination of manual set power scripts with ubuntu's default acpi system, and I have tried to install the powersave daemon (its in the universe repository), and no dice.  I have tried to do this in kubuntu and ubuntu both with fresh and not-so-fresh installes.  In the past 2 weeks I have installed suse, ubuntu, and kubuntu 11 times.

Every time I either automatically or manually set aticonfig --set-powerstate=1 --effective-now I get a distorted ugly screen and 7/10 times the system shortly after locks up, and im screwed.

I have tried: 2.6.16.18, 2.6.16.20, 2.6.17rc5, and 2.6.17rc6...

Im currently running 2.6.17rc6.  

As a sidenote, anyone that has a tpad t60 or similar, you should probably disable ahci unless you want more headaches.  The disk speed is exactly the same, it still shows up as /dev/sda to the OS, but ahci mode is very buggy when it comes to power management.  As a matter of fact, it hasnt been natively built into the kernel till 2.6.17rc6, anything that claims to have it before hand (such as ubuntu's default kernel) has done so with a customized patch.

If anyone can shed any light on this acpi/power management situation.. it would be greatly appreciated..

I know all we all want is a stable system, with good battery life and good package management.  It's a good thing suse has rpm's or I would've switched ;)...  don't even mention yast.[/QUOTE]

---

### Post by brokerjoker on 2006-07-03
Exactly the same here. TP T60 with x1300 and aticonfig --set-powerstate crashes randomly. I have the impression that this issue is related to the temperature of the system. The colder it is, the higher is the probabilty that the system won't crash.

Anyhow, this feature ist complete unusable this way. Too sad, as my battery life is quite short this way.

I think about trying the new ATI driver, but I must admit that I am a coward and I need a stable system these days. Does anyone have experiences with that?

Thanks, bj.

---

