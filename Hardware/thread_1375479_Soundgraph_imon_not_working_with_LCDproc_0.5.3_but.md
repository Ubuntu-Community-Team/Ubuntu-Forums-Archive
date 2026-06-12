---
title: "Soundgraph imon not working with LCDproc 0.5.3 but did on 0.5.2"
date: 2010-01-07
forum: Hardware
---

### Post by jfenton78 on 2010-01-07
I have a Antec Fusion case which has the Soundgraph iMon VFD and IR. The VFD shows up as ffdc when I do a lsusb. Here is that output:

Bus 002 Device 005: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller

Now here is the problem. On Mythbuntu 9.04 with a fresh install of LCDproc 0.05.2 all I had to do was change the driver in LCDd.conf to imon. After a restart of LCDd the VFD worked fine. 

In Mythbuntu 9.1 with a fresh install of LCDproc 0.5.3 and using the same procedure the VFD does not work. Can anyone help me troubleshoot this? I've already tried copying the LCDd.conf from 9.04 to 9.1 and it doesn't work.

---

### Post by regebro on 2010-05-03
It worked for me in 9.10, but not in 10.04. No errors, just a blank screen. No hints from LCDd even with report level 5 on what could be wrong.

Any ideas of how to troubleshoot this would be appreciated.

---

### Post by regebro on 2010-05-03
In fact, I found it. It's the display type that isn't detected properly. A file with options in modprobe.d solved it:

[https://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10](https://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10)

---

