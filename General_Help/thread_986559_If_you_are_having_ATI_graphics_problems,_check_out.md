---
title: "If you are having ATI graphics problems, check out this link."
date: 2008-11-18
forum: General Help
---

### Post by Marius Derekus on 2008-11-18
Here are tons of ATI graphics drivers. Just select "linux" and then get your graphics drivers. (These drivers are made by ATI themselves, so this is a reliable source and it should work.)

Here is the link: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by whitethorn on 2008-11-18
I'd be careful with these drivers. You have to reinstall the drivers with every kernel update. If you willing to wait a little longer you can usually install them through synaptic and not have to worry about updating them yourself.

---

### Post by Yellow Pasque on 2008-11-19
> Here is the link: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

It would probably be a better idea for Ubuntu 8.10 users to install them through Synaptic/dpkg. The latest 8-11 Catalyst drivers are in Intrepid's "proposed" repo. You can enable this repo through System -> Administration -> Software Sources (the Pre-released option under the Updates tab). Make sure the restricted repo is enabled on the first tab if you want to use these proprietary drivers.

I would also be careful about installing other available proposed updates, unless you see a change in their changelog(s) that fixes a specific issue you have and can't wait for the fix to be finalized.

---

### Post by arosboro on 2008-12-14
Is there any way to make a filter for packages in the intrepid-proposed repository?

Can I just change package upgrade behaviour to 'Prefer versions from :intrepid-updates' under the Distribution tab of Preferences?

I'm trying to figure out an easy way to wade through the 68 updates that are now available after adding the proposed repository, while automatically applying new updates that come through from intrepid-updates.

---

