---
title: "[SOLVED] Removing gDesklets using synaptic"
date: 2008-07-11
forum: General Help
---

### Post by Universal344 on 2008-07-11
I have gDesklets installed.  Recently I tried to uninstall it using add/remove programs but it told me I had to use synaptic package manager.
I found the following packages in synaptic: gdesklets, gdesklets-data.
Will removing these packages successfully remove gDesklets and all the Desklets  that came with it?  Also should I say remove or completely remove.

Thanks in advance.

---

### Post by chris4585 on 2008-07-11
> **Universal344 said:**
> I have gDesklets installed.  Recently I tried to uninstall it using add/remove programs but it told me I had to use synaptic package manager.
I found the following packages in synaptic: gdesklets, gdesklets-data.
Will removing these packages successfully remove gDesklets and all the Desklets  that came with it?  Also should I say remove or completely remove.

Thanks in advance.

You can either remove them using synaptic or use a command

```
sudo apt-get remove --purge gdesklets gdesklets-data
```

---

### Post by Universal344 on 2008-07-11
I think I will try the command in the terminal but first could someone tell me what the --purge switch in the command does and why it is needed in the situation.

---

### Post by chris4585 on 2008-07-11
the option --purge removes all the config files too.  If you didn't use purge then the config files would still be on your computer, and if you reinstalled it, the old config files would be there, and if you didnt reinstall that package those config files would be wasting space

---

### Post by Universal344 on 2008-07-11
Thanks, I'll run the command and post results.

---

### Post by chris4585 on 2008-07-11
:)

---

### Post by Universal344 on 2008-07-11
It worked, gdesklets is now completely gone, thanks again.

---

### Post by chris4585 on 2008-07-11
You're welcome :D

---

