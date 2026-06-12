---
title: "[SOLVED] Uninstall Zimbra Desktop"
date: 2008-09-19
forum: General Help
---

### Post by Merovius on 2008-09-19
I installed Zimbra. _zdesktop_0_90_build_1278_linux_i686.sh. From download. Now how the heck to uninstall it? :confused:

Any help appreciated.

TIA

---

### Post by Dayne89 on 2008-09-19
never heard of zimbra. cant you click applications in top left corner, then add/remove. type zimbra in the box in the top right. click the button next to zimbre and click apply changes to un-install.

---

### Post by Merovius on 2008-09-20
Installed with a .sh file from the website. It is not listed in add remove programs. I believe I will nedd to do it from the terminal. Not that good with terminal commands without instructions.

Thanks

---

### Post by veli on 2008-09-20
You have to run the command:

./install.sh -u

this file should be in the directory where zimbra is installed. Answer YES when asked about removing the software. This is what I remember, may be it's a good idea to read the Readme file or check withe their forums.

---

### Post by Merovius on 2008-09-20
I found a site with instructions including the command you mentioned. I couldn't find the file they said to CD to so it wouldn't run. 

I found a zimbra folder and it had an uninstall.sh file. I made it executable and ran it. the uninstall seemed to work for the most part but it said at one point it couldn't stop the service. I'm thinking maybe I need to uninstall as root. It may be uninstalled but I cant be sure.

Thanks for the tips.

---

### Post by ZedsDeadBaby on 2008-10-24
Took me a min to get it but just navigate to the zimbra folder in your home and you'll see the uninstaller.

In Terminal cd to the folder, mine is below:

-->  :~$ cd ~/zimbra/zdesktop
-->  :~$ ./uninstall.sh

This should kick off the uninstaller and allow you to remove it.  At first I thought zimbra would be a neat-o app, but I wasn't real impressed once I put it to work.  My gmail accounts were not enjoying zimbra trying to mess with em.  I'll stick with Evolution.  :)

Good luck!:popcorn:

---

