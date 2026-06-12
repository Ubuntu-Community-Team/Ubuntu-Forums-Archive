---
title: "kinit error on startup"
date: 2008-07-18
forum: General Help
---

### Post by Sneaky07 on 2008-07-18
Hi I've been trying to edit my xorg.conf file in order to see if I can get the binary drivers to work for my video card in order to use 3D acceleration.  It has worked so far but I get this error on startup when it loads:

```
kinit:name_to_dev_t(/dev/disk/by-uuid/f21f554c-8fd7-45b5-bee5-52bdfb67df73)=sbd5(8,21)
kinit:trying to resume from /dev/disk/by-uuid/f21f554c-8fd7-45b5-bee5-52bdfb67df73
kinit:No resume image, doing normal boot...
```

Then after this it brings me to tty1 login and then loads up the default X configuration program which I don't want to use because it doesn't allow me 3D acceleration.  I know how to get 3D acceleration but I have to do it manually in tty1 and then start the X server.  I'm just trying to see if I could ever get 3D acceleration on normal boot instead of having to go through the inconvenience each time.  Thanks in advance!! :guitar:

On a side note:  I have a AGP Nvidia 6800 GT and I've been trying to get this working for months.  I made sure the PCI slot was right too for the xorg.conf file.  Has anyone else had this problem??  Is it AGP, if it is do I need to get another card??

---

### Post by Sneaky07 on 2008-07-18
Also, after I run: ```
dpkg -l | grep gdm
```

I get:
```
ii feisty-gdm-themes     0.23
   Feisty GDM themes
ii gdm        2.20.6-0ubuntu2
     GNOME Display Manager
ii ubuntu-gdm-themes     0.29
   Ubuntu GDM themes
```

---

