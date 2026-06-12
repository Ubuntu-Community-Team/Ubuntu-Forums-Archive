---
title: "SSD drive &amp; TRIM"
date: 2010-04-17
forum: Hardware
---

### Post by loseby on 2010-04-17
Will be going to Lucid Lynx and was wondering if it will support TRIM in SSD's ?

Are there any programs that run in Linux to clean up SSD's ?

---

### Post by loseby on 2010-04-18
Anyone know if next version of Ubuntu will support the TRIM feature in Solid State Drives ?

ATM Win7 has this feature and hoping LL will have it to .


Anybody have any ideas ?

---

### Post by robbel on 2010-04-30
TRIM is not (yet) available in 10.04: [https://bugs.launchpad.net/bugs/571476](https://bugs.launchpad.net/bugs/571476)

---

### Post by nhasian on 2010-04-30
all you need to do to enable TRIM is to install the Linux Kernel 2.6.33 or higher from: 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by loseby on 2010-05-01
have decided to put 10.04 on a separate sata drive and just keep win7 on the ssd

---

### Post by gmrple on 2010-07-14
> **nhasian said:**
> all you need to do to enable TRIM is to install the Linux Kernel 2.6.33 or higher from: 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Hi, I just recently installed an SSD and came across this guide: [ Tuning Solid State Drives in Linux (page 2). ]("http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/2/") Is it necessary to add the discard option to fstab (my fstab lacks that line completely) or will the 2.6.33 kernel automagically detect that I have a SSD that supports TRIM and enable it?

---

### Post by nhasian on 2010-07-14
in addition to the newer kernel you need to add the discard option to your /etc/fstab

---

