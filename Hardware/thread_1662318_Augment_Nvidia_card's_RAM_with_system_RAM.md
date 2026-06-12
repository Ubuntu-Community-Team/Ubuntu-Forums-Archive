---
title: "Augment Nvidia card's RAM with system RAM?"
date: 2011-01-07
forum: Hardware
---

### Post by Afisamuleal on 2011-01-07
Hello, is it possible to somehow use the system RAM for purposes of the videocard?

I have an Nvidia 7600 GT OC card with only 256 MB of memory, whereas the computer hosting said card has 8 GB of system RAM. I'm attempting to play StarCraft II in Wine, and after researching the following message, I speculate that perhaps my video card just isn't good enough.

```
fixme:win:EnumDisplayDevicesW ((null),0,0x440e7e0,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  128 (GLX)
  Minor opcode of failed request:  27 (X_GLXCreatePbuffer)
  Serial number of failed request:  2544
  Current serial number in output stream:  2545

```

Thanks,
Afisamuleal

---

### Post by 3602 on 2011-01-07
256? That's a lot. Two years ago I had 32 and I played Splinter Cell on it.
That said, I know that in Windows you cannot allocate system RAM into GRAM because, well, it just doesn't work that way. I'm not sure about Ubuntu/Linux, but I believe this is down to the hardware level.

---

### Post by mikewhatever on 2011-01-08
Actually, many graphics cards use system RAM, the so called shared memory. Check if there is an option in the BIOS to allocate more shared memory.

---

### Post by Fafler on 2011-01-08
Some cards can, but the 7600 isnt one of them. Also, i really dont think its the problem. Go to winehq.org and find starcraft 2 in the app db. The solution to your problem is probably there.

---

