---
title: "Alienware m9750 and Ubuntu 7.10 ?"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by TDK800 on 2007-10-29
Has anyone run Ubuntu 7.10 on Alienware m9750? I'm wondering about compatibility with the solid state hard disks.

---

### Post by fidelisprivatus on 2007-11-14
I am wondering the same thing.  Has anyone tried?

---

### Post by hannestum on 2007-12-15
Got Alienware m9750 with 2 x 160GB RAID0

Gutsy live CD boots without Errors, but I'm not able to install it because gparted isn't able to detect the partitions right. (Although I'm using dmraid)

So If anyone manages to get the installation done on the same configuration, please tell me...

---

### Post by kneehighspy on 2008-01-20
well i just decided to try to install 7.10 on my m9750.  i've got 7.10 installed on a test hard drive (an external 20gb usb / sata).  did all the partition creations manually and have 7.10 booting and running via the external hd.

issue i have going now is finding all the drivers and get the system completely working.  the default drivers see my Intel PRO/Wireless 3945ABG adapter, allows me to semi configure the adapter.  i can see my routers ssid, but it sees it as a protected network and i don't have wep or wpa enabled and i'm using auto channel scan, 11g and 11b mixed mode without super g enabled, and visibility enabled.  i'm using mac address filtering, but as i mentioned, everything works fine in windows.  i also have my 360, wii and ps3 connected wirelessly along with 2 psp's, 2 nds lites, apple iphone, wifes dell laptop, daughters acer laptop, everything as mentioned wireless.  so for now i can't get it to connect to my network (dlink dgl-4300).

everything works fine in xp and vista on my laptop (well its windows, 'fine' can be any definition).

but if you guys are still interested in findings, i'm gonna download all the drivers and try to get 7.10 working tonight / tomorrow. and if interested, i'll post what my findings are.

---

### Post by Bheath3 on 2008-02-01
I just installed Ubuntu on my Alienware M9750 yesterday. I am very new to Linux so I am having some issues of course. I am running a Core 2 Duo 2.0 GHz, 4 GB RAM, Dual Geforce Go 7950GTX's, and Raid 0 on duel WD Scorpio HDD's. The first issue I ran into was the Raid partition. I had to delete the Raid and then turn Raid off in the BIOS settings. That brought up the issue of Vista not seeing any drive to install on. Well Vista is horrible anyways so I went back to XP with no issues at all. Once I had XP on one drive I popped in the Ubuntu disk and I was all set. Raid is disabled so I have two 232 GB partitions. No issues during the Linux install or the updates. Wireless works fine so far along with both video cards in SLI mode.  The one issue I am still having is the sound card. I have sound with headphones or a speaker plugged in but nothing from the laptop speakers at all. I have been going through all the posts trying various things and nothing yet. But, like I said I am very new to Linux so I do not know any of the commands and the whole terminal thing still throws me as I have only ever used Windows. I will update my post when I figure out whats going on with the sound issue. If you have any questions specific to the M9750 let me know and I will do my best to help as much as I can.

---

### Post by Rashind on 2008-02-29
Bheath3, 

Are you trying to use an external sound card?  (For instance, the x-fi card that you plug in?)

If so, you might need to disable your on-board sound in the system's BIOS to get Ubuntu to recognize the card properly.

---

### Post by Alienwarem9750 on 2008-05-05
The biggest issue it seems is the raid setup on the m9750. 

did anybody here work their way though this HOWTO Guide?

[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto")

I'm in the process now so I will update this when I haev a result.

EDIT:

Or this?
[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation](http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation)

---

### Post by Alienwarem9750 on 2008-05-21
Success :):):) 

Worked my way through that second guide and got there in the end.  

(I actually did it with a Raid1 setup as I have already had 1 HDD Fail and I don't want to be rebuilding this again like last time)

---

