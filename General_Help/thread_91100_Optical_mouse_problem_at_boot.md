---
title: "Optical mouse problem at boot"
date: 2005-11-16
forum: General Help
---

### Post by Delas on 2005-11-16
Hi all.
While my kubuntu 5.10 is loading, the *light* of my optical mouse turn off. When i enter KDE, I can't move the pointer, but the left & right click works fine.

Have you any idea?
Thanks!

---

### Post by mlomker on 2005-11-17
[QUOTE=Delas]Have you any idea?[/QUOTE]

Well, not directly.  Try unplugging the USB and then plugging it back in.  This command should show that the system is recognizing it properly (though it must be seeing something for the buttons to work):

```

mlomker@mlomkernote:/$ dmesg
[4302504.366000] usb 3-3.2: USB disconnect, address 3
[4302507.320000] usb 3-3.2: new low speed USB device using ehci_hcd and address 4
[4302507.381000] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:03.3-3.2

```

---

### Post by Delas on 2005-11-17
I forgot to say that the mouse is PS2...
Anycase, thanks for the answer mlomker.

---

