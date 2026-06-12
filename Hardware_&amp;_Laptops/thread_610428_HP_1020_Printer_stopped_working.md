---
title: "HP 1020 Printer stopped working"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by chrono13 on 2007-11-12
I have a month or so old fresh install of 7.10
I have an HP 1020 laser printer that worked great out of the box.

A couple of days ago, I went to change it to the default (as it was defaulting to printing to PostScript).

I changed this in Sys/Pref/Default Printer. One app did not seem to recognize this change, so I also changed it in Sys/Admin/Printing. While I was there, I also changed that users can cancel each others jobs, though I don't have a second user on this system yet.

As far as I can remember, and as far as I can tell, no other changes were made. Printing no longer works. Restarted, still not working.

In an effort to fix it, I've likely made things worse. I've removed the printer, added it, removed cups, and reinstalled it. Changed USB ports, installed gnome-cups-manager and added the printer through it, and it still will not work.

/var/log/cups/error_log

```

E [11/Nov/2007:19:59:57 -0800] CUPS-Delete-Printer: Unauthorized
E [11/Nov/2007:20:00:00 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:00:28 -0800] Pause-Printer: Unauthorized
E [11/Nov/2007:20:07:02 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [11/Nov/2007:20:07:13 -0800] [Job 21] No %%BoundingBox: comment in header!
E [11/Nov/2007:20:10:27 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:10:30 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:10:32 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [11/Nov/2007:20:11:18 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:15:45 -0800] CUPS-Delete-Printer: Unauthorized
E [11/Nov/2007:20:17:17 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:17:58 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:18:00 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:18:05 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [11/Nov/2007:20:18:07 -0800] [Job 24] No %%BoundingBox: comment in header!
E [11/Nov/2007:20:23:05 -0800] cupsdAuthorize: Local authentication certificate not found!
E [11/Nov/2007:20:23:05 -0800] cupsdAuthorize: Local authentication certificate not found!
E [11/Nov/2007:20:23:05 -0800] cupsdAuthorize: Local authentication certificate not found!
E [11/Nov/2007:20:23:05 -0800] cupsdAuthorize: Local authentication certificate not found!
E [11/Nov/2007:20:23:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [11/Nov/2007:20:23:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [11/Nov/2007:20:23:06 -0800] cupsdAuthorize: Local authentication certificate not found!
E [11/Nov/2007:20:23:10 -0800] cupsdAuthorize: Local authentication certificate not found!
E [11/Nov/2007:20:23:10 -0800] Pause-Printer: Unauthorized
E [11/Nov/2007:20:25:29 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:25:35 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:25:40 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [11/Nov/2007:20:26:15 -0800] [Job 27] No %%BoundingBox: comment in header!
E [11/Nov/2007:20:30:12 -0800] Pause-Printer: Unauthorized
E [11/Nov/2007:20:30:21 -0800] Pause-Printer: Unauthorized
E [11/Nov/2007:20:30:26 -0800] Resume-Printer: Unauthorized
E [11/Nov/2007:20:30:46 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [11/Nov/2007:20:30:46 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [11/Nov/2007:20:31:20 -0800] CUPS-Delete-Printer: Unauthorized
E [11/Nov/2007:20:34:06 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:34:10 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:34:26 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [11/Nov/2007:20:37:58 -0800] CUPS-Delete-Printer: Unauthorized
E [11/Nov/2007:20:38:07 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:38:15 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [11/Nov/2007:20:38:22 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:20:38:26 -0800] [Job 32] No %%BoundingBox: comment in header!
E [11/Nov/2007:20:47:12 -0800] CUPS-Delete-Printer: Unauthorized
E [11/Nov/2007:21:07:38 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:21:07:40 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:21:07:45 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [11/Nov/2007:21:10:36 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:21:10:54 -0800] CUPS-Add-Modify-Printer: Unauthorized
E [11/Nov/2007:21:11:03 -0800] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Nov/2007:21:11:07 -0800] [Job 34] No %%BoundingBox: comment in header!

```

Please help, I need to print. I'm desperate, and I'll be booting into the desktop CD to see if I can print from there as I'm in a bit of a time crunch. Regardless, I'll need to fix my printing very soon.

Thanks.

---

### Post by jmdeschamps on 2007-11-21
Same thing here. SAme log messages...
Not nice since it was so nice before.
I know it's not helping the OP, but it gives a clue to those that know (i hope) that it is not an isolated problem

---

### Post by jmdeschamps on 2007-11-22
Yeh! found this that worked for me

[http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL)

See Ubuntu Notes 2/5 down the page.

Good luck!

---

### Post by chrono13 on 2007-11-23
> **jmdeschamps said:**
> Yeh! found this that worked for me

[http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL)

See Ubuntu Notes 2/5 down the page.

Good luck!

This worked! Thank you!

To anyone else who may encounter this, with the same error messages in the log, this worked for me:

```

sudo apt-get install build-essential
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
tar zxf foo2zjs.tar.gz
cd foo2zjs
sudo make uninstall
make
./getweb 1020
sudo make install install-hotplug cups
sudo gnome-cups-manager
# I graphically deleted my printer here, and added it again.
sudo make cups

```

Note that the link includes more details (under "Ubuntu Notes"), and some information on how to make this work for different printers other than the 1020.

Thanks again jmdeschamps! :biggrin:

---

