---
title: "Wubi interferes with PVR on Windows?"
date: 2008-10-22
forum: General Help
---

### Post by wsmaal on 2008-10-22
After install Wubi on Vista (Ultimate/SP1) I noticed that Wubi is the cause that My TV and Radio (Hauppauge MCE 150) doesn't work when I boot Vista. When I remove Wubi from Vista then the problem is solved.

What a pity, because Linux boot much faster then Vista on my PC. When I only want browsing or check my email, I don't need Vista :-)

---

### Post by ago on 2008-10-22
I really do not think that to be the case. Wubi does not touch any other file other than the ones in c:\ubuntu and c:\wubildr* as well as one registry key.

---

### Post by wsmaal on 2008-10-22
> **ago said:**
> I really do not think that to be the case. Wubi does not touch any other file other than the ones in c:\ubuntu and c:\wubildr* as well as one registry key.

I thought so either.. The problem is reproducible. When I remove Wubi and boot Windows I haven't any problem with my PVR. When I install Wubi again then the problem is back as soon I boot Windows (I tried XP as well Vista). Any suggestion what can be the cause?

---

### Post by ago on 2008-10-22
Do a manual uninstallation one step at the time:

A) rename or remove c:\ubuntu
B) rename or remove c:\wubildr
C) remove the windows key 
D) remove the entry from the boot menu

---

### Post by wsmaal on 2008-10-22
> **ago said:**
> Do a manual uninstallation one step at the time:

A) rename or remove c:\ubuntu
B) rename or remove c:\wubildr
C) remove the windows key 
D) remove the entry from the boot menu

Apparently were the previous regulary uninstalls of Wubi succeeded, because I don't find anything after inspecting the above mentioned A-D. (Also mentioned in the [_WubiGuide)_]("https://wiki.ubuntu.com/WubiGuide"). Because the proven reproducible PVR problem, I expect that I run again into the same problem when I reinstall Wubi for the 3th time.

---

