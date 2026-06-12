---
title: "Updater icon"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by epp on 2009-05-05
I decided to give Ubuntu another try after all this time and it works on my laptop.  :)

Is there any type of updater icon that is displayed when updates are available and what it looks like?  Since installing Ubuntu last night, I have yet to see one and I'm sure that updates have been available since 9.04 was released last month.

Thanks (and it's good to be back!)

---

### Post by drs305 on 2009-05-05
The way ubuntu notifies you of changes has ... changed. Here is the exerpt from the release notes:
> 
Change in notifications of available updates

Ubuntu 9.04 introduces a change to the handling of package updates, launching update-manager directly instead of displaying a notification icon in the GNOME panel. Users will still be notified of security updates on a daily basis, but for updates that are not security-related, users will only be prompted once a week.

Users who wish to continue receiving update notifications in the previous manner can restore the earlier behavior using the following command:

**gconftool -s --type bool /apps/update-notifier/auto_launch false**


Here are the release notes:
[http://www.ubuntu.com/getubuntu/releasenotes/904]("http://www.ubuntu.com/getubuntu/releasenotes/904")

---

### Post by epp on 2009-05-05
I see.  And thanks for the Release Notes link.

---

### Post by cybergalvez on 2009-05-06
> **drs305 said:**
> The way ubuntu notifies you of changes has ... changed. Here is the exerpt from the release notes:


Here are the release notes:
[http://www.ubuntu.com/getubuntu/releasenotes/904]("http://www.ubuntu.com/getubuntu/releasenotes/904")

interesting, sounds very windowsish.  I actually liked the unobtrusiveness of the update icon.  We'll have to see how this goes, if its annoying it's going to get turned off, but I'll wait and see

---

