---
title: "hp deskjet f4280 install problems"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by Littlejohn on 2009-01-10
Hi all.

I'm fairly new to Ubuntu and I'm not what you would call a "natural". But for some reason I love it, even if I've been trying to set up my hp deskjet f4280 on hardy (64bit) for a few weeks without any success.

Today I decided to try the install following these instructions:
[http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

It all seemed to go well until Step 6.

When I do sudo python ./installer/fix_symlink.py,
I get: python: can't open file './installer/fix_symlink.py': [Errno 2] No such file or directory

When I try cat /installer/fix_symlink.py, 
I get: cat: /installer/fix_symlink.py: No such file or directory

I searched for the script, but can't find it anywhere. 

From what I can see from the 'make' messages (what was left in the buffer), there were a few warnings but nothing I though was a show-stopper.

Is this script a result of the 'make'? or the 'configure' or the download?

Would anyone have an idea how could I correct this?

Ultimately I'd like to set it up wirelessly to me Apple Time Capsule so I can print wirelessly from my macbook too.

But for now, I just want to be able to print from Ubuntu. I can from my MB already.

Thanks,

Jean

---

### Post by taurus on 2009-01-10
Are you in the right directory?  What's the output of this command from a terminal?

```
ls -la
```
By the way, ./installer/fix_symlink.py is not the same as /installer/fix_symlink.py.

---

### Post by Littlejohn on 2009-01-10
I think I was in hplip-2.8.12 (I moved around since then...)

an@ubuntu-desktop:~/Desktop/hplip-2.8.12$ ls -al
total 14460
drwxr-xr-x 19 jean gdm   12288 2009-01-10 10:17 .
drwxr-xr-x  3 jean jean   4096 2009-01-10 10:13 ..
-rw-r--r--  1 jean gdm  280156 2008-12-17 16:45 aclocal.m4
-rwxr-xr-x  1 jean gdm    8328 2008-12-17 16:41 align.py
drwxr-xr-x  2 jean gdm    4096 2008-12-17 16:45 base
-rwxr-xr-x  1 jean gdm   29385 2008-12-17 16:41 check.py
-rwxr-xr-x  1 jean gdm    6450 2008-12-17 16:41 clean.py
-rwxr-xr-x  1 jean gdm    9168 2008-12-17 16:41 colorcal.py
-rwxr-xr-x  1 jean gdm   44573 2007-04-27 15:13 config.guess
-rw-r--r--  1 jean gdm   40769 2009-01-10 10:15 config.log
-rwxr-xr-x  1 jean gdm   32124 2009-01-10 10:15 config.status
-rwxr-xr-x  1 jean gdm   32665 2007-04-27 15:13 config.sub
-rwxr--r--  1 jean gdm  815650 2008-12-17 16:45 configure
-rwxr-xr-x  1 jean gdm   14197 2008-12-17 16:44 configure.in
drwxr-xr-x  2 jean gdm    4096 2008-12-17 16:45 copier
-rw-r--r--  1 jean gdm   17941 2008-12-17 16:41 COPYING
-rw-r--r--  1 jean gdm     830 2009-01-10 10:16 cupsext.la
-rw-r--r--  1 jean gdm     350 2009-01-10 10:16 cupsext_la-cupsext.lo
-rwxr-xr-x  1 jean gdm   25502 2008-12-17 16:41 dat2drv.py
drwxr-xr-x  9 jean gdm    4096 2008-12-17 16:45 data
-rwxr-xr-x  1 jean gdm   17574 2006-11-17 09:08 depcomp
drwxr-xr-x  2 jean gdm   12288 2009-01-10 10:17 .deps
-rwxr-xr-x  1 jean gdm    2498 2008-12-17 16:41 devicesetup.py
drwxr-xr-x  4 jean gdm    4096 2008-12-17 16:46 doc
-rwxr-xr-x  1 jean gdm   24990 2008-12-17 16:41 fab.py
-rw-r--r--  1 jean gdm   43696 2009-01-10 10:17 fat.o
drwxr-xr-x  4 jean gdm    4096 2008-12-17 16:45 fax
-rwxr-xr-x  1 jean gdm    2299 2008-12-17 16:41 faxsetup.py
-rwxr-xr-x  1 jean gdm    5603 2008-12-17 16:41 firmware.py
-rw-r--r--  1 jean gdm   73757 2008-12-17 16:45 foomatic_drv.inc
-rwxr-xr-x  1 jean gdm    5002 2009-01-10 10:17 hp
-rwxr-xr-x  1 jean gdm    7016 2008-12-17 16:41 hpdio.py
-rw-r--r--  1 jean gdm   40904 2009-01-10 10:17 hp-hp.o
-rwxr-xr-x  1 jean gdm    6996 2009-01-10 10:17 hpijs
-rw-r--r--  1 jean gdm   65136 2009-01-10 10:17 hpijs-apollo21xx.o
-rw-r--r--  1 jean gdm   54184 2009-01-10 10:17 hpijs-apollo2560.o
-rw-r--r--  1 jean gdm  116232 2009-01-10 10:17 hpijs-apollo2xxx.o
-rw-r--r--  1 jean gdm   13880 2009-01-10 10:17 hpijs-breaks_open.o
-rw-r--r--  1 jean gdm    1237 2009-01-10 10:17 hpijs-capture.o
-rw-r--r--  1 jean gdm   28568 2009-01-10 10:17 hpijs-colormatcher_open.o
-rw-r--r--  1 jean gdm   44552 2009-01-10 10:17 hpijs-colormatch.o
-rw-r--r--  1 jean gdm   85872 2009-01-10 10:17 hpijs-compression.o
-rw-r--r--  1 jean gdm  101264 2009-01-10 10:17 hpijs-context.o
-rw-r--r--  1 jean gdm   15408 2009-01-10 10:17 hpijs-create_so.o
-rw-r--r--  1 jean gdm   30096 2009-01-10 10:17 hpijs-creator.o
-rw-r--r--  1 jean gdm   22424 2009-01-10 10:17 hpijs-dj3320_cmap.o
-rw-r--r--  1 jean gdm  332872 2009-01-10 10:17 hpijs-dj3320.o
-rw-r--r--  1 jean gdm   70064 2009-01-10 10:17 hpijs-dj350.o
-rw-r--r--  1 jean gdm   19528 2009-01-10 10:17 hpijs-dj3600_cmap.o
-rw-r--r--  1 jean gdm   57872 2009-01-10 10:17 hpijs-dj3600.o
-rw-r--r--  1 jean gdm   63120 2009-01-10 10:17 hpijs-dj4100_cmap.o
-rw-r--r--  1 jean gdm   77104 2009-01-10 10:17 hpijs-dj540.o
-rw-r--r--  1 jean gdm    9600 2009-01-10 10:17 hpijs-dj600_maps.o
-rw-r--r--  1 jean gdm  104376 2009-01-10 10:17 hpijs-dj600.o
-rw-r--r--  1 jean gdm  116136 2009-01-10 10:17 hpijs-dj630.o
-rw-r--r--  1 jean gdm    6432 2009-01-10 10:17 hpijs-dj660_maps.o
-rw-r--r--  1 jean gdm   91944 2009-01-10 10:17 hpijs-dj660.o
-rw-r--r--  1 jean gdm    9584 2009-01-10 10:17 hpijs-dj690_maps.o
-rw-r--r--  1 jean gdm  105392 2009-01-10 10:17 hpijs-dj690.o
-rw-r--r--  1 jean gdm   62736 2009-01-10 10:17 hpijs-dj6xx.o
-rw-r--r--  1 jean gdm    6448 2009-01-10 10:17 hpijs-dj850_maps.o
-rw-r--r--  1 jean gdm  104064 2009-01-10 10:17 hpijs-dj850.o
-rw-r--r--  1 jean gdm   57608 2009-01-10 10:17 hpijs-dj890.o
-rw-r--r--  1 jean gdm    9624 2009-01-10 10:17 hpijs-dj895_maps2.o
-rw-r--r--  1 jean gdm    6416 2009-01-10 10:17 hpijs-dj895_maps.o
-rw-r--r--  1 jean gdm   80152 2009-01-10 10:17 hpijs-dj8x5.o
-rw-r--r--  1 jean gdm  117200 2009-01-10 10:17 hpijs-dj8xx.o
-rw-r--r--  1 jean gdm    6488 2009-01-10 10:17 hpijs-dj970_maps2.o
-rw-r--r--  1 jean gdm    6448 2009-01-10 10:17 hpijs-dj970_maps3.o
-rw-r--r--  1 jean gdm   12792 2009-01-10 10:17 hpijs-dj970_maps.o
-rw-r--r--  1 jean gdm  131608 2009-01-10 10:17 hpijs-dj9xx.o
-rw-r--r--  1 jean gdm  200704 2009-01-10 10:17 hpijs-dj9xxvip.o
-rw-r--r--  1 jean gdm  117736 2009-01-10 10:17 hpijs-djgenericvip.o
-rw-r--r--  1 jean gdm    1239 2009-01-10 10:17 hpijs-filterhpa.o
-rw-r--r--  1 jean gdm   34192 2009-01-10 10:17 hpijs-globals.o
-rw-r--r--  1 jean gdm   54184 2009-01-10 10:17 hpijs-halftoner.o
-rw-r--r--  1 jean gdm   51936 2009-01-10 10:17 hpijs-halftoner_open.o
-rw-r--r--  1 jean gdm   51096 2009-01-10 10:17 hpijs-header.o
-rw-r--r--  1 jean gdm   40768 2009-01-10 10:17 hpijs-hpijsfax.o
-rw-r--r--  1 jean gdm   63904 2009-01-10 10:17 hpijs-hpijs.o
-rw-r--r--  1 jean gdm   30192 2009-01-10 10:17 hpijs-hpiom.o
-rw-r--r--  1 jean gdm   25160 2009-01-10 10:17 hpijs-htmtxhi.o
-rw-r--r--  1 jean gdm   14280 2009-01-10 10:17 hpijs-ijs.o
-rw-r--r--  1 jean gdm   47440 2009-01-10 10:17 hpijs-ijs_server.o
-rw-r--r--  1 jean gdm   42144 2009-01-10 10:17 hpijs-jccolor.o
-rw-r--r--  1 jean gdm   19952 2009-01-10 10:17 hpijs-jdatadbf.o
-rw-r--r--  1 jean gdm   85816 2009-01-10 10:17 hpijs-job.o
-rw-r--r--  1 jean gdm  135744 2009-01-10 10:17 hpijs-ljcolor.o
-rw-r--r--  1 jean gdm  157704 2009-01-10 10:17 hpijs-ljfastraster.o
-rw-r--r--  1 jean gdm  196200 2009-01-10 10:17 hpijs-ljjetready.o
-rw-r--r--  1 jean gdm   84176 2009-01-10 10:17 hpijs-ljm1005.o
-rw-r--r--  1 jean gdm  110488 2009-01-10 10:17 hpijs-ljmono.o
-rw-r--r--  1 jean gdm   83792 2009-01-10 10:17 hpijs-ljzjsmono.o
-rw-r--r--  1 jean gdm  107608 2009-01-10 10:17 hpijs-ljzjs.o
-rw-r--r--  1 jean gdm    2024 2009-01-10 10:17 hpijs-models.o
-rw-r--r--  1 jean gdm    9608 2009-01-10 10:17 hpijs-phobos_cmaps.o
-rw-r--r--  1 jean gdm   41176 2009-01-10 10:17 hpijs-pmselect.o
-rw-r--r--  1 jean gdm   31360 2009-01-10 10:17 hpijs-printerfactory.o
-rw-r--r--  1 jean gdm  120496 2009-01-10 10:17 hpijs-printer.o
-rw-r--r--  1 jean gdm   24704 2009-01-10 10:17 hpijs-printerproxy.o
-rw-r--r--  1 jean gdm   83240 2009-01-10 10:17 hpijs-psp100.o
-rw-r--r--  1 jean gdm  132320 2009-01-10 10:17 hpijs-quickconnect.o
-rw-r--r--  1 jean gdm  408920 2009-01-10 10:17 hpijs-registry.o
-rw-r--r--  1 jean gdm   32904 2009-01-10 10:17 hpijs-scaler.o
-rw-r--r--  1 jean gdm   37984 2009-01-10 10:17 hpijs-scaler_open.o
-rw-r--r--  1 jean gdm    1236 2009-01-10 10:17 hpijs-script.o
-rw-r--r--  1 jean gdm   76664 2009-01-10 10:17 hpijs-services.o
-rw-r--r--  1 jean gdm   43448 2009-01-10 10:17 hpijs-systemservices.o
-rw-r--r--  1 jean gdm   31720 2009-01-10 10:17 hpijs-translator.o
-rw-r--r--  1 jean gdm   18144 2009-01-10 10:17 hpijs-versioncode.o
-rw-r--r--  1 jean gdm    2432 2009-01-10 10:17 hpijs-version.o
-rw-r--r--  1 jean gdm     716 2009-01-10 10:15 hplip.conf
-rw-r--r--  1 jean gdm     800 2008-12-17 16:41 hplip.conf.in
-rw-r--r--  1 jean gdm     333 2009-01-10 10:15 hplip.desktop
-rw-r--r--  1 jean gdm     336 2008-12-17 16:41 hplip.desktop.in
-rwxr-xr-x  1 jean gdm     112 2008-12-17 16:41 hplip-install
-rwxr-xr-x  1 jean gdm   19110 2009-01-10 10:17 hplipjs
-rw-r--r--  1 jean gdm   15680 2009-01-10 10:17 hplipjs.o
-rw-r--r--  1 jean gdm   14101 2009-01-10 10:15 hplip.list
-rw-r--r--  1 jean gdm   13984 2008-12-17 16:41 hplip.list.in
-rw-r--r--  1 jean gdm     296 2009-01-10 10:15 hplip-systray.desktop
-rw-r--r--  1 jean gdm     299 2008-12-17 16:41 hplip-systray.desktop.in
-rwxr-xr-x  1 jean gdm    4968 2009-01-10 10:17 hp-mkuri
-rw-r--r--  1 jean gdm   15176 2009-01-10 10:17 hp-mkuri.o
-rw-r--r--  1 jean gdm    1202 2009-01-10 10:16 hpmudext.la
-rw-r--r--  1 jean gdm     354 2009-01-10 10:16 hpmudext_la-hpmudext.lo
-rwxr-xr-x  1 jean gdm    7005 2009-01-10 10:17 hppgsz
-rw-r--r--  1 jean gdm   65136 2009-01-10 10:17 hppgsz-apollo21xx.o
-rw-r--r--  1 jean gdm   54184 2009-01-10 10:17 hppgsz-apollo2560.o
-rw-r--r--  1 jean gdm  116232 2009-01-10 10:17 hppgsz-apollo2xxx.o
-rw-r--r--  1 jean gdm   13880 2009-01-10 10:17 hppgsz-breaks_open.o
-rw-r--r--  1 jean gdm    1237 2009-01-10 10:17 hppgsz-capture.o
-rw-r--r--  1 jean gdm   28568 2009-01-10 10:17 hppgsz-colormatcher_open.o
-rw-r--r--  1 jean gdm   44552 2009-01-10 10:17 hppgsz-colormatch.o
-rw-r--r--  1 jean gdm   85872 2009-01-10 10:17 hppgsz-compression.o
-rw-r--r--  1 jean gdm  101264 2009-01-10 10:17 hppgsz-context.o
-rw-r--r--  1 jean gdm   15408 2009-01-10 10:17 hppgsz-create_so.o
-rw-r--r--  1 jean gdm   30096 2009-01-10 10:17 hppgsz-creator.o
-rw-r--r--  1 jean gdm   22424 2009-01-10 10:17 hppgsz-dj3320_cmap.o
-rw-r--r--  1 jean gdm  332872 2009-01-10 10:17 hppgsz-dj3320.o
-rw-r--r--  1 jean gdm   70064 2009-01-10 10:17 hppgsz-dj350.o
-rw-r--r--  1 jean gdm   19528 2009-01-10 10:17 hppgsz-dj3600_cmap.o
-rw-r--r--  1 jean gdm   57872 2009-01-10 10:17 hppgsz-dj3600.o
-rw-r--r--  1 jean gdm   63120 2009-01-10 10:17 hppgsz-dj4100_cmap.o
-rw-r--r--  1 jean gdm   77104 2009-01-10 10:17 hppgsz-dj540.o
-rw-r--r--  1 jean gdm    9600 2009-01-10 10:17 hppgsz-dj600_maps.o
-rw-r--r--  1 jean gdm  104376 2009-01-10 10:17 hppgsz-dj600.o
-rw-r--r--  1 jean gdm  116136 2009-01-10 10:17 hppgsz-dj630.o
-rw-r--r--  1 jean gdm    6432 2009-01-10 10:17 hppgsz-dj660_maps.o
-rw-r--r--  1 jean gdm   91944 2009-01-10 10:17 hppgsz-dj660.o
-rw-r--r--  1 jean gdm    9584 2009-01-10 10:17 hppgsz-dj690_maps.o
-rw-r--r--  1 jean gdm  105392 2009-01-10 10:17 hppgsz-dj690.o
-rw-r--r--  1 jean gdm   62736 2009-01-10 10:17 hppgsz-dj6xx.o
-rw-r--r--  1 jean gdm    6448 2009-01-10 10:17 hppgsz-dj850_maps.o
-rw-r--r--  1 jean gdm  104064 2009-01-10 10:17 hppgsz-dj850.o
-rw-r--r--  1 jean gdm   57608 2009-01-10 10:17 hppgsz-dj890.o
-rw-r--r--  1 jean gdm    9624 2009-01-10 10:17 hppgsz-dj895_maps2.o
-rw-r--r--  1 jean gdm    6416 2009-01-10 10:17 hppgsz-dj895_maps.o
-rw-r--r--  1 jean gdm   80152 2009-01-10 10:17 hppgsz-dj8x5.o
-rw-r--r--  1 jean gdm  117200 2009-01-10 10:17 hppgsz-dj8xx.o
-rw-r--r--  1 jean gdm    6488 2009-01-10 10:17 hppgsz-dj970_maps2.o
-rw-r--r--  1 jean gdm    6448 2009-01-10 10:17 hppgsz-dj970_maps3.o
-rw-r--r--  1 jean gdm   12792 2009-01-10 10:17 hppgsz-dj970_maps.o
-rw-r--r--  1 jean gdm  131608 2009-01-10 10:17 hppgsz-dj9xx.o
-rw-r--r--  1 jean gdm  200704 2009-01-10 10:17 hppgsz-dj9xxvip.o
-rw-r--r--  1 jean gdm  117736 2009-01-10 10:17 hppgsz-djgenericvip.o
-rw-r--r--  1 jean gdm    1239 2009-01-10 10:17 hppgsz-filterhpa.o
-rw-r--r--  1 jean gdm   34192 2009-01-10 10:17 hppgsz-globals.o
-rw-r--r--  1 jean gdm   54184 2009-01-10 10:17 hppgsz-halftoner.o
-rw-r--r--  1 jean gdm   51936 2009-01-10 10:17 hppgsz-halftoner_open.o
-rw-r--r--  1 jean gdm   51096 2009-01-10 10:17 hppgsz-header.o
-rw-r--r--  1 jean gdm   25160 2009-01-10 10:17 hppgsz-htmtxhi.o
-rw-r--r--  1 jean gdm   42144 2009-01-10 10:17 hppgsz-jccolor.o
-rw-r--r--  1 jean gdm   19952 2009-01-10 10:17 hppgsz-jdatadbf.o
-rw-r--r--  1 jean gdm   85816 2009-01-10 10:17 hppgsz-job.o
-rw-r--r--  1 jean gdm  135744 2009-01-10 10:17 hppgsz-ljcolor.o
-rw-r--r--  1 jean gdm  157704 2009-01-10 10:17 hppgsz-ljfastraster.o
-rw-r--r--  1 jean gdm  196200 2009-01-10 10:17 hppgsz-ljjetready.o
-rw-r--r--  1 jean gdm   84176 2009-01-10 10:17 hppgsz-ljm1005.o
-rw-r--r--  1 jean gdm  110488 2009-01-10 10:17 hppgsz-ljmono.o
-rw-r--r--  1 jean gdm   83792 2009-01-10 10:17 hppgsz-ljzjsmono.o
-rw-r--r--  1 jean gdm  107608 2009-01-10 10:17 hppgsz-ljzjs.o
-rw-r--r--  1 jean gdm    2024 2009-01-10 10:17 hppgsz-models.o
-rw-r--r--  1 jean gdm    9608 2009-01-10 10:17 hppgsz-phobos_cmaps.o
-rw-r--r--  1 jean gdm   41176 2009-01-10 10:17 hppgsz-pmselect.o
-rw-r--r--  1 jean gdm   31360 2009-01-10 10:17 hppgsz-printerfactory.o
-rw-r--r--  1 jean gdm  120496 2009-01-10 10:17 hppgsz-printer.o
-rw-r--r--  1 jean gdm   49376 2009-01-10 10:17 hppgsz-PrinterProperties.o
-rw-r--r--  1 jean gdm   24704 2009-01-10 10:17 hppgsz-printerproxy.o
-rw-r--r--  1 jean gdm   83240 2009-01-10 10:17 hppgsz-psp100.o
-rw-r--r--  1 jean gdm  132320 2009-01-10 10:17 hppgsz-quickconnect.o
-rw-r--r--  1 jean gdm  408920 2009-01-10 10:17 hppgsz-registry.o
-rw-r--r--  1 jean gdm   32904 2009-01-10 10:17 hppgsz-scaler.o
-rw-r--r--  1 jean gdm   37984 2009-01-10 10:17 hppgsz-scaler_open.o
-rw-r--r--  1 jean gdm    1236 2009-01-10 10:17 hppgsz-script.o
-rw-r--r--  1 jean gdm   43448 2009-01-10 10:17 hppgsz-systemservices.o
-rw-r--r--  1 jean gdm   31720 2009-01-10 10:17 hppgsz-translator.o
-rw-r--r--  1 jean gdm   18144 2009-01-10 10:17 hppgsz-versioncode.o
-rw-r--r--  1 jean gdm    2432 2009-01-10 10:17 hppgsz-version.o
-rwxr-xr-x  1 jean gdm   19123 2008-12-17 16:41 hpssd.py
-rwxr-xr-x  1 jean gdm    5841 2008-12-17 16:41 info.py
-rw-r--r--  1 jean gdm     799 2008-12-17 16:41 __init__.py
drwxr-xr-x  2 jean gdm    4096 2008-12-17 16:45 installer
-rwxr-xr-x  1 jean gdm    7549 2008-12-17 16:41 install.py
-rwxr-xr-x  1 jean gdm   13184 2006-11-17 09:08 install-sh
drwxr-xr-x  4 jean gdm    4096 2008-12-17 16:45 io
drwxr-xr-x  2 jean gdm    4096 2008-12-17 16:46 ip
-rw-r--r--  1 jean gdm     326 2009-01-10 10:16 ipmain.lo
-rwxr-xr-x  1 jean gdm    6851 2008-12-17 16:41 levels.py
-rw-r--r--  1 jean gdm     814 2009-01-10 10:16 libhpip.la
-rw-r--r--  1 jean gdm     868 2009-01-10 10:16 libhpmud.la
-rw-r--r--  1 jean gdm     346 2009-01-10 10:16 libhpmud_la-dot4.lo
-rw-r--r--  1 jean gdm     348 2009-01-10 10:16 libhpmud_la-hpmud.lo
-rw-r--r--  1 jean gdm     342 2009-01-10 10:16 libhpmud_la-jd.lo
-rw-r--r--  1 jean gdm     344 2009-01-10 10:16 libhpmud_la-mlc.lo
-rw-r--r--  1 jean gdm     348 2009-01-10 10:16 libhpmud_la-model.lo
-rw-r--r--  1 jean gdm     346 2009-01-10 10:16 libhpmud_la-musb.lo
-rw-r--r--  1 jean gdm     344 2009-01-10 10:16 libhpmud_la-pml.lo
-rw-r--r--  1 jean gdm     342 2009-01-10 10:16 libhpmud_la-pp.lo
drwxr-xr-x  2 jean gdm    4096 2009-01-10 10:17 .libs
-rw-r--r--  1 jean gdm    1594 2009-01-10 10:17 libsane-hpaio.la
-rw-r--r--  1 jean gdm     360 2009-01-10 10:17 libsane_hpaio_la-common.lo
-rw-r--r--  1 jean gdm     358 2009-01-10 10:16 libsane_hpaio_la-hpaio.lo
-rw-r--r--  1 jean gdm     352 2009-01-10 10:17 libsane_hpaio_la-io.lo
-rw-r--r--  1 jean gdm     362 2009-01-10 10:17 libsane_hpaio_la-marvell.lo
-rw-r--r--  1 jean gdm     360 2009-01-10 10:16 libsane_hpaio_la-mfpdtf.lo
-rw-r--r--  1 jean gdm     354 2009-01-10 10:16 libsane_hpaio_la-pml.lo
-rw-r--r--  1 jean gdm     380 2009-01-10 10:17 libsane_hpaio_la-sanei_init_debug.lo
-rw-r--r--  1 jean gdm     354 2009-01-10 10:17 libsane_hpaio_la-scl.lo
-rw-r--r--  1 jean gdm     360 2009-01-10 10:17 libsane_hpaio_la-soapht.lo
-rw-r--r--  1 jean gdm     356 2009-01-10 10:17 libsane_hpaio_la-soap.lo
-rw-r--r--  1 jean gdm     354 2009-01-10 10:17 libsane_hpaio_la-xml.lo
-rwxr-xr-x  1 jean gdm  219342 2009-01-10 10:15 libtool
-rwxr-xr-x  1 jean gdm    2602 2008-12-17 16:41 linefeedcal.py
-rw-r--r--  1 jean gdm  199251 2007-08-14 14:43 ltmain.sh
-rwxr-xr-x  1 jean gdm   11587 2008-12-17 16:41 makecopies.py
-rw-r--r--  1 jean gdm  553374 2009-01-10 10:15 Makefile
-rw-r--r--  1 jean gdm   23901 2008-12-17 16:41 Makefile.am
-rw-r--r--  1 jean gdm  626087 2008-12-17 16:45 Makefile.in
-rwxr-xr-x  1 jean gdm    5744 2008-12-17 16:41 makeuri.py
-rwxr-xr-x  1 jean gdm   11135 2006-11-17 09:08 missing
drwxr-xr-x  3 jean gdm    4096 2008-12-17 16:46 pcard
-rw-r--r--  1 jean gdm     829 2009-01-10 10:17 pcardext.la
-rw-r--r--  1 jean gdm     344 2009-01-10 10:17 pcardext_la-fat.lo
-rw-r--r--  1 jean gdm     354 2009-01-10 10:17 pcardext_la-pcardext.lo
-rwxr-xr-x  1 jean gdm   13294 2008-12-17 16:41 plugin.py
drwxr-xr-x  2 jean gdm    4096 2008-12-17 16:45 plugins
drwxr-xr-x  2 jean gdm   73728 2008-12-17 16:45 ppd
-rwxr-xr-x  1 jean gdm    2482 2008-12-17 16:41 pqdiag.py
-rwxr-xr-x  1 jean gdm    4162 2008-12-17 16:41 print.py
-rwxr-xr-x  1 jean gdm    2812 2008-12-17 16:41 printsettings.py
drwxr-xr-x  8 jean gdm    4096 2008-12-17 16:45 prnt
-rwxr-xr-x  1 jean gdm    8196 2008-12-17 16:41 probe.py
-rwxr-xr-x  1 jean gdm    4959 2009-01-10 10:17 ptest
-rw-r--r--  1 jean gdm   34456 2009-01-10 10:17 ptest.o
drwxr-xr-x  4 jean gdm    4096 2008-12-17 16:45 scan
-rw-r--r--  1 jean gdm     848 2009-01-10 10:17 scanext.la
-rw-r--r--  1 jean gdm     350 2009-01-10 10:17 scanext_la-scanext.lo
-rwxr-xr-x  1 jean gdm   49092 2008-12-17 16:41 scan.py
-rwxr-xr-x  1 jean gdm   20452 2008-12-17 16:41 sendfax.py
-rwxr-xr-x  1 jean gdm   36015 2008-12-17 16:41 setup.py
-rw-r--r--  1 jean gdm    4137 2008-12-17 16:41 systray.py
-rwxr-xr-x  1 jean gdm    5748 2008-12-17 16:41 testpage.py
-rwxr-xr-x  1 jean gdm    3289 2008-12-17 16:41 timedate.py
-rwxr-xr-x  1 jean gdm    8124 2008-12-17 16:41 toolbox.py
drwxr-xr-x  2 jean gdm    4096 2008-12-17 16:46 ui
drwxr-xr-x  2 jean gdm    4096 2008-12-17 16:46 ui4
-rwxr-xr-x  1 jean gdm   24542 2008-12-17 16:41 unload.py
-rw-r--r--  1 jean gdm      29 2008-12-17 16:45 unreleased.inc
-rw-r--r--  1 jean gdm     330 2009-01-10 10:16 xbi2gray.lo
-rw-r--r--  1 jean gdm     328 2009-01-10 10:16 xchgbpp.lo
-rw-r--r--  1 jean gdm     330 2009-01-10 10:16 xcolrspc.lo
-rw-r--r--  1 jean gdm     332 2009-01-10 10:16 xconvolve.lo
-rw-r--r--  1 jean gdm     324 2009-01-10 10:16 xcrop.lo
-rw-r--r--  1 jean gdm     332 2009-01-10 10:16 xfakemono.lo
-rw-r--r--  1 jean gdm     322 2009-01-10 10:16 xfax.lo
-rw-r--r--  1 jean gdm     326 2009-01-10 10:16 xgamma.lo
-rw-r--r--  1 jean gdm     330 2009-01-10 10:16 xgray2bi.lo
-rw-r--r--  1 jean gdm     330 2009-01-10 10:16 xgrayout.lo
-rw-r--r--  1 jean gdm     328 2009-01-10 10:16 xinvert.lo
-rw-r--r--  1 jean gdm     330 2009-01-10 10:16 xjpg_dct.lo
-rw-r--r--  1 jean gdm     330 2009-01-10 10:16 xjpg_dec.lo
-rw-r--r--  1 jean gdm     330 2009-01-10 10:16 xjpg_enc.lo
-rw-r--r--  1 jean gdm     330 2009-01-10 10:16 xjpg_fix.lo
-rw-r--r--  1 jean gdm     330 2009-01-10 10:16 xjpg_huf.lo
-rw-r--r--  1 jean gdm     328 2009-01-10 10:16 xmatrix.lo
-rw-r--r--  1 jean gdm     322 2009-01-10 10:16 xpad.lo
-rw-r--r--  1 jean gdm     322 2009-01-10 10:16 xpcx.lo
-rw-r--r--  1 jean gdm     322 2009-01-10 10:16 xpnm.lo
-rw-r--r--  1 jean gdm     328 2009-01-10 10:16 xrotate.lo
-rw-r--r--  1 jean gdm     336 2009-01-10 10:16 xsaturation.lo
-rw-r--r--  1 jean gdm     326 2009-01-10 10:16 xscale.lo
-rw-r--r--  1 jean gdm     324 2009-01-10 10:16 xskel.lo
-rw-r--r--  1 jean gdm     326 2009-01-10 10:16 xtable.lo
-rw-r--r--  1 jean gdm     326 2009-01-10 10:16 xthumb.lo
-rw-r--r--  1 jean gdm     324 2009-01-10 10:16 xtiff.lo
-rw-r--r--  1 jean gdm     330 2009-01-10 10:16 xtonemap.lo
-rw-r--r--  1 jean gdm     330 2009-01-10 10:16 xyxtract.lo
jean@ubuntu-desktop:~/Desktop/hplip-2.8.12$ 

Here's what's in /installer:

total 252
drwxr-xr-x  2 jean gdm   4096 2008-12-17 16:45 .
drwxr-xr-x 19 jean gdm  12288 2009-01-10 10:17 ..
-rw-r--r--  1 jean gdm  60431 2008-12-17 16:41 core_install.py
-rw-r--r--  1 jean gdm   5947 2008-12-17 16:41 dcheck.py
-rw-r--r--  1 jean gdm 126144 2008-12-17 16:41 distros.dat
-rw-r--r--  1 jean gdm    799 2008-12-17 16:41 __init__.py
-rwxr-xr-x  1 jean gdm  32531 2008-12-17 16:41 text_install.py
jean@ubuntu-desktop:~/Desktop/hplip-2.8.12/installer$ 

I can't see what I'm supposed to run.

---

### Post by Littlejohn on 2009-01-10
I went through the steps again, this time skipping step #6 (fix_symlink). The make worked (or at least seemed to...). Then when I ran sudo hp-setup, I got this message:

Unable to connect to HPLIP I/O (hpssd).

If I do a sudo /etc/init.d/hplip restart I get:
sudo: /etc/init.d/hplip: command not found

I've been running around in circles for weeks now.

Any help would be greatly appreciated.

---

### Post by taurus on 2009-01-10
Did you run the "sudo make install"?

---

### Post by Littlejohn on 2009-01-10
Yes, seemed ok, then I unplugged/replugged the usb.

Then I sudo hp-setup, then it tells me it can't connect to HPLIP I/O (hpssd).

Does it matter where I run hp-setup from?

---

### Post by Littlejohn on 2009-01-10
I thought I ran it, maybe not because I ran it once more and now it works!!

thanks for your help!

Now, in your opinion, do you think I could just connect the printer to my Airport Extreme?

I wouldn't want to push my luck...

---

### Post by Littlejohn on 2009-01-10
Well, printing works, but I can't get the HP software to run (HP-Setup, or toolbox).

I installed the gui from add/remove and now it says Error: No device found or unsupported device.

I don't get it.

---

### Post by sanandrikos on 2009-02-18
I got the same error today.
"python: can't open file './installer/fix_symlink.py': [Errno 2] No such file or directory"
i tried a few things but no luck, i could only see the printer but i couldnt scan nor open the hp software.
eventually i did the most simple thing i could and everything worked fine..

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

it gets automatically installed..hope that helps..

---

