---
title: "Dual boot Vista and Ubuntu"
date: 2008-07-25
forum: General Help
---

### Post by scottybowl on 2008-07-25
I had Ubuntu installed on my laptop, I have since resized one of the ext partitions on Ubuntu and formatted it for NTFS. I succesfully installed Vista on this new partition but don't have the option to boot into Ubuntu any more (it goes straight to booting Vista).

How can I have the boot menu to decide which OS to load up?

Thanks!

Scott

---

### Post by dcstar on 2008-07-25
> **scottybowl said:**
> I had Ubuntu installed on my laptop, I have since resized one of the ext partitions on Ubuntu and formatted it for NTFS. I succesfully installed Vista on this new partition but don't have the option to boot into Ubuntu any more (it goes straight to booting Vista).

How can I have the boot menu to decide which OS to load up?

Thanks!

Scott

Do a forum search for reinstalling Grub - and then on adding in a Windows boot option.

---

### Post by scottybowl on 2008-07-25
ive had a look but none of them seem to be the same scenario as what i have... 

i.e. ubuntu installed, vista installed, needing to boot to both AFTER both are installed

---

### Post by bryncoles on 2008-07-25
ive read about this issue - problem is (as i understand it) windows overwrites grub bootloader with its own MBR, which of course does not recognise ubuntu!

usually, people recommend downloading the subergrub boot disc

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

which you can download and burn, and use to restore grub (which will let you boot windows and ubuntu. hurrah!

cant walk you through it im afraid - but the online documentation should help you....

good luck!

---

### Post by scottybowl on 2008-07-25
found the solution (If youve already installed both and its booting to Vista)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5)

That page is all you need - worked a dream and only took 5 minutes, am now able to dual boot :)

---

