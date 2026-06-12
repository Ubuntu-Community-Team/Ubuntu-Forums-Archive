---
title: "Recent kernel update kicked out my wireless - ??"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by picante on 2009-06-23
I just installed the recommended software updates, as the update manager told me to, and now my wireless connections aren't showing up at all. I suspect it may possibly relate to the big kernel update, but really I wouldn't have a clue. I had to fix my wireless a while ago by downloading a separate driver and after that it worked fine, but now it's back to its old tricks. I also tried the make file in the folder for that driver and it didn't seem to do anything.

lspci reads:

```
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

I have a feeling that's not really what my card is. I'm using a Compaq Presario C700. Anyway iwconfig reads:
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

Any help would be MUCH appreciated.

Thanks.

---

### Post by dsavi on 2009-06-23
Did you happen to download the source code for the driver and compile it? Often drivers require the kernel source to compile, so they are specific to the kernel that you have. In that case all that would be needed would be a recompilation. But I don't know what the case is with you.

---

### Post by Scott M. Sanders on 2009-06-23
You may need the Linux restricted modules or an update thereof, as I did when my Intel wireless got the boot on a kernel update. 

Seem Ubuntu and restricted wireless don't play well together, as I've seen this posted many times here.

---

### Post by picante on 2009-06-24
> **dsavi said:**
> Did you happen to download the source code for the driver and compile it? Often drivers require the kernel source to compile, so they are specific to the kernel that you have. In that case all that would be needed would be a recompilation. But I don't know what the case is with you.

Yeah it was a pretty serious ordeal of several hours messing about to get this driver to work, but some friend of my housemates who happened to be a Linux user did most of it for me. I watched, but I wouldn't really know exactly what was going on, as I've only been a Linux user as of a few months ago. What would I need to do to recompile it for the updated kernel?

Thanks a lot.

---

