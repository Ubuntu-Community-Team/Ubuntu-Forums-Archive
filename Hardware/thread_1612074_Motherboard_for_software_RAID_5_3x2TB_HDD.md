---
title: "Motherboard for software RAID 5 3x2TB HDD"
date: 2010-11-02
forum: Hardware
---

### Post by robertfitzroy on 2010-11-02
I was asked to set up an economic but effective data backup system. As such, I planned to use an old Dell PowerEdge 700 Server with a RAID 5 configuration. I ordered three 2TB WD caviar black HDDs to swap into it. Afterwards, I found out that the RAID Controller in the Dell only supports drives up to 1TB in size.

I don't have the budget for a whole new controller card ($300-$600), so I want to put them into a software raid 5 using ubuntu, but I'll need to purchase a new motherboard (hopefully $100-$200). I'm struggling to identify a good motherboard. I'm not sure what specifications I should be looking for. Here are a few questions I've come across:

1. Should I avoid a motherboard with built-in raid (since I'll be using software raid anyway)?

2. Is there any way to modify the configurations of RAID 5 to lengthen the HDD failure time? This is due to the fact that WD Caviar black drives have the deep state recovery, and most hardware raid cards will fail the HDD after 7 to 15 seconds, while the recovery can take up to 2 minutes. Hence, is there any way to make the RAID wait longer?

3. Is the current Ubuntu HOWTO applicable to Ubuntu 10? ([https://help.ubuntu.com/community/Installation/SoftwareRAID#Configuring the RAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID#Configuring the RAID"))

4. In software raid, will I have trouble with the size of the drives or the total size of the array? Also, will Ubuntu be able to handle a 4TB drive (3x2TB in raid 5)?

---

