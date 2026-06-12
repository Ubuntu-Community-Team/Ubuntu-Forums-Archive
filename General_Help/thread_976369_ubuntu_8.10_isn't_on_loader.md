---
title: "ubuntu 8.10 isn't on loader?"
date: 2008-11-09
forum: General Help
---

### Post by Airfoot on 2008-11-09
I recently installed ubuntu 8.10 as a third os w/ vista and xp, I did the Install inside of windows option of the live cd (it's a family computer and GRUB intimidates my Mom and Bro) but ubuntu wasn't added to my windows boot menu (i did not have this problem with 8.04).  Ubuntu Was intalled fine but I cannot boot into it, is there any way to manually add ubuntu to the boot loader?

---

### Post by caljohnsmith on 2008-11-09
I would recommend reinstalling, but make sure all your antivirus/anti-malware software is completely disabled before reinstalling. That's a likely reason why Ubuntu wasn't added to your Windows boot menu. You can first uninstall Ubuntu by going to Add/Remove Programs in the Control Panel. Let me know if that helps.

---

### Post by smo0th on 2008-11-09
try installing it in a disk/partition different than xp&vi$ta

---

### Post by hendoc on 2008-11-09
Some one thinks you installed Ubuntu inside Windows. Best to just reinstall or maybe use Super Grub to repair the boot loader. You certainly are not going to find Ubuntu in your Windows Add/Remove programs. Turn off your firewall and spyware programs? Come on guys. You are being confusing.

---

### Post by caljohnsmith on 2008-11-09
> **hendoc said:**
> Some one thinks you installed Ubuntu inside Windows. Best to just reinstall or maybe use Super Grub to repair the boot loader. You certainly are not going to find Ubuntu in your Windows Add/Remove programs. Turn off your firewall and spyware programs? Come on guys. You are being confusing.
Airfoot clearly stated in his post that:
> I did the Install inside of windows option of the live cd
Installing Ubuntu inside of Windows is an option with Ubuntu now, and it is done via the Wubi program. So using Super Grub will not help him if he has Ubuntu installed via Wubi inside Windows. You might want to check out the [Wubi page at the Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide") if you are unfamiliar with Wubi. :)

---

### Post by Airfoot on 2008-11-10
Thanks, I reinstalled without my windows antivirus enabled and ubuntu was added to the loader, and thanks for the quick response time!

---

### Post by caljohnsmith on 2008-11-10
Glad to hear it worked. Cheers and have fun with Ubuntu. :)

---

