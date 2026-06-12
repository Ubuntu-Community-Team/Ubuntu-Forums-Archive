---
title: "dual booting with vista - graphics chip problem"
date: 2009-05-19
forum: Hardware
---

### Post by BeccaPA on 2009-05-19
I recently installed Ubuntu 9.04, and discovered that my Intel graphics chip had been blacklisted and therefore I was unable to enable visual effects. I found the command to override this, and everything went smoothly. However, today I decided to dual boot with Windows Vista, and it can't seem to install my graphics card correctly. Is this problem related to what I've done in Ubuntu?

---

### Post by coffeecat on 2009-05-19
> **BeccaPA said:**
> Is this problem related to what I've done in Ubuntu?

Extremely unlikely. The only way I can think you could affect Vista is by reconfiguring the BIOS. If what you've done is an edit of xorg.conf (I would guess that's the "command to override this") then it's impossible. Vista can't read Linux filesystems (unless you install a special driver) and even if it could read your Ubuntu filesystem, it's not going to unless you run a Vista executable to do so.

Post this override command - better still a link to it -  and then we can see.

Also, post details of your Intel graphics chip. It might just be a Vista issue with this particular chipset.

---

