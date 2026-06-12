---
title: "External drive question"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by hatewindows on 2009-04-03
Hello all--I installed ubuntu on a usb Ext HD and all works ok--However it seems to ONLY boot up when the ext drive is plugged into the machine that set up the drive in the first place.. When i plug my Ext drive into another computer--I get a grub error--it doesnt come up with a menu like it does on my main machine that set up the ext hd with ubuntu.. I did everything correctly--copied the boot sector to the ext drive--what could be wrong? Thanks so much..  MARK

---

### Post by shane8002 on 2009-04-03
Are you trying to use the drive so you can just plug it into any computer and use ubuntu?

---

### Post by hatewindows on 2009-04-03
Yes

---

### Post by shane8002 on 2009-04-04
Im not sure that would work because it installs packages based on your hardware. Its not going to boot because it's not a .iso bootable image.

---

### Post by dandnsmith on 2009-04-04
> I did everything correctly--copied the boot sector to the ext drive--what could be wrong?
I'd guess that it is due to the differences in drives between the 2 PCs.
The boot sector carries a memory of which drive grub thinks it has to boot, which doesn't accord with the new setup.

You imply that it still works on the original setup - is that so?

---

### Post by hatewindows on 2009-04-04
Yes it always boots on the machine that installed ubuntu onto the ext drive...

---

### Post by dandnsmith on 2009-04-05
Right - so you need to reinstall grub to the external HDD in the new environment, so it can get it right.

---

