---
title: "Reinstalling Windows Vista"
date: 2008-09-23
forum: General Help
---

### Post by lynx_hanan on 2008-09-23
Hi everyone

Im currently running Ubuntu 8.04 and vista ultimate on my notebook. Recently due to  virus attack (which my antivirus was unable to prevent). This has left some considerable damage , some key system files are corrupted n stuff. I want to do a clean windows vista install but the problem is i also dont want loose my Ubuntu. i wanted to know how can i recover ubuntu after reinstalling vista.???

---

### Post by mike1821 on 2008-09-23
Re-installing windows will result in creating a new MBR. Ubuntu partition will remain intact, but it will not be able to boot as the original MBR will have been erased.


In order to recover this you simply need to re-install GRUB. Let me know if you need instructions of how to do this.

---

### Post by bigken on 2008-09-23
Take a look [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") on how to fix grub

---

