---
title: "Processor Scaling - Not Selectable"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by iThinkergoiMac on 2008-02-21
So... I have an IBM ThinkPad R50 with Ubuntu 7.10 installed. I can't seem to be able to control the processor scaling. It's a great feature to have when I'm on battery, but I'd like to set the processor to the full speed when I'm on AC power. When I had Efty on here, I could do that. Just put in the processor scaling applet in the menubar and left-click on it. But in Gutsy nothing happens when I click on it and the option isn't there in the preferences. This is the exact same model of computer I had before, so I'm wondering why the option went away.

To recap: processor scaling works just fine on this, but I can't control it. It's not a huge deal, but it would be nice.

Specs:
IBM ThinkPad R50
Intel Pentium M (Centrino) 1.5 GHz Processor
ATI Radeon Mobility 7500
768 MB RAM
40 GB 5200rpm HD
Intel Pro Wireless Card
Gigabit Ethernet

Thanks!

---

### Post by PurposeOfReason on 2008-02-21
You can mess with those options in gconf-editor. Go to panel-gnomepowermanager, and tinker away.

---

### Post by iThinkergoiMac on 2008-02-21
OK... so I can edit it, but there's got to be a better way. Like how it used to bring up a menu whenever left-clicked on it... is it possible to resurrect that feature?

---

### Post by Yellow Pasque on 2008-02-21
> **PurposeOfReason said:**
> You can mess with those options in gconf-editor. Go to panel-gnomepowermanager, and tinker away.
Laptops often ignore the gnome settings for some reason. If that suggestion doesn't work, post your /etc/cpufreqd.conf file.

---

### Post by Yellow Pasque on 2008-02-21
> **iThinkergoiMac said:**
> OK... so I can edit it, but there's got to be a better way. Like how it used to bring up a menu whenever left-clicked on it... is it possible to resurrect that feature?
Go to a terminal and try this:
```
sudo apt-get install cpufrequtils
sudo cpufreq-info
```

---

### Post by iThinkergoiMac on 2008-02-21
> **Temüjin said:**
> Laptops often ignore the gnome settings for some reason. If that suggestion doesn't work, post your /etc/cpufreqd.conf file.

The suggestion did indeed work... and for working on AC power my setting are exactly what I want now (full power all the time). But when on battery I'm going to want to be able to switch between settings. I'll try your suggestion and see what happens.

So, yes, my laptop listens to those settings!

---

### Post by iThinkergoiMac on 2008-02-21
> **Temüjin said:**
> Go to a terminal and try this:
```
sudo apt-get install cpufrequtils
sudo cpufreq-info
```

So... it installed... but didn't really make any kind of difference that I can tell.

Also, the terminal spat out a bunch of things that were "automatically installed but no longer needed" or something like that... should I remove them?

---

### Post by Yellow Pasque on 2008-02-21
What is the output from cpufreq-info?

> Also, the terminal spat out a bunch of things that were "automatically installed but no longer needed" or something like that... should I remove them?
Yes, you can remove them.

---

### Post by iThinkergoiMac on 2008-02-21
Output:

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: centrino
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 600 MHz - 1.50 GHz
  available frequency steps: 600 MHz, 800 MHz, 1000 MHz, 1.20 GHz, 1.40 GHz, 1.50 GHz
  available cpufreq governors: conservative, userspace, ondemand, powersave, performance
  current policy: frequency should be within 600 MHz and 1.50 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.50 GHz (asserted by call to hardware).
```

Yes, I did set it to performance in the config file. So... it's listening just fine. I'm just trying to get the menu in GNOME back that was there in Edgy.

I figured I could remove the stuff... just wanted to make sure. Freed 50 MB :)

---

### Post by iThinkergoiMac on 2008-02-21
This is disturbing... I can't hibernate or sleep my computer anymore... and my USB flash drive isn't mounting automatically. I'm going to restart and see if that fixes it... but I really would like to be able to hibernate my computer again...

---

### Post by iThinkergoiMac on 2008-02-21
> **iThinkergoiMac said:**
> This is disturbing... I can't hibernate or sleep my computer anymore... and my USB flash drive isn't mounting automatically. I'm going to restart and see if that fixes it... but I really would like to be able to hibernate my computer again...

Strange... back to normal. I don't know what that was...

---

