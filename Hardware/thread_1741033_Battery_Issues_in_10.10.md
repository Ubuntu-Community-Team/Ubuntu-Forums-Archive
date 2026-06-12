---
title: "Battery Issues in 10.10"
date: 2011-04-27
forum: Hardware
---

### Post by tlebeau on 2011-04-27
I have a Toshiba Satellite L645 and the battery is not recognised in Ubuntu 10.10 

I have been searching forums and launchpad for over a week for a solution to no avail.  There is a [relevant bug on launchpad]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/703302") that doesn't seem to be getting any attention, so I thought I would open my own thread here and see what comes of it.

Basically the battery is not being recognised by the system.  I ***am*** able to run the laptop on battery, but there is no warning when the battery is about to die.  While plugged in OR unplugged, power manager displays as if it is plugged in "on AC power".  Finally, under the power manager settings, there is now "On Battery" tab for settings.

Under Windows 7 Home, the battery WAS recognised, so it seems like it should be possible under Ubuntu.

---

### Post by tlebeau on 2011-04-27
Here are the results of my acpi -V from terminal

deadkenny@Satellite:~$ acpi -V
Adapter 0: off-line
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10

---

### Post by tlebeau on 2011-04-29
just did a fresh install of 11.04 and the issue persists.  Also ensured that my bios was current prior to the reinstall.

---

### Post by tlebeau on 2011-04-30
Whats a brotha gotta do to get some help?

---

### Post by lukeanders70 on 2011-04-30
I have the same problem (except in 11.04) and unfortunately have found no solution. I assume you have already tried going into  "power management" and making sure the icon is turned on. Also try taking the battery out and putting it back in (this worked for me for one section and now doesn't anymore)sorry I couldn't be more of a help

---

### Post by tlebeau on 2011-04-30
Ive powered down, removed the battery and power cord and held down the power button for 20 seconds.
Ensured bios is updated
Checked the power manager and there is no "On Battery" tab, I have it set to always show the icon (which displays "On AC Power" even when unplugged as if the battery doesn't exist at all)
i have tried some lshal/acpi -v commands, all of which seem to indicate there is no battery present (which is obviously untrue)

---

### Post by lukeanders70 on 2011-05-01
Unfortunately, I don't have any idea how to help you. I will continue searching and will post anything I find. One more suggestion is (and I'm not one to be talking) that if you help other people they will be more likely to help you, improve your rating and you will have a better chance of getting a response, sorry I couldn't be more helpful.

---

### Post by lukeanders70 on 2011-05-02
Hey, I took out my battery, put it back in, booted into windows (where battery display works), restarted computer, booted into Ubuntu and battery icon was back.

going to go and try rebooting, to see if it works


update: unfortunately battery Icon is  once again gone... I have no Idea why the procedure above worked... sorry for getting your hopes up. If you find a fix make sure to post it

---

### Post by tlebeau on 2011-05-02
I completely removed windows from this machine due to the large amount of crap that came pre-installed form Toshiba.  I wonder if perhaps one of the programs that came pre-installed was actually some sort of ambassador between windows and the battery, allowing them to communicate with each other.  Sounds kinda crazy to me, but after weeks of searching and no real results, I will try about anything!

---

