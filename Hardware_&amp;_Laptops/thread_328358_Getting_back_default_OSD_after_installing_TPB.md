---
title: "Getting back default OSD after installing TPB"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by mgchan on 2006-12-30
I was trying to get TPB to work since I had used it before, but after I installed TPB I realized that I didn't really need it - all the keys that I use on my Thinkpad X40 work as I want.  Well, worked...now I don't have the volume OSD any more, whereas it used to work with Gnome.  I already removed tpb through apt, but I think it removed some packages when I installed it, and I don't remember which.  How can I return my Edgy installation to its defaults in terms of this OSD and volume button handling?

---

### Post by tro on 2007-03-05
Same problem here. I'd like to know how to get back the original OSD.

I've updated KDE from 3.5.5 to 3.5.6, which may have caused this as well, though.

---

### Post by tro on 2007-03-06
I think I figured it out. You need the kmilo and kmilo-legacy packages installed and the tpctl package uninstalled. The you can configure the module in the KDE Control Center under System Administration.

---

### Post by putkiradio on 2007-03-16
> **mgchan said:**
> How can I return my Edgy installation to its defaults in terms of this OSD and volume button handling?

I got the same problem, but fortunately found the way to fix this. Run the following in terminal:

- sudo apt-get install hotkey-setup (in case you don't have this already)
- gnome-keybinding-properties (and change the keyboard shortcuts in volume down,up,mute)

that should do it.

---

### Post by deromka on 2007-06-09
Thanks man, it's working indeed!!!

---

### Post by tedrogers on 2007-06-25
Any idea about the brightness up and down buttons....I couldn't find these in the keyboard shortuts menu?

---

