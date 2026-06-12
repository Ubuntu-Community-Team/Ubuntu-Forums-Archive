---
title: "[SOLVED] Radeon HD4350"
date: 2008-11-17
forum: General Help
---

### Post by hjallen on 2008-11-17
cross-listed from multimedia and video
Has anyone had success with the Radeon HD4350? I have tried following the suggested install at [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) with no luck. The install appears to work but on reboot it reverts to low-res mode. Let me know if I need to provide any other info. I cannot find any direct references to the use of this card with Ubuntu or other dists. I know it is a new offering but need a card that works now. I need to decide pretty soon whether to abandon and return or not. Any suggestions would be appreciated. My setup is the following
Ubuntu Hardy 64
Gigabyte GA-EP45-UD3P
ASUS EAH4350 SILENT/DI/512MD2
4 gb corsair dominator
Intel core 2 duo E8500

Thanks

---

### Post by Yellow Pasque on 2008-11-18
It won't give you hardware acceleration right now, but I'd recommend building the open-source radeonhd driver to get high resolutions. Even if you intend to install the proprietary driver, this will make it easier to work in the desktop.
I wrote this document, so let me know if you have issues: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by hjallen on 2008-11-18
thanks for the reply. i tried it and things went well until the configure and here is what i got...

jallen@ariel:/usr/src/xf86-video-radeonhd$ sudo libtoolize
jallen@ariel:/usr/src/xf86-video-radeonhd$ sudo ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: configure.ac: not using aclocal
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
configure.ac:10: error: possibly undefined macro: AM_CONFIG_HEADER
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:14: error: possibly undefined macro: AM_INIT_AUTOMAKE
configure.ac:16: error: possibly undefined macro: AM_MAINTAINER_MODE
configure.ac:37: error: possibly undefined macro: AM_CONDITIONAL
configure.ac:69: error: possibly undefined macro: XORG_DRIVER_CHECK_EXT
configure.ac:86: error: possibly undefined macro: AC_MSG_WARN
configure.ac:335: error: possibly undefined macro: XORG_MANPAGE_SECTIONS
configure.ac:337: error: possibly undefined macro: XORG_RELEASE_VERSION
autoreconf: /usr/bin/autoconf failed with exit status: 1
jallen@ariel:/usr/src/xf86-video-radeonhd$ sudo make
make: *** No targets specified and no makefile found.  Stop.

It suggested I move libtool.m4 to aclocal.m4 so I did this, right or wrong.
/usr/share/aclocal/libtool.m4 aclocal.m4

Any help is appreciated...  I am off to bed and will check back late tomorrow.

---

### Post by Yellow Pasque on 2008-11-18
Hmm.. Other people have had this issue too. I'm thinking the list of dependencies that build-dep gave me was missing something. See if the xorg-dev package is installed on your system for me.
```
sudo apt-get install xorg-dev
```

If it was already installed, try this before the autogen command:
```
cd /usr/src/xf86-video-radeonhd
sudo libtoolize -v --copy --install
```

---

### Post by hjallen on 2008-11-18
when I try 
sudo libtoolize -v --copy --install
it fails and doesn't like the -v or --install options.  checking the help, these options are not listed.

so I ran with --copy only and got similar results as before.
jallen@ariel:/usr/src/xf86-video-radeonhd$ sudo libtoolize  --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
jallen@ariel:/usr/src/xf86-video-radeonhd$ sudo ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: configure.ac: not using aclocal
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
configure.ac:10: error: possibly undefined macro: AM_CONFIG_HEADER
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:14: error: possibly undefined macro: AM_INIT_AUTOMAKE
configure.ac:16: error: possibly undefined macro: AM_MAINTAINER_MODE
configure.ac:37: error: possibly undefined macro: AM_CONDITIONAL
configure.ac:69: error: possibly undefined macro: XORG_DRIVER_CHECK_EXT
configure.ac:86: error: possibly undefined macro: AC_MSG_WARN
configure.ac:335: error: possibly undefined macro: XORG_MANPAGE_SECTIONS
configure.ac:337: error: possibly undefined macro: XORG_RELEASE_VERSION
autoreconf: /usr/bin/autoconf failed with exit status: 1
jallen@ariel:/usr/src/xf86-video-radeonhd$ sudo make
make: *** No targets specified and no makefile found.  Stop.


any thoughts?
thanks

---

### Post by hjallen on 2008-11-18
i found that i did not have the acinclude.m4 so I copied libtool.m4 to acinclude.m4 followed by aclocal.  running the libtoolize and autogen commands then gave me...
sudo libtoolize
You should update your `aclocal.m4' by running aclocal.
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
jallen@ariel:/usr/src/xf86-video-radeonhd$ sudo ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal -I m4
aclocal: couldn't open directory `m4': No such file or directory
autoreconf: aclocal failed with exit status: 1

---

### Post by Yellow Pasque on 2008-11-19
Hmm. I'm sorry that this is turning about to be more difficult than I thought for you. Anyway, this is what my m4 dir looks like:

```
:/usr/src/xf86-video-radeonhd/m4$ ls -la
drwxr-sr-x 2 root src   4096 2008-11-18 01:55 .
drwxr-sr-x 9 root src   4096 2008-11-18 01:56 ..
lrwxrwxrwx 1 root src     29 2008-10-28 23:26 libtool.m4 -> /usr/share/aclocal/libtool.m4
lrwxrwxrwx 1 root src     33 2008-10-28 23:26 lt~obsolete.m4 -> /usr/share/aclocal/lt~obsolete.m4
lrwxrwxrwx 1 root src     31 2008-10-28 23:26 ltoptions.m4 -> /usr/share/aclocal/ltoptions.m4
lrwxrwxrwx 1 root src     29 2008-10-28 23:26 ltsugar.m4 -> /usr/share/aclocal/ltsugar.m4
lrwxrwxrwx 1 root src     31 2008-10-28 23:26 ltversion.m4 -> /usr/share/aclocal/ltversion.m4
```

---

### Post by hjallen on 2008-11-20
I don't have an m4 directory in  /usr/src/xf86-video-radeonhd/ 
Also, at the xorg radeon wiki [http://www.x.org/wiki/radeonhd](http://www.x.org/wiki/radeonhd)
it is suggested that 64bit users use
 ./autogen.sh --prefix /usr --libdir /usr/lib64.
This appears to work better but I still have low-res on reboot.
Thanks for all your help.

---

### Post by erdewit on 2008-11-22
I have an HD4350 card as well (from Asus) and managed to compile the latest radeonhd driver from git. Unfortunately the only thing I get is a completely white screen. I can hear the welcome sound of KDE though.

---

### Post by Yellow Pasque on 2008-11-22
hjallen, I did a clean install of Ubuntu 8.10 (64-bit) and the directions worked perfectly without any sort of extra setup. At this point, I think your issue has to do with something being different in Hardy (older version of autotools?). I hope to hear from more Hardy users.

erdewit, the white screen error almost sounds like something from fglrx interfering. Did you previously use fglrx/Catalyst? If so, is it still installed?

---

### Post by hjallen on 2008-11-24
I have upgraded to 8.10.  After working on other Intrepid issues (shutdown hangs on ALSA, and the flaky NetworkManager) I have returned to the video card.  The first thing I noticed was that lspci now recognizes the chip-set on the video card.  Compiling as instructed works but on reboot, video is transient, out of focus, and the colors are not right.  When I recover and use the vesa drivers at least I get 1280x1024 video.  Any thoughts on why the video is so poor?
Thanks.

---

### Post by hjallen on 2008-11-24
Question:  What is the difference between the Radeonhd and fglrx drivers?  I'm sure I am missing something obvious but an explanation on this would be appreciated.  Does the fglrx driver support the radeon hd4350?

---

### Post by hjallen on 2008-12-01
radeonhd driver works now.  I had to change the Screen section of xorg.conf.  The monitor or driver does not like 1680x1050.
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"radeonhd 4350"
	Monitor		"DELL 2007WFP"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x960" "1280x1024"
#"1680x1050" 
		ViewPort	0 0
	EndSubSection
EndSection

```

---

### Post by hjallen on 2008-12-02
After a lot of searching I found a the trick for getting the 8.11 ati fglrx driver installed on intrepid 64bit.  A good fellow named Kano put together this script to repackage the intrepid make to avoid the mismatched ABI version error.  The script is at:
[http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)
Hopefully this will be fixed in the next ati release.

---

