---
title: "[SOLVED] Gimp 2.6.3 Install Problems"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by jdorenbush on 2008-12-08
I am trying to install [Gimp 2.6.3]("ftp://ftp.gimp.org/pub/gimp/v2.6/"). I currently have the version that is listed in the Synaptic, 2.6.1.

*The only reason I am updating is to try and gain the ability to contain all the Gimp windows within one window - see this [screenshot]("http://www.gimp.org/screenshots/gnome-1280x800-fresh-start.jpg"). As opposed to having my graphic, Toolbox, and Layers window all opened in separate windows, which hogs up my Windows List in the ubuntu Panel.*

The only way to update is to download source files. I removed Gimp 2.6.1. Downloaded source files for 2.6.3, extracted, and ran ./configure. This is the error message I was given.

```
checking for BABL... configure: error: Package requirements (babl >= 0.0.22) were not met:

No package 'babl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BABL_CFLAGS
and BABL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

I checked 'babl' in Synaptic and it shows it as installed.

---

### Post by taurus on 2008-12-08
Make sure you install the -dev (libbabl-0.0.0-dev) also.

---

### Post by jdorenbush on 2008-12-08
Got it, that worked. Thanks

---

### Post by jdorenbush on 2008-12-09
*EDIT: Mark as solved. Creating new thread.*

---

### Post by Mark Phelps on 2008-12-09
I know you solved this by using the source, but you can also do this without using the source by doing the following:
1) Go to GetDeb and scroll to the GIMP 2.6.3 entry
2) Download the three GIMP-related packages
3) Use the package installer on each of the packages, starting with the library package and ending with GIMP
4) You will have to run a package resynch command in the middle, but it will tell you about that.
5) It will remove some gutenprint packages in the process
6) When done, you have the new 2.6.3 GIMP

Just thought I'd mention this so that, when they upgrade next time, you won't have to struggle with the source to do an upgrade.

---

### Post by jdorenbush on 2008-12-09
> **Mark Phelps said:**
> I know you solved this by using the source, but you can also do this without using the source by doing the following:
1) Go to GetDeb and scroll to the GIMP 2.6.3 entry
2) Download the three GIMP-related packages
3) Use the package installer on each of the packages, starting with the library package and ending with GIMP
4) You will have to run a package resynch command in the middle, but it will tell you about that.
5) It will remove some gutenprint packages in the process
6) When done, you have the new 2.6.3 GIMP

Just thought I'd mention this so that, when they upgrade next time, you won't have to struggle with the source to do an upgrade.

How do I do step #4?

---

### Post by Mark Phelps on 2008-12-09
When I did this, I got an error message about the synaptic cache being out of sync and to run a specific command -- which fixed it.  The install order was:
1) gimp-data
2) libgimp
3) gimp

I think the error was right after the gimp-data but before the libgimp. That was when it told me that gutenprint was being uninstalled. Sorry, I don't remember the actual error message. If you tried this and didn't get the error message, then there is no problem with synaptic.

---

