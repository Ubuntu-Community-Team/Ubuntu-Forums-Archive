---
title: "firefox preferences and data?"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by ZaaBI_AlonSo on 2009-06-14
how can i save my firefox preperences and bookmarks and all these stuff?
firefox on my hd installation which i can't boot into, so i want to save the data from a live cd of ubuntu?

can i do that?

---

### Post by quixote on 2009-06-14
To save your preferences:  boot from the liveCD.  

Open nautilus (the file manager) and click on the drive that has the right size to be your misbehaving hard drive.  That will mount it. Go to what was your home directory, and do "show hidden files." (it's a setting under "View".)  Your settings are under a folder called ".mozilla".  You can just save the whole thing to a removable drive, call it for instance "mozilla-prefs-from-old-drive".  

When you're starting over with a new firefox, you can copy the new default .mozilla to something, so that you have a backup in case things don't work, and then copy your old .mozilla into your new home directory.  Suddenly, your new firefox should look just like your old one did :) .

(Your actual profile is in a subdirectory: .mozilla/firefox/some-weird-letters-and-numbers.default.  If you set up other profiles, there'll be more than one folder.)

Bookmarks are also a folder under your profile, called "bookmarkbackups"  So I think you'll have everything if you copy over the .mozilla folder.

---

### Post by ZaaBI_AlonSo on 2009-06-14
> **quixote said:**
> To save your preferences:  boot from the liveCD.  

Open nautilus (the file manager) and click on the drive that has the right size to be your misbehaving hard drive.  That will mount it. Go to what was your home directory, and do "show hidden files." (it's a setting under "View".)  Your settings are under a folder called ".mozilla".  You can just save the whole thing to a removable drive, call it for instance "mozilla-prefs-from-old-drive".  

When you're starting over with a new firefox, you can copy the new default .mozilla to something, so that you have a backup in case things don't work, and then copy your old .mozilla into your new home directory.  Suddenly, your new firefox should look just like your old one did :) .

(Your actual profile is in a subdirectory: .mozilla/firefox/some-weird-letters-and-numbers.default.  If you set up other profiles, there'll be more than one folder.)

Bookmarks are also a folder under your profile, called "bookmarkbackups"  So I think you'll have everything if you copy over the .mozilla folder.

thnks a lot really helpfull

---

