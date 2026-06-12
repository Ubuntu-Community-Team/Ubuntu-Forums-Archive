---
title: "ubuntu 16.04 on Dell Precision 7510 can not boot from usb"
date: 2016-12-26
forum: Hardware
---

### Post by sourcelibre on 2016-12-26
-

    I have the Dell 7510 with 14.04 installed from the factory. It will not boot completely any USB Live drives even from commercial companies, such as OSDisc. It has been suggested that the UEFI:UBUNTU on the primary HD might be preventing the complete boot from USB.

    The original BIOS system setup would not even recognize a USB boot was possible. After contacting Dell support I realized that Dell did not have a Tech Center support just for Linux and the New 7510 was configured wrong for UBUNTU. The following is the correct setup if you want to boot from a USB drive.

    PressF2 -System setup 
    1.disable the secure boot
    2.In "Advanced boot"
    -enable Legacy Option ROMs
    -enable Attempt Legacy Boot


    -->I also went to the Fastboot option and changed it to do a thorough hardware configuration setup.

    Now I can boot from the USB - the next issue:

    
    The USB Live will boot the OS through the countdown and splash screen then hang. The flash drive boots on all other machines in the office.

    WhenI boot from the USB drive I get the following:

---

### Post by wildmanne39 on 2016-12-26
Moved to own thread for better support.

---

### Post by lisati on 2017-01-03
Did you find the problem? If so, what was your solution?

---

### Post by sourcelibre on 2017-01-20
[SOLVED] See link under hardware -**Dell Precision 7510 BIOS did not recognize second drive**

Dell opened a problem/issue case with Engineering.  Dell cannot determine why BIOS does not see second SSD.

---

