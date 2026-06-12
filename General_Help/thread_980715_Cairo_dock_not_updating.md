---
title: "Cairo dock not updating"
date: 2008-11-13
forum: General Help
---

### Post by silence.hr on 2008-11-13
> Unpacking replacement cairo-dock ...
dpkg: error processing /var/cache/apt/archives/cairo-dock_1.6.3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/cairo-dock/icon-mouse.png', which is also in package cairo-dock-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/cairo-dock_1.6.3.1_all.deb

this is what i get .... have no idea what to do. (clueless)

---

### Post by eternalnewbee on 2008-11-13
Maybe this can be solved by```
sudo apt-get update
```

---

### Post by fabounet on 2008-11-13
there is a mix between the Ubuntu repos and the project's one, so remove it first.
do a "apt-get --purge" for all cairo-dock* packages (save your ~/.cairo-dock in case), then reinstall it.

---

### Post by silence.hr on 2008-11-13
> **fabounet said:**
> there is a mix between the Ubuntu repos and the project's one, so remove it first.
do a "apt-get --purge" for all cairo-dock* packages (save your ~/.cairo-dock in case), then reinstall it.

i looked in synaptic and saw different versions of cairo-dock and cairo-dock-data, so i guessed it's something like what you say. problem is ... could you be little more specific and which repos to use later?

---

### Post by Pemakhov on 2008-11-13
> **silence.hr said:**
> this is what i get .... have no idea what to do. (clueless)

Hi
It seems, there are installed the package cairo-dock-data in your system.
Try to remove cairo-dock & cairo-dock-data with Synaptic, and then install cairo-dock package again (don't install cairo-dock-data).
It must work.

---

### Post by broomster on 2008-11-13
> **Pemakhov said:**
> Hi
It seems, there are installed the package cairo-dock-data in your system.
Try to remove cairo-dock & cairo-dock-data with Synaptic, and then install cairo-dock package again (don't install cairo-dock-data).
It must work.


I can confirm this works for me. I had similar troubles.

I took a backup of my .cairo-dock directory, and uninstalled cairo-dock and cairo-dock-data. reinstalling them straight afterwards. Problem solved :-) Thank you!

---

