---
title: "[SOLVED] Running into problems while installing OOo 3.0"
date: 2008-11-09
forum: General Help
---

### Post by semitone36 on 2008-11-09
Hey all

I am in the middle of trying to install Open Office 3.0 following the [installation instructions]("http://download.openoffice.org/common/instructions.html#linux") and I am running into a snag.  I am on step 6, installing the rpm files, and I get this error:

```
travis@travis-laptop:~/Desktop/OOO300_m9_native_packed-1_en-US.9358/RPMS$ rpm -Uvih *rpm
error: Failed dependencies:
	/bin/basename is needed by jre-1.6.0_07-fcs.i586
	/bin/cat is needed by jre-1.6.0_07-fcs.i586
	/bin/cp is needed by jre-1.6.0_07-fcs.i586
	/bin/gawk is needed by jre-1.6.0_07-fcs.i586
	/bin/grep is needed by jre-1.6.0_07-fcs.i586
	/bin/ln is needed by jre-1.6.0_07-fcs.i586
	/bin/ls is needed by jre-1.6.0_07-fcs.i586
	/bin/mkdir is needed by jre-1.6.0_07-fcs.i586
	/bin/mv is needed by jre-1.6.0_07-fcs.i586
	/bin/pwd is needed by jre-1.6.0_07-fcs.i586
	/bin/rm is needed by jre-1.6.0_07-fcs.i586
	/bin/sed is needed by jre-1.6.0_07-fcs.i586
	/bin/sort is needed by jre-1.6.0_07-fcs.i586
	/bin/touch is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/cut is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/dirname is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/expr is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/find is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/tail is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/tr is needed by jre-1.6.0_07-fcs.i586
	/usr/bin/wc is needed by jre-1.6.0_07-fcs.i586
	/bin/sh is needed by jre-1.6.0_07-fcs.i586
	libfreetype.so.6 is needed by ooobasis3.0-core04-3.0.0-9358.i586
	libgnomevfs-2.so.0 is needed by ooobasis3.0-gnome-integration-3.0.0-9358.i586
	libgconf-2.so.4 is needed by ooobasis3.0-gnome-integration-3.0.0-9358.i586
	/bin/sh is needed by openoffice.org3-dict-en-3.0.0-9358.i586
	/bin/sh is needed by openoffice.org3-dict-es-3.0.0-9358.i586
	/bin/sh is needed by openoffice.org3-dict-fr-3.0.0-9358.i586

```

I really am not sure where to go from here... should I do an apt-get install for each and every one of these dependencies?  Ideas?

---

### Post by exploder on 2008-11-09
These instructions will get the job done.

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

This will save you a lot of trouble!

---

### Post by mike2357 on 2008-11-09
With Ubuntu, which is based on Debian, I think you would be better off by downloading OpenOffice's .deb files rather than .rpm files.

If you click on "more platforms and languages" at [http://www.openoffice.org]("http://www.openoffice.org") , you will see where you get the choice to download Linux DEB files.

Assuming you put all of the .deb files in a directory, you can install them using:

sudo dpkg -iR <directory_name>

When I installed OpenOffice3, I uninstalled OpenOffice2 first; I don't know if that's necessary but it might avoid confusion.

---

### Post by semitone36 on 2008-11-10
> **exploder said:**
> These instructions will get the job done.

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

This will save you a lot of trouble!

Thanks for the reply, unfortunately I already tried tombuntu's method and I ran into a similar problem...

[QUOTE=mike2357]With Ubuntu, which is based on Debian, I think you would be better off by downloading OpenOffice's .deb files rather than .rpm files.[/QUOTE]

This could very well be what I was doing wrong! I didnt realize I had a choice in files lol Ill try this out when I get home

---

### Post by snowpine on 2008-11-10
Are you using Intrepid? If so, there is a muuuuuch easier method:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Good luck!

---

### Post by ugm6hr on 2008-11-10
> **semitone36 said:**
> Thanks for the reply, unfortunately I already tried tombuntu's method and I ran into a similar problem...

This could very well be what I was doing wrong! I didnt realize I had a choice in files lol Ill try this out when I get home

tombuntu's method works for Hardy just fine - as long as you use the correct files (i.e. .deb download).

If you use 64-bit Ubuntu - you need to use Torrent to get the .deb

---

### Post by Skripka on 2008-11-10
> **ugm6hr said:**
> tombuntu's method works for Hardy just fine - as long as you use the correct files (i.e. .deb download).

If you use 64-bit Ubuntu - you need to use Torrent to get the .deb


You can get 64-bit debs right off the OO.org website too.

---

### Post by semitone36 on 2008-11-13
UPDATE:
Hey sorry for the slow reply, it turned out that mike2357 was right.  I needed to get the .deb files and I also needed the 64bit architecture.  So with a little searching I found what I was looking for in the OOo3 mirrors.  Thanks all for your help!

---

