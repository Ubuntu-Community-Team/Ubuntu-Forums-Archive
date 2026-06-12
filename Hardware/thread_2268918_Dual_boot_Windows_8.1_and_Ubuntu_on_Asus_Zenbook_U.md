---
title: "Dual boot Windows 8.1 and Ubuntu on Asus Zenbook UX305?"
date: 2015-03-12
forum: Hardware
---

### Post by pete_m2 on 2015-03-12
I'm a Mac user (and a former Windows) user, with some limited experience with Ubuntu. I'm thinking of switching to Ubuntu, specifically the new Asus Zenbook ux305. However, I still need Windows for a number of the Adobe apps. Having searched posts re dual booting, it appears it isn't very straightforward to set up with Windows machines (?) 

Before making the purchase, I'd love to know if anyone has accomplished it with the ux305, and would be willing to share the steps taken, caveats, tips?

Also, what is the best way to share files between the two OSs?

Thanks!!

---

### Post by coffeecat on 2015-03-14
You posted this in the Windows sub-forum which is really intended for questions about Windows OS specifically. Advice on setting up a Windows/Ubuntu dual-boot and whether particular hardware is compatible with Ubuntu is really an Ubuntu question. Therefore...

*Thread moved to **Hardware**.*

---

### Post by oldfred on 2015-03-14
Best to have a separate NTFS shared data partition, but with Windows 8 you still need the always on hibernation or fast boot off.

some other Asus, usually issues are fairly command by brand, with options and market being differences in exact models. Some links are older versions of Ubuntu and newer Ubuntu should be better as newer kernel, support software & drivers.

Just checked and is that the new Broadwell chip? That may have more issues as it is so new that all the updates are not yet in recent distributions. You may even have to use the beta 15.04  which I do not normally suggest.

       UEFI may have setting that is Windows 8 or Windows 7, which probably is to turn off secure boot
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)

 Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)
 install 13.04 on asus ux32a, problems with usb boot - several reports working well no details
[http://ubuntuforums.org/showthread.php?t=2146440](http://ubuntuforums.org/showthread.php?t=2146440)

I do not know if just Dell issues or more common.

 Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
[http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)

---

