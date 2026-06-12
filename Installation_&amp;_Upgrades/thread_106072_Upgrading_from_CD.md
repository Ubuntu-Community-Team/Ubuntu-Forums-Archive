---
title: "Upgrading from CD"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by tbobo05 on 2005-12-19
Is there anyway to upgrade from the cd? (I.E. change the repositories to point to the cd and use the smartupgrade feature)  Does anyone know of any apparent problems that may occur from upgrading from the cd? (packages becoming broken due to dependencies being upgraded maybe?) I am not exactly sure of how to go about this and what to expect, so any help would be appreciated.                               Thanks

---

### Post by matthew on 2005-12-19
I haven't tried it, but I recall hearing that if you just put a newer Ubuntu installation cd in the drive while using Ubuntu it will bring up an upgrade dialog box.

Can anyone confirm this from experience?

---

### Post by dcstar on 2005-12-19
[QUOTE=tbobo05]Is there anyway to upgrade from the cd? (I.E. change the repositories to point to the cd and use the smartupgrade feature)  Does anyone know of any apparent problems that may occur from upgrading from the cd? (packages becoming broken due to dependencies being upgraded maybe?) I am not exactly sure of how to go about this and what to expect, so any help would be appreciated.                               Thanks[/QUOTE]
Yes, you can do this.

There is a HOWTO about on what steps you need to take to have it happen successfully:

[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

Basically you have to manually add in the new CD to your repositories, and re-install some Ubuntu meta-packages (if necessary) to ensure that all things get upgraded.

Afterwards you have to manually change all other repository settings from "hoary" to "breezy" to ensure you get all the updates.

---

### Post by tbobo05 on 2005-12-20
Thanks all.   I now have a fully upgraded breezy install.  Thanks again!

---

