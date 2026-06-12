---
title: "external RAID enclosure with eSata not picked up (no portmultiplier)"
date: 2012-12-19
forum: Hardware
---

### Post by schelleursli on 2012-12-19
Hi guys, I posted this same question already on [askubuntu]("http://askubuntu.com/questions/227009/ubuntu-and-external-raid-enclosure-with-esata-no-portmultiplier"), but maybe it was the wrong platform to search for help on such a specific problem, hopefully somebody can give me a helping hand here.




On to my problem:
  

I've got an External enclosure with 2x1TB hard-disks working in RAID0  mode formatted with ntfs, the whole thing is supposed to be connected  via eSata. The problem seems to be that my motherboard doesn't support port multiplying on my eSata connector, so Ubuntu is seeing it as one big  disk but isn't able to mount it due to a read write error. In the error  message it is telling me to use dmraid if I'm using a soft/fakeraid,  which I guess I do, but since ubuntu only sees one big disk where  there's actually two, dmraid errors with "no raid disks". 
  

I've got a few different BIOS options in which mode to run my sata  controller SATA, RAID, AHCI. I'm running in AHCI mode, tried the others  too but that didn't seem to make a difference.
  

If I switch to my old windows installation on the same computer the  enclosure is getting picked up and I can browse my files. So I guess the  problem is that ubuntu can't cope with my hard disks because of no port multiplying support? I could hook it up with USB2.0 but I'd really  like the additional speed of my eSata port, is there a way to get this  running?
  

Some Infos: 
  PC: ZBOX HD-ND22
  Chipset: NVIDIA ION
  Ubuntu: 12.10 i686
  Kernel: 3.5.0-19-generic
  Parts of Syslog: [http://paste.ubuntu.com/1420234/](http://paste.ubuntu.com/1420234/)
  ntfs-3g and dmraid: [http://paste.ubuntu.com/1420251/](http://paste.ubuntu.com/1420251/)
  Enclosure: Stardom sohoraid sr2 [http://stardom.com.tw/sohoraid_sr2_spec.html](http://stardom.com.tw/sohoraid_sr2_spec.html) (old usb2.0/esata version)
  



I hope those are the most important bits, if I missed anything important I'll be happy to get more information if you tell me what's missing.

---

### Post by schelleursli on 2013-01-08
I seem to be very lonely with that problem, does anybody have a clue where I could get support for this? It runs on windows on the same computer so it must be possible to get it working on ubuntu too?

---

