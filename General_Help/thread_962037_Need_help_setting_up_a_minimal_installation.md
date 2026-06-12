---
title: "Need help setting up a minimal installation"
date: 2008-10-28
forum: General Help
---

### Post by Suilenroc on 2008-10-28
Hey there all. So I've been looking for a good distro to install on a 4gb flash drive, but just couldn't find one that fit my needs. So I decided to install ubuntu from the minimal CD, and work from there. 

I currently have XFCE working, but there's some problems. There's no panels on the top or bottom, so no buttons with an nicely layed out menu. Can anyone help me with that? There's more problems, but that's the big one. Thanks!

---

### Post by jpkotta on 2008-10-28
Try installing xubuntu-default-settings.

If that doesn't work, try installing other packages that xubuntu-desktop depends on.  One of them should contain the settings for the default desktop setup.  
```
aptitude show xubuntu-desktop
```

Or you could just install the whole thing.  Installing xubuntu-desktop is almost the same as installing from the Xubuntu install CD.

These packages just set up the defaults that are copied to a new user's config.  Thus if you already have a user with an XFCE config, these packages won't do anything for that user. 

You could figure out how to configure XFCE manually.  I don't know much about that.

Finally, you can try something like Fluxbox or FVWM (Crystal).  Those are really more minimal anyway.

---

### Post by ciscosurfer on 2008-10-28
This might be of interest: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

