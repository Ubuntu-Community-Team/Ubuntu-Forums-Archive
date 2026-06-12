---
title: "Trouble while configuring SynCE to sync with a WM5 device"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by 7ofAnn on 2007-02-04
Hi everyone

I'm trying to install SynCE (Ubuntu 6.10), following the oultine on [http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_Subversion](http://www.synce.org/index.php/Building_SynCE_with_Windows_Mobile_2005_support_from_Subversion)

I get into trouble while doing ./configure of the odccm part.  The following output is the error message I get:

+=========================================================================
checking for LIBSYNCE... yes
checking for GLIB... yes
checking for GNET... configure: error: Package requirements (gnet-2.0) were not met:

No package 'gnet-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNET_CFLAGS
and GNET_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
+=========================================================================

This is Chinese to me (even after reading the man pages).  How to proceed, does anyone have a clue?  

I tried to install the package gnet-2.0, but it could not be found.

Thanks in advance for your help.
Ann

---

### Post by argotnaut on 2007-06-30
Ann, the packages you need to install are libgnet-dev and libgnet2.0-0. After I installed those, it was complaining about hal, so I then had to install libhal-dev.

---

