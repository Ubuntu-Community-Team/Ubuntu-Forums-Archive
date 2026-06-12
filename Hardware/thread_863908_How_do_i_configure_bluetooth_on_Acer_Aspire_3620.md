---
title: "How do i configure bluetooth on Acer Aspire 3620"
date: 2008-07-19
forum: Hardware
---

### Post by Avinash.Rao on 2008-07-19
Hi,

I have installed Ubuntu 8.04 and i am trying to connect to my HTC phone via bluetooth or USB! I am able to connect to different mobile phones using the HTC phones but i am not able to connect to the laptop. When i search for Bluetooth devices on the mobile, it says there no devices.

I have done everything mentioned in the link below. The bluetooth services are running and there is no error.
The drag and drop option on "gnome-obex-send" gives the following error.

There was an error launching the application
Details: Failed to execute child process "gnome-obex-send" (No such file or directory)

[http://www.linuxquestions.org/linux/...s_under_Ubuntu](http://www.linuxquestions.org/linux/...s_under_Ubuntu)

Kindly help
Avinash

---

### Post by Avinash.Rao on 2008-07-19
Hello all,

I just realized that bluetooth device is not present on my laptop. 
How do i get my phone to connect to the laptop using USB cable? 
I connected the phone to the laptop using the USB, but Ubuntu doesn't seem to detect it. 

Also is there an equivalent to Active Sync in Ubuntu?

Thanks,
Avinash

---

### Post by Avinash.Rao on 2008-07-24
I confirmed this from the ACER support and my laptop has bluetooth device, but the LED doesnt glow. How do i get this working??

---

### Post by kioftes on 2008-07-27
I have the same problem on an acer aspire 9302. The bluetooth led is always off and the switch is not working. I installed the acer_acpi module but still no luck. This is the output of dmesg

```
kioftes@Soula:~$ dmesg | grep Bluetooth
[   48.290295] Bluetooth: Core ver 2.11
[   48.290638] Bluetooth: HCI device and connection manager initialized
[   48.290642] Bluetooth: HCI socket layer initialized
[   48.326540] Bluetooth: L2CAP ver 2.9
[   48.326751] Bluetooth: L2CAP socket layer initialized
[   48.405715] Bluetooth: RFCOMM socket layer initialized
[   48.405733] Bluetooth: RFCOMM TTY layer initialized
[   48.405736] Bluetooth: RFCOMM ver 1.8

```

I forgot to say that i am on (kubuntu) hardy 8.04.1, but it has never worked even when i was on edgy, feisty and gutsy...

---

### Post by Avinash.Rao on 2008-07-28
Here's my output.

dmesg | grep Bluetooth
[   53.797504] Bluetooth: Core ver 2.11
[   53.798192] Bluetooth: HCI device and connection manager initialized
[   53.798196] Bluetooth: HCI socket layer initialized

I tried connecting my PDA using USB and i installed Multisync from add/remove programs, but i had no luck, coz, the OS is not detecting the device i guess.

---

