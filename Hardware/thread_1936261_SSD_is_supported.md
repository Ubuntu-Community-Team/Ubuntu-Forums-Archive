---
title: "SSD is supported?"
date: 2012-03-05
forum: Hardware
---

### Post by Riot@ct on 2012-03-05
Is still necessary align SSD in Ubuntu?

Thanks in advance! :)

---

### Post by wolfen69 on 2012-03-05
From what I've read, if you choose "use whole disk" during installation, it automatically aligns. I did this, and have no issues. You may also want to add **noatime** and **discard** to your fstab entry.

---

### Post by Riot@ct on 2012-03-06
> **wolfen69 said:**
> From what I've read, if you choose "use whole disk" during installation, it automatically aligns. I did this, and have no issues. You may also want to add **noatime** and **discard** to your fstab entry.

Thank you :)

---

### Post by fjgaude on 2012-03-06
> **wolfen69 said:**
> From what I've read, if you choose "use whole disk" during installation, it automatically aligns. I did this, and have no issues. You may also want to add **noatime** and **discard** to your fstab entry.

That's all it takes with the latest SandForce controllers.

---

