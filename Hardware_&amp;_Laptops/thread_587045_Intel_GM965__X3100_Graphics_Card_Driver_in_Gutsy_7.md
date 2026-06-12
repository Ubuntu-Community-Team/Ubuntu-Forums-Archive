---
title: "Intel GM965 / X3100 Graphics Card Driver in Gutsy 7.10"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by undoIT on 2007-10-22
I've got a fresh install of Gutsy on my Latitude D830. It is incredible how much stuff worked out of the box. The only things that weren't working were the sound card, which was easy to fix, and the video card driver, which is running Vesa.

Has anyone gotten the Intel drivers installed for the GM965 GPU to enable 3D acceleration?

Congrats to the Ubuntu team on this awesome release!!!

---

### Post by Linicks on 2007-10-22
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)

Nick

---

### Post by undoIT on 2007-10-22
ah. Perhaps EXA support will be added to Ubuntu in the future.

I guess it is for the better. Don't need Compiz-Fusion chewing into my battery life anyways ;-)

---

### Post by licefork on 2007-10-22
I have that same graphics card, and compiz worked just fine in Gutsy Tribe 5, but after the beta and final release, it stopped working! If you didn't read all of the info on that link Linicks sent you, there is a work-around. Mine works perfectly, here's how:

```
sudo gedit /etc/xdg/compiz/compiz-manager
```

Then add this to the end of this file:
```
SKIP_CHECKS=yes
```

Now reboot, enable "Extra" visual effects, and voila! It crashed on me the first time though, the second time I enabled "Normal" first, then "Extra" and it worked fine.

Don't forget to install the settings manager!
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by eeried on 2007-12-04
Hello, 

I understood the chipset is blacklisted in Ubuntu Gutsy. Now the workaround suggested by Bell wiki has a caveat

> NOTE: Enabling Compiz Fusion on this video chipset will disable video playback. 

No fix, according to the dell-wiki page.

I suppose there's a chance Hardy will support the EXA architecture.

---

