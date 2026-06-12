---
title: "Scanner through wireless router?"
date: 2011-02-07
forum: Hardware
---

### Post by carfield on 2011-02-07
I've asked a question and cannot find solution for a long time:

I am using wireless router WL-520GU, it have a USB port connected to a printer + scanner: "HP Photosmart C4400"

I can print to this printer by pointing CUPS to use network printer at socket://192.168.1.1:9100, can I also get the scanning image from the scanner?

I've installed xsane and sane. And tried to run "xsane
hpaio:/net/photosmart_c4400_series?ip=192.168.1.1". However, it is complaining:

"Dec 11 02:58:10 (none) xsane: io/hpmud/jd.c 88: unable to read device-id"

Look like xsane actually expecting the wireless router at 192.168.1.1 have sane daemon setup... but that is not the case.

Can I tell xsane send scanning command as it is an USB connection, to ip 192.168.1.1? That is the way will work but I cannot find any solution about this. Will anyone know any program can do this?

---

### Post by [Snc] on 2011-02-07
If the scanner is not a network scanner (has a Ethernet port), then network scanning is almost impossible. 

Some network multi tasking devices (scanner/printer/fax/...) have a homepage on their URL (IP 192.168.x.y), if yours has not, then the only solution, I can give you is, that you install some network scanning deamon along with a custom firmware (ie. Oleg or tomato) for your router.

To get to the point, the effort is bigger than the reward after that :), either it is supported out of the box, or not at all.

PS. You can still try the ASUS community ;)

---

### Post by carfield on 2011-02-07
Any router model that have linux support out of the box? Buy a router probably cheap nowadays :-)

---

### Post by [Snc] on 2011-02-08
> **carfield said:**
> Any router model that have linux support out of the box? Buy a router probably cheap nowadays :-)

*Maybe you know of any router, that hasn't got Linux support???*

I don't know every router manufacturer out there, but I would say 99 of 100 routers are Linux driven ;). 

The WL 500 series (520 counts too) goes well with the Oleg or tomato firmware, this allows you to telnet (via putty) to the router and manage it like a remote PC (running linux).

---

### Post by carfield on 2011-02-08
I've do a quick search, for my WL-520GU router, it need to do a lot of thing to get SANE install there, and a lot of them fail.

For WL 500 series, is there built-in SANE support? Say WL 500g [http://reviews.cnet.com/ASUS_WL500g_LAN_router/4505-3319_7-30650222.html](http://reviews.cnet.com/ASUS_WL500g_LAN_router/4505-3319_7-30650222.html) , is that just plug and play for scanner? Say my linux client config is fine.

---

### Post by [Snc] on 2011-02-08
> **carfield said:**
> I've do a quick search, for my WL-520GU router, it need to do a lot of thing to get SANE install there, and a lot of them fail.

For WL 500 series, is there built-in SANE support? Say WL 500g [http://reviews.cnet.com/ASUS_WL500g_LAN_router/4505-3319_7-30650222.html](http://reviews.cnet.com/ASUS_WL500g_LAN_router/4505-3319_7-30650222.html) , is that just plug and play for scanner? Say my linux client config is fine.

I also have the WL500Gp, with Oleg :)

The WL community is huge (russia, china, ...) so it should be in unslung. And since WL500 has a debian based OS, you can recompile the sources :)

A word from this [forum]("http://wl500g.info/archive/index.php/t-923.html")
> done.
as usual : 
ipkg update
ipkg install sane-backends

You'll need xinetd or inetd (inetutils) to make it run.

---

