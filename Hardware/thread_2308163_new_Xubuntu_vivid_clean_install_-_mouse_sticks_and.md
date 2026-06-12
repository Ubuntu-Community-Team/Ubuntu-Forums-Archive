---
title: "new Xubuntu vivid clean install - mouse sticks and freezes"
date: 2015-12-31
forum: Hardware
---

### Post by idee on 2015-12-31
Happy New Year!

  I have a clean new install of Xubuntu vivid.  The mouse cursor randomly "sticks", freezes and disappears over open app panes.  Specifically over buttons or input sections.  Are there any settings l can change?  It is most frustrating.

 Thank you for the support.

---

### Post by v3.xx on 2015-12-31
Have you updated your system since you installed?

How much ram do you have and what kind of graphics are you running?

---

### Post by idee on 2015-12-31
Installed it last night, and allowed it to update as the first step after install, so yes.

Graphic?  Video cards?  Nvidia Quadro NVS 290 & GeForce GT 200

4 g ram

---

### Post by v3.xx on 2015-12-31
Try running this code when the mouse is freezing up.

```
dmesg | tail -f > ~/Desktop/dmesg.txt
```

This will output a text file to your Desktop.

---

### Post by idee on 2016-01-01
Here is what it showed.  By the way.  It is a pretty constant frustration.  Thanks for the help.

> [   22.468227] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   22.468228] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   22.468230] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   22.468233] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   22.468234] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   22.468236] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   22.468238] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   22.681866] 8139too 0000:07:09.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   24.967422] vgaarb: device changed decodes: PCI:0000:20:00.0,olddecodes=io+mem,decodes=none:owns=none
[   24.967427] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem

> **idee said:**
> Here is what it showed.  By the way.  It is a pretty constant frustration.  Thanks for the help.

those smilies should be "=none : owns=" without the spaces.

Additional note, when it freezes, it also pretty much freezes out the whole desktop until it lets go.

And again

> [   31.640138] ata2.00: configured for UDMA/100
[   31.648950] ata2.01: configured for UDMA/133
[   31.648976] sd 1:0:1:0: [sdc] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   31.648980] sd 1:0:1:0: [sdc] Sense Key : Medium Error [current] [descriptor]
[   31.648983] sd 1:0:1:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
[   31.648985] sd 1:0:1:0: [sdc] CDB: 
[   31.648987] Read(10): 28 00 0a 40 25 10 00 00 f8 00
[   31.648996] blk_update_request: I/O error, dev sdc, sector 171976120
[   31.649011] EXT4-fs error (device sdc2): __ext4_get_inode_loc:3795: inode #2759036: block 11010487: comm lightdm-gtk-gre: unable to read itable block
[   31.649012] ata2: EH complete

---

### Post by Bucky Ball on 2016-01-01
Just throwing this in. I would stop this pursuit and forget about Vivid 15.04. It has less than a month's support left (EOL late-January) at which time you are going to need to upgrade to or clean install 15.10 anyway. 

My suggestion? Install 15.10 now and save yourself some time and effort. Who knows? 15.10 may install without issue. Good luck. :)

---

### Post by idee on 2016-01-02
A bit more background.  I have been around Linux for a bit (since OS2 Warp).  No expert, but familiar.  I have been using SuSE since the late 90's. It used to be super solid.  The latest versions have been challenging to say the least.  I have friends that love Ubuntu, so after a bit of digging and reading I have decided to make the change.  To be honest I am so tired of chasing the ever moving target of updates.  All I want is a solid distro that I can make home.  I don't know what the issue is with my mouse in Xubuntu, but I think it is XFCE.  I used and was pleased with that years back, but saw something similar for a time.  The past few years I have been using LXDE on openSuse.  I downloaded 15.10 Lubuntu today.  I will reinstall with that and see if we can call it good.  I am hoping to call this side of the Linux world home.  Sorry for the long post and thanks for the help.

---

### Post by Bucky Ball on 2016-01-02
All good. See how you go with 15.10. As well as longer support it is upgradeable mid-2016 to the next long-term support release, 16.04 LTS, where hopefully you can live for a few years. Xubuntu LTS releases have three years support, Ubuntu five. When 15.10 runs out of steam (interim releases have nine months support) you can hit the LTS and stay there.

---

### Post by idee on 2016-01-02
Thanks Bucky.  Good to know.  I'm definitely new to the Ubuntu world and eager to learn.  

BTW - the Lubuntu solution worked.  I no longer have the mouse freeze issue.  

I have a few other questions as I get settled in, but that will be another post.  I am not sure how to mark this post closed.  It was really never solved, but is no longer an issue.


thanks again

---

### Post by Bucky Ball on 2016-01-02
Good news. :)

Yea, we don't have a 'resolved' button, which would be handy in situations such as this, but see the first link in my signature for how to use 'solved' instead. Marking it as such will not close the thread to further discussion. Good luck.

---

### Post by Bucky Ball on 2016-01-02
Good news. :)

Yea, we don't have a 'resolved' button, which would be handy in situations such as this, but see the first link in my signature for how to use 'solved' instead. Good luck.

---

