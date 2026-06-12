---
title: "HP Pavilion a1210n - cannot install (SATA reason?)"
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by OMNIpotus on 2008-01-31
I've tried 4 different versions of Ubuntu and each one has differing success, on top of trying FreeBSD and SuSE.  About the only progress I've made was with the Live amd64 version of 7.04 (though it may have been feisty... I've honestly lost track).  The problem appears to be the SATA hard drive on my computer because I was able to boot into the desktop of the Live CD but it could not detect my hard drive to install or partition.

I've tried varying BIOS settings, but none of them are anything that anyone else seems to have.  The drive is listed in the BIOS as a TSS-something (sorry, at work).  My friend was telling me something about my SATA being on a different thread or IRQ because the hard drive is detected very late into the boot (of Windows).  Windows (all flavors) has had no problems installing or detecting the HD.

If anyone has any tips I'd appreciate the time.

HP Pavilion a1210n ([CNET comp specs]("http://reviews.cnet.com/desktops/hp-pavilion-a1210n-athlon/4507-3118_7-31518256.html?tag=sub"))
HD 200g SATA 7200 RPM

---

### Post by Yellow Pasque on 2008-01-31
There are some ideas here: [http://www.planetamd64.com/index.php?showtopic=7390](http://www.planetamd64.com/index.php?showtopic=7390)

---

### Post by OMNIpotus on 2008-02-16
OMG, here's the answer.  I'm posting this from Ubuntu because of redsync
[http://ubuntuforums.org/showthread.php?t=299929](http://ubuntuforums.org/showthread.php?t=299929)

---

