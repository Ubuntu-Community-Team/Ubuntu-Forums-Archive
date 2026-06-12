---
title: "Macbook Air 4.2 + Ubuntu 10.04 - Low resolution screen - Support for Intel HD 3000?"
date: 2012-04-08
forum: Hardware
---

### Post by serxyz on 2012-04-08
I have a Macbook Air 4.2 (year 2011) running with Ubuntu 10.04.03 (64bit). Everything works perfect, except for the screen resolution display: I am stuck to the low resolution mode (1020 x 768) instead of the native resolution (1440 x 900). 

After some research in forums, I found out that the problem is the lack of support in Lucid Lynx for the Intel HD 3000 graphics driver. Worse still, it seems that there is not much that can be done about it, apart from trying to use the xorg-edgers PPA, which is not recommended due to stability concerns:

<http://askubuntu.com/questions/58376/how-do-i-install-the-intel-hd-3000-video-driver>

Does anyone know if anything has changed since then? Is there any solution to this problem? I do not want to upgrade the Ubuntu version because 10.04 is actually my favorite, it is very stable and I like gnome2 much better than gnome3 or Unity. Also, do you know if adding xorg-edgers PPA might fix this issue without compromising the system's stability? (I haven't tried myself).

Thank you guys. Any comment or suggestion will be really appreciated.

SerXYZ.

---

### Post by 2F4U on 2012-04-09
Seems to be a known issue and a workaround is documented in the Mac community wiki:

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)

---

### Post by serxyz on 2012-04-09
> **2F4U said:**
> Seems to be a known issue and a workaround is documented in the Mac community wiki:

[https://help.ubuntu.com/community/MacBookAir4-2](https://help.ubuntu.com/community/MacBookAir4-2)
Thank you for the link. However, as far I understand, the solution given there works only for Ubuntu 11.10 (Oneiric Ocelot), and NOT for Ubuntu 10.04 (Lucid Lynx) which is the one I am using. In particular they refer to a "post-install-oneiric.sh" script that contains a fix to i915:

=================================================
<https://help.ubuntu.com/community/MacBookAir4-2>

LCD Panel
Does not work out of the box without using 'nomodeset' (see above) and then only at the wrong resolution. Works perfectly after running the post-install-oneiric.sh script - see above.

wget -Nq [http://www.almostsure.com/mba42/fix-i915.sh](http://www.almostsure.com/mba42/fix-i915.sh)
bash fix-i915.sh
=================================================

Do you think is possible to modify the script "fix-i915.sh", which needs Ubuntu 11.10 in order to be run, so that I could apply the fix to an Ubuntu 10.04 system? I went a little bit through the script but couldn't really figure out what it is actually doing.

Thanks.

S.

---

