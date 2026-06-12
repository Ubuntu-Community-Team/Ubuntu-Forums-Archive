---
title: "Epson WP4535-DWF printer"
date: 2012-03-24
forum: Hardware
---

### Post by Stef700 on 2012-03-24
Hi,

I have just installed an Epson WP4535-DWF Ethernet connected printer on 192.168.0.19 (Reserved ip).

It's working under Windows 7 and XP clients....

Now I want to access it from my Ubuntu 11.10

I came across this site

[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

Which says this model of printer works very well under Ubuntu

(And there seems to be at least three different drivers for it  !!!!!!!!!)

Now what do I do next as I have NEVER installed a printer under Linux/Ubuntu before...

An idiots guide, or just a few pointers (Steps 1, 2, 3 etc would be very much appreciated)

Thanks in advance,
Stef
):P

---

### Post by Frogs Hair on 2012-03-24
All I have ever had to do is connect the printer open Systems Settings > Printer . When the port or connection is detected in the case of a wired printer, a list of brands will appear.

Select the brand and a list of models will appear. Selecting the model should locate the correct driver if available. It may take 15 to 20 seconds to locate the printer or it may be detected right away . Manually entering the port or connection is also possible.

Selecting the particular model helps to locate the correct driver . I am offered a generic driver not for my printer if I don't narrow the search selecting the model number.

---

### Post by Stef700 on 2012-03-24
This is a *network* connected printer and my Ubuntu client does not auto detect it...

I am flummoxed and don't know what to do next... 

(In Windows it is easy, you just install the drivers, on disk, and it connects)

Epson provide Linux/Ubuntu drivers but no instructions as far as I can tell...

I'll go and do some more research on the Epson support site but if anyone has any ideas???

Thanks,
Stef

---

### Post by beanhead on 2012-03-24
Lets use the CUPS web based config for this setup.
open firefox and put in [http://localhost:631](http://localhost:631) in the address bar.
you should then see the cups page.

click administration tab, click add printer.
you will be prompted for the printer info
when you are asked for the printer device use network printer.
the path to your printer device should be lpr://computerNameThatThePrinterIsConnectedTo/Printername

select your printer manfacturer from the next list
then select your model from the list.

then cups will ask for the root username and password.

you will see a notification that the printer has been added.

you can then set your printing options.

---

### Post by Stef700 on 2012-03-24
Apologies in advance for my ignorance but:

1/ It's a network connected printer so it doesn't have a "computerNameThatThePrinterIsConnectedTo" (It is ***not*** host connected) so I cannot construct a URL along the lines suggested...

2/ It is not on the list of printers that come up...

As I said earlier there are two new Epson Linux drivers for it (March 2012) and [http://www.openprinting.org/printers](http://www.openprinting.org/printers) seems to suggest that it works well under Ubuntu & Debian (not other versions of Linux) using older revs of these drivers...

Is it possible that this printer could have its own built in ipp server? and if so how to configure to install the drivers and access it ???? :-(

From the printers blurb:

Network Printing Protocols                                                                              TCP/IP: LPR,  IPP,  Port9100,  WSD                                                                                              Network Management Protocols                                                                              TCP/IP: TCP/IPv4,  TCP/IPv6,  SNMP v1,  HTTP,  DHCP,  BOOTP,   AutoIP,  DNS,  Bonjour (mDNS),  SNTP,  SSDP,  WSD,  LLTD,  LLMNR,  SLP,   ENPC

---

### Post by kurt18947 on 2012-03-24
I'm not sure how this will work but I've just brought up the printing window, click 'add printer', 'network printer', 'find Network Printer',  then in the 'Host' window type the I.P. address only no http:// or anything else.  Click forward and see what's found.

---

### Post by Stef700 on 2012-03-24
> **kurt18947 said:**
> I'm not sure how this will work but I've just brought up the printing window, click 'add printer', 'network printer', 'find Network Printer',  then in the 'Host' window type the I.P. address only no http:// or anything else.  Click forward and see what's found.

WOW it Works ! - And isn't the UBUNTU test print page pretty!

I did exactly what you said...

It showed in the DEVICES box: "JetDirect(myip)" which was a bit misleading (for an EPSON!)  but I see where it is coming from!

In the QUEUE box it inserted: "PASSTHRU" and in the CONNECTION box a very long list including
"LDP/LPR QUEUE PASSTHRU" which I selected and then clicked FORWARD. 

It then went and found the correct driver and installed it and it works !

Many thanks!
:guitar:

---

### Post by mörgæs on 2012-03-24
Moved to the hardware forum.

---

### Post by kurt18947 on 2012-03-25
> **stef700 said:**
> wow it works ! - and isn't the ubuntu test print page pretty!

I did exactly what you said...

It showed in the devices box: "jetdirect(myip)" which was a bit misleading (for an epson!)  but i see where it is coming from!

In the queue box it inserted: "passthru" and in the connection box a very long list including
"ldp/lpr queue passthru" which i selected and then clicked forward. 

It then went and found the correct driver and installed it and it works !

Many thanks!
:guitar:

 :D  Glad it worked.

---

