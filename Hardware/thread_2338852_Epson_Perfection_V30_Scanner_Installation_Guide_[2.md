---
title: "Epson Perfection V30 Scanner Installation Guide [2016]"
date: 2016-10-02
forum: Hardware
---

### Post by maclenin on 2016-10-02
After performing a successful (re) install of the iscan application / scanner drivers for a usb-connected Epson Perfection V30 scanner in a 16.04 (xubuntu 64 bit) environment, I thought I'd leave a few notes to (perhaps) ease the path for others. These [2016] notes are based on [this earlier guide]("https://ubuntuforums.org/showthread.php?t=1447789").

There appear to be two separate Epson links available, which (in combination) provide access to the necessary (.deb) packages. The packages are bundled inside the *data*, *core* and *plugins* folders of an *iscan-*.tar.gz* archive.

I used the search terms *v30* and *Linux* on the Epson site to find the drivers.

1. This [link]("http://download.ebz.epson.net/dsc/search/01/search/searchModule") leads (via search) to a (later) version of the *data* and *core* packages and **esci** plugin.
2. This [link]("http://support.epson.net/linux/en/iscan_c.html") leads (directly) to a (previous) version of the *data* and *core* packages and **network** plugin.

A README file is archived alongside the package folders and provides a simple 3-step installation aside.

There are also thorough install and usage notes available via link from the driver download page.

In my case, I had already installed the data and core packages from link 2, before I located and used dpkg to install the esci plugin (only) via link 1 (without removing the "previous" version data and core packages).

All works to...perfection.

Good luck!

---

