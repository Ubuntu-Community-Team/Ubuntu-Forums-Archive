---
title: "Apache + PHP dependency problems"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by anonymousreality on 2009-01-30
Hi,

I'm having some problems getting some PHP modules to load properly due to some dependency problems with .so files and I don't have enoug experience of ubuntu or linux to solve them (quickly).

Here are the error messages:
```

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/bbcode.so' - /lib/libc.so.1: version `SUNW_1.1' not found (required by /usr/lib/php5/20060613+lfs/bbcode.so) in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/gd.so' - libX11.so.4: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/http.so' - libcurl.so.4: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/zip.so' - /lib/libc.so.1: version `SUNW_1.1' not found (required by /usr/lib/php5/20060613+lfs/zip.so) in Unknown on line 0

```

The offending modules (http.so, zip.so, gd.so and bbcode.so) were, possibly foolishly, manually copied from an existing installation, so weren't really installed properly.

EDIT: It just occured to me that trying to install these properly might help! However, that didn't work either, these 404 errors from apt-get are quite possibly what's holding me back

```

$ sudo apt-get --fix-missing install php5-gd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  defoma file fontconfig-config libapache2-mod-php5 libfontconfig1 libgd2-xpm libxpm4 php5-cgi php5-common php5-mysql ttf-dejavu
Suggested packages:
  defoma-doc psfontmgr x-ttcidfont-conf dfontmgr php-pear libgd-tools
Recommended packages:
  libft-perl
The following packages will be REMOVED:
  libgd2-noxpm
The following NEW packages will be installed:
  defoma file fontconfig-config libfontconfig1 libgd2-xpm libxpm4 php5-gd ttf-dejavu
The following packages will be upgraded:
  libapache2-mod-php5 php5-cgi php5-common php5-mysql
4 upgraded, 8 newly installed, 1 to remove and 53 not upgraded.
Need to get 3915kB/12.0MB of archives.
After unpacking 8114kB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  defoma ttf-dejavu fontconfig-config libfontconfig1 libxpm4
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com feisty/main defoma 0.11.10
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com feisty/main ttf-dejavu 2.14-2
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com feisty/main fontconfig-config 2.4.2-1ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com feisty/main libfontconfig1 2.4.2-1ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com feisty/main libxpm4 1:3.5.6-1
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/defoma/defoma_0.11.10_all.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/t/ttf-dejavu/ttf-dejavu_2.14-2_all.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/fontconfig-config_2.4.2-1ubuntu1_all.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/libfontconfig1_2.4.2-1ubuntu1_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxpm/libxpm4_3.5.6-1_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Unable to correct missing packages.
E: Aborting install.

```

I know that I need to install certain packages to get these up and running, but I've no idea which ones and the ones that I have been able to figure out just give 404s when trying to run apt-get. I've tried aptitude as well, but no joy.

Install Info: Linux skylamp 2.6.20-16-server #2 SMP Sun Sep 23 19:57:25 UTC 2007 i686

I just hope I haven't broken anything yet!

Anyone able to help?

Thanks,
Brian.

---

