---
title: "Suspend script?"
date: 2009-02-15
forum: Hardware
---

### Post by AVeryLongNickname on 2009-02-15
Hi! 
I've got two problems with Suspend on my Acer Aspire One.

The first is that in Xubuntu my suspend button don't work. that is, when i select suspend from the shutdown menu, the laptop enters suspend mode, but when i press the suspend button nothing happens.

The other problem is my wifi. It works great with the MadWifi hal driver. but after suspend i have to run 
```
sudo madwifi-unload
sudo /sbin/modprobe ath_pci
```
to get my wifi running. 
Are there any scripts running every time the computer enters/exits suspend that i can add those commands to?

Thanks a lot for any help! =)

---

