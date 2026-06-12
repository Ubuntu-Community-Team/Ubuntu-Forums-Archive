---
title: "I need some help here!!!"
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by Deadlnynightshade on 2006-04-23
I got this comp from a friend of mine and it won't boot. It keeps prompting for an ubuntu user login without this password/login it will not continue the boot up process. I spoke with the previous owner of the comp and he says he has no idea what the user login is, he never had to do that. I also can't get into safe mode to try to get the the comp to boot... can anyone help me out with this "user login" thing, I have no idea what to do.

---

### Post by Ensnared on 2006-04-23
Sounds like a BIOS password... When does it show up, and what exactly does it say? Does it show up before the GRUB bootloader, or is it the GRUB bootloader asking for a password?

If it's a BIOS password that prevents you from booting from a floppy or CD as well, then you have to figure out how to remove it - this can usually be done by contacting customer support for the computer in question. It can also be done by either a jumper-setting on the motherboard or removing the BIOS battery for a few minutes with no power connected to the PC, but this seems to vary a lot between models.

If it's a GRUB password then I have no idea how to circumvent it - I've never even had that set up, and I thought GRUB only allowed for passwords to edit the bootmenu on the fly, not to actually boot the system, but don't quote me on that ;)

Anyway, if the previous owner used the computer and never needed a password I'd say this whole thing seems a tad suspicious. I've worked with customer support, and in most cases where issues like this has popped up it's been because someone's sold a stolen computer - I'm not saying that's the case here, but if you can't boot the computer without a password, then the previous owner couldn't either - computers do a lot of weird stuff but they don't suddenly decide to password-protect themselves ;)

---

