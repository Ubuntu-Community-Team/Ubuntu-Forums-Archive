---
title: "100% CPU + Crackly Sound"
date: 2005-01-02
forum: Hardware &amp; Laptops
---

### Post by spartas on 2005-01-02
I am running ubuntu on my dell 8200 machine (this is a Pentium 4-m processor), and I have finally gotten it to run at 100% of the CPU (1.9Ghz).  I added speedstep-ich to /etc/modules, however now I have an even large problem.  When I unplug the ac from the system when it's running the screen goes black for a few seconds, then comes back on, but the CPU is still running at 100%.  I'm thinking that I have to edit an acpi file, like power.sh or ac.sh or something, but I have only been using ubuntu since September, so I don't know where this file is located, nor what I need to add/delete/modify in the file. I guess I'll remove speedstep-ich from /etc/modules until I find a way for it to work.

Secondly, I have also gotten ALSA to work now, but the sound is very crackly.  I have no clue where to begin with this problem.

Please respond to me if you have any suggestions.  I really would like for my speedstep to be working properly.

---

### Post by beefsprocket on 2005-01-02
Methinks (and I could be totally wrong here) that you should check to see what APM modules are loaded. ACPI and APM don't get along very well on my 8000. I think that ACPI overrides APM but hey, my 2 cents anyways.

---

