---
title: "Unknown error while updating Kubuntu 9.04/KDE 4.3"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by peterson2k4 on 2009-08-27
a dialog box pops up and I get the following;

[INDENT]Unknown error, please report a bug.
More information is available in the detailed report.
[/INDENT]


The report goes as follows;



[INDENT]kubuntu-docs Preconfiguring packages ... Preconfiguring packages ... Preconfiguring packages ... (Reading database ... 188390 files and directories currently installed.) Preparing to replace tzdata 2009j-0ubuntu0.9.04 (using .../tzdata_2009l-0ubuntu0.9.04_all.deb) ... Unpacking replacement tzdata ... Setting up tzdata (2009l-0ubuntu0.9.04) ... Current default timezone: 'America/Chicago' Local time is now: Thu Aug 27 01:43:24 CDT 2009. Universal Time is now: Thu Aug 27 06:43:24 UTC 2009. Run 'dpkg-reconfigure tzdata' if you wish to change it. (Reading database ... 188390 files and directories currently installed.) Preparing to replace libmjpegtools-1.9 1:1.9.0-0.0 (using .../libmjpegtools-1.9_1-0x1.5032c087b129p-21.9.0-0.0ubuntu3_i386.deb) ... Unpacking replacement libmjpegtools-1.9 ... Preparing to replace mono-runtime 2.0.1-4 (using .../mono-runtime_2.0.1-4ubuntu0.1_i386.deb) ... Unpacking replacement mono-runtime ... Preparing to replace mono-2.0-runtime 2.0.1-4 (using .../mono-2.0-runtime_2.0.1-4ubuntu0.1_i386.deb) ... Unpacking replacement mono-2.0-runtime ... Preparing to replace mono-jit 2.0.1-4 (using .../mono-jit_2.0.1-4ubuntu0.1_i386.deb) ... Unpacking replacement mono-jit ... Preparing to replace mono-common 2.0.1-4 (using .../mono-common_2.0.1-4ubuntu0.1_i386.deb) ... Unpacking replacement mono-common ... Preparing to replace libmono0 2.0.1-4 (using .../libmono0_2.0.1-4ubuntu0.1_i386.deb) ... Unpacking replacement libmono0 ... Preparing to replace libmono-system2.0-cil 2.0.1-4 (using .../libmono-system2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-system2.0-cil ... Preparing to replace libmono-security2.0-cil 2.0.1-4 (using .../libmono-security2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-security2.0-cil ... Preparing to replace mono-gac 2.0.1-4 (using .../mono-gac_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement mono-gac ... Preparing to replace mono-2.0-gac 2.0.1-4 (using .../mono-2.0-gac_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement mono-2.0-gac ... Preparing to replace libmono-corlib2.0-cil 2.0.1-4 (using .../libmono-corlib2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-corlib2.0-cil ... Preparing to replace libmono-cairo2.0-cil 2.0.1-4 (using .../libmono-cairo2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-cairo2.0-cil ... Preparing to replace libmono-data-tds2.0-cil 2.0.1-4 (using .../libmono-data-tds2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-data-tds2.0-cil ... Preparing to replace libmono2.0-cil 2.0.1-4 (using .../libmono2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono2.0-cil ... Preparing to replace libmono-posix2.0-cil 2.0.1-4 (using .../libmono-posix2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-posix2.0-cil ... Preparing to replace libmono-sharpzip2.84-cil 2.0.1-4 (using .../libmono-sharpzip2.84-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-sharpzip2.84-cil ... Preparing to replace libmono-system-data2.0-cil 2.0.1-4 (using .../libmono-system-data2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-system-data2.0-cil ... Preparing to replace libmono-sqlite2.0-cil 2.0.1-4 (using .../libmono-sqlite2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-sqlite2.0-cil ... Preparing to replace libmono-system-web2.0-cil 2.0.1-4 (using .../libmono-system-web2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-system-web2.0-cil ... Preparing to replace libmono-getoptions2.0-cil 2.0.1-4 (using .../libmono-getoptions2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-getoptions2.0-cil ... Preparing to replace libmono-data2.0-cil 2.0.1-4 (using .../libmono-data2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-data2.0-cil ... Preparing to replace libmono-i18n2.0-cil 2.0.1-4 (using .../libmono-i18n2.0-cil_2.0.1-4ubuntu0.1_all.deb) ... Unpacking replacement libmono-i18n2.0-cil ... Processing triggers for man-db ... Setting up kubuntu-docs (9.04.2) ... [/INDENT]


Anyone know what's up with that nonsense?

---

### Post by inobe on 2009-08-27
it looks like you got some updates from the server.

have you restarted while the updates were installing, also did you attempt to stop the updates in any way ?


did you try opening kpackagekit to see if you could continue the updates installation ?

---

### Post by peterson2k4 on 2009-08-28
Yea, I can get the updates ok but,  when it is loading cache and it reaching 98% it gives me the error.  It happens if I am looking for updates or trying to install updates.  It happens in KpackageKit.  While typing this I was changing around some sources to see if that would fix it (I don't really know what I am doing) and it is stuck on 99% trying to download additional packages.  It is stuck on 97/100.

Did I close out during some updates loading?  I think I did a few weeks back.  but I have not been able to update my pc for awhile.

don't know if this helps but, I was having this problem with both my Gnome and KDE session.

---

### Post by oboedad55 on 2009-08-28
> **peterson2k4 said:**
> Yea, I can get the updates ok but,  when it is loading cache and it reaching 98% it gives me the error.  It happens if I am looking for updates or trying to install updates.  It happens in KpackageKit.  While typing this I was changing around some sources to see if that would fix it (I don't really know what I am doing) and it is stuck on 99% trying to download additional packages.  It is stuck on 97/100.

Did I close out during some updates loading?  I think I did a few weeks back.  but I have not been able to update my pc for awhile.

don't know if this helps but, I was having this problem with both my Gnome and KDE session.

Running out of disk space?

---

### Post by peterson2k4 on 2009-08-29
nope disk is good.

---

