---
title: "Two /dev/input/mouse1 devices.  Is this a problem for multitouch?"
date: 2011-05-29
forum: Hardware
---

### Post by lumix on 2011-05-29
Natty on Acer Iconia W500:

I've been stabbing myself for weeks in the confusion and darkness of Ubuntu multitouch "Wikis" and threads.  I have no idea (because I can't find an idea of) which device(s) can be used by whatever driver (evdev? evtouch? eGalax?), but in any case...I'm wondering if having 2 mouse1 devices (or any at all) will interfere with multitouch (i.e. screen input).

usb-eGalax_Inc._USB_TouchController-event-mouse -> ../event7
lrwxrwxrwx 1 root root 9 2011-05-29 09:19 usb-eGalax_Inc._USB_TouchController-mouse -> ../mouse0
lrwxrwxrwx 1 root root 9 2011-05-29 09:19 usb-SONiX_USB_Keyboard_0131-event-kbd -> ../event8
lrwxrwxrwx 1 root root 9 2011-05-29 09:19 usb-SONiX_USB_Keyboard_0131-event-mouse -> ../event9
lrwxrwxrwx 1 root root 9 2011-05-29 09:19 usb-SONiX_USB_Keyboard_0131-if01-event-mouse -> ../event9
lrwxrwxrwx 1 root root 9 2011-05-29 09:19 usb-SONiX_USB_Keyboard_0131-if01-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2011-05-29 09:19 usb-SONiX_USB_Keyboard_0131-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2011-05-29 09:19 usb-SuYin_1.3M_Front_HF2015-A821-OV01-VA-R01.01.01-event-if00 -> ../event6
lrwxrwxrwx 1 root root 9 2011-05-29 09:19 usb-SuYin_1.3M_Rear_HF2015-A821-OV01-VA-R01.01.01-event-if00 -> ../event5

---

