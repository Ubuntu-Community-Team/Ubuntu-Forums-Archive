---
title: "How do I get my HDD icon to rest on my dock instead of my desktop?"
date: 2008-12-01
forum: General Help
---

### Post by PsychedelicWonders on 2008-12-01
I have the AWN dock and I want to place my media HDD icon that is currently on my desktop onto the dock itself like the rest of my other "quick" icons.

How do i do this?

Thanks.

---

### Post by PsychedelicWonders on 2008-12-02
bump

---

### Post by PsychedelicWonders on 2008-12-02
bump

---

### Post by PsychedelicWonders on 2008-12-03
bump

---

### Post by PsychedelicWonders on 2008-12-03
bump

---

### Post by PsychedelicWonders on 2008-12-05
bump

---

### Post by scouser73 on 2008-12-05
What you need to do is click the AWN Manager, scroll down to **Stacks Plugger**, and the click activate, then your HDD will appear in the AWN.

---

### Post by PsychedelicWonders on 2008-12-05
> **scouser73 said:**
> What you need to do is click the AWN Manager, scroll down to **Stacks Plugger**, and the click activate, then your HDD will appear in the AWN.

I take it I right click and then go to Stacks Plugger?

Not sure if I've seen this setting before... is it right out in the open?

It will auto detect which HDD I want to use?  (I have 2 HDD's and only want 1 of the 2 on the dock)

---

### Post by nothingspecial on 2008-12-05
To remove the icons from your desktop press Ctrl + F2 and type ```
gconf-editor
``` Then navigate apps > nautilus > desktop and uncheck volumes_visible.

To add them to your dock. Go System > Preferences > Awn Manager and activate Stacks Plugger. All your removable media will show on your bar. Remove your cd icon and your other hard-drive by right clicking on the icon and choosing hide volume.

Voila

---

### Post by joshzam on 2009-04-13
> **nothingspecial said:**
> To remove the icons from your desktop press Ctrl + F2 and type ```
gconf-editor
``` Then navigate apps > nautilus > desktop and uncheck volumes_visible.

This is a great way to remove ALL volumes from the desktop, but how would one remove only the icons for permanent internal drives while still allowing icons for temporary external drives to appear when needed?

---

### Post by joshzam on 2009-04-13
In case anyone is interested, I realized that my internal HD was showing up on the desktop because I had mounted it in the media folder. After changing the mountpoint to the mnt folder, the icon no longer shows up. Very happy.

---

### Post by PsychedelicWonders on 2009-04-13
> **nothingspecial said:**
> To remove the icons from your desktop press Ctrl + F2 and type ```
gconf-editor
``` Then navigate apps > nautilus > desktop and uncheck volumes_visible.

To add them to your dock. Go System > Preferences > Awn Manager and activate Stacks Plugger. All your removable media will show on your bar. Remove your cd icon and your other hard-drive by right clicking on the icon and choosing hide volume.

Voila

This sounds awesome.

But will this block me from ever having icons on the desktop?

When I create new ones, instead of going to the desktop, they'll just go to the dock?

What about saving files & stuff like that?

I usually save any files that I am working on on my desktop.

---

