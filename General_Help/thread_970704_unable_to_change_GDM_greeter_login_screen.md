---
title: "unable to change GDM greeter login screen"
date: 2008-11-04
forum: General Help
---

### Post by mike4ubuntu on 2008-11-04
Is anybody else having a problem with changing the GDM greeter / login screen in Intrepid?  After going to the Login Screen applet under the System menu, and changing the login screen to something other than the default, it doesn't seem to stick when I re-login.  I can even add a new greeter to the list, but it won't stick either.  I'm thinking this is a privilege problem on some config file, but I don't know which file.  I'm reusing an existing home directory, but I didn't import it during installation.  I set a symbolic link to the directory after installation.

---

### Post by dbryant32 on 2008-11-04
Beside Theme: in the drop down box.. You do have Selected only chosen right?
I installed a couple of login window themes just to have them not show up too. But mine was set to Random from selected. I changed to Selected only and it worked.

if you think it's ownership problems try:
sudo chown yourusername the directory you didn't import

---

### Post by mike4ubuntu on 2008-11-05
yep, didn't notice the random setting in the drop list.  "select only" works just fine.

thanks!

---

