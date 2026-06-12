---
title: "CUPS broken pipe / lpd failed / ..."
date: 2009-03-26
forum: Hardware
---

### Post by Conq321 on 2009-03-26
Dear all,

I'm trying to make my printer work via a print server. I've google a lot and searched the entire forum here, but none of the solutions given worked for me.

Printer: HP Business Inkjet 1000 series
Printserver: Sitecom LN 308 (MFP)
Printserver hooked up via rooter

When trying to install the new printer via [http://localhost:631/admin](http://localhost:631/admin)

'Server section'
Show printers shared by other systems ... on
Share published printers connected to this system ... on 
Allow remote administration ... on
[others ... off]

I clicked the button 'find new printers' in printers section

Found: hp Business Inkjet 1000 series (hp Business Inkjet 1000 series 192.168.0.110)

That's good news, so I clicked 'add this printer'. I left name, description and location to their default values (all nice names) and clicked continue.

This took a while, but then came the screen to select my drivers. Model/Driver for hp_Business_Inkjet_1000_series_192.168.0.110 was given by default and i kept the default driver (hp business inkjet 1000)

Next screen gave a succes message.

Description: hp Business Inkjet 1000 series
Location: Local Printer
Printer Driver: HP Business Inkjet 1000 Foomatic/hpijs, hpijs 2.8.7
Printer State: processing, accepting jobs, published.
Device URI: socket://192.168.0.110 

Now when i print a test page (or any other page from any other program), the job gets send, gets processed, but then i get the following message:

First: connected to 192.168.0.110
Then (few seconds later): Unable to write print data: Broken pipe

Nothing actually gets printed out.

A suggestion was to change socket://192.168.0.110:9100 (in cups-config) 
to lpd://192.168.0.110

but that did not work either.

Others things tried:
- check for hplip ... ok
- use ipp (printer found, but no results)
- use lpr (printer found, but no results)

Any ideas on this?

Thanks in advance!

ATTACHEMENT :

error_log , resulting from:

- printed test page via cups manager as installed as described above
- changed uri to socket://192.168.0.110:9100 and tested
- changed uri to lpd://192.168.0.110 and tested

---

### Post by tiger99tiger on 2009-08-31
Conq321,

5 months later, and no response. Either only two people in the whole world have this problem, or it is too difficult to solve....

I have a different printer (Epsom RX-560), different Sitecom server (WL-203), and exactly the same problem. same error message. I did all the same things as you have done, quite logical really, and then I checked this forum. I am on Ubuntu Jaunty, 64 bit.

So I think we can rule out the printer, Gnome and Xfce, and the bug lies in the bit that is common (probably!).

I can print to other network printers, which have their own internal server, via socket://192.168.x.y:9100. In fact that has been totally trouble free for a long time.

So is it CUPS or the Sitecom server? I wonder....

I am thinking that the Sitecom box sometimes allocates the USB printer to only one PC at a time, because the USB protocol requires it to do that. It is normally switched by a Windoze utility, which could be replicated on Linux, if we were to analyse what data it sends to the Sitecom, and reverse engineer it. But that should only be true for a Windoze GDI printer, and in both cases we seem to have a real printer, not some brain-dead piece of junk. In any case I am testing with only one PC on the network booted up, and the Sitecom box has never seen the others, so it "should" default to the only PC it knows.

I checked that it was not Apparmor causing the problem by turning it off.

There are a lot of errors of the form "cupsdAuthorize: No authentication data provided." in /var/log/cups/error_log, with the LogLevel parameter in /etc/cups/cupsd.conf to "debug". I wonder.....

Sitecom do not mention Linux on their web site, although I suspect that some of their products are using it internally. I wonder where the source code is, or are they being naughty? But the server I have supposedly works with OS X, and does not seem to need a driver for that, not would we expect it to, so it should be OK for Linux.

In the next few days I will try a different print server, one built into a NAS box, to see if that makes any difference. If that does not work, I will have to take the server and printer to my friend's office, to try it with Windoze, just to ensure that it really works. (I don't have Windoze here, I am glad to say!) I will report my findings later.

Alan

---

### Post by marchewk on 2009-09-01
I have Epson Stylus S20 and Edimax PS-1216U print server and the same problem.

---

