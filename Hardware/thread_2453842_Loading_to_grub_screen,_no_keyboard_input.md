---
title: "Loading to grub screen, no keyboard input"
date: 2020-11-17
forum: Hardware
---

### Post by xibakon on 2020-11-17
I installed Ubuntu today and I wanted to switch back to windows so I restarted my computer. After I did that I could not pick my OS and it took me to the GNU GRUB screen. In there I cannot type and I cannot go to my BIOS screen. Could I get any help?

---

### Post by CatKiller on 2020-11-18
The issue is that in the pre-OS environment there isn't support for elaborate hardware. UEFI can emulate that support, by making newer hardware appear to be older hardware, but it needs to be enabled and it won't necessarily work for everything. In particular, even if it would work if it were enabled, not having it enabled means that you can't get into the UEFI setup to enable it.

So, the easy option is to plug in an old keyboard.

The slightly more complicated solution (which also works for when you've inadvertently enabled Fast Boot, which *also* prevents you entering the UEFI setup) is to run ```
systemctl reboot --firmware-setup
```

That will reboot you into your UEFI setup, where you can enable the emulation of old input devices. If neither your keyboard nor your mouse works in your UEFI setup, you'll still need to find an old keyboard to plug in.

---

### Post by xibakon on 2020-11-18
Okay I’ll try that. Does it matter if it’s in USB 2.0 or USB 3.0?

---

### Post by xibakon on 2020-11-18
[FIXED] I tried plugging in an old keyboard and still no response. I even tried taking out the CMOS battery and that did nothing to help.
Update: I got it working. Thank you for your help!

---

### Post by CatKiller on 2020-11-18
> **xibakon said:**
> Okay I’ll try that. Does it matter if it’s in USB 2.0 or USB 3.0?

Depends on the keyboard, and depends on the port. There are keyboards that won't work in USB 3 ports.

---

