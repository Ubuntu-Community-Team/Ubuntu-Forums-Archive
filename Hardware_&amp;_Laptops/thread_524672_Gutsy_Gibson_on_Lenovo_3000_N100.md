---
title: "Gutsy Gibson on Lenovo 3000 N100"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by rfdparker2002 on 2007-08-13
Last night I upgraded to [development] Gutsy on my Lenovo 3000 N100, which I purchased about 6 months ago from The Linux Emporium, which I have since upgraded to Edgy, then Feisty, now as I said the Development version of Gutsy Gibson, so I thought I would post my experience of doing so.

Now as this is a development release I expected to run into a fair few troubles with hardware in software at the early stage, anyways, here are the problems I've had, if anyone can help with them it would be much appreciated:
[LIST]
[*]There appears to be a problem with OpenOffice.org in which even though I have the both versions 5 and 6 of Sun's JRE and also FSF JRE installed OpenOffice.org does not list anything in it's Java settings (Tools> Options> OpenOffice.org> Java). I can't work out why it's not finding the JRE installs.
[*]Part way through boot-up, even though my CD/DVD drive is empty it is checked every 5 seconds and this continues indefinetly and also CPU usage is high, top reveals the offending process to be udevd, which if I kill cpu usage drops and the CD drive stop checking, but has the adverse effect of not allowing any new devices to be connected, this is probably the worse problem I have and I can't find a way to fix it
[*]In the new version of Rhythmbox sounds in music become distorted at the 'loudest' parts of the tracks, this is not the case in any other program (e.g: totem, of which mine is the xine-lib) or in rhythmbox with the 'crossfading backend', but that backend seems to make the program less stable.
[*]The new tracker tool which I only found out about by looking around in top seems to suffer from the same problems as beagle in terms of high cpu usage in indexing, and also I can't seem to find a way to set a shortcut key for the search window
[*]Also if I don't kill udevd not only does it usage a large amount of cpu power, but the cpu which is usually 48-61 C reached 77 C
[*]All my screen fonts were very large to begin with, which I managed to track down to the dpi setting itself to about 123 which I put back to 96
[*]I'll edit this post if I find/remember any more problems that weren't present in feisty
[/LIST]

So if any one can help me with either OpenOffice.org Java or the CD/DVD drive problems it would be much appreciated

---

### Post by rfdparker2002 on 2007-08-14
Hello is there anyone who knows how to fix my udevd problem, or is it a known bugs, I do have the latest updates installed and still the problems occurs

---

