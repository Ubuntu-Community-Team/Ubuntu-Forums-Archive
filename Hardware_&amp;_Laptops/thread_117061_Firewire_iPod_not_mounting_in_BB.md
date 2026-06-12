---
title: "Firewire iPod not mounting in BB"
date: 2006-01-14
forum: Hardware &amp; Laptops
---

### Post by knichel on 2006-01-14
I have a 30G iPod that is firewire. When I plug it in, It doesnt mount. I ran dmesg and got the following info...

[4297922.922000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[4297922.922000] ieee1394: Node suspended: ID:BUS[0-00:1023] GUID[000a2700020f5938]
[4298151.515000] ieee1394: Node resumed: ID:BUS[0-00:1023] GUID[000a2700020f5938]
[4298151.515000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[4298151.515000] scsi6 : SCSI emulation for IEEE-1394 SBP-2 Devices


Not sure what to make of it. I just want to be able to use my iPod with ubuntu. I am trying to file for divorce from Microsoft.

Please help a ubuntu (linux) newbie. I really like ubuntu so far.

--
mike

---

### Post by bernardfrancois on 2006-01-18
Another great source of information is the ubuntu wiki.
There is some information about IPod's out there: [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ipod&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=ipod&titlesearch=Titles)

You can use that page to learn more stuff about Ubutnu, I think theres a 'getting started' or something like that as well.

If you aren't scared of using a CLI (command line interface), then you can start with the following commands:
man -a intro
man bash

You'll discover it's very powerful and it's a great advantage over windows.

You can also try newbiedoc (needs to be installed with synaptic first).

btw: welcome

---

