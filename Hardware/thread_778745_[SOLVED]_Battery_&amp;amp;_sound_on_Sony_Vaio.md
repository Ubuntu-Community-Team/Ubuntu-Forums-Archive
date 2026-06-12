---
title: "[SOLVED] Battery &amp;amp; sound on Sony Vaio"
date: 2008-05-02
forum: Hardware
---

### Post by AndyCee on 2008-05-02
I've recently installed Hardy on my wife's Sony Vaio VGN-D25G. While I'm never going to buy a notebook from Sony again...

...the only way I can get even the LiveCD to run is by adding "acpi=off" to the end of the boot command. It has remained in the grub menu.

I can't get battery status, working sound, the laptop to shut down properly or the second USB (???) working - I suspect it's because I have acpi turned off. Interestingly, wireless network works fine (though without the light).

Can anyone help? Any ideas on what I can check or change?

Cheers,
-AndyCee

---

### Post by AndyCee on 2008-05-15
Problem solved at

[https://bugs.launchpad.net/linux/+bug/191137](https://bugs.launchpad.net/linux/+bug/191137)

Apparently it's a kernel issue - solution was to remove "quiet splash" and "acpi=off" from the grub boot command, and the power cable at bootup.

I'm a little disappointed in the lack of support I got for this question, but oh well, fixed now :)

---

### Post by Xnyper on 2008-06-06
Just thought I'd mention that this problem affects the VGN-240 as well.  The provided link does contain a fix, but you have to search for it.  This worked for me:

At the install prompt (where you can choose between trying, installing, booting to first hard disk, etx...) press F6, back-arrow a few spaces and remove the word "quiet" from "quiet splash" and hit enter.

---

