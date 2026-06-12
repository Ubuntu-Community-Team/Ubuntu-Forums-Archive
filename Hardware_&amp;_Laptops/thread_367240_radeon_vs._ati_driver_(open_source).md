---
title: "radeon vs. ati driver (open source?)"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by linuxaz on 2007-02-21
Hello,
I was just trying out the new Feisty herd 4 on my DV 8040us laptop with an ATI 200m video card.

I'm wondering what the difference is between the radeon driver (that I use with SuSE 10.2), and the one that I found being used by this version of Ubuntu called "ati"?

I have been unable to install the fglrx driver in SuSE, so I'm using the radeon driver at the moment.

So, what's the difference?

Thanks,

linuxaz

---

### Post by ctt1wbw on 2007-02-22
I'm not using Feisty yet, but the propreitary ATI driver that you get off the ATI webiste is the fglrx driver, I think???  And the ATI/Radeon driver is the open source one.  

I have the XPress 200m and had to use the ATI propreitary driver to get beryl working.  The open source driver woudln't work at all.

---

### Post by linuxaz on 2007-02-22
Ok,
I found the answer myself.  "ati" is a small wrapper that is used to detect the proper driver for Xorg to use such as "radeon" or others for the ATI video cards.  I've never seen SuSE use it before, so was curious.

linuxaz

---

### Post by linuxaz on 2007-02-22
ct,
I'd like to know what "how-to" you followed to get it working!

linuxaz

---

### Post by ctt1wbw on 2007-02-22
I followed this one:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I downloaded the driver from ati and followed the instructions for use in Edgy.  :)

---

