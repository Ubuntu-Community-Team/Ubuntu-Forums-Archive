---
title: "[SOLVED] Grub error 17"
date: 2008-10-10
forum: General Help
---

### Post by davideotape on 2008-10-10
I recently installed ubuntu on my second hard drive, but had to remove the hard drive because I needed it in another computer. However, the grub bootloader was also installed on the windows hard drive (vista) and comes up with error 17 when I try to boot. Has anyone got any suggestions of what I can do to get the windows harddrive booting windows again?

---

### Post by caljohnsmith on 2008-10-10
> **davideotape said:**
> I recently installed ubuntu on my second hard drive, but had to remove the hard drive because I needed it in another computer. However, the grub bootloader was also installed on the windows hard drive (vista) and comes up with error 17 when I try to boot. Has anyone got any suggestions of what I can do to get the windows harddrive booting windows again?
If you have your Vista Install/Recovery CD, just go to the command line and run:
```
bootrec /fixmbr
```
If you don't have a Vista Recovery CD, you can download one [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let me know how it goes or if you run into problems.

---

### Post by davideotape on 2008-10-12
Thanks a lot, that worked a treat :)

---

### Post by caljohnsmith on 2008-10-12
Glad to hear it worked OK; cheers and have fun. :)

---

