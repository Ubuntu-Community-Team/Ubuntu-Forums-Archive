---
title: "r-cran-hmisc: Installed, but not recognized by R"
date: 2008-09-20
forum: General Help
---

### Post by gordonsowner on 2008-09-20
Hi,

I tried to get the Hmisc package for R via:

```
aptitude install r-cran-hmisc
```

I got one 404 error, but I thought it looked like it worked through the problem.  However, when I try to access the Hmisc library in R, it tells me it doesn't exist.  Any ideas about this?  Here is the output I got from the 'aptitude' command:

```
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
Building tag database...
The following packages have been automatically kept back:
  bind9-host binutils ca-certificates exim4 exim4-base exim4-config 
  exim4-daemon-light file fuse-utils groff-base libapr1 libaprutil1 
  libck-connector0 libcurl3 libedit2 libelfg0 libfuse2 libgc1c2 libgif4 
  libhdf4g libicu38 libjasper1 liblockfile1 libltdl3 libmagic1 
  libmysqlclient15off libnetcdf4 libogdi3.2 libpcap0.8 libpq5 libtiff4 
  libx11-6 libx11-data libxau6 libxcb-xlib0 libxcb1 libxdmcp6 libxext6 
  libxml2 mailx mtools mysql-common openssh-blacklist openssh-client 
  openssl openssl-blacklist postgis postgresql-8.3 postgresql-client-8.3 
  postgresql-client-common postgresql-common python-apt python-central 
  python-gdbm tofrodos ucf x11-common xauth 
The following NEW packages will be automatically installed:
  r-cran-lattice 
The following packages have been kept back:
  adduser apache2 apache2-mpm-prefork apache2-utils apache2.2-common apt 
  apt-utils aptitude at base-files base-passwd bash bash-completion 
  belocs-locales-bin bsdutils console-setup console-terminus console-tools 
  coreutils cpio cron curl dash debconf debconf-i18n debianutils 
  dhcp3-client dhcp3-common dnsutils dosfstools dpkg e2fslibs e2fsprogs 
  eject ethtool fdutils findutils ftp gcc-4.2-base gdal-bin gettext-base 
  gnupg gpgv grep gzip hdparm hostname ifupdown initramfs-tools initscripts 
  iproute iptables klibc-utils klogd laptop-detect libacl1 libatm1 libattr1 
  libblkid1 libcomerr2 libconsole libcurl3-gnutls libcwidget3 libdb4.6 
  libdbus-1-3 libdevmapper1.02.1 libexpat1 libgcrypt11 libidn11 libiw29 
  libkeyutils1 libklibc libkrb53 libldap-2.4-2 liblzo2-2 libncurses5 
  libncursesw5 libnewt0.52 libpam-modules libpam-runtime libpam0g libpopt0 
  libsasl2-2 libsasl2-modules libsepol1 libsigc++-2.0-0c2a libslang2 libss2 
  libssl0.9.8 libtasn1-3 libtext-wrapi18n-perl libusb-0.1-4 libuuid1 
  libwrap0 login lsb-base lsb-release lshw lsof ltrace lynx lzma make 
  makedev man-db manpages mawk memtest86+ mime-support mktemp mlocate 
  module-init-tools mount mtr-tiny nano ncurses-base ncurses-bin netbase 
  netcat netcat-traditional ntfs-3g ntpdate openssh-server parted passwd 
  pciutils postgresql-8.3-postgis ppp pppconfig pppoeconf procps python 
  python-minimal python2.5 python2.5-minimal rsync sed ssl-cert strace sudo 
  sysklogd sysv-rc tar tasksel tasksel-data tcpd tcpdump telnet time tree 
  tzdata update-inetd usbutils util-linux util-linux-locales uuid-runtime 
  vim-common vim-tiny vsftpd w3m wget whiptail wireless-tools wpasupplicant 
  xkb-data 
The following NEW packages will be installed:
  r-cran-hmisc r-cran-lattice 
0 packages upgraded, 2 newly installed, 0 to remove and 223 not upgraded.
Need to get 595kB/1957kB of archives. After unpacking 7365kB will be used.
Do you want to continue? [Y/n/?] WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  r-cran-hmisc r-cran-lattice 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Writing extended state information...
Err http://http.us.debian.org sid/main r-cran-lattice 0.17-13-1
  404 Not Found [IP: 64.50.238.52 80]
E: Failed to fetch http://http.us.debian.org/debian/pool/main/l/lattice/r-cran-lattice_0.17-13-1_amd64.deb: 404 Not Found [IP: 64.50.238.52 80]
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
Building tag database...

```

---

### Post by cariboo on 2008-09-20
If you read the output from your post you will see that the programs did not download. Why are you downloading from a Debian repository when the programs you want to download are available in the Ubuntu repositories.

Even though Ubuntu is based on Debian Unstable, sometimes the packages get changed, and the debian version may not work exactly as expected.

Jim

---

### Post by gordonsowner on 2008-09-20
Ok, being not completely familiar with package downloads, I *thought* I was downloading from Ubuntu... I assumed when I issued the command that that was where the packages were coming from... Can you tell me how I set 'aptitude' (or do i have to use 'apt-get'?) to pull from the Ubuntu repositories?

Thanks,

---

### Post by Voynix on 2008-09-20
Hi,

To install the Hmisc package (or any other R package):

1. Open a terminal and type
```
sudo R
```

2. Invoke the install.packages command:
```
install.packages()
```

3. A dialog will prompt you for a cran mirror. Choose a location near you.

4. A new dialog will list all the available packages. Select Hmisc and and press ok.

The package will be installed. Close the terminal, and open a new R session (not sudo). To use the Hmisc library type

```
library(Hmisc)
```

Cheers

---

### Post by gordonsowner on 2008-09-21
Hi,

I tried that the first time... it required some other tools on my system (like gfortran, i believe).  that's why i tried the 'aptitude' install of the package... the same is true of perl modules which, if they are available, i install from aptitude rather than CPAN (for perl) or the method you suggested for R.

Any insight on why the aptitude install doesn't work?

Thanks,

---

