---
title: "Multiple Grub problems installing 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by HawkST on 2009-11-06
Hey guys, I tried to install 9.10 (clean install) after my 8.04 started to get a bit heavy, but have encountered some problems.

The first install appeared to run fine (I was in and out of the room but no error messages appeared to show), but when I started the computer, all that happened was it said Grub loading and nothing happened.

Then, I tried to reinstall and tinkered about a bit, which lead to grub-rescue appearing - so I reinstalled again, using the default settings again (using the option to use the whole drive for the install in the partitioner), and at 94% an error message popped up saying "unable to update-grub, this is fatal error" (or similar).

The installer then quit and went straight into the Live CD (with a little exclamation saying "ubiquity had crashed" with the title "
Ubiquity crashed with InstallStepError in configure_bootloader()"


Please help :(

Edit* it was a loose SATA power cable causing the issues! Took about 3 seconds to fix once I sorted it - it was not related to the install at all (which worked fine once this was sorted)

---

