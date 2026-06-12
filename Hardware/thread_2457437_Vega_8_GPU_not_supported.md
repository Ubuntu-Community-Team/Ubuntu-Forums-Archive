---
title: "Vega 8 GPU not supported?"
date: 2021-02-02
forum: Hardware
---

### Post by hacktech10 on 2021-02-02
I have an Acer swift 3 with Ryzen 5 3500u and Vega 8 graphics and i really want to put ubuntu on it, no matter what linux os i try the grub works then the loading screen will sit for about a minute before it stutters once then freezes. i know its a problem with support on my GPU and on the latest kernel that is on 20.+ should support it. when i boot with text it says "vgacon disables amdgpu kernel modesetting"
I've tried amdgpu.dc=0 and = 1 and nomodeset and many others and i still cant get it to work. I'm not greatly profficient with linux but i think it has to do with it trying to apply drivers when loading the OS. Can someone please help?

---

### Post by howefield on 2021-02-02
Support request, so moved to the "*Hardware*" firum.

---

### Post by CelticWarrior on 2021-02-02
[COLOR=#000000]Ryzen 5 3500u and Vega 8 graphics is perfectly supported. Not long ago I installed one from another manufacturer and it works beautifully. The problem, if any, must be specific to yours.

Make sure you installed in UEFI mode with Secure Boot disabled. Also update UEFI ("BIOS") if there's an update available (very likely it is one already, even brand new computers nowadays need a firmware update).[/COLOR]

---

