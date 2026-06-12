---
title: "Printing issue"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by Brainburp on 2005-04-11
Hi

I can't seem to get Ubuntu/Gnome/Linux to send data to the printer

I have an Epson Stylus Photo 810. The printer is detected, it allows me to select the printer from the driver list and seems to install the GImp-Print driver. However, when i try and print anything, i get absolutely nothing. It doesn't even send the data to the print monitor - I have tried Autodecting, selcting the printer manually, run it on USB and Parallel port but to no avail

Any help is appreciated

Thank you!

---

### Post by wfx on 2005-04-11
Test if:
"cat /etc/cups/cupsd.conf | grep ServerName"
output something like "ServerName 127.0.0.1"

If so then do:
"/etc/init.d/cupsys restart"
(maybe the server is not runing)

make a test page and then:
"cat /var/log/cups/error_log"

---

### Post by Brainburp on 2005-04-16
Thank you very much for the info - here are my results - sorry its taken a few days to get back to you

I am going to download the latest versions of 

cupsys
gimp-print
foomatic 

and now also the version of ESP Ghostprint

to see what happens - It's a shame, this is the only issue i've had with Ubuntu and Linux, i'd rather it was easier.. but hay where would the fun be??

I am a little worried by the comments in the error log that i have 38 jobs in the print que!  Better work out how i can empty it.. 

thank you 


----------------------
the hostname of your server, as advertised to the world.
#ServerName myhost.domain.com

/etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd
cupsd: Child exited with status 13!

dan@ubuntu:~$ cat /var/log/cups/error_log
II [16/Apr/2005:10:30:24 +0100] Listening to 7f000001:631
I [16/Apr/2005:10:30:24 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
I [16/Apr/2005:10:30:24 +0100] Configured for up to 100 clients.
I [16/Apr/2005:10:30:24 +0100] Allowing up to 100 client connections per host.
I [16/Apr/2005:10:30:24 +0100] Full reload is required.
I [16/Apr/2005:10:30:24 +0100] LoadPPDs: Read "/etc/cups/ppds.dat", 2346 PPDs...
I [16/Apr/2005:10:30:24 +0100] LoadPPDs: No new or changed PPDs...
I [16/Apr/2005:10:30:24 +0100] Full reload complete.
I [16/Apr/2005:10:59:36 +0100] Scheduler shutting down normally.
I [16/Apr/2005:16:32:39 +0100] Listening to 7f000001:631
I [16/Apr/2005:16:32:39 +0100] Loaded configuration file "/etc/cups/cupsd.conf"
I [16/Apr/2005:16:32:39 +0100] Configured for up to 100 clients.
I [16/Apr/2005:16:32:39 +0100] Allowing up to 100 client connections per host.
I [16/Apr/2005:16:32:39 +0100] Full reload is required.
I [16/Apr/2005:16:32:41 +0100] LoadPPDs: Read "/etc/cups/ppds.dat", 2346 PPDs...
I [16/Apr/2005:16:32:42 +0100] LoadPPDs: No new or changed PPDs...
I [16/Apr/2005:16:32:42 +0100] Full reload complete.
I [16/Apr/2005:16:57:04 +0100] Adding start banner page "none" to job 38.
I [16/Apr/2005:16:57:04 +0100] Adding end banner page "none" to job 38.
I [16/Apr/2005:16:57:04 +0100] Job 38 queued on 'Stylus-Photo-810' by 'dan'.
E [16/Apr/2005:16:57:04 +0100] Unable to convert file 0 to printable format for job 38!
I [16/Apr/2005:16:57:04 +0100] Hint: Do you have ESP Ghostscript installed?
I [16/Apr/2005:16:57:04 +0100] Hint: Try setting the LogLevel to "debug".

---

### Post by wfx on 2005-04-16
A normal printjob on my system look like this:> I [14/Apr/2005:16:10:12 +0200] Adding start banner page "none" to job 230.
I [14/Apr/2005:16:10:12 +0200] Adding end banner page "none" to job 230.
I [14/Apr/2005:16:10:12 +0200] Job 230 queued on 'DeskJet5652' by 'wolfgang'.
I [14/Apr/2005:16:10:12 +0200] Started backend /usr/lib/cups/backend/parallel (P ID 19448) for job 230. 
The server ip "7f000001" looks strange for me?
Please check again if you have this line in "/etc/cups/cupsd.conf":
"ServerName 127.0.0.1"
> II [16/Apr/2005:10:30:24 +0100] Listening to 7f000001:631 
Do you restart it as normal user?
Yes then: "sudo /etc/init.d/cupsys restart"
No then is there some more output behind " cupsd: Child exited with status 13!" ?

Yes this "Unable to convert file 0 to printable format for job 38!" look like any
missing converter. But i dont think it is.
Please set the loglevel in /etc/cups/cupsd.conf" to debug :
LogLevel debug
Print any normal text (with gedit)

---

### Post by Brainburp on 2005-04-17
dan@ubuntu:~$ sudo /etc/init.d/cupsys restart
Password:
 * Restarting Common Unix Printing System: cupsd                         [ ok ]

---------------------------------------------------------------------------------------------------

Ah ha!

Needed restart the cupsys server as SUDO user -  Then it worked!! Thank you - and Sorry for being such a numpty! 

Will i need restart the server everytime i log on? 

thanks again

---

### Post by wfx on 2005-04-18
No you dont need to restart it manualy (only if you change something in the config).

---

### Post by robi72 on 2005-05-01
[QUOTE=Brainburp]Hi

I can't seem to get Ubuntu/Gnome/Linux to send data to the printer

I have an Epson Stylus Photo 810. The printer is detected, it allows me to select the printer from the driver list and seems to install the GImp-Print driver. However, when i try and print anything, i get absolutely nothing. It doesn't even send the data to the print monitor - I have tried Autodecting, selcting the printer manually, run it on USB and Parallel port but to no avail

Any help is appreciated

Thank you![/QUOTE]
 I had similar problem, I deleted the printer in the GUI dialog and re-added the printer
but I picked other driver than before and it works fine.

---

