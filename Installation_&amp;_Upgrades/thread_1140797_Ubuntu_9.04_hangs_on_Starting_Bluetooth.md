---
title: "Ubuntu 9.04 hangs on Starting Bluetooth"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by lex3001 on 2009-04-27
I just installed Ubuntu 9.04 on an AMD Athlon machine (ASUS A7V8X mobo, 1.5GB RAM).

When I plug in my USB wifi (Linksys WUSB54G v.1) and try and boot, it hangs forever at Starting Bluetooth. I do not have any bluetooth devices.

If I keep this USB device plugged in and try and install Ubuntu from the CD, the same problem occurs during the installation from the CD.

If I unplug it then I can install and boot fine.

How do I resolve this?

Sounds similar to this but supposedly this was resolved a long time ago:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927)

---

### Post by jolarson on 2009-06-05
I am having the same problem.  I just did a fresh install of 9.04 and it hangs on boot whenever I have my Linksys wusb54g connected to the computer.  Then once I have booted it does not recognize the wireless card.  It also seems to hang when I enter lsusb, in the terminal.  It worked previously when I had 8.10 installed, though it doesn't work in the 64bit Ubuntu.

---

### Post by jenkinbr on 2009-06-06
Same issue here - linksys wusb54gsc--a model which I have come to associate with a lot of cussing and swearing.

I ended up ditching the adaptor all together in favor of a nice, cheap belkin model.

---

### Post by Frenziefrenz on 2009-06-10
Same here with a Linksys WUSB54GS v1.

---

### Post by jolarson on 2009-06-13
so does anyone have any insight on how to fix this problem?

---

### Post by jolarson on 2009-06-24
bump!

---

### Post by wpshooter on 2009-06-24
> **jolarson said:**
> so does anyone have any insight on how to fix this problem?

When you are doing the installation of Ubuntu are you using the live/desktop CD version or the ALTERNATE (text based) CD version ?

---

### Post by jolarson on 2009-06-24
I used the Live CD version off of a USB flash drive.

---

### Post by wpshooter on 2009-06-24
> **jolarson said:**
> I used the Live CD version off of a USB flash drive.

I would try installing from the ALTERNATE CD version.

---

### Post by jolarson on 2009-06-24
I will try that tonight when I get home.

---

### Post by jolarson on 2009-06-25
After reinstalling from the alternate CD it still does the same thing.  It hangs on boot if the Wireless card is plugged in.  and if I boot without it then put it in it hangs lsusb.  Do you have any other suggestions or ideas?  Might disabling/uninstalling bluetooth fix it?

---

### Post by jenkinbr on 2009-06-26
If you don't use bluetooth, You can safely disable it.

How to do this, I don't know, but I can check.

edit: I'm not sure how to disable bluetooth.  I just settled with uninstalling it. (I can always re-install later, if needed)

---

### Post by jolarson on 2009-06-26
I tried uninstalling the bluetooth packages, but that did not really help.  Though it does slowly boot.  but still it hangs lsusb.  so it seems there is some other error as well.

---

