---
title: "Keyboard doesn't work"
date: 2019-08-06
forum: Hardware
---

### Post by ecec on 2019-08-06
After I upgraded from Ubuntu 18.04 to 19.04, my ASUS keyboard stopped working. It fails in both graphical mode and text mode, but works in GRUB. Whenever I plug it in, I also get this peculiar message from dmesg:
```
asus_wmi: Asus Management GUID not found
```

---

### Post by esbenman on 2019-08-11
I have the same exact problem, upgrading from 18.04 to 19.04. Asus keyboard. I also have a Thunderbolt 3 dock (Lenovo). Keyboard works in Grub, but not in Linux. My dmesg says: 

  [  314.012810] usb 1-3.4.3: new low-speed USB device number 13 using xhci_hcd[  314.119771] usb 1-3.4.3: New USB device found, idVendor=04f2, idProduct=1125, bcdDevice= 0.70
[  314.119780] usb 1-3.4.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  314.119785] usb 1-3.4.3: Product: Asus Keyboard
[  314.119789] usb 1-3.4.3: Manufacturer: CHICONY
[  314.151859] asus_wmi: Asus Management GUID not found
[  314.154750] hid_asus: Unknown symbol asus_wmi_evaluate_method (err -2)

The keyboard on the laptop works, but the desktop keyboard does not...

---

