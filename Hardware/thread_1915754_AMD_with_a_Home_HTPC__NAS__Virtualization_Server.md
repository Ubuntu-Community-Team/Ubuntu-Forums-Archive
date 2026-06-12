---
title: "AMD with a Home HTPC / NAS / Virtualization Server"
date: 2012-01-26
forum: Hardware
---

### Post by 00trav on 2012-01-26
I was going to post to some hardware forums, but I figured it would probably be best to post here at the source.

Background:  I currently running a hybrid HTPC / NAS server in my apartment (ubuntu of course, with xmbc on the front end). It originally started out as a pure HTPC, then I realized it was more efficient to store all my media files on it, then all my other documents, and now it is pretty much a NAS. In addition, I also run various websites which backup daily or weekly via rsync to the server. Recently it has become unstable freezing randomly.  After weeks of infuriating investigating I can't figure out what is going on, but I am pretty sure it is hardware based (yes, I checked logs and there is NOTHING in the logs which telegraphs what causes the full system freeze).  Given that the current system is just a repurposed old gaming rig, it is probably at its end of life anyway, so I decided it is worth spending the money to get a new system (just for data integrity alone). 

Given that this server has become a general purpose server, I was thinking of dropping some money and getting a fast cpu/mobo (with SATAIII and USB 3.0) and some integrated graphics.  Also, I do development work and find myself spinning up virtual machines for testing and development all the time.  It would be more convenient to be able to spin up the virtual machines from the server and therefore I am willing to spend more and get a system that is on the 'overkill' side so I can run 3-4 virtual machines on it. 

Question:  I am debating between going the AMD FX-6100 route or the AMD Llano (APU) route.  

Specific Questions:
1.  While it appears that ubuntu 11.10 worked out most of the kinks with the APU drivers, I am concerned about virtualization with the APU.  Does anyone have experience?  I am not talking about a fully virtualized environment, but a base ubuntu install with 1-3 VMware player instances or VirtualBox instances running.

2.  One of the cool features of the new AMD FX line is the ability to shut down some cores and ramp up the live cores for better single thread speeds.  I am slightly confused on what the requirements are to achieve this (and if this is a windows only type feature).  (a) is this feature software (driver) related - it seems like from what I have read, it is automatic at the mobo / bios level? (b) does it require an AMD 900 series northbridge?  (c) ultimately, does it make any difference in ubuntu?  Does anyone have any hands on experience with the FX line of processors in ubuntu?  Pretty much all the indepth reviews are windows based. 

Thanks,
Trav

---

