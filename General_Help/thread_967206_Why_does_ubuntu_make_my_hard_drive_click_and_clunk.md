---
title: "Why does ubuntu make my hard drive click and clunk?"
date: 2008-11-01
forum: General Help
---

### Post by ubnewbie2 on 2008-11-01
It started doing it under 8.04 (I don't remember it doing it under 7.10), and is still doing it under 8.10 - although it's a bit different - maybe slightly less often now.

---

### Post by damis648 on 2008-11-01
Are you using a laptop?

---

### Post by HittingSmoke on 2008-11-01
> **ubnewbie2 said:**
> It started doing it under 8.04 (I don't remember it doing it under 7.10), and is still doing it under 8.10 - although it's a bit different - maybe slightly less often now.

Define "clunk". Is it like a clattering sound? If you get the room quiet and watch your HDD light do they sync up?

---

### Post by ubnewbie2 on 2008-11-01
> **damis648 said:**
> Are you using a laptop?

No

---

### Post by ubnewbie2 on 2008-11-01
> **HittingSmoke said:**
> Define "clunk". Is it like a clattering sound? If you get the room quiet and watch your HDD light do they sync up?

Sounds like it's going into standby and parking the heads or something. A metallic clunk, a bit rattly (quite a bit unnerving).  It certainly does it while the HD light is flickering away, but I actually have 2 drives and no way of telling if it's both drives, or whether it is accessing the other drive when one of them clunks (or clicks).

---

### Post by russlar on 2008-11-01
Install the smartmontools package, and run sudo smartctl -H /dev/sd*. This will give you a health rating of your drives, provided they support SMART.

---

### Post by OrangeCrate on 2008-11-01
Please make sure you have all of your important files backed up. I've heard sounds like that before. Right before the drive failed. I hope that not the case for you, and it's something else, but it's better to be safe than sorry at this point.

---

### Post by ubnewbie2 on 2008-11-01
> **russlar said:**
> Install the smartmontools package, and run sudo smartctl -H /dev/sd*. This will give you a health rating of your drives, provided they support SMART.

Both pass

It reports

```
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

---

### Post by ubnewbie2 on 2008-11-01
> **OrangeCrate said:**
> Please make sure you have all of your important files backed up. I've heard sounds like that before. Right before the drive failed. I hope that not the case for you, and it's something else, but it's better to be safe than sorry at this point.

It is too coincidental that it started when I upgraded ubuntu last time, and has changed with this upgrade - and it actually seems better now than it was.

---

### Post by Stoodle on 2008-11-01
Yeah, I have the same problem. My external hard drive's been doing this for a while. It's a 500 GB Seagate. I don't think it'd be failing because I got it last year I think and the hard drive in my computer that I got in 2002 still works. My external drive doesn't clunk but it makes a higher pitched tick sound. It reminds me of a cricket chirping but only for a split second and it's every couple minutes.

---

### Post by ubnewbie2 on 2008-11-01
Seems like a known bug 

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

what a mess, and it doesn't look like it's fixed

---

