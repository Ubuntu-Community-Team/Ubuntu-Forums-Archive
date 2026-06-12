---
title: "properly close the USB connection with the USBRH thermometer"
date: 2019-08-28
forum: Hardware
---

### Post by LastStarDust on 2019-08-28
Hello!

I am an experimental physicist who is developing the DAQ system for our particle physics (neutrino) experiment.

We monitor temperature and humidity in our detectors using some [USBRH]("https://strawberry-linux.com/catalog/items?code=52002") probes. Even if the company that produces these devices is called Strawberry Linux, there are no official Linux drivers ... they really have a strange sense of humor.

Anyway, there are a couple of non-official Linux drivers lying around in the internet.
[LIST]
[*][https://github.com/kimata/usbrh](https://github.com/kimata/usbrh) (kimata)
[*][https://github.com/osapon/usbrh-linux](https://github.com/osapon/usbrh-linux) (osapon)
[/LIST]
The **kimata** one is a kernel module but it makes the kernel panic every time. So I decided to use the osapon one.

The **osapon** driver is a simple user-space application that uses the old libusb 0.1 API and it kind of works but it has a strange issue that now I am going to describe. The first time that the temperature is read, everything runs fine, but the second time that I run the program, I get a meaningless temperature (-40) after a considerable. I think that the device is not closed properly. **If I replace the "[FONT=courier new]usb_close[/FONT]" call with the "[FONT=courier new]usb_reset[/FONT]" call everything works fine, but I am wondering if this is the right way to proceed.**Everytime that I call the program this line appears in dmesg:
```
[FONT=courier new]usb 5-4.4: reset low-speed USB device number 17 using xhci_hcd[/FONT]
```

This is the part of the code that (should) closes the USB connection:
```
[FONT=courier new]     if ((rc = usb_release_interface(dh, dev->config->interface->altsetting->bInterfaceNumber)) < 0) {
        puts("usb_release_interface error");
        usb_reset(dh);
         // usb_close(dh);
        exit(5);
    }


    if (usb_reset(dh) < 0) puts("usb_reset error");
    // if (usb_close(dh) < 0) puts("usb_close error");[/FONT]
```

**I am open to any kind of suggestion. In the worst case scenario I might just flood dmesg with those messages or silence them somehow. In the best case scenario I would like to know how to properly close the connection with the USBRH.**

---

