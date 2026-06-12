---
title: "Use apt packages cache for Next Ubuntu clean Install?"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by AkifTariq on 2009-10-22
I use either alternate Ubuntu CD or minimal Ubuntu CD (when I have a good Internet connection available) to install Ubuntu. I am thinking of reinstalling Ubuntu soon. I figured out I have a lot of packages cached in a folder /var/cache/apt/archives. Is there a way that I can ask Ubuntu installation process to consult this cache folder first for latest packages if not found then get them from Internet (if using minimal Ubuntu installation CD) or Ubuntu Installation CD (if using alternate/live CD for installation). From other forums I read about apt-cacher but I do not know if I can set it while new installation of Ubuntu.

---

### Post by earthpigg on 2009-10-22
hi,

this may be the tool-you-are-looking-for-but-did-not-realize-it:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

:D

---

### Post by ajgreeny on 2009-10-22
> **earthpigg said:**
> hi,

this may be the tool-you-are-looking-for-but-did-not-realize-it:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

:D
Yes, this is the way!

Install it from the repos and run it to make an iso (or a CD if you want to, though I never bother with that) and save the iso to a usb drive.  Then reinstall, install aptoncd to the new install and run that to restore the iso you just made, and finally update your new install and add any packages you had previously.  I always find that not everything I have installed is still in the cache, in spite of asking for the system to keep everything in synaptic's preferences, but it will certainly save a lot of downloading.

---

### Post by AkifTariq on 2009-10-23
Thank you very much guys. I will definitely give it a try. I have downloaded its deb and will make an ISO in the evening.

---

