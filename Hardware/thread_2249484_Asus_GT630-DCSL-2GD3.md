---
title: "Asus GT630-DCSL-2GD3"
date: 2014-10-22
forum: Hardware
---

### Post by andrey21 on 2014-10-22
detected to ubuntu?

---

### Post by slickymaster on 2014-10-22
> **andrey21 said:**
> detected to ubuntu?
I do not understand, this makes absolutely no sense. ^^^

Please have a read at these two threads:
[Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475&p=8920811#post8920811")
[Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945")

---

### Post by andrey21 on 2014-10-22
Asus GT630-DCSL-2GD3 this card work in ubuntu?

---

### Post by oldfred on 2014-10-22
If that is the standard nVidia card.
You may need nomodeset to install or first boot add it to grub menu. Or until you install the proprietary nVidia driver from System Settings.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]
 Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

