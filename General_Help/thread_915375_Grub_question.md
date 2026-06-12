---
title: "Grub question"
date: 2008-09-09
forum: General Help
---

### Post by Rain724 on 2008-09-09
Hey guys! For fun I installed leopard on an external firewire/usb hard drive. My bios will not let me boot to firewire, and usb is to slow... Is there anyway i can configure the GRUB bootloader that comes with ubuntu to boot to an external hard drive through firewire?

Any help would be great!

Thanks in advance,
Rain

---

### Post by kk0sse54 on 2008-09-09
For your bios does not support it then I do not believe there is a way

---

### Post by louieb on 2008-09-09
Maybe. Just a guess but GRUB may be able to chainload Leopards own boot loader.  

a typical chainload entry looks something like this 

```
title chainload an OS
rootnoverify (hd1,0)
chainloader +1
```

May have to tweak it a little. Do a search for** chainload **on this page for more information. 
[IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by Rain724 on 2008-09-09
Thank you guys. C!oud, I probably agree with you, but im going to try what louieb said just to make sure.

I won't have to to try it to night, but ill try to get on and tell you how it goes if i have time tomorrow.

Thanks again,
Rain

---

### Post by kk0sse54 on 2008-09-10
Post back with the results because I would be interested if it works :).

---

