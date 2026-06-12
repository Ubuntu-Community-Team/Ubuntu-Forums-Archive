---
title: "Network Printer error"
date: 2020-04-27
forum: Hardware
---

### Post by heroquestelf on 2020-04-27
I'm running a Dell Inspiron I3670 with the new Focal Fossa 20.04 LTS and I cannot get it to talk to my Epson Workforce Pro WF-4734 network printer.

The problem SEEMS to be with CUPS, but I've been digging through Google and all of the answers I've found have been in computer language that was over my head.

I've tried reinstalling the printer several times. I even went to the Epson website and downloaded their "epson-inkjet-printer-escpr2_1.1.11-1lsb3.2_amd64.deb" printer utility, which added an "Epson Inkjet printer #1" option to my printer install interface. Still, regardless of what I try, I still keep getting the 'server-error-internal-error' error. 

The computer recognizes that I have a printer on the network. The computer can obviously see it. I just can't print to it. When I try and print to it, it gives me the following error: Stopped - No destination host name supplied by cups-browsed for printer "EPSON_WF_4730_Series", is cups-browsed running?

I've tried stopping and restarting the CUPS service, but that doesn't seem to help. Can anyone provide me with any guidance?

edit: I was able to get a different driver installed, and now it appears to recognize the printer, but when I try to print a test page it stops at "Processing: Rendering completed"

---

### Post by heroquestelf on 2020-04-27
I'm going to leave this up in order to help anyone else who might run into the same problem, but I solved the issue by installing (reinstalling?) Puppet (or "Puppet-CUPS")

I ran the command

> sudo apt install puppet

and then reinstalled the network printer and everything now works perfectly!!

---

### Post by jjconstru1 on 2020-04-30
Would this work with Ubuntu 18.04 and HP 1512 printer? My printer failed after general updates. Cups was not working, now is working. Printer menu appears when print is activated, but printer does nothing. In my dual boot with windows 7, the printer still works fine in windows. My printer software is HP 3.17.10 repack0-5. Any help would be appreciated. Soon, I'll try reloading Ubuntu OS.

---

