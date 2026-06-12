---
title: "[SOLVED] Lost C drive and need to recover ubuntu wubi created on D"
date: 2008-09-24
forum: General Help
---

### Post by gr8npwrfl on 2008-09-24
I had a catastrophic hard drive failure on my C drive and it is 
gone completely.

I had used Wubi to create an Ubuntu install on my D drive. The
install is still there with all the data.

I installed a new hard drive and installed a complete new install
of Windows XP with all the service packs.

How do I recover the boot menu so I can boot back into my Ubuntu
8.04 install.

I do not want to delete the installed system.

I did not know that Wubi was doing the booting not Grub. 
If I try and install Wubi again to the new C drive it wants
to remove my existing installation.

---

### Post by ago on 2008-09-25
copy  D:\ubuntu\winboot\wubildr* C:\

Then add a line to C:\boot.ini:

C:\wubildr.mbr="Ubuntu"

---

### Post by gr8npwrfl on 2008-09-28
Thank you for your response. I can see where that would work just fine.

Because I added another hard drive and changed graphic cards, what I did was backup /ubuntu to an external drive.

I then ran the wubi installer again from scratch. Copied the Wubi directory to another place, Restored the ubuntu directory and copied the new wubi directory over the old copy that was restored.

This gave me a working system with the new drive configuration and everything is fine now.

---

