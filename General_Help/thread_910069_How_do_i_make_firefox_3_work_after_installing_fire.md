---
title: "How do i make firefox 3 work after installing firefox 2 on Ubuntu 8.04"
date: 2008-09-04
forum: General Help
---

### Post by Avinash.Rao on 2008-09-04
Hi all,

In the process of making .mht files work on Ubuntu 8.04, i installed firefox2 from the link [http://www.debianadmin.com/install-firefox2-in-ubuntu-and-list-of-recomended-addons.html](http://www.debianadmin.com/install-firefox2-in-ubuntu-and-list-of-recomended-addons.html). 

I can manually execute firefox-3.0 from the command line, but if i open firefox from the main menu I firefox-2.0. How do i change this? I have to make sure all the LTSP users get this as well! 

Thanks
Avinash

---

### Post by eggdeng on 2008-09-04
You can edit the menu command by going to System -> Preferences -> Main Menu- > Internet -> Firefox. Right-click and choose properties. Just replace the current command with whatever command you use from the terminal. As for the LTSP aspect, I'm afraid I'm not qualified to comment.

---

### Post by Avinash.Rao on 2008-09-04
No this didn't help, it still opens firefox 2. I guess its more to do with the links i created during the ff2 installation.

> **eggdeng said:**
> You can edit the menu command by going to System -> Preferences -> Main Menu- > Internet -> Firefox. Right-click and choose properties. Just replace the current command with whatever command you use from the terminal. As for the LTSP aspect, I'm afraid I'm not qualified to comment.

---

### Post by thestig_992 on 2008-09-04
for a quick fix, just change the links from ff2 to ff3.
I think that running ff2 will have a shorcut of "firefox" whereas ff3 will be "sh /(wherever you run ff3 from)/firefox...". the sh is the important part.

You might get some problems with running flash and stuff after doing this though, i would recommend uninstalling ff2 and installing ff3 properly first

---

### Post by Archmage on 2008-09-04
> **Avinash.Rao said:**
> No this didn't help, it still opens firefox 2. I guess its more to do with the links i created during the ff2 installation.

You need to enter the full path for your firefox3 install to make it work.

E.g. /usr/lib/firfox3/firefox (or whereever it is hidden).

---

### Post by Avinash.Rao on 2008-09-04
Hi all,

I uninstalled FF2 and FF3 using synaptic package manager.
I installed FF3 after this and to my surpirse i am still getting FF2!! 
How do i FF3 working on my machine?



> **Archmage said:**
> You need to enter the full path for your firefox3 install to make it work.

E.g. /usr/lib/firfox3/firefox (or whereever it is hidden).

---

### Post by pastalavista on 2008-09-04
Open Synaptic Package Manager and completely remove everything starting with "firefox-2" and install everything with "firefox-3" (except dummy packages and developer files). Firefox should not be running when you do it.. then run
```
sudo aptitude remove
```

---

