---
title: "Unable to use desktop effects after upgrade to 8.10"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by dutchstriker on 2008-12-04
I had been using compiz effects on 8.04 without any problems.  When I upgraded to 8.10, I could no longer use them.  The computer won't let me switch from None to Normal under Visual Effects (System->Preferences->Appearance->Visual Effects).  Initially, it told me it couldn't do it.  After fiddling with compiz-check, it now freezes if I attempt to switch it or type "compiz" in the terminal.

Additional potentially useful information:
Typing "lspci | grep -i graphic" in the terminal yields:
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

Is my graphics card no longer supported by 8.10 or something?  Thanks for any help!

---

### Post by inobe on 2008-12-04
hi, have you read any bug reports before upgrading to a non LTS version ??

[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

scroll down in the link

---

### Post by dutchstriker on 2008-12-05
Ah... I did read that... Well, most of it anyway.  That's way at the bottom!  Who has time for that?

---

