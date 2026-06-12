---
title: "Fingerprint Reader, Undervolting, fsck error?"
date: 2008-09-09
forum: Hardware
---

### Post by merlin_0525 on 2008-09-09
I just bought a new Sager NP7680 (Centrino 2), and after doing battle for a week, have almost everything working. The only things left are:

Installing and configuring the integrated fingerprint reader - How do I go about doing this? I've installed the bioapi package, but don't know what to do next...going to follow the directions on [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader) and see if it works...

Undervolting doesn't seem to work. The undervolting howto at [http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402) works fine until I get to the optimizer script. At that point, the VID's just keep going down, until it hits 0 and errors out. I think that my cpu just isn't accepting the new VIDs, since the temperature on the CPU doesn't decrease as the VID decreases. How do I go about solving this? I saw other users having the same problem, but didn't see a solution anywhere...

Finally, whenever I boot, the fsck utility runs (if I don't skip the "checking drives" part of bootup). While it runs, during running the maintenance shell with:
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found

I found one solution is to run fsck off the boot cd, which I'll try as soon as my friend gives me back my boot cd...

EDIT: erp...found another problem. My wireless card (Intel WiFi 5300) is getting relatively slow connection speeds even with good signals. My friend's wireless is getting a full 54Mbps, while I'm only getting 18Mbps (at the moment). Any ideas? (followed the howto on getting the 5300 card working)

Thanks in advance!

---

### Post by merlin_0525 on 2008-09-09
Alright, really confused now...I'm getting a 48Mbps speed now (moved to a different location) - still not 54Mbps, like my friend sitting next to me (also running HH).

I've also just noticed that my power button doesn't pop-up the quit screen like its supposed to(Using KPowerSave).

---

### Post by merlin_0525 on 2008-09-10
I'm going to ignore the wireless speed problem for now (and wait for 8.10 to be released, which apparently supports the 5300 card), since it seems I am getting a connection, just not always a fast one.

Any pointers regarding the fingerprint reader and undervolting?

Also, regarding the power button - I noticed a few more buttons on my computer aren't being recognized (As in, when I press the combination in "keyboard shortcuts" the key doesn't register as a pressed button) Examples include the power button, fn+F4 (sleep button), and the third hotkey button above the keyboard i have (the first two are recognized and customizable).

---

