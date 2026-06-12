---
title: "gnome-power-manager problems!"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by kimbrel on 2007-11-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/162949](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/162949) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a Lenovo Thinkpad T60 (Core Duo, Intel 945M chipsets, ATI Radeon Mobility X1400, Intel PRO/Wireless 3945ABG) that I started with Feisty.
I had no issues with power management under Feisty.
After upgrading to Gutsy, I have massive problems with gnome-power-manager.

When I unplug the machine from AC power, even with a fully-charged battery, gnome-power-manager puts it to sleep (S3). After this has happened once, g-p-m no longer responds to the lid switch as a sleep-triggering event even though I have configured it to sleep when I close the lid both on AC and on battery power.

Has anyone else seen these problems with gnome-power-manager on Gutsy? 
I’ve started a bug report over on Launchpad, but I haven’t gotten any responses yet.

---

### Post by TheRoot on 2007-11-17
Yes I have seen this error on my friends Laptop the same as yours. Only the problem he is facing is: when he switches to battery power the screen goes "dim", even though he has set its settings to not be dim even if he is using the battery power. 

Strange right?

anyway take a look at this file maybe it shall help you:
/etc/default/acpi-support

---

### Post by dysolve on 2007-11-17
my laptop screen dim when i go to battery power to turn this feature off on my machine its a setting in bios..

---

