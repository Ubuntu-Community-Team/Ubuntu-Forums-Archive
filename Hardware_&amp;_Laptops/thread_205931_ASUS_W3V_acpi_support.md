---
title: "ASUS W3V acpi support"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by deldar on 2006-06-29
Hi all,

   I've been hit by the freeze bug upon install time (after a fine install, boot stops displaying "mounting root filesystem") on my Asus W3V.

   This turned out to be a problem with acpi : acpi=off into boot options "solved" it ... but of course, no acpi support means no proper battery control etc ...

   I've seen some posts on the linux kernel mailing lists about acpi support for this laptop lately (but I can find the url now ... should have bookmarked) ... so upgrading the kernel might be a good shot.

   Someone tried to upgrade to 2.6.17.1

Best,

Update : see my message below

--
deldar

---

### Post by jeremytaylor on 2006-06-29
Hi there,
I have an w3v too and am happily using the 2.6.17 kernel with no major problems. 
jeremy

---

### Post by Hellkeepa on 2006-06-29
HELLo!

Tried to give it 5 to 10 minutes to boot on, or just did as I and waited for a few secs before thinking it had crashed?
If it does indeed take long to boot, after it has uncompressed the kernel, then you might want to try the -386 kernel; I did not have this problem on it, as well as another one.

More details about the latter issue in this thread:
[http://ubuntuforums.org/showthread.php?t=204100](http://ubuntuforums.org/showthread.php?t=204100)

Happy codin'!

---

### Post by deldar on 2006-06-30
I tried the 386 kernel ... but I had to disable acpi as well in order to be able to boot ...
I guess I'll try to compile my own 2.6.17.2 kernel ...

---

### Post by deldar on 2006-06-30
I just installed a new 2.6.17.2 vanilla kernel
- download from kernel.org
- download patch for suspend2
- pactch kernel
- tweak kernel config a bit
- create ubuntu packages
- install new createdp packages

ACPI seems to be working :
- no acpi=off is needed to boot
- battery charge is accurate
- using acpi suspend in suspend2 config seems to work (!)

---

