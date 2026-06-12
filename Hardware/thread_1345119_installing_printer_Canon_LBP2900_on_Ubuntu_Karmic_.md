---
title: "installing printer Canon LBP2900 on Ubuntu Karmic 64bit"
date: 2009-12-03
forum: Hardware
---

### Post by whitered on 2009-12-03
I'm trying to install my printer as described here: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)
i compiled the drivers from the source code successful, found CNCUPSLBP2900CAPTK.ppd in the folder /usr/local/share/cups/model/ and then copied it to /usr/share/cups/model/

after that I typed
```
sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
```and got the error:
```
lpadmin: Bad device-uri scheme "ccp"!
```there's no ccpd file in /etc/init.d/ and no ccpdadmin in /usr/sbin


why don't I have the ccpd file and how can I get it?

I found ccpd, ccpdadmin and other related files in the folder CAPT_Printer_Driver_for_Linux_Src_V190_uk_EN/Src/cndrvcups-capt-1.90/libs - in the sources downloaded from canon site.
I tryed to copy ccpd and ccpdadmin into the exptected folders, but i still have "bad device-uri" with lpadmin command

My printer worked fine under Ubuntu 8.04 - 9.04 (32bit), but I did not compile the drivers from sources on that systems

---

