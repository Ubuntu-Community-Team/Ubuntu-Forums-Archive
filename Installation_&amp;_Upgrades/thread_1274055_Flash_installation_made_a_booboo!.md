---
title: "Flash installation made a booboo!"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by MC_Claus on 2009-09-24
Hi all

I tried to install the flash player plugin, via the download at the adobe site. It ran in user mode and the installation failed due to the obvious lack of root rights!

Now it totally messed up my apt/synaptic. I can't install it, dpkg/apt complains that it is missing the package. I can't remove it, via dpkg/apt, because it then asks me to reinstall, because of the package being broken.

I tried removing it via the 
```
sudo dpkg --force-remove-reinstreq -r/-P adobe-flashplugin
```
but it gives the same error

Also 
```
sudo dpkg --force-all -r/-P adobe-flashplugin
```

Gives no new result.

What to do? I'm fresh out of ideas! :-/

---

### Post by wojox on 2009-09-24
Try:

```
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
```

---

### Post by MC_Claus on 2009-09-24
> **wojox said:**
> Try:

```
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
```

Thanks for the suggestion :-)

dpkg: warning: ignoring request to remove flashplugin-nonfree which isn't installed

Didn't work :-(

I tried installing this via apt, but that could not install due to the adobe-flashplugin!

---

