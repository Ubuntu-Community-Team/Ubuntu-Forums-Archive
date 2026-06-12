---
title: "labtec keyboard, missing keys"
date: 2008-08-05
forum: Hardware
---

### Post by Stex on 2008-08-05
Hi there, I've got a new wireless keyboard for my laptop but occasionally it starts acting up and misses keystrokes. Much like when the batteries run out, except I can fix it by unplugging and plugging in the receiver again.

I thought this was just a defect or it being cheap but when I used it on windows it worked perfectly for hours.

Any idea what's wrong or where I could look for more information of what's happening? I'm used to the terminal and configuring X but don't know where to start with this problem...

Thanks

---

### Post by tamoneya on 2008-08-05
right after you get a couple of misses run this line in terminal:```
dmesg | tail
```Then post the results here.

---

### Post by Stex on 2008-08-06
Nothing happens I don't think, the last stuff is about my CPU.
```
[   82.878537] CPU1 attaching sched-domain:
[   82.878541]  domain 0: span 03
[   82.878546]   groups: 02 01
```

When I pull it out and put it back in it goes through this:
```
[15920.150148] usb 1-1.1: USB disconnect, address 3
[15922.141796] usb 1-1.1: new low speed USB device using ehci_hcd and address 5
[15922.245752] usb 1-1.1: configuration #1 chosen from 1 choice
[15922.252091] input: PATEN USB HID Device         as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.1/1-1.1:1.0/input/input14
[15922.297354] input,hidraw0: USB HID v1.10 Keyboard [PATEN USB HID Device        ] on usb-0000:00:1d.7-1.1
[15922.307600] input: PATEN USB HID Device         as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.1/1-1.1:1.1/input/input15
[15922.341173] input,hidraw1: USB HID v1.10 Device [PATEN USB HID Device        ] on usb-0000:00:1d.7-1.1
[15922.346304] input: PATEN USB HID Device         as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1.1/1-1.1:1.2/input/input16
[15922.409212] input,hidraw2: USB HID v1.10 Mouse [PATEN USB HID Device        ] on usb-0000:00:1d.7-1.1

```

---

