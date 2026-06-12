---
title: "[Lubuntu 13.04 desktop amd64] Asus M4A78L-M no audio through HDMI"
date: 2013-08-20
forum: Hardware
---

### Post by buttonmasher2 on 2013-08-20
[http://www.asus.com/Motherboards/M4A78LM/#specifications](http://www.asus.com/Motherboards/M4A78LM/#specifications) 


I cannot get audio to pass through hdmi. I can see the hardware as an option when looking through audio devices in vlc nothing works and checked the volume control settings, F6 and choose hdmi audio out,Playbacks only option s/pdif.

Any help?

---

### Post by Yellow Pasque on 2013-08-20
Use workaround 1 here:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

---

### Post by buttonmasher2 on 2013-08-20
> **Temüjin said:**
> Use workaround 1 here:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)


That did it. Thank you very much. I had to learn "sudo leafpad /etc/default/grub" to get it to take. Good deal.




Thanks again.

---

