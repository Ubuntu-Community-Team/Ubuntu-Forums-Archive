---
title: "nvidia-settings"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by tribunal on 2008-01-26
Hi all!
I have Kubuntu 7.10, nvidia-video card and nvidia-driver
I have wide monitor, so I often need a scaling option in nvidia-settings to be enabled (Flat panel scaling)
And it works ok
But I have one problem:
I have to reenable it each time I restart my PC
Checkboxes  are enable, but option doesn't work, so, I disable it, enable it again and it start working (?) :(
Is there a way to work it right from the start?

---

### Post by forestpixie on 2008-01-26
do you open it with root rights? if you do kdesu nvidia-settings (I guess gksudo does it in gnome) you can save changes to xorg.conf

---

### Post by tribunal on 2008-01-26
Yes, with root rights
But it didn't help
Anyway, I have found a solution at nvidia site: this option is still doesn't work, that is why users should write this option (FlatPanelProperties) by hand in x.org

---

### Post by oldsoundguy on 2008-01-26
try the third party program "Envy" for installing your drivers .. worked for me on three machines and I have monitor rotation on all three and wide screen on one.

---

### Post by Welcomed Rain on 2008-01-26
I would agree with oldsoundguy. I was having problems with my Nvidia video driver saving my resolution. After every re-start I would have to re-select the settings even though I had made the changes as root; it didn't even matter whether I made the change using Nvidia's  X Server Settings program or manually by booting into the recovery mode and using dpkg-reconfigure xserver-xorg. I did a reinstall using Envy and it cleared whatever glitch was causing the problem. You might also check to see if you have the latest Nvidia driver. Nvidia released a new driver December 20th 169.07 (which had a bug that made the fan run at 100%) and then an update which fixed that bug about a week ago. I don't know if it is right for your card but I would recommend double checking. This latest driver is 169.09. Good luck.

---

