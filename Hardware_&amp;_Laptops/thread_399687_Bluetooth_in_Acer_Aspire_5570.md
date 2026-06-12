---
title: "Bluetooth in Acer Aspire 5570"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by hectorUbu on 2007-04-02
Hi,

I have an Acer Aspire 5570 laptop which seems to be working fine with Feisty. I got wireless and sound working OTB but I can't get the Bluetooth to work. By sliding the front switch the Bluetooth light doesn't turn on and nothing happens.

```
$ dmesg | grep "Bluetooth"
[   94.201000] Bluetooth: Core ver 2.11
[   94.201000] Bluetooth: HCI device and connection manager initialized
[   94.201000] Bluetooth: HCI socket layer initialized
[   94.233000] Bluetooth: L2CAP ver 2.8
[   94.233000] Bluetooth: L2CAP socket layer initialized
[   94.308000] Bluetooth: RFCOMM socket layer initialized
[   94.308000] Bluetooth: RFCOMM TTY layer initialized
[   94.308000] Bluetooth: RFCOMM ver 1.8

```

I tried installing the acer_acpi module but when trying to insert it I get:

```
FATAL: Error inserting acer_acpi (/lib/modules/2.6.20-13-lowlatency/extra/acer_acpi.ko): No such device
```

... and dmesg:

```
[ 3138.647000] acer_acpi: Acer Laptop ACPI Extras version 0.4
[ 3138.648000] acer_acpi: No WMI interface, unable to load.
```

Also I tried inserting the acerhk module but didn't work either.

Any help??

Thank you!


Hector

---

### Post by Pagan Byte on 2007-05-10
Hey there. I too have an Aspire 5570, but can't get Feisty to load sound or video past 1024x768. Although my Bluetooth turns on, I don't have any hardwar to test the functionality of the service. What did you do that got your sound working? I tanked my laptop install when trying drives from Realtek and am reloading the laptop as of now.

---

### Post by alxjl on 2007-05-11
start your terminal then type "alsamixer". turn on surround by pressing m. It should bring up sound. As for ur resolution, i got 1200x800 simply by installing sudo apt-get install 915resolution that is if your 5570 is using the intel945gm chipset. I hope this helps you.

---

### Post by isagani on 2007-05-22
Sorry to be a little bit off topic here... Have you tried using your ACER aspire 5570's external vga port. I'm planning to buy this laptop (really cheap) and I need to make sure that the vga out will work. I reckon it should but would there be any resolution problems like the one you mentioned?

Thanks!

---

### Post by dr_cerebro on 2007-10-22
> **hectorUbu said:**
> Hi,

I have an Acer Aspire 5570 laptop which seems to be working fine with Feisty. I got wireless and sound working OTB but I can't get the Bluetooth to work. By sliding the front switch the Bluetooth light doesn't turn on and nothing happens.

```
$ dmesg | grep "Bluetooth"
[   94.201000] Bluetooth: Core ver 2.11
[   94.201000] Bluetooth: HCI device and connection manager initialized
[   94.201000] Bluetooth: HCI socket layer initialized
[   94.233000] Bluetooth: L2CAP ver 2.8
[   94.233000] Bluetooth: L2CAP socket layer initialized
[   94.308000] Bluetooth: RFCOMM socket layer initialized
[   94.308000] Bluetooth: RFCOMM TTY layer initialized
[   94.308000] Bluetooth: RFCOMM ver 1.8

```

I tried installing the acer_acpi module but when trying to insert it I get:

```
FATAL: Error inserting acer_acpi (/lib/modules/2.6.20-13-lowlatency/extra/acer_acpi.ko): No such device
```

... and dmesg:

```
[ 3138.647000] acer_acpi: Acer Laptop ACPI Extras version 0.4
[ 3138.648000] acer_acpi: No WMI interface, unable to load.
```

Also I tried inserting the acerhk module but didn't work either.

Any help??

Thank you!


Hector

Check this: [http://ubuntuforums.org/showthread.php?t=580672&page=2](http://ubuntuforums.org/showthread.php?t=580672&page=2)

---

### Post by gregsmith_to on 2007-11-10
hectorUbu, I  have the same laptop, I couldn't get Bluetooth to work on Ubuntu or Vista, I think the answer is very simple: there is a switch for bluetooth, but no interface. Presumably, if you plug in a bluetooth USB unit, the switch is there to make it easier to turn on and off.  I guess it's like those volume controls on the keyboard: They work with a standard control mechanism for the system audio, so any type of audio hardware can be controlled with them, but they don't imply that the hardware exists. The manual makes no mention of any bluetooth interface, and the switch is described as 'switch for bluetooth interface (optional)' , or something like that.

---

### Post by hazememam on 2008-04-23
&#1605;&#1588;&#1603;&#1608;&#1608;&#1608;&#1608;&#1608;&#1608;&#1608;&#1608;&#1585;

---

