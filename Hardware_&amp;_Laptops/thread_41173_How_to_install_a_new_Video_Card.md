---
title: "How to install a new Video Card?"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by Musashi on 2005-06-12
I have a onboard card, works fine but I will install a new one. How to configure X to the new card work fine?

---

### Post by skoal on 2005-06-12
I assume you are using an "integrated" video controller when you say "onboard"?  Either way, the easiest sol'n would be to:

1. From within the current X session you are in now, open up /etc/X11/xorg.conf and change the driver to "nv", "ati", or whatever default X driver matches your new card.
2. power down the computer, insert the new video card, and reboot.
3. Hit F2/Del for BIOS, and make sure "onboard/integrated" video is disabled.  Save and reboot.

You should (hopefully) get a GDM login screen.  If not, wait til GDM kills itself, then touch up any X driver related issues in xorg.conf.

4. After the default driver for your card works in an X session, then follow one of the 2 guidelines for installing an accelerated Nvidia or ATI driver.

\\//_

---

