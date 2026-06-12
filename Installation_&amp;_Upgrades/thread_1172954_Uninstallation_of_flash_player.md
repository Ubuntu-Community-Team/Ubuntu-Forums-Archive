---
title: "Uninstallation of flash player"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by hannah2312 on 2009-05-29
I have ubuntu netbook remix and I seem to have installed 2 flash players. One adobe, which i downloaded from the internet, and the other was installed by ubuntu when i tried to play a youtube video. The youtube videos still wont play properly. either the picture is jumpy and keeps freezing or the sound doesn't work. I need to uninstall them both and start again, but i don't know how. Could anyone help me please?? I need exact intructions because otherwise i'd kill something :)

---

### Post by Partyboi2 on 2009-05-29
Hi, open a terminal (Applications>Accessories>Terminal) and remove with
```
sudo apt-get remove flashplugin-nonfree adobe-flashplugin
 
```

---

### Post by coffeecat on 2009-05-29
Open System > Adminstration > Synaptic. Have a look for flashplugin-nonfree and/or flashplugin-installer. This is probably the version that was installed by Ubuntu. I'm not sure, but I believe the version you download from Adobe is called adobe-flashplugin. Have a look in Synaptic for that as well. If you can find both, mark them both for uninstallation and uninstall them. Now re-install flashplugin-nonfree, which always works for me.

By the way, instead of simply reinstalling flashplugin-nonfree, try installing the package ubuntu-restricted-extras. That installs flashplugin, MS core fonts, and a whole load of useful multimedia codecs. You may or may not need the codecs on a netbook, but it's useful if you do.

---

### Post by hannah2312 on 2009-06-25
thankyou all. i got it sorted =)

---

