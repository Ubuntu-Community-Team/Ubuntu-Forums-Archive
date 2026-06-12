---
title: "Anyone with a working Bixolon thermal printer in 16.04+?"
date: 2018-01-08
forum: Hardware
---

### Post by Chemtox on 2018-01-08
Howdy,

just updated a POS terminal from 14.04 to 16.04 (fresh install), and now its Bixolon SRP-330 thermal printer it's acting up: it prints garbage and beeps like crazy with receipts that worked just fine before.

The CUPS test page itself comes out with 4-5 lines of garbage at the top, and the printer always goes completely crazy with the next print after a partial cut, so I had to disable automated cutting altogether.

The self-test print comes out just fine though, cut and everything, so it seems the problem is in the driver --all of the unified drivers at the [Bixolon site]("http://www.bixolon.com/html/en/download/download_product.xhtml?prod_id=73#link"), from v1.3.2 to 1.3.7.1.  I still have the original 1.0 driver, but it only works with old 2.4 kernels.  The scripting errors that show even in the install docs don't give me much hope for Bixolon fixing this mess, but still...

...anyone got a Bixolon working in 16.04+ to give me hopes? (before I go back to 14.04 or, yucks, switch to Winbugs, to have more than 1 year of updates...)

---

