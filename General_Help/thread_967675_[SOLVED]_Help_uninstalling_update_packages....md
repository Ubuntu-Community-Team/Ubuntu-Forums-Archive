---
title: "[SOLVED] Help uninstalling update packages..."
date: 2008-11-02
forum: General Help
---

### Post by Tamalin on 2008-11-02
I had started upgrading Ubuntu 8.04 to 8.10, but later decided to keep 8.04.  I canceled the download, but my update manager had already downloaded several packages and told me it was going to keep them.  How can I find out what these packages are, and how can I remove them?

---

### Post by snova on 2008-11-02
It doesn't install anything until all the packages have been downloaded, so nothing was changed. However, these new packages will remain in the package cache so that if you decide to update later on, it will not have to download them again.

If you want to clear the package cache (useful if it gets big), run this:

```
sudo apt-get autoclean
```

---

### Post by tuxxy on 2008-11-02
Why the sudden change of heart, not these bad reviews flooding the boards by any chance as Ibex is an excellent update.

---

### Post by sj1410 on 2008-11-02
you can find the packages in /var/cache/apt/ directory


> **Tamalin said:**
> I had started upgrading Ubuntu 8.04 to 8.10, but later decided to keep 8.04.  I canceled the download, but my update manager had already downloaded several packages and told me it was going to keep them.  How can I find out what these packages are, and how can I remove them?

---

### Post by Sef on 2008-11-02
It would be best to reinstall Hardy.  Some packages have already been removed.

---

### Post by zvacet on 2008-11-03
In **synaptic **under **file tab** you will see **history**.Look there and see whitch packages you instaled and if any removed.DElete new installed and reinstall if any was removed.

---

### Post by Tamalin on 2008-11-03
Ok, I had already run apt-get autoclean before starting this thread, but it finished after barely a second, where as downloading the packages took about 15 minutes.  I had figured they were stored somewhere else.  Thank you!

---

### Post by zvacet on 2008-11-04
>  I had figured they were stored somewhere else.

If you install it with synaptic or apt-get they are in var/cache/apt/archives,but autoclean is not option you are looking for.Maybe 

```
sudo apt-get clean
```

is a better idea.In terminal run **man apt-get** and you will see all options.

---

### Post by Tamalin on 2008-12-13
Well, in reply to the change of heart question, I just wanted to stick to the LTS editions, thats all.  Hardy is working fine for me and I don't really want to update all that bad.

---

