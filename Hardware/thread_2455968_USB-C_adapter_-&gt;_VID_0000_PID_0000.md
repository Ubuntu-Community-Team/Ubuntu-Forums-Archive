---
title: "USB-C adapter -&gt; VID 0000 PID 0000"
date: 2020-12-31
forum: Hardware
---

### Post by Andrew F in Australia on 2020-12-31
Hi All,

Bought an adapter that comes up as a VID =0000 and PID = 0000 from a local 'walmart' equivalent as I'm on holidays.
[https://www.kmart.com.au/product/usb-c-to-3.5mm-aux-adaptor/2884322](https://www.kmart.com.au/product/usb-c-to-3.5mm-aux-adaptor/2884322)

The adapter works in Windows, but am happy to file this under the: "it's dead, Jim" if needed, but asking for advice.
Hardware also recognised in Windows as VID000, etc...

I use a dual boot laptop for work - linux/Ubuntu and Windows - only use Windows at work for about 40% of the time.  Ubuntu at home and when doing prep work.

Output here

dmesg (adapter only plugged in, no headphones.)
```

[ 1533.476673] usb 1-4: new full-speed USB device number 7 using xhci_hcd
[ 1533.627754] usb 1-4: New USB device found, idVendor=0000, idProduct=0000, bcdDevice= 1.00
[ 1533.627760] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=1
[ 1533.627764] usb 1-4: Product: CBHT Audio
[ 1533.627767] usb 1-4: Manufacturer: CBHT Audio
[ 1533.627769] usb 1-4: SerialNumber: CBHT Audio
[ 1533.636624] input: CBHT Audio CBHT Audio as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.3/0003:0000:0000.0005/input/input32
[ 1533.697115] hid-generic 0003:0000:0000.0005: input,hidraw3: USB HID v2.01 Device [CBHT Audio CBHT Audio] on usb-0000:00:14.0-4/input3

```

uname -a
```
Linux horace 5.4.0-58-generic #64-Ubuntu SMP Wed Dec 9 08:16:25 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

plugging in headphones disables the keyboard and brings a black square on the monitor with a prohibition sign in it.  Also logs the following on dmesg

```


dmesg 

[ 1961.928339] pcieport 0000:00:1d.6: AER: Corrected error received: 0000:05:00.0
[ 1961.928514] alx 0000:05:00.0: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Receiver ID)
[ 1961.928522] alx 0000:05:00.0: AER:   device [1969:e0b1] error status/mask=00000080/00000000
[ 1961.928528] alx 0000:05:00.0: AER:    [ 7] BadDLLP               
[ 1961.930141] pcieport 0000:00:1d.6: AER: Corrected error received: 0000:05:00.0
[ 1961.930204] alx 0000:05:00.0: AER: PCIe Bus Error: severity=Corrected, type=Data Link Layer, (Receiver ID)
[ 1961.930212] alx 0000:05:00.0: AER:   device [1969:e0b1] error status/mask=00000080/00000000
[ 1961.930217] alx 0000:05:00.0: AER:    [ 7] BadDLLP     
```   

Does anybody have a clue to get this working? I have a workaround already, but would like to get a set of headphones working if possible

---

