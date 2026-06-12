---
title: "USB-flashed ISO not booting anymore after update BIOS"
date: 2023-09-08
forum: Hardware
---

### Post by alevykh on 2023-09-08
Hello!


I have Ubuntu since 22.04.1. All worked very fine!
My BIOS version was 3002. After first BIOS update from 3002=> 3202 (this update of BIOS directly related to zenbleed issue). My secret key was rewritten and I reinstall Ubuntu with version 22.04.2.


Now BIOS update to 3205 and kernel on Ubuntu update to 6.2. My secret key was lost again and I flashed new 22.04.3 to my USB, but now Ubuntu not load anymore. I see only screen where I can choose "Try and Install Ubuntu". Ok, I choose this options, but nothing happens, I see black screen only. Now I have not Ubuntu (because I clear my NVME from BIOS) and can't install Ubuntu again :(((


PS: I try to flash 20.04.x but I saw another error "blah-blah unsupported/unknown CPUID" <= something like that...


Q: What should I do?
PS: Now I've install and use w11 for short time ((


MB: ASUS TUF GAMING B550M-PLUS WIFI II
CPU: AMD Ryzen 7 5700x

EDITED:
Ubuntu 23.04 works! 18.04.x 20.04.x 22.04.x not working, others brands works too. I stay on 23.04 edition but fonts are not looking fine (

---

### Post by alevykh on 2023-09-11
This issue related to new Secure Boot Keys (vendor ASUS) was updated in 3205 BIOS. If I clear (disable) this keys 22.04.x loaded from USB-flash, as expected. If keys not cleared then BIOS ask to ENROLL MOK key, but where I can take this key?? Stay on 23.04 again (

PS ENROLL MOK key ask only  22.04.1 release, others not working

---

