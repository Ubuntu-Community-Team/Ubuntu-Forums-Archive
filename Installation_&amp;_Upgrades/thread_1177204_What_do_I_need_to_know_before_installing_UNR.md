---
title: "What do I need to know before installing UNR?"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by kstella on 2009-06-03
My MSI Wind U100 is still running Hardy Heron, and I'd like to switch to Jaunty - Ubuntu Netbook Remix. Is there anything I need to know beforehand - what might stop working afterward, etc.?

I'd also like to know if it's possible to make the switch without erasing my home folder. :s

I read [here]("https://wiki.ubuntu.com/UNR/Installation/Hard") that I can just add the packages to my Hardy installation, but I'd rather move up to Jaunty because of better support for my wireless card.

Thanks.

---

### Post by dandnsmith on 2009-06-03
I suggest that the first thing is to create a bootable USB stick,
and run it as a live system without installing.
That way you'll have a much better idea of whether it can cope with your hardware.

After that you'll possibly have some more informed questions to ask.

---

### Post by kstella on 2009-06-03
That's a good idea; I guess I'll do that.

According to the [wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#MSI%20Wind%20U100"), though, it "Works very well" and doesn't list any necessary additional tweaks.

---

### Post by Brandon Williams on 2009-06-04
I the [release notes for Jaunty](http://www.ubuntu.com/getubuntu/releasenotes/904) there is a very important note about a problem in the current version of the "desktop-switcher" utility, which is used to switch between the UNR interface and a standard Gnome desktop. If you switch to Jaunty UNR, I suggest that you either install the developer's custom desktop-switcher (see the bug report referenced in the release notes) or avoid using the desktop-switcher.

---

### Post by kstella on 2009-06-07
Thanks for the heads up, Brandon!

---

