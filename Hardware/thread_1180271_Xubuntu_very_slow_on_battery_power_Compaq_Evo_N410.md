---
title: "Xubuntu very slow on battery power Compaq Evo N410c"
date: 2009-06-06
forum: Hardware
---

### Post by moodle on 2009-06-06
Hello,

I am a Linux newbie.  I have tried Ubuntu, Xubuntu and Puppy Linux on my Compaq Evo N410c laptop.

All three distributions are snappish when AC power is plugged in, but grind to a sluggish halt if I unplug the cable to run on battery power.

The battery is only one year old, and when I had Windows installed it provided up to 2 hours runtime with no slowdown in speed.

The slowdown in linux happens whether or not I am using wireless.

My system has 371MB RAM, a Mobile Intel(R) Pentium(R) III CPU - M 1000MHz, and 13GB of available diskspace.

My wireless card is a Belkin, using Windows drivers with the Ndiswrapper.

Installations I have tried are Ubuntu 8.04, Xubuntu 9.04, and Puppy 4.1.2.

Thank you in advance for all your help.

David

---

### Post by kabloink on 2009-06-06
Most likely the cpu is being put into an ondemand or powersave mode once power is removed. A easy way to check this and make changes is to add the cpu governor applet in Xubuntu or the cpu frequency scaling monitor applet in Ubuntu to your task bar.

---

### Post by moodle on 2009-06-07
Hi Kabloink,

Thank you for the reply.  I tried adding the cpu governor applet, but unfortunately the computer still runs very slow when the power is unplugged, even if I select 'performance' in the governor applet.

Do you have any other suggestions?

David

---

### Post by moodle on 2009-07-13
I'm still struggling with this issue.  Can anyone else help please?

Could the problem be that the battery in my laptop is not a Compaq original?

---

### Post by moodle on 2009-07-13
I would like to reiterate that the laptop has exactly the same problem when running Puppy Linux and ZenWalk Linux.

---

