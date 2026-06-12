---
title: "T420 does not sleep/awake properly (22.04.4)"
date: 2024-06-29
forum: Hardware
---

### Post by csae2608 on 2024-06-29
Hello ,

i have installed Ubuntu 22.04 on a T420 with dual-graphics (Intel3000HD-Nvidia NVS 4200m)

the laptop has installed graphics driver fine and would function,
however, i went to "additional drivers" and changed from "nouveau" to "nvidia-390 (tested)" and let install things and after reboot everything seems to function well;


under "About" it shows "Graphics": NVS 4200m/PCIe/SSE2 NVS 4200m/PCIe/SSE2 twice the same entry with no mention of Intel HD 3000 anylonger, so can i suppose only Nvidia Driver is used?



the big issue is hhowever, that the laptop would not properly wake from sleep; it would somehow go into sleep it seems, but somehow remain warm;

when i open lid, the laptop would show black screen w/ error message:

```
Xhci_hcd 0000:05:00.0: cant' change power state from D3hot to D0 (config space inaccessible
```


it this behaviour fixable or should i revert to nouveau driver (and loose hence some GPU performance is suppose)

thank you very much.

---

### Post by deadflowr on 2024-06-29
Looks like your issue is well known:
[https://forums.developer.nvidia.com/t/bug-cant-change-power-state-from-d3cold-to-d0-config-space-inaccessible-stuck-at-boot/112912/18](https://forums.developer.nvidia.com/t/bug-cant-change-power-state-from-d3cold-to-d0-config-space-inaccessible-stuck-at-boot/112912/18)

I'm not sure what the fix, if any, is.

---

### Post by csae2608 on 2024-06-30
one workaround is "sudo pm-suspend" before closing-lid;

however, i noticed shutdowns with nvidia-graphics 390 here on the T420 maybe caused also by temperatures in room of around 30 Celsius centigrades;

could revert to nouveau to see if it helps with temperatures of the laptop/gpu.

---

