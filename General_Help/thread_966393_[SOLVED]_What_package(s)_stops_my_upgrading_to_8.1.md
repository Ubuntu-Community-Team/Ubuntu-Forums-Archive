---
title: "[SOLVED] What package(s) stops my upgrading to 8.10?"
date: 2008-11-01
forum: General Help
---

### Post by knutschr on 2008-11-01
Upgrade manager gives the message:

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

It must be the last reason, I think.
Can I find out what packages these are, somewhere?

---

### Post by Sef on 2008-11-01
>   * Unofficial software packages not provided by Ubuntu

Have you added any unofficial software packages?  You can check this way:  System > Administration > Software Sources > Third Party Software.

---

### Post by CatKiller on 2008-11-01
I had something similar with my upgrade. Upgrade-manager hadn't updated itself properly, and Amarok had dependency problems. I did my upgrade in the end by manually changing the /etc/apt/sources.list to intrepid sources, removing amarok, running ```
sudo apt-get update && sudo apt-get dist-upgrade
``` for the upgrade to Intrepid and then reinstalling Amarok.

---

### Post by knutschr on 2008-11-01
Updating now :-)
I looked at /var/log/dist-upgrade and found many complanis about kuser, as I also have KDE4 installed.
I then removed kde-admin with Synaptic, and voila!

---

### Post by knutschr on 2008-11-02
I now have installed Intrepid.
and everyting works ;.)
I think may be that is because I in advance removed everything that gave me errors earlier.

---

