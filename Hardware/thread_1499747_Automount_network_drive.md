---
title: "Automount network drive"
date: 2010-06-02
forum: Hardware
---

### Post by picopir8 on 2010-06-02
I have a network file server that I would like automounted whenever my laptop connects to the network. Does anyone know how to accomplish this?

I do not think fstab is the answer because that would only mount the drive at bootup and manually mounting is less cumbersome than rebooting.  What I am looking for is to use the network availability as the trigger event that causes the drive to be mounted.

---

### Post by dino99 on 2010-06-02
[http://www.google.fr/search?as_q=network%2Bmount%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=network%2Bmount%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by picopir8 on 2010-06-03
LOL, how is that link supposed to help?

I already know how to mount network shares, what I want is something that will mount/unmount them depending on their availability on the network.  That way when I remove my laptop from the network the shares are unmounted.  When the laptop returns to the network the file shares are remounted without having to reboot or logout/login.

If anyone else is looking for a REAL answer though, after some more digging these look promising.

[http://ubuntuforums.org/showthread.php?t=1027173](http://ubuntuforums.org/showthread.php?t=1027173)
[http://ubuntuforums.org/showthread.php?t=637258](http://ubuntuforums.org/showthread.php?t=637258)

---

