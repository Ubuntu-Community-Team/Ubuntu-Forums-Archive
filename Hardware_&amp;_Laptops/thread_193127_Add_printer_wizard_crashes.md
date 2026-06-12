---
title: "Add printer wizard crashes"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by notoriousdbp on 2006-06-09
Hi all, I don't know if this is the right area but I really need some help with printing in Dapper.  Basically, when I go to add a printer I get a box on screen which says "reading printer database" and it just gets stuck there and doesn't go any further than that.  I've also installed foomatic-gui to get into printing that way but my laptop makes all the right sounds as though it's starting the app and I'm even prompted for the root password then I just get nothing.

I've tried running foomatic-gui from terminal and I get this output:

*** glibc detected *** double free or corruption (!prev): 0x0816e838 ***
Unable to read printer database.

Can anyone help as to what I need to do to get things up and running?  I just don't know where to begin and I certainly don't want to re-install the OS or anything drastic like that.

---

### Post by notoriousdbp on 2006-06-11
Hi there, sorry to ask again but can anybody help at all?  I'm really stuck

---

### Post by ransu_k on 2006-06-13
Hi, I have exactly the same broblem and error message. Unfortunately I don't know how to solve it. :(

---

### Post by notoriousdbp on 2006-06-15
so that's 2 of us, I still have the same problem.  can anyone out there help at all

---

### Post by notoriousdbp on 2006-06-20
[QUOTE=notoriousdbp]so that's 2 of us, I still have the same problem.  can anyone out there help at all[/QUOTE]
I'm still stuck.  My system is fully up to date. Heeelp please.

---

### Post by notoriousdbp on 2006-06-20
If it helps it's gnome-cups-add that is crashing

---

### Post by bruder_s on 2006-06-27
Same problem here.

What I did:

1. sudo gedit /etc/cups/cupsd.conf
Find the LogLevel setting and edit to: LogLevel debug 
2. sudo /etc/init.d/cupsys restart
3. supo gnome-cups-add
4. (in another terminal) sudo tail /var/log/cups/error_log

My error_log at this point: 

```

D [27/Jun/2006:10:18:35 +0200] [cups-deviced] Added device "ipp"...
D [27/Jun/2006:10:18:35 +0200] [cups-deviced] Added device "http"...
D [27/Jun/2006:10:18:35 +0200] [cups-deviced] Added device "bluetooth"...
D [27/Jun/2006:10:18:35 +0200] [cups-deviced] Added device "epson:/dev/lp0"...
D [27/Jun/2006:10:18:36 +0200] [cups-deviced] Added device "canon:/dev/lp0"...
D [27/Jun/2006:10:18:36 +0200] [cups-deviced] Added device "beh"...
D [27/Jun/2006:10:18:36 +0200] [cups-deviced] Added device "hp:/no_device_found"...
D [27/Jun/2006:10:18:36 +0200] [cups-deviced] Added device "smb"...
D [27/Jun/2006:10:18:36 +0200] [cups-deviced] Added device "lpd"...
W [27/Jun/2006:10:19:08 +0200] [cups-deviced] Backend "parallel" did not respond within 30 seconds!

```

I don't know if this is an error and why it occurs, but since it breaks everything I decided to get rid of this.
After further researching, I found out how to disable the parallel-port:

5. sudo rm /usr/lib/cups/backend/parallel

Now the Wizard starts again.

Maybe this will help you a little bit.
I guess you won't be able to print on the parallel port anymore.

Christian

---

### Post by notoriousdbp on 2006-07-08
Thanks for that, I got a different error log though:

D [08/Jul/2006:23:23:17 +0100] cupsdReadClient: 5 POST / HTTP/1.1
D [08/Jul/2006:23:23:17 +0100] cupsdAuthorize: No authentication data provided.
D [08/Jul/2006:23:23:17 +0100] CUPS-Get-Default
I [08/Jul/2006:23:23:17 +0100] CUPS-Get-Default client-error-not-found: No default printer
D [08/Jul/2006:23:23:17 +0100] cupsdProcessIPPRequest: 5 status_code=406 (client-error-not-found)
D [08/Jul/2006:23:23:17 +0100] cupsdReadClient: 5 POST / HTTP/1.1
D [08/Jul/2006:23:23:17 +0100] cupsdAuthorize: No authentication data provided.
D [08/Jul/2006:23:23:17 +0100] CUPS-Get-Printers
I [08/Jul/2006:23:23:17 +0100] CUPS-Get-Printers client-error-not-found: No destinations added.
D [08/Jul/2006:23:23:17 +0100] cupsdProcessIPPRequest: 5 status_code=406 (client-error-not-found)


I got rid of the parallel port as my laptop doesn't have one anyway but still hangs when I try to run it.

---

### Post by notoriousdbp on 2006-07-18
I'm afraid I had to reinstall Dapper to get a printer installed but to be fair I think a lot of things were wrong with my previos installation (such as user switching not working etc)  I did try foomatic gui again on my new install but no joy still on that one but everything is fine with cups.

---

### Post by zeitgeist on 2006-09-15
Hi,

I had the same problem. 

From my menu (System - Printers) foomatic-gui was called and ended with the same error that notoriousdbp stated:

foomatic-gui
*** glibc detected *** double free or corruption (!prev): 0x08179528 ***
Unable to read printer database.

[solved] I had success with calling

```
gnome-cups-manager
```

on the commandline. Then I could add a printer. 

zeitgeist

---

### Post by kswnsn on 2006-10-10
If you are/have run KDE, and selected a certain GTK style under the KDE control center, you will have a ~/.gtkrc-2.0 file that will prevent certain GNOME apps from running. First rename this file to see if it clears the issue, and if so, try a different theme. I was using "Glider" but changed to "Human" to correct this issue.

---

