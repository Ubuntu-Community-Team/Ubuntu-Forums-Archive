---
title: "Security Update Breaks Networking in 8.10"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by CrunchyDoodle on 2008-12-25
I'm running ubuntu 8.10 from an external USB hard drive on my MSI Wind U100 Netbook. With a little help from this forum, I had both the wired and wireless networking working very well, in addition to Bluetooth. Since my initial installation there have been two security updates. The most recent broke networking, both wired and wireless. It does not even ask for the Keyring password which holds the wireless passkey for the NetworkManager Applet. 

My work around is to select a previous kernel from GRUB at boot up. The one that works is 2.6.27.10-generic, while the bad one is 2.6.27.11-generic. I would like to have the security updates, but would be lost without any networking.

Does anyone have a suggestion on how to get networking back with the most recent security update?

Bye.    :cool:

---

### Post by cariboo on 2008-12-26
If there really isn't anything you need that is included in kernel 2.6.27.11 I'd stick with the previous kernel release, and just get rid of the choice in /boot/grub/menu.lst.

Jim

---

### Post by CrunchyDoodle on 2008-12-26
I am not aware of anything in particular with the newer kernel, other than a bunch of security updates, that I would need. So, do I need those security updates? That's not clear.

For now, I'll select the older working kernel.

Bye.    :cool:

> **cariboo907 said:**
> If there really isn't anything you need that is included in kernel 2.6.27.11 I'd stick with the previous kernel release, and just get rid of the choice in /boot/grub/menu.lst.

Jim

---

### Post by Moop on 2008-12-26
I read where someone else had this problem and found out that the permissions had changed for networking. Check and see if the permissions are different in the old and new kernels for networking.

---

### Post by CrunchyDoodle on 2008-12-26
Yes, that seems likely. I will look into that. This would not be the first time I've had an update break ubuntu with a subtle change in permissions. You'd think this was Vista?    :rolleyes:

Bye.   :cool:


> **Moop said:**
> I read where someone else had this problem and found out that the permissions had changed for networking. Check and see if the permissions are different in the old and new kernels for networking.

---

