---
title: "Configure IR Remote"
date: 2020-04-08
forum: Hardware
---

### Post by mmcmonster2 on 2020-04-08
I have a Logitech Harmony 650 remote.  The remote works perfectly out-of-the-box when running LibreElec (a bare-bones Linux distro that just runs Kodi).

I reformatted the computer and installed Linux Mint 19.3/Ubuntu Bionic 18.04.

Now the remote control doesn't work right.  Most of the buttons aren't configured at all.

I used the Ubuntu LIRC page ( [https://help.ubuntu.com/community/LIRC](https://help.ubuntu.com/community/LIRC) ), which doesn't work.  Installing lirc doesn't bring up the configuration screen.  If I type 'sudo dpkg-reconfigure lirc', it just pauses a couple seconds and returns to the prompt without any error messages or anything.

How can I configure my IR remote?

---

### Post by mmcmonster2 on 2020-04-08
Resolved.

Apparently, lirc is broken in Ubuntu Bionic.

You can fix the problem by installing lirc from Ubuntu Xenial and then fixating the package so it doesn't get updated to the newer version in Bionic.  See [https://twosortoftechguys.wordpress.com/2018/07/24/make-lirc-work-in-ubuntu-18-04/](https://twosortoftechguys.wordpress.com/2018/07/24/make-lirc-work-in-ubuntu-18-04/)

Hopefully this will get fixed before the Xenial repositories get taken off line.

---

