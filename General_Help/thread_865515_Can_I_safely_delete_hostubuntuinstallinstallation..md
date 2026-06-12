---
title: "Can I safely delete /host/ubuntu/install/installation.iso?"
date: 2008-07-20
forum: General Help
---

### Post by dkoppenh on 2008-07-20
The title pretty much says it all.  After Ubuntu is installed to disk with Wubi, do I need to keep the /host/ubuntu/install/installation.iso around?

I know that nowadays 700MB is something to scoff at, but when you have a small, old laptop hard drive, every MB counts.

Thanks in advance,
David

PS - Why does Wubi have to create the image on the HDD in the first place?  Couldn't it just use the CD that it's running from?

---

### Post by ago on 2008-07-21
Yes you can delete it. In fact wubi rev 506 deletes by default now.

The reason we do not use a CD is that if the CD is in the tray then you boot off the CD without using the wubi directives, so we need to make sure you boot off hard disk. And in any case the installation is faster when the ISO is on HD.

---

### Post by dkoppenh on 2008-07-21
> **ago said:**
> Yes you can delete it. In fact wubi rev 506 deletes by default now.

OK, thanks!

> **ago said:**
> 
The reason we do not use a CD is that if the CD is in the tray then you boot off the CD without using the wubi directives, so we need to make sure you boot off hard disk. And in any case the installation is faster when the ISO is on HD.

That makes sense.  And since the iso is now deleted by default, the question about keeping the install 'on the CD' is less important.

David

---

