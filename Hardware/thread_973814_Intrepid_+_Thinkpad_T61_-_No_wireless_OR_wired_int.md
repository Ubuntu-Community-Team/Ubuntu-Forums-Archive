---
title: "Intrepid + Thinkpad T61 - No wireless OR wired internet after update!"
date: 2008-11-07
forum: Hardware
---

### Post by azredwing on 2008-11-07
Hi all,

Just installed Intrepid on my notebook. I did a couple updates and now both my wireless and wired connections are dead. Apparently the wireless issue was a fixed bug, but I can't get online to get the update since my wired connection won't work, either. network-manager doesn't detect it, but lspci does fine:

> 
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev03)


Any ideas on how to get this up and running? Thanks!

EDIT: I got the wire working. Install the following driver:

[http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=3003&DwnldID=15817&agr=Y&lang=eng&PrdMap=3003](http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=3003&DwnldID=15817&agr=Y&lang=eng&PrdMap=3003)

Then, 

```

$ sudo rmmod e000e; sudo modprobe e000e

```

I was able to get my ethernet to detect, and I am currently running apt-get upgrade. I'll let you know once the wireless is working again. Hopefully this helps somebody out!

---

### Post by azredwing on 2008-11-07
I'm writing this from the airport, so clearly the wireless got fixed in the last update :O again, hope this helps anybody whose wired AND wireless devices got hosed while upgrading to Intrepid...

---

