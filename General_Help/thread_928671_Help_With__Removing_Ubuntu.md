---
title: "Help With  Removing Ubuntu"
date: 2008-09-24
forum: General Help
---

### Post by liljak on 2008-09-24
Removing Ubuntu From a Vista + Ubuntu Dual-Boot

Now i know there are a fwe threads on this topic already but i what to make sure im getting the correct info as i dont really what to loss everything on my HDD so please bear with me.

Ok so i have read that first i need to remove grub and this is done by inserting the vista installation disk and running something called fixmbr (if someone can give instruction on how to run that would be great) once that has been run windows vista should boot straight into vista now i read that i can now remove the ubuntu partition via vista partition tool and then ubuntu should be gone with no errors what so ever im hoping to if someone can tell me if this all i correct and will work with no problems i would be very great full and if im wrong somewhere please so say i really dont what to mess you my HDD and can not back it up :cry: lol so thanks in advance for your help!

---

### Post by mike1821 on 2008-09-24
This will do the job required!

---

### Post by mike1234 on 2008-09-24
> **liljak said:**
> Removing Ubuntu From a Vista + Ubuntu Dual-Boot

Now i know there are a fwe threads on this topic already but i what to make sure im getting the correct info as i dont really what to loss everything on my HDD so please bear with me.

Ok so i have read that first i need to remove grub and this is done by inserting the vista installation disk and running something called fixmbr (if someone can give instruction on how to run that would be great) once that has been run windows vista should boot straight into vista now i read that i can now remove the ubuntu partition via vista partition tool and then ubuntu should be gone with no errors what so ever im hoping to if someone can tell me if this all i correct and will work with no problems i would be very great full and if im wrong somewhere please so say i really dont what to mess you my HDD and can not back it up :cry: lol so thanks in advance for your help!

 Here is a link to MS.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

M.

---

### Post by liljak on 2008-09-24
Thats great guys thanks for telling me it will work and thanks for the link ^^

---

### Post by caljohnsmith on 2008-09-24
In case you are unclear about that Microsoft link, the bottom line is that from your Vista Install CD you should run:
```
bootrec /fixmbr
```
That should be all it takes. :)

---

