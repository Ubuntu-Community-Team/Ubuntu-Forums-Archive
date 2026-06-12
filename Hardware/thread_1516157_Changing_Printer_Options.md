---
title: "Changing Printer Options"
date: 2010-06-23
forum: Hardware
---

### Post by libssd on 2010-06-23
I'm pretty sure I have done a thorough search, and am surprised this question hasn't been raised before. I am unable to change printer options for a shared printer that is connected to a Mac. Printing works, but is shifted to the very top of the paper, unless I set a large top margin, e.g. 1.5" in the document format. I believe the problem is that the default page size is A4, while I am using US Letter size paper.

However, the paper size option (as are all others) is grayed out, so I am unable to change it. The same printer, viewed from the Mac, defaults to US Letter. 

This looks like a permissions problem on the Linux end, confirmed by receiving a 403 Forbidden error message when attempting to change printer options through the CUPS web interface, but I have been unable to figure which permissions (if any) need to be changed. 

Alternatively, if I could change the default paper size from the command line, that would be acceptable.

Suggestions (other than changing the document page margins)?

---

### Post by libssd on 2010-06-23
I'm making some progress on this. Invoking the web interface for CUPS, I changed the default paper size option from A4 to Letter. However, it's still showing up as A4 on the remote netbook.

This now looks as if I have to authenticate to CUPS on the Mac from the netbook, as I get an error message when trying to change printer options through CUPS on the netbook:

```
426 Upgrade Required

You must access this page using the URL [https://10.0.1.2:631/admin](https://10.0.1.2:631/admin).
```

Remote administration is enabled for CUPS on the Mac.

One possible gotcha is that CUPS 1.4.3 is running on Linux, while the Mac is running CUPS 1.3.11.

---

### Post by libssd on 2010-06-23
I'm getting close, but still not quite there. Running CUPS Admin on the Mac allowed me to change the default page size from A4 to US Letter.

However, on the Linux netbook, I'm still unable to change any printer options, whether using the printing utility, or from the print page of an application.

If I duplicate the HP_Laserjet_1012 printer, and install the appropriate driver, everything is accessible, but the print job never gets to the Mac, although Linux thinks it does.

Using CUPS Admin from Linux, trying to change the printer options returns:

```

SSL connection error.

Unable to make a secure connection to the server. 
This may be a problem with the server, or it may 
be requiring a client authentication certificate 
that you don't have.
```

What next?

---

### Post by libssd on 2010-06-23
Error log shows it's still looking for credentials:

```

D [23/Jun/2010:18:46:07 -0400] cupsdAcceptClient: 20 from localhost (Domain)D [23/Jun/2010:18:46:07 -0400] cupsdReadClient: 20 POST / HTTP/1.1
D [23/Jun/2010:18:46:07 -0400] cupsdAuthorize: No authentication data provided.
D [23/Jun/2010:18:46:07 -0400] Get-Subscriptions ipp://localhost/
D [23/Jun/2010:18:46:07 -0400] Get-Subscriptions client-error-not-found: No subscriptions found.
D [23/Jun/2010:18:46:07 -0400] cupsdProcessIPPRequest: 20 status_code=406 (client-error-not-found)
D [23/Jun/2010:18:46:07 -0400] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Jun/2010:18:46:07 -0400] Script header: Content-Type: text/html;charset=utf-8
D [23/Jun/2010:18:46:07 -0400] Script header: 
D [23/Jun/2010:18:46:07 -0400] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Jun/2010:18:46:07 -0400] [CGI] lang="en_US.UTF8", locale="/en_US"...
D [23/Jun/2010:18:46:07 -0400] cupsdCloseClient: 20
D [23/Jun/2010:18:46:07 -0400] PID 1671 (/usr/libexec/cups/cgi-bin/admin.cgi) exited with no errors.
D [23/Jun/2010:18:46:10 -0400] cupsdReadClient: 17 GET /admin/log/error_log HTTP/1.1
D [23/Jun/2010:18:46:10 -0400] cupsdAuthorize: Authorized as seldendeemer using Basic

```

---

### Post by libssd on 2010-06-23
Incremental progress. In cupsd.conf on the Mac, I added:

[INDENT]DefaultEncryption never[/INDENT]

After restarting CUPS, I am now asked for my Linux login/password before changing printer options using CUPS Admin.

But, when printing from an application, all choices are still grayed out, same for system-config-printer. There must be some way to enable changes in printer options other than through CUPS Admin. 

Surely, I'm not the only person in the world trying to print wirelessly from Ubuntu to a USB shared printer on a Mac running OS X 10.5. But, so far, I have been unable to find a solution on Linux or Apple forums. Strange.

---

### Post by libssd on 2010-06-28
I'm beginning to question my sanity.

I thought I found the solution (mostly) in an Apple Support document: **[RemoteDesktop 3.0 Help]("http://docs.info.apple.com/article.html?path=RemoteDesktop/3.0/en/ARDC858.html")**:

> Use the Copy Items task to copy the following file and folder to all the target computers:
/private/etc/cups/printers.conf
/private/etc/cups/ppd/
Because these files are hidden in the Finder, you may have to use the Terminal or the Finder's "Go to Folder" command to add them to the "Items to copy" list.
After doing essentially this at the command line and restarting, Open Office apps, Gedit, PDF files, etc all have changeable print options now. But web browsers and the Printing utility still do not, which leads me to wonder if I was imagining the problem with the other apps. I don't feel like restoring from a backup to find out. The status quo is good enough.

---

