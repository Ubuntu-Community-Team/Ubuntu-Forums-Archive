---
title: "Firefox Problem"
date: 2008-09-08
forum: General Help
---

### Post by iampriteshdesai on 2008-09-08
Of late my Firefox 3 seems to have caught cold. It hangs during browsing often. It becomes non-responsive and screen goes black. So i have to use Opera. Opera doesn't have this problem. I have 1.25 GB RAM.

---

### Post by coffeecat on 2008-09-08
It might be worth resetting all the firefox configuration files to their defaults to see if the problem is there. Try this. First of all export all your bookmarks with Bookmarks > Organise Bookmarks > export html. Now shut down firefox and go to your home folder and show hidden folders and files with ctrl-H. Rename the .mozilla folder to .mozilla.backup. Now restart firefox. It will generate a new .mozilla folder with all the default settings, and because of this you will have lost your bookmarks, login passwords, addons and any other tweaks you have made.

If Firefox now behaves properly, import your saved bookmarks, redo all your passwords and reinstall your addons. If you are happy with the way Firefox is working now you can delete the .mozilla.backup folder.

If this doesn't fix things, simply delete the new .mozilla folder, rename the .mozilla.backup folder back to .mozilla and you'll be back where you were, with all your original addons, etc but with the same problem.

---

