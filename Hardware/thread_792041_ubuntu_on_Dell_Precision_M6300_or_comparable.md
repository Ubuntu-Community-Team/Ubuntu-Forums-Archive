---
title: "ubuntu on Dell Precision M6300 or comparable"
date: 2008-05-12
forum: Hardware
---

### Post by t_e_r on 2008-05-12
Hi,

New to ubuntu, but have run Debian/testing on my laptop for a while.
I am deciding between Dell Precision M6300, or HP 8710w, or Lenovo T61P. Will try ubuntu (or a variant, don't know enough to figure out which one yet). I have searched this forum and the Dell support forums. There was a thread about success on the HP, however, later questions about the DVD drive went unanswered.
None of these machines are actually supported by the manufacturers for Linux. One of them is even explicitly unsupportive. The Dell forum here and the Linux forum at Dell seems to be restricted to the N series.
Hoping to get some clues ...

---

### Post by mcyouthmin on 2008-05-14
I've been running Ubuntu on an IBM t42 for a while and its been great. Just got a Precision M6300 today provided by work. Will be loading Ubuntu on it later today / tomorrow to see how it works out. 

I'll let you know, of course anyone else with experience on this particular platform would be great to hear from.

---

### Post by t_e_r on 2008-05-14
I just placed my order for an HP 8510w, with the ATI FireGL instead of the Nvidia Quadro FX 570m, thus avoiding a proprietary driver. This is a step down and back from the 8710w, which is the equivalent of the M6300. You get a price break and some space from the bleeding edge.
I will make a report on how this goes with Ubuntu. It might be good to collect all <?>Ubuntu experiences for this class of "mobile workstation" together?
Estimated ship date is not till the end of May though.

---

### Post by mcyouthmin on 2008-05-14
Out of all the Ubuntu installs I've done, this one was the easiest, and I also have the Nvidia chip installed. Everything worked like a champ. I installed the 64 bit of 08.04 on here. 

No tweaking, updating drivers, or trying to figure out what's not working necessary, although I'm sure the time will come. 

Good luck to you with your install.

---

### Post by t_e_r on 2008-05-15
Congrats! I just heard on the webvine that live Hardy Heron has problems with ATI cards. I may have to pay for that choice with some hair :roll:. Hope I can get help here when the time comes.

---

### Post by t_e_r on 2008-06-20
Well, I just lost my follow-up post here because I took too much time composing it and got logged out. So here's the brief version of it.

I installed the 64-bit desktop version on the HP 8510w. The installation went well, but I had weird problems trying to test things in the liveCD mode - freezes during boots and app launches.

I had to install the proprietary ati fglrx driver, because of weird artifacts with the FOSS driver. Other weirdness remain - a flickering gnome-screensaver (known but unsolved AKAIK from googling, and searching on these forums). Some java apps would have blank interiors for windows or boxes. I am guessing it could be a timing problem between different threads (on the CPU or GPU) drawing different parts of a composite. You need to run aticonfig if you want a particular external monitor setup - there is no desktop preference for that. Driving a HD monitor is no problem.

I could not remap the M$ key to an alt key to use in emacs, either via desktop preferences or xorg.conf. The desktop preference menu *does* cover all xorg.conf keyboard options, and there is no need to tweak under the hood. This is not particularly a Ubuntu quirk.

I have not tried the fingerprint reader, or the firewire. All other devices work as expected.

---

