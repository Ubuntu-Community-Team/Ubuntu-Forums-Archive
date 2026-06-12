---
title: "Printing pdf from Ubuntu 13 to OsX Mavericks using lp"
date: 2014-04-08
forum: Hardware
---

### Post by Warren_Prince on 2014-04-08
I'm having problems printing a pdf from my ubuntu server in the cloud to my local print queue.  The Mavericks server is using cups 1.7.1 and I believe IPP is 2.2.  

The command I'm using is :  lp -h xxx.xxx.xxx.xxx:631 -d "Bechtelsville_Main" CI_700427.pdf.  I know the pdf exists and is valid.  lp returns a request id with the proper job number for Bechtelsville_Main, but CUPS on Bechtelsville_Main reports:  *The file ‘/private/var/spool/cups/d01305-001’ could not be opened."*  

I know the ports and firewall and communications are correct because if i print a shell script instead of the pdf, it prints fine on Bechtelsville_Main.

I've attempted to redirect port 631 directly to the printer, but then I get an error, lp: Error - add '/version=1.1' to server name., but I can't seem to figure out where to put the version=1.1 .

I'd appreciate any help.

---

