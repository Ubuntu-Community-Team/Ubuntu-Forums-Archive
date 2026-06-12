---
title: "Grub and CD-ROM"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by SlayerMan on 2007-06-05
Hi all,

I've got a little problem running Ubuntu Feisty on an older laptop. The thing is, the laptop has a cd drive which is slightly defetive, i.e. it doesn't recognize if a cd is in it or not. So when there is no cd in the drive, it tries to read the (non-available) cd for a long time before giving up.

Now my problem is that the first stage of grub seems to somehow access the cd drive, leading to a long delay (> 1 minute) before the boot menu appears.

Is there something that can be done about this problem? Maybe some switch for grub so that it does not try to access the cd drive?

Unfortunately, repairing the cd drive is not an option.

Kind Regards
SlayerMan

---

### Post by mikewhatever on 2007-06-05
I'd say that's not grub but BIOS. Enter the BIOS setup and make sure booting from cd-rom is disabled.

---

### Post by SlayerMan on 2007-06-05
Hmm, are you sure? The display shows "GRUB stage (don't remember right now) loading", and after that the drive starts up (whirring around for a minute, after which the boot menu eventually gets displayed).

---

### Post by mikewhatever on 2007-06-05
No, I am not sure, but since the cd-rom does not really work, it would not hurt trying. Besides, GRUB reads nothing from cd-rom to the very best of my knowledge.

---

### Post by SlayerMan on 2007-06-06
Hmm, I just checked the BIOS settings, and the boot sequence is set so that it first tries to boot from HDD. The laptop at hand isn't mine, but from a person who kindly asked me to install Linux onto it (it's a new Linux user). The problem is, of course, not Ubuntu's fault, but nevertheless I am searching for a workaround. Maybe switching to LILO could help? Could somebody point me to a guide how to (gracefully) switch Ubuntu's bootloader from GRUB to LILO?

---

### Post by SlayerMan on 2007-06-06
I found a simple but working solution: I disabled the whole drive in the BIOS. It still tries to access the non existing cd, but grub doesn't freeze anymore and the system boots up fine.

---

