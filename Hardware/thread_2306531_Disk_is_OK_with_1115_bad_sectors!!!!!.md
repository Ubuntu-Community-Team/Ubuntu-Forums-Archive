---
title: "Disk is OK with 1115 bad sectors!?!?!?!?!?"
date: 2015-12-16
forum: Hardware
---

### Post by n.e.t.gallatin on 2015-12-16
**So I'm a bit confused, the SMART status of my disk is OK with over a thousand bad sectors!? So what’s up with the message?**

fsck comes back clean

```
e2fsck 1.42.9 (4-Feb-2014)
Multimedia: clean, 68339/218595328 files, 787406893/874354176 blocks

```

gdisk comes back clean

```
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): v

No problems found. 4062 free sectors (2.0 MiB) available in 2
segments, the largest of which is 2048 (1024.0 KiB) in size
```

** SMART data assessment:**

[ATTACH=CONFIG]266183[/ATTACH]

---

### Post by tgalati4 on 2015-12-16
This looks like a new disk.  Contact the manufacturer and get an RMA for a replacement.  Back up any important data, which is probably not much for only 6 days of use.  It's possible that shipping damage or just break-in wear is causing some sectors to not be read.  Depending on where you bought this disk, it could be a second-quality disk sold at a discount.  It runs, but does not meet specifications.

The disk is fine, until it is not fine.

---

### Post by weatherman2 on 2015-12-16
> **n.e.t.gallatin said:**
> **So I'm a bit confused, the SMART status of my disk is OK with over a thousand bad sectors!? So what’s up with the message?**

No problems found. 4062 free sectors (2.0 MiB) available in 2
segments, the largest of which is 2048 (1024.0 KiB) in size[/CODE]

** SMART data assessment:**

[ATTACH=CONFIG]266183[/ATTACH]

Please give the rest of the S.M.A.R.T. Attributes.  See the scroll bar on the right?  Scroll down to show the rest of the Attributes.

Some S.M.A.R.T. Attributes are anomalies, because their use depends on the manufacturer.  If they are "Pending Sectors" then I would be worried.

Also, what make/model is the drive?

I'd run the extended S.M.A.R.T. test (may take a few hours).

I usually use GSmartControl for doing S.M.A.R.T. stuff.

---

### Post by n.e.t.gallatin on 2015-12-16
[ATTACH=CONFIG]266191[/ATTACH][ATTACH=CONFIG]266192[/ATTACH]


bought 1/14/2014

[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16822236604"]WD Green WD40EZRX 4TB IntelliPower 64MB Cache SATA - OEM

[/URL]**Could it be software or hardware related? I've been having issues ever since I installed a iStar backpane, and started running Mint 17.**

---

### Post by weatherman2 on 2015-12-16
Oh, I have one of those drives.  That's a real error - probably a catastrophic failure.  You can verify that by running the Extended S.M.A.R.T. test or even the short one (which should take only two minutes).  You can run these S.M.A.R.T. tests with GSmartControl.  I would be very surprised if it passes the extended test with that many pending sectors.

I agree with tgalati4: RMA it if it's still under warranty - get your data off (if you can) and get it replaced.

---

### Post by n.e.t.gallatin on 2015-12-16
Thank You, It did fail

---

### Post by weatherman2 on 2015-12-16
Personally, I would wipe it too once you've copied your data off, before you send it back.  (Unless you aren't worried about the remote possibility of some hack at WD seeing it.)  It would be curious to see if wiping it gets rid of the pending sectors.  I've done that a few times to clear pending sectors, but you have over a thousand - doubt it would work.  I'd RMA it now no matter what.

You can wipe the drive - write zeros to it - easily once you're sure your data is off!!! - with this command:

```
sudo dd if=/dev/zero of=/dev/sdb bs=16M
```

BE CAREFUL with the dd command!  This assumes your 4TB drive is still at /dev/sdb - please make sure that's still the right device ID before issuing the command above so that you don't wipe the wrong disk!

That dd command will probably take about eight hours on a 4TB drive, so it's something to launch before you go to bed.  If you do it, again I'd check the number of pending sectors one more time before you send it back, just to see if the number went down, up, or stayed the same.

---

