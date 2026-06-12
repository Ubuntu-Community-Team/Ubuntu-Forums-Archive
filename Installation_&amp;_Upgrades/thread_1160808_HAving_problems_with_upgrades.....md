---
title: "HAving problems with upgrades...."
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by nestorpistor on 2009-05-16
I just reinstalled on my laptop and did a CLI update and upgrade only to have the upgrade stall and completely freeze the laptop.  had to power off to reboot.  It stalled at package 6 which was GNOME-APPLETS-DATA.

After the reboot, I did the CLI update again then installed the offending package with no problems.  I started a CLI upgrade and it stalled again but at pkg 7 which is LIBGL1-MESA-DRI 7.4-0UBUNTU3.1 stalled at 21% downloaded.

Is there something wrong with the repositories?  The network is steady.  My kids have been playing internet games all evening and I've used the laptop with the new Ubuntu studio install to surf and download a whole bunch of tar files to install after I finish upgrading.

Any thoughts ao ideas?  I'm running an HP Pavilion Entertainment PC DV6000 with dual core turion procs and 2 gig mem & Nvidia.  It was running the previous version of ubuntu just fine with nary a problem.

I installed the I386 version.

Thanks
Nestor

---

### Post by tommcd on 2009-05-16
> **nestorpistor said:**
> I just reinstalled on my laptop and did a CLI update and upgrade only to have the upgrade stall and completely freeze the laptop. 
What version of Ubuntu did you install? 
When you say "upgrade" are you trying to upgrade to the current version 9.04?
How are you doing the updates? Post the commands you are using.

---

### Post by nestorpistor on 2009-05-16
> **tommcd said:**
> What version of Ubuntu did you install? 
When you say "upgrade" are you trying to upgrade to the current version 9.04?
How are you doing the updates? Post the commands you are using.

Installed 9.04 I386

CLI  apt-get update
     apt-get upgrade

gets stuck solid at pkg 6

rebooted
CLI  apt-get update
     apt-get install gnome-applets-data

it installed fine

CLI  apt-get update
     apt-get upgrade

gets stuck solid at pkg 7

rebooted, went to bed pissed off.

I'll be trying 64 bit today and if it does the same I'm outta here.

Nestor

---

### Post by tommcd on 2009-05-17
> **nestorpistor said:**
> 
CLI  apt-get update
     apt-get upgrade

I assume you used "**sudo** apt-get update" and " sudo apt-get upgrade". Is that correct?

When you ran "sudo apt-get upgrade" did it say any packages were being held back? With "apt-get upgrade" if a new package needs to be installed (to satisfy a dependency or whatever) it will be held back. To install the new package along with the updates you must run "sudo apt-get dist-upgrade". I have seen this happen a few times, so I always use dist-upgrade now.
If you use the update manager GUI, then no packages are held back in these cases. So I assume that the update manager uses dist-upgrade.

Do you use a proxy or firewall that may be blocking the updates?
Perhaps try a different mirror.

---

### Post by nestorpistor on 2009-05-17
No flame intended...i just capitalized to make my answers stand out...


> **tommcd said:**
> i assume you used "**sudo** apt-get update" and " sudo apt-get upgrade". Is that correct?   [b][i]yes...
[/i][/b]
when you ran "sudo apt-get upgrade" did it say any packages were being held back?   ***no...***

with "apt-get upgrade" if a new package needs to be installed (to satisfy a dependency or whatever) it will be held back.   ***i know that...***

to install the new package along with the updates you must run "sudo apt-get dist-upgrade".  [b][i]i did not know that, thanks
[/i][/b]
 i have seen this happen a few times, so i always use dist-upgrade now.
If you use the update manager gui, then no packages are held back in these cases. So i assume that the update manager uses dist-upgrade. ***the upgrade manager also stalls at the packages indicates...***

do you use a proxy or firewall that may be blocking the updates?
 [b][i]no, unless there is one activated during the ubuntu studio intall.  
[/i][/b]
perhaps try a different mirror.  ***how do i do that???  Example please...***


---

### Post by tommcd on 2009-05-18
To use a different mirror, go to: system > administration > software_sources, and select the main server instead of the mirror for the country you are in. What country are you in? 
The USA mirrors work well for me. Some people report faster spped with the main servers though, so try that.

---

### Post by nestorpistor on 2009-05-19
> **tommcd said:**
> To use a different mirror, go to: system > administration > software_sources, and select the main server instead of the mirror for the country you are in. What country are you in? 
The USA mirrors work well for me. Some people report faster spped with the main servers though, so try that.
I'm in Canada.  I don't know what the software source is set to and I'll probably never will as I gave up and loaded Debian 5.  That's what I'll stick with unless I can't get the wireless to work.

Thanks for the help.  Too slow in coming.

---

