---
title: "Hard drive clicking"
date: 2009-07-27
forum: Hardware
---

### Post by tompagenet on 2009-07-27
I've just installed Jaunty (9.04) using wubi on my Dell XPS M1330. All is good when running on the mains power, but when running from the battery the hard drive seems to go to sleep and wake up again over and over again, much as described in [bug 59695]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695"). That bug is marked as having had a Fix Released, but I'm very much getting the clicking.

I'd really appreciate any help here, and I should say I'm a real Ubuntu beginner, so do spell it out in words of less than one syllable.

Many thanks

Tom

---

### Post by komputes on 2009-07-27
From my experience if your hard drive is clicking, make a backup while you still can...

---

### Post by mikewhatever on 2009-07-27
Well, the bug was mainly a problem on desktop computers where power saving is not a feature of great importance, or on notebooks running on AC power. The fix makes sure there is no disk power saving when running on AC, however, it is only logical to try and save some watts when on battery.
There are ways of reducing disk activity and saving power, quite accidentally, just for your notebook.
[http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

It may look a bit intimidating, but I am sure the author an others, including myself can help.

---

### Post by tompagenet on 2009-07-28
Thanks mikewhatever, kind of you to respond and offer help.

The problem does sound like the aforementioned bug - i.e. while running on battery the hard drive will go to sleep and then wake up again about once a minute, with the distinctive click that accompanies the heads parking and being re-awoken.

I'm not really concerned about power consumption when on battery - obviously I want the machine to run without running out of power immediately, but I have no need to optimise it very much. However I don't want the hard drive to keep going to sleep - I can't imagine this repeated cycle does the drive much good, and if I left it happening I would need to follow komputes' advice below.

Many thanks

Tom

---

### Post by mikewhatever on 2009-07-28
I understand the concern, but on the other hand, am quite sure it's probably not that bad. You should only be worried if you work on battery a lot, also, bare in mind that no hard disk is going to last forever. My own hdd has been making the clicking for 3 years without replacing.
You should check the current value of Load_Cycle_Count by installing **smartmontools** from the repositories and running the following command: **sudo smartctl -a /dev/sda | grep Load_Cycle_Count**.
If you want to disable the spin-downs when on battery altogether, use **sudo hdparm -B 254 /dev/sda**, although a lower value (for example 192) is recommended.

---

