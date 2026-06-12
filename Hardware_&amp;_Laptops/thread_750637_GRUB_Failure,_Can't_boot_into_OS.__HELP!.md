---
title: "GRUB Failure, Can't boot into OS.  HELP!"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by bpcrshooter15 on 2008-04-09
I just deleted my Linux partition to give me some my hard drive room for a music project i was working on.     So i exteneded my windows partition and when i rebooted a little while ago the grub menu still tries to load but all it says is
"GRUB"
and hangs there.  I can't reinstall the linux distro because now i don't have enough room to dual boot apparently and I don't have a Vista disk, just the reinstallation disk from Dell.  

How can i get back into Vista, fix/remove grub, or whatever to not lose my data?

---

### Post by ibutho on 2008-04-09
You could get the [super grub disk]("http://supergrub.forjamari.linex.org/") which is a small live cd that can help remove (or reinstall) grub.

---

### Post by kutjara on 2008-04-09
> **bpcrshooter15 said:**
> I just deleted my Linux partition to give me some my hard drive room for a music project i was working on.     So i exteneded my windows partition and when i rebooted a little while ago the grub menu still tries to load but all it says is
"GRUB"
and hangs there.  I can't reinstall the linux distro because now i don't have enough room to dual boot apparently and I don't have a Vista disk, just the reinstallation disk from Dell.  

How can i get back into Vista, fix/remove grub, or whatever to not lose my data?

The reinstallation disk should give you the same boot options as a regular Vista disk. Just boot from it and choose the "repair" option. That'll fix your MBR and you'll be able to boot normally.

Failing that, download the ISO from [http://www.ultimatebootcd.com/index.html](http://www.ultimatebootcd.com/index.html) and burn an Ultimate Boot CD, which has tools to get your MBR back.

---

### Post by bpcrshooter15 on 2008-04-10
ok, thanks for the responses.  is there any risk of losing any data or hard drives getting formatted if I use the System Repair thing that is on my Dell Reinstallation disk?  or any particular way I should go about doing it (such as which options to select when using the system restore)?

---

### Post by kutjara on 2008-04-10
> **bpcrshooter15 said:**
> ok, thanks for the responses.  is there any risk of losing any data or hard drives getting formatted if I use the System Repair thing that is on my Dell Reinstallation disk?  or any particular way I should go about doing it (such as which options to select when using the system restore)?

Surpirsingly for a Microsoft product, System Repair works well. It'll just fix your MBR and you'll be all set. It doesn't monkey around with anything you don't want it to.

---

