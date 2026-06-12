---
title: "Able to install with madwifi?"
date: 2005-01-07
forum: Installation &amp; Upgrades
---

### Post by andrewski on 2005-01-07
I have a madwifi-supported card that's working fine in Gentoo and I'm going to try to install Ubuntu soon.  Is madwifi supported on the installation CD, or is there another method by which I can get madwifi support in Ubuntu after installing it?

Thanks for any answers; I'm looking forward to trying Ubuntu! 8)

---

### Post by castrojo on 2005-01-07
It's on the CD in the restricted modules package. I don't recall if it was supported on install or not, but doing an 

apt-get install linux-restricted-modules-`uname -r`

 should do the trick.

---

### Post by andrewski on 2005-01-07
[QUOTE=whiprush]It's on the CD in the restricted modules package. I don't recall if it was supported on install or not, but doing an 

apt-get install linux-restricted-modules-`uname -r`

 should do the trick.[/QUOTE]
 So I can just type that after install?

---

### Post by daniels on 2005-01-07
It's not supported *during* the install, but it works fine in the installed system once you install linux-restricted-modules, as suggested; I fixed the former at Mataró, so you can use madwifi in the Hoary install.

---

### Post by flyfishin on 2005-01-28
[QUOTE=daniels]I fixed the former at Mataró, so you can use madwifi in the Hoary install.[/QUOTE]

I just installed Hoary Array 3 and my D-Link DWL-AG650 was recognized during the install.  However, upon reboot it was not seen.  I noticed that the ath modules were not on the system upon reboot.  I had to use aptitude and install the linux-restricted-modules package, thanks whiprush, and then the ath modules were on my system and hence I can now use my wireless card.  I installed Hoary on my laptop twice and it occured with each install.  I guess I was expecting linux-restricted-modules to be installed and my card working upon reboot since it was recognized during the install.  Is this a poor assumption to make?

---

### Post by Pluk on 2005-01-28
warty recognized my atheros wlancard (madwifi driver) during install and next boot.

---

### Post by flyfishin on 2005-01-28
[QUOTE=Pluk]warty recognized my atheros wlancard (madwifi driver) during install and next boot.[/QUOTE]

That's interesting. My understanding of daniels' post was that it wasn't working with Warty's install but now works with Hoary's install.

---

