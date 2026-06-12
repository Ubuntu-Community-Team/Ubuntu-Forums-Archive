---
title: "Impossible Installation on a HP 6710b"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by Hell4You on 2007-11-15
Well, I found many forums, topics, other websites about this, but none of them could provide me the correct solution.

This is the most accurate: [http://mytwu.blogspot.com/2007/07/how-i-installed-ubuntu-feisty-fawn-on.html](http://mytwu.blogspot.com/2007/07/how-i-installed-ubuntu-feisty-fawn-on.html)

(I'm a novice ubuntu-user, so keep it easy plz [-o< :P)
I'll describe all the problems i found:

**At first: Installation is impossible.**
I have: 3x Ubuntu 7.10 Live CD (different downloads, burned at different speeds, different burners, different CD brands), and 1x Ubuntu 7.10 Alternate CD.
After many modifications in my BIOS i finally got the life CD to boot.
All three live cd's give a corrupt file error on about 67% (?? guessed). It's not in my laptop, because the same problem occures on another workstation i have.

Next i tried the Alternate CD, but it doesn't even boot the text-based installer. It stops on a blank screen after about 10-15 seconds from installation launch. ](*,)

The only way i can imagine to get Ubuntu on my laptop is using a preinstalled image, so i installed Ubuntu on my workstation using the Alternate CD (the Live CD's are corrupt), created an image and installed it on my laptop.
Now i had to use 'dpkg-reconfigure xserver-xorg' because the graphics on my workstation are different then on my laptop.

**Second: X3100 Graphics**
Great, it finally booted the installation. Now the frequently mentioned Intel GMA965 X3100 Graphics problem appeared. I couldn't enable the desktop effects (not that important, but i wanted to play warsow, look-a-like problem). First i had to manually edit the xorg.conf to support 1680x1050, and while this was fixed i tried infinite different tutorials, fixes and workarounds. But no success.

Can anybody tell me what went wrong? ANY help is greatly appreciated! :?

---

