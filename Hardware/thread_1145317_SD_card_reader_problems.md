---
title: "SD card reader problems"
date: 2009-05-01
forum: Hardware
---

### Post by V-600 on 2009-05-01
I have the aspire one (8gb ssd, 512 MB) and installed UNR a few days ago. I have gone through and have been tweaking the odd setting to speed up ssd usage but nothing more than that. 

Since installing, neither card reader has seen my 16GB sdhc card whether it's present at boot up or not.

My bios is up to date (seen in a guide to check) and i can't find anything about what to do if no card is seen. Only that it "should" be seen if present on boot up.

Any ideas about how to proceed would be very welcome.

Many thanks

---

### Post by jim87410 on 2009-05-01
Hey Nathan,
I was just starting to research this problem.  Is your A-1 an older model?  You said you only have 512MB RAM.

I just purchased mine last month.  1GB RAM, 8GB SSD Internal & 8GB SSD External & Windows XP Home.  My Bios is Rev 3.5.  I haven't checked to see if it is the latest version or not.  I don't see very many options in Setup other than boot order & passwords.

Just to check I just rebooted without the left external SSD installed.  When I plugged a SSD card into the left SSD reader it was recognized.  However if I plug a SSD card into the right SSD reader it is no joy... nada.

I am an Acer partner and went to the Acer partner looking for information.  There are two separate controllers; a standard SD controller and a SD/MMC controller.  When I run lspci in the command prompt I see both controllers.  When I run sudo lshw | less and then search for SD (/SD) System:0 is the SD/MMC host controller. The SD Host controller is under system:1 UNCLAIMED.  Not sure what that means.  And then the last occurrence of SD is under *-disk which is the internal SSD /dev/sda.

With an SSD plugged into both SD slots I can run sudo fdisk -l to show all of the recognized drives.  Obviously the internal SSD - /dev/sda shows up.  The left external SSD is /dev/mmcblk0.

I have to say I am not sure where to go next.  Does anyone else have any ideas?

---

### Post by V-600 on 2009-05-02
Thanks. I thought my bios was up to date with version 3.3309. I didn't realise there was a 3.5 so will look into that.

I bought the AA1 approx 3 months ago so its not that old.

---

### Post by V-600 on 2009-05-02
This is part of the output of lspci (missing all the intel stuff at the beginning and going from the first mention of anything that looked like an SD card reader)

01:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
01:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
01:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
01:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

I don't know why the SD/MMC card reader appears twice though. Surely the left hand card reader is purely just an SD card reader.

Any ideas what this means?

---

