---
title: "Linux software RAID (mdadm) or DM-RAID ?"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by darrenm on 2009-08-16
Hi. I have a mainboard with SATA RAID (like many people now I assume). I have 2 identical disks and due to fakeraid not being the best supported in Linux I used the better option at the time of installing using md Linux software RAID. 

This has been working fine for the last couple of releases, dist-upgrading each time until a couple of days ago where the update to Karmic has stopped my md arrays from working. All the Karmic installation media seem to be able to set up is DM-RAID and will only see my 2 disks as one, even though I have them configured in the BIOS as single IDE disks.

My question is - is DM-RAID now the assumed way that people will use RAID on fakeraid SATA controllers? I was always under the impression that mdadm was the preferred best solution for software arrays in Linux but that doesn't seem to be the case anymore.

---

### Post by haider_up32 on 2009-08-17
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

having few problems mounting partitions

---

