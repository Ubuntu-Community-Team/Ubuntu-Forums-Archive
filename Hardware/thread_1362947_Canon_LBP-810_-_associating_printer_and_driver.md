---
title: "Canon LBP-810 - associating printer and driver"
date: 2009-12-23
forum: Hardware
---

### Post by 2ways on 2009-12-23
Hi Folks,

Over the years there has been a bunch of traffic here and elsewhere about installing the Canon LBP-810 printer.

I am on a Sony Vaio laptop, i386, running a single boot installation of 9.10.

I have been through every script and every suggestion I can find and cannot get my printer to work.  If it's not going to work, I can accept that.

My frustration is that some people seem to get it to work (at least in a limited fashion), but, in every 'how to', one of the options I am supposed to select is not offered to me.  Partly that could be a change in operating systems, from jaunty to karmic, etc, but there is something more sinister going on, I am quite sure.

The option that is consistently missing seems to be where I associate the driver I've installed with the printer that has been found.

The driver that seems to work for people is at:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-LBP-810](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-LBP-810)

The kind of script that seems to work is at:
[http://ubuntuforums.org/showthread.php?t=81454](http://ubuntuforums.org/showthread.php?t=81454)

which is something of a rehash of this french thread:
[http://forum.ubuntu-fr.org/viewtopic.php?id=23422&p=1](http://forum.ubuntu-fr.org/viewtopic.php?id=23422&p=1)

I get no complaints from any of the command line operations, installing the driver, etc., but both posts say I should not select the 'discovered' printer, but rather the 'local printer' option, and then specify the printer in the next step as attached to the usb port.

1) selecting a local printer is not an option in Printer Configuration in Karmic as far as I can tell

2) when selecting the discovered printer (correctly recognised as Canon LBP-810), it tells me that it knows the printer is connected to the usb port.

3) contrary to the 'how to' posts, in future steps in printer Configuration, I am never offered Canon LBP-810 to select as the printer driver I want to associate with this printer.  I am offered the foomatic driver for the LBP-470 because it doesn't think it knows about a driver for the LBP-810.

How do I tell my computer to associate the installed driver with my printer?  How do I get the LBP-810 driver into the list of possible drivers?

Having gone through the configuration process accepting the recommendations, everything seems happy.  I have a printer called Canon LBP-810 installed and I can send jobs to the print queue.  It's just that nothing ever prints.

Typing lpq on the command line tells me that 'Canon LBP-810 is ready and printing' and lists the jobs I have queued up.  Nothing ever happens.

Also, before adding the printer, I tried lpinfo -v in the command line and found:

direct usb://Canon/LBP-810

While after adding the printer, that line is missing.  Is that simply because that backend is no longer available?  I was also puzzled by the double back slash, since I thought the double slash was reserved for network options and single slashes were the local options.

Is there a way I can do all of this on the command line and access more options than through the gui?

Thanks for your help.

Merry Christmas!

Lewis

---

### Post by HappyFeet on 2009-12-23
It sounds like you've pretty much tried everything. I had a Lexmark that refused to work in linux, so I went out and bought an HP. Upon plugging it in, it was immediately recognized and configured. HP is hands down the best for linux.

I can't really help you with your immediate problem, but just thought I'd throw my .02 in. Good luck and happy holidays.

Oh, one other thing you could do if you're willing, is to install windows in virtualbox to run the printer. Not elegant, but it works.

And one more thing. If your user name is your real email address, you might want to consider asking the mods to change it. It is NOT a good idea.

---

### Post by rosros-5 on 2009-12-30
With the  driver [http://www.are-ata.org/debian/capt/capt-0.4.tar.gz](http://www.are-ata.org/debian/capt/capt-0.4.tar.gz)
I installed my Canon LBP-810 (connected to a USB port), 
in Ubuntu 8.10 Intrepid, with the following configuration
[I]Device URI: serial:/dev/ttyS0?baud=115200
Make and Model: Canon LBP-810 Foomatic/capt (recommended)
[/I]The result is: [I]No printing. 

[/I]The printing troubleshooter states:[I]
The printer's state message is: '/usr/lib/cups/filter/foomatic-rip failed'
[/I][There IS a symlink /usr/lib/cups/filter/foomatic-rip to the actual file /usr/foomatic-rip]

Here is the diagnostic output:
[I]
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest LBP-810>,
 'cups_instance': None,
 'cups_queue': 'LBP-810',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'serial',
 'cups_printer_dict': {'device-uri': u'serial:/dev/ttyS0?baud=115200',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Canon LBP-810 Foomatic/capt (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 4100,
                       'printer-uri-supported': u'ipp://localhost:631/printers/LBP-810'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Adjustment': {u'LeftSkip': u'110',
                                               u'TopSkip': u'90'},
                               u'General': {u'PageRegion': u'A4',
                                            u'PageSize': u'A4'},
                               u'Miscellaneous': {u'AlwaysReset': u''}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'serial',
                      'device-id': u'',
                      'device-info': u'Serial Port #1',
                      'device-make-and-model': u'Unknown'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'AccessLog': '/var/log/cups/access_log',
                          'AutoPurgeJobs': 'No',
                          'BrowseInterval': '30',
                          'BrowsePort': '631',
                          'BrowseProtocols': 'CUPS',
                          'BrowseShortNames': 'Yes',
                          'BrowseTimeout': '300',
                          'Classification': 'none',
                          'DataDir': '/usr/share/cups',
                          'DefaultCharset': 'UTF-8',
                          'DefaultLanguage': 'en',
                          'DocumentRoot': '/usr/share/cups/doc-root',
                          'ErrorLog': '/var/log/cups/error_log',
                          'FilterLimit': '0',
                          'Group': 'lpadmin',
                          'HideImplicitMembers': 'Yes',
                          'HostnameLookups': 'Off',
                          'ImplicitAnyClasses': 'Off',
                          'ImplicitClasses': 'On',
                          'KeepAlive': 'On',
                          'KeepAliveTimeout': '60',
                          'MaxClients': '100',
                          'MaxJobs': '0',
                          'MaxJobsPerPrinter': '0',
                          'MaxJobsPerUser': '0',
                          'MaxLogSize': '1m',
                          'MaxRequestSize': '0m',
                          'PageLog': '/var/log/cups/page_log',
                          'PreserveJobFiles': 'Off',
                          'PreserveJobHistory': 'On',
                          'Printcap': '/etc/printcap',
                          'PrintcapFormat': 'BSD',
                          'RIPCache': '8m',
                          'RemoteRoot': 'remroot',
                          'RequestRoot': '/var/spool/cups',
                          'ServerBin': '/usr/lib/cups',
                          'ServerCertificate': '/etc/cups/ssl/server.crt',
                          'ServerKey': '/etc/cups/ssl/server.key',
                          'ServerRoot': '/etc/cups',
                          'SystemGroup': 'lpadmin',
                          'TempDir': '/var/spool/cups/tmp',
                          'Timeout': '300',
                          'User': 'lp',
                          '_debug_logging': '1',
                          '_remote_admin': '1',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '1',
                          '_user_cancel_any': '1',
                          'defaultauthtype': 'Basic'},
 'error_log_checkpoint': 412730L}
Page 9 (Print test page):
{'test_page_job_status': [(False,
                           81,
                           'LBP-810',
                           'Test Page',
                           'Stopped',
                           None)],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [30/Dec/2009:19:28:03 +0100] cupsdCloseClient: 14',
               'D [30/Dec/2009:19:28:03 +0100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [30/Dec/2009:19:28:03 +0100] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [30/Dec/2009:19:28:03 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Dec/2009:19:28:03 +0100] Get-Jobs ipp://localhost/jobs/',
               'D [30/Dec/2009:19:28:03 +0100] [Job 81] Loading attributes...',
               'D [30/Dec/2009:19:28:03 +0100] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [30/Dec/2009:19:28:03 +0100] cupsdCloseClient: 14',
               'D [30/Dec/2009:19:28:03 +0100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [30/Dec/2009:19:28:03 +0100] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [30/Dec/2009:19:28:03 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Dec/2009:19:28:03 +0100] Create-Printer-Subscription /',
               'D [30/Dec/2009:19:28:03 +0100] cupsdCreateSubscription(con=0xb8d98208(14), uri="/")',
               'D [30/Dec/2009:19:28:03 +0100] pullmethod="ippget"',
               'D [30/Dec/2009:19:28:03 +0100] notify-lease-duration=86400',
               'D [30/Dec/2009:19:28:03 +0100] notify-time-interval=0',
               'D [30/Dec/2009:19:28:03 +0100] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [30/Dec/2009:19:28:03 +0100] Added subscription 156 for server',
               'I [30/Dec/2009:19:28:03 +0100] Saving subscriptions.conf...',
               'D [30/Dec/2009:19:28:03 +0100] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [30/Dec/2009:19:28:03 +0100] cupsdCloseClient: 14',
               'D [30/Dec/2009:19:28:04 +0100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [30/Dec/2009:19:28:04 +0100] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [30/Dec/2009:19:28:04 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Dec/2009:19:28:04 +0100] Get-Notifications /',
               'D [30/Dec/2009:19:28:04 +0100] cupsdIsAuthorized: requesting-user-name="rr"',
               'D [30/Dec/2009:19:28:04 +0100] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [30/Dec/2009:19:28:04 +0100] cupsdCloseClient: 14',
               'D [30/Dec/2009:19:28:06 +0100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [30/Dec/2009:19:28:06 +0100] cupsdCloseClient: 14',
               'D [30/Dec/2009:19:28:06 +0100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [30/Dec/2009:19:28:06 +0100] cupsdReadClient: 14 POST / HTTP/1.1',
               'D [30/Dec/2009:19:28:06 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Dec/2009:19:28:06 +0100] Cancel-Subscription /',
               'D [30/Dec/2009:19:28:06 +0100] cupsdIsAuthorized: requesting-user-name="rr"',
               'I [30/Dec/2009:19:28:06 +0100] Saving subscriptions.conf...',
               'D [30/Dec/2009:19:28:06 +0100] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)',
               'D [30/Dec/2009:19:28:06 +0100] cupsdCloseClient: 14',
               'D [30/Dec/2009:19:28:06 +0100] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [30/Dec/2009:19:28:06 +0100] cupsdCloseClient: 13',
               'D [30/Dec/2009:19:28:06 +0100] cupsdReadClient: 14 GET /admin/log/error_log HTTP/1.1',
               'D [30/Dec/2009:19:28:06 +0100] cupsdAuthorize: No authentication data provided.']}

[/I](sigh)

---

### Post by 2ways on 2009-12-31
Hi Folks,
Here's an update on the situation to this point.

Major success.  Can print...most of the time.  Still some issues, however, that need to be resolved.

Here's how it worked:

1. Downloaded driver for Canon LBP-810 from [http://www.boichat.ch/nicolas/capt/](http://www.boichat.ch/nicolas/capt/)

This driver says it is Version 0.1.  There is another driver floating around at [http://www.are-ata.org/debian/capt/capt-0.4.tar.gz](http://www.are-ata.org/debian/capt/capt-0.4.tar.gz) (mentioned above), but the *.ppd files are identical.

2. Mostly followed (see below) the instructions at [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190), including downloading the driver from Canon, installing dummy packages.

I'm on Karmic, so I used the Karmic-specific instructions.

Note: 'Following the instructions' will mean following the instructions from Canon in the guide included with the tar archive you've just downloaded.  That will mean unpacking the guide archive as well (a separate step from unpacking the driver archive).

Note: For ubuntu, use the 'deb' instructions from Canon.

In the Canon instructions, pause after Step 4.

The Canon driver does not support the LBP-810, that is, it does not include a ppd file for the LBP-810 in its archive, so I manually included the ppd file from the link above (my Step 1) in the directory of cups ppd files.

Before executing Canon Step 5:

Find the Nicholas Boichat driver and change into that directory where the driver archive is.  The file is capt-0.1.tar.gz.

In a terminal:

```
$ tar zxvf capt-0.1.tar.gz

$ cp capt-0.1/ppd/Canon-LBP-810-capt.ppd /usr/share/cups/model
```Now you can continue with Canon's instructions, but at Step 5, the command will use our newly added ppd file for the LBP-810, so the execution of Step 5 will look like this:

```
$ /usr/sbin/lpadmin -p LBP5000 -m Canon-LBP-810-capt.ppd -v ccp:/var/ccpd/fifo0 -E
```Don't forget to switch back to the ubuntu instructions before Canon Step 7.

Okay.  That all worked, in so far as I am now able to print files from Karmic to my LBP-810, sometimes.

However, the rest of the instructions at the community docs link above don't pan out for me.

Problems I am still having related directly to the community docs instructions:
1. Restart and Verify section:
When I reboot ubuntu, then switch on my printer, then execute:
```
lewis@Asa:~$ sudo /etc/init.d/ccpd status
[sudo] password for lewis: 
Canon Printer Daemon for CUPS: ccpd: 2658

```I always only get the one process listed (unless I am printing something, then I could have multiple processes).

The comment in the instructions is that this indicates a problem with the way the ccpd daemon is starting.  I have followed the instructions quite closely, so there is something else going wrong here.

2. Status monitor section:
I can start the status monitor, but it gives me no message at all.  No matter how I manipulate the printer in other ways, the monitor remains unchanged and blank.

Further questions:
1. For a while, I couldn't restart ccpd.  It would give me the [fail] notice.  That has cleared up for the moment, but I don't know how or why.

2. The print queue never clears.  I can print a test page, but the job stays in the queue as 'processing' even though the page has come out of the printer.  This means that subsequent jobs in the queue won't ever print unless I manually kill the first job.  It continues to happen for every job in the queue.  Once cleared the next job does print.

3. Sometimes in 'Printer Configuration > Properties' the Printer Status says something about 'Can't open fifo' and 'something interrupted'.  I can't be exact because I can't reproduce the problem reliably.

A final point.  The community docs instructions are largely a rehash of a French forum post at [http://doc.kubuntu-fr.org/imprimantes_canon_lasershot](http://doc.kubuntu-fr.org/imprimantes_canon_lasershot), but the French post explicitly claims that it's instructions will work for a Canon LBP-810, yet provides no comment about how that is possible without a specific LBP-810 ppd file.  My French isn't good enough to go on the forum and ask the question, but I'm dying to find out why he said the LBP-810 is compatible with his instructions.  Anybody want to do us all (me) a favour and ask the question on that forum?  I can read the response, just can't construct the question!  Alas.

The summary is:

There is a way to get files printed on the Canon LBP-810 from Karmic.

There are still a number of annoying problems.

My goal is to make this laptop the family computer, so all procedures need to be family-proof.  Specifically, they need to be able to turn on the computer or printer or both (in any order, hopefully) and simply open a file and click on print.  That status seems a little way off yet, but I am still hopeful.

Any more help would be much appreciated.

Should I start a new thread with my remaining issues since the 'associating printer and driver' issue has actually been solved?  Advice on that would be helpful.

Thanks,
Lewis

---

### Post by 2ways on 2010-01-04
Just a follow up to one issue:

After a print job has finished, the 'Printer State' remains as 'Processing', but when I cancel the print job (because it never finishes 'Processing' and blocks other jobs from printing) moves to 'Idle - Can't open FIFO: Interrupted system...'

I can still print in that state, however.  For example, I can click on 'Print test page' and the 'Printer State' moves to 'Idle' and then to 'Processing', and the test page prints.

Any ideas why my print queue never clears?

It's not just sort of 'hung' either because the 'time submitted' continues to increase.  It really thinks it is still processing the job even though the page has already come out of the printer.

Thanks,
Lewis

---

### Post by eastman75 on 2010-01-30
> **2ways said:**
> Hi Folks,

Over the years there has been a bunch of traffic here and elsewhere about installing the Canon LBP-810 printer.

I have been through every script and every suggestion I can find and cannot get my printer to work.  If it's not going to work, I can accept that.

The option that is consistently missing seems to be where I associate the driver I've installed with the printer that has been found.

I get no complaints from any of the command line operations, installing the driver, etc., but both posts say I should not select the 'discovered' printer, but rather the 'local printer' option, and then specify the printer in the next step as attached to the usb port.

1) selecting a local printer is not an option in Printer Configuration in Karmic as far as I can tell

2) when selecting the discovered printer (correctly recognised as Canon LBP-810), it tells me that it knows the printer is connected to the usb port.

3) contrary to the 'how to' posts, in future steps in printer Configuration, I am never offered Canon LBP-810 to select as the printer driver I want to associate with this printer.  I am offered the foomatic driver for the LBP-470 because it doesn't think it knows about a driver for the LBP-810.

Having gone through the configuration process accepting the recommendations, everything seems happy.  I have a printer called Canon LBP-810 installed and I can send jobs to the print queue.  It's just that nothing ever prints.

Typing lpq on the command line tells me that 'Canon LBP-810 is ready and printing' and lists the jobs I have queued up.  Nothing ever happens.



Hi Lewis,

I am on a i386 desktop, running a single boot installation of 9.10.
I have done the same as you described. I am agree with every line of your message as I experienced the same frustration.

I had downloaded and installed capt-0.4.tar.gz (the work was done by Vivien Bregier and the file may be found at [http://debian.are-ata.org/]("http://debian.are-ata.org/")).   

I also get no complaints from any of the command line operations, installing the driver. Here is an example:

```

# cd capt
# make
gcc  -O2 -g -Wall -DNDEBUG capt.c -o capt
capt.c: In function ‘bitmap_seek’:
capt.c:117: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
capt.c:120: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
capt.c: In function ‘get_line’:
capt.c:148: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
capt.c:153: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result
capt.c: In function ‘compress_bitmap’:
capt.c:356: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
# make install
install -s -m a=rx capt /usr/bin
install -m a=rx capt-print /usr/bin
install -m a=r ppd/Canon-LBP-810-capt.ppd /usr/share/cups/model
install -m a=r etc/capt.conf /etc
# modprobe usblp
# chmod a+rw /dev/usb/lp0
# /etc/init.d/cups restart
 * Restarting Common Unix Printing System: cupsd              [ OK ] 

```

At this point I restarted the system and switched the printer on.
Went to System->Administration->Printing and saw that a new LBP-810 printer was added. OK, I did not remove or use it.

I sent a test page to the print queue for the installed "Canon LBP-810" printer and printing was stopped with an error "foomatic-rip failed". 

I also tried lpinfo -v in the command line after adding the printer and found:

direct usb://Canon/LBP-810
direct parallel:/dev/lp0

I was told that if you tells CUPS to use correct /dev/..., it will send data to the printer directly, which interferes with the data CAPT sends
itself, resulting in no page being printed. So I changed URI to "parallel:/dev/lp0". Some people suggest "file:///dev/null".

Then, people say that Ubuntu uses different names for USB printer devices and suggest to modify **/etc/capt.conf**-- substitute 
```
DEVICE=/dev/usb/lp0
``` 
for
```
DEVICE=/dev/usblp0
``` 

There is also the following advice.
For the printer to appear in the printer manager use the command
```
/usr/sbin/lpadmin -p LBP-810 -m Canon-LBP-810-capt.ppd -v /dev/null -E
```

So I am in dispair...
Anatoly

P.S. On command
```
/etc/init.d/ccpd status
```
I got the following 
```

: command not found, line 2: 
: command not found, line 12: 
: command not found, line 13: 
: command not found, line 19: 
: digit argument is needed: 0

```

The same is when starting ccpd. Any idea?

---

### Post by eastman75 on 2010-02-02
Hi Folks,

As Lewis said: 'Major success...'

I did managed installing the Nicolas Boichat's CAPT driver for Canon LBP-810 together with the Canon CAPT v1.90 proprietary driver (CAPTDRV190.tar.gz) on Ubuntu 9.10. My computer is a common desktop without any specific hardware.

The only addition to the Lewis's procedure is in installing transitional packages for CUPSYS as the Canon CAPT Driver references CUPSYS library libcupsys2. (Transitional package is a dummy package to ease transition to new package name.) I have found and installed the following transitional packages using Synaptic.

- cupsys-common-1.4.1-5ubuntu2.1_all.deb
- cupsys-1.4.1-5ubuntu2.1_i386.deb  
- cupsys-ddk-1.4.1-5ubuntu2.1_i386.deb  
- cupsys-bsd-1.4.1-5ubuntu2.1_i386.deb  
- cupsys-client-1.4.1-5ubuntu2.1_i386.deb   

Fortunately enough these packages were found on my computer inbetweeen those installed manually. 

Other installation steps are as described by Lewis with the same annoying problems but I've never bothered myself with restarting ccpd or using it at all, as well as with Status Monitor. Who cares? ;)

---

### Post by ias on 2010-05-27
Hello All,

After years of trying, I got this working on an AMD64

[http://newyork.ubuntuforums.org/showthread.php?p=9368266#post9368266](http://newyork.ubuntuforums.org/showthread.php?p=9368266#post9368266)

Thanks to Rocky77

IAS

---

### Post by ias on 2010-05-27
> **ias said:**
> Hello All,

After years of trying, I got this working on an AMD64

[http://newyork.ubuntuforums.org/showthread.php?p=9368266#post9368266](http://newyork.ubuntuforums.org/showthread.php?p=9368266#post9368266)

Thanks to Rocky77

IAS


Hey, I just used the same method on my 32-bit machine, and it works for the first time!

The difference is that I got the files directly from canon. 

Here the method for 32-bit:

Go to e.g. [http://support-au.canon.com.au/contents/AU/EN/0900772408.html](http://support-au.canon.com.au/contents/AU/EN/0900772408.html), to downloand CAPT_Printer_Driver_for_Linux_V200_uk_EN.tar.gz

Once you extract this download, you install the files by going into the extracted directory.. /Driver/Debian and then running the commands

```

sudo dpkg -i cndrvcups-common_2.00-2_i386.deb
sudo dpkg -i cndrvcups-capt_2.00-2_i386.deb

```

(leave out installing ia32-libs, as i guess this is only for the 64-bit version)

Then go to /etc/init.d/ccpd and delete the contents, replacing it with this:

```

#!/bin/sh
# ccpd startup script for Canon Printer Daemon for CUPS
# Modified for Debian GNU/Linux
# by Raphael Doursenaud <rdoursenaud@free.fr>.
DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=ccpd
DESC="Canon Printer Daemon for CUPS"
test -f $DAEMON || exit 0
case $1 in
start)
echo -n "Starting $DESC: $NAME"
start-stop-daemon --start --quiet --exec $DAEMON
echo "."
;;
stop)
echo -n "Stopping $DESC: $NAME"
start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
echo "."
;;
status)
echo "$DESC: $NAME:" `pidof $NAME`
;;
restart)
echo -n "Restarting $DESC: $NAME"
start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
sleep 1
start-stop-daemon --start --quiet --exec $DAEMON
echo "."
;;
*)
echo "Usage: ccpd {start|stop|status}"
exit 1
;;
esac
exit 0

```

Then install the printer
```

sudo /etc/init.d/cups restart
sudo /usr/sbin/lpadmin -p LBP-810 -m CNCUPSLBP1120CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
sudo /usr/sbin/ccpdadmin -p LBP-810 -o /dev/usb/lp0
sudo /etc/init.d/ccpd restart

```

Lastly 

```

sudo ccpd start

```

That's it. I am still a little stunned this works, it's been so long trying. I have no clue what is going on really, but it works - sort of.

If you restart or put the thing to sleep you have to do the "sudo /etc/init.d/ccpd restart"
again each time, it seems. I created a little launcher. Isn't there a way to add this to start-up or something?

Hope this works for others.


IAS

---

