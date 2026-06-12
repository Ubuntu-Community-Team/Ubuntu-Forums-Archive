---
title: "[SOLVED] HP 1000 Printer"
date: 2008-10-23
forum: General Help
---

### Post by hatmancan on 2008-10-23
i am trying to get my printer to work.. it works in windows xp but when i start ubuntu will not work..here is my error report
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x8707460>,
 'cups_instance': None,
 'cups_queue': 'hp_LaserJet_1000',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/hp_LaserJet_1000?serial=0',
                       'printer-info': u'Hewlett-Packard hp LaserJet 1000',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP LaserJet 1000 Foomatic/foo2zjs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167940,
                       'printer-uri-supported': u'ipp://localhost:631/printers/hp_LaserJet_1000'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [10],
 'test_page_job_status': [(10, 'hp_LaserJet_1000', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

someone please help
ty
hat

---

### Post by drs305 on 2008-10-23
I am using the HP LaserJet 1000 on both Hardy and Intrepid. I have installed **hplip** and **hplip-gui** as well as all the **cups** packages from synaptic.

I installed the printer via System, Administration, Printing, Add Printer. The driver is: HP LaserJet 1000 Foomatic/foo2zjs 

The printer address is: usb://HP/LaserJet%201000

I can access the printer settings via cups: [http://localhost:631/printers](http://localhost:631/printers)
although when I try to access the printer via System, Preferences, HPLIP Toolbox it shows the printer as not installed.

From time to time I can only get it to be seen by the system by recycling the printer power.

If none of this is helpful, I know I have visited this site but don't know if I ever used it:
[http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/")

---

### Post by Tamlynmac on 2008-10-24
You may wish to check which version of the HPLIP driver is installed. The newest one is available at:

[http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html)

I had similar problems until I installed the newest driver available at that site. Just simply use the automatic installer and follow the instructions. After installing this driver my all-in-one HP just worked...

---

### Post by hatmancan on 2008-10-24
i am new to this open source.. my printer is showing as default..
i have tried to download everything possible but do not understand it..i have gone to all above links but get to confused..i think i am just going to have to exit ubuntu/kde and open windows and boot to windows and print from there..
i am using evolution and it will not even let me print from there..i use for business..this is not going to be good if i have to keep exiting back and forth..

if someone can suggest how to install then please help me
ty
hat

---

### Post by drs305 on 2008-10-24
> **hatmancan said:**
> i am new to this open source.. my printer is showing as default..

if someone can suggest how to install then please help me
ty
hat

I will be glad to try and help you. I will go through the steps. If you don't understand how to accomplish the step, send me a message or ask here.

1. Uninstall hplib 3.7
Open synaptic (System, Administration, Synaptic Package Manager).
Click the right window and type **hplip**  If you see it installed (green box), check the version number. If it is 3.7 or less, right click and select 'Mark for Removal'. Then hit 'Apply' in the top menu.

2. Download HP Drivers:
Go to [HP Linux Imaging and Printing]("http://hplipopensource.com/hplip-web/gethplip.html")
Click on the green "Download HPLIP" (Version 2.8.9)
A new window will open. Select "Save File".
The file "**hplip-2.8.9.run**" should download to your desktop. If the Desktop is not your default download location, move the file there.

All the steps with graphics are displayed here:
[http://hplipopensource.com/hplip-web/install/install/index.html]("http://hplipopensource.com/hplip-web/install/install/index.html")

3. Open a terminal (System, Accessories, Terminal) and run these commands. When you run the second one, you should see "**hplip-2.8.9.run**" and perhaps an error message about not being able to open a directory (that is ok):
```

cd $HOME/Desktop
ls hplip*

```

4. Install. In the terminal window, copy and paste this command and ENTER:
```
sh hplip-2.8.9.run
```
a. I selected custom, but when it asks, select "a" for automatic.
b. Select "y" if it displays your correct version of ubuntu.
c. Support for parallel printing. Select "**y**" or "**n**". Your choice.
d. Enter your password.
e. Press ENTER at the "read installation notes" prompt

5. You may get 'missing dependency' messages. The program is designed to download these and continue the installation. 

6. When the installation is complete, it will ask you to unplug your usb connection or restart the computer and run "sudo hp-setup". 
a. Since the first is easier, we will use the re-plug option. Type '**p**".
b. Unplug the usb connection from the printer or computer, wait a few seconds, and then reconnect it. After reattaching the usb connection, type **ENTER**. 

7. The HP Setup Program will now start.
a. Select the "**USB** option.
b. "**Next**". 
You should see your printer listed.
c. "**Next**". 
d. Make sure "Download Plug-in" is selected and click on "**Download and Install**"
e. After a delay while the plugin is downloaded (you won't see it), 
check the "**Accept Terms**" and then "**Install Plugin**"
f. You should get a "Plugin Installed" message.
g. Enter printer information, if desired, then "**Next**".
h. Tick the "Print Test Page" and then "**Finish**". 

If you have difficulties with this, tell us what the error messages are and we can try altering the installation.

If you uninstalled hplib in the first steps and want to restore it after giving up on this method:
```

sudo aptitude install hplip hplip-data

```

---

### Post by hatmancan on 2008-10-24
drs..you are a savior.. worked like a charm...
now i have to fine tune my canon scanner..lol know how to do that as well...out of curiosity where are you from..
and by the way thanks soooooo much for helping me with such great instructions..i literally spent 3 hrs trying to find instructions for people like myself who are not used to this open source..
ty
tyty
hat

---

### Post by hatmancan on 2008-10-26
hey drs.. i am having a problem again???
when i go to print now it goes through all the process and at the top it says print job has finished printing..
problem is nothing is printing???
can you suggest anything or do i go through the process i did before?
ty
hat

---

### Post by drs305 on 2008-10-26
I replied via PM before I saw this. I have a couple of suggestions which I sent you. 

When we get a solution that works one of us can post it here.

---

### Post by hatmancan on 2008-10-26
hey drs..
i went to system>printers and then highlighted my hp1000..
i then clicked change driver on the one that was showing and installed thehpis driver..
this worked and now printer is back up running again...

just to let you know.. for some unknown reason the print seems to be alot cleaner then when i print usung windows os.. have you ever heard of this before?
cheers and ty again
hat

---

### Post by drs305 on 2008-10-26
Although I relied on the foomatic drivers (foo2zjs) for a long time, recently I have found the HP drivers (hpijs) to be a bit more reliable for me. 

I haven't printed with windows for a while now so I can't honestly compare the two but I'm glad you are seeing improvement.

---

### Post by gtmarks on 2009-09-24
I am having a similar problem.  I've tried (numerous times) following drs305's instructions.  Step 7 is a bit different for me; after step 7c, I do not get any "download" options.  I do seem to be able to install the printer, but get results like this:

505$lpr t

506$lpq
hp_LaserJet_2420 is ready and printing
Rank    Owner   Job     File(s)                         Total Size
active  marks   51      t                               1024 bytes

507$lpq
hp_LaserJet_2420 is ready
Rank    Owner   Job     File(s)                         Total Size
1st     marks   51      t                               1024 bytes

In between 506 and 507, a bubble popped up to announce that the print job had completed.  Meanwhile, nothing comes out of the printer.

In System -> Administration -> Printing, I've tried troubleshooting the problem.  The printing troubleshooter reports: 

Status Messages
There are status messages associated with this queue.
The printer's state message is: '/usr/lib/cups/backend/hp failed'.

I then enable debugging and attempt to print a test page.  I click "Print Test Page"; when the marked job does not print, I highlight "No" and receive these error log messages:

D [24/Sep/2009:17:22:27 -0500] update_cups_browse: Refused 184 bytes from 165.134.13.82
D [24/Sep/2009:17:22:27 -0500] cupsdReadClient: 28 POST / HTTP/1.1
D [24/Sep/2009:17:22:27 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:27 -0500] Get-Jobs ipp://localhost/printers/
D [24/Sep/2009:17:22:27 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:27 -0500] cupsdReadClient: 28 POST / HTTP/1.1
D [24/Sep/2009:17:22:27 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:27 -0500] Get-Jobs ipp://localhost/printers/
D [24/Sep/2009:17:22:27 -0500] [Job 32] Loading attributes...
D [24/Sep/2009:17:22:27 -0500] [Job 41] Loading attributes...
D [24/Sep/2009:17:22:27 -0500] [Job 42] Loading attributes...
D [24/Sep/2009:17:22:27 -0500] [Job 50] Loading attributes...
D [24/Sep/2009:17:22:27 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:27 -0500] cupsdReadClient: 28 POST / HTTP/1.1
D [24/Sep/2009:17:22:27 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:27 -0500] Create-Printer-Subscription /
D [24/Sep/2009:17:22:27 -0500] cupsdCreateSubscription(con=0x7fc3de01ae10(28), uri="/")
D [24/Sep/2009:17:22:27 -0500] pullmethod="ippget"
D [24/Sep/2009:17:22:27 -0500] notify-lease-duration=86400
D [24/Sep/2009:17:22:27 -0500] notify-time-interval=0
D [24/Sep/2009:17:22:27 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [24/Sep/2009:17:22:27 -0500] Added subscription 34 for server
I [24/Sep/2009:17:22:27 -0500] Saving subscriptions.conf...
D [24/Sep/2009:17:22:27 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:28 -0500] update_cups_browse: Refused 161 bytes from 165.134.13.82
D [24/Sep/2009:17:22:28 -0500] cupsdReadClient: 28 POST / HTTP/1.1
D [24/Sep/2009:17:22:28 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:28 -0500] Get-Notifications /
D [24/Sep/2009:17:22:28 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:22:28 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)
I [24/Sep/2009:17:22:51 -0500] Saving subscriptions.conf...
D [24/Sep/2009:17:22:51 -0500] [Job 51] job-sheets=none,none
D [24/Sep/2009:17:22:51 -0500] [Job 51] banner_page = 0
D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[0]="hp_LaserJet_2420"
D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[1]="51"
D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[2]="marks"
D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[3]="t"
D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[4]="1"
D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[5]="media=Letter sides=one-sided finishings=3 number-up=1 job-uuid=urn:uuid:ddbb3f45-2c13-3e35-7ce4-4c3417c7efd3"
D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[6]="/var/spool/cups/d00051-001"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[9]="SERVER_ADMIN=root@ubuntu"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[10]="SOFTWARE=CUPS/1.3.9"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[12]="TZ=America/Chicago"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[13]="USER=root"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[16]="IPP_PORT=631"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[17]="CHARSET=utf-8"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[18]="LANG=en_US.UTF8"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[19]="PPD=/etc/cups/ppd/hp_LaserJet_2420.ppd"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[20]="RIP_MAX_CACHE=8m"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[21]="CONTENT_TYPE=text/plain"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[22]="DEVICE_URI=hp:/usb/hp_LaserJet_2420?serial=CNDJC12254"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[23]="PRINTER=hp_LaserJet_2420"
D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[24]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"
I [24/Sep/2009:17:22:51 -0500] [Job 51] Started filter /usr/lib/cups/filter/texttopdf (PID 16593)
I [24/Sep/2009:17:22:51 -0500] [Job 51] Started filter /usr/lib/cups/filter/pdftopdf (PID 16594)
I [24/Sep/2009:17:22:51 -0500] [Job 51] Started filter /usr/lib/cups/filter/cpdftocps (PID 16595)
I [24/Sep/2009:17:22:51 -0500] [Job 51] Started backend /usr/lib/cups/backend/hp (PID 16596)
I [24/Sep/2009:17:22:51 -0500] Saving subscriptions.conf...
D [24/Sep/2009:17:22:51 -0500] PID 16593 (/usr/lib/cups/filter/texttopdf) exited with no errors.
D [24/Sep/2009:17:22:51 -0500] [Job 51] Page = 612x792; 12,12 to 600,780
D [24/Sep/2009:17:22:51 -0500] PID 16594 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [24/Sep/2009:17:22:51 -0500] [Job 51] Device copies: 1; device collate:
D [24/Sep/2009:17:22:51 -0500] [Job 51] pdftops - copying to temp print file "/tmp/4abbf13b70f9d"
D [24/Sep/2009:17:22:51 -0500] [Job 51] Page = 612x792; 12,12 to 600,780
D [24/Sep/2009:17:22:51 -0500] [Job 51] slow_collate=0, slow_duplex=0, slow_order=0
D [24/Sep/2009:17:22:51 -0500] [Job 51] Before copy_comments - %!PS-Adobe-3.0
D [24/Sep/2009:17:22:51 -0500] [Job 51] %!PS-Adobe-3.0
D [24/Sep/2009:17:22:51 -0500] [Job 51] %%LanguageLevel: 2
D [24/Sep/2009:17:22:51 -0500] [Job 51] %%DocumentSuppliedResources: (atend)
D [24/Sep/2009:17:22:51 -0500] [Job 51] %%DocumentMedia: plain 612 792 0 () ()
D [24/Sep/2009:17:22:51 -0500] [Job 51] %%BoundingBox: 0 0 612 792
D [24/Sep/2009:17:22:51 -0500] [Job 51] %%Pages: 1
D [24/Sep/2009:17:22:51 -0500] [Job 51] %%EndComments
D [24/Sep/2009:17:22:51 -0500] [Job 51] Before copy_prolog - %%BeginDefaults
I [24/Sep/2009:17:22:51 -0500] Saving subscriptions.conf...
D [24/Sep/2009:17:22:51 -0500] [Job 51] Before copy_setup - %%BeginSetup
D [24/Sep/2009:17:22:51 -0500] cupsdAcceptClient: 30 from localhost (Domain)
D [24/Sep/2009:17:22:51 -0500] cupsdAcceptClient: 32 from localhost (Domain)
D [24/Sep/2009:17:22:51 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:22:51 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:51 -0500] Get-Notifications /
D [24/Sep/2009:17:22:51 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:22:51 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:51 -0500] cupsdReadClient: 32 POST / HTTP/1.1
D [24/Sep/2009:17:22:51 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:51 -0500] Get-Notifications /
D [24/Sep/2009:17:22:51 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:22:51 -0500] cupsdProcessIPPRequest: 32 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:51 -0500] cupsdCloseClient: 32
D [24/Sep/2009:17:22:51 -0500] cupsdReadClient: 28 POST / HTTP/1.1
D [24/Sep/2009:17:22:51 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:51 -0500] Get-Notifications /
D [24/Sep/2009:17:22:51 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:22:51 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:51 -0500] cupsdCloseClient: 30
D [24/Sep/2009:17:22:52 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82
D [24/Sep/2009:17:22:54 -0500] cupsdAcceptClient: 30 from localhost (Domain)
D [24/Sep/2009:17:22:54 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:22:54 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:54 -0500] CUPS-Get-Printers
D [24/Sep/2009:17:22:54 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:54 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:22:54 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:54 -0500] CUPS-Get-Classes
D [24/Sep/2009:17:22:54 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:54 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:22:54 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:54 -0500] CUPS-Get-Default
D [24/Sep/2009:17:22:54 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:54 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:22:54 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:54 -0500] Get-Printer-Attributes ipp://localhost/printers/hp_LaserJet_2420
D [24/Sep/2009:17:22:54 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:54 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:22:54 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:54 -0500] Get-Jobs ipp://localhost/printers/hp_LaserJet_2420
D [24/Sep/2009:17:22:54 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:54 -0500] cupsdCloseClient: 30
D [24/Sep/2009:17:22:56 -0500] cupsdAcceptClient: 30 from localhost (Domain)
D [24/Sep/2009:17:22:56 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:22:56 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:56 -0500] CUPS-Get-Printers
D [24/Sep/2009:17:22:56 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:56 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:22:56 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:56 -0500] CUPS-Get-Classes
D [24/Sep/2009:17:22:56 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:56 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:22:56 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:56 -0500] CUPS-Get-Default
D [24/Sep/2009:17:22:56 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:22:56 -0500] cupsdReadClient: 30 POST /jobs/ HTTP/1.1
D [24/Sep/2009:17:22:56 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:22:56 -0500] Cancel-Job ipp://localhost/printers/t
D [24/Sep/2009:17:22:56 -0500] Cancel-Job client-error-not-found: The printer or class was not found.
D [24/Sep/2009:17:22:56 -0500] cupsdProcessIPPRequest: 30 status_code=406 (client-error-not-found)
D [24/Sep/2009:17:22:56 -0500] cupsdCloseClient: 30
D [24/Sep/2009:17:22:57 -0500] cupsdNetIFUpdate: "lo" = localhost:631
D [24/Sep/2009:17:22:57 -0500] cupsdNetIFUpdate: "eth0" = 165.134.13.82:631
D [24/Sep/2009:17:22:57 -0500] cupsdNetIFUpdate: "lo" = localhost:631
D [24/Sep/2009:17:22:57 -0500] cupsdNetIFUpdate: "eth0" = fe80::226:55ff:fef4:2b69%eth0:631
D [24/Sep/2009:17:22:57 -0500] cupsdNetIFUpdate: "wlan0" = fe80::221:6aff:fe67:9152%wlan0:631
D [24/Sep/2009:17:22:57 -0500] update_cups_browse: Refused 172 bytes from 165.134.13.82
D [24/Sep/2009:17:22:58 -0500] update_cups_browse: Refused 184 bytes from 165.134.13.82
D [24/Sep/2009:17:22:59 -0500] update_cups_browse: Refused 161 bytes from 165.134.13.82
D [24/Sep/2009:17:23:01 -0500] cupsdAcceptClient: 30 from localhost (Domain)
D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:01 -0500] CUPS-Get-Printers
D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:01 -0500] CUPS-Get-Classes
D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:01 -0500] CUPS-Get-Default
D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 30 POST /jobs/ HTTP/1.1
D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:01 -0500] Cancel-Job ipp://localhost/jobs/51
D [24/Sep/2009:17:23:01 -0500] cupsdIsAuthorized: requesting-user-name="marks"
I [24/Sep/2009:17:23:01 -0500] Saving subscriptions.conf...
I [24/Sep/2009:17:23:01 -0500] Saving subscriptions.conf...
I [24/Sep/2009:17:23:01 -0500] [Job 51] Canceled by "marks".
D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:01 -0500] cupsdCloseClient: 30
D [24/Sep/2009:17:23:01 -0500] cupsdAcceptClient: 30 from localhost (Domain)
D [24/Sep/2009:17:23:01 -0500] cupsdAcceptClient: 32 from localhost (Domain)
D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:01 -0500] Get-Notifications /
D [24/Sep/2009:17:23:01 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 32 POST / HTTP/1.1
D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:01 -0500] Get-Notifications /
D [24/Sep/2009:17:23:01 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 32 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 28 POST / HTTP/1.1
D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:01 -0500] Get-Notifications /
D [24/Sep/2009:17:23:01 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:01 -0500] cupsdCloseClient: 32
D [24/Sep/2009:17:23:01 -0500] cupsdCloseClient: 30
D [24/Sep/2009:17:23:02 -0500] cupsdAcceptClient: 30 from localhost (Domain)
D [24/Sep/2009:17:23:02 -0500] [Job 51] Unloading...
D [24/Sep/2009:17:23:02 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82
D [24/Sep/2009:17:23:02 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:23:02 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:02 -0500] CUPS-Get-Printers
D [24/Sep/2009:17:23:02 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:02 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:23:02 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:02 -0500] CUPS-Get-Classes
D [24/Sep/2009:17:23:02 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:02 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:23:02 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:02 -0500] CUPS-Get-Default
D [24/Sep/2009:17:23:02 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:02 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:23:02 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:02 -0500] Get-Printer-Attributes ipp://localhost/printers/hp_LaserJet_2420
D [24/Sep/2009:17:23:02 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:02 -0500] cupsdReadClient: 30 POST / HTTP/1.1
D [24/Sep/2009:17:23:02 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:02 -0500] Get-Jobs ipp://localhost/printers/hp_LaserJet_2420
D [24/Sep/2009:17:23:02 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:02 -0500] cupsdCloseClient: 30
D [24/Sep/2009:17:23:12 -0500] cupsdReadClient: 28 POST /jobs/ HTTP/1.1
D [24/Sep/2009:17:23:12 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:12 -0500] Cancel-Job ipp://localhost/jobs/51
D [24/Sep/2009:17:23:12 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:12 -0500] Cancel-Job client-error-not-possible: Job #51 is already canceled - can't cancel.
D [24/Sep/2009:17:23:12 -0500] cupsdProcessIPPRequest: 28 status_code=404 (client-error-not-possible)
D [24/Sep/2009:17:23:15 -0500] cupsdAcceptClient: 30 from localhost (Domain)
D [24/Sep/2009:17:23:15 -0500] cupsdReadClient: 30 POST /printers/hp_LaserJet_2420 HTTP/1.1
D [24/Sep/2009:17:23:15 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:15 -0500] Print-Job ipp://localhost/printers/hp_LaserJet_2420
D [24/Sep/2009:17:23:15 -0500] [Job ???] Auto-typing file...
I [24/Sep/2009:17:23:15 -0500] [Job ???] Request file type is application/postscript.
D [24/Sep/2009:17:23:15 -0500] add_job: requesting-user-name="marks"
D [24/Sep/2009:17:23:15 -0500] Adding default job-sheets values "none,none"...
I [24/Sep/2009:17:23:15 -0500] [Job 52] Adding start banner page "none".
I [24/Sep/2009:17:23:15 -0500] Saving subscriptions.conf...
I [24/Sep/2009:17:23:15 -0500] [Job 52] Adding end banner page "none".
I [24/Sep/2009:17:23:15 -0500] [Job 52] File of type application/postscript queued by "marks".
D [24/Sep/2009:17:23:15 -0500] [Job 52] hold_until=0
I [24/Sep/2009:17:23:15 -0500] [Job 52] Queued on "hp_LaserJet_2420" by "marks".
I [24/Sep/2009:17:23:15 -0500] Saving subscriptions.conf...
D [24/Sep/2009:17:23:15 -0500] [Job 52] job-sheets=none,none
D [24/Sep/2009:17:23:15 -0500] [Job 52] banner_page = 0
D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[0]="hp_LaserJet_2420"
D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[1]="52"
D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[2]="marks"
D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[3]="Test Page"
D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[4]="1"
D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[5]="job-uuid=urn:uuid:b24c94fd-d248-3cd5-654a-926bbc2432fb"
D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[6]="/var/spool/cups/d00052-001"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[9]="SERVER_ADMIN=root@ubuntu"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[10]="SOFTWARE=CUPS/1.3.9"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[12]="TZ=America/Chicago"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[13]="USER=root"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[16]="IPP_PORT=631"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[17]="CHARSET=utf-8"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[18]="LANG=en_US.UTF8"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[19]="PPD=/etc/cups/ppd/hp_LaserJet_2420.ppd"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[20]="RIP_MAX_CACHE=8m"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[21]="CONTENT_TYPE=application/postscript"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[22]="DEVICE_URI=hp:/usb/hp_LaserJet_2420?serial=CNDJC12254"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[23]="PRINTER=hp_LaserJet_2420"
D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[24]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"
I [24/Sep/2009:17:23:15 -0500] [Job 52] Started filter /usr/lib/cups/filter/pstopdf (PID 16630)
I [24/Sep/2009:17:23:15 -0500] [Job 52] Started filter /usr/lib/cups/filter/pdftopdf (PID 16632)
I [24/Sep/2009:17:23:15 -0500] [Job 52] Started filter /usr/lib/cups/filter/cpdftocps (PID 16633)
I [24/Sep/2009:17:23:15 -0500] [Job 52] Started backend /usr/lib/cups/backend/hp (PID 16637)
I [24/Sep/2009:17:23:15 -0500] Saving subscriptions.conf...
D [24/Sep/2009:17:23:15 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:15 -0500] [Job 52] pstopdf 6 args: 52 marks Test Page 1 job-uuid=urn:uuid:b24c94fd-d248-3cd5-654a-926bbc2432fb /var/spool/cups/d00052-001
D [24/Sep/2009:17:23:15 -0500] [Job 52] PPD: /etc/cups/ppd/hp_LaserJet_2420.ppd
D [24/Sep/2009:17:23:15 -0500] [Job 52] Resolution: 600x1200
D [24/Sep/2009:17:23:15 -0500] [Job 52] Page size: Letter
D [24/Sep/2009:17:23:15 -0500] [Job 52] Width: 612, height: 792, absolute margins: 12.00, 12.12, 599.88, 780.00
D [24/Sep/2009:17:23:15 -0500] [Job 52] Relative margins: 12.00, 12.12, 12.12, 12.00
D [24/Sep/2009:17:23:15 -0500] [Job 52] PPD options: -r600x1200 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [24/Sep/2009:17:23:15 -0500] [Job 52] PostScript to be injected:
D [24/Sep/2009:17:23:15 -0500] [Job 52] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dDoNumCopies -dPDFSETTINGS=/printer -r600x1200 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -
D [24/Sep/2009:17:23:16 -0500] cupsdAcceptClient: 32 from localhost (Domain)
D [24/Sep/2009:17:23:16 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82
D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 32 POST / HTTP/1.1
D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:16 -0500] Get-Notifications /
D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 32 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:16 -0500] cupsdAcceptClient: 33 from localhost (Domain)
D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 33 POST / HTTP/1.1
D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:16 -0500] Get-Notifications /
D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 32 POST / HTTP/1.1
D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:16 -0500] Get-Job-Attributes ipp://localhost/jobs/52
D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 32 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:16 -0500] cupsdCloseClient: 33
D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 28 POST / HTTP/1.1
D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:16 -0500] Get-Notifications /
D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:16 -0500] cupsdCloseClient: 32
D [24/Sep/2009:17:23:16 -0500] [Job 52] GPL Ghostscript 8.64: Set UseCIEColor for UseDeviceIndependentColor to work properly.
D [24/Sep/2009:17:23:16 -0500] PID 16630 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [24/Sep/2009:17:23:16 -0500] PID 16632 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [24/Sep/2009:17:23:16 -0500] [Job 52] Device copies: 1; device collate:
D [24/Sep/2009:17:23:16 -0500] [Job 52] pdftops - copying to temp print file "/tmp/4abbf15457bac"
D [24/Sep/2009:17:23:16 -0500] [Job 52] Page = 612x792; 12,12 to 600,780
D [24/Sep/2009:17:23:16 -0500] [Job 52] slow_collate=0, slow_duplex=0, slow_order=0
D [24/Sep/2009:17:23:16 -0500] [Job 52] Before copy_comments - %!PS-Adobe-3.0
D [24/Sep/2009:17:23:16 -0500] [Job 52] %!PS-Adobe-3.0
D [24/Sep/2009:17:23:16 -0500] [Job 52] %%LanguageLevel: 2
D [24/Sep/2009:17:23:16 -0500] [Job 52] %%DocumentSuppliedResources: (atend)
D [24/Sep/2009:17:23:16 -0500] [Job 52] %%DocumentMedia: plain 612 792 0 () ()
D [24/Sep/2009:17:23:16 -0500] [Job 52] %%BoundingBox: 0 0 612 792
D [24/Sep/2009:17:23:16 -0500] [Job 52] %%Pages: 1
D [24/Sep/2009:17:23:16 -0500] [Job 52] %%EndComments
D [24/Sep/2009:17:23:16 -0500] [Job 52] Before copy_prolog - %%BeginDefaults
I [24/Sep/2009:17:23:16 -0500] Saving subscriptions.conf...
D [24/Sep/2009:17:23:16 -0500] [Job 52] Before copy_setup - %%BeginSetup
D [24/Sep/2009:17:23:16 -0500] [Job 52] Before page loop - %%Page: 1 1
D [24/Sep/2009:17:23:16 -0500] [Job 52] Copying page 1...
I [24/Sep/2009:17:23:16 -0500] Saving subscriptions.conf...
D [24/Sep/2009:17:23:16 -0500] [Job 52] pagew = 587.9, pagel = 767.9
D [24/Sep/2009:17:23:16 -0500] [Job 52] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [24/Sep/2009:17:23:16 -0500] [Job 52] PageLeft = 12.0, PageRight = 599.9
D [24/Sep/2009:17:23:16 -0500] [Job 52] PageTop = 780.0, PageBottom = 12.1
D [24/Sep/2009:17:23:16 -0500] [Job 52] PageWidth = 612.0, PageLength = 792.0
D [24/Sep/2009:17:23:16 -0500] [Job 52] prnt/backend/hp.c 727: INFO: open device failed stat=21; will retry in 30 seconds...
D [24/Sep/2009:17:23:16 -0500] cupsdAcceptClient: 33 from localhost (Domain)
D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 33 POST / HTTP/1.1
D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:16 -0500] Get-Notifications /
D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:16 -0500] cupsdAcceptClient: 35 from localhost (Domain)
D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 35 POST / HTTP/1.1
D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:16 -0500] Get-Notifications /
D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 35 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:16 -0500] cupsdCloseClient: 33
D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 28 POST / HTTP/1.1
D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:16 -0500] Get-Notifications /
D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:16 -0500] cupsdCloseClient: 35
D [24/Sep/2009:17:23:22 -0500] cupsdAcceptClient: 33 from localhost (Domain)
D [24/Sep/2009:17:23:22 -0500] Report: clients=3
D [24/Sep/2009:17:23:22 -0500] Report: jobs=8
D [24/Sep/2009:17:23:22 -0500] Report: jobs-active=3
D [24/Sep/2009:17:23:22 -0500] Report: printers=4
D [24/Sep/2009:17:23:22 -0500] Report: printers-implicit=0
D [24/Sep/2009:17:23:22 -0500] Report: stringpool-string-count=4830
D [24/Sep/2009:17:23:22 -0500] Report: stringpool-alloc-bytes=15520
D [24/Sep/2009:17:23:22 -0500] Report: stringpool-total-bytes=104824
D [24/Sep/2009:17:23:22 -0500] cupsdReadClient: 33 POST / HTTP/1.1
D [24/Sep/2009:17:23:22 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:22 -0500] CUPS-Get-Printers
D [24/Sep/2009:17:23:22 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:22 -0500] cupsdReadClient: 33 POST / HTTP/1.1
D [24/Sep/2009:17:23:22 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:22 -0500] CUPS-Get-Classes
D [24/Sep/2009:17:23:22 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:22 -0500] cupsdReadClient: 33 POST / HTTP/1.1
D [24/Sep/2009:17:23:22 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:22 -0500] CUPS-Get-Default
D [24/Sep/2009:17:23:22 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:22 -0500] cupsdReadClient: 33 POST / HTTP/1.1
D [24/Sep/2009:17:23:22 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:22 -0500] Get-Printer-Attributes ipp://localhost/printers/hp_LaserJet_2420
D [24/Sep/2009:17:23:22 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:22 -0500] cupsdReadClient: 33 POST / HTTP/1.1
D [24/Sep/2009:17:23:22 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:22 -0500] Get-Jobs ipp://localhost/printers/hp_LaserJet_2420
D [24/Sep/2009:17:23:22 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:22 -0500] cupsdCloseClient: 33
D [24/Sep/2009:17:23:28 -0500] [Job 32] Unloading...
D [24/Sep/2009:17:23:28 -0500] [Job 41] Unloading...
D [24/Sep/2009:17:23:28 -0500] [Job 42] Unloading...
D [24/Sep/2009:17:23:28 -0500] [Job 50] Unloading...
D [24/Sep/2009:17:23:28 -0500] update_cups_browse: Refused 172 bytes from 165.134.13.82
D [24/Sep/2009:17:23:29 -0500] update_cups_browse: Refused 184 bytes from 165.134.13.82
D [24/Sep/2009:17:23:30 -0500] update_cups_browse: Refused 161 bytes from 165.134.13.82
E [24/Sep/2009:17:23:36 -0500] PID 16596 (/usr/lib/cups/backend/hp) stopped with status 1!
D [24/Sep/2009:17:23:36 -0500] PID 16595 (/usr/lib/cups/filter/cpdftocps) exited with no errors.
D [24/Sep/2009:17:23:47 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82
D [24/Sep/2009:17:23:54 -0500] [Job 52] prnt/backend/hp.c 743: ERROR: cannot open channel PRINT
E [24/Sep/2009:17:23:54 -0500] PID 16637 (/usr/lib/cups/backend/hp) stopped with status 1!
D [24/Sep/2009:17:23:54 -0500] [Job 52] Wrote 1 pages...
D [24/Sep/2009:17:23:54 -0500] PID 16633 (/usr/lib/cups/filter/cpdftocps) exited with no errors.
D [24/Sep/2009:17:23:54 -0500] [Job 52] File 0 is complete.
I [24/Sep/2009:17:23:54 -0500] [Job 52] Backend returned status 1 (failed)
I [24/Sep/2009:17:23:54 -0500] Saving subscriptions.conf...
D [24/Sep/2009:17:23:54 -0500] set_hold_until: hold_until = 1253831334
I [24/Sep/2009:17:23:54 -0500] Saving subscriptions.conf...
D [24/Sep/2009:17:23:54 -0500] cupsdAcceptClient: 33 from localhost (Domain)
D [24/Sep/2009:17:23:54 -0500] cupsdAcceptClient: 35 from localhost (Domain)
D [24/Sep/2009:17:23:54 -0500] cupsdReadClient: 33 POST / HTTP/1.1
D [24/Sep/2009:17:23:54 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:54 -0500] Get-Notifications /
D [24/Sep/2009:17:23:54 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:54 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:54 -0500] cupsdReadClient: 35 POST / HTTP/1.1
D [24/Sep/2009:17:23:54 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:54 -0500] Get-Notifications /
D [24/Sep/2009:17:23:54 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:54 -0500] cupsdProcessIPPRequest: 35 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:54 -0500] cupsdCloseClient: 35
D [24/Sep/2009:17:23:54 -0500] cupsdReadClient: 28 POST / HTTP/1.1
D [24/Sep/2009:17:23:54 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:54 -0500] Get-Notifications /
D [24/Sep/2009:17:23:54 -0500] cupsdIsAuthorized: requesting-user-name="marks"
D [24/Sep/2009:17:23:54 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:54 -0500] cupsdAcceptClient: 35 from localhost (Domain)
D [24/Sep/2009:17:23:54 -0500] cupsdReadClient: 35 POST / HTTP/1.1
D [24/Sep/2009:17:23:54 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:54 -0500] Get-Printer-Attributes ipp://ubuntu:631/printers/hp_LaserJet_2420
D [24/Sep/2009:17:23:54 -0500] cupsdProcessIPPRequest: 35 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:54 -0500] cupsdReadClient: 35 POST / HTTP/1.1
D [24/Sep/2009:17:23:54 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:23:54 -0500] Get-Job-Attributes ipp://localhost/jobs/52
D [24/Sep/2009:17:23:54 -0500] cupsdProcessIPPRequest: 35 status_code=0 (successful-ok)
D [24/Sep/2009:17:23:54 -0500] cupsdCloseClient: 33
D [24/Sep/2009:17:23:55 -0500] cupsdNetIFUpdate: "lo" = localhost:631
D [24/Sep/2009:17:23:55 -0500] cupsdNetIFUpdate: "eth0" = 165.134.13.82:631
D [24/Sep/2009:17:23:55 -0500] cupsdNetIFUpdate: "lo" = localhost:631
D [24/Sep/2009:17:23:55 -0500] cupsdNetIFUpdate: "eth0" = fe80::226:55ff:fef4:2b69%eth0:631
D [24/Sep/2009:17:23:55 -0500] cupsdNetIFUpdate: "wlan0" = fe80::221:6aff:fe67:9152%wlan0:631
D [24/Sep/2009:17:23:55 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82
D [24/Sep/2009:17:23:59 -0500] update_cups_browse: Refused 172 bytes from 165.134.13.82
D [24/Sep/2009:17:24:00 -0500] update_cups_browse: Refused 184 bytes from 165.134.13.82
D [24/Sep/2009:17:24:01 -0500] update_cups_browse: Refused 161 bytes from 165.134.13.82
D [24/Sep/2009:17:24:24 -0500] Report: clients=3
D [24/Sep/2009:17:24:24 -0500] Report: jobs=8
D [24/Sep/2009:17:24:24 -0500] Report: jobs-active=3
D [24/Sep/2009:17:24:24 -0500] Report: printers=4
D [24/Sep/2009:17:24:24 -0500] Report: printers-implicit=0
D [24/Sep/2009:17:24:24 -0500] Report: stringpool-string-count=4779
D [24/Sep/2009:17:24:24 -0500] Report: stringpool-alloc-bytes=15040
D [24/Sep/2009:17:24:24 -0500] Report: stringpool-total-bytes=104312
D [24/Sep/2009:17:24:26 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82
D [24/Sep/2009:17:24:30 -0500] update_cups_browse: Refused 172 bytes from 165.134.13.82
D [24/Sep/2009:17:24:31 -0500] update_cups_browse: Refused 184 bytes from 165.134.13.82
D [24/Sep/2009:17:24:32 -0500] update_cups_browse: Refused 161 bytes from 165.134.13.82
D [24/Sep/2009:17:24:32 -0500] cupsdReadClient: 28 POST / HTTP/1.1
D [24/Sep/2009:17:24:32 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:24:32 -0500] Get-Job-Attributes ipp://localhost/jobs/52
D [24/Sep/2009:17:24:32 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)
D [24/Sep/2009:17:24:32 -0500] cupsdReadClient: 28 POST / HTTP/1.1
D [24/Sep/2009:17:24:32 -0500] cupsdAuthorize: No authentication data provided.
D [24/Sep/2009:17:24:32 -0500] Cancel-Subscription /
D [24/Sep/2009:17:24:32 -0500] cupsdIsAuthorized: requesting-user-name="marks"
I [24/Sep/2009:17:24:32 -0500] Saving subscriptions.conf...
D [24/Sep/2009:17:24:32 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)
D [24/Sep/2009:17:24:32 -0500] cupsdAcceptClient: 33 from localhost (Domain)
D [24/Sep/2009:17:24:32 -0500] cupsdReadClient: 33 GET /admin/log/error_log HTTP/1.1
D [24/Sep/2009:17:24:32 -0500] cupsdAuthorize: No authentication data provided.

The printing troubleshooter apologizes for being unable to work out what the problem is, and offers this diagnostic output:

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest hp_LaserJet_2420 (default)>,
 'cups_instance': None,
 'cups_queue': 'hp_LaserJet_2420',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/hp_LaserJet_2420?serial=CNDJC12254',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP LaserJet 2420 Postscript (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/backend/hp failed',
                       'printer-state-reasons': [u'connecting-to-device'],
                       'printer-type': 168148,
                       'printer-uri-supported': u'ipp://localhost:631/printers/hp_LaserJet_2420'},
 'cups_printer_remote': False,
 'hplip_output': (['',
                   '\x1b[01mHP Linux Imaging and Printing System (ver. 3.9.8)\x1b[0m',
                   '\x1b[01mDevice Information Utility ver. 5.2\x1b[0m',
                   '',
                   'Copyright (c) 2001-9 Hewlett-Packard Development Company, LP',
                   'This software comes with ABSOLUTELY NO WARRANTY.',
                   'This is free software, and you are welcome to distribute it',
                   'under certain conditions. See COPYING file for more details.',
                   '',
                   '',
                   '\x1b[01mhp:/usb/hp_LaserJet_2420?serial=CNDJC12254\x1b[0m',
                   '',
                   '\x1b[01mDevice Parameters (dynamic data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  back-end                      hp                                                        ',
                   '  cups-printers                 hp_LaserJet_2420                                          ',
                   '  cups-uri                      hp:/usb/hp_LaserJet_2420?serial=CNDJC12254                ',
                   '  dev-file                                                                                ',
                   '  device-state                  1                                                         ',
                   '  device-uri                    hp:/usb/hp_LaserJet_2420?serial=CNDJC12254                ',
                   '  deviceid                      MFG:Hewlett-Packard;CMD:PJL,MLC,PCLXL,PCL,PJL,POSTSCRIPT;1',
                   '                                284.4DL:4d,4e,1;MDL:hp LaserJet                           ',
                   '                                2420;CLS:PRINTER;DES:Hewlett-Packard LaserJet 2420;       ',
                   '  duplexer                      1                                                         ',
                   '  error-state                   0                                                         ',
                   '  host                                                                                    ',
                   '  in-tray1                      1                                                         ',
                   '  in-tray2                      1                                                         ',
                   '  is-hp                         True                                                      ',
                   '  media-path                    1                                                         ',
                   '  panel                         0                                                         ',
                   '  panel-line1                                                                             ',
                   '  panel-line2                                                                             ',
                   '  photo-tray                    0                                                         ',
                   '  port                          1                                                         ',
                   '  r                             0                                                         ',
                   '  revision                      254                                                       ',
                   '  rg                            000                                                       ',
                   '  rr                            000000                                                    ',
                   '  rs                            000000000                                                 ',
                   '  serial                        CNDJC12254                                                ',
                   '  status-code                   1000                                                      ',
                   '  status-desc                   Idle                                                      ',
                   '  supply-door                   1                                                         ',
                   '  top-door                      4                                                         ',
                   '\x1b[01m',
                   'Model Parameters (static data):\x1b[0m',
                   '\x1b[01m  Parameter                     Value(s)                                                  \x1b[0m',
                   '  ----------------------------  ----------------------------------------------------------',
                   '  align-type                    0                                                         ',
                   '  clean-type                    0                                                         ',
                   '  color-cal-type                0                                                         ',
                   '  copy-type                     0                                                         ',
                   '  embedded-server-type          1                                                         ',
                   '  fax-type                      0                                                         ',
                   '  fw-download                   False                                                     ',
                   '  icon                          laserjet_2410.png                                         ',
                   '  io-mfp-mode                   3                                                         ',
                   '  io-mode                       6                                                         ',
                   '  io-support                    6                                                         ',
                   '  job-storage                   0                                                         ',
                   '  linefeed-cal-type             0                                                         ',
                   '  model                         hp_LaserJet_2420                                          ',
                   '  model-ui                      HP LaserJet 2420                                          ',
                   '  model1                        HP LaserJet 2420 Printer                                  ',
                   '  model2                        HP LaserJet 2420d Printer                                 ',
                   '  model3                        HP LaserJet 2420dn Printer                                ',
                   '  model4                        HP LaserJet 2420n Printer                                 ',
                   '  monitor-type                  0                                                         ',
                   '  panel-check-type              1                                                         ',
                   '  pcard-type                    0                                                         ',
                   '  plugin                        0                                                         ',
                   '  plugin-reason                 0                                                         ',
                   '  power-settings                0                                                         ',
                   '  pq-diag-type                  0                                                         ',
                   '  r-type                        0                                                         ',
                   '  r0-agent1-kind                4                                                         ',
                   '  r0-agent1-sku                 Q6511A/Q6511X                                             ',
                   '  r0-agent1-type                1                                                         ',
                   '  scan-style                    0                                                         ',
                   '  scan-type                     0                                                         ',
                   '  status-battery-check          0                                                         ',
                   '  status-dynamic-counters       0                                                         ',
                   '  status-type                   3                                                         ',
                   '  support-released              True                                                      ',
                   '  support-subtype               15460                                                     ',
                   '  support-type                  2                                                         ',
                   '  support-ver                   0.9.5                                                     ',
                   "  tech-class                    ['LJMono', 'Postscript']                                  ",
                   "  tech-subclass                 ['Normal']                                                ",
                   '  tech-type                     3                                                         ',
                   '  usb-pid                       10519                                                     ',
                   '  usb-vid                       1008                                                      ',
                   '  wifi-config                   0                                                         ',
                   '\x1b[01m',
                   'Status History (most recent first):\x1b[0m',
                   '\x1b[01m  Date/Time             Code   Status Description                        User      Job ID  \x1b[0m',
                   '  --------------------  -----  ----------------------------------------  --------  --------',
                   '  09/24/09 17:13:47     1000   Idle                                      marks     0       ',
                   '  09/24/09 17:09:07     501    Print job has completed                   marks     50      ',
                   '  09/24/09 17:08:59     500    Started a print job                       marks     50      ',
                   '  09/24/09 17:08:59     1000   Idle                                      marks     0       ',
                   '',
                   '',
                   'Done.',
                   ''],
                  ['\x1b[35;01mwarning: No display found.\x1b[0m',
                   '\x1b[31;01merror: hp-info -u/--gui requires Qt4 GUI support. Entering interactive mode.\x1b[0m',
                   ''],
                  0),
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Collate': u'False',
                                            u'Duplex': u'None',
                                            u'InputSlot': u'Auto',
                                            u'ManualFeed': u'False',
                                            u'MediaType': u'None',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter'},
                               u'HPImagingOptions': {u'HPEconoMode': u'PrinterDefault',
                                                     u'HPHalftone': u'PrinterDefault',
                                                     u'Resolution': u'600x1200dpi',
                                                     u'Smoothing': u'PrinterDefault'},
                               u'HPJobRetention': {u'HPJobName': u'DocName',
                                                   u'HPJobRetentionOption': u'HPJobRetentionOff',
                                                   u'HPUserName': u'FileSharingName'},
                               u'HPWaterMarks': {u'HPwmBrightness': u'Medium',
                                                 u'HPwmFontName': u'HelveticaB',
                                                 u'HPwmFontSize': u'pt48',
                                                 u'HPwmPages': u'AllPages',
                                                 u'HPwmSwitch': u'Off',
                                                 u'HPwmTextAngle': u'Deg45',
                                                 u'HPwmTextMessage': u'Draft',
                                                 u'HPwmTextStyle': u'Medium'},
                               u'InstallableOptions': {u'HPOption_Duplexer': u'False',
                                                       u'HPPaperPolicy': u'PromptUser',
                                                       u'InstalledMemory': u'Mem32_47'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Hewlett-Packard;MDL:hp LaserJet 2420;CLS:PRINTER;DES:hp LaserJet 2420;SN:CNDJC12254;',
                      'device-info': u'HP LaserJet 2420 USB CNDJC12254 HPLIP',
                      'device-make-and-model': u'HP LaserJet 2420'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/backend/hp failed',
 'printer-state-reasons': [u'connecting-to-device']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '2000000',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 42174,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_attempted': '24/Sep/2009:17:23:15 +0000',
 'test_page_job_id': [52],
 'test_page_job_status': [(False,
                           51,
                           'hp_LaserJet_2420',
                           't',
                           'Canceled',
                           None),
                          (True,
                           52,
                           'hp_LaserJet_2420',
                           'Test Page',
                           'Held',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'22:28:54',
                            'job-id': 52,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 1,
                            'job-more-info': u'ipp://localhost:631/jobs/52',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'marks',
                            'job-printer-state-message': u'/usr/lib/cups/backend/hp failed',
                            'job-printer-state-reasons': [u'connecting-to-device'],
                            'job-printer-up-time': 1253831072,
                            'job-printer-uri': u'ipp://ubuntu:631/printers/hp_LaserJet_2420',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 4,
                            'job-state-reasons': u'job-hold-until-specified',
                            'job-uri': u'ipp://localhost:631/jobs/52',
                            'job-uuid': u'urn:uuid:b24c94fd-d248-3cd5-654a-926bbc2432fb',
                            'printer-uri': u'ipp://localhost/printers/hp_LaserJet_2420',
                            'time-at-completed': None,
                            'time-at-creation': 1253830995,
                            'time-at-processing': 1253830995})],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [24/Sep/2009:17:22:27 -0500] update_cups_browse: Refused 184 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:22:27 -0500] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:27 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:27 -0500] Get-Jobs ipp://localhost/printers/',
               'D [24/Sep/2009:17:22:27 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:27 -0500] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:27 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:27 -0500] Get-Jobs ipp://localhost/printers/',
               'D [24/Sep/2009:17:22:27 -0500] [Job 32] Loading attributes...',
               'D [24/Sep/2009:17:22:27 -0500] [Job 41] Loading attributes...',
               'D [24/Sep/2009:17:22:27 -0500] [Job 42] Loading attributes...',
               'D [24/Sep/2009:17:22:27 -0500] [Job 50] Loading attributes...',
               'D [24/Sep/2009:17:22:27 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:27 -0500] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:27 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:27 -0500] Create-Printer-Subscription /',
               'D [24/Sep/2009:17:22:27 -0500] cupsdCreateSubscription(con=0x7fc3de01ae10(28), uri="/")',
               'D [24/Sep/2009:17:22:27 -0500] pullmethod="ippget"',
               'D [24/Sep/2009:17:22:27 -0500] notify-lease-duration=86400',
               'D [24/Sep/2009:17:22:27 -0500] notify-time-interval=0',
               'D [24/Sep/2009:17:22:27 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [24/Sep/2009:17:22:27 -0500] Added subscription 34 for server',
               'I [24/Sep/2009:17:22:27 -0500] Saving subscriptions.conf...',
               'D [24/Sep/2009:17:22:27 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:28 -0500] update_cups_browse: Refused 161 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:22:28 -0500] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:28 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:28 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:22:28 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:22:28 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)',
               'I [24/Sep/2009:17:22:51 -0500] Saving subscriptions.conf...',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] job-sheets=none,none',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] banner_page = 0',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[0]="hp_LaserJet_2420"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[1]="51"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[2]="marks"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[3]="t"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[4]="1"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[5]="media=Letter sides=one-sided finishings=3 number-up=1 job-uuid=urn:uuid:ddbb3f45-2c13-3e35-7ce4-4c3417c7efd3"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] argv[6]="/var/spool/cups/d00051-001"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[9]="SERVER_ADMIN=root@ubuntu"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[12]="TZ=America/Chicago"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[13]="USER=root"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[16]="IPP_PORT=631"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[17]="CHARSET=utf-8"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[18]="LANG=en_US.UTF8"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[19]="PPD=/etc/cups/ppd/hp_LaserJet_2420.ppd"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[20]="RIP_MAX_CACHE=8m"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[21]="CONTENT_TYPE=text/plain"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[22]="DEVICE_URI=hp:/usb/hp_LaserJet_2420?serial=CNDJC12254"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[23]="PRINTER=hp_LaserJet_2420"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] envp[24]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"',
               'I [24/Sep/2009:17:22:51 -0500] [Job 51] Started filter /usr/lib/cups/filter/texttopdf (PID 16593)',
               'I [24/Sep/2009:17:22:51 -0500] [Job 51] Started filter /usr/lib/cups/filter/pdftopdf (PID 16594)',
               'I [24/Sep/2009:17:22:51 -0500] [Job 51] Started filter /usr/lib/cups/filter/cpdftocps (PID 16595)',
               'I [24/Sep/2009:17:22:51 -0500] [Job 51] Started backend /usr/lib/cups/backend/hp (PID 16596)',
               'I [24/Sep/2009:17:22:51 -0500] Saving subscriptions.conf...',
               'D [24/Sep/2009:17:22:51 -0500] PID 16593 (/usr/lib/cups/filter/texttopdf) exited with no errors.',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] Page = 612x792; 12,12 to 600,780',
               'D [24/Sep/2009:17:22:51 -0500] PID 16594 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] Device copies: 1; device collate:',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] pdftops - copying to temp print file "/tmp/4abbf13b70f9d"',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] Page = 612x792; 12,12 to 600,780',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] slow_collate=0, slow_duplex=0, slow_order=0',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] Before copy_comments - %!PS-Adobe-3.0',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] %!PS-Adobe-3.0',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] %%LanguageLevel: 2',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] %%DocumentSuppliedResources: (atend)',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] %%DocumentMedia: plain 612 792 0 () ()',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] %%BoundingBox: 0 0 612 792',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] %%Pages: 1',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] %%EndComments',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] Before copy_prolog - %%BeginDefaults',
               'I [24/Sep/2009:17:22:51 -0500] Saving subscriptions.conf...',
               'D [24/Sep/2009:17:22:51 -0500] [Job 51] Before copy_setup - %%BeginSetup',
               'D [24/Sep/2009:17:22:51 -0500] cupsdAcceptClient: 30 from localhost (Domain)',
               'D [24/Sep/2009:17:22:51 -0500] cupsdAcceptClient: 32 from localhost (Domain)',
               'D [24/Sep/2009:17:22:51 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:51 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:51 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:22:51 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:22:51 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:51 -0500] cupsdReadClient: 32 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:51 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:51 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:22:51 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:22:51 -0500] cupsdProcessIPPRequest: 32 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:51 -0500] cupsdCloseClient: 32',
               'D [24/Sep/2009:17:22:51 -0500] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:51 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:51 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:22:51 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:22:51 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:51 -0500] cupsdCloseClient: 30',
               'D [24/Sep/2009:17:22:52 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:22:54 -0500] cupsdAcceptClient: 30 from localhost (Domain)',
               'D [24/Sep/2009:17:22:54 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:54 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:54 -0500] CUPS-Get-Printers',
               'D [24/Sep/2009:17:22:54 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:54 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:54 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:54 -0500] CUPS-Get-Classes',
               'D [24/Sep/2009:17:22:54 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:54 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:54 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:54 -0500] CUPS-Get-Default',
               'D [24/Sep/2009:17:22:54 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:54 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:54 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:54 -0500] Get-Printer-Attributes ipp://localhost/printers/hp_LaserJet_2420',
               'D [24/Sep/2009:17:22:54 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:54 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:54 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:54 -0500] Get-Jobs ipp://localhost/printers/hp_LaserJet_2420',
               'D [24/Sep/2009:17:22:54 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:54 -0500] cupsdCloseClient: 30',
               'D [24/Sep/2009:17:22:56 -0500] cupsdAcceptClient: 30 from localhost (Domain)',
               'D [24/Sep/2009:17:22:56 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:56 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:56 -0500] CUPS-Get-Printers',
               'D [24/Sep/2009:17:22:56 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:56 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:56 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:56 -0500] CUPS-Get-Classes',
               'D [24/Sep/2009:17:22:56 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:56 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:22:56 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:56 -0500] CUPS-Get-Default',
               'D [24/Sep/2009:17:22:56 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:22:56 -0500] cupsdReadClient: 30 POST /jobs/ HTTP/1.1',
               'D [24/Sep/2009:17:22:56 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:22:56 -0500] Cancel-Job ipp://localhost/printers/t',
               'D [24/Sep/2009:17:22:56 -0500] Cancel-Job client-error-not-found: The printer or class was not found.',
               'D [24/Sep/2009:17:22:56 -0500] cupsdProcessIPPRequest: 30 status_code=406 (client-error-not-found)',
               'D [24/Sep/2009:17:22:56 -0500] cupsdCloseClient: 30',
               'D [24/Sep/2009:17:22:57 -0500] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [24/Sep/2009:17:22:57 -0500] cupsdNetIFUpdate: "eth0" = 165.134.13.82:631',
               'D [24/Sep/2009:17:22:57 -0500] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [24/Sep/2009:17:22:57 -0500] cupsdNetIFUpdate: "eth0" = fe80::226:55ff:fef4:2b69%eth0:631',
               'D [24/Sep/2009:17:22:57 -0500] cupsdNetIFUpdate: "wlan0" = fe80::221:6aff:fe67:9152%wlan0:631',
               'D [24/Sep/2009:17:22:57 -0500] update_cups_browse: Refused 172 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:22:58 -0500] update_cups_browse: Refused 184 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:22:59 -0500] update_cups_browse: Refused 161 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:23:01 -0500] cupsdAcceptClient: 30 from localhost (Domain)',
               'D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:01 -0500] CUPS-Get-Printers',
               'D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:01 -0500] CUPS-Get-Classes',
               'D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:01 -0500] CUPS-Get-Default',
               'D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 30 POST /jobs/ HTTP/1.1',
               'D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:01 -0500] Cancel-Job ipp://localhost/jobs/51',
               'D [24/Sep/2009:17:23:01 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'I [24/Sep/2009:17:23:01 -0500] Saving subscriptions.conf...',
               'I [24/Sep/2009:17:23:01 -0500] Saving subscriptions.conf...',
               'I [24/Sep/2009:17:23:01 -0500] [Job 51] Canceled by "marks".',
               'D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:01 -0500] cupsdCloseClient: 30',
               'D [24/Sep/2009:17:23:01 -0500] cupsdAcceptClient: 30 from localhost (Domain)',
               'D [24/Sep/2009:17:23:01 -0500] cupsdAcceptClient: 32 from localhost (Domain)',
               'D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:01 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:01 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 32 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:01 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:01 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 32 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:01 -0500] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:01 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:01 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:01 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:01 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:01 -0500] cupsdCloseClient: 32',
               'D [24/Sep/2009:17:23:01 -0500] cupsdCloseClient: 30',
               'D [24/Sep/2009:17:23:02 -0500] cupsdAcceptClient: 30 from localhost (Domain)',
               'D [24/Sep/2009:17:23:02 -0500] [Job 51] Unloading...',
               'D [24/Sep/2009:17:23:02 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:23:02 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:02 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:02 -0500] CUPS-Get-Printers',
               'D [24/Sep/2009:17:23:02 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:02 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:02 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:02 -0500] CUPS-Get-Classes',
               'D [24/Sep/2009:17:23:02 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:02 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:02 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:02 -0500] CUPS-Get-Default',
               'D [24/Sep/2009:17:23:02 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:02 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:02 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:02 -0500] Get-Printer-Attributes ipp://localhost/printers/hp_LaserJet_2420',
               'D [24/Sep/2009:17:23:02 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:02 -0500] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:02 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:02 -0500] Get-Jobs ipp://localhost/printers/hp_LaserJet_2420',
               'D [24/Sep/2009:17:23:02 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:02 -0500] cupsdCloseClient: 30',
               'D [24/Sep/2009:17:23:12 -0500] cupsdReadClient: 28 POST /jobs/ HTTP/1.1',
               'D [24/Sep/2009:17:23:12 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:12 -0500] Cancel-Job ipp://localhost/jobs/51',
               'D [24/Sep/2009:17:23:12 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               "D [24/Sep/2009:17:23:12 -0500] Cancel-Job client-error-not-possible: Job #51 is already canceled - can't cancel.",
               'D [24/Sep/2009:17:23:12 -0500] cupsdProcessIPPRequest: 28 status_code=404 (client-error-not-possible)',
               'D [24/Sep/2009:17:23:15 -0500] cupsdAcceptClient: 30 from localhost (Domain)',
               'D [24/Sep/2009:17:23:15 -0500] cupsdReadClient: 30 POST /printers/hp_LaserJet_2420 HTTP/1.1',
               'D [24/Sep/2009:17:23:15 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:15 -0500] Print-Job ipp://localhost/printers/hp_LaserJet_2420',
               'D [24/Sep/2009:17:23:15 -0500] [Job ???] Auto-typing file...',
               'I [24/Sep/2009:17:23:15 -0500] [Job ???] Request file type is application/postscript.',
               'D [24/Sep/2009:17:23:15 -0500] add_job: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:15 -0500] Adding default job-sheets values "none,none"...',
               'I [24/Sep/2009:17:23:15 -0500] [Job 52] Adding start banner page "none".',
               'I [24/Sep/2009:17:23:15 -0500] Saving subscriptions.conf...',
               'I [24/Sep/2009:17:23:15 -0500] [Job 52] Adding end banner page "none".',
               'I [24/Sep/2009:17:23:15 -0500] [Job 52] File of type application/postscript queued by "marks".',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] hold_until=0',
               'I [24/Sep/2009:17:23:15 -0500] [Job 52] Queued on "hp_LaserJet_2420" by "marks".',
               'I [24/Sep/2009:17:23:15 -0500] Saving subscriptions.conf...',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] job-sheets=none,none',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] banner_page = 0',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[0]="hp_LaserJet_2420"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[1]="52"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[2]="marks"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[3]="Test Page"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[4]="1"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[5]="job-uuid=urn:uuid:b24c94fd-d248-3cd5-654a-926bbc2432fb"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] argv[6]="/var/spool/cups/d00052-001"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[9]="SERVER_ADMIN=root@ubuntu"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[12]="TZ=America/Chicago"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[13]="USER=root"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[16]="IPP_PORT=631"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[17]="CHARSET=utf-8"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[18]="LANG=en_US.UTF8"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[19]="PPD=/etc/cups/ppd/hp_LaserJet_2420.ppd"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[20]="RIP_MAX_CACHE=8m"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[22]="DEVICE_URI=hp:/usb/hp_LaserJet_2420?serial=CNDJC12254"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[23]="PRINTER=hp_LaserJet_2420"',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] envp[24]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"',
               'I [24/Sep/2009:17:23:15 -0500] [Job 52] Started filter /usr/lib/cups/filter/pstopdf (PID 16630)',
               'I [24/Sep/2009:17:23:15 -0500] [Job 52] Started filter /usr/lib/cups/filter/pdftopdf (PID 16632)',
               'I [24/Sep/2009:17:23:15 -0500] [Job 52] Started filter /usr/lib/cups/filter/cpdftocps (PID 16633)',
               'I [24/Sep/2009:17:23:15 -0500] [Job 52] Started backend /usr/lib/cups/backend/hp (PID 16637)',
               'I [24/Sep/2009:17:23:15 -0500] Saving subscriptions.conf...',
               'D [24/Sep/2009:17:23:15 -0500] cupsdProcessIPPRequest: 30 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] pstopdf 6 args: 52 marks Test Page 1 job-uuid=urn:uuid:b24c94fd-d248-3cd5-654a-926bbc2432fb /var/spool/cups/d00052-001',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] PPD: /etc/cups/ppd/hp_LaserJet_2420.ppd',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] Resolution: 600x1200',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] Page size: Letter',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] Width: 612, height: 792, absolute margins: 12.00, 12.12, 599.88, 780.00',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] Relative margins: 12.00, 12.12, 12.12, 12.00',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] PPD options: -r600x1200 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] PostScript to be injected:',
               'D [24/Sep/2009:17:23:15 -0500] [Job 52] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dDoNumCopies -dPDFSETTINGS=/printer -r600x1200 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -',
               'D [24/Sep/2009:17:23:16 -0500] cupsdAcceptClient: 32 from localhost (Domain)',
               'D [24/Sep/2009:17:23:16 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 32 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:16 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 32 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:16 -0500] cupsdAcceptClient: 33 from localhost (Domain)',
               'D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 33 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:16 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 32 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:16 -0500] Get-Job-Attributes ipp://localhost/jobs/52',
               'D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 32 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:16 -0500] cupsdCloseClient: 33',
               'D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:16 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:16 -0500] cupsdCloseClient: 32',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] GPL Ghostscript 8.64: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [24/Sep/2009:17:23:16 -0500] PID 16630 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [24/Sep/2009:17:23:16 -0500] PID 16632 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] Device copies: 1; device collate:',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] pdftops - copying to temp print file "/tmp/4abbf15457bac"',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] Page = 612x792; 12,12 to 600,780',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] slow_collate=0, slow_duplex=0, slow_order=0',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] Before copy_comments - %!PS-Adobe-3.0',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] %!PS-Adobe-3.0',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] %%LanguageLevel: 2',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] %%DocumentSuppliedResources: (atend)',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] %%DocumentMedia: plain 612 792 0 () ()',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] %%BoundingBox: 0 0 612 792',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] %%Pages: 1',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] %%EndComments',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] Before copy_prolog - %%BeginDefaults',
               'I [24/Sep/2009:17:23:16 -0500] Saving subscriptions.conf...',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] Before copy_setup - %%BeginSetup',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] Before page loop - %%Page: 1 1',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] Copying page 1...',
               'I [24/Sep/2009:17:23:16 -0500] Saving subscriptions.conf...',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] pagew = 587.9, pagel = 767.9',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] PageLeft = 12.0, PageRight = 599.9',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] PageTop = 780.0, PageBottom = 12.1',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] PageWidth = 612.0, PageLength = 792.0',
               'D [24/Sep/2009:17:23:16 -0500] [Job 52] prnt/backend/hp.c 727: INFO: open device failed stat=21; will retry in 30 seconds...',
               'D [24/Sep/2009:17:23:16 -0500] cupsdAcceptClient: 33 from localhost (Domain)',
               'D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 33 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:16 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:16 -0500] cupsdAcceptClient: 35 from localhost (Domain)',
               'D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 35 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:16 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 35 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:16 -0500] cupsdCloseClient: 33',
               'D [24/Sep/2009:17:23:16 -0500] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:16 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:16 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:16 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:16 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:16 -0500] cupsdCloseClient: 35',
               'D [24/Sep/2009:17:23:22 -0500] cupsdAcceptClient: 33 from localhost (Domain)',
               'D [24/Sep/2009:17:23:22 -0500] Report: clients=3',
               'D [24/Sep/2009:17:23:22 -0500] Report: jobs=8',
               'D [24/Sep/2009:17:23:22 -0500] Report: jobs-active=3',
               'D [24/Sep/2009:17:23:22 -0500] Report: printers=4',
               'D [24/Sep/2009:17:23:22 -0500] Report: printers-implicit=0',
               'D [24/Sep/2009:17:23:22 -0500] Report: stringpool-string-count=4830',
               'D [24/Sep/2009:17:23:22 -0500] Report: stringpool-alloc-bytes=15520',
               'D [24/Sep/2009:17:23:22 -0500] Report: stringpool-total-bytes=104824',
               'D [24/Sep/2009:17:23:22 -0500] cupsdReadClient: 33 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:22 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:22 -0500] CUPS-Get-Printers',
               'D [24/Sep/2009:17:23:22 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:22 -0500] cupsdReadClient: 33 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:22 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:22 -0500] CUPS-Get-Classes',
               'D [24/Sep/2009:17:23:22 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:22 -0500] cupsdReadClient: 33 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:22 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:22 -0500] CUPS-Get-Default',
               'D [24/Sep/2009:17:23:22 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:22 -0500] cupsdReadClient: 33 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:22 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:22 -0500] Get-Printer-Attributes ipp://localhost/printers/hp_LaserJet_2420',
               'D [24/Sep/2009:17:23:22 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:22 -0500] cupsdReadClient: 33 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:22 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:22 -0500] Get-Jobs ipp://localhost/printers/hp_LaserJet_2420',
               'D [24/Sep/2009:17:23:22 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:22 -0500] cupsdCloseClient: 33',
               'D [24/Sep/2009:17:23:28 -0500] [Job 32] Unloading...',
               'D [24/Sep/2009:17:23:28 -0500] [Job 41] Unloading...',
               'D [24/Sep/2009:17:23:28 -0500] [Job 42] Unloading...',
               'D [24/Sep/2009:17:23:28 -0500] [Job 50] Unloading...',
               'D [24/Sep/2009:17:23:28 -0500] update_cups_browse: Refused 172 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:23:29 -0500] update_cups_browse: Refused 184 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:23:30 -0500] update_cups_browse: Refused 161 bytes from 165.134.13.82',
               'E [24/Sep/2009:17:23:36 -0500] PID 16596 (/usr/lib/cups/backend/hp) stopped with status 1!',
               'D [24/Sep/2009:17:23:36 -0500] PID 16595 (/usr/lib/cups/filter/cpdftocps) exited with no errors.',
               'D [24/Sep/2009:17:23:47 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:23:54 -0500] [Job 52] prnt/backend/hp.c 743: ERROR: cannot open channel PRINT',
               'E [24/Sep/2009:17:23:54 -0500] PID 16637 (/usr/lib/cups/backend/hp) stopped with status 1!',
               'D [24/Sep/2009:17:23:54 -0500] [Job 52] Wrote 1 pages...',
               'D [24/Sep/2009:17:23:54 -0500] PID 16633 (/usr/lib/cups/filter/cpdftocps) exited with no errors.',
               'D [24/Sep/2009:17:23:54 -0500] [Job 52] File 0 is complete.',
               'I [24/Sep/2009:17:23:54 -0500] [Job 52] Backend returned status 1 (failed)',
               'I [24/Sep/2009:17:23:54 -0500] Saving subscriptions.conf...',
               'D [24/Sep/2009:17:23:54 -0500] set_hold_until: hold_until = 1253831334',
               'I [24/Sep/2009:17:23:54 -0500] Saving subscriptions.conf...',
               'D [24/Sep/2009:17:23:54 -0500] cupsdAcceptClient: 33 from localhost (Domain)',
               'D [24/Sep/2009:17:23:54 -0500] cupsdAcceptClient: 35 from localhost (Domain)',
               'D [24/Sep/2009:17:23:54 -0500] cupsdReadClient: 33 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:54 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:54 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:54 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:54 -0500] cupsdProcessIPPRequest: 33 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:54 -0500] cupsdReadClient: 35 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:54 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:54 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:54 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:54 -0500] cupsdProcessIPPRequest: 35 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:54 -0500] cupsdCloseClient: 35',
               'D [24/Sep/2009:17:23:54 -0500] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:54 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:54 -0500] Get-Notifications /',
               'D [24/Sep/2009:17:23:54 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'D [24/Sep/2009:17:23:54 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:54 -0500] cupsdAcceptClient: 35 from localhost (Domain)',
               'D [24/Sep/2009:17:23:54 -0500] cupsdReadClient: 35 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:54 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:54 -0500] Get-Printer-Attributes ipp://ubuntu:631/printers/hp_LaserJet_2420',
               'D [24/Sep/2009:17:23:54 -0500] cupsdProcessIPPRequest: 35 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:54 -0500] cupsdReadClient: 35 POST / HTTP/1.1',
               'D [24/Sep/2009:17:23:54 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:23:54 -0500] Get-Job-Attributes ipp://localhost/jobs/52',
               'D [24/Sep/2009:17:23:54 -0500] cupsdProcessIPPRequest: 35 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:23:54 -0500] cupsdCloseClient: 33',
               'D [24/Sep/2009:17:23:55 -0500] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [24/Sep/2009:17:23:55 -0500] cupsdNetIFUpdate: "eth0" = 165.134.13.82:631',
               'D [24/Sep/2009:17:23:55 -0500] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [24/Sep/2009:17:23:55 -0500] cupsdNetIFUpdate: "eth0" = fe80::226:55ff:fef4:2b69%eth0:631',
               'D [24/Sep/2009:17:23:55 -0500] cupsdNetIFUpdate: "wlan0" = fe80::221:6aff:fe67:9152%wlan0:631',
               'D [24/Sep/2009:17:23:55 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:23:59 -0500] update_cups_browse: Refused 172 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:24:00 -0500] update_cups_browse: Refused 184 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:24:01 -0500] update_cups_browse: Refused 161 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:24:24 -0500] Report: clients=3',
               'D [24/Sep/2009:17:24:24 -0500] Report: jobs=8',
               'D [24/Sep/2009:17:24:24 -0500] Report: jobs-active=3',
               'D [24/Sep/2009:17:24:24 -0500] Report: printers=4',
               'D [24/Sep/2009:17:24:24 -0500] Report: printers-implicit=0',
               'D [24/Sep/2009:17:24:24 -0500] Report: stringpool-string-count=4779',
               'D [24/Sep/2009:17:24:24 -0500] Report: stringpool-alloc-bytes=15040',
               'D [24/Sep/2009:17:24:24 -0500] Report: stringpool-total-bytes=104312',
               'D [24/Sep/2009:17:24:26 -0500] update_cups_browse: Refused 148 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:24:30 -0500] update_cups_browse: Refused 172 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:24:31 -0500] update_cups_browse: Refused 184 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:24:32 -0500] update_cups_browse: Refused 161 bytes from 165.134.13.82',
               'D [24/Sep/2009:17:24:32 -0500] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [24/Sep/2009:17:24:32 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:24:32 -0500] Get-Job-Attributes ipp://localhost/jobs/52',
               'D [24/Sep/2009:17:24:32 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:24:32 -0500] cupsdReadClient: 28 POST / HTTP/1.1',
               'D [24/Sep/2009:17:24:32 -0500] cupsdAuthorize: No authentication data provided.',
               'D [24/Sep/2009:17:24:32 -0500] Cancel-Subscription /',
               'D [24/Sep/2009:17:24:32 -0500] cupsdIsAuthorized: requesting-user-name="marks"',
               'I [24/Sep/2009:17:24:32 -0500] Saving subscriptions.conf...',
               'D [24/Sep/2009:17:24:32 -0500] cupsdProcessIPPRequest: 28 status_code=0 (successful-ok)',
               'D [24/Sep/2009:17:24:32 -0500] cupsdAcceptClient: 33 from localhost (Domain)',
               'D [24/Sep/2009:17:24:32 -0500] cupsdReadClient: 33 GET /admin/log/error_log HTTP/1.1',
               'D [24/Sep/2009:17:24:32 -0500] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 11 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

Where do I go from here?

---

### Post by drs305 on 2009-09-24
gtmarks,

I have moved on to Karmic. I initially had problems getting the HP1000 working in Karmic but this worked:

Uninstall al[QUOTE]l CUPS and HP references in Synaptic (hplip, cups, cups-common, cupsys, etc)
Install hplip - this will also install CUPS
Add the printer via the CUPS window in a browser ([http://localhost:631/](http://localhost:631/))

I then had to disconnect and reconnect the printer and recycle the power, but eventually got it working via this method.

---

### Post by gtmarks on 2009-09-24
Greetings, drs305!

Thank you for your suggestion.  When I return to work, where the computer is located, I'll try it; however, my recollection is that I already tried uninstalling and installing CUPS/HP packages in Synaptic.  Have definitely tried deleting, adding, reconfiguring the printer via localhost:631, as well as restarting printer and computer.

One possibly relevant note is that I am able to print with no problem to the other printers in my local network; I just can't print to the one in my office (which is the one I really need to use), which is connected via USB.  As suggested in my previous post, the computer certainly seems to recognize that the USB connection exists and even seems to think things are printing, but nothing comes out of the printer.

The USB connector is functional; when I hook it up to a different laptop (Mac OS X) it prints with no problem.

---

### Post by drs305 on 2009-09-24
> **gtmarks said:**
> Greetings, drs305!

Thank you for your suggestion. 

My computer also could see the printer as a USB device, and often would print a blank page or say the print job was completed without actually doing anything. 

Eventually the HPLIP setup started working. IIRC, sometimes it would automatically select the printer and other times I had to manually set it up via CUPS. Even after I got it working I sometimes have to recycle the power or disconnect/reconnect the USB connection to get it to work. Also clearing out any 'hung' print jobs, which sometimes prevented a more recent print job from starting.

Good luck - hope you get your's working.

---

### Post by gtmarks on 2009-09-25
I'd rather not try this:

>  Uninstall all CUPS and HP references in Synaptic (hplip, cups, cups-common, 
> cupsys, etc)

For example, removing cups in Synaptic entails removal of ubuntu-desktop, which I certainly don't want to remove.

I ran another test on the printer.  Do the following log files shed any light on the problem?

hp-check[8589]: info: :
Initializing. Please wait...
Ubuntu 

9.04 

scheduler is running 

1.3.9 

Linux ubuntu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux 

hp-check[8589]: info: :
hp-check[8589]: info: :---------------
hp-check[8589]: info: :| SYSTEM INFO |
hp-check[8589]: info: :---------------
hp-check[8589]: info: :
hp-check[8589]: info: :Basic system information:
hp-check[8589]: info: :Linux ubuntu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux 
hp-check[8589]: info: :
hp-check[8589]: info: :Distribution:
hp-check[8589]: info: :ubuntu 9.04
hp-check[8589]: info: :
hp-check[8589]: info: :Checking Python version...
hp-check[8589]: info: :OK, version 2.6.2 installed
hp-check[8589]: info: :
hp-check[8589]: info: :Checking PyQt 4.x version...
hp-check[8589]: info: :OK, version 4.4.4 installed.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for CUPS...
hp-check[8589]: info: :Status: scheduler is running
hp-check[8589]: info: :Version: 1.3.9
hp-check[8589]: info: :error_log is set to level: info
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dbus/python-dbus...
hp-check[8589]: info: :dbus daemon is running.
hp-check[8589]: info: :python-dbus version: 0.83.0
hp-check[8589]: info: :
hp-check[8589]: info: :
hp-check[8589]: info: :------------------------------------
hp-check[8589]: info: :| COMPILE AND RUNTIME DEPENDENCIES |
hp-check[8589]: info: :------------------------------------
hp-check[8589]: info: :
note: To check for compile-time only dependencies, re-run hp-check with the -c parameter (ie, hp-check -c).
note: To check for run-time only dependencies, re-run hp-check with the -r parameter (ie, hp-check -r).
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: CUPS - Common Unix Printing System...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: CUPS DDK - CUPS driver development kit...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: CUPS devel- Common Unix Printing System development files...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: CUPS image - CUPS image development files...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: DBus - Message bus system...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: gcc - GNU Project C and C++ Compiler...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: libcrypto - OpenSSL cryptographic library...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: libjpeg - JPEG library...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: libpthread - POSIX threads library...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: libtool - Library building support services...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: libusb - USB library...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: make - GNU make utility to maintain groups of programs...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: PolicyKit - Administrative policy framework...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: PyQt 4 DBus - DBus Support for PyQt4...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: Python DBus - Python bindings for DBus...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: Python devel - Python development files...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: Python libnotify - Python bindings for the libnotify Desktop notifications...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: Python XML libraries...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: Python 2.3 or greater - Required for fax functionality...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: Python 2.2 or greater - Python programming language...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: Reportlab - PDF library for Python...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: SANE - Scanning library...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: SANE - Scanning library development files...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: scanimage - Shell scanning program...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for dependency: xsane - Graphical scanner frontend for SANE...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :
hp-check[8589]: info: :----------------------
hp-check[8589]: info: :| HPLIP INSTALLATION |
hp-check[8589]: info: :----------------------
hp-check[8589]: info: :
hp-check[8589]: info: :
hp-check[8589]: info: :Currently installed HPLIP version...
hp-check[8589]: info: :HPLIP 3.9.8 currently installed in '/usr/share/hplip'.
hp-check[8589]: info: :
hp-check[8589]: info: :Current contents of '/etc/hp/hplip.conf' file:
hp-check[8589]: info: :# hplip.conf.  Generated from hplip.conf.in by configure.

[hplip]
version=3.9.8

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-3.9.8
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
cupsfilter=/usr/lib/cups/filter
drv=/usr/share/cups/drv/hp

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
dbus-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
hpijs-install=no
foomatic-drv-install=no
foomatic-ppd-install=no
foomatic-rip-hplip-install=no
hpcups-install=yes
cups-drv-install=yes
cups-ppd-install=no
internal-tag=3.9.8.36
restricted-build=no
ui-toolkit=qt4
qt3=no
qt4=yes
policy-kit=yes
hpijs-only-build=no
lite-build=no
udev-acl-rules=no

hp-check[8589]: info: :
hp-check[8589]: info: :Current contents of '/var/lib/hp/hplip.state' file:
hp-check[8589]: info: :# hplip.state - HPLIP runtime persistent variables. 

[plugin]
installed=0
eula=0


hp-check[8589]: info: :
hp-check[8589]: info: :Current contents of '~/.hplip/hplip.conf' file:
hp-check[8589]: info: :[last_used]
printer_name = 
printer = 
working_dir = .
device_uri = "hp:/usb/hp_LaserJet_2420?serial=CNDJC12254"

[commands]
scan = /usr/bin/xsane -V %SANE_URI%

[installation]
version = 3.9.8.36
date_time = 09/25/2009 15:31:26

[settings]
systray_messages = 0
systray_visible = 1

[fax]
email_address = 
voice_phone = 

[refresh]
rate = 30
enable = false
type = 1

[polling]
enable = false
device_list = 
interval = 5


hp-check[8589]: info: :
hp-check[8589]: info: :--------------------------
hp-check[8589]: info: :| DISCOVERED USB DEVICES |
hp-check[8589]: info: :--------------------------
hp-check[8589]: info: :
hp-check[8589]: info: :  Device URI                        Model           
hp-check[8589]: info: :  --------------------------------  ----------------
hp-check[8589]: info: :  hp:/usb/hp_LaserJet_2420?serial=  HP LaserJet 2420
  CNDJC12254                                        
hp-check[8589]: info: :
hp-check[8589]: info: :---------------------------------
hp-check[8589]: info: :| INSTALLED CUPS PRINTER QUEUES |
hp-check[8589]: info: :---------------------------------
hp-check[8589]: info: :
hp-check[8589]: info: :
hp-check[8589]: info: :Color-LaserJet-CP3525
hp-check[8589]: info: :---------------------
hp-check[8589]: info: :Type: Printer
hp-check[8589]: info: :Device URI: hp:/net/HP_Color_LaserJet_CP3525?ip=165.134.13.111
hp-check[8589]: info: :PPD: /etc/cups/ppd/Color-LaserJet-CP3525.ppd
hp-check[8589]: info: :PPD Description: HP Color LaserJet cp3525 pcl3, hpcups 3.9.8
hp-check[8589]: info: :Printer status: printer Color-LaserJet-CP3525 is idle.  enabled since Thu 24 Sep 2009 06:22:52 PM CDT 
hp-check[8589]: info: :Communication status: Good
hp-check[8589]: info: :
hp-check[8589]: info: :hp-LaserJet-2420
hp-check[8589]: info: :----------------
hp-check[8589]: info: :Type: Printer
hp-check[8589]: info: :Device URI: hp:/usb/hp_LaserJet_2420?serial=CNDJC12254
hp-check[8589]: info: :PPD: /etc/cups/ppd/hp-LaserJet-2420.ppd
hp-check[8589]: info: :PPD Description: HP LaserJet 2420 pcl3, hpcups 3.9.8
hp-check[8589]: info: :Printer status: printer hp-LaserJet-2420 now printing hp-LaserJet-2420-0.  enabled since Fri 25 Sep 2009 03:30:04 PM CDT     /usr/lib/cups/backend/hp failed 
hp-check[8589]: info: :Communication status: Good
hp-check[8589]: info: :
hp-check[8589]: info: :MathGradPrinter
hp-check[8589]: info: :---------------
hp-check[8589]: info: :Type: Printer
hp-check[8589]: info: :Device URI: hp:/net/hp_LaserJet_4240?zc=MathGradPrinter
hp-check[8589]: info: :PPD: /etc/cups/ppd/MathGradPrinter.ppd
hp-check[8589]: info: :PPD Description: HP LaserJet 4240 Postscript (recommended)
hp-check[8589]: info: :Printer status: printer MathGradPrinter is idle.  enabled since Thu 24 Sep 2009 06:23:48 PM CDT 
hp-check[8589]: info: :Communication status: Good
hp-check[8589]: info: :
hp-check[8589]: info: :
hp-check[8589]: info: :----------------------
hp-check[8589]: info: :| SANE CONFIGURATION |
hp-check[8589]: info: :----------------------
hp-check[8589]: info: :
hp-check[8589]: info: :'hpaio' in '/etc/sane.d/dll.conf'...
hp-check[8589]: info: :OK, found. SANE backend 'hpaio' is properly set up.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking output of 'scanimage -L'...
hp-check[8589]: info: :device `v4l:/dev/video0' is a Noname CKA7216 virtual device 

hp-check[8589]: info: :
hp-check[8589]: info: :---------------------
hp-check[8589]: info: :| PYTHON EXTENSIONS |
hp-check[8589]: info: :---------------------
hp-check[8589]: info: :
hp-check[8589]: info: :Checking 'cupsext' CUPS extension...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking 'pcardext' Photocard extension...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking 'hpmudext' I/O extension...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :Checking 'scanext' SANE scanning extension...
hp-check[8589]: info: :OK, found.
hp-check[8589]: info: :
hp-check[8589]: info: :
hp-check[8589]: info: :
hp-check[8589]: info: :-----------------
hp-check[8589]: info: :| USB I/O SETUP |
hp-check[8589]: info: :-----------------
hp-check[8589]: info: :
hp-check[8589]: info: :Checking for permissions of USB attached printers...
hp-check[8589]: info: :
HP Device 0x2917 at 002:003: 
hp-check[8589]: info: :    Device URI: hp:/usb/hp_LaserJet_2420?serial=CNDJC12254
hp-check[8589]: info: :    Device node: /dev/bus/usb/002/003
hp-check[8589]: info: :    Mode: 0660
hp-check[8589]: info: :getfacl: Removing leading '/' from absolute path names 
# file: dev/bus/usb/002/003 
# owner: lp 
# group: lp 
user::rw- 
user:marks:rw- 
group::rw- 
mask::rw- 
other::--- 
 

hp-check[8589]: info: :
HP Device 0x171d at 003:002: 
warning:     Device URI: (Makeuri FAILED)
hp-check[8589]: info: :
hp-check[8589]: info: :---------------
hp-check[8589]: info: :| USER GROUPS |
hp-check[8589]: info: :---------------
hp-check[8589]: info: :
hp-check[8589]: info: :marks adm dialout cdrom plugdev lpadmin admin sambashare 

hp-check[8589]: info: :
hp-check[8589]: info: :-----------
hp-check[8589]: info: :| SUMMARY |
hp-check[8589]: info: :-----------
hp-check[8589]: info: :
hp-check[8589]: info: :No errors or warnings.
hp-check[8589]: info: :
hp-check[8589]: info: :Done.

---

### Post by drs305 on 2009-09-25
Your version of hplip is the same as mine, so the software *can* work with the HP LaserJet-1000.

Other than the fact that the -1000 isn't listed, nothing really pops out. By the way, when pasting large amounts of text it's preferred to place it within code tags (click the # symbol at the top of the post). This greatly reduces the height of the post but still allows viewers to scroll through the entire contents.

I can understand the hesitation in removing ubuntu-desktop. It doesn't uninstall lots of apps as you might imagine, and if you remove cups and reinstall it nothing will be lost. I've done it lots of times but don't do anything you aren't comfortable with.

You could just try reinstalling cups and hplip (sudo apt-get install --reinstall cups hplip), but simple reinstalls generally don't fix things.

Other than those suggestions, it would probably be best to either look for other strings with entries in the past several months or start a new thread. Not too many forumites probably look at an old post with this many responses and also mark SOLVED.

---

### Post by sgosnell on 2009-09-25
I haven't tried that model printer, but I can say that every HP printer I've tried to install worked fine under Linux, although not under Windows.  I just open System/Administration/Printing, click on Add, tell it to add a new printer, and it finds the printer, then offers to install the drivers.  I select HP, the closest model if the actual model isn't shown, and I get a working printer immediately.  For scanning, I add HPLIP, and the scanner works.  I've never had a problem of any kind with an HP printer under Ubuntu, even a couple that I never got to scan under Windows even after hours on the phone to India and being sent new install CDs.  It just won't work under Windows XP, but under Ubuntu everything works fine.

---

### Post by gtmarks on 2009-09-25
Sorry about the lengthy log file posts.  I'll put them between pound symbols next time.

Actually, my printer is not the HP 1000.  (Sorry again; I found this thread by Googling my error message and didn't notice until too late that my model number was different.)  The printer that's been giving me problems is an HP LaserJet 2420.  However, I just tried printing (from the same computer via USB) to an HP LaserJet 3052 and had no difficulty whatsoever: I plugged it in, in about five seconds Ubuntu detected it, and documents printed.  So it would seem Ubuntu is performing just fine; my problem is presumably an antiquated printer.

Synaptic gave me some sort of stern warning about uninstalling ubuntu-desktop--I had visions of having nothing left above BIOS level--but I'm relieved to hear it's safe to do.  In my case it's a moot point, though.

I am grateful for all of your helpful advice.

---

