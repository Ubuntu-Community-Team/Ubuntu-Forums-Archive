---
title: "Lightweight Way to Install Single HP ppd Driver?"
date: 2013-02-18
forum: Hardware
---

### Post by jakfish on 2013-02-18
lubuntu 12.10/HP 6500 wireless printer
 
I have the 6500's ppd, it installs, but I get a bunch of errors about missing files and programs when I try to print test page.
 
I'd rather not install the enire HP package (20+ mbs) especially this printer will be abandoned shortly.  Even the PCL 3 generic driver, which I downloaded into /usr/share/ppd won't work, though both said drivers talk to the printer wirelessly; they just won't put out a page.
 
12.04 had the HP drivers; I can't find any drivers in clean install of 12.10 (livecd, no update from 12.04)
 
Thanks for any help,
Jake

---

### Post by schragge on 2013-02-18
```

sudo lpadmin -E -p [color=blue]printer[/color] -P [color=blue]ppd-file[/color]

```
where
[color=blue]printer[/color] - name of your printer as shown by *lpstat -t*
[color=blue]ppd-file[/color] - PPD file for your printer

---

### Post by jakfish on 2013-02-18
Many thanks for the quick response.  Did as you suggested, command successfully entered, but I'm getting the error:

Idle - File "/usr/lib/cups/filter/foomatic-rip-hplip" not available: No such file or directory

I imagine that file is in the huge hplip.  Does that mean I have to install the entire package?

Jake

Follow-up: I symlinked it to foomatic-rip, and then was prompted for the hpijs program, which appears to be stand-alone in repo.  Installed that, test page talks wirelessly to printer, but prints out only failure to initialize error.

---

### Post by schragge on 2013-02-18
Do you have *printer-driver-hpijs* installed?

[highlight]Edit.[/highlight]
Oh I see. Yes, you do.
Where did you get the ppd file from? This one is HPIJS for quantal:
[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/quantal/hplip/quantal-proposed/download/package-import%40ubuntu.com-20120620201900-q8gny3mevpunkkbt/hpdeskjet_6500hpijs.-20091205021850-ayi2h4dh5pxsp4gj-7347/hp-deskjet_6500-hpijs.ppd.gz](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/quantal/hplip/quantal-proposed/download/package-import%40ubuntu.com-20120620201900-q8gny3mevpunkkbt/hpdeskjet_6500hpijs.-20091205021850-ayi2h4dh5pxsp4gj-7347/hp-deskjet_6500-hpijs.ppd.gz)

Instead of *printer-driver-hpijs*, you also can try *printer-driver-hpcups*. The ppd for it:
[http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/quantal/hplip/quantal-proposed/download/package-import%40ubuntu.com-20120620201900-q8gny3mevpunkkbt/hpdeskjet_6500.ppd.g-20091205021850-ayi2h4dh5pxsp4gj-6603/hp-deskjet_6500.ppd.gz](http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/quantal/hplip/quantal-proposed/download/package-import%40ubuntu.com-20120620201900-q8gny3mevpunkkbt/hpdeskjet_6500.ppd.g-20091205021850-ayi2h4dh5pxsp4gj-6603/hp-deskjet_6500.ppd.gz)

---

### Post by jakfish on 2013-02-18
I using the ppd you sugest, from bazaar.  I ended up installing the hplip from the repo--the last time, I used the latest from linux open printing, and their's was much gigger, 60 mbs of apps and depedencies and installed things I didn't need such as HP Manager.

The one in the repo is smaller and to the point.

Do you know Lubuntu 12.10 has little in the way of print drivers when 12.04 had a full stock?

Thanks again for your assistance,
Jake

---

