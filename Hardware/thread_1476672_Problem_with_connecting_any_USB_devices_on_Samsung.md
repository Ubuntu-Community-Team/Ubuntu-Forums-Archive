---
title: "Problem with connecting any USB devices on Samsung NB30"
date: 2010-05-08
forum: Hardware
---

### Post by Serge925 on 2010-05-08
I've just installed the Netbook Remix version of 10.4 on my newly bought Samsung NB30.  Installation from the USB pendrive went without any problem, but after the reboot I can't see USB devices connected. After connecting any pendrive, flashcard reader, etc, dmesg does not output anything USB related, the output of lsusb is always empty.  The usb controller is still there:
```
lspci | grep -i usb
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI  Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI  Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI  Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI  Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI  Controller (rev 02)

```Several reboots didn't help.
ANy suggestion on what went wrong?

PS. dmesg doesn't report when a usb device is  connected.  The only match to 'usb' is at the loading stage:
```
    0.224630] SCSI subsystem initialized
    0.224930] libata version 3.00 loaded.
    0.225146] usbcore: registered new interface driver usbfs
    0.225283] usbcore: registered new interface driver hub
    0.225463] usbcore: registered new device driver usb
    0.225955] ACPI: WMI: Mapper loaded

```

---

### Post by Serge925 on 2010-05-09
just found that the reason is the IRQ conflict.  Following advice from
[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)
The step that finally helped was adding 'pci=noacpi' to the boot parameters.

---

### Post by recreation on 2010-06-25
The 
  Samsung   NB30  has just dropped in price! Check it out here:   [http://www.upiq.com/api.php?pid=95528162]("http://www.upiq.com/api.php?pid=92284390")

---

