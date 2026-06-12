---
title: "My iPod woes"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by credo on 2005-05-16
Hey all
Im running Hoary. I have a 1st Gen Ipod (with the moving wheel), using Firewire.
I am getting increasingly irritated with iPod support for linux. Here are some of the things that happen to me:

1) The iPod won't Mount (50% of the time):
I know that my iPod *can* mount, because it happens the other 50% of the time. I know the kernel modules are all there. So how come sometimes it mounts (big "no-entry" symbol on my iPod screen),  and sometimes it doesnt (big "tick" on my ipod screen).

Its not as though I can mount it manually - the device nodes are not created!

Here is dmesg:```
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[000a270002057f3e]
ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0800FFC0
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ohci1394: fw-host0: SelfID received, but NodeID invalid (probably new bus reset occurred): 0800FFC0
ieee1394: Error parsing configrom for node 0-00:1023
ieee1394: Error parsing configrom for node 0-01:1023
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
```

2) When synchronizing with gtkpod, all my songs disappear (10% of the time)
Every nown and again, once iv finished syncing, I take my ipod out and turn it on. All my songs have dissappeared. I plug the ipod back in, and it see's all the songs as "orphaned". It takes me a good half an hour to sort this mess out

3) When synchronizing with gtkpod, the new songs I'v added dont actually add (5% of the time)

4) When synchronizing with gtkpod, the ipod database corrupts (10% of the time)
Songs have dissappeared, and gtkpod can't re-read the database. Results in me having to format the device.

Can anyone help me?

---

### Post by mushupork on 2005-05-26
Make sure your iPod firmware is updated.  There is an iPod Updater available at Apple's web site.  My 3G iPod mounts 100% so far.

---

