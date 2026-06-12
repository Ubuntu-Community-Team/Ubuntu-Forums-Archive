---
title: "Cannot connect wireless canon mp620"
date: 2009-11-11
forum: Hardware
---

### Post by slambrick on 2009-11-11
I have been desperatley trying to set up my Acer laptop (Karmic) for wireless printing but cannot get it to work at all. Can anyone help?

---

### Post by BigBananaMan on 2010-01-25
I've been working on the same thing with my MP620 on Ubuntu 9.10 AMD64 and have not gotten anywhere.  Do you mean how to configure it to the wifi network without using their useless proprietary software?  Next time make sure to provide more info on what exactly your problem is and system specs, help others help you.

If you can't get it connected wirelessly, Canon told me it is impossible... so 20 minutes later I solved it myself with the help of nmap.  Just connect your printer to the router with a patch cable and note what IP it is at.  Punch [http://[ip](http://[ip) address here] into your browser.  From there you can easily enter your router info so that you can then connect it wirelessly. 

Once you do that, your printer is still going to be useless but at least you can mess with it.  If you're on 32 bit architecture you can use [this guide]("http://www.michael-krueger.org/2009/01/how-to-use-canon-pixma-mp620-with.html") but if you're on 64, you'll have to wait for the community to find a solution.

[Here is one thread trying to solve it]("http://ubuntuforums.org/showthread.php?t=1323409") but there are many more.

---

### Post by Kyle138 on 2010-01-27
Thanks BigBananaMan, (dude that's weird to say/type/whatever) ;)

You're tip for setting the IP and the guide from Michael-Krueger's blogspot that you posted worked great. I'm printing and scanning now. Now to go repeat these actions on three more computers :P

---

### Post by ubuking on 2010-05-01
I have (finally) managed to install my Canon MP620 over WLAN using Ubuntu 10.04 Lucid Lynx AMD 64-Bit version. The trick was to combine several tutorials (Luca Gibelli, Holger Metzger, Leon Atkinson) and put things in the right order. Thanks Guys! At least it now works for me!

The Canon drivers are built for a 32-bit architecture, so we have to do some additional actions to make it work. 

First open up a terminal and install the ia32-libs as the drivers would require these:
sudo apt-get install ia32-libs
The Canon drivers are looking for libcupsys2, so download a transitional dummy package from Jaunty and install it.
[http://packages.ubuntu.com/jaunty/all/libcupsys2/download]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download")

Then download the drivers from Canon Support Australia website:

[IJ Printer Driver Ver. 2.80 for Linux(debian Common package)]("http://support-au.canon.com.au/contents/AU/EN/0100083403.html")

[URL="http://support-au.canon.com.au/contents/AU/EN/0100084001.html"]IJ Printer Driver Ver. 2.80 for Linux(debian Package for the MP610 series)
[/URL]
In the terminal, go to the directory where you have saved the files and install the drivers using the commands
sudo dpkg -i --force-architecture –force-all cnijfilter-common_2.80-1_i386.deb
sudo dpkg -i --force-architecture –force-all cnijfilter-mp610series_2.80-1_i386.deb
The next step is to install the CUPS 64-bit drivers from Sourceforge; as there are no Debs you have to install alien for conversion
sudo apt-get install alien

Here are the links to the drivers: 
cups-bjnp 0.5.4 file released: [cups-bjnp-0.5.4-1.fc10.x86_64.rpm]("http://sourceforge.net/projects/cups-bjnp/files/cups-bjnp/cups-bjnp-0.5.4-1.fc10.x86_64.rpm/") 
[cups-bjnp 0.5.4 file released: cups-bjnp-debuginfo-0.5.4-1.fc10.x86_64.rpm ]("http://sourceforge.net/projects/cups-bjnp/files/cups-bjnp/cups-bjnp-debuginfo-0.5.4-1.fc10.x86_64.rpm/")
You can install them using the commands:
sudo alien -i cups-bjnp-0.5.4-1.fc10.x86_64.rpm
sudo alien -i cups-bjnp-debuginfo-0.5.4-1.fc10.x86_64.rpm 

Download the ppd files from Sourceforge and copy the ppd and conf file to the proper location:
[ppdMP620-630en-1.5.tar.gz]("http://sourceforge.net/projects/mp610linux/files/MP620%20and%20MP630%20enhanced%20PPDs/ppdMP620-630en-1.5.tar.gz")

sudo cp canonmp620-630en.ppd /usr/share/ppd/
sudo cp cifmp610.conf /usr/lib/bjlib/

Now restart CUPS:
sudo /etc/init.d/cups restart

Turn on the printer and check that you can ping it from your PC.
Open CUPS web interface in your browser: [http://localhost:631]("http://localhost:631")
Choose “Add Printer” and wait for some 30 seconds. 
On the following page you will be able to choose the “Device”. Pull down the list of Discovered Network Printers and select the following entry:
Canon MP620 series <ip address> (Canon MP620 series)
Select and press Continue, fill in the admin and move to the next page.
Select Canon MP620-630 series Ver.2.80en (en) and press Add Printer

This should do the trick.

From this point Scanning works pretty much out-of-the box, provided that you first install XSANE. I have used Synaptic to do so.

---

### Post by tgraczyk on 2010-05-07
Thank you so much for this post.  I'll admit, it's been a long day and it took me a couple minutes to realize I needed to save the i386 files, then get to that directory in terminal before running the force architecture, but it worked.  For the first time, I'm printing wirelessly in Ubuntu.  I've always been happy Ubuntu, but now I love it.  Thank you again.  This worked, just like you said it would.

---

### Post by skyh on 2010-05-13
ubuking, thanks for the steps... unfortunately, I get to be one of those people that printer detection just simply won't work for.

No matter what I seem to do, looking for my MP620 just doesn't work -- cups can't find it. And I followed your instructions *to the letter*, so I really don't know what the problem is.

Now, keep in mind, I can print by manually setting up the printer. That works fine.. but without being able to detect it, I can't scan.

I feel like there should be some way to manually set a network scanner in xsane, but I can't seem to find a way to do it..

Any suggestions?

---

### Post by Kyle138 on 2010-05-13
I had that problem, could print but couldn't scan. Mine turned out to be because I had them on two different networks. Canon was on the wireless network so all my laptops scanned and printed, but desktop on the wired network could only print, not scan. Apparently the printing packets can cross the router but not the scanning packets. I don't know if this is the same issue you're having but it's something to try.

---

### Post by rennaps on 2010-05-30
> **ubuking said:**
> I have (finally) managed to install my Canon MP620 over WLAN using Ubuntu 10.04 Lucid Lynx AMD 64-Bit version. The trick was to combine several tutorials (Luca Gibelli, Holger Metzger, Leon Atkinson) and put things in the right order. Thanks Guys! At least it now works for me!


ubuking, thank you for combining tutorials for this byzantine method in a comprehensible way, it worked perfectly for me.

---

### Post by e4uforums on 2010-06-08
**THANK YOU UBUKING!**  Using your tutorial to install the printer was as easy as using the provided drivers in Windows.  The first time I installed these it took me the better part of 90 minutes (unfortunately I didn't take notes).  The second time it took me maybe 10 minutes using your instructions.  Thank you again!  

To get it to work on mine, I had to make two small adjustments to the instructions, maybe this will help someone else...

Original:
```
sudo dpkg -i --force-architecture –force-all cnijfilter-common_2.80-1_i386.deb
sudo dpkg -i --force-architecture –force-all cnijfilter-mp610series_2.80-1_i386.deb
```

Modified:
```
sudo dpkg -i --force-architecture cnijfilter-common_2.80-1_i386.deb
sudo dpkg -i --force-architecture cnijfilter-mp610series_2.80-1_i386.deb
```

---

### Post by tgraczyk on 2010-07-20
I'm back and I need help.  I moved from Wubi to a dedicated partition and need to set up the printer, again.  I followed everything as I did before, including using the modified code posted by e4uforums, but I still can't see the printer.  The main thing I noticed this time is that the very first step, ia32-libs, gives the error message 

laptop:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs

I've tried a work around for this and still can't get anything to work.  Does anyone have any ideas?  Please help.  Thank you.

                 Workaround:
 cd /tmp
wget [http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/i/ia32-libs/ia32-libs_2.7ubuntu6.1_amd64.deb)
dpkg-deb -x ia32-libs_2.7ubuntu6.1_amd64.deb ia32-libs
sudo cp ia32-libs/usr/lib32/libstdc++.so.5.0.7  /usr/lib32/
cd /usr/lib32
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

***This is corrected, please see the next post

---

### Post by tgraczyk on 2010-07-21
I figured it out.  Apparently I have more than one image disk of Ubuntu because I have three different architectures in the house.  I installed the wrong type onto this computer.  I cleaned everything off, made sure the computer was booting only to Vista and then reloaded Ubuntu using the correct disk.  After that, everything worked just as it did before.  Thank you anyway!!  Ubuking, you are an Angel!!

---

### Post by oldtraveler on 2010-08-06
> **ubuking said:**
> 
First open up a terminal and install the ia32-libs as the drivers would require these:
sudo apt-get install ia32-libs
The Canon drivers are looking for libcupsys2, so download a transitional dummy package from Jaunty and install it.
[http://packages.ubuntu.com/jaunty/al...psys2/download](http://packages.ubuntu.com/jaunty/al...psys2/download)

Then download the drivers from Canon Support Australia website:

[IJ Printer Driver Ver. 2.80 for Linux(debian Common package)]("http://support-au.canon.com.au/contents/AU/EN/0100083403.html")

[URL="http://support-au.canon.com.au/contents/AU/EN/0100084001.html"]IJ Printer Driver Ver. 2.80 for Linux(debian Package for the MP610 series)
[/URL]


The terminal indicates some errors.  Here is a copy:

phil@ubuntu10:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  odbcinst1debian1 linux-headers-2.6.32-21-generic odbcinst unixodbc
  linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.7.0-1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: numeric hostname: 04
newaliases: fatal: file /etc/postfix/main.cf: parameter mydomain: bad parameter value: 04
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
 bsd-mailx
E: Sub-process /usr/bin/dpkg returned an error code (1)
phil@ubuntu10:~$ 

=========================


Downloading each of these drivers gives an error 
"Error:Wrong architcture 'i386' 
 Now what?

---

### Post by Ekaitz on 2010-08-30
Hello,

Thank you, ubuking for your post!
But I have a problem, my MP620 is detected, but the printer don't print :/

This is the troobleshot.txt (Debug tool for printer):

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Canon_MP620>,
 'cups_instance': None,
 'cups_queue': 'Canon_MP620',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'bjnp',
 'cups_printer_dict': {'device-uri': u'bjnp://192.168.1.16:8611',
                       'printer-info': u'Canon MP620',
                       'printer-is-shared': False,
                       'printer-location': u'Chambre de Tiphaine',
                       'printer-make-and-model': u'Canon MP620-630 series Ver.2.80fr',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'cups-insecure-filter-warning'],
                       'printer-type': 10522652,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Canon_MP620'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.3',
                                 'device-uri': u'bjnp://192.168.1.16:8611',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'fr_FR'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'media-default': u'iso_a4_210x297mm',
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'na_legal_8.5x14in',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a4_210x297mm',
                                                     u'iso_a4_210x297mm',
                                                     u'jis_b5_182x257mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'adobe_4X6.bl_104.422x156.633mm',
                                                     u'adobe_4X8_4x8in',
                                                     u'adobe_4X8.bl_104.422x208.844mm',
                                                     u'na_5x7_5x7in',
                                                     u'adobe_5X7.bl_132.644x182.386mm',
                                                     u'na_govt-letter_8x10in',
                                                     u'adobe_8X10.bl_206.022x257.528mm',
                                                     u'adobe_l_3.5x5in',
                                                     u'na_5x7_5x7in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'adobe_postdbl_7.875x5.83333in',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_dl_110x220mm',
                                                     u'jpn_you4_105x235mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'adobe_creditcard_2.125x3.38889in',
                                                     u'adobe_businesscard_55.0333x91.0167mm',
                                                     u'adobe_wide_4x7.11111in',
                                                     u'custom_min_54.0032x86.0002mm',
                                                     u'custom_max_8.5x23in'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'fr_FR',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'Canon MP620',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': False,
                                 'printer-location': u'Chambre de Tiphaine',
                                 'printer-make-and-model': u'Canon MP620-630 series Ver.2.80fr',
                                 'printer-more-info': u'http://localhost:631/printers/Canon_MP620',
                                 'printer-name': u'Canon_MP620',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1283189087,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'cups-insecure-filter-warning'],
                                 'printer-type': 10522652,
                                 'printer-up-time': 1283190677,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Canon_MP620'],
                                 'queued-job-count': 1,
                                 'server-is-sharing-printers': False,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided',
                                                     u'two-sided-long-edge',
                                                     u'two-sided-short-edge'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Couleurs & intensit?': {u'CNBalanceC': u'0',
                                                         u'CNBalanceM': u'0',
                                                         u'CNBalanceY': u'0',
                                                         u'CNContrast': u'0',
                                                         u'CNDensity': u'0',
                                                         u'CNGamma': u'1.8',
                                                         u'CNRenderIntent': u'photo'},
                               u'General': {u'Duplex': u'None',
                                            u'InputSlot': u'cassette',
                                            u'MediaType': u'plain',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Resolution': u'600'},
                               u"Rendu de l'impression": {u'CNGrayscale': u'False',
                                                          u'CNHalftoning': u'ed',
                                                          u'CNQuality': u'3'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'network',
                      'device-id': u'MFG:Canon;CMD:BJL,BJRaster3,BSCCe,NCCe,PLI;SOJ:TXT01,BJNP2;MDL:MP620 series;CLS:PRINTER;DES:Canon MP620 series;VER:1.100;STA:10;HRI:EU;MSI:DAT,E3,HFSF;PDR:4;',
                      'device-info': u'Canon MP620 series 192.168.1.16',
                      'device-location': u'',
                      'device-make-and-model': u'Canon MP620 series'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'',
 'printer-state-reasons': [u'cups-insecure-filter-warning']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 4808,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_attempted': '30/ao\xc3\xbbt/2010:19:52:17 +0000',
 'test_page_job_id': [4],
 'test_page_job_status': [(True,
                           4,
                           'Canon_MP620',
                           'Test Page',
                           'Arr\xc3\xaat\xc3\xa9',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'fr-fr',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 4,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/4',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'adrien',
                            'job-preserved': True,
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'cups-insecure-filter-warning'],
                            'job-printer-up-time': 1283190746,
                            'job-printer-uri': u'ipp://Adrien-VAIO:0/printers/Canon_MP620',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/4',
                            'job-uuid': u'urn:uuid:85737c0c-411d-3ad5-5b39-e4930c3cc7bf',
                            'printer-uri': u'ipp://localhost/printers/Canon_MP620',
                            'time-at-completed': None,
                            'time-at-creation': 1283190737,
                            'time-at-processing': 1283190737})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [30/Aug/2010:19:52:11 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:11 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:11 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:11 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:11 +0200] cupsdReadClient: 11 1.1 Get-Jobs 1',
               'D [30/Aug/2010:19:52:11 +0200] Get-Jobs ipp://localhost/printers/',
               'D [30/Aug/2010:19:52:11 +0200] [Job 3] Loading attributes...',
               'D [30/Aug/2010:19:52:11 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [30/Aug/2010:19:52:11 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:11 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:11 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:11 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:11 +0200] cupsdReadClient: 11 1.1 Get-Jobs 1',
               'D [30/Aug/2010:19:52:11 +0200] Get-Jobs ipp://localhost/printers/',
               'D [30/Aug/2010:19:52:11 +0200] [Job 1] Loading attributes...',
               'D [30/Aug/2010:19:52:11 +0200] [Job 2] Loading attributes...',
               'D [30/Aug/2010:19:52:11 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [30/Aug/2010:19:52:11 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:11 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:11 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:11 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:11 +0200] cupsdReadClient: 11 1.1 Create-Printer-Subscription 1',
               'D [30/Aug/2010:19:52:11 +0200] Create-Printer-Subscription /',
               'D [30/Aug/2010:19:52:11 +0200] cupsdCreateSubscription(con=0x7fa1134fc030(11), uri="/")',
               'D [30/Aug/2010:19:52:11 +0200] pullmethod="ippget"',
               'D [30/Aug/2010:19:52:11 +0200] notify-lease-duration=86400',
               'D [30/Aug/2010:19:52:11 +0200] notify-time-interval=0',
               'D [30/Aug/2010:19:52:11 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [30/Aug/2010:19:52:11 +0200] Added subscription 2 for server',
               'D [30/Aug/2010:19:52:11 +0200] cupsdMarkDirty(-----S)',
               'D [30/Aug/2010:19:52:11 +0200] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [30/Aug/2010:19:52:11 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:12 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:12 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:12 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:12 +0200] cupsdReadClient: 11 1.1 Get-Notifications 1',
               'D [30/Aug/2010:19:52:12 +0200] Get-Notifications /',
               'D [30/Aug/2010:19:52:12 +0200] cupsdIsAuthorized: requesting-user-name="adrien"',
               'D [30/Aug/2010:19:52:12 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [30/Aug/2010:19:52:12 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 16 POST /printers/Canon_MP620 HTTP/1.1',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 16 1.1 Print-Job 1',
               'D [30/Aug/2010:19:52:17 +0200] Print-Job ipp://localhost/printers/Canon_MP620',
               'D [30/Aug/2010:19:52:17 +0200] [Job ???] Auto-typing file...',
               'I [30/Aug/2010:19:52:17 +0200] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdMarkDirty(----J-)',
               'D [30/Aug/2010:19:52:17 +0200] add_job: requesting-user-name="adrien"',
               'D [30/Aug/2010:19:52:17 +0200] Adding default job-sheets values "none,none"...',
               'I [30/Aug/2010:19:52:17 +0200] [Job 4] Adding start banner page "none".',
               'D [30/Aug/2010:19:52:17 +0200] cupsdMarkDirty(-----S)',
               'D [30/Aug/2010:19:52:17 +0200] cupsdMarkDirty(----J-)',
               'I [30/Aug/2010:19:52:17 +0200] [Job 4] Adding end banner page "none".',
               'I [30/Aug/2010:19:52:17 +0200] [Job 4] File of type application/vnd.cups-banner queued by "adrien".',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] hold_until=0',
               'I [30/Aug/2010:19:52:17 +0200] [Job 4] Queued on "Canon_MP620" by "adrien".',
               'D [30/Aug/2010:19:52:17 +0200] cupsdMarkDirty(----J-)',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdMarkDirty(-----S)',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] job-sheets=none,none',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] argv[0]="Canon_MP620"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] argv[1]="4"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] argv[2]="adrien"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] argv[3]="Test Page"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] argv[4]="1"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] argv[5]="job-uuid=urn:uuid:85737c0c-411d-3ad5-5b39-e4930c3cc7bf job-originating-host-name=localhost"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] argv[6]="/var/spool/cups/d00004-001"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[10]="SERVER_ADMIN=root@Adrien-VAIO"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[11]="SOFTWARE=CUPS/1.4.3"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[13]="TZ=Europe/Paris"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[14]="USER=root"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[17]="IPP_PORT=631"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[18]="CHARSET=utf-8"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[19]="LANG=fr_FR.UTF-8"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[20]="PPD=/etc/cups/ppd/Canon_MP620.ppd"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[21]="RIP_MAX_CACHE=1006728k"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[23]="DEVICE_URI=bjnp://192.168.1.16:8611"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[24]="PRINTER_INFO=Canon MP620"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[25]="PRINTER_LOCATION=Chambre de Tiphaine"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[26]="PRINTER=Canon_MP620"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[27]="CUPS_FILETYPE=document"',
               'D [30/Aug/2010:19:52:17 +0200] [Job 4] envp[28]="FINAL_CONTENT_TYPE=printer/Canon_MP620"',
               'I [30/Aug/2010:19:52:17 +0200] [Job 4] Started filter /usr/lib/cups/filter/bannertops (PID 19088)',
               'I [30/Aug/2010:19:52:17 +0200] [Job 4] Started filter /usr/lib/cups/filter/pstopdf (PID 19089)',
               'I [30/Aug/2010:19:52:17 +0200] [Job 4] Started filter /usr/lib/cups/filter/pdftopdf (PID 19090)',
               'I [30/Aug/2010:19:52:17 +0200] [Job 4] Started filter /usr/lib/cups/filter/cpdftocps (PID 19091)',
               'E [30/Aug/2010:19:52:17 +0200] Unable to execute /usr/lib/cups/filter/pstocanonij: insecure file permissions (0100755)',
               'E [30/Aug/2010:19:52:17 +0200] [Job 4] Unable to start filter "pstocanonij" - Operation not permitted.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdMarkDirty(-----S)',
               'E [30/Aug/2010:19:52:17 +0200] [Job 4] Stopping job because the scheduler could not execute a filter.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdMarkDirty(----J-)',
               'D [30/Aug/2010:19:52:17 +0200] cupsdMarkDirty(-----S)',
               'D [30/Aug/2010:19:52:17 +0200] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Canon_MP620) from localhost',
               'D [30/Aug/2010:19:52:17 +0200] PID 19088 (/usr/lib/cups/filter/bannertops) was terminated normally with signal 15.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:17 +0200] PID 19091 (/usr/lib/cups/filter/cpdftocps) was terminated normally with signal 15.',
               'D [30/Aug/2010:19:52:17 +0200] PID 19090 (/usr/lib/cups/filter/pdftopdf) was terminated normally with signal 15.',
               'D [30/Aug/2010:19:52:17 +0200] PID 19089 (/usr/lib/cups/filter/pstopdf) was terminated normally with signal 15.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 17 1.1 Get-Jobs 1',
               'D [30/Aug/2010:19:52:17 +0200] Get-Jobs ipp://localhost/printers/',
               'D [30/Aug/2010:19:52:17 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [30/Aug/2010:19:52:17 +0200] cupsdCloseClient: 17',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [30/Aug/2010:19:52:17 +0200] Get-Notifications /',
               'D [30/Aug/2010:19:52:17 +0200] cupsdIsAuthorized: requesting-user-name="adrien"',
               'D [30/Aug/2010:19:52:17 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 17 1.1 Get-Job-Attributes 1',
               'D [30/Aug/2010:19:52:17 +0200] Get-Job-Attributes ipp://localhost/jobs/4',
               'D [30/Aug/2010:19:52:17 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAcceptClient: 18 from localhost (Domain)',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1',
               'D [30/Aug/2010:19:52:17 +0200] Get-Printer-Attributes ipp://Adrien-VAIO:0/printers/Canon_MP620',
               'D [30/Aug/2010:19:52:17 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://Adrien-VAIO:0/printers/Canon_MP620) from localhost',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 18 1.1 Get-Job-Attributes 1',
               'D [30/Aug/2010:19:52:17 +0200] Get-Job-Attributes ipp://localhost/jobs/4',
               'D [30/Aug/2010:19:52:17 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 11 1.1 Get-Notifications 1',
               'D [30/Aug/2010:19:52:17 +0200] Get-Notifications /',
               'D [30/Aug/2010:19:52:17 +0200] cupsdIsAuthorized: requesting-user-name="adrien"',
               'D [30/Aug/2010:19:52:17 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAcceptClient: 19 from localhost (Domain)',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 18 WAITING Closing on EOF',
               'D [30/Aug/2010:19:52:17 +0200] cupsdCloseClient: 18',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1',
               'D [30/Aug/2010:19:52:17 +0200] Get-Printer-Attributes ipp://Adrien-VAIO:0/printers/Canon_MP620',
               'D [30/Aug/2010:19:52:17 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://Adrien-VAIO:0/printers/Canon_MP620) from localhost',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:17 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:17 +0200] cupsdReadClient: 19 1.1 Get-Job-Attributes 1',
               'D [30/Aug/2010:19:52:17 +0200] Get-Job-Attributes ipp://localhost/jobs/4',
               'D [30/Aug/2010:19:52:17 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost',
               'D [30/Aug/2010:19:52:17 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:18 +0200] [Job 4] Unloading...',
               'D [30/Aug/2010:19:52:26 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:26 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:26 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:26 +0200] cupsdReadClient: 11 1.1 Get-Job-Attributes 1',
               'D [30/Aug/2010:19:52:26 +0200] Get-Job-Attributes ipp://localhost/jobs/4',
               'D [30/Aug/2010:19:52:26 +0200] [Job 4] Loading attributes...',
               'D [30/Aug/2010:19:52:26 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/4) from localhost',
               'D [30/Aug/2010:19:52:26 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:26 +0200] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [30/Aug/2010:19:52:26 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:26 +0200] cupsdAuthorize: No authentication data provided.',
               'D [30/Aug/2010:19:52:26 +0200] cupsdReadClient: 11 1.1 Cancel-Subscription 1',
               'D [30/Aug/2010:19:52:26 +0200] Cancel-Subscription /',
               'D [30/Aug/2010:19:52:26 +0200] cupsdIsAuthorized: requesting-user-name="adrien"',
               'D [30/Aug/2010:19:52:26 +0200] cupsdMarkDirty(-----S)',
               'D [30/Aug/2010:19:52:26 +0200] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [30/Aug/2010:19:52:26 +0200] cupsdSetBusyState: Dirty files',
               'D [30/Aug/2010:19:52:26 +0200] cupsdAcceptClient: 18 from localhost (Domain)',
               'D [30/Aug/2010:19:52:26 +0200] cupsdReadClient: 18 GET /admin/log/error_log HTTP/1.1',
               'D [30/Aug/2010:19:52:26 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [30/Aug/2010:19:52:26 +0200] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 11 (Printer state reasons):
{'printer-state-message': u'Filter "/usr/lib/cups/filter/pstocanonij" for printer "Canon_MP620" not owned by root',
 'printer-state-reasons': [u'cups-insecure-filter-warning']}
Page 12 (Locale issues):
{'printer_page_size': u'A4',
 'system_locale_lang': None,
 'user_locale_ctype': 'fr_FR',
 'user_locale_messages': 'fr_FR'}

___

Can you help me?
Sorry for my english, I'm 13 and I'm french... :-|

---

### Post by rghv65c on 2010-09-17
Check out this site as it has detailed instructions on installing the  MP620 on Ubuntu.  This worked for me.  Even scanning and wireless too.  

To get it to work on x64 you have to force the architecture

here are the instructions. 

[http://bkintegration.com/?p=235 ]("http://bkintegration.com/?p=235")

Ubuntu 9.10 x64
Asus F8sn-B1 (laptop)

---

### Post by BigBananaMan on 2010-12-17
I'm copy/pasting this to a couple places so please excuse any redundancies.

After getting fed up wasting time re-learning and screwing up setting up multiple computers, I was going to write an install script so I never have to spend an entire day re-learning the whole process again. Kevin Carter beat me to it and did a better job than I would have anyway. These are good for new users or just somebody that has to install to multiple systems or occasional reinstall. You can find the scripts [HERE]("http://bkintegration.com/2010/08/install-canon-mp620-on-ubuntu-linux-10-04/")

To make life even easier the proper .ppd file is [HERE]("http://sourceforge.net/project/showfiles.php?group_id=210977")

If you just bought the printer and are wondering how to get it to connect wirelessly (which Canon says is impossible and then suggested I buy Windows just to set up the kickbacks err printer. hmm...) You can connect it first to your router with a patch cable and check the IP through the printer interface. Then punch [http://printer](http://printer) ip here into your browser and set it up to use your wifi.

---

### Post by marty331 on 2011-01-01
BigBananaMan you are a genius!  I know have both mine and my wife's computer hooked up to our printers!  I have us both running Ubuntu 10.10.  Thanks so much for your script!

---

