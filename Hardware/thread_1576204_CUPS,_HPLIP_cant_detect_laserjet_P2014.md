---
title: "CUPS, HPLIP cant detect laserjet P2014"
date: 2010-09-16
forum: Hardware
---

### Post by baronsamedi on 2010-09-16
Hello,

I am running ubuntu 10.04. I have a Hewlett Packard Laserjet P2014 that was taking forever to print PDFs, so i did some search and decided to try my luck upgrading HPLIP from

[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

I had to install it manually to include the --enable-pp-build option, as the printer goes through the paralel port. For a while the printer was detected, but wouldnt print anything (not even the test page), and all I was getting the "/usr/lib/cups/backend/hp failed" message. So I started tinkering with CUPS, and eventually deleted the printer from the list, and now hp-setup, CUPS or the Printer Admin can't find the printer.

hp-check says:

"warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP."

I am completely lost and knackered by now. Anybody has any idea about what I can do?

Thanks.

---

### Post by baronsamedi on 2010-09-18
SOLVED

What I dis is remove completely HPLIPS:

```
$ sudo rm -rf /usr/share/hplip
$ sudo rm -rf /etc/hp
$ sudo rm -rf ~/.hplip
```

Then remove completely CUPS

```
$ sudo apt-get purge cups
```

(I renamed the directory /etc/cups, which the unistall hadn't deleted, just to make sure that no trace of the older installation remained)

And then installed HPLIP following the instructions here

[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

(No need to install CUPS, as the installation of HPLIP includes it)

... et presto!

---

