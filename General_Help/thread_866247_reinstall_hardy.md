---
title: "reinstall hardy"
date: 2008-07-21
forum: General Help
---

### Post by Uchiha_madara on 2008-07-21
how can i re-install ubuntu hardy without formatting?
and how can i know the Chipset of My motherbord ??

---

### Post by Potatoj316 on 2008-07-21
Why dont you want to reformat.  You wont have to reformat manually, the installer will do it for you and I think if you reinstall to the same place it keeps your /home directory but I wouldnt count on it if its important.  Otherwise I dont think its possible to install without reformating.

---

### Post by WRDN on 2008-07-21
You can't reinstall it, but if you want to keep your files, I would recommend moving [/home to another partition]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/"), if not done so already.
Then, during the installation process, you could select "Manual" partitioning, use the swap that already exists, use the /home partition that will exist, and then, just select the root partition, and give it the mount point "/".

However, rather than going to the trouble of performing these actions, what problems do you currently have, as it may be possible to fix them?

---

### Post by Uchiha_madara on 2008-07-21
how can i revert The Modification that i made upon the Sytem
in /usr/src/alsa
or in the Kernel ???

---

### Post by Uchiha_madara on 2008-07-21
how can i revert The Modification that i made upon the Sytem
in /usr/src/alsa
or in the Kernel ???

---

### Post by WRDN on 2008-07-21
What did you alter, and what is the consequence?
You could try reinstalling alsa-base/ alsa-utils and other alsa programs.
If you do this, the system should add the files back.

---

