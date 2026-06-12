---
title: "Epson EPL driver problem - upgrade Ubuntu"
date: 2005-03-15
forum: Hardware &amp; Laptops
---

### Post by steffen on 2005-03-15
I've had severe trouble using my Epson EPL 6200L printer with Ubuntu. Aparently, there is a Debian bug in this driver, and I need to update/downgrade my Ghostscript gs-gpl and gs-esp.

On the site where I got this information ([http://sourceforge.net/forum/forum.php?forum_id=447670](http://sourceforge.net/forum/forum.php?forum_id=447670)) it says I should uninstall these before updating. However, when I attempt to de-select gs-esp, I get a series of dependancies that will also be removed, among them bonobo, Scribus, etc.

Is removing this really that crucial? Or can I only remove gs-epl 7.07.1-9 forcefully and immediately install my downloaded version, and assume the system would still work...?

---

### Post by steffen on 2005-03-17
For others who might have similar problems:

- apt-get remove gs-esp
- dpkg -i gs-afpl (sourceforge package)
- dpkg -i --force-downgrade gs-fonts-package from sourceforge
- dpkg -i --force-downgrade --force-overwrite ghostscript_8.14 package from sourceforge

---

### Post by steffen on 2005-03-17
For those who are wondering - this actually works, both through USB port and SMB network  =D>

Forum: [https://sourceforge.net/forum/forum.php?thread_id=1250082&forum_id=236645](https://sourceforge.net/forum/forum.php?thread_id=1250082&forum_id=236645)

Files: [https://sourceforge.net/project/showfiles.php?group_id=69547](https://sourceforge.net/project/showfiles.php?group_id=69547)

---

### Post by sooqing on 2006-01-08
Can you tell me where do you get gs-afpl and gs-fonts??

---

### Post by eradan on 2007-11-17
After the dist-upgrade to Gutsy my Epson EPL 6200L doesn't work anymore.

I've found a trick to print but it's not a good solution:

The printer works if I force the installation of this packages:

* gs-afpl_8.53-1_i386.deb
* libjasper-1.701-1

you can download them here:
* [http://packages.ubuntu.com/feisty/libs/libjasper-1.701-1](http://packages.ubuntu.com/feisty/libs/libjasper-1.701-1)
* [http://packages.ubuntu.com/feisty/text/gs-afpl](http://packages.ubuntu.com/feisty/text/gs-afpl)

and install it using:

* sudo dpkg -i libjasper-1.701-1_1.701.0-2ubuntu0.7.04_i386.deb
* sudo dpkg -i --force-conflicts gs-afpl_8.53-1_i386.deb

Now you can proceed to install the printer using this ppd file:

* [http://grappalug.homelinux.net/index.php?mod=none_Fdplus&fdaction=download&url=sections/03_Documenti/Epson_EPL6200L_su_Ubuntu/EPL-6200L.ppd.txt](http://grappalug.homelinux.net/index.php?mod=none_Fdplus&fdaction=download&url=sections/03_Documenti/Epson_EPL6200L_su_Ubuntu/EPL-6200L.ppd.txt)

(note that this is a modified ppd that use the gs-aflp as interpreter)

and the debian package driver:

* [http://grappalug.homelinux.net/index.php?mod=none_Fdplus&fdaction=download&url=sections/03_Documenti/Epson_EPL6200L_su_Ubuntu/epsoneplijs_0.4.0-2_i386.deb](http://grappalug.homelinux.net/index.php?mod=none_Fdplus&fdaction=download&url=sections/03_Documenti/Epson_EPL6200L_su_Ubuntu/epsoneplijs_0.4.0-2_i386.deb)

Now the printer should work (at least: it does on my system).

But *unfortunaly* you cannot upgrade your system anymore!!!
Anytime you'll try to dist-upgrade you'are going to have back an error message due the presence of the gs-afpl package! :(

You can remove it, upgrade your system and reinstall gs-afpl again...

Yes, this is just a placebo!
I hope that someone could give us better informations for Gutsy!!!

A better and suitable solution should be to find a proper filter (in place of gs-afpl) to use in the ppd file that produce the postscript to send to the printer...

Any ideas?

Cheers,
Ivan

---

