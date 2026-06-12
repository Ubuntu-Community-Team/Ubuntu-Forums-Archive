---
title: "Vista/Ubuntu dual boot partitioning"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by andrewpmk on 2008-12-16
I got a new Toshiba Portege M800 laptop with Windows Vista Home Premium on it. I would like to set up a Vista/Ubuntu dual boot.

However, the partitioning is very weird. There are 4 partitions, as follows:

/dev/sda1: 1572 MB
/dev/sda2: 232500 MB
/dev/sda3: 8756 MB
/dev/sda4: 7227 MB

I presume that /dev/sda2 is the main Windows partition. The others are probably recovery partitions of some sort.

How do I resize the Windows partitions and install a Ubuntu dual boot?

---

### Post by iaculallad on 2008-12-16
Just to be sure that /dev/sda2 is really your vista partition, you could input the command below on your terminal while booted on your LiveCD.

```
fdisk -l
```

Use GParted to adjust the size of a partition to accommodate Ubuntu.

---

### Post by codedash on 2008-12-26
Hi there. Happy holidays.
Did portege work out of the box??
I am between a toshiba u400 laptop with x3100 graphics vs portege m800 with GMA 4500MHD and put ubuntu 8.10. Any thoughts?

---

### Post by strohmi on 2008-12-31
> **codedash said:**
> Hi there. Happy holidays.
Did portege work out of the box??
I am between a toshiba u400 laptop with x3100 graphics vs portege m800 with GMA 4500MHD and put ubuntu 8.10. Any thoughts?

I've got a Toshiba Portege M800 and I've installed Kubuntu 8.10 yesterday. Seems to work fine out of the box. WLAN, graphics (despite of the GMA 4500 chipset) even the camera seems to be OK.

I only see one problem: KDE (or KDM or the XServer?) is restarting after working some time with the machine. Some popups are displayed saying "Your monitor setup has changed" and asking to accept or ignore the changed monitor setup (while actually nothing was changed). Then the screen goes blank and I have to re-login to KDE. All windows are closed of course and unsaved data is lost:-(

I've then disabled the HDMI port in the BIOS and now it works more stable. Nevertheless I've seen the problem once but after beeing able to work for a longer time than before.

BR
Strohmi

---

