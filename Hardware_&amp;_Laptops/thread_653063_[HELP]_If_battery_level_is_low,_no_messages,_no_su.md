---
title: "[HELP] If battery level is low, no messages, no suspend... the system goes down! :("
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by starise on 2007-12-29
Hi. I'm a desperate user! :(

When power of my battery is low, nothing appear by gnome-power-manager. No notifies and it don't suspend my system (the option is enabled). Simply the system goes down and i lost all my unsaved works! Also at the boot i find Inconsistency in my file systems. The only solution is manually check sometimes the battery level and shutdown the notebook before! :( :(

I need this function 'cause i use so much the notebook on battery.

P.S.: My notebook is a Dell XPS M1330

---

### Post by ilarrain on 2007-12-30
Same problem on my laptop. A Toshiba Tecra A6. I've even lost every file on my ext3 partition once. now I'm on a much decentralided partition table, using reiserfs and xfs for partitions frecuently changed and ext2 for boot.

And now I never let my laptop run completely out of battery.

I'd be very glad if someone post a fix for this problem.

---

### Post by alex1996arm on 2007-12-30
is there an icon??:)

---

### Post by starise on 2007-12-31
Yes. g-p-m icon is present. Suspend-to-ram work correctly but not automatic.

---

### Post by twrock on 2008-01-01
Just adding my name to the list of people with this problem. I'm using a Dell 700m.
Seems to be a significant number of problems with Ubuntu and power management. I wonder if other distros have this stuff ironed out. Seems laptop power management is a fairly important issue that should be up there on the priority list of bug fixes. How wide ranging is this issue?

---

### Post by starise on 2008-01-02
> **twrock said:**
> Just adding my name to the list of people with this problem. I'm using a Dell 700m
I have also a Dell. Coincidence? ;)

---

### Post by twrock on 2008-01-20
First, here's my sytem info: Dell 700m laptop running Gutsy. Problem: no warning messages on low battery and no hibernate, just "instant-off" when the battery runs down. Suspend seemed to be working properly via the keyboard trigger and via the lid closing.

So I did a bunch of messing around with gnome-power-manager in the configuration editor. Unfortunately that means I'm really unsure of which values I changed that started to make a difference. In any case, I now am getting warning messages and hibernate action on critically low battery. I say "initial" because it worked once completely (i.e. all the warning messages as the charge dropped to critical and "empty" states and then finally hibernated), but after restoring from hibernate, the second time I let the battery discharge, the computer hung up while trying to go into hibernate and had to be fully rebooted (by holding down the power button). Anyway, here's what I did.

Based on another post ([http://ubuntuforums.org/showthread.php?t=666557](http://ubuntuforums.org/showthread.php?t=666557)), I added "acpi-cpufreq" to the /etc/modules file (just because that worked for someone else, not because I have any idea of what difference that made) and unchecked /apps/gnome-power-manager/general/user_time_for_policy in the Configuration Editor.

Then as I looked through the other settings in the Configuration Editor, I decided to make the following additional changes:
/apps/gnome-power-manager/actions/critical_battery set to hibernate
/apps/gnome-power-manager/thresholds/percentage_action set to 3 (I think I'll set this even higher so that there is enough battery power left to completely hibernate.)
/apps/gnome-power-manager/thresholds/percentage_critical set to 5
/apps/gnome-power-manager/thresholds/percentage_low set to 10
Finally, I made sure everything in /apps/gnome-power-manager/notify was checked.
I rebooted to make sure the settings would all be active.

After my initial testing, I went back and changed the thresholds percentages to 16, 18, and 20, just to be sure that was doing anything at all and to not have to wait until my battery was completely dead again. At 20% I got the battery is "low" message, about two minutes later I got the "critically low" message and a warning that the laptop would hibernate soon (but it said I had 0% battery state!), and about two minutes later it hibernated properly. And this time around, I unplugged the AC cord and let it run through another hibernate cyle, and the second cyble worked this time. So it looks like I have at least something working at least some time. The most important to me was just getting the warning messages to pop up again (pre-Gusty), instead of just having the machine die without notice in the middle of something important.

I don't know if any of that helps anyone else, but at least it did help me some.

Unfortunately all of this change created a new problem. It now seems like each time I unplug the AC cord, the system suspends and I have to bring it out of suspend to use it. It isn't too much of a problem, but it is annoying. I did set the /apps/gnome-power-manager/general/invalid_timeout to 1000 (up from 500), hoping this had something to do with it. Unforunately, that seems to have done nothing. I also get the following pop up on resume from suspension: "Action forbidden. Policy time-out is not valid. Please wait a few seconds and try again." I tried setting the /apps/gnome-power-manager/general/policy_suppression_timeout to 7 to resolve this, but that didn't help either. Any suggestions about either of these would be appreciated.

---

### Post by twrock on 2008-01-26
Ok, after a bunch more testing, it seems the only thing that I actually needed to do to get low battery warnings and auto-hibernate on low battery was to add "acpi-cpufreq" to the /etc/modules file. So it doesn't matter on my machine which notification measure I choose in the Configuration Editor (time-based or percentage-changed-based). But increasing the threshold values did make sure that there was enough power left to finish hibernating.

---

### Post by Endolith on 2008-05-31
I also have this problem on a Dell Inspiron 8600.  It just shuts off with no warning whatsoever.

---

