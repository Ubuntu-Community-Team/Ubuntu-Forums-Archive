---
title: "USB Drive Issues, 20.04"
date: 2021-02-24
forum: Hardware
---

### Post by Dr._B on 2021-02-24
I have had an odd issue crop up in Ubuntu 20.04. When I plug in a USB drive it opens fine and I can use it normally, but if I eject it and then re-insert it, it doesn't always load. It doesn't matter which USB port I use. None of my other USB devices (webcam, mouse, keyboard and microphone) have any issues, so I doubt its an issue with my hardware. I've even tried moving the other devices around so that I can use their ports for the USB key, and the problem persists.

Issue persists across multiple USB drives, as well as on SD cards plugged in via a USB3 hub with built-in card reader.

Any suggestions as to what may be occurring.

---

### Post by #&amp;thj^% on 2021-02-24
> **Dr._B said:**
> 
Issue persists across multiple USB drives, as well as on SD cards plugged in via a USB3 hub with built-in card reader.

Any suggestions as to what may be occurring.

I see a lot of post's regarding **USB3 hubs**, if you can try with usb2. 
Is the hub full with devices, or the majority of the ports used?

---

### Post by TheFu on 2021-02-24
Does **dmesg** see the device inserted and removed?  If that doesn't happen, there is little we can do.

---

### Post by Dr._B on 2021-02-24
dmesg is giving this error:

> [193156.940842] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?[193161.056985] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193165.297086] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193169.389221] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193174.113377] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193178.201545] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193182.605667] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193186.833799] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193190.929934] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193195.182090] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193199.626217] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193203.722356] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193207.958491] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193212.038668] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193216.266765] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193220.354900] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193224.579046] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193228.671198] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193232.911322] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?
[193236.991475] usb usb2-port2: Cannot enable. Maybe the USB cable is bad?




---

### Post by #&amp;thj^% on 2021-02-24
You may want to add yourself to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1856608](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1856608)

---

