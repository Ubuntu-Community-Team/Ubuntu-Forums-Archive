---
title: "wireless trouble..."
date: 2008-08-19
forum: Hardware
---

### Post by dkobel on 2008-08-19
Hey, I'm setting up my dad with ubuntu on his brand new hp pavilion dv9910us. So far, most things are working well except the wireless. The restricted drivers are installed/enabled, but there is still no wireless internet. No matter if I switch on or off the wireless manually, it still does not show up or catch a signal (and when I access admin>networking it doesn't show up at all.)

can anyone kindly help me out?

---

### Post by pwnprog on 2008-08-19
does it have a broadcom wireless adaptor? if so, this thread should get you up and running in 10 minutes or so. it did for me and anybody else i've referred. [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

### Post by dkobel on 2008-08-19
it is not broadcom; however, i looked at some other stuff and i have an Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter. people say it's easy to install via madwifi (see this website: [http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work/](http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work/) ) but when I get to sudo make install i get this error:
> dennis@dennis-laptop:~/Desktop/madwifi-ng-r2756+ar5007$ sudo make install
cd: 1: can't cd to /lib/modules/2.6.24-21-server/build
Makefile.inc:66: *** /lib/modules/2.6.24-21-server/build is missing, please set KERNELPATH.  Stop.

I googled that, and it said something about making a symbolic link? things that i tried to make a symbolic link were vague and i don't know what they mean...

---

