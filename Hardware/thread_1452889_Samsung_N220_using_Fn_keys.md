---
title: "Samsung N220 using Fn keys"
date: 2010-04-12
forum: Hardware
---

### Post by BerlinNurse on 2010-04-12
I am using ubuntu on Samsung N220. I didn't found linux drives or software on samsungs website.
I want to use the Fn-keys for example, to deactivate the WLAN, the touchpad, show the battary-status, adjust the brightness, using the extern VGA (beamer), ...

---

### Post by BerlinNurse on 2010-04-13
Has no one an idea how to use the Fn keys with its netbook-specific funtions?

Why is it a netbook-distribution?

---

### Post by Patle on 2010-06-17
I assume you already got an answer. If not, the reason the fn-keys are not working is that the N150/N210N220 aren not recognized by udev.

You can update the files:

/lib/udev/rules.d/95-keymap.rules
/lib/udev/rules.d/95-keyboard-force-release.rules

so that the product is recognized and the fn-keys will at least be detected. Most of them work as expected as well.

See:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/554066](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/554066)

To get the brightness (fn-up and fn-dwn) working I just added keyboard shortcuts to a small program that adjusts the backlight, based on the idea of [http://ubuntuforums.org/showthread.php?t=1397371](http://ubuntuforums.org/showthread.php?t=1397371) post no 9

Hope that helps! :-)

---

