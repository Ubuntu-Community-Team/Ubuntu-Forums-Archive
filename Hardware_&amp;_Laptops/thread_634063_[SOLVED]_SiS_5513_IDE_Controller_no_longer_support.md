---
title: "[SOLVED] SiS 5513 IDE Controller no longer supported"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by dawynn on 2007-12-07
OK -- This one continues to bug me.  I have not seen a true official answer.

There is a kernel module built to support the SiS 5513 IDE controller.  This was compiled as a module for kernels up through Feisty, and I see that it is available for all 2.6.22 kernels built for Debian -- including those in Testing and Unstable.  For some reason, however, Ubuntu has chosen to stop compiling this module for Gutsy and Hardy.

Without this module, users of SiS 5513 IDE controllers have reported a number of problems, depending on the rest of their architecture and how their drives are set up.  This ranges from a complete inability to boot up, to general intermitent crashes after boot up.

This thread shows that this module also affects users with an Intel 82801 EB / ER IDE controller:
[http://ubuntuforums.org/showthread.php?t=586894](http://ubuntuforums.org/showthread.php?t=586894)

Based on the idea that this affects both SiS 5513 and Intel 82801 EB / ER controllers, the following bugs are very possibly directly related to this one missing module.
Bug 123789, Kernel 2.6.22-x will not boot on laptop

Bug 131945, Bad recognition of DD by ata_piix

Bug 133666, please patch linux-source-2.6.22 to fix ata_piix bug

Bug 150693, stock 2.6.22 kernels don't detect both IDE HDDs anymore

Bug 152820, Upgrade to linux-image-2.6.22-14 kernel renders my PC unbootable

Bug 155702, pata_sis fails to enable udma100, which causes a long (~1min) delay at boot. Patch available!

Bug 163753, Strange ATA HD configuration

Bug 164722, kernel 2.6.22 crash on toshiba m30x-127

At this point, we know that there's a problem for many, if not all, users who have SiS 5513 IDE controllers and other similar controllers that use this module.  And I've shown and documented in several of these bugs and in the forums that the solution here is quite simple -- just to bring back the sis5513 module.

The thing that baffles me -- the kernel folk are indicating that they don't *want* to fix this issue in Gutsy.  When we know we have such an easy fix that will cure the problem, and we know the fix will isolate itself to only those who need the fix, why wouldn't we want to get this fixed, and help move Gutsy toward a truly stable system?  (I'm sorry -- I'm having trouble calling Gutsy "stable" when the powers that be choose to keep the system completely unbootable for specific known architectures)

So -- 

1) Why was the module removed in the first place?

2) What harm is there in bringing back this module?

3) If there is something we're trying to fix by removing this module, we didn't get it done in Gutsy.  If we want to try again in Hardy, that's another issue.  But for the sake of restoring capability to existing users in the stable system, can we please go with the pragmatic approach and just compile this module again (simply because -- it works)?

Cheers!

---

### Post by dawynn on 2007-12-19
I have posted updates to Bug 152820.  Feel free to review.

In my case, this ended up mostly being a documentation problem.  There were changes put into the Gutsy kernel regarding how IDE drives are addressed.  These changes were not properly documented.  That caused a HEAP of confusion, as can be seen by the number of Bugs and related forum messages.

For me, I just had to change the / (root) partition in my /etc/fstab file from /dev/hd* to /dev/sd*.  After that, I was finally able to use the stock Gutsy kernels.

My Gutsy system is working now -- with the stock kernels.  Once we see the Restricted modules for Hardy -- I'll be able to get that working also.

Cheers!

---

### Post by dawynn on 2007-12-20
Final notes -- for anyone using a SiS 5513 related IDE controller.  Note that this is one man's experience.  Your mileage may vary.

For Gutsy:
/boot/grub/menu.lst should be set to recognize the boot drive as /dev/hd* (or by UUID).  /etc/fstab should be set to recognize the / (root) partition as /dev/sd*, and all other partitions as /dev/sd*.

For Hardy:
/boot/grub/menu.lst should be set to recognize the boot drive as /dev/sd* (or by UUID).  /etc/fstab should be set to recognize all hard drives as /dev/sd*.  (Perhaps applies to CD / DVD drives as well -- I have not tested yet).

I'm guessing from what I see in some of the bug and forum messages that Gutsy was intended to completely switch over to /dev/sd* (see Bug 152820).  But, this did not work, at least for SiS 5513 controllers (perhaps related to Bug 133666).  However, Hardy does seem to be completely switched over to /dev/sd*.

Weird.  But that's how it all worked for me.

Cheers!

---

### Post by Dean Philip on 2007-12-21
so can external usb sata hdd case work ?

[http://www.amazon.com/Dekcell-External-Aluminum-Enclosure-Cooling/dp/B000I1IV34/ref=sr_1_1?ie=UTF8&s=electronics&qid=1198220353&sr=1-1](http://www.amazon.com/Dekcell-External-Aluminum-Enclosure-Cooling/dp/B000I1IV34/ref=sr_1_1?ie=UTF8&s=electronics&qid=1198220353&sr=1-1)
[http://www.cross-mark.com/black-sata-case-external-serial-univers-p-824.html](http://www.cross-mark.com/black-sata-case-external-serial-univers-p-824.html)
[http://www.compusa.com/products/product_info.asp?pfp=SEARCH&Ntt=hdd+case&N=0&Dx=mode+matchall&Nty=1&D=hdd+case&Ntk=All&product_code=52878408](http://www.compusa.com/products/product_info.asp?pfp=SEARCH&Ntt=hdd+case&N=0&Dx=mode+matchall&Nty=1&D=hdd+case&Ntk=All&product_code=52878408)

---

### Post by dawynn on 2008-02-29
I'm trying to go back and update resolutions on several of my issues.

I addressed this problem not only in the forums but also in a number of bugs that others had opened.

The official answer that I got back was this -- we should no longer be using the /dev/hd* or /dev/sd* references.  Instead, we should be using the UUID's to reference our drives.

When I first saw the UUID's, I didn't understand why they were needed.  I still have trouble with completely understanding why we need these cryptic codes.  Honestly, I understand exactly what partition /dev/hda1 or /dev/sda1 is referring to.  The UUID is completely alien to me.  On the other hand, I have seen that it works.  Both in Gutsy and Hardy (well -- it *did* work in Hardy, ever since Hardy crashed on me -- I currently can't vouch for the state of the Hardy world), the UUID references made my computer work quite well with the various partitions.

Again -- YMMV, but UUID solved my issue.

---

