---
title: "Boot with readonly root"
date: 2008-08-08
forum: General Help
---

### Post by imangh on 2008-08-08
Hello
I want to use old PCs as disk less thin clients, I configured an Ubuntu server for PXE netboot and used Ubuntu desktop to load on clients, now I want to make nfsroot read only to prevent the clients to damage Ubuntu desktop files but I couldn't do it because GNOME will fail during boot. I try to follow an online manual but I couldn't because it is about Gentoo linux.([http://gentoo-wiki.com/HOWTO_Read-only_root_filesystem](http://gentoo-wiki.com/HOWTO_Read-only_root_filesystem))
Would you please tell me how boot a Ubuntu with readonly root partition?

thanks a lot

---

### Post by dcstar on 2008-08-08
> **imangh said:**
> Hello
I want to use old PCs as disk less thin clients, I configured an Ubuntu server for PXE netboot and used Ubuntu desktop to load on clients, now I want to make nfsroot read only to prevent the clients to damage Ubuntu desktop files but I couldn't do it because GNOME will fail during boot. I try to follow an online manual but I couldn't because it is about Gentoo linux.([http://gentoo-wiki.com/HOWTO_Read-only_root_filesystem](http://gentoo-wiki.com/HOWTO_Read-only_root_filesystem))
Would you please tell me how boot a Ubuntu with readonly root partition?

thanks a lot

Set it up like a USB "Live" disk:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by imangh on 2008-08-08
Thank you, but actually I need Non Persistent clients.

---

