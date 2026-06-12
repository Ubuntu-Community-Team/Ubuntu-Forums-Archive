---
title: "Ubuntu 16.04 wont load my microSD of 4gb"
date: 2016-06-11
forum: Hardware
---

### Post by santiago9 on 2016-06-11
Some idea?
i try whit different microSD of 2gb and are run good, but the 4gb wont load...  some idea? 

before of post this i check other post here that similar issue but, dont fix the problem...

---

### Post by Omar_Jair on 2016-06-11
Try to use Gparted and Reformat your SD card to a FAT format, try to plug it in again, a word to the wise though, check if your SD is being read on other machines, if it doesnt load it may be broken.

---

### Post by X-RED_Tech on 2016-06-12
Also not all SD card readers support SDHC (4-32GB). A very old device often supports the original standard only (up to 2GB).
We may be able to check that for you if we know what's in your machine. The reader should be listed with either **lsusb** (lists USB devices) or **lspci**&#8203; (lists PCI devices), in terminal.

---

