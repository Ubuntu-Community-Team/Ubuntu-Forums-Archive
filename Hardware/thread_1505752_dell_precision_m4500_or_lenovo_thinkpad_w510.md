---
title: "dell precision m4500 or lenovo thinkpad w510?"
date: 2010-06-09
forum: Hardware
---

### Post by tgomas on 2010-06-09
I'm looking for a new laptop and my choice will probably be one of them.
Does anyone have some experience running ubuntu on them?

---

### Post by progfrog on 2010-06-11
I got a M4500. It seems to run off the Live CD. But once Ubuntu is installed, I run into this showstopper:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/556856](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/556856)

---

### Post by progfrog on 2010-06-23
It appears that the nouveau bug I cited earlier is not the only culprit. When installing onto the Dell Precision M4500, be careful about how you partition your drives, in particular if you have a minicard SSD HD, because of this:

[http://support.dell.com/support/topics/global.aspx/support/dsn/document?c=us&l=en&s=gen&docid=88C044B94A5A73A6E040AC0A65E92ECD&journalid=87F88EC84E8B1B58E040AC0A66E935CA&Query=&SystemID=&ServiceTag=&contenttype=-1&os=-1&component=-1&lang=-1&doclang=en&toggle=false]("http://support.dell.com/support/topics/global.aspx/support/dsn/document?c=us&l=en&s=gen&docid=88C044B94A5A73A6E040AC0A65E92ECD&journalid=87F88EC84E8B1B58E040AC0A66E935CA&Query=&SystemID=&ServiceTag=&contenttype=-1&os=-1&component=-1&lang=-1&doclang=en&toggle=false")

I repeatedly got blank screens after booting. The problem was not the nouveau bug, but that the boot device couldn't be found because of this BIOS problem. Once I realized, I reinstalled and set the boot to the main HD, plus the nouveau workaround. Now I got Lucid working on the M4500. All is fine; just some minor glitches with the touchpad.

---

### Post by Chris T on 2010-11-13
If it is still of interest, I have a W510 and I am quite happy with it.  My experience is reported [here]("http://math.umons.ac.be/an/W510/").

---

### Post by bachor on 2011-10-14
> **Chris T said:**
> If it is still of interest, I have a W510 and I am quite happy with it.  My experience is reported [here]("http://math.umons.ac.be/an/W510/").

 wow Chris,

there is some useful informations on your web. I have W510 i5 m520,nVidia FX880M, 15.6 HD+,and just installed Xubuntu 11.04-32bit. I made Recovery DVDs, shrinked Win 7,made LVM and Xubu 11.04. Although I put Grub in MBR.

 I was wondering how different my install would be since I used newer Ubu distro. Is it big difference with 64bit version? 

 How do I find [which command] if all those extras such as Wifi,Bluetooth,USB3,Webcam,Audio,SDHC,Fingerprint,etc. works in my install? 

 Could you help newbie bit? thank you

---

