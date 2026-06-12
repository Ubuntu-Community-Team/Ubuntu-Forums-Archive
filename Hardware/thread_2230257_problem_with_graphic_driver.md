---
title: "problem with graphic driver"
date: 2014-06-18
forum: Hardware
---

### Post by anonymous9 on 2014-06-18
I have acer ferrary one with radeon hd3200 m. When I start instaling driver i have this error :Check if system has the tools required for installation.fglrx installation requires that the system have kernel headers.  /lib/modules/3.13.0-29-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

 Thanks.

---

### Post by ajgreeny on 2014-06-18
I think that graphic card will use only the open source driver that you had when you installed Ubuntu.

The proprietary version, fglrx, supports the 5000 series and newer, if I remember correctly.

---

### Post by anonymous9 on 2014-06-18
I've downloaded it from amd :

[h=1]AMD Catalyst&#8482; Display Driver[/h][COLOR=#000000][FONT=Calibri][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]The drivers above support English only.
The display driver requires POSIX shared memory to be enabled on the system.
Kernal Sources package is no longer required if Kernel Header package is installed.
32-Bit packages must be installed for 64-Bit Linux drivers to install or work.[/FONT]
[FONT=inherit]*These sites are community resources, and are not supported by, or affiliated with AMD in any way[/FONT]
[/FONT]
[/FONT]
[FONT=inherit][/FONT]
[FONT=inherit][/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][TABLE="width: 571"]
[TR]
[TH="class: table-heading"]NAME[/TH]
[TH="class: table-heading"]FILE SIZE[/TH]
[TH="class: table-heading"]REVISION NUMBER[/TH]
[TH="class: table-heading"]RELEASE DATE[/TH]
[TH="class: table-heading"]DOWNLOAD LINK[/TH]
[/TR]
[TR]
[TD="class: table-row"][AMD Catalyst&#8482; 13.1 Proprietary Linux x86 Display Driver]("http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip")[/TD]
[TD="class: table-row"]102 MB[/TD]
[TD="class: table-row"]13.1[/TD]
[TD="class: table-row"]1/21/2013[/TD]
[TD="class: table-row"][Download]("http://www2.ati.com/drivers/legacy/amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64.zip")[/TD]
[/TR]
[TR]
[TD="class: table-row-full, colspan: 5"]**Description:**
[FONT=inherit]Automated installer and Display Drivers for Xorg 6.9 to Xserver 1.12 and Kernel version up to 3.4[/FONT]
[/TD]
[/TR]
[/TABLE]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by Mark Phelps on 2014-06-18
As you can see in the AMD Catalyst info, it supports the XServer up to v1.12 -- and THAT is the problem.  Newer Ubuntu versions use a newer XServer than that, which is incompatible with the AMD Catalyst drivers.  IF you force the installation of these drivers, you will only corrupt your display, have to remove them (which will be hard, with no display), and reinstall the default Radeon drivers.

Sorry, the there is no Catalyst driver that works with your card and recent Ubuntu versions.

---

