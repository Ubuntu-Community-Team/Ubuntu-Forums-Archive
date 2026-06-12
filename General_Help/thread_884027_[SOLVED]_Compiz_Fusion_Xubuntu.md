---
title: "[SOLVED] Compiz Fusion Xubuntu"
date: 2008-08-08
forum: General Help
---

### Post by ArtF10 on 2008-08-08
I have a question regarding Compiz Fusion.  I am currently using XUbuntu.  According to this thread:

[http://ubuntuforums.org/showthread.php?t=777750](http://ubuntuforums.org/showthread.php?t=777750)

it(Xubuntu) does not allow Compiz Fusion to be installed.  Although, the thread is a bit old and so I wanted to know is there an option to install Compiz Fusion on Xubuntu in the same way that it is installed in Ubuntu(i.e. from synaptic)?

---

### Post by john.nicholls on 2008-08-08
Xubuntu can certainly run Compiz. In Gutsy and Hardy it is part of the normal install and can be accessed through Advanced Desktop Effects Settings. On earlier versions use Synaptic to install.

---

### Post by ArtF10 on 2008-08-08
[http://www.thecodingstudio.com/opensource/linux/screenshots/?linux_distribution_sm=Xubuntu%208.04%20Hardy%20Heron%20Alpha%205](http://www.thecodingstudio.com/opensource/linux/screenshots/?linux_distribution_sm=Xubuntu%208.04%20Hardy%20Heron%20Alpha%205)

From which menu would Desktop Effects Settings be available in Xubuntu 8.04?

---

### Post by spoketire on 2008-08-09
I would also be interested to know where to see these settings. I have Xubuntu Hardy and haven't found them yet.

---

### Post by ArtF10 on 2008-08-09
Would the procedure be:
1.  Install Compiz Fusion
2.  From a terminal, type ccsm to open the Compiz Fusion Manager?

Please let me know if this would work as, just like *spoketire*, I can't see Advanced Desktop Effects Settings in XUbuntu.

---

### Post by Kevbert on 2008-08-09
First question is what display card do you have ?  Compiz will work with most ATI, Intel and nVidia cards.  Compiz is found under Settings - Advanced Desktop Effect Settings.  I can't remember exactly if I had to install anything but you can install it via Applications-System-Synaptic Package Manager.  Next do a search on compiz.  The following should be selected:
compiz
compizconfig-backend-gconf
compizconfig-settings-manager
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
If not right-click on the box and Mark for Installation, then click on Apply when all packages have been selected.

---

### Post by sisco311 on 2008-08-09
here is a howto
[http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/)
(it's for gusty but will work with hardy)

---

### Post by ArtF10 on 2008-08-09
Thanks for the help guys.....

Presumably, the **Advanced Desktop Effect Settings** option will only appear after installing Compiz, because it does not show up with the default Xubuntu installation.i.e. it is not there before Compiz Fusion is installed.

I actually read that HOW-TO and, for the above reason, was not satisfied as unfortunately, the person who wrote that HOW-TO did not mention anything about this option showing up in the Advanced menu.

---

### Post by Kevbert on 2008-08-10
That HowTo does actually work.  If you have any problems please ask.

---

### Post by ArtF10 on 2008-08-10
SOLVED

It worked.  The Advanced Desktop Effect Settings menu showed up only AFTER installing Compiz Fusion.  Thanks for the help.

---

### Post by sisco311 on 2008-08-10
> **ArtF10 said:**
> SOLVED

It worked.  The Advanced Desktop Effect Settings menu showed up only AFTER installing Compiz Fusion.  Thanks for the help.

Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

### Post by spoketire on 2008-08-11
> **john.nicholls said:**
> Xubuntu can certainly run Compiz. In Gutsy and Hardy it is part of the normal install and can be accessed through Advanced Desktop Effects Settings.

So I guess it's not actually installed by default then, right?

---

### Post by john.nicholls on 2008-08-12
> **spoketire said:**
> So I guess it's not actually installed by default then, right?

Yes, it is installed; it's just not activated.

---

