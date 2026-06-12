---
title: "Diagnose and fix usb not working"
date: 2013-03-05
forum: Hardware
---

### Post by lucacerone on 2013-03-05
Dear all,
I recently received a laptop (lenovo ThinkPad X220) at work with Ubuntu 12.04 64bit installed that works just fine except that one of the two usb ports doesn't work.
I have no idea how to find and solve the problem, so I would be grateful if you could help me.

When I connect my external usb hd to the port that doesn't work, the power led doesn't even turn on. The same is if I try to charge my Smartphone using usb,
neither it charges or detects that it has been connected to a USB port.

The other port works just fine.

Reading around I thought that you might be interested in the output of
```
sudo lsusb
```

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b217 Chicony Electronics Co., Ltd 
Bus 002 Device 012: ID 04e8:689e Samsung Electronics Co., Ltd GT-S5670 [Galaxy Fit]
```

In this moment I am charging my mobile using the working USB port (that is the last device listed: Bus 002 Device 012: ID 04e8:689e Samsung Electronics Co., Ltd GT-S5670 [Galaxy Fit])

Also the output of:
```
 dmesg | grep -i USB
```
just after connecting my external hd to the port that is not working is:
```
[    0.721602] usbcore: registered new interface driver usbfs
[    0.721611] usbcore: registered new interface driver hub
[    0.721632] usbcore: registered new device driver usb
[    0.966833] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.966906] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.985372] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.985539] hub 1-0:1.0: USB hub found
[    0.985649] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.005326] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.005480] hub 2-0:1.0: USB hub found
[    1.005530] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.005538] uhci_hcd: USB Universal Host Controller Interface driver
[    1.005572] usbcore: registered new interface driver libusual
[    1.296702] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.429221] hub 1-1:1.0: USB hub found
[    1.540210] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.672657] hub 2-1:1.0: USB hub found
[    1.743947] usb 1-1.6: new high-speed USB device number 3 using ehci_hcd
[   18.521031] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input6
[   18.521100] usbcore: registered new interface driver uvcvideo
[   18.521102] USB Video Class driver (1.1.1)
[55417.219229] usb 2-1.2: new high-speed USB device number 3 using ehci_hcd
[55417.642880] Initializing USB Mass Storage driver...
[55417.643124] scsi6 : usb-storage 2-1.2:1.3
[55417.643271] usbcore: registered new interface driver usb-storage
[55417.643274] USB Mass Storage support registered.
[55418.329239] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[55418.330234] usbcore: registered new interface driver cdc_acm
[55418.330235] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
[55480.125260] usb 2-1.2: USB disconnect, device number 3
[55480.339914] usb 2-1.2: new high-speed USB device number 4 using ehci_hcd
[55480.423716] usb 2-1.2: device descriptor read/64, error -71
[55480.647257] usb 2-1.2: device descriptor read/all, error -71
[55480.718860] usb 2-1.2: new high-speed USB device number 5 using ehci_hcd
[55480.802861] usb 2-1.2: device descriptor read/64, error -71
[55480.990427] usb 2-1.2: device descriptor read/64, error -71
[55481.165890] usb 2-1.2: new high-speed USB device number 6 using ehci_hcd
[55481.398424] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[55481.400982] scsi7 : usb-storage 2-1.2:1.3
[55482.490830] usb 2-1.2: reset high-speed USB device number 6 using ehci_hcd
[55482.574686] usb 2-1.2: device descriptor read/64, error -71
[55482.762253] usb 2-1.2: device descriptor read/64, error -71
[55482.937841] usb 2-1.2: reset high-speed USB device number 6 using ehci_hcd
[55483.021627] usb 2-1.2: device descriptor read/64, error -71
[55483.209179] usb 2-1.2: device descriptor read/64, error -71
[55483.384919] usb 2-1.2: reset high-speed USB device number 6 using ehci_hcd
[55483.630217] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[55562.625282] usb 2-1.2: USB disconnect, device number 6
[55562.828624] usb 2-1.2: new high-speed USB device number 7 using ehci_hcd
[55562.925088] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[55562.927674] scsi8 : usb-storage 2-1.2:1.3
[56273.854408] usb 2-1.2: reset high-speed USB device number 7 using ehci_hcd
[56273.938197] usb 2-1.2: device descriptor read/64, error -71
[56274.343462] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[56278.962780] usb 2-1.2: reset high-speed USB device number 7 using ehci_hcd
[56279.057047] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[56283.564436] usb 2-1.2: reset high-speed USB device number 7 using ehci_hcd
[56284.051103] usb 2-1.2: device not accepting address 7, error -71
[56284.123030] usb 2-1.2: reset high-speed USB device number 7 using ehci_hcd
[56284.609747] usb 2-1.2: device not accepting address 7, error -71
[56284.681867] usb 2-1.2: reset high-speed USB device number 7 using ehci_hcd
[56284.922513] usb 2-1.2: device descriptor read/8, error -71
[56285.046526] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[56285.132732] usb 2-1.2: reset high-speed USB device number 7 using ehci_hcd
[56285.238421] usb 2-1.2: device descriptor read/all, error -71
[56285.308492] usb 2-1.2: reset high-speed USB device number 7 using ehci_hcd
[56285.403240] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[57096.818137] usb 2-1.2: reset high-speed USB device number 7 using ehci_hcd
[57096.901880] usb 2-1.2: device descriptor read/64, error -71
[57097.089512] usb 2-1.2: device descriptor read/64, error -71
[57097.265097] usb 2-1.2: reset high-speed USB device number 7 using ehci_hcd
[57097.348908] usb 2-1.2: device descriptor read/64, error -71
[57097.536488] usb 2-1.2: device descriptor read/64, error -71
[57097.712071] usb 2-1.2: reset high-speed USB device number 7 using ehci_hcd
[57098.126982] usb 2-1.2: device not accepting address 7, error -71
[57098.198973] usb 2-1.2: reset high-speed USB device number 7 using ehci_hcd
[57098.613865] usb 2-1.2: device not accepting address 7, error -71
[57098.614516] usb 2-1.2: USB disconnect, device number 7
[57098.693980] usb 2-1.2: new high-speed USB device number 8 using ehci_hcd
[57098.790320] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[57098.793036] scsi9 : usb-storage 2-1.2:1.3
[57159.140620] usb 2-1.2: reset high-speed USB device number 8 using ehci_hcd
[57159.224442] usb 2-1.2: device descriptor read/64, error -71
[57159.412001] usb 2-1.2: device descriptor read/64, error -71
[57159.587605] usb 2-1.2: reset high-speed USB device number 8 using ehci_hcd
[57159.671410] usb 2-1.2: device descriptor read/64, error -71
[57159.858988] usb 2-1.2: device descriptor read/64, error -71
[57160.034616] usb 2-1.2: reset high-speed USB device number 8 using ehci_hcd
[57160.449442] usb 2-1.2: device not accepting address 8, error -71
[57160.521426] usb 2-1.2: reset high-speed USB device number 8 using ehci_hcd
[57160.760985] usb 2-1.2: device descriptor read/8, error -71
[57160.892816] usb 2-1.2: device descriptor read/8, error -71
[57160.996633] usb 2-1.2: USB disconnect, device number 8
[57161.076176] usb 2-1.2: new high-speed USB device number 9 using ehci_hcd
[57161.172729] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[57161.175634] scsi10 : usb-storage 2-1.2:1.3
[58462.392065] usb 2-1.2: USB disconnect, device number 9
[58462.597520] usb 2-1.2: new high-speed USB device number 10 using ehci_hcd
[58462.693941] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[58462.696673] scsi11 : usb-storage 2-1.2:1.3
[58463.770690] usb 2-1.2: reset high-speed USB device number 10 using ehci_hcd
[58464.068982] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[58464.165966] usb 2-1.2: reset high-speed USB device number 10 using ehci_hcd
[58464.309933] usb 2-1.2: device descriptor read/all, error -71
[58464.381469] usb 2-1.2: reset high-speed USB device number 10 using ehci_hcd
[58464.599206] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[58465.457203] usb 2-1.2: USB disconnect, device number 10
[58465.662554] usb 2-1.2: new high-speed USB device number 11 using ehci_hcd
[58465.758897] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[58465.761398] scsi12 : usb-storage 2-1.2:1.3
[59568.263446] usb 2-1.2: reset high-speed USB device number 11 using ehci_hcd
[59568.378228] usb 2-1.2: device firmware changed
[59568.378474] usb 2-1.2: USB disconnect, device number 11
[59568.455033] usb 2-1.2: new high-speed USB device number 12 using ehci_hcd
[59568.551166] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[59568.553694] scsi13 : usb-storage 2-1.2:1.3

```

I have no idea what the output means, but as you can see there are some errors listed.

I thank you all guys in advance for the help!
If you require more information just ask,
Cheers,
-Luca

---

### Post by lucacerone on 2013-03-06
Since I am getting no response, I have also posted the same question on [Askubuntu]("http://askubuntu.com/questions/264654/diagnose-and-fix-usb-not-working") (just telling so that you can follow there as well)

Hope somebody here or there can help :)

---

### Post by sudodus on 2013-03-06
> **lucacerone said:**
> Since I am getting no response, I have also posted the same question on [Askubuntu]("http://askubuntu.com/questions/264654/diagnose-and-fix-usb-not-working") (just telling so that you can follow there as well)

Hope somebody here or there can help :)

I suggest that you try to find out if it is a hardware or software problem. Try to boot the laptop from a USB boot drive (and you can try various linux distros). If the problem persists, it is likely to be bad hardware, maybe as simple as a bad connection. It would be even better, if you can try when booted from a Bart PE or Windows PE or Windows install CD/USB drive (but I think a test with a few live linux distros is enough).

If/when we think is a software problem, we'll look more into your detailed output, and discuss how to solve it.

Good luck :-)

---

### Post by lucacerone on 2013-03-06
Thanks Sudosus,
is there any distro in particular that you would advice? (I am now putting the Ubuntu 12.04 (32bit) live on my USB key)

Cheers,
Luca

---

### Post by lucacerone on 2013-03-06
Ok using Ubuntu 12.04 (32 bit) live I could plug my smartphone (in the faulty usb port)
and have it recognized as an external media player and navigate the sd card...

It seems that the port works to me..

After rebooting I retried on my installed Ubuntu and the smartphone is not even recognized (sorry today I don't have my external hd with me)

---

### Post by matt_symes on 2013-03-06
Hi

From errno.h...

Error -71 is EPROTO; a protocol error.

There are loads of things which can cause this but is usually doggy hardware or power management.

This may or may not help; disable auto suspend. From the terminal..

```
echo -1 | sudo tee /sys/module/usbcore/parameters/autosuspend
```

Plug the device in.

This is not persistent though so, if it works, it will need to be made persistent.

What i find odd is that only one port is not working and this works from a liveCD/USB.

Kind regards

---

### Post by sudodus on 2013-03-06
> **lucacerone said:**
> Dear all,
I recently received a laptop (lenovo ThinkPad X220) at work with Ubuntu 12.04 64bit installed that works just fine except that one of the two usb ports doesn't work.


Fine, now we know it is a software error depending on your installed system. Ubuntu works from a live session.

You got it at work. Is there someone to ask, who is responsible for the installation. Maybe there is some special software installed, that might cause the problem. Could it be reset to some standard configuration for your 'corporate environment'?

---

### Post by lucacerone on 2013-03-06
Hi, first of all thanks to matt_symes. Unfortunately your command didn't solve the things.
Sudosus, thanks, but I don't think we have any special software installed that might be causing the issue. I work for a university, I just got one of the laptop available at my lab.

Also I won't be using this computer since next monday, so I am sorry if I won't reply before commenting for eventual proposed solutions.

Thanks a lot again,
Luca

---

