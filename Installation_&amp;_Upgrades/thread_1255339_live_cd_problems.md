---
title: "live cd problems"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by ironman357 on 2009-09-01
I downloaded a copy of the live unbuntu CD 9.04, in order to ascertain which of my three laptops would be best to install ubuntu on.  Two of the laptops failed to boot into ubuntu at all.    The other one booted into Ubuntu once, but then crashed after five minutes. They are all from different manufactures.  I recopied the live cd and download it from the website twice, and tried again on each laptop in order to make sure it wasn’t the download/cd. Should I conclude that Ubuntu can’t work on my laptops or can I go ahead with the install?

---

### Post by Swagman on 2009-09-01
If there's nothing on the drive you want to keep then... Sure go ahead.

When the install completes .. After reboot.. It will want to install about 297 updates anyway !!

---

### Post by ironman357 on 2009-09-01
but is it likely to work if the live cd doesn't. how reliable is the live cd as a test ?

---

### Post by automaton26 on 2009-09-01
It doesn't matter how many times you downloaded the .iso file or wrote it to CD.

You can only be reasonably confident that you have a proper copy of the LiveCD if you do _both_ of these:

[LIST=1]
[*]Use MD5SUM to verify that the downloaded .iso file is exactly correct.
[*]Use the "Verify" option in your CD-writing application, when writing the CD.
[/LIST]
I'd also try running memtest from the LiveCD menu, and checking the hard disk for errors. Then at least you know the laptop "should" work, but only if the hardware is supported.

---

