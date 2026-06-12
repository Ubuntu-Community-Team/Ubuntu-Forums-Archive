---
title: "Installation questions"
date: 2008-07-14
forum: General Help
---

### Post by AramilXiloscient on 2008-07-14
Hello every body! I finally got my installation CD in the mail (I ordered the free cd, it took something like 5 weeks to arrive), and I am itching to install it. But I have two questions about installing ubuntu.

Could someone give me a step-by-step instructions on how to install ubuntu onto a already partitioned drive.

And, I am wondering if I could install ubuntu onto my external hard drive. [[COLOR="MediumTurquoise"][COLOR="Purple"]Here is the drive's info.[/COLOR][/COLOR]]("http://http://www.buy.com/prod/western-digital-320gb-my-passport-elite-usb-2-0-portable-hard-drive/q/loc/101/207539405.html#cRevSec")

---

### Post by mikewhatever on 2008-07-14
Follow this guide [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall).
The installer should be able to shrink one of the existing partitions in order to create partitions for Ubuntu. Installation to an external HDD is the same, with the exception of GRUB boot loader, which should go to the MBR of the external HDD and not the internal one.

---

### Post by AramilXiloscient on 2008-07-14
I currently don't have anything on the partition. So could I shrink the partition as far as I can to freeup more space for ubuntu?

---

### Post by mikewhatever on 2008-07-14
> **AramilXiloscient said:**
> I currently don't have anything on the partition. So could I shrink the partition as far as I can to freeup more space for ubuntu?

Theoretically, yes. The questions to ask are, how far can you go, and do you need that partition. Instead of shrinking it to the size of 10 MB, wouldn't it be more logical to delete it?

---

