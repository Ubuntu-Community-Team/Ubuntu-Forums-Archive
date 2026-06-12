---
title: "Installing drivers for nvidia 520M"
date: 2016-06-01
forum: Hardware
---

### Post by pradeep22 on 2016-06-01
I am using ubuntu 14.04 LT machine..S..Few days back i tried to play video on the machine. but the video quality was very poor..So i install Nvidia 352 driver and reboot machine. As ubuntu goes in some type of error..So i googled where someone advised to remove nvidia using purge command..After that ubuntu boots successfully but video problem still arise..So is there any solution for that. as my laptop have two graphics cards..

---

### Post by Bashing-om on 2016-06-01
pradeep22; Hello;

Show us what we are working with:
```

lspci -k | grep -EA2 'VGA|3D'

```

And what is presently installed for drivers:
```

dpkg -l | grep -i nvidia
lsmod | grep nvidia

```

[INDENT][INDENT]match up the hardware/drivers
[INDENT][INDENT]be good to see
[/INDENT][/INDENT][/INDENT][/INDENT]

---

