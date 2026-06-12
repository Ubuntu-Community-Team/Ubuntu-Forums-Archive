---
title: "Gnome Download Manager Application?"
date: 2008-10-07
forum: General Help
---

### Post by Nullack on 2008-10-07
Hi :)

Ive been looking around for a download manager that:

1. Allows for scheduling so I can use my off peak ISP time
2. Interfaces with FF
3. Preferably is gnome based so I dont have to install QT

I dont seem to be able to find one?

Any help would be appreciated, thanks

---

### Post by jerome1232 on 2008-10-07
Well I don't know if this meet your criteria but it's a firefox addon call downthemall

[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

I'm trying it out right now

---

### Post by Nullack on 2008-10-07
It doesnt support scheduling by the look of it? Having used it before I found the code to be slow and to drag my cpu down a fair bit.

---

### Post by jerome1232 on 2008-10-07
Ok I'll take another crack at it :) from the repos I did a search for download manager:
```
apt-cache search download manager
elinks - advanced text-mode WWW browser
elinks-data - advanced text-mode WWW browser - data files
elinks-doc - advanced text-mode WWW browser - documentation
kget - download manager for KDE 4
ktorrent - BitTorrent client for KDE
synaptic - Graphical package manager
aria - Tool to download files from the Internet via HTTP or FTP
awn-applets-python-core - A collection of applets for avant-window-navigator
d4x - graphical download manager
d4x-common - graphical download manager - common files
elinks-lite - advanced text-mode WWW browser - lightweight version
emusic-remote - browser and download manager for eMusic.com
epiphany-extension-gwget - Gwget extension for Epiphany web browser
gwget - GNOME front-end for wget
jedit - a cross platform programmer's text editor written in Java
jigdo - GTK+ download manager (beta version)
libparallel-forkmanager-perl - A simple parallel processing fork manager for Perl
metacafe-dl - download videos from metacafe.com
moto4lin - file manager and seem editor for Motorola phones (like C380/C650)
qnapi-gnome - application that downloads Polish subtitles from www.napiprojekt.pl
qtstalker - commodity and stock market charting and technical analysis
sixpack-bibtex - bibtex bibliography and reference manager
torrentflux - web based, feature-rich BitTorrent download manager
wmget - Background download manager in a Window Maker dock app

```

A couple caught my eye d4x, and aria
more of these may be what your looking for, run apt-cache show on the ones you think might make it, then try the ones that look promising. d4x seems to have everything but FF integration. I'll bet gwget is decent since wget is so good.
```
apt-cache show d4x
Package: d4x
Priority: optional
Section: universe/net
Installed-Size: 2116
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian QA Group <packages@qa.debian.org>
Architecture: amd64
Version: 2.5.7.1-5
Depends: libao2 (>= 0.8.8), libatk1.0-0 (>= 1.13.2), libc6 (>= 2.6.1-1), libcairo2 (>= 1.4.0), libfontconfig1 (>= 2.4.0), libgcc1 (>= 1:4.2.1), libglib2.0-0 (>= 2.14.0), libgtk2.0-0 (>= 2.12.0), libpango1.0-0 (>= 1.19.0), libssl0.9.8 (>= 0.9.8e-1), libstdc++6 (>= 4.2.1), libx11-6, libxcomposite1 (>= 1:0.3-1), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxrandr2 (>= 2:1.2.0), libxrender1, d4x-common (= 2.5.7.1-5)
Filename: pool/universe/d/d4x/d4x_2.5.7.1-5_amd64.deb
Size: 741976
MD5sum: 78123aab9e7abe78e779884a36a0c344
SHA1: 26cf831a94ec6541bc6a05a7f0d38f23b6140180
SHA256: 7fc8a965b1269e9326fac3802b94c62b6b237d94a65d34322b88830b08f52331
Description: graphical download manager
 Downloader for X is a powerful graphical download manager.
 It supports both HTTP(S) and FTP protocols and has nice graphical
 user interface, though some actions can also be performed using
 the command line.
 .
 Among others, its key features include proxy and SOCKS5 support,
 recursive downloading, wildcard matching, download scheduler,
 multiple download queues and more...
 .
 Homepage: http://www.krasu.ru/soft/chuchelo/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu



apt-cache show aria
Package: aria
Priority: optional
Section: universe/net
Installed-Size: 2028
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Rene Engelhard <rene@debian.org>
Architecture: amd64
Version: 1.0.0-16.1
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1-21), libglib1.2ldbl (>= 1.2.10-18), libgtk1.2 (>= 1.2.10-4), libssl0.9.8 (>= 0.9.8f-1), libstdc++6 (>= 4.2.1-4), libx11-6, libxext6, libxi6, zlib1g (>= 1:1.2.3.3.dfsg-1)
Filename: pool/universe/a/aria/aria_1.0.0-16.1_amd64.deb
Size: 702584
MD5sum: 8becb5a6a409ea0c1de987e10935a7ac
SHA1: 462e5bf87d8a50363fae865add1c6f93732045f5
SHA256: b01c44026590506e4b2d20879857004ba6a6f2c1a8a5f9ac73bd151834965ac2
Description: Tool to download files from the Internet via HTTP or FTP
 Aria is a download manager.
 .
 The transfer can be paused, resumed, queued and saved. It has a very user
 friendly GTK based GUI, and useful log consoles. Program supports
 CRC checking, HTTP proxy server, cut-and-paste, drag-and-drop, and
 can define specific file retrieving procedure for particular web servers.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by Nullack on 2008-10-07
Thanks, I did have various searches around the place before posting. D4X's website is having a page load error and seems to be deprecated now so I didnt try that before posting. I had a look at the various aria2 front ends but I dont see where they do scheduling.

I noticed wikipedia had a comparison table for download managers but that again didnt help.

Im begginning to think such an app doesnt exist on gnome.

---

### Post by brijith on 2008-10-10
Hai,

I suggest **wget**. It may help you. though it has a got a GTK version I personally prefer to use it in terminal. You can add it in cron tab to schedule the download.

If you need advice in this direction you can ask me. I will help you.

---

### Post by jaygo on 2008-12-29
I highly recommend the flashgot plugin for firefox. It will let you pass all or some downloads to your preferred download manager, and it has a long list of presets to save you time. Essentially, it integrates whatever download manager you have with your browser.

---

