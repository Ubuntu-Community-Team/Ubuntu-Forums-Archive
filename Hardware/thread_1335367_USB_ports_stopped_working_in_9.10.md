---
title: "USB ports stopped working in 9.10"
date: 2009-11-23
forum: Hardware
---

### Post by nmgarnett on 2009-11-23
Hi
I've recently upgraded to 9.10 and all my USB ports have stopped working - I've done lsusb and lspci and get a list of controllers I've also installed pmount and update pciids, so I've looked at all posts in the forum and tried averything and they are still not working?
One thing is that when I plug something like a pen drive in, if they have a light it lights up for about 3 seconds then goes out
Any help appreciated
Nick Garnett

---

### Post by cariboo on 2009-11-23
We need to do some troubleshooting. After you have plugged in your device, open an Applications-->Accessories-->Terminal and type:

```
dmesg | tail -n15
```

and paste the output in your next post. The above command will print the last 15 lines of dmesg, and it will tell us whether your device is detected or not.

---

### Post by nmgarnett on 2009-11-23
Hi Cariboo907
AS per your request the output from dmesg | tail -n15

[   21.206465] agpgart-via 0000:00:00.0: putting AGP V2 device into 0x mode
[   21.206563] pci 0000:01:00.0: putting AGP V2 device into 0x mode
[   32.472036] usb 1-3: device not accepting address 3, error -110
[   32.584055] usb 1-3: new high speed USB device using ehci_hcd and address 4
[   43.016037] usb 1-3: device not accepting address 4, error -110
[   43.128034] usb 1-3: new high speed USB device using ehci_hcd and address 5
[   53.568038] usb 1-3: device not accepting address 5, error -110
[   53.568076] hub 1-0:1.0: unable to enumerate USB device on port 3
[   58.196499] wlan0: authenticate with AP 00:11:95:02:41:3c
[   58.198249] wlan0: authenticated
[   58.198253] wlan0: associate with AP 00:11:95:02:41:3c
[   58.199705] wlan0: RX AssocResp from 00:11:95:02:41:3c (capab=0x431 status=0 aid=1)
[   58.199711] wlan0: associated
[   58.204347] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   68.837503] wlan0: no IPv6 routers present

Thanks
Nick Garnett

---

### Post by anewman on 2009-11-23
My USB has gone tits up too with a recent update and I have seen similar output in dmesg (although they do seem to change alot too). You don't by any chance happen to be using an Nvidia Nforce based motherboard?! If so then it's something to do with our chipsets I imagine being incompatible with a recent update.

My USB mouse is working fine but other things aren't.

---

