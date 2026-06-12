---
title: "Installing fglrx breaks xorg"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by missingno on 2009-08-24
After my hard drive crashed, I finally got my laptop back from repairs and needed to freshly install Ubuntu. I'd previously been running 8.04 and the only graphics problems I'd had with my Radeon X1200 under fglrx were rapid flickering when running some 3D games at the same time as Compiz Fusion. Not a huge issue. 
Now I installed 9.04, and when I went and installed fglrx I found that X would no longer start up, it just gave me some garbled graphics until I gave it a hard reboot. I rebooted into the repair mode or whatever it's called, and tried the option to autorepair xorg.conf - no dice. I uninstalled fglrx, and now I could get X up and running again, but at a low resolution and it wouldn't let me set it back to 1280x800. I again tried the tool to repair xorg.conf, still no go. I came up with the idea to reload the live cd and copy whatever working xorg.conf it had originally generated - this file worked, but only if I didn't also have fglrx installed.

...And now as I go to look at my xorg.conf to paste it here I notice it's practically blank, just naming "configured screen" and such - and backups show that it was always the same version anyway so I have no clue how replacing it like I did half fixed things...

Uh, anyway, without fglrx I'm getting occasional flickering, sometimes windows seem frozen - not updating their display until I minimize and maximize them, and Compiz Fusion runs pretty slowly. Anyone know how I might get it working?

---

### Post by oldrocker99 on 2009-08-24
This is a pretty well-known issue. The 9.04 XOrg is incompatible with the fglrx drivers, which is why I'm still rocking 8.10 and crossing my fingers about Karmic.

:guitar:

---

### Post by tuxxy on 2009-08-24
Save the finger crossing and go switch to nvidia video card :D

---

### Post by Mark Phelps on 2009-08-24
> **missingno said:**
>  Anyone know how I might get it working?

You won't. It has been well established that ATI dropped driver support for lots of legacy cards, including yours, some months back such that with 9.04, your only recourse is using the open source drivers.

And as to future releases, ATI has indicated no plans to return to supporting these cards.  So, there's nothing coming from them down the road.

---

### Post by tubasoldier on 2009-08-24
I am in the same boat. You will have to use the xorg ati driver. It seems to do OK with compiz but not nearly as good as the fglrx driver did.

---

