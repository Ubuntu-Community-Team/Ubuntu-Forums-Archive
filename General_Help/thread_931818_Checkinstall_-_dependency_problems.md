---
title: "Checkinstall - dependency problems?"
date: 2008-09-27
forum: General Help
---

### Post by helpdeskdan on 2008-09-27
Compiled the new gnucash and check-installed.  Worked great!  That is, till update removed all the my dependencies.  "Arg!" said I.  I thought I would try this:
(note: --fstrans=no is a workaround for a recent bug, if you haven't heard)

fakeroot checkinstall  --fstrans=no --requires guile-1.6-slib libcrypt-ssleay-perl libdate-manip-perl libfinance-quote-perl libhtml-tableextract-perl slib gnucash-common gnucash-docs

But, that gives me:
========================= Installation results ===========================
/var/tmp/HSaTcSjIllEnclRbEdABe/installscript.sh: 4: libcrypt-ssleay-perl: not found

Hmm....

$
$sudo apt-get install libcrypt-ssleay-perl
...
libcrypt-ssleay-perl is already the newest version.
$

Arg again!

So, I reinstall all my dependencies and hope they stay.  

How does one create a usable package without being a guru?

---

