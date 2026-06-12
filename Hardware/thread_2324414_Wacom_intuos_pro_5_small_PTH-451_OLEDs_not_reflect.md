---
title: "Wacom intuos pro 5 small PTH-451 OLEDs not reflecting the mode switch"
date: 2016-05-13
forum: Hardware
---

### Post by Haythem_Dhahri on 2016-05-13
As I mentioned in the title  the OLEDs are not reflecting the mode switch.
some solution suggest to run sudo chmod 666 /sys/bus/usb/devices/*/wacom_led/status_led*_select
but for me it return No such file or directory
I found the file status_led0_select containing 0 when I change its content to 1 ,2 and 3 the leds switch.
Here  is the full path of the file :  /sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/0003:056A:0314.0003/wacom_led/status_led0_select
The chmod doesn't complain about the new path but no thing happen to the leds.
Any idea or a workaround to solve this problem its hard to guess which mode is activated without the led indicator.

---

