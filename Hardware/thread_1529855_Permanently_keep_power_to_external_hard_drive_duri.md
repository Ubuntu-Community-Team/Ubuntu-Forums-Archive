---
title: "Permanently keep power to external hard drive during sleep?"
date: 2010-07-12
forum: Hardware
---

### Post by Dobro_player on 2010-07-12
Hello everyone, I am using a Dell Mini 910 netbook and I am running Kubuntu off an external hard drive which is powered by a USB port. Usually the power to the USB ports is switched off during the sleep (suspend to RAM) mode, but I need to keep power to the USB port the external hard is plugged into, otherwise the computer does not wake up properly. I can fix this problem temporarily by putting this command in the terminal:```
sudo acpitool -W 9
``` but I have to do this every time I restart. The output to this command looks like this:
```
Changed status for wakeup device #9 (USB1)

   Device       S-state   Status   Sysfs node
  ---------------------------------------
  1. LID0         S3    *enabled   
  2. HDEF         S4     disabled  pci:0000:00:1b.0
  3. PXS1         S4     disabled  
  4. PXS2         S4     disabled  pci:0000:03:00.0
  5. PXS3         S3     disabled  pci:0000:04:00.0
  6. PXS4         S4     disabled  
  7. PXS5         S4     disabled  
  8. PXS6         S4     disabled  
  9. USB1         S3     enabled   pci:0000:00:1d.0
  10. USB2        S3     disabled  pci:0000:00:1d.1
  11. USB3        S0     disabled  pci:0000:00:1d.2
  12. USB4        S3     disabled  pci:0000:00:1d.3
  13. USB7        S3     disabled  pci:0000:00:1d.7
  14. SLT0        S4     disabled  
  15. SLT1        S4     disabled  
  16. SLT2        S4     disabled  
  17. SLT3        S4     disabled  
  18. SLT6        S4     disabled
```Is there a way to make this change permanent so that I don't have to enter this command every time I restart?

---

### Post by mikewhatever on 2010-07-12
Why not use /etc/rc.local? Add a command to the file and it will get executed on every startup.

---

### Post by Dobro_player on 2010-07-13
This worked. Thank-you for your help!

---

