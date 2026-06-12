---
title: "External SSD not recognized"
date: 2021-04-15
forum: Hardware
---

### Post by edmondo2 on 2021-04-15
Goodmorning everyone.


Two weeks ago I had a problem with my SSD on which I had a double partition for Ubuntu 18 and Windows. As for Ubuntu I was able to log in but any application I tried to start froze my operating system. But the data was visible. I took my PC to the technician who suggested changing the SSD as he said it broke. After that he changed it for me and gave me the removed SSD.


To which I bought an interface (M.2 SATA to USBB 3.1 Gen. 1) to try to recover some data left over on the old SSD but unfortunately, upon connection, I am unable to see anything with my current Ubuntu version and working.


Could you kindly help me?

PS I also made an attempt to alter the order of the Bios, giving priority to the USB port, but the laptop cannot get it started. This worries me a lot because in any case, before taking it to the technician, at least I was able to start it even if it was unstable.

---

### Post by yancek on 2021-04-15
Is your old SSD shown in the BIOS firmware?
Generally, external drives will be available under the /media/username directory (substitute your actual username).  Do you see it there?

---

### Post by edmondo2 on 2021-04-15
> **yancek said:**
> Is your old SSD shown in the BIOS firmware?
Generally, external drives will be available under the /media/username directory (substitute your actual username).  Do you see it there?

Dear yancek,

thanks for your reply.

Unfortunately nothing is shown under the folder you indicated, just as if the SSD did not exist.

What I can't understand is why it partially worked when it was in the internal slot of the laptop.

Regarding the first question, I don't know how to answer. I limited myself, in the bios, to altering the ordering of the peripherals read but without obtaining results.

---

### Post by CelticWarrior on 2021-04-15
Too many possibilities...

The first thing you should understand is that SSDs fail catastrophically, now they "work", now they don't. It's nothing like the old HDD that could go for years with hundreds of bad sectors increasing only so slightly in some cases. With SSDs the first symptom is suddenly becoming read-only (that alone would freeze any OS running from it). So, the most likely hypotheses is now you have a total and unrecoverable failure.

Other possibility is incompatibility. M.2 drives come in two "flavors", old SATA and new NVME. USB external adapters usually support one or the other, not both (unless explicitly specified). If your drive is NVME then it won't be detected in the M.2 SATA enclosure.

Also, even when compatible "on paper" a few of those cheap adapters simply don't work with some brands of drives.

You can check with Disks. If the drive is shown and with the correct capacity but entirely blank, unformatted, then it's likely beyond any data recovery. If not present (in Disks) then it can be any of the other possibilities.

An obvious lesson to learn here is to have backups.

---

