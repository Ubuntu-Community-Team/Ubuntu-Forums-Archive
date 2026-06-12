---
title: "Want to change flash player in Firefox"
date: 2008-08-13
forum: General Help
---

### Post by GmAz on 2008-08-13
How do I go about changing the flash player in Firefox3?  I am using Adobe's, but it is very buggy, slow and often just doesn't work.  I want to try the open source one that was available when I chose Adobe's, but I cannot find a way to get rid of Adobe's.  I can disable it, but it doesn't allow me to choose another one.  Thanks.

---

### Post by mb_webguy on 2008-08-13
While I really want to support open source efforts, you won't be upgrading by going to the open source Flash plugin.  If you just want Flash to work, there are a couple of things to try first.  

If you haven't already, try installing the libflashsupport package, which will fix some incompatibilities between Flash and PulseAudio that causes the Flash plugin (and often the browser) to crash.

If that doesn't make things any better, you could try upgrading to the newer version of the Adobe Flash plugin, which is in the Intrepid repositories, though you can download the deb package [here]("http://packages.ubuntu.com/intrepid/flashplugin-nonfree").  Make sure you uninstall the libflashsupport package first, if necessary.

If neither of those work for you, well...  you can try the open source plugins, but I haven't had much luck with them.  Search Synaptic for "flash plugins", and look for libflash-mozplugin, mozilla-plugin-gnash, or swfdec-mozilla.  Of those, I'd try mozilla-plugin-gnash first.  Be sure to uninstall flashplugin-nonfree or any other Flash plugins before you install another one.

Good luck...

P.S.  I'm using Flash 10 (the Intrepid package) and I'm not having any problems at all.

---

### Post by alienexplorers on 2008-08-17
Switch to the flash 10 files it should fix your problems, it did mine.

---

### Post by altonbr on 2009-02-27
Isn't there a command in the terminal to change Firefox's default flash player? Does anyone remember what it is?

---

