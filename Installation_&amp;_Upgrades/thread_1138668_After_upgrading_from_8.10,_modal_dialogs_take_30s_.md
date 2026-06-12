---
title: "After upgrading from 8.10, modal dialogs take 30s to display in gnome"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by loteq on 2009-04-26
Hi,

I have just upgraded from intrepid (8.10) to jaunty (9.04)

Whenever any gnome program seems to open a modal dialog (right-click on the panel->properties, or just opening a file browser in any program). The invoking program freezes for 30s-1min more or less, until the dialog shows up. This is a showstopper of course unless i find a solution. I have been looking around on the forums but have not been able to find a solution.

I have tried disabling compiz, switching back to Human theme from my previous theme shiki-solours... I'm out of ideas.

Help/guidance would be greatly appreciated!

---

### Post by cariboo on 2009-04-26
What make/model graphics adapter does your computer have?

---

### Post by loteq on 2009-04-26
Hi,

My Display Adapter is an Nvidia Geforce 7300 LE. I have the NVIDIA driver version 180.44 installed.

---

### Post by rudyneeser on 2009-04-27
The first time I logged in to Jaunty after upgrading from 8.10 I had the same problem, although a reboot fixed it and so far the problem has not reappeared. I am also using a nvidia 7300. Have you had any luck fixing the problem? Are you also having random system freezes?

---

### Post by loteq on 2009-04-27
No, the problem is not solved. I did  not have access to my computer yesterday, so I could not mess around with it. I'll try uninstalling the nvidia drivers to see if the issue persists in low graphics mode.

---

### Post by loteq on 2009-04-27
If I uninstall the nvidia proprietary drivers the problem goes away, but no GPU acceleration, and no compiz.

Is there a way I can grab a previous version of the nvidia driver that is still compatible with the current kernel?

Update:

I reinstalled the nvidia drivers, and now the issue is solved. Nothing like a little shamanism in the information age.

---

### Post by loteq on 2009-04-27
Solved

---

