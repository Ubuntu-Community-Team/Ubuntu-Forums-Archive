---
title: "EPSON WF-3520 Scanner"
date: 2014-01-22
forum: Hardware
---

### Post by longlegged-guy on 2014-01-22
I bought myself and EPSON WF-3520 for Christmas. Supposedly it works well  with Linux using the epkowa backend.
Ubuntu 13.10

I connect it using a normal USB printer cable.

$ lsusb # shows
Bus 003 Device 006: ID 04b8:0899 Seiko Epson Corp. 

After going to the Epson site and  downloading and installing
epson-inkjet-printer-escpr_1.3.1-1lsb3.2_amd64.deb 
and using the printer configuration tool, printing works.

I then download and install
iscan-data_1.26.0-1_all.deb 
iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb

For good measure I add myself to the lp, lpadmin, and scanner groups

$ scanimage -L # alternates in behavior. On odd numbered invocations I get
device `epkowa:usb:003:006' is a Epson WF-3520/3530/3540 Series flatbed scanner
On even numbered invocations it hangs until I Ctrl-C.

sane-find-scanner output is even less helpful

$ sane-find-scanner
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x8087/0x8000 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x8087/0x8008 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x174c/0x3074 at 004:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0x0821 at 003:005: Access denied (insufficient permissions)
could not open USB device 0x174c/0x2074 at 003:002: Access denied (insufficient permissions)
could not open USB device 0x045e/0x078c at 003:004: Access denied (insufficient permissions)
could not open USB device 0x093a/0x2510 at 003:003: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

Just for fun, I try it with sudo
$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

$ xsane # hangs after popping up a window saying scanning for devices

HELP!

---

### Post by Bigpat on 2014-01-26
[SIZE=3][FONT=Times New Roman]OKI have just had this issues you have. Very good that you have addedyour self to the the printer group.[/FONT][/SIZE] [FONT=Times New Roman]Openthe system stetting then select the printer icon and then remove theprinter. Then remove the [/FONT][FONT=Times New Roman]driversbelow.[/FONT]
[FONT=Times New Roman]
Epson-inkjet-printer-escpr_1.3.1-1lsb3.2_amd64.deb[/FONT]


[FONT=Times New Roman, serif][SIZE=3]iscan-data_1.26.0-1_all.deband finally [/SIZE][/FONT]


[FONT=Times New Roman, serif][SIZE=3]iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb.[/SIZE][/FONT]


[FONT=Times New Roman, serif][SIZE=3]Oncethe above has been completed.  [/SIZE][/FONT]


[FONT=Times New Roman, serif][SIZE=3]Thenyou start over f[/SIZE][/FONT][FONT=Times New Roman]romthe Epson website please see the link below grab your version if 64bit then grab 64 bit version. Use the link below[/FONT]


[[FONT=Times New Roman, serif][SIZE=3]http://download.ebz.epson.net/dsc/search/01/search/searchModule[/SIZE][/FONT]]("http://download.ebz.epson.net/dsc/search/01/search/searchModule")


[FONT=Times New Roman, serif][SIZE=3]thentype WF-3520 in the search box. You will then select the  &#8220;Latest&#8221;version .[/SIZE][/FONT]


[FONT=Times New Roman, serif][SIZE=3]ThenAccept and then download the  driver labeled: [/SIZE][/FONT]


[FONT=Times New Roman, serif][SIZE=3][COLOR=#333333]epson-inkjet-printer-201212w_1.0.0-1lsb3.2_amd64.deb[/COLOR][/SIZE][/FONT]


[FONT=Times New Roman, serif][SIZE=3][COLOR=#333333]thendownload the down the [/COLOR][COLOR=#333333]corepackage&data package[/COLOR][COLOR=#333333]for scanner [/COLOR][COLOR=#333333]fromthe same page and not the one you have downloaded.[/COLOR][/SIZE][/FONT]


[COLOR=#333333][FONT=Times New Roman, serif][SIZE=3]iscan-data_1.26.0-1_all.deb then  iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb[/SIZE][/FONT][/COLOR]


[FONT=Times New Roman, serif][SIZE=3]Hereare the install steps. [/SIZE][/FONT]


[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]1install  the GDebiPackage Installer youcan fin it in the software center. Note that you will use Gdebi toinstall all the package in this order[/SIZE][/FONT][/COLOR]


[FONT=Times New Roman, serif][SIZE=3][COLOR=#333333]1.epson-inkjet-printer-201212w_1.0.0-1lsb3.2_amd64.deb[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman, serif][SIZE=3][COLOR=#333333]2Then go back to system setting and add the printer.[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman, serif][SIZE=3][COLOR=#333333]3[/COLOR][COLOR=#333333].[/COLOR][COLOR=#333333]iscan-data_1.26.0-1_all.deb[/COLOR][/SIZE][/FONT]
[COLOR=#333333][FONT=Times New Roman, serif][SIZE=3]4.iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Times New Roman, serif][SIZE=3]
Pleasemake sure you right click on each package and install with gdebi. [/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Times New Roman, serif][SIZE=3]Afterthe last last package is install image scan should show up in yourgraphics section of you applications.
It took me 4 hours to get my scanner detected and I have the WF-2540 MODEL GOOD LUCK.[/SIZE][/FONT][/COLOR]

---

### Post by longlegged-guy on 2014-12-22
Ah. Basically you are saying I should have used the 
ESC/P Driver (full feature) driver with 2012 release date
rather than the newer ESC/P-R Driver  (generic driver) that I did use.

Will try it.

Thanks.

---

### Post by longlegged-guy on 2014-12-22
I still have problems. I was able to scan one page from the flatbed, but I got an I/O error when I tried to use the ADF and
I can't even seem to get it to use the flatbed now.

Mostly I just use Scan 2 Cloud and have the printer send the scan directly to my email. That works fine for most of what I do,
but I still wish everything worked right.

---

### Post by sammiev on 2014-12-22
13.10 is EOL time to move on to 14.04

---

### Post by Mike_Walsh on 2014-12-23
Unfortunately, sammiev is right.

Since 13.10 has reached end-of-life, and is no longer supported, you will, I am afraid, get repeated reminders from mods and admins IF you want to receive support and advice on the forums. EOL releases are not supported on the forums, therefore we shouldn't really encourage you to keep using it; besides which, it's just bad practice..!

Initially, your first step should really be to upgrade to 14.04.1 LTS; a clean install would be best. Equally, 12.04 LTS would work, as it is supported till 2017.

-------------------------------------------------------------------------------------------------------------------------

As to your scanner issues, go to the following page:-

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=33473&DSCCHK=358a41ac4f7191b7847c24f698a73a3ecc33dc12](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=33473&DSCCHK=358a41ac4f7191b7847c24f698a73a3ecc33dc12)

Scroll to the bottom, and click on 'Accept'.

The two packages you will want are as follows:-
[FONT=Tahoma]
[SIZE=2]iscan-data_1.33.0-1_all.deb. This MUST be installed first, as the scanner package requires data in THIS one in order to be able to install correctly.
[/SIZE]
[SIZE=2]Then, depending on whether you want 32-bit (i386) or 64-bit (amd64), install the appropriate version of iscan-2.30.0-1~usb0.1.ltdl7_(i386 OR amd64).deb
[/SIZE]
[SIZE=2]Both of these will install through the Software Centre. If you wish, you can install them with either Synaptic package manager, or the gDebi installer (this one works better for 'standalone' installs.)
[/SIZE][SIZE=2]
[/SIZE][SIZE=2]Once these are installed, look in the Dash for 'Image Scan for Linux!' This is your Epson Scanner utility. You will find, when you first try to use it, that you will receive a message something along the lines of 'Scanner not detected', or something similar. Don't panic! Exit the scanner program; switch the printer/scanner off, THEN turn it back on, and open the scanner program again. All things being equal, it SHOULD now work.
[/SIZE]
[SIZE=2]Hope this all helps.
[/SIZE]

[SIZE=2]
Regards,[/SIZE][/FONT][COLOR=#333333][FONT=Tahoma][SIZE=2]
[/SIZE]
[/FONT][/COLOR]Mike. ;)[COLOR=#333333][FONT=Tahoma]

[/FONT][/COLOR]

---

