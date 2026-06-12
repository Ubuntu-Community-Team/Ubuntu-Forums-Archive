---
title: "Install Open Office 3.10 by complete novice"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by bsmith52 on 2009-05-17
I wanted to install Open Office 3.10 because it seemed to be the easiest way to extract text from a .pdf file (in conjunction with pdfimport.oxt). The [www.openoffice.org](www.openoffice.org) site recommended removal of the native version (I have ubuntu 8.10 with Open Office 2.4), so I executed the Synaptic Package Manager and uninstalled all the Open Office packages that I could find.  I then downloaded the package onto my desktop:

bill@bill-desktop:~/Desktop$ ls
basic                                           pdfimport.oxt
description.xml                                 pdfimport.uno.so
help                                            pdf_types.xcu
META-INF                                        registration
OOo_3.1.0_LinuxIntel_install_wJRE_en-US.tar.gz  xpdfimport
pdf_import_filter.xcu                           xpdfimport_err.pdf

I then did the following:

sudo tar xfvz OOo_3.1.0_LinuxIntel_install_wJRE_en-US.tar.gz

I now have the following:

bill@bill-desktop:~/Desktop$ ls
basic            META-INF                                        pdf_import_filter.xcu  pdf_types.xcu  xpdfimport_err.pdf
description.xml  OOo_3.1.0_LinuxIntel_install_wJRE_en-US.tar.gz  pdfimport.oxt          registration
help             OOO310_m11_native_packed-2_en-US.9399           pdfimport.uno.so

I moved to the newly created directory, and see this:

bill@bill-desktop:~/Desktop$ cd OOO310_m11_native_packed-2_en-US.9399
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-2_en-US.9399$ ls
installdata  JavaSetup.jar  licenses  readmes  RPMS  setup  update

This is where I am stuck.  I am so new to ubuntu and Linux that I can't figure out how to do the actual install.

---

### Post by bngguy on 2009-05-17
> **bsmith52 said:**
> I wanted to install Open Office 3.10 because it seemed to be the easiest way to extract text from a .pdf file (in conjunction with pdfimport.oxt). The [www.openoffice.org](www.openoffice.org) site recommended removal of the native version (I have ubuntu 8.10 with Open Office 2.4), so I executed the Synaptic Package Manager and uninstalled all the Open Office packages that I could find.  I then downloaded the package onto my desktop:

bill@bill-desktop:~/Desktop$ ls
basic                                           pdfimport.oxt
description.xml                                 pdfimport.uno.so
help                                            pdf_types.xcu
META-INF                                        registration
OOo_3.1.0_LinuxIntel_install_wJRE_en-US.tar.gz  xpdfimport
pdf_import_filter.xcu                           xpdfimport_err.pdf

I then did the following:

sudo tar xfvz OOo_3.1.0_LinuxIntel_install_wJRE_en-US.tar.gz

I now have the following:

bill@bill-desktop:~/Desktop$ ls
basic            META-INF                                        pdf_import_filter.xcu  pdf_types.xcu  xpdfimport_err.pdf
description.xml  OOo_3.1.0_LinuxIntel_install_wJRE_en-US.tar.gz  pdfimport.oxt          registration
help             OOO310_m11_native_packed-2_en-US.9399           pdfimport.uno.so

I moved to the newly created directory, and see this:

bill@bill-desktop:~/Desktop$ cd OOO310_m11_native_packed-2_en-US.9399
bill@bill-desktop:~/Desktop/OOO310_m11_native_packed-2_en-US.9399$ ls
installdata  JavaSetup.jar  licenses  readmes  RPMS  setup  update

This is where I am stuck.  I am so new to ubuntu and Linux that I can't figure out how to do the actual install.

just delete everything you downloaded and the directory that was created and download the deb package which can be found here:

[http://download.openoffice.org/other.html#en-US]("http://download.openoffice.org/other.html#en-US")

---

### Post by bsmith52 on 2009-05-17
Thanks, I'll try that first thing in the am.

Bill

---

