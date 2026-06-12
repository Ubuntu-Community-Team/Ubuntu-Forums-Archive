---
title: "Upgrade to Karmic failed while configuring"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by newspire on 2009-11-06
I was upgrading from Jaunty to Karmic and the updater hung on gucharmap.  I told it to continue.  It then failed on some other package and the system froze.  When I rebooted it could not mount one of the file systems, swap I think, and dropped me to a prompt.  I remounted / as wr and ran:
apt-get install -f
and
dpkg --configure --pending

Again it would hang on things related to gucharmap giving an error about corrupt tar files.  I deleted the corrupted tar files and ran apt-get and dpkg again.  This time they seemed to run.

I rebooted and it booted but now the system seems to be partly in Jaunty and partly in Karmic.  When I run the update manager it says it can not update everything and offers a partial update.  When I do this I get an error: "Unable to upgrade from Karmic to Jaunty with this tool."

Is there a way to force all packages up to Karmic?

Thanks
Andy

---

