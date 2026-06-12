---
title: "render-dev dependency issue"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by RagingOcelot on 2006-03-29
Hi all,

I'm trying to get libxrender-dev installed, in which case I need render-dev, but I already have x11proto-render-dev installed.  When I try to install the render-dev package so that libxrender-dev can be installed, I get the message:

Preconfiguring packages ...
(Reading database ... 209268 files and directories currently installed.)
Unpacking render-dev (from .../render-dev_1%3a0.9.2-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/render-dev_1%3a0.9.2-1_all.deb (--unpack):
 trying to overwrite `/usr/lib/pkgconfig/renderproto.pc', which is also in package x11proto-render-dev
Errors were encountered while processing:
 /var/cache/apt/archives/render-dev_1%3a0.9.2-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

This is an error I of course have to fix as I cannot install any other package until this issue is cleared up.  I take it renderproto.pc is probably an important file.  Does anyone have any suggestions?

---

### Post by RagingOcelot on 2006-04-01
so no one's ever had this happen to them?

---

### Post by HankD on 2006-05-02
I just had it happen (and all the X font rendering is now wrong).
Did you find a fix?

---

### Post by RagingOcelot on 2006-05-02
A fresh install of Ubuntu did the trick (big surprise).  I think I made the mistake of enabling experimental repositories which led to a lot of dependency issues.  Can't swear to it, but I think that's what it was.

---

### Post by HankD on 2006-05-03
Debian Testing repository seems to be the culprit.
Turning off that and "apt-get install -f" seems to fix it,
although the font defaults still seem to be changed.

---

