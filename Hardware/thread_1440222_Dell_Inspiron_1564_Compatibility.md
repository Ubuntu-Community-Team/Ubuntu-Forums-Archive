---
title: "Dell Inspiron 1564 Compatibility?"
date: 2010-03-27
forum: Hardware
---

### Post by arcelios on 2010-03-27
I'm looking at buying a [Dell Inspiron 1564]("http://www.dell.com/us/en/home/notebooks/inspiron-1564/pd.aspx?refid=inspiron-1564&s=dhs&cs=19&redirect=1"), and I was wondering if anyone has had any experience with it?

If this would be a bad choice of laptop hardware, could anyone suggest a more Ubuntu-friendly one?

---

### Post by ritendragoel on 2010-04-20
couple of weeks back i purchased dell inspiron 1564. It is supporting only windows 7. for ubuntu user it will support only 10.04 64 bit amd version. lower versions it will not support. moreover it start hanging once you run more than application in ubuntu. laptop slow down if you connect external hard disk.

---

### Post by kevein on 2010-12-25
I have a Dell Inspiron 1564, With 2 operating systems installed windows7 and Ubuntu 10.10, everything going nice, but problem that wireless card not detected and I don't know how to configure it.

---

### Post by shashank86 on 2011-02-06
I have a 1564 with win7 and maverick dual boot. Everything seems to be fine except for the occasional glitches in the display and mousepad. In fact i am searching for those solutions here.

---

### Post by TBABill on 2011-02-06
My 1564 works beautifully. I have the Core i3-330m with on-chip Intel GPU. The ONLY thing I have to do is enable my Broadcom BCM4312 wireless by installing firmware and driver. Very easy though. Simply ```
sudo apt-get install --reinstall bcmwl-kernel-source
``` or take the easy way and just go to SYSTEM>>ADMINISTRATION>>HARDWARE (or ADDITIONAL DRIVERS) and select the STA driver.

---

