---
title: "Wireless + Audio"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by #Reistlehr- on 2007-02-04
Hey guys, took me a while to get the nVidia drivers installed but i got it. Next feat was the wireless and audio. The audio stopped working once nVidia was installed.

```
mike@ubuntu:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: HDA Generic [HDA Generic]

```

Now, i tried that asla stuff, but that was a no go.

the wireless

```
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

```

i tried ndiswrapper, but when i rebooted, it wouldnt even recognize the wireless adapter. when i try to delete the driver, it says it cant find it, when i try to get the version with ndiswrapper -l, it says bcmwl5: invalid driver!

any pointers would be the best.


Edgy, AMD64.

---

### Post by #Reistlehr- on 2007-02-06
just wondering if anybody would happen to know of anything i could try

---

