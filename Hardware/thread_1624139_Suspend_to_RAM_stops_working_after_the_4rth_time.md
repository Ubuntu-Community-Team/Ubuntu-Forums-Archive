---
title: "Suspend to RAM stops working after the 4rth time"
date: 2010-11-17
forum: Hardware
---

### Post by archwndas on 2010-11-17
Dear all,
I have the latest Ubuntu x86_64 10.10. It is fully updated to the current latest version. However, this problem insists since the very first version of 10.10. Wake up from suspend works fine the first, second and 3rd time you do suspend in RAM. The 4rth time however it doesn't wake up and I see a blank screen. I have to shutdown and boot again. 

I also have another problem with the sound system. After each reboot I see that both the speakers and mic are muted. 

Please help,
best Archwn.

---

### Post by Fafler on 2010-11-17
Please tell us a bit more about your hardware.

---

### Post by archwndas on 2010-11-19
Well I was trying to do that yesterday but the forums would not allow me to reply and although I was loging in correctly it would always take me back to the login screen every time I was pressing "New reply". I am not writing this from my laptop now, but I can tell you a fwe things about my hardware. I have saved the output of:

lshw
lspci
lsusb

at home and I was thinking of attaching it. Is that enough or you need more?

I have a Sager laptop 8662 model 15.4 inch monitor with a Intel Core 2 Duo CPU at 2.8 GHz and 6MB cache. I have 4 GB RAM and an NVIDIA GTX 260 card with 1GB RAM. I have also an 0402:5606 ALi Corp. USB 2. 0 Camera that doesn't work in Linux after some point in time.

Is that enough?

Cheers,
Archwn.

---

### Post by Fafler on 2010-11-20
The USB camera might be the culprit. Make sure no driver is claiming it, as i've seen USB cameras make computers crash when waking up from suspend before.

I was mostly interested in which model and chipsset generation you had, but it's newer than anything i have any real experience with. I think it can be related to the camera, the kernel/acpi stuff in which case i have no idea what to do, or the X server. Is there any harddrive activity when you try to resume? If something other than the kernel if preventing it from resuming, you should be able to find something about it in the log files.

---

### Post by archwndas on 2010-11-23
Here they are.

---

