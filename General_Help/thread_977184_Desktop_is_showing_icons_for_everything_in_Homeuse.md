---
title: "Desktop is showing icons for everything in /Home/*user*"
date: 2008-11-10
forum: General Help
---

### Post by DarkN00b on 2008-11-10
1. My Intrepid machine has two logins -- one for me and one for my wife. 

2. I just reinstalled and restored our /Home directories.

3. Her desktop is displaying all the icons from her /Home/*her* directory.

4. Her /Home/*her*/Desktop directory contains nothing, not even any hidden files.

There is a setting in gconf-editor at */apps/nautilus/preferences/desktop_is_home_dir* that allow you to do this but that option is not checked. I have made sure her user owns all files and directories inside her home folder as well as making sure all permissions are set correctly. All files and directories are accounted for.

If anyone could help me fix this I would be very grateful.

---

### Post by Ocxic on 2008-11-10
try activating that option in the config editor, log out then back in, the disable the option and logout and back in, this should reset the setting associated with that type of option, and hopefully get everything back to normal.

---

### Post by DarkN00b on 2008-11-10
Something went pear-shaped when I restored our home folders. Everything is fixed now. Thanks for your help.

---

