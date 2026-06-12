---
title: "inkscape install problem, apt-get update problem, ubuntu 8.04"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by statmech on 2009-03-30
Hi all:

I am trying to install inkscape under ubuntu 8.04, and got this strange problem:

```

   [root@apollo vql]# apt-get install inkscape
   Reading Package Lists... Done
   Building Dependency Tree... Done
   You might want to run `apt-get -f install' to correct these:
   The following packages have unmet dependencies:
     4Suite: Depends: PyXML (>= 0.7) but it is not going to be installed
     ORBit2: PreDepends: /sbin/install-info
	     Depends: libglib-2.0.so.0
	     Depends: libgmodule-2.0.so.0
	     Depends: libgobject-2.0.so.0
	     Depends: libgthread-2.0.so.0
     VFlib2: Depends: libttf.so.2
     XFree86: Depends: XFree86-base-fonts (= 4.3.0) but it is not going to be installed
	      Depends: libfreetype.so.6
     XFree86-font-utils: Depends: libfreetype.so.6
     XFree86-libs: Depends: freetype (>= 2.1.3-4) but it is not going to be installed

   ... cut ...

     xscreensaver: Depends: libglib-2.0.so.0
		   Depends: libgmodule-2.0.so.0
		   Depends: libgobject-2.0.so.0
     xsri: Depends: libglib-2.0.so.0
	   Depends: libgmodule-2.0.so.0
	   Depends: libgobject-2.0.so.0
     xterm: Depends: libfontconfig.so.1
	    Depends: libfreetype.so.6
     ypbind: Depends: portmap but it is not going to be installed
   E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
   [root@apollo vql]# 

```

Forced install:

```

   [root@apollo vql]# apt-get -f install
   Reading Package Lists... Done
   Building Dependency Tree... Done
   Correcting dependencies... Done
   The following extra packages will be installed:
      GConf2 (2.4.0-1)
      ORBit (0.5.17-10.3)
      Omni-foomatic (0.9.0-4)
      PyXML (0.8.3-1)
      SDL_mixer (1.2.4-9)
      XFree86-base-fonts (4.3.0-59.legacy)
      arts (1.1.4-3)
      aspell-devel (0.50.3-16)
      basesystem (8.0-2)
      compat-libstdc++-devel (7.3-2.96.118)
      cyrus-sasl-devel (2.1.15-6.2.legacy)
      dev (3.3.8-2)
      docbook-dtds (1.0-22.1)
      docbook-style-dsssl (1.78-2)
      fedora-logos (1.1.20-1)
      fedora-release (1-3)
      file (4.02-2)
      fontconfig (2.2.1-6.1)
      freetype (2.1.4-5)
      gd (2.0.15-1)
      gdk-pixbuf (0.22.0-11.3.4)
      glib (1.2.10-11)
      glib2 (2.2.3-1.1)
      gnome-python2-canvas (2.0.0-2)
      info (4.5-2)
      libcap (1.10-16)
      libgnome (2.4.0-1)
      libpcap (0.7.2-8.fc1.2)
      libungif (4.1.0-16)
      mkisofs (2.01-0.a19.2.FC1.1)
      mount (2.11y-29)
      net-tools (1.60-20.1)
      netpbm-progs (9.24-12.1.1)
      newt (0.51.6-1)
      openmotif (2.2.2-16.1.2.legacy)
      openssl (0.9.7a-33.10)
      perl-libwww-perl (5.65-6)
      portmap (4.0-57)
      ppp (2.4.1-15)
      procmail (3.22-11)
      pvm (3.4.4-14)
      redhat-config-language (1.0.16-1)
      redhat-config-printer (0.6.79.5-1)
      sane-backends (1.0.12-4)
      scrollkeeper (0.3.12-2)
      usermode (1.69-1)
      which (2.16-1)
      wxGTK2-gl (2.4.2-0.fdr.1.1)
      xmltex (20000118-14.1)
      xmms (1.2.10-1.p)
      yelp (2.4.0-1)
   The following packages will be REMOVED:
      curl-devel (7.10.6-7.2.legacy)
      kdeaddons (3.1.4-2)
      kdeartwork (3.1.4-1)
      kdebase (6:3.1.4-9.legacy)
      kdegames (6:3.1.4-2)
      kdegraphics (7:3.1.4-1)
      kdemultimedia (6:3.1.4-1)
      kdenetwork (7:3.1.4-1)
      kdeutils (6:3.1.4-1)
      libXinerama (1.0.1-1.2)
      openssh-askpass (3.6.1p2-19.4.legacy)
      openssh-clients (3.6.1p2-19.4.legacy)
      openssl-devel (0.9.7a-33.13.legacy)
   The following NEW packages will be installed:
      GConf2 (2.4.0-1)
      ORBit (0.5.17-10.3)
      Omni-foomatic (0.9.0-4)
      PyXML (0.8.3-1)
      SDL_mixer (1.2.4-9)
      XFree86-base-fonts (4.3.0-59.legacy)
      arts (1.1.4-3)
      aspell-devel (0.50.3-16)
      basesystem (8.0-2)
      compat-libstdc++-devel (7.3-2.96.118)
      cyrus-sasl-devel (2.1.15-6.2.legacy)
      dev (3.3.8-2)
      docbook-dtds (1.0-22.1)
      docbook-style-dsssl (1.78-2)
      fedora-logos (1.1.20-1)
      fedora-release (1-3)
      file (4.02-2)
      fontconfig (2.2.1-6.1)
      freetype (2.1.4-5)
      gd (2.0.15-1)
      gdk-pixbuf (0.22.0-11.3.4)
      glib (1.2.10-11)
      glib2 (2.2.3-1.1)
      gnome-python2-canvas (2.0.0-2)
      info (4.5-2)
      libcap (1.10-16)
      libgnome (2.4.0-1)
      libpcap (0.7.2-8.fc1.2)
      libungif (4.1.0-16)
      mkisofs (2.01-0.a19.2.FC1.1)
      mount (2.11y-29)
      net-tools (1.60-20.1)
      netpbm-progs (9.24-12.1.1)
      newt (0.51.6-1)
      openmotif (2.2.2-16.1.2.legacy)
      openssl (0.9.7a-33.10)
      perl-libwww-perl (5.65-6)
      portmap (4.0-57)
      ppp (2.4.1-15)
      procmail (3.22-11)
      pvm (3.4.4-14)
      redhat-config-language (1.0.16-1)
      redhat-config-printer (0.6.79.5-1)
      sane-backends (1.0.12-4)
      scrollkeeper (0.3.12-2)
      usermode (1.69-1)
      which (2.16-1)
      wxGTK2-gl (2.4.2-0.fdr.1.1)
      xmltex (20000118-14.1)
      xmms (1.2.10-1.p)
      yelp (2.4.0-1)
   0 upgraded, 51 newly installed, 13 removed and 0 not upgraded.
   Need to get 24.0MB/33.4MB of archives.
   After unpacking 36.8MB disk space will be freed.
   Do you want to continue? [Y/n] 
   Err http://download.fedora.us fedora/1/i386/os basesystem 8.0-2
     404 Not Found [IP: 152.46.7.221 80]
   Err http://download.fedora.us fedora/1/i386/os file 4.02-2
     404 Not Found [IP: 152.46.7.221 80]
   Err http://download.fedora.us fedora/1/i386/os fedora-release 1-3
     404 Not Found [IP: 152.46.7.221 80]
   Err http://download.fedora.us fedora/1/i386/os dev 3.3.8-2
     404 Not Found [IP: 152.46.7.221 80]
   Err http://download.fedora.us fedora/1/i386/os glib2 2.2.3-1.1
     404 Not Found [IP: 152.46.7.221 80]
   Err http://download.fedora.us fedora/1/i386/os info 4.5-2
     404 Not Found [IP: 152.46.7.221 80]
   Err http://download.fedora.us fedora/1/i386/os which 2.16-1
     404 Not Found [IP: 152.46.7.221 80]
   Err http://download.fedora.us fedora/1/i386/os GConf2 2.4.0-1
     404 Not Found [IP: 152.46.7.221 80]
   Err http://download.fedora.us fedora/1/i386/os glib 1:1.2.10-11
     404 Not Found [IP: 152.46.7.221 80]
   Err http://download.fedora.us fedora/1/i386/os ORBit 1:0.5.17-10.3
     404 Not Found [IP: 152.46.7.221 80]
   Err http://download.fedora.us fedora/1/i386/os Omni-foomatic 0.9.0-4
     404 Not Found [IP: 152.46.7.221 80]
   Err http://download.fedora.us fedora/1/i386/os SDL_mixer 1.2.4-9
     404 Not Found [IP: 152.46.7.221 80]

   ... cut ...

   Failed to fetch http://download.fedora.us/fedora/fedora/1/i386/RPMS.os/ppp-2.4.1-15.i386.rpm  404 Not Found [IP: 152.46.7.221
   80]
   Failed to fetch http://download.fedora.us/fedora/fedora/1/i386/RPMS.os/procmail-3.22-11.i386.rpm  404 Not Found [IP:
   152.46.7.221 80]
   Failed to fetch http://download.fedora.us/fedora/fedora/1/i386/RPMS.os/yelp-2.4.0-1.i386.rpm  404 Not Found [IP: 152.46.7.221
   80]
   E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
   [root@apollo vql]# 

```

Update apt-get database:

```

   [root@apollo vql]# apt-get update
   Ign http://ruslug.rutgers.edu fedora/1 release
   Ign http://download.fedora.us fedora/1/i386 release                            
   Ign http://rpm.livna.org fedora/1/i386 release                                 
   Err http://ruslug.rutgers.edu fedora/1/macromedia pkglist
     301 Moved Permanently
   Ign http://ruslug.rutgers.edu fedora/1/macromedia release                      
   Err http://ruslug.rutgers.edu fedora/1/macromedia srclist                      
     301 Moved Permanently
   Err http://download.fedora.us fedora/1/i386/os pkglist                         
     404 Not Found [IP: 152.46.7.221 80]
   Ign http://download.fedora.us fedora/1/i386/os release                

   ... cut ...

   Err http://rpm.livna.org fedora/1/i386/stable srclist
     302 Found
   Err http://rpm.livna.org fedora/1/i386/unstable srclist
     302 Found
   Err http://rpm.livna.org fedora/1/i386/testing srclist
     302 Found
   Failed to fetch http://ruslug.rutgers.edu/macromedia/apt/fedora/1/base/pkglist.macromedia  301 Moved Permanently
   Failed to fetch http://ruslug.rutgers.edu/macromedia/apt/fedora/1/base/srclist.macromedia  301 Moved Permanently

   ... cut ...

   Failed to fetch http://rpm.livna.org/fedora/1/i386/base/srclist.unstable  302 Found
   Failed to fetch http://rpm.livna.org/fedora/1/i386/base/srclist.testing  302 Found
   Reading Package Lists... Done
   Building Dependency Tree... Done
   E: Some index files failed to download, they have been ignored, or old ones used instead.
   [root@apollo vql]# 

```

It seems that the apt-get package repository web sites had been
moved, so I cannot even update the apt-get package repositories.

Thanks for any info and/or help.

---

### Post by Partyboi2 on 2009-03-30
Hi, can you open a terminal an post your sources.list please
```
cat /etc/apt/sources.list
```

---

### Post by Francewhoa on 2010-03-12
The following worked for me [http://ubuntuforums.org/showpost.php?p=8957047&postcount=6](http://ubuntuforums.org/showpost.php?p=8957047&postcount=6)

---

