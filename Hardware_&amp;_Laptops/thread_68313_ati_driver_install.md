---
title: "ati driver install"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by red_Marvin on 2005-09-22
I've followed the [HOWTO on installing ATI drivers](http://www.ubuntuforums.org/showthread.php?t=65276) on ubuntu (hoary, ati 9200),
when errors arose I googled for answers and went on. However, I find it hard to
google this problem, mainly because the error message is in Swedish and most help
forums are not.

When I run the command [COLOR=DarkGreen]sh make_install.sh[/COLOR]
I get the error
[COLOR=DarkRed]FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-386/kernel/drivers/char/drm/fglrx.ko): Operation not permitted
failed.
[/COLOR]
A quick google revealed the following solution:
[COLOR=DarkGreen]mv /lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko $HOME[/COLOR]
Which gave the error
[COLOR=DarkRed]mv: kan inte ta status på "/lib/modules/2.6.10-5-386/kernel/drivers/video/fglrx.ko": Filen eller katalogen finns inte[/COLOR]
Which translates into mv: can not check status on [...]: The file or directory does not exist.
This also proved true when I checked for myself.

---

### Post by red_Marvin on 2005-09-23
If noone knows, perhaps someone could tell me how to reinstall the standard ones,
since as for now my 3d acceleration is even worse than when I started.

---

### Post by Paulo Wageck on 2005-09-23
those drivers are a pain in the butt...

get open gl working correctly is the worst phase...

well..

check my [http://del.icio.us/drpaulo](http://del.icio.us/drpaulo) and there you will find some usefull ati links...

after trying many different distros over the last 14 days (FC4, SuSe 9.3, Debian Sarge and Mandriva) i can tell you this... 

- debian - very stable - too much work to get it all working... slower release cicle for stable apt-get programs... (if compared to ubuntu)
- fedora core 4 - didn't took much time using it...
- mandriva - very nice distro.... misses some good thigs from the debian... (no apt-get)...
- SuSe 9.3 - VERY good distro... very professional...

What I wish I would be using... a hybrid of debian and ubuntu ....  (stability and advantages from ubuntu software...)...

What I am using: Hoary.... Sometimes it hangs OppenOffice 1 or 2... good idea... i love them... but they hang too often... -Breezy (crashed during install)...

What I will do.. stick with ubuntu... is the only one I could manage to get working easily my ati radeon 9800 pro (opengl ok) + webcam + sound + joystick + monitor + APT package system + a promissing future.

Well.... Now I am 100% open source here... Since I got tired from the betryals of the other operating system.....


Sincerely,

DrPaulo.Com

---

