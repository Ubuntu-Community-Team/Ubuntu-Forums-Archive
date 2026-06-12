---
title: "New graphics card then Ubuntu seems to &quot;hang&quot;"
date: 2015-04-24
forum: Hardware
---

### Post by deeppow on 2015-04-24
Installed a new graphics card, Nvidia 960, and was expecting to have to install new driver.  Booting into Ubuntu 14.04, it says it needs to run in lower resolution.  No problem with that but a menu then comes up that would appear to allow me to run at lower resolution.  But Ubuntu at that point doesn't respond to either the keyboard nor mouse.  I'm using a wireless combo so I plugged a wired keyboard, no difference.

How do I get by this problem?  Thanks for any help!

---

### Post by ajgreeny on 2015-04-24
What was the previous graphic card?

If you previously had another card using a different driver to the one needed for the nvidia 960, that driver should have been removed before you booted with the new card.

Try booting to a text console either by choosing recovery mode or by hitting "E" when you get the grub menu and replacing "quiet splash" in the kernel line with text then running the removal command with **sudo apt-get remove <old-driver-package>** then reboot again.

You may also need to remove any /etc/X11/xorg.conf file that already exists, if there is one.

---

### Post by deeppow on 2015-04-24
Went from GTX650Ti to the GTX960.

I'll give that a try.  Appreciate the info.

---

### Post by efflandt on 2015-04-26
Which Ubuntu version and nvidia driver version. I have a GTX 750 Ti that also has the new Maxwell chip and even though it worked with an updated nvidia-current (304) driver in 12.04 and worked with live/install iso, it did not work with default nouveau driver or when I installed nvidia-current in 14.04.1 from root console with networking enabled in recovery boot. It worked after I purged that and installed **nvidia-331-updates**. I am currently running **nvidia-349** package from xorg-edgers ppa.

I wish I had known that the GTX 960 was about to be released within a month after I got my GTX 750 Ti, but the GTX 750 Ti works fine for the games I play using half the power of the GTX 960 or my old GTX 550 Ti (60 watts vs. 120 or 116 watts).

But since GTX 960 is newer I cannot confirm if it works with nvidia-331-updates or if you need a newer nvidia version from a ppa repo.

---

