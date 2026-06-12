---
title: "Wireless no longer connects at work"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by nickj6282 on 2005-11-29
I'm having a rather strange problem with my wireless networking in Breezy. I connect to our wireless router at work (a standard Linksys router, not unlike the one I use at home) and up until last Wednesday, I didn't have a problem. Now I can't seem to get the signal from my desk anymore. Windows PCs in the same room can connect without a problem, and if I go into the other room, I can connect too, but I can no longer get signal at my desk. I talked to the network admin and the router hasn't moved or changed in any way. I'm on a Dell Inspiron 600m laptop with a mini-pci Intel Pro/Wireless 2200 card. Any thoughts?

Thanks
-Nick

---

### Post by mfreeze on 2005-11-29
I had a problem similar to this the other day.  I connect at home to a wireless network with no security enabled on the router.  When I took my laptop to work instead of connecting to my WEP enabled router at my workplace, it connected to my neighbors open network.  The problem connecting back to my network seemed to be that their wireless ESSID had written itself into my configuration file. and I was no longer connecting to my system.

I don't know if this will help you or not, and you may already know this, but examine your /etc/network/interfaces file to see if you have accidentally picked up any stray information.  To connect automatically to a DHCP enabled network you should have the following lines in the file: (assuming your wireless card is ath0)

```

iface ath0 inet dhcp
auto ath0

```

If you see any other lines that may belong to another network you may want to disable the interface, edit your    /etc/network/interfaces file, and restart the interface.

This worked for me and I hope it does for you.

Best Regards,

---

