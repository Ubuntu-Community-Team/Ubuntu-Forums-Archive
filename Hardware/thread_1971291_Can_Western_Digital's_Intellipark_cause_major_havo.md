---
title: "Can Western Digital's Intellipark cause major havoc?"
date: 2012-05-02
forum: Hardware
---

### Post by RedPenguin on 2012-05-02
Just to lay some ground work I have the following:

A Compaq Presario F739WM Laptop that has an NVidia MCP51 SATA Controller.

It had originally a Hitachi 160GB SATA 1.5Gbs, then a 160GB Samsung Drive, now finally a WD Scorpio Blue WD10JPVT 1TB SATA 3.0Gbs.

Now before I learned about Intellipark, I was having errors from "Hard Drive Mismatch" during attempting install to random "EXT4 - Failed Inodes".

Even Windows 7's Hard Drive Sentinel was telling me the hard drive could be failing.

Yet I used the famous WDIDLE3 utility and it seems now that no matter how hard I try I can't get Ubuntu 12.04 OR Windows 7 to report problems.

Could all of this seriously be cause by an 8-second idle drive head parking? I mean I've read here and other places it can cause major lag and hard drive premature death, but nothing mentioning crashes.

---

### Post by ahallubuntu on 2012-05-02
Look at the S.M.A.R.T. report from the drive:

```
sudo smartctl -a /dev/sda 
```

and look in particular at the Load Cycle Count (or Load/Unload Cycle count).

---

