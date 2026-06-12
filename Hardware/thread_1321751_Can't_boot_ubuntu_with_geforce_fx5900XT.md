---
title: "Can't boot ubuntu with geforce fx5900XT"
date: 2009-11-10
forum: Hardware
---

### Post by Vietred on 2009-11-10
I'm using Kubuntu 9.10. Everything is fine with Intel onboard graphic card. But after I install geforce fx5900XT, I can't boot to ubuntu. Even 8.04 & 9.10 live CD is no use. All I see after choosing Ubuntu from GRUB is a black screen and a blinking "_"
Is Anyone have a solution? I really love ubuntu + KDE4, but this is quite disappointed :(

---

### Post by Vietred on 2009-11-10
any help...?

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
That's strange with the live CD. Did you remove the Intel driver before shutting down to use the Nvidia Card? It might be trying to run the Nvidia card with Intel drivers, and we all know that's a fail!

---

### Post by Vietred on 2009-11-10
I didn't remove the intel driver before shutting down. But how can it try to run intel driver with nvidia card if I boot with the live CD? Very strange.

---

### Post by ST3ALTHPSYCH0 on 2009-11-10
That's why I mentioned the live CD was an odd issue. Is the vid card known good in another system? If so, I'd recommend booting with the OB GPU, saving your xorg.conf to a backup file, and uninstalling the intel driver. It can't hurt, and can always be undone.

---

