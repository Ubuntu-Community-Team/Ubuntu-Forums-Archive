---
title: "Cups slow printing with FUJI XEROX DocuCentre-V 4070"
date: 2023-03-13
forum: Hardware
---

### Post by andrefidelidade on 2023-03-13
Hi all,

I really need your help to try to figure out why printing to the FUJI XEROX DocuCentre-V 4070 is slow that expected. This is a network printer connected via cable to the local network.

In the current setup we are only able to print 1 document every 4 seconds under heavy load (with around 180 documents waiting in queue) in production environment, although the printer is capable of handling much more. From what I can see, must of documents printed have 2 pages.

For the printer driver we are using the package **printer-driver-fujixerox/focal,now 1.1.0+ds-3 amd64**, which is a generic driver used for several fujixerox printers this one included.

For cups the version installed is **2.3.1-9ubuntu1.2**

In the meanwhile, I have tried the following to fix the problem:

[LIST]
[*]Add the flag ?waiteof=false (which helped a little)
[*]Set the cups flag BrowseLocalProtocols to none (which didn't help)
[/LIST]

I have been searching around the web without much success.

Your help is much appreciated.

André

---

