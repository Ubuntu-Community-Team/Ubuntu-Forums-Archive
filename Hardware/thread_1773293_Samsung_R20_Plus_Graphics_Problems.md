---
title: "Samsung R20 Plus Graphics Problems"
date: 2011-06-01
forum: Hardware
---

### Post by daz1uk on 2011-06-01
Hi,

I have been trying to install the proprietry drivers for my onboard x1250, I followed instructions fount on the ubuntu site but now have a problem:

darryl@darryl-R20-P400:~$ fglrxinfo
Segmentation fault
darryl@darryl-R20-P400:~$ sudo dpkg-reconfigure xserver-xorg
darryl@darryl-R20-P400:~$ sudo fglrxinfo
darryl@darryl-R20-P400:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Segmentation fault
darryl@darryl-R20-P400:~$ perl -n0077 -e 'print "Using driver $1 v$3 by $2.\n" while /Module (radeon|fglrx|intel|nvidia|nv|vesa): vendor="([^"]+)"\n.*version = (\S+)/img;' /var/log/Xorg.${DISPLAY:1:1}.log
Using driver fglrx v8.84.60 by FireGL - ATI Technologies Inc..
Using driver radeon v6.14.99 by X.Org Foundation.
Using driver vesa v2.3.0 by X.Org Foundation.
darryl@darryl-R20-P400:~$ sudo aticonfig --initial
aticonfig: No supported adapters detected

I don't understand why it is using 3 drivers? or why when I try to aticonfig --initial it tells me that I dont have a supported adapter.

lspci returns:
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Xpress 1250

I no longer have access to my logon screen and can only boot into unity2d instead of 3d :(

---

