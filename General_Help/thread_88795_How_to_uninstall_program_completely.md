---
title: "How to uninstall program completely?"
date: 2005-11-11
forum: General Help
---

### Post by capcorn on 2005-11-11
I tried removing xubuntu-desktop via synaptics manager but found out that the uninstallation was not clean. Some XFCE packages are still there. 

I logged out and I can still see XFCE as an option when I select the session. I login to the XFCE session but was greeted with a blank desktop with a XFCE right-click menu.

1. When I installed xubuntu using synaptics manager, it is relatively simple. Select xubuntu-desktop and install. All packages that it needs are installed together. 
So why is it that uninstallation isn't like that?

2. How can I completely uninstall xubuntu?

3. I find some XFCE packages marked as obsolete in synaptics manager. Can I remove these without causing any problems?

Thanks you for your precious time.

---

### Post by ossi on 2005-11-11
In Synaptics - did you chose "mark for complete removal" ? Otherwise, if you know the nme of all the packages you could open a console and type```
 apt-get remove --purge "package names"
```

---

### Post by capcorn on 2005-11-11
I did mark it for complete removal.
But some packages still remains in my system.

I will try to do a command line removal like what you have suggested.

Thank you.

---

### Post by nszabolcs on 2005-11-11
[QUOTE=capcorn] Some XFCE packages are still there. [/QUOTE]
are you sure no other packages depend on them?


[QUOTE=capcorn]
I logged out and I can still see XFCE as an option when I select the session. I login to the XFCE session but was greeted with a blank desktop with a XFCE right-click menu.
[/QUOTE]

i think you should remove xfce config files from your home directory manually
~/.config/xfce4
~/.config/xfce4-session
~/.cache/xfce4
~/.cache/sessions
~/.local/share/xfce4

---

### Post by trash-can on 2005-11-11
The thing is xubuntu-desktop is a metapackage, which only depends on packages that alltogeather make up xubuntu-desktop, so removing it does not actually remove all packages that make up xubuntu-desktop. Same is true for ubuntu-desktop, kubuntu-desktop and other metapackages. I think aptitude solves this problem, but I am not using it right now. When making some changes I just log packages beeing installed, so I can later manually revert back to previous state.```
sudo apt-get install some-package-with-many-dependencies | tee logs/some-package-with-many-dependencies.log
```Ofcourse logs directory has to exist :) So anyway, that ensures that I can manually remove dependant packages.

---

### Post by capcorn on 2005-11-13
Hi trash-can,

I get what you meant. Just wondering, where is the log directory located?
Does it log down all the packages installed?
To do a clean uninstallation, I have to uninstall all the installed packages manually?

Thank you.

---

