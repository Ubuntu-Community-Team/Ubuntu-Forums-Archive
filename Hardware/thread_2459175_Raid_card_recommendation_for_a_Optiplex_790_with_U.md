---
title: "Raid card recommendation for a Optiplex 790 with Ubuntu Server"
date: 2021-03-12
forum: Hardware
---

### Post by remag03 on 2021-03-12
I'm wanting to run an website off of this Dell Optiplex 790 MT and that's more or less the easy part I can get the website up easily with apache and wordpress. But the problem lies in that my Dell Optiplex 790 doesn't support raid in the Bios. 

I am new to Linux and for example it took me a long time to figure out how to program the onboard NIC to change the IPv4 address.

So if I get a raid card for my 790 and am running Ubuntu server can anyone recommend a card that would support raid 10? Also I am not entirely sure how LVM works yet but I feel that I am going to need a raid card to work with it.

---

### Post by CelticWarrior on 2021-03-12
You don't need any RAID card to work with [LVM]("https://wiki.ubuntu.com/Lvm").
You may also want to take a look at [SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID").

---

### Post by remag03 on 2021-03-12
> **CelticWarrior said:**
> You don't need any RAID card to work with [LVM]("https://wiki.ubuntu.com/Lvm").
You may also want to take a look at [SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID").

I see what you are saying after checking those links

---

### Post by TheFu on 2021-03-12
+1 for using Linux Software RAID or LVM if you can.

HW-RAID has a number of downsides.
Fake-RAID (usually included in motherboards and some really CHEAP RAID cards) has all the negatives that HW-RAID has AND all the negatives that SW-RAID has.

---

