---
title: "Installed 4Gb RAM - shows as 2.7Gb"
date: 2010-01-04
forum: Hardware
---

### Post by sml on 2010-01-04
Just installed 4Gb of RAM in my Macbook but it shows as 2.7Gb in the System Monitor and 2.8Gb in the 'top' command.

Or with 'lshw' command, system memory is 2747Mib.

Does this sound correct? Why is it not closer to 4Gb?

---

### Post by SuperSonic4 on 2010-01-04
What does your BIOS say regarding your RAM? Chances are it's an old motherboard which cannot handle more than 2.7

---

### Post by Shippou on 2010-01-04
Are you running a 64-bit OS? A 32-bit OS cannot detect 4GB of RAM exactly.

---

### Post by sml on 2010-01-04
According to the Apple specs, it supports up to 8Gb.

I am using an i686 ubuntu version. Could this be a limitation?

---

### Post by sml on 2010-01-04
> **Shippou said:**
> Are you running a 64-bit OS? A 32-bit OS cannot detect 4GB of RAM exactly.

Thanks :)

---

### Post by Shippou on 2010-01-04
Try installing a 64-bit version.

Hope this solves the problem.

BTW, also check if some of the RAM is shared. For example, I have 2.5GB of RAM, in which 500MB is shared for video (since I have no video card). So, though the system detects I have 2.5GB of RAM, I could only use 2GB for applications and stuff. The rest acts as a video card.

The setting is in the BIOS.

---

### Post by sml on 2010-01-04
Ahh .. that makes sense.

Thanks :)

---

