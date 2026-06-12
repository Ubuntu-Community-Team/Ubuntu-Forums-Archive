---
title: "AMD Drivers failing to display desktop"
date: 2017-10-25
forum: Hardware
---

### Post by jfulton3 on 2017-10-25
I recently upgraded to Ubuntu 17.10 and tried installing AMD drivers version 17.30.  The installation went fine for the drivers.  After rebooting I dont see a desktop.  I will see the text from booting and the cursor arrow.  I am unable to interact with the computer after this.  I was forced to remove the drivers and use the default graphics drivers.  I have tried this with Ubuntu 17.04 also and had problems with the AMD drivers not working.
I followed the instructions at the AMD website, running amdgpu-pro-install to install the drivers.

---

### Post by Yellow Pasque on 2017-10-26
What GPU do you have?
```
lspci
```

---

### Post by jfulton3 on 2017-10-26
> **Temüjin said:**
> What GPU do you have?
```
lspci
```

1:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Ellesmere [Radeon RX 470/480] (rev c7)

---

### Post by Yellow Pasque on 2017-10-26
Let me think about it

---

### Post by QIII on 2017-10-26
Wayland session or X session?

---

### Post by jfulton3 on 2017-10-26
I installed in Wayland, but when the computer becomes unusable is at boot.  I'm guessing its at login, where you can select Wayland or x session.  All I see is the text from the boot and the mouse cursor.  I can move the cursor around, but can't interact with the computer, other than ctrl-alt-delete to reboot again.  

When I tried to install the drivers in 17.04 it was xession.  Which I was also unable to complete.

---

### Post by QIII on 2017-10-26
I guess I'll need to think about it, too, then.  :)

---

