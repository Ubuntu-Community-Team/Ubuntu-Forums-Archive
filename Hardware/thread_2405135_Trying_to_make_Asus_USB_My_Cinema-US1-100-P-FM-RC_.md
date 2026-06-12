---
title: "Trying to make Asus USB My Cinema-US1-100-P-FM-RC Analog TV tuner work"
date: 2018-11-01
forum: Hardware
---

### Post by pete-br on 2018-11-01
Here is the LinuxTV page with all the hardware info I can give you.[URL="https://www.linuxtv.org/wiki/index.php/Asus_USB_My_Cinema-US1-100-P-FM-RC_(id_0x0b05:0x1756)"]
[https://www.linuxtv.org/wiki/index.php/Asus_USB_My_Cinema-US1-100-P-FM-RC_(id_0x0b05:0x1756)](https://www.linuxtv.org/wiki/index.php/Asus_USB_My_Cinema-US1-100-P-FM-RC_(id_0x0b05:0x1756))[/URL]

I am trying to make this device work.


I have obtained, altered, build and installed the V4L drivers trying to make this device work:
[https://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](https://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

I have added my card to the em28xx.h file
and defined it in the em28xx-cards.c file.

And then build it and installed it as explained in the 'Developer's Approach' section.
That part worked, but the card does not work and no /dev/videoX device is added.

---

### Post by pete-br on 2018-11-01
In the em28xx-cards.c file
under the section
/*
 *  Board definitions
 */
I added
    ```
[EM2862_BOARD_ASUS_MYCINEMA_US1100PFMRC] = {
        .name          = "Asus USB My Cinema US1-100-P-FM-RC",
        .def_i2c_bus   = 1,
        .i2c_speed     = EM28XX_I2C_CLK_WAIT_ENABLE |
                 EM28XX_I2C_FREQ_400_KHZ,
        .tuner_type    = TUNER_NXP_TDA18271,
        .tuner_gpio    = default_tuner_gpio,
        .has_dvb       = 0,
        .input         = {{
            .type     = EM28XX_VMUX_TELEVISION,
            .vmux     = EM28XX_AMUX_VIDEO,
            .amux     = EM28XX_AMUX_LINE_IN,
            .gpio     = NULL,
        } },
        .radio           = {
            .type     = EM28XX_RADIO,
            .amux     = EM28XX_AMUX_LINE_IN,
            }
    },
```


I added to the em28xx.h file:
```
/* Boards supported by driver */
...
#define EM2862_BOARD_ASUS_MYCINEMA_US1100PFMRC    103
```

dmesg reports:
```
[22942.618277] usb 2-1.2: new high-speed USB device number 6 using ehci-pci
[22942.734235] usb 2-1.2: New USB device found, idVendor=0b05, idProduct=1756
[22942.734241] usb 2-1.2: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[22942.734245] usb 2-1.2: Product: ASUS Analog TV T
[22942.734249] usb 2-1.2: SerialNumber: 105496930000170
[27317.673445] usbcore: deregistering interface driver em28xx
[27365.816387] media: Linux media interface: v0.10
[27365.839364] videodev: Linux video capture interface: v2.00
[27365.839366] WARNING: You are using an experimental version of the media stack.
                   As the driver is backported to an older kernel, it doesn't offer
                   enough quality for its usage in production.
                   Use it with care.
               Latest git patches (needed if you report a bug to [EMAIL="linux-media@vger.kernel.org"]linux-media@vger.kernel.org[/EMAIL]):
                   3b796aa60af087f5fec75aee9b17f2130f2b9adc media: rename soc_camera I2C drivers
[27365.853893] usbcore: registered new interface driver em28xx
```

---

