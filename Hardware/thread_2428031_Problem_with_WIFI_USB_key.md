---
title: "Problem with WIFI USB key"
date: 2019-09-29
forum: Hardware
---

### Post by jean-michel.richer on 2019-09-29
Hello everybody,
  I am posting this thread because I have no idea where to start to solve this problem.

I have a D-Link WIFI USB key (DWA-140) which works generally fine with other computers.
For a AMD Ryzen 1700X system with MSI A320M GAMING PRO (MS-7A39) motherboard.

Whenever I start the computer, the WIFI USB key is recognized, I get an IP address but then
I can't get access to internet. I have unplug the key and plug it again.

  I would like to solve the problem so that the key works fine from the start.

Here is the dmesg output :

```
[   37.242228] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[   37.242404] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[   51.103789] usb 3-3: reset high-speed USB device number 2 using xhci_hcd
[   85.112154] snd_hda_codec_hdmi hdaudioC0D0: HDMI: invalid ELD data byte 27
[   90.049462] wlx00265a834cdb: authenticate with e4:9e:12:b4:d4:7c
[   90.905260] wlx00265a834cdb: send auth to e4:9e:12:b4:d4:7c (try 1/3)
[   90.907102] wlx00265a834cdb: authenticated
[   90.908054] wlx00265a834cdb: associate with e4:9e:12:b4:d4:7c (try 1/3)
[   90.911810] wlx00265a834cdb: RX AssocResp from e4:9e:12:b4:d4:7c (capab=0x411 status=0 aid=1)
[   91.123235] wlx00265a834cdb: associated
[   92.025453] IPv6: ADDRCONF(NETDEV_CHANGE): wlx00265a834cdb: link becomes ready
[   93.158966] rfkill: input handler disabled
[  228.554600] wlx00265a834cdb: deauthenticating from e4:9e:12:b4:d4:7c by local choice (Reason: 3=DEAUTH_LEAVING)
[  229.340363] xhci_hcd 0000:03:00.0: WARN Set TR Deq Ptr cmd failed due to incorrect slot or ep state.
```

Does anybody have any idea what I should look for ?

Best regards,
Jean-Michel

---

