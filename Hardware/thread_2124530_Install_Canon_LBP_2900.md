---
title: "Install Canon LBP 2900"
date: 2013-03-11
forum: Hardware
---

### Post by drjugaljpatel on 2013-03-11
Hello,
I have installed the 12.10 64bit version. I have been through all the LBP 2900 installation posts, but none of them have been able to solve my problem. The printer is recognized but does not print, it just shows as processing. Downloaded the latest 2.5 drivers from canon, followed their instructions, I get these errors... 

root@jugal-Vostro-A840:/home/jugal/Downloads/Linux_CAPT_PrinterDriver_V250_uk_EN/64-bit_Driver/RPM# rpm -ivh cndrvcups-common-2.50-1.x86_64.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: Failed dependencies:
    /bin/sh is needed by cndrvcups-common-2.50-1.x86_64
    libatk-1.0.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libc.so.6 is needed by cndrvcups-common-2.50-1.x86_64
    libc.so.6()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libc.so.6(GLIBC_2.0) is needed by cndrvcups-common-2.50-1.x86_64
    libc.so.6(GLIBC_2.1) is needed by cndrvcups-common-2.50-1.x86_64
    libc.so.6(GLIBC_2.1.3) is needed by cndrvcups-common-2.50-1.x86_64
    libc.so.6(GLIBC_2.2.5)(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libc.so.6(GLIBC_2.3) is needed by cndrvcups-common-2.50-1.x86_64
    libc.so.6(GLIBC_2.3)(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libcups.so.2()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libdl.so.2 is needed by cndrvcups-common-2.50-1.x86_64
    libdl.so.2()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libdl.so.2(GLIBC_2.0) is needed by cndrvcups-common-2.50-1.x86_64
    libdl.so.2(GLIBC_2.1) is needed by cndrvcups-common-2.50-1.x86_64
    libgdk-x11-2.0.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libgdk_pixbuf-2.0.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libglade-2.0.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libglib-2.0.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libgmodule-2.0.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libgobject-2.0.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libgtk-x11-2.0.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libm.so.6 is needed by cndrvcups-common-2.50-1.x86_64
    libm.so.6()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libm.so.6(GLIBC_2.0) is needed by cndrvcups-common-2.50-1.x86_64
    libpango-1.0.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libpangox-1.0.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libpangoxft-1.0.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libpthread.so.0 is needed by cndrvcups-common-2.50-1.x86_64
    libpthread.so.0()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libpthread.so.0(GLIBC_2.0) is needed by cndrvcups-common-2.50-1.x86_64
    libpthread.so.0(GLIBC_2.1) is needed by cndrvcups-common-2.50-1.x86_64
    libpthread.so.0(GLIBC_2.2.5)(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libpthread.so.0(GLIBC_2.3.2) is needed by cndrvcups-common-2.50-1.x86_64
    librt.so.1 is needed by cndrvcups-common-2.50-1.x86_64
    libxml2.so.2()(64bit) is needed by cndrvcups-common-2.50-1.x86_64
    libz.so.1()(64bit) is needed by cndrvcups-common-2.50-1.x86_64

How do i proceed?

---

### Post by pdc on 2013-03-11
......one solution is to wait for 13.04 ubuntu ........... that will seem exciting .......and then install the 32bit version of that ............ sadly 32bit installs allow quick and successful installs of the capt driver ...using the 32bit debian packages that Canon supply

.....or today create a small 32bit 12.10 ubuntu partition; install the 32bit deb packages ....and enjoy using your printer

or work your way through this thread [http://translate.google.co.nz/translate?sl=fr&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Ftutoriel%2Finstaller_pilote_canon_lbp](http://translate.google.co.nz/translate?sl=fr&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Ftutoriel%2Finstaller_pilote_canon_lbp)

where Sivella offers instructions: for a beginner who insists on a 64bit install, they give themselves extra work!!

---

