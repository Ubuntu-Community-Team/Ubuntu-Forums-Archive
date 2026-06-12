---
title: "Intel 3945 -&gt; Tried installing iwlwifi through backports - killed sound/wifi"
date: 2008-05-15
forum: Hardware
---

### Post by chickan on 2008-05-15
I've been having wireless issues with my Acer 5610 laptop with an Intel 3945abg wireless chip.  Since installing Hardy, the wireless worked out of the box initially, however, after about 3-4 minutes of use, it stops working and I have to reconnect to my wireless network to get it working again.  Was quite annoying, so I search for answers here on the forums.  

Following several suggestions, I installed the linux-backports-generic-hardy package, and upon rebooting, the restricted iwlwifi driver was in use as the threads said.  However, now my wireless did not work at all.  It still showed up using "iwconfig", however even setting the essid manually through iwconfig, it would not connect (or even see) my wireless network.  
To add insult to injury, now my sound stopped working.  The volume icon had a slash through it, and clicking on it gave an error message.  Under sounds, changing through Alsa to OSS to Autodetect, clicking Test gave errors on all of them.

So I unistalld the backports drivers, rebooted, and now iwconfig shows no wireless card at all, and neither does network manager.  Sound also still does not work.  Rebooted into windows, everything works there (posting from it).

Any thoughts?  Suggestions?

On a side note, I've noticed that if I let my laptop sit idle for a minute or so, it hesitates really bad, almost like it was asleep or something, even when though the screen never turned off or anything.  Anyone else experiencing this?  This did not happen under Feisty (skipped Gutsy release for my laptop).

---

### Post by balagosa on 2008-05-16
hmm...not that i know of. i didnt experience this, well i never did mess with the linux-backports.

not that this might help, but ever tried reinsalling your kernel from synaptics?

---

### Post by chickan on 2008-05-16
no, I haven't tried that yet, but I'll try that tonight.  Other suggestions?  I really don't want to reinstall, but it looks like I might have to.

---

