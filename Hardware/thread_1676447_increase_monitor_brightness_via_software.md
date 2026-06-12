---
title: "increase monitor brightness via software"
date: 2011-01-27
forum: Hardware
---

### Post by magowiz82 on 2011-01-27
Hi,
I've got an old crt monitor that actually is really dark even with brightness set to maximum, is there any software for ubuntu 10.10 that makes me increase brightness? 
I tried with gxvattr but it doesn't seem to work.

---

### Post by magowiz82 on 2011-01-31
bump

---

### Post by cascade9 on 2011-01-31
If you've got an nVidia card, you can adjust the birghtness from nvidia x server settings.

---

### Post by magowiz82 on 2011-01-31
Unfortunatelly I've got an ATI card...

---

### Post by cascade9 on 2011-01-31
ATI/AMD card do have a birghtness control as well. If you have the Catalyst drivers installed anyway.

---

### Post by magowiz82 on 2011-01-31
Do you mean fglrx driver?

---

### Post by cascade9 on 2011-01-31
Yes ;) 

Its somewhere in the Catalyst control centre.

---

### Post by magowiz82 on 2011-01-31
I noticed that my video card is no longer supported by last fglrx driver in ubuntu 10.10, so I downloaded an older driver from ati website which is a rpm file for 64bit architecture (it says I have to install also if I have x86-32 bit) but If I do 
```
sudo alien -i --scripts fglrx.rpm
``` I get an error :
 ```
fglrx64-6-8-0_8.28.8-2_amd64.deb
Unable to install at /usr/share/perl5/Alien/Package/Deb.pm line 92, <GETPERMS> line 126.
    find fglrx64_6_8_0-8.28.8 -type d -exec chmod 755 {} ;
    rm -rf fglrx64_6_8_0-8.28.8
```

---

### Post by magowiz82 on 2011-01-31
I found an installation script for the same driver version but it seems that my xorg is too new to install it :
```
 sudo ./ati-driver-installer-8.28.8.run 
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install

```

---

### Post by magowiz82 on 2011-01-31
I found a way using xgamma command , so with command :
```
xgamma -rgamma 1.5 -ggamma 1.5 -bgamma 1.5 
```
I get the brightness I wanted, is there a way to add this configuration to xorg.conf or to launch this command once xorg is started ? I tried inserting it in /etc/rc.local but it didn't work.

---

### Post by magowiz82 on 2011-01-31
I found it : I added the gamma option to monitor section of my xorg.conf:
```
Gamma  1.50 1.50 1.50
```

---

### Post by cascade9 on 2011-02-01
Yay! You fixed it. :D 

BTW, what ATI card is that using?

---

### Post by magowiz82 on 2011-02-01
I'm using an ATI Radeon 9200 PRO

---

### Post by cascade9 on 2011-02-01
Thanks ;) 

I was just curious, no real reason to ask.

---

### Post by magowiz82 on 2011-02-01
You're welcome.

---

### Post by Simple-man on 2011-02-09
Thank you, that really helped me, `couse i had the same problem with gamma and rest of them... :D:D thx y   :guitar:

---

