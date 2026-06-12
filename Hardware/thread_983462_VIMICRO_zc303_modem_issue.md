---
title: "VIMICRO zc303 modem issue"
date: 2008-11-15
forum: Hardware
---

### Post by martmonkey on 2008-11-15
I have a vimicro zc303 webcam. For some reason xubuntu intrepid is not assigning the correct drivers for it. I did install the gspca drivers by following a guide in this forums but still no joy. xubuntu still trying to install zc0301 drivers instead. So i am not being able to use the device. I managed to use this webcam with no issue in gutsy and hardy.

---

### Post by Yezinki on 2008-11-15
Read linux23dragon's post on webcam driver uppdates & hard wrae specs....or ask for his assistance.

Good luck.

---

### Post by Yezinki on 2008-11-15
Ubuntu 8.10 as a rule supports/ has drivers for newer devices.

So if your system peripherals are old stick with Hardy.

My thoughts,

Regards,

Yezinki.

---

### Post by martmonkey on 2008-11-15
My system peripherals are not old. I allready followed linux23dragons instructions provided but it didn't sort out the issue. Still the webcam is not recognised.
I added the gspca_zc3xx module to /etc/modules but that didn't help either.

---

### Post by Yezinki on 2008-11-16
At the moment is not supported by Ubuntu 8.10, wait or get a new cam.

---

### Post by martmonkey on 2008-11-16
I am not going to buy new modem because xubuntu intrepid is not supporting my cam. It is easier to scrap xubuntu than buying a new cam Yezinski.

---

### Post by martmonkey on 2008-11-16
By the way GSPCA driver supports zc0303. But seems like intrepid is preventing it.

---

### Post by martmonkey on 2008-11-18
I downgraded the kernel and everything is working fine. So it was an issue with the current kernel the intrepid comes with.

---

