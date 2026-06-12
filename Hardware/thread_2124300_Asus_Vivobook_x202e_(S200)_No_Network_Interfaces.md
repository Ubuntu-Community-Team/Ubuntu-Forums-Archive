---
title: "Asus Vivobook x202e (S200) No Network Interfaces"
date: 2013-03-10
forum: Hardware
---

### Post by BrokenKingpin on 2013-03-10
I just bought an Asus Vivobook x202e (S200) laptop, and after disabling secure boot and booting Ubuntu 12.10 off of a USB stick I noticed that it is not seeing the network adapters (wired or wireless). I have also tried Linux Mint and it is also not seeing anything. I think the wireless is a Broadcom, wired is a Atheros 8162. I don't care if I can't get the wired working, but I need the wireless. Might be hard to get the one working without the other. I have seen other postings indicating the wireless works on this laptop under Ubuntu, so I am not sure why it isn't on mine (works under Win8). Any ideas?

---

### Post by sanderj on 2013-03-10
The usual recipe:

```
lspci | grep -i net
lsusb
```

... and google the unique network names.

Furthermore: I would download Ubuntu 13.04 daily from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) and if that sees your hardware

---

### Post by BrokenKingpin on 2013-04-04
Thanks for the suggestion... I put a nightly build of 13.04 on and the Ethernet worked out of the box, and the wireless worked by installing the restricted driver. I could not be happier. The only thing that is not working is the bluetooth, but I will open a new thread about this.

---

