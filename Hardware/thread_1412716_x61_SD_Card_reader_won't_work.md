---
title: "x61 SD Card reader won't work"
date: 2010-02-21
forum: Hardware
---

### Post by srilyk on 2010-02-21
Hi, I'm using ubuntu 9.10 on a Lenovo x61 tablet PC. My card reader has worked on every version of Ubuntu so far - 9.04 at least. Since I've upgraded to 9.10, my card reader hasn't worked. 

the card reader definitely exists:
x61:~$ lspci | grep SD
05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)


any suggestions/help would be great.

Thanks!

---

### Post by ceasar.sun on 2010-06-01
I do the follow on Lucid, 

1. make sure to install libccid package, it would depend on libccid
```
sudo apt-get install  libccid
```
2. restart pcscd service
```
sudo /etc/init.d/pcscd restart
```

Hope it could work on previous version

---

