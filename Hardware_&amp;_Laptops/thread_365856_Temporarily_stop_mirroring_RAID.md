---
title: "Temporarily stop mirroring RAID"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by el3ktro on 2007-02-20
Hello,

I hope somebody can help me. I have a computer with two harddisks, both are configured in a mirroring RAID setup, running SuSE. I want to replace both harddisks with larger ones, and install Ubuntu. The problem is, there are only two harddisk slots available. So what I was thinking is this:

Shutdown, remove the old harddisks, put the new ones in and install Ubuntu with RAID enabled. Now the tricky part: I have to remove one of the new harddrives and put one of the old ones in, so I can copy all relevant data over. But of course I DON'T want this old harddisk and the new harddisk start to mirror to each other, so I would have to somehow temporarily disable the RAID mirroring. After I have copied everything over, I would shutdown, put the second new harddrive in, turn the compuer on again and enable the RAID mirror, so that all the data that I've just copied will be mirror to this second new harddisk.

Is this possible somehow? Can I somehow temporarily disable or stop a RAID, and after a while tell the RAID to start mirroring again?

---

### Post by Redeyes_Gambit on 2007-02-20
First of all, what are you using for RAID? Is it hardware RAID or software (fake) RAID? Were you using dmraid in SuSe?

---

### Post by el3ktro on 2007-02-20
It's software. The drives are partitioned as "RAID auto detect" and I have configured the RAID devices in /etc/raidtab. I'm still thinking about an easier way to accomplish this, but as I said the server (19") has only two drive slots.

Tom

---

### Post by Redeyes_Gambit on 2007-02-21
Hm. When you boot an Ubuntu live CD does it detect the two RAID drives? What is the output of "fdisk -l" (that is an "L" by the way, not an "i" ;-) ?

---

### Post by el3ktro on 2007-02-23
I can't test that until the weekend, it's a productive server. Is there a way to temprarily stop a RAID, without destroying it? I mean in a mirroring RAID, the purpose is that if one drive fails I can remove it and add a new one. So I should be able to tell the RAID to abandon one of the harddisks, or not?

---

### Post by Redeyes_Gambit on 2007-02-23
I'm not entirely sure. I mean yea, it would be logical that one could reconstruct an array and pause and such since that IS kinda the whole point lol. However, I myself have been having RAID issues and wanted to make sure Ubuntu can *see* your array controller/disks. Knowing whether or not mirroring can be paused is moot if Ubuntu can't see your array ;) .

I have a running thread trying to diagnose my problems with RAID if you'd care to take a look:

[http://www.ubuntuforums.org/showthread.php?t=367167](http://www.ubuntuforums.org/showthread.php?t=367167)

---

