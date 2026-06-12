---
title: "Driver Tobii pc eye tracker"
date: 2013-12-30
forum: Hardware
---

### Post by bartvl on 2013-12-30
Due ALS, an motor neuron disease, i´m not able to control the keyboard or mouse. That is why i have an eye-tracker device. This works fine in windows. However i´m used to linux. There are no drivers or software for Linux. Is there a way to reverse engineering the windows driver? 

I´ve contacted the manufacturer of the driver, MCCI Corporation. They told me that tobii is responsible. when i connect the device in ubuntu, dmesg shows me:

```
Dec 29 20:21:16 bart-VirtualBox kernel: [  275.072251] usb 2-2: new full-speed USB device number 3 using ohci_hcdDec 29 20:21:17 bart-VirtualBox kernel: [  275.294153] usb 2-2: not running at top speed; connect to a high speed hub
Dec 29 20:21:17 bart-VirtualBox kernel: [  275.312317] usb 2-2: New USB device found, idVendor=0525, idProduct=a4a1
Dec 29 20:21:17 bart-VirtualBox kernel: [  275.312337] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=10
Dec 29 20:21:17 bart-VirtualBox kernel: [  275.312343] usb 2-2: Product: Tobii IS Eye Tracker
Dec 29 20:21:17 bart-VirtualBox kernel: [  275.312348] usb 2-2: Manufacturer: Tobii Technology AB
Dec 29 20:21:17 bart-VirtualBox kernel: [  275.312353] usb 2-2: SerialNumber: 112000361
Dec 29 20:21:17 bart-VirtualBox kernel: [  275.368438] cdc_ether 2-2:1.0 usb0: register 'cdc_ether' at usb-0000:00:1f.4-2, CDC Ethernet Device, be:7f:85:5e:27:fd
Dec 29 20:21:17 bart-VirtualBox kernel: [  275.368979] usbcore: registered new interface driver cdc_ether
Dec 29 20:22:58 bart-VirtualBox kernel: [  376.891061] usb 2-2: USB disconnect, device number 3
Dec 29 20:22:58 bart-VirtualBox kernel: [  376.892415] cdc_ether 2-2:1.0 usb0: unregister 'cdc_ether' usb-0000:00:1f.4-2, CDC Ethernet Device
bart@bart-VirtualBox:~$ 

```

---

### Post by tgalati4 on 2013-12-30
Some work was done in 2005 to port a linux driver:  [http://andrewd.ces.clemson.edu/tobii/](http://andrewd.ces.clemson.edu/tobii/)

So, I would image that newer modules (what drivers are called in linux) exist.

[http://www.tobii.com/en/eye-tracking-research/global/AM/application-market-for-tobii-eye-trackers/t2t/](http://www.tobii.com/en/eye-tracking-research/global/AM/application-market-for-tobii-eye-trackers/t2t/)

[http://psy.cns.sissa.it/t2t/About_T2T.html](http://psy.cns.sissa.it/t2t/About_T2T.html)

So the piece parts are there.  Just need to link to an on-screen keyboard (like matchbox-keyboard) or define an xorg input device to interface with the desktop.

---

### Post by bartvl on 2013-12-30
HERO!  I was not familiar with t2t. I will give it a shot.  Is it capable to switch between mouse buttons and hold to select and scroll? Have you ever set this up?

---

### Post by tgalati4 on 2013-12-30
Sorry, I just did a google search on  *Tobii IS Eye Tracker linux module* and these links came up.  There is a google+ discussion group that you can sign up for and ask the question there.  Otherwise, send an email to the developer.  Explain your condition and perhaps he can point you to a turn-key solution.

---

### Post by mikeb2 on 2014-04-25
I am also interested in using eye-tracker in linux...were you able to find a solution?

---

