---
title: "turn off HD DMA at boot time"
date: 2005-01-03
forum: Hardware &amp; Laptops
---

### Post by mrosenlof on 2005-01-03
Is there a kernel parameter (command line) that I can set in my GRUB menu so that DMA will be turned off at boot time?

I'm booting a mini-itx board with a compact flash disk in an IDE adapter (minimal configuration).  I get several errors about DMA timeouts after the 'starting Ubuntu' message at bootup.  It takes a very long time to get to the point where init starts up and then the boot seems to progress at a more or less normal speed.

thanks for any help!

---

### Post by twisted_steel on 2005-01-03
To disable DMA completely, it looks like the parameter is  ```
ide=nodma
```
    If you only want to disable DMA on a specific drive, the parameter is  ```
hda=nodma
```  where hda is the device.

---

### Post by mrosenlof on 2005-01-04
Thank you!

The ide=nodma parameter got me past this.

---

