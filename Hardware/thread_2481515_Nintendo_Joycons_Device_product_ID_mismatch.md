---
title: "Nintendo Joycons: Device product ID mismatch"
date: 2022-12-01
forum: Hardware
---

### Post by arieleoar on 2022-12-01
Hi There!

I have two third party nintendo joycons (L & R) that i'm trying to connect to my ubuntu 22.10. Those connects ok but the buttons mapping are not correct and doing some research `evtest` throws that the device product id (and the device itself) are not correctly recognized:

For left joycon:
  ```

Input driver version is 1.0.1 
Input device ID: bus 0x5 vendor 0x57e product 0x2009 version 0x8001
Input device name: "Nintendo Switch Pro Controller"

```
And For Right joycon
  ```

Input driver version is 1.0.1
Input device ID: bus 0x5 vendor 0x57e product 0x2009 version 0x8001
Input device name: "Nintendo Switch Pro Controller"

```


Checking in the [`hid-nintendo`]("https://github.com/DanielOgorchock/linux") project that now is mainlined into the kernel, looks like those produc id are wrong and doesn't match the ones that the driver is going to recognize:

**hid-ids.c**
  ```

  #define USB_VENDOR_ID_NINTENDO  0x057e
  #define USB_DEVICE_ID_NINTENDO_WIIMOTE    0x0306
  #define USB_DEVICE_ID_NINTENDO_WIIMOTE2    0x0330
  #define USB_DEVICE_ID_NINTENDO_JOYCONL    0x2006 <-- This should be recognized for L joycon
  #define USB_DEVICE_ID_NINTENDO_JOYCONR    0x2007 <-- This should be recognized for R joycon
  #define USB_DEVICE_ID_NINTENDO_PROCON    0x2009 <-- This is getting recognized for both instead
  #define USB_DEVICE_ID_NINTENDO_CHRGGRIP    0x200E

```

So the question is, is there a way to change the product id of the device in order to correct this? or at least a modification somewhere to make the kernel recognize the devices correctly?

If not so then, where can i open a bug for this issue? should this go directly to a ticket to the kernel (not ubuntu)?

Thanks and regards!!

PS: This joycons connect through Bluetooth, these doesn't connect via USB. (for someone wondering...)

---

