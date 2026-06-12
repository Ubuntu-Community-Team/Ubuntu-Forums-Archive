---
title: "Gnome and KDE in Ubuntu 9.04?"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by gedumer on 2009-07-05
I installed Ubuntu 9.04 with Gnome. Is there a way that I can switch to KDE to try it out? I don't want to try it in VirtualBox... I'd like to be able to switch between the 2 on the same machine. I know that you can switch between the 2 in OpenSuse at startup... can I do that in Ubuntu? If so... How?

Thanks

---

### Post by Simian Man on 2009-07-05
Just install the package "kde".  Then logout, and you should have the option to login to gnome or kde.

---

### Post by gedumer on 2009-07-05
Which KDE package... there are so many of them?

---

### Post by schnelle on 2009-07-05
Install kubuntu-desktop package from synaptic. After restart at login choose kde session.

---

### Post by aysiu on 2009-07-05
You don't even have to restart.

After you install *kubuntu-desktop*, just log out, and you can choose KDE from the session list before logging back in again.

More details here:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by gedumer on 2009-07-05
One final question... this will leave Gnome intact right? It won't screw up anything I have done with Gnome will it? Finally... can I uninstall KDE if I don't like it? I have a few KDE apps installed under Gnome and I wouldn't want to mess them up if I uninstall KDE.

Thanks again

---

### Post by aysiu on 2009-07-05
> **gedumer said:**
> One final question... this will leave Gnome intact right? It won't screw up anything I have done with Gnome will it? Finally... can I uninstall KDE if I don't like it? I have a few KDE apps installed under Gnome and I wouldn't want to mess them up if I uninstall KDE.

Thanks again
It would leave Gnome with the same functionality. But it may not be "intact," depending on what you mean by that.

Your Gnome Applications menu will be cluttered up with KDE applications (more than what you have now installed), and your KDE will be cluttered up with Gnome applications.

If you want to be able to restore things to exactly the way they were before, then don't use Synaptic to install *kubuntu-desktop*.

Instead, in [the terminal](http://www.psychocats.net/ubuntu/terminal), paste in the command ```
sudo apt-get update && sudo apt-get install kubuntu-desktop
``` It'll list a whole bunch of packages to add and then ask you for confirmation.

Before you confirm, highlight all of those packages and then paste them into a text document and save that as *restoregnome.txt* in your home directory.

Then confirm.

If you later want to remove only the newly added packages you can type ```
sudo apt-get remove
``` and then paste in all of those packages before hitting Enter.

---

### Post by gedumer on 2009-07-05
Thanks... I'm ready to give it a go now.

---

