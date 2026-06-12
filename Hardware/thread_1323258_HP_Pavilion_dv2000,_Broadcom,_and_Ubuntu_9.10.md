---
title: "HP Pavilion dv2000, Broadcom, and Ubuntu 9.10"
date: 2009-11-11
forum: Hardware
---

### Post by linuxprowannabe on 2009-11-11
So I have ubuntu fully downloaded, and everything's great, except Ubuntu 9.10's not recognizing the Broadcom wireless I have. The little wireless switch is glowing orange (off) no matter if it's turned on or off. I can't find any solution to this - any advice?

---

### Post by agyeya on 2009-11-12
Hi
I am using a DV6-1541 HP Pavillion. I ugraded my 9.04 to 9.10. For some time my Broadcom BCM4312 was working very well.

I don't know what I did yesterday night, but now I am only able to get wired connection and no "Enable Wireless" in the network manager.

Assistance is appreciated.

---

### Post by Ayuthia on 2009-11-12
> **linuxprowannabe said:**
> So I have ubuntu fully downloaded, and everything's great, except Ubuntu 9.10's not recognizing the Broadcom wireless I have. The little wireless switch is glowing orange (off) no matter if it's turned on or off. I can't find any solution to this - any advice?

You might try System->Administration->Hardware Drivers and see if there is an option for the Broadcom card.  If there isn't, please go into the Terminal and post the results of:
```
lspci -nn
```

---

### Post by Ceadda on 2009-11-12
I had this same problem with a Broadcom 4318 after doing a few updates using a wired connection I was able to grab the restricted drivers.

---

