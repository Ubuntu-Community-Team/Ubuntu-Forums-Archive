---
title: "Usb mouse not working properly"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by henriquemaia on 2006-06-20
I have an usb mouse but I use it mostly as a ps/2 one through an adaptor to keep the usb slots free. With this configuration it works without problems.

Today I needed the adaptor for another computer and connected my mouse through the usb ports. The mouse started acting weirdly, losing the focus randomly, changing the pointer and freezing for second each 10 seconds or so. 

I have checked dmesg and the output is this:

```
[ 8067.615375] hub 1-0:1.0: port 6 disabled by hub (EMI?), re-enabling...
[ 8067.615380] usb 1-6: USB disconnect, address 105
[ 8067.697132] usb 1-6: new low speed USB device using ohci_hcd and address 106
[ 8067.800388] input: USB OpticalWheel Mouse as /class/input/input464
[ 8067.800428] input: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:00:02.0-6
[ 8089.366549] hub 1-0:1.0: port 6 disabled by hub (EMI?), re-enabling...
[ 8089.366554] usb 1-6: USB disconnect, address 106
[ 8089.448307] usb 1-6: new low speed USB device using ohci_hcd and address 107
[ 8089.548128] input: USB OpticalWheel Mouse as /class/input/input465
[ 8089.548168] input: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:00:02.0-6
[ 8098.180760] hub 1-0:1.0: port 6 disabled by hub (EMI?), re-enabling...
[ 8098.180765] usb 1-6: USB disconnect, address 107
[ 8098.262517] usb 1-6: new low speed USB device using ohci_hcd and address 108
[ 8098.365872] input: USB OpticalWheel Mouse as /class/input/input466
[ 8098.365911] input: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:00:02.0-6
[ 8113.748719] hub 1-0:1.0: port 6 disabled by hub (EMI?), re-enabling...
[ 8113.748724] usb 1-6: USB disconnect, address 108
[ 8113.830477] usb 1-6: new low speed USB device using ohci_hcd and address 109
[ 8113.933653] input: USB OpticalWheel Mouse as /class/input/input467
[ 8113.933692] input: USB HID v1.10 Mouse [USB OpticalWheel Mouse] on usb-0000:00:02.0-6

``` 
This goes on endlessly for as long as the mouse is connected to the usb port. When I change it back to ps/2, I get:

```
[ 8114.664483] usb 1-6: USB disconnect, address 109
[ 8117.768118] input: ImExPS/2 Generic Explorer Mouse as /class/input/input468
``` 
And the messages stop. The mouse gets back to its proper behaviour.

Does anyone else have this? Is it a bug?

---

### Post by rai4shu2 on 2006-06-20
Maybe your USB hub doesn't like the mouse for some weird reason. Maybe you could try some other hub/USB connection.

---

### Post by henriquemaia on 2006-06-21
[quote=rai4shu2]Maybe your USB hub doesn't like the mouse for some weird reason. Maybe you could try some other hub/USB connection.[/quote]

On my secondary hub (pc front), it works ok. Any ideas why the main hub rejects the mouse?

---

