---
title: "Tweaking Synaptics settings in Maverick"
date: 2010-11-09
forum: Hardware
---

### Post by dansmith on 2010-11-09
I'd like to adjust my trackpad settings with more control than is provided by the Mouse Preferences.  Various discussions suggested to me that what I need to do is adjust the Synaptics daemon settings.  However, nothing I've tried seems to work, and some of the instructions I'm seeing definitely don't apply to Maverick.

I'm observing the active settings via "synclient -l"

First attempt:
[http://jjinux.blogspot.com/2009/09/linux-least-bad-synaptics-configuration.html](http://jjinux.blogspot.com/2009/09/linux-least-bad-synaptics-configuration.html)

I created the directory /etc/hal/fdi/policy and added the suggested file.  After a reboot, no settings seemed to have changed.  Further reading suggested that HAL is not used in Maverick.

Second attempt:
[http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html](http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html)

I put a file similar to the suggestion in /etc/udev/rules.d (named appletouch.rules).  (The test setting I used was 'ENV{x11_options.TapButton3}="0"'.)  After a reboot, the TapButton3 setting had not changed.

Third attempt:
[http://ubuntuforums.org/showthread.php?t=1451386](http://ubuntuforums.org/showthread.php?t=1451386) (see also further discussion in the second attempt link)

I wanted to put a file like the one suggested in /usr/lib/X11/xorg.conf.d, but that directory does not exist.  The only xorg.conf.d directory on my system is /usr/share/X11/xorg.conf.d.  So I put my file (named customtrackpad.conf) there.  (The setting code: 'Option "TapButton3" "0"'.)  After a reboot, the TapButton3 setting still has not changed.

Since I have the impression a lot of people mess with these settings, I'm sure it can't be that complicated.  Can anyone enlighten me?

---

### Post by dino99 on 2010-11-09
uptodate help:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by dansmith on 2010-11-09
Just what I needed!  Thanks.

---

