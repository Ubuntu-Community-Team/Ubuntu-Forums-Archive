---
title: "Customisation of xorg.conf file"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by technossomy on 2005-12-28
Dear all

I have made 2 changes to my Ubuntu 5.10 machine:
- new videocard: ATI to Matrox
- new screen: Acer AL1714 to HP L1520

I then noticed that the X environment will not start and the boot procedure is asking me to enter the diagnostics routine, which by the way it will not do. I believe all that is involved is a change in the xorg.conf file. Does anyone have experience in this? I suppose I need to change the Monitor, Device and Screen section, but I do not know the exact entries.

Thanks in advance

Tech

---

### Post by shin on 2005-12-28
In console type
sudo dpkg-reconfigure xserver-xorg
and follow the instructions. It should detect all your stuff but still you should take horizsync and vertrefresh of your new monitor from the manual. Just in case.

If still xorg doesn't start - change your graphics driver (device section) to "vesa". Now you should be able to start it. Do some google and find correct settings for your card. Install needed drivers etc.

---

### Post by technossomy on 2005-12-28
Thanks, that worked.

---

