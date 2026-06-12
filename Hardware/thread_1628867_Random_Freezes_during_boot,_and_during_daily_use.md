---
title: "Random Freezes during boot, and during daily use"
date: 2010-11-23
forum: Hardware
---

### Post by Sh4wn on 2010-11-23
Hi guys,

I have installed Ubuntu on my **HP Compaq Mini 311c**. Unfortunately I have a few problems with it. It freezes randomly.

- Sometimes during boot (red dots stop blinking, and doesn't boot anymore)
- Sometimes when already booted, and during normal use of my laptop it suddenly hangs, and then nothing works anymore (mouse/keyboard/...)
- Same as above, but sometimes with kernel panic (blinking capslock light)

I have the idea it happens more often when connected the power adapter is connected.

Hardware:
- Intel Atom N270
- nVidia ION Chipset (with nvidia proprietary driver)
- Wireless chipset: 03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
- Touchpad: ALPS

If you need more information please tell me, I will add it as soon as possible.

Thanks in advance.

---

### Post by Fafler on 2010-11-23
The most obvious thing to try is memtest86+. Just install it and it will appear in the grub menu.

Have you looked in the logs?

Try this:
```
sudo cat /var/log/messages | grep -B 11 "log source"

```

It will print out the last 10 entries in the log file before it locked up.

---

### Post by Sh4wn on 2010-11-23
> **Fafler said:**
> The most obvious thing to try is memtest86+. Just install it and it will appear in the grub menu.

Have you looked in the logs?

Try this:
```
sudo cat /var/log/messages | grep -B 11 "log source"

```

It will print out the last 10 entries in the log file before it locked up.

I attached the result of the above command, I'm going to run memtest86+ now.

---

### Post by Fafler on 2010-11-23
It's hard to tell. Maybe network related, but i don't really have any ideas. Try turning acpi off. From the grub menu, select your kernel (the first entry) and press e to edit. Look for a line ending with "splash" , add "acpi=off" after it and press ctrl+x to boot. You loose powersaving and some other stuff, but it might help figuring out whats wrong.

---

