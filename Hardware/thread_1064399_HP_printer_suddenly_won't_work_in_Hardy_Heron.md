---
title: "HP printer suddenly won't work in Hardy Heron"
date: 2009-02-08
forum: Hardware
---

### Post by grashdur on 2009-02-08
Today my HP Laserjet 1200 stopped accepting print jobs from my main computer (my Gateway desktop computer, running Hardy Heron). Print jobs go into the print queue, but the light on the printer never starts flashing, and the job never prints. 

When I go into System > Administration > Printing, I see that the print-test-page button is greyed out. When I go into the next tab, I see that the printer is not "Enabled" -- when I check this box to enable the printer and click "Apply" at bottom, then in the first tab the print-test-page button is no longer greyed out. When I then click this button, I get an error message. Then after a couple attempts, all the printers disappear from the list -- both the Laserjet 1200 and "PDF." 

The printer itself is okay: I plugged it in to my laptop (running Intrepid Ibex) and the printer installed automatically and I could print a test page. (BTW, I can't solve this just by installing Intrepid Ibex on my main computer -- it cannot install there.)

The only things I've changed lately on the computer: 

* I ran updates yesterday, as I do once every week. After I ran the updates, no restart was required. I was able to print fine afterwards. But after starting up again today, there's no printing.

* I installed OpenJDK Java Runtime yesterday (I already had Sun Java 6 Runtime installed, but OpenOffice was complaining that it needed JRE, so I added this one too). OpenOffice works fine again after this Java installation. I tried uninstalling OpenJDK today to see if the printer problem would be go away, but it didn't, so I just reinstalled it again.

* One other possibility: My wife was printing from a special web page in Firefox (having to do with applying for student financial aid). The site would *not allow* her to print to PDF, so she tried to print to the paper printer. It stayed forever it the queue and no other printing would work either. Could a website with special printing restrictions somehow have messed up my printer setup in Ubuntu?

---

### Post by 73ckn797 on 2009-02-08
I would probably re-install the printer drivers.

Were there any printer related updates installed?

---

### Post by grashdur on 2009-02-08
Reinstall printer drivers: That makes sense. Do I do that in Synaptic Package Manager? What keywords should I search by?

I don't recall seeing printer updates on that list, but I wasn't looking carefully. Also, I might not have printed anything since the previous week's updates.

---

### Post by 73ckn797 on 2009-02-08
> **grashdur said:**
> Reinstall printer drivers: That makes sense. Do I do that in Synaptic Package Manager? What keywords should I search by?

I don't recall seeing printer updates on that list, but I wasn't looking carefully. Also, I might not have printed anything since the previous week's updates.


Search using "hp".

You can click in the list and just type "hp" and see what is installed. You may want to un-install those that are installed and then re-install.

---

### Post by grashdur on 2009-02-08
Interesting. I searched in Synaptic for "hp" and got absolutely nothing -- nothing is installed, and nothing is available. I clicked the Origin button and see (as I understand) the list of repositories enabled: I see four of them beginning with us.archive.ubuntu.com in addition to Local/main and Local/non-free.

While on my laptop (running Ibex) I tried also searching Synaptic for "hp": Installed I see:
cupsddk-drivers
hpijs
hplip
hplip-data
pnm2ppa
pxljr
...and I see a whole lot of things listed that are not currently installed. Confusing. Looking back at my main computer again, I tried searching for other things: "cups": no results; "gnome": no results (I would thing *something* would come up!)

---

### Post by 73ckn797 on 2009-02-08
Do you have the appropriate software sources selected in "Software Sources?

See attachment.

My choices may differ from what you have as far as additional listings show. The first 2 are typical.

---

### Post by grashdur on 2009-02-08
My wife is using that computer right now. I'll probably have to resume this tomorrow. I'll verify whether I have such sources selected.

---

### Post by grashdur on 2009-02-09
I was making a very silly mistake with the Synaptic Pkg Mgr: When I clicked to search, I was letting it search for "Version" instead of "Name and Description." 

So I tried using the Synaptic Pkg Mgr to reinstall the following packages: cupddk-drivers, foo2zjs, foomatic-db, foomatic-db-engine, hplip-data, openprinting-ppds, pxlr

It didn't help. When I try clicking "Print Test Page" I still get the error message "CUPS server error   There was an error during the CUPS operation: 'server-error-service-unavailable'.

Perhaps I should try reinstalling the applications "Printer" and "Manage Print Jobs" in Applications > Add/Remove.

---

### Post by 73ckn797 on 2009-02-09
Uninstall all printer stuff and start from scratch may be best. I do not know the command line way to fix.

---

### Post by grashdur on 2009-02-10
Thanks for sticking in there with me, 73ck. Just now I went into Synaptic, searched for "cupsys" and "cups" and "hp" then marked for deletion all packages that looked relevant to printing: about 26 packages in total. Then I ran into an issue I hadn't anticipated: Synaptic is set up to automatically remove all packages that depend on the ones I've marked for removal, even things that you wouldn't imagine would be affected. So when I looked at the final list of packages I was about to remove, the list included 282 packages, totalling over a gigabyte, including such things as Adobe Reader, Audacity, Brasero, Easytag, Evince, F-Spot, Firefox, Gdebi, Gedit, Gimp, gksu, gnome-applets, gnome-screensaver, Terminal, gnome-system-monitor, GnuCash, Kontact, Korganizer, language-selector, OpenOffice, Rhythbox, Samba, ubuntu-desktop, and VLC -- basically, just about all the programs that I use and perhaps a significant chunk of the OS itself. My concern is that if I proceed from here, I'll be stuck redownloading, installing, and configuring all my software over again in the best case, or having a gutted OS that hardly works any more in the worst case. 

Let me review first of all what else I've tried so far: 
* I've used the "reinstall" option in Synaptic to reinstall system-config-printer-gnome, system-config-printer-common, foomatic-filters, cupsddk-drivers, foo2zjs, foomatic-db, foomatic-db-engine, hplip-data, pxljr, cupsddk and I think a few other packages that I don't have written down now.
* Since corresponding with you last time I tried switching to a different driver for my printer -- but when I tried to apply the change, in each case I got the same error message as when trying to print a test page: "CUPS server error   There was an error during the CUPS operation: 'server-error-service-unavailable'."
* As mentioned before, in the printer-configuration window, I've tried checking the box for "Enabled" for this printer -- but when I then try to print a test page, I get that error message (just as above).

What do you think? Is there anything I can do other than gutting the entire OS? Reinstalling Hardy Heron would be another option, with about the same amount of work involved, but if the problem is caused by a faulty update, then the problem will return anyway once I run all the updates.

I have one more idea, a workaround: I have another printer that I haven't used in several years, an Epson color inkjet printer. I'll see if I can just set that up and use it for now.

---

### Post by 73ckn797 on 2009-02-11
I have not had to do what you are doing but I think that you can remove just the HP specific stuff. When you click on the driver/HP stuff select only "Mark for removal" not complete removal. See what that'll do fer ya.

---

### Post by grashdur on 2009-02-12
Actually, that's what I was doing already -- I completely avoided the "remove completely" option, as I didn't know what it was for or what the difference was.

....Yep, I just checked again: All depending packages are also eliminated, regardless of whether you "Mark for Removal" or "Mark for Complete Removal."

---

### Post by impact on 2009-02-12
You need to edit /etc/cups/cupsd.conf first and (sudo gedit /etc/cups/cupsd.conf) and change LOGLEVEL to DEBUG instead of WARNING or whatever is there. It's near the beginning of the file.

Then restart cups. (sudo /etc/init.d/cups restart ) 

Try printing again and when the error shows up again, analyze the logfile (sudo cat /var/log/cups/error_log). That should give you an idea what's wrong.

You can also access some more info about printers by visiting this URL [http://localhost:631/](http://localhost:631/)

---

### Post by grashdur on 2009-02-12
Hello impact: I modified that file as you advised. When I tried restarting cups with the command you recommended, and got this error message: 

> sudo: /etc/init.d/cups: command not found

So I rebooted instead (perhaps logging out and in would be enough?).

I tried printing a test page from within System > Administration > Printing, and got the same error message that I've been getting. 

I then checked that error log as you said and got this mass of data: 

```
E [12/Feb/2009:12:32:27 -0800] Resume-Printer: Unauthorized
E [12/Feb/2009:12:32:29 -0800] Unable to execute /usr/lib/cups/backend/hp: No such file or directory
E [12/Feb/2009:12:32:29 -0800] [Job 66] Unable to start backend "hp" - No such file or directory.
I [12/Feb/2009:13:08:04 -0800] Listening to :::631 (IPv6)
I [12/Feb/2009:13:08:04 -0800] Listening to 0.0.0.0:631 (IPv4)
I [12/Feb/2009:13:08:04 -0800] Listening to /var/run/cups/cups.sock (Domain)
I [12/Feb/2009:13:08:04 -0800] Loaded configuration file "/etc/cups/cupsd.conf"
D [12/Feb/2009:13:08:04 -0800] Repairing ownership of "/var/run/cups"
D [12/Feb/2009:13:08:04 -0800] Creating missing directory "/var/run/cups/certs"
D [12/Feb/2009:13:08:04 -0800] Repairing ownership of "/var/run/cups/certs"
D [12/Feb/2009:13:08:04 -0800] Repairing access permissions of "/var/run/cups/certs"
I [12/Feb/2009:13:08:04 -0800] Using default TempDir of /var/spool/cups/tmp...
I [12/Feb/2009:13:08:04 -0800] Configured for up to 100 clients.
I [12/Feb/2009:13:08:04 -0800] Allowing up to 100 client connections per host.
I [12/Feb/2009:13:08:04 -0800] Using policy "default" as the default!
I [12/Feb/2009:13:08:04 -0800] Full reload is required.
I [12/Feb/2009:13:08:04 -0800] Loaded MIME database from '/etc/cups': 36 types, 39 filters...
D [12/Feb/2009:13:08:04 -0800] Loading printer HP_LaserJet_1200...
*** WARNING *** The program 'cupsd' uses the Apple Bonjour compatibility layer of Avahi.
*** WARNING *** Please fix your application to use the native API of Avahi!
*** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd>
D [12/Feb/2009:13:08:04 -0800] Loading printer PDF...
D [12/Feb/2009:13:08:04 -0800] Loading printer Stylus_C42...
D [12/Feb/2009:13:08:04 -0800] Scanning /var/spool/cups for jobs...
D [12/Feb/2009:13:08:04 -0800] [Job 36] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 36] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 28] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 28] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 44] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 44] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 23] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 23] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 35] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 35] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 4] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 4] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 24] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 24] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 15] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 15] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 26] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 26] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 18] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 18] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 41] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 41] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 6] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 6] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 11] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 11] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 19] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 19] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 29] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 29] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 64] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 64] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 61] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 61] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 12] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 12] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 7] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 7] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 25] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 25] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 21] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 21] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 49] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 49] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 22] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 22] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 10] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 10] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 55] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 55] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 62] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 62] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 40] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 40] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 30] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 30] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 34] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 34] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 54] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 54] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 14] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 14] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 13] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 13] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 9] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 9] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 58] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 58] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 57] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 57] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 33] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 33] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 39] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 39] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 2] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 2] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 59] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 59] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 38] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 38] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 63] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 63] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 65] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 65] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 48] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 48] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 32] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 32] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 52] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 52] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 66] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 66] Auto-typing document file "/var/spool/cups/d00066-001"...
D [12/Feb/2009:13:08:04 -0800] [Job 43] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 43] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 20] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 20] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 46] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 46] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 60] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 60] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 42] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 42] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 47] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 47] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 37] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 37] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 27] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 27] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 17] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 17] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 31] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 31] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 45] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 45] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 56] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 56] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 51] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 51] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 8] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 8] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 53] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 53] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 16] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 16] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 5] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 5] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 1] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 1] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 50] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 50] Unloading...
D [12/Feb/2009:13:08:04 -0800] [Job 3] Loading attributes...
D [12/Feb/2009:13:08:04 -0800] [Job 3] Unloading...
I [12/Feb/2009:13:08:04 -0800] Loading NextJobId from job cache file "/var/cache/cups/job.cache"...
I [12/Feb/2009:13:08:04 -0800] Full reload complete.
I [12/Feb/2009:13:08:04 -0800] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [12/Feb/2009:13:08:04 -0800] Listening to :::631 on fd 13...
I [12/Feb/2009:13:08:04 -0800] Listening to 0.0.0.0:631 on fd 14...
I [12/Feb/2009:13:08:04 -0800] Listening to /var/run/cups/cups.sock on fd 15...
I [12/Feb/2009:13:08:04 -0800] Resuming new connection processing...
D [12/Feb/2009:13:08:04 -0800] Report: clients=0
D [12/Feb/2009:13:08:04 -0800] Report: jobs=66
D [12/Feb/2009:13:08:04 -0800] Report: jobs-active=1
D [12/Feb/2009:13:08:04 -0800] Report: printers=3
D [12/Feb/2009:13:08:04 -0800] Report: printers-implicit=0
D [12/Feb/2009:13:08:04 -0800] Report: stringpool-string-count=742
D [12/Feb/2009:13:08:04 -0800] Report: stringpool-alloc-bytes=9608
D [12/Feb/2009:13:08:04 -0800] Report: stringpool-total-bytes=14440
D [12/Feb/2009:13:08:05 -0800] cupsdAcceptClient: 19 from localhost (Domain)
D [12/Feb/2009:13:08:05 -0800] cupsdNetIFUpdate: "lo" = localhost...
D [12/Feb/2009:13:08:05 -0800] cupsdNetIFUpdate: "eth0" = 192.168.0.185...
D [12/Feb/2009:13:08:05 -0800] cupsdNetIFUpdate: "lo" = localhost...
D [12/Feb/2009:13:08:05 -0800] cupsdNetIFUpdate: "eth0" = fe80::240:caff:fe91:3f31%eth0...
D [12/Feb/2009:13:08:05 -0800] update_cups_browse: Refused 186 bytes from 192.168.0.185
D [12/Feb/2009:13:08:05 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:08:05 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:08:05 -0800] CUPS-Get-Printers
D [12/Feb/2009:13:08:05 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:08:05 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:08:05 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:08:05 -0800] CUPS-Get-Classes
D [12/Feb/2009:13:08:05 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:08:05 -0800] cupsdCloseClient: 19
D [12/Feb/2009:13:08:06 -0800] update_cups_browse: Refused 170 bytes from 192.168.0.185
D [12/Feb/2009:13:08:09 -0800] cupsdAcceptClient: 19 from localhost (Domain)
D [12/Feb/2009:13:08:09 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:08:09 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:08:09 -0800] CUPS-Get-Printers
D [12/Feb/2009:13:08:09 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:08:09 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:08:09 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:08:09 -0800] CUPS-Get-Classes
D [12/Feb/2009:13:08:09 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:08:09 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:08:09 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:08:09 -0800] CUPS-Get-Printers
D [12/Feb/2009:13:08:09 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:08:09 -0800] cupsdCloseClient: 19
D [12/Feb/2009:13:08:36 -0800] update_cups_browse: Refused 186 bytes from 192.168.0.185
D [12/Feb/2009:13:08:37 -0800] update_cups_browse: Refused 170 bytes from 192.168.0.185
D [12/Feb/2009:13:08:41 -0800] cupsdAcceptClient: 19 from localhost (Domain)
D [12/Feb/2009:13:08:41 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:08:41 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:08:41 -0800] Get-Jobs ipp://localhost/jobs/
D [12/Feb/2009:13:08:41 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:08:41 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:08:41 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:08:41 -0800] CUPS-Get-Printers
D [12/Feb/2009:13:08:41 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:08:41 -0800] cupsdCloseClient: 19
D [12/Feb/2009:13:09:07 -0800] cupsdNetIFUpdate: "lo" = localhost...
D [12/Feb/2009:13:09:07 -0800] cupsdNetIFUpdate: "eth0" = 192.168.0.185...
D [12/Feb/2009:13:09:07 -0800] cupsdNetIFUpdate: "lo" = localhost...
D [12/Feb/2009:13:09:07 -0800] cupsdNetIFUpdate: "eth0" = fe80::240:caff:fe91:3f31%eth0...
D [12/Feb/2009:13:09:07 -0800] Report: clients=0
D [12/Feb/2009:13:09:07 -0800] Report: jobs=66
D [12/Feb/2009:13:09:07 -0800] Report: jobs-active=1
D [12/Feb/2009:13:09:07 -0800] Report: printers=3
D [12/Feb/2009:13:09:07 -0800] Report: printers-implicit=0
D [12/Feb/2009:13:09:07 -0800] Report: stringpool-string-count=742
D [12/Feb/2009:13:09:07 -0800] Report: stringpool-alloc-bytes=9608
D [12/Feb/2009:13:09:07 -0800] Report: stringpool-total-bytes=14440
D [12/Feb/2009:13:09:07 -0800] update_cups_browse: Refused 186 bytes from 192.168.0.185
D [12/Feb/2009:13:09:08 -0800] update_cups_browse: Refused 170 bytes from 192.168.0.185
D [12/Feb/2009:13:09:38 -0800] update_cups_browse: Refused 186 bytes from 192.168.0.185
D [12/Feb/2009:13:09:39 -0800] update_cups_browse: Refused 170 bytes from 192.168.0.185
D [12/Feb/2009:13:10:04 -0800] cupsdAcceptClient: 19 from localhost (Domain)
D [12/Feb/2009:13:10:05 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:05 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:05 -0800] CUPS-Get-Printers
D [12/Feb/2009:13:10:05 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:05 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:05 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:05 -0800] CUPS-Get-Classes
D [12/Feb/2009:13:10:05 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:05 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:05 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:05 -0800] CUPS-Get-Default
D [12/Feb/2009:13:10:05 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:05 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:05 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:05 -0800] Get-Printer-Attributes ipp://localhost/printers/HP_LaserJet_1200
D [12/Feb/2009:13:10:05 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:05 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:05 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:05 -0800] Get-Printer-Attributes ipp://localhost/printers/HP_LaserJet_1200
D [12/Feb/2009:13:10:05 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:05 -0800] cupsdReadClient: 19 GET /printers/HP_LaserJet_1200.ppd HTTP/1.1
D [12/Feb/2009:13:10:05 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:05 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:05 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:05 -0800] Get-Jobs ipp://localhost/jobs/
D [12/Feb/2009:13:10:05 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:09 -0800] cupsdNetIFUpdate: "lo" = localhost...
D [12/Feb/2009:13:10:09 -0800] cupsdNetIFUpdate: "eth0" = 192.168.0.185...
D [12/Feb/2009:13:10:09 -0800] cupsdNetIFUpdate: "lo" = localhost...
D [12/Feb/2009:13:10:09 -0800] cupsdNetIFUpdate: "eth0" = fe80::240:caff:fe91:3f31%eth0...
D [12/Feb/2009:13:10:09 -0800] Report: clients=1
D [12/Feb/2009:13:10:09 -0800] Report: jobs=66
D [12/Feb/2009:13:10:09 -0800] Report: jobs-active=1
D [12/Feb/2009:13:10:09 -0800] Report: printers=3
D [12/Feb/2009:13:10:09 -0800] Report: printers-implicit=0
D [12/Feb/2009:13:10:09 -0800] Report: stringpool-string-count=742
D [12/Feb/2009:13:10:09 -0800] Report: stringpool-alloc-bytes=9608
D [12/Feb/2009:13:10:09 -0800] Report: stringpool-total-bytes=14440
D [12/Feb/2009:13:10:09 -0800] update_cups_browse: Refused 186 bytes from 192.168.0.185
D [12/Feb/2009:13:10:10 -0800] update_cups_browse: Refused 170 bytes from 192.168.0.185
D [12/Feb/2009:13:10:15 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:15 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:15 -0800] Get-Jobs ipp://localhost/jobs/
D [12/Feb/2009:13:10:15 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:15 -0800] cupsdReadClient: 19 POST /jobs/ HTTP/1.1
D [12/Feb/2009:13:10:15 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:15 -0800] Cancel-Job ipp://localhost/jobs/66
D [12/Feb/2009:13:10:15 -0800] cupsdIsAuthorized: requesting-user-name="grashdur"
D [12/Feb/2009:13:10:15 -0800] Discarding unused job-completed event...
I [12/Feb/2009:13:10:15 -0800] [Job 66] Canceled by "grashdur".
D [12/Feb/2009:13:10:15 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:15 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:15 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:15 -0800] Get-Jobs ipp://localhost/jobs/
D [12/Feb/2009:13:10:15 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:16 -0800] [Job 66] Unloading...
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 19 POST /admin/ HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:21 -0800] Resume-Printer ipp://localhost/printers/HP_LaserJet_1200
D [12/Feb/2009:13:10:21 -0800] cupsdIsAuthorized: username=""
E [12/Feb/2009:13:10:21 -0800] Resume-Printer: Unauthorized
D [12/Feb/2009:13:10:21 -0800] cupsdSendError: 19 code=401 (Unauthorized)
D [12/Feb/2009:13:10:21 -0800] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"
D [12/Feb/2009:13:10:21 -0800] cupsdCloseClient: 19
D [12/Feb/2009:13:10:21 -0800] cupsdAcceptClient: 19 from localhost (Domain)
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 19 POST /admin/ HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: Authorized as root using Local
D [12/Feb/2009:13:10:21 -0800] Resume-Printer ipp://localhost/printers/HP_LaserJet_1200
D [12/Feb/2009:13:10:21 -0800] cupsdIsAuthorized: username="root"
D [12/Feb/2009:13:10:21 -0800] Discarding unused printer-state-changed event...
I [12/Feb/2009:13:10:21 -0800] Saving printers.conf...
I [12/Feb/2009:13:10:21 -0800] Printer "HP_LaserJet_1200" started by "root".
D [12/Feb/2009:13:10:21 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:21 -0800] cupsdAcceptClient: 22 from localhost (Domain)
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 22 POST / HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:21 -0800] Get-Jobs ipp://localhost/jobs/
D [12/Feb/2009:13:10:21 -0800] cupsdProcessIPPRequest: 22 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 22 POST / HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: No authentication data provided.
D [12/Feb/2009:13:10:21 -0800] CUPS-Get-Printers
D [12/Feb/2009:13:10:21 -0800] cupsdProcessIPPRequest: 22 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:21 -0800] cupsdCloseClient: 22
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: Authorized as root using Local
D [12/Feb/2009:13:10:21 -0800] CUPS-Get-Printers
D [12/Feb/2009:13:10:21 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: Authorized as root using Local
D [12/Feb/2009:13:10:21 -0800] CUPS-Get-Classes
D [12/Feb/2009:13:10:21 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: Authorized as root using Local
D [12/Feb/2009:13:10:21 -0800] CUPS-Get-Printers
D [12/Feb/2009:13:10:21 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: Authorized as root using Local
D [12/Feb/2009:13:10:21 -0800] CUPS-Get-Classes
D [12/Feb/2009:13:10:21 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: Authorized as root using Local
D [12/Feb/2009:13:10:21 -0800] CUPS-Get-Default
D [12/Feb/2009:13:10:21 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: Authorized as root using Local
D [12/Feb/2009:13:10:21 -0800] Get-Printer-Attributes ipp://localhost/printers/HP_LaserJet_1200
D [12/Feb/2009:13:10:21 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: Authorized as root using Local
D [12/Feb/2009:13:10:21 -0800] Get-Printer-Attributes ipp://localhost/printers/HP_LaserJet_1200
D [12/Feb/2009:13:10:21 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 19 GET /printers/HP_LaserJet_1200.ppd HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: Authorized as root using Local
D [12/Feb/2009:13:10:21 -0800] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Feb/2009:13:10:21 -0800] cupsdAuthorize: Authorized as root using Local
D [12/Feb/2009:13:10:21 -0800] Get-Jobs ipp://localhost/jobs/
D [12/Feb/2009:13:10:21 -0800] cupsdProcessIPPRequest: 19 status_code=0 (successful-ok)
D [12/Feb/2009:13:10:22 -0800] update_cups_browse: Refused 186 bytes from 192.168.0.185
D [12/Feb/2009:13:10:23 -0800] cupsdReadClient: 19 POST /printers/HP_LaserJet_1200 HTTP/1.1
D [12/Feb/2009:13:10:23 -0800] cupsdAuthorize: Authorized as root using Local
D [12/Feb/2009:13:10:23 -0800] Print-Job ipp://localhost/printers/HP_LaserJet_1200
D [12/Feb/2009:13:10:23 -0800] Adding default job-sheets values "none,none"...
I [12/Feb/2009:13:10:23 -0800] [Job 67] Adding start banner page "none".
D [12/Feb/2009:13:10:23 -0800] Discarding unused job-created event...
I [12/Feb/2009:13:10:23 -0800] [Job 67] Adding job file of type application/postscript.
I [12/Feb/2009:13:10:23 -0800] [Job 67] Adding end banner page "none".
I [12/Feb/2009:13:10:23 -0800] [Job 67] Queued on "HP_LaserJet_1200" by "root".
D [12/Feb/2009:13:10:23 -0800] [Job 67] hold_until = 0
D [12/Feb/2009:13:10:23 -0800] Discarding unused printer-state-changed event...
D [12/Feb/2009:13:10:23 -0800] [Job 67] job-sheets=none,none
D [12/Feb/2009:13:10:23 -0800] [Job 67] banner_page = 0
D [12/Feb/2009:13:10:23 -0800] [Job 67] argv[0]="HP_LaserJet_1200"
D [12/Feb/2009:13:10:23 -0800] [Job 67] argv[1]="67"
D [12/Feb/2009:13:10:23 -0800] [Job 67] argv[2]="root"
D [12/Feb/2009:13:10:23 -0800] [Job 67] argv[3]="Test Page"
D [12/Feb/2009:13:10:23 -0800] [Job 67] argv[4]="1"
D [12/Feb/2009:13:10:23 -0800] [Job 67] argv[5]="job-uuid=urn:uuid:9c192f8e-55f2-3f20-58c0-6cc5210fe9aa"
D [12/Feb/2009:13:10:23 -0800] [Job 67] argv[6]="/var/spool/cups/d00067-001"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[9]="SERVER_ADMIN=root@grashdur-desktop"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[10]="SOFTWARE=CUPS/1.3.7"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[12]="TZ=America/Los_Angeles"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[13]="USER=root"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[16]="IPP_PORT=631"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[17]="CHARSET=utf-8"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[18]="LANG=en_US.UTF8"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[19]="PPD=/etc/cups/ppd/HP_LaserJet_1200.ppd"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[20]="RIP_MAX_CACHE=8m"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[21]="CONTENT_TYPE=application/postscript"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[22]="DEVICE_URI=hp:/usb/HP_LaserJet_1200?serial=00CNCY032772"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[23]="PRINTER=HP_LaserJet_1200"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[24]="FINAL_CONTENT_TYPE=printer/HP_LaserJet_1200"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[25]="AUTH_U****"
D [12/Feb/2009:13:10:23 -0800] [Job 67] envp[26]="AUTH_P****"
I [12/Feb/2009:13:10:23 -0800] [Job 67] Started filter /usr/lib/cups/filter/pstops (PID 6723)
I [12/Feb/2009:13:10:23 -0800] [Job 67] Started filter /usr/lib/cups/filter/foomatic-rip (PID 6724)
E [12/Feb/2009:13:10:23 -0800] Unable to execute /usr/lib/cups/backend/hp: No such file or directory
E [12/Feb/2009:13:10:23 -0800] [Job 67] Unable to start backend "hp" - No such file or directory.
D [12/Feb/2009:13:10:23 -0800] Discarding unused job-completed event...
*** glibc detected *** /usr/sbin/cupsd: double free or corruption (!prev): 0x080e9db8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7be7a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7beb4f0]
/usr/lib/libcups.so.2(cupsArrayDelete+0x37)[0xb7da6087]
/usr/sbin/cupsd[0x8083680]
/usr/sbin/cupsd[0x8084a96]
/usr/sbin/cupsd[0x80705fd]
/usr/sbin/cupsd[0x807df0d]
/usr/sbin/cupsd(cupsdReadClient+0x51a)[0x8059dda]
/usr/sbin/cupsd[0x8090821]
/usr/sbin/cupsd[0x806acb0]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7b92450]
/usr/sbin/cupsd[0x804fa41]
======= Memory map: ========
```

By the way, I tried clicking that link and Firefox told me:

> Firefox can't establish a connection to the server at localhost:631

---

### Post by impact on 2009-02-13
The only thing I found is this post:

[http://ubuntuforums.org/showthread.php?t=925222](http://ubuntuforums.org/showthread.php?t=925222)

If that doesn't work, I suggest you visit [https://bugs.launchpad.net/](https://bugs.launchpad.net/) and file a bug report or search for a similar one to attach your findings to.

[http://localhost:631/](http://localhost:631/) should show you the CUPS administration page. If it doesn't work, try visiting [http://127.0.0.1:631/](http://127.0.0.1:631/) - different URL, but same thing.

---

### Post by grashdur on 2009-02-14
Wow!! That worked! And it was so easy! All I had to do was go into Synaptic and install the package called hpijs, and I didn't even have to reboot!

Thank you, impact!!

And by the way, that second link for the CUPS web-based printer manager works. I've bookmarked it, as it looks useful. As soon as I looked at it, it told me that some hp backend file was missing.

I wanted to thank you, but somehow the little thankyou icon is missing from the webpage right now. Strange.

---

### Post by grashdur on 2009-02-14
This issue is SOLVED. I would mark the thread as such, but I've looked all over and I don't see the icon to click for indicating this status.

---

