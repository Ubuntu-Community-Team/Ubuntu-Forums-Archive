---
title: "[SOLVED] Where do I delete from grub?"
date: 2008-09-27
forum: General Help
---

### Post by kokkus on 2008-09-27
HI. I installed virtualbox for some reason.
I removed it because I don't need it.
Now there are 100s of useless stuff on my grublist.
I though startup manager could help me but I can't delete from grub with startup manager.
And why didn't they escaped from grub when I removed virtualbox?
Thanks.

---

### Post by lisati on 2008-09-27
I'm confused as to the connection between virtualbox and grub.

Short of getting in and editing grub's menu.lst manually, you can sometimes do a clean-up with the following command: ```
sudo update-grub
```

---

### Post by kokkus on 2008-09-27
I got 3 doubled up everything on grub. 3 Generetic, 3 Virtual, 3 server, but for some reason only 1 with windows xp professional.
 I though the reason was because of virtual box since it happend right after i installed it.
Btw. Thanks. I hoped I didn't have to do it manually since there were like 20 things in grub, but it works fine now.
Hmm, how could that waired thing happen?

---

### Post by lisati on 2008-09-27
> **kokkus said:**
> I got 3 doubled up everything on grub. 3 Generetic, 3 Virtual, 3 server, but for some reason only 1 with windows xp professional.
 I though the reason was because of virtual box since it happend right after i installed it.
Btw. Thanks. I hoped I didn't have to do it manually since there were like 20 things in grub, but it works fine now.
Hmm, how could that waired thing happen?

Sometimes there are two lines with the same version number, with one a "recovery mode" startup.

---

### Post by kokkus on 2008-09-27
> **lisati said:**
> Sometimes there are two lines with the same version number, with one a "recovery mode" startup.
Hehe I know that. But they were also 3 doubled.
Very strange.
Anyway, everything works fine now.
THanks:)

---

