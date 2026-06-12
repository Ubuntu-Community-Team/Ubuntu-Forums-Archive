---
title: "Setting up a network printer w. no desktop environment"
date: 2008-08-31
forum: Hardware
---

### Post by adcwoef on 2008-08-31
Hello


I would like to set up a network printer on my system. The printer works fine in Ubuntu, OS X and Windows and it's easy to install. But now I want to set it up on my other machine which has no desktop environment (no x) and therefore no easy click-dialogs to set up the printer from. I have Googled around the web for a while but I did not find out how. One term that I came across on pretty mucg every site is 'CUPS - common UNIX printing something'. But the CUPS seems to be a program for settings up a printing server which is not what I want to do. I just want to connect to a network printer directly with the TCP/IPv4-protocols.

I would love some help from you guys ;-) Anything from tips, links to tutorial, guides, manuals etc. My Googles skills failed me this time.

Thanks.

---

### Post by IntuitiveNipple on 2008-08-31
Assuming the printer is *published* on the local PC (check using [http://localhost:631/printers/](http://localhost:631/printers/)) it can be added on a remote system from the command line using (on the remote system of course!):
```

lpadmin -E -p <PrinterLocalName> -v <Printer-URI>

```
So, for example, if on the host 'printserver' there's a printer named 'Deskjet995C', on the remote system you'd do:
```

lpadmin -E -p Deskjet995C -v ipp://printserver/printers/Deskjet995C

```
"-E" enables the printer and makes it ready for accepting jobs.
"-p ..." is the local name given to the printer.

To check the new printer's options:
```

lpoptions -p Deskjet995C

finishings=3 copies=1 job-hold-until=no-hold job-priority=50 
number-up=1 auth-info-required=none job-sheets=none,none
printer-info=Deskjet995C printer-is-accepting-jobs=1 printer-is-shared=0
printer-location printer-make-and-model='Remote Printer' printer-state=3
printer-state-change-time=1220213912 printer-state-reasons=none
printer-type=2097158

```

---

