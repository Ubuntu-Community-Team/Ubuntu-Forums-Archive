---
title: "Problems with ATI driver"
date: 2005-01-14
forum: Hardware &amp; Laptops
---

### Post by cassius on 2005-01-14
I have tried to install the driver for my Radeon 9700 Pro gfx card.

I converted the rpm to .deb. I removed the xlibmesa-gl package because it conflicted with the installation. Then I forced the installation of the driver.

When I use the lsmod command I find the fglrx module.

But fglrxinfo shows that Im still using the mesa driver.

When I try to install the xlibmesa-gl package again I get this error:

"The following packages have unmet dependencies:
  python2.3-mysqldb: Depends: libmysqlclient10 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)."

And when I try to install anything else I get this error:

"Depends: xlibmesa-gl but it is not going to be installed or
libgl1"

on several packages.

Can anybody help me? Im stuck!  ](*,)

---

### Post by emperor on 2005-01-15
I would recommend that you use the ati packages for your card that are in the Universe repo.  The packages are:
   
   fglrx-driver
   fglrx-control
   
  See the oldest (first) entry in this thread on how to add the Universe to apt's .
  [http://www.ubuntuforums.org/showthread.php?t=179]("http://www.ubuntuforums.org/showthread.php?t=179")
  
   There is a short Howto here and more info on the forum:
   [http://www.ubuntulinux.org/wiki/BinaryDriverHowto]("http://www.ubuntulinux.org/wiki/BinaryDriverHowto")
   
   In order to get Xv working, you will have to run fglrxconfig.
  ====================================
   1. Back up your current XF86Config-4 file first.
   2. sudo fglrxconfig
   3. When asked " Do you want to use an external AGPGART, chooise Y.
   4. You will also need to correct the fonts, copying the "FontPath ..." entries to
   the new XF86Config-4 file and disable the incorrect or incomplete font listings.
  
  The above info is in the first entry in this thread:
  [http://www.ubuntuforums.org/showthread.php?t=3567&page=5&pp=10]("http://www.ubuntuforums.org/showthread.php?t=3567&page=5&pp=10")
   
 After proper installation, you should be able to change your screen resolution using "gnome-display-properties" in the "Computer - System Configuration Menu"
   
   e.p.

---

