---
title: "need help with GRUB"
date: 2008-11-25
forum: General Help
---

### Post by unbuntunoob321 on 2008-11-25
last night on my laptop i wanted to partition my hard drive and get rid of ubuntu and reinstall it again off my ubuntu disk

after i got rid of ubuntu on my hard drive i get this error message from grub after restarting my computer

"GRUB Loading stage1.5.

Grub loading, please wait...
Error 17"

i cant get on my computer at all

what should i do?

---

### Post by Gonz_91 on 2008-11-25
Have you simply formatted the Ubuntu partition?

Are you dual-booting Windows?

---

### Post by unbuntunoob321 on 2008-11-25
> **Gonz_91 said:**
> Have you simply formatted the Ubuntu partition?

Are you dual-booting Windows?

yes to both

i had grub to dual boot, but now all i get is that error message

---

### Post by djbushido on 2008-11-25
If you are just running windows, load up the install disk, and at the recover console run "fixmbr". This will fix your drive for windows.

NOTE: this assumes that your linux partition is gone. If not, hell will ensue. Been there. Done that.

EDIT: if you don't have any files you need on your windows partition, and that is the only partition, you can reinstall windows, and then resize the ntfs partition and dual boot. Otherwise, prepare for manual partitioning and manual grub setup.

---

### Post by caljohnsmith on 2008-11-25
If you are going to reinstall Ubuntu, just go ahead and do so, and it should install Grub again so you can boot Windows or Ubuntu. If for some reason you need to immediately get into Windows before installing Ubuntu, you can do as djbushido's suggested and run "fixmbr" from the "recovery console" of the Windows Install CD. Or you can download the [Super Grub Disk]("http://www.supergrubdisk.org") to install a Windows MBR that way. Let us know how it goes or if you run into problems. :)

---

### Post by unbuntunoob321 on 2008-11-25
> **djbushido said:**
> If you are just running windows, load up the install disk, and at the recover console run "fixmbr"

NOTE: this assumes that your linux partition is gone. If not, hell will ensue. Been there. Done that.

ok i have never had to load the install disk before, i have it right here

im not sure how to boot from the install disk, if i just throw the disk in will it automatically load up?

---

### Post by djbushido on 2008-11-25
make sure your BIOS is set to boot from CD, but otherwise yes, the cd will boot itself.

---

### Post by unbuntunoob321 on 2008-11-25
it didnt automatically boot from the cd for me i had to press f12 at the boot up and select boot from cd/dvd drive 

but i think im fixing it 

...i think

---

### Post by djbushido on 2008-11-26
write another post if something else goes wrong, we'll be happy to help you fix it.

---

