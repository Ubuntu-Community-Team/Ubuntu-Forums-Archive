---
title: "[SOLVED] Complete Removal of Wine"
date: 2008-09-21
forum: General Help
---

### Post by DougieFresh4U on 2008-09-21
I want to remove Wine and files associated with it.
Then I want to reinstall.
Can some one please provide code?
I have removed it through Synaptic before but when I install again, it seems to have remembered old config.

---

### Post by Rhubarb on 2008-09-21
Delete your ~/.wine directory.
Open up your home directory in Nautilus, press Ctrl + H to unhide all your hidden directories.  Find .wine and delete it.

This will remove all your wine settings (and any windows programs you had installed before).

---

### Post by wolfen69 on 2008-09-21
```
sudo apt-get *purge* wine
```then ```
sudo apt-get clean
``` then ```
sudo apt-get autoremove
``` these steps should be taken whenever anything is uninstalled.

btw, i'm originally from rochester. :-)

---

### Post by DougieFresh4U on 2008-09-21
> **Rhubarb said:**
> Delete your ~/.wine directory.
Open up your home directory in Nautilus, press Ctrl + H to unhide all your hidden directories.  Find .wine and delete it.

This will remove all your wine settings (and any windows programs you had installed before).
Thanks so much!
> **wolfen69 said:**
> ```
sudo apt-get *purge* wine
```then ```
sudo apt-get clean
``` then ```
sudo apt-get autoremove
``` these steps should be taken whenever anything is uninstalled.
Thank you.
btw, i'm originally from rochester. :-)

I'm not, and wish I weren't here now :(

Only it's still in my 'Applications' menu

---

### Post by Rhubarb on 2008-09-21
If it's still in your Applications menu, then use this to get rid of it:

Right click on the applications menu, select ***Edit Menus***.
Then right click on wine, and select delete.

Refer to the screenshot to see exactly how.

---

