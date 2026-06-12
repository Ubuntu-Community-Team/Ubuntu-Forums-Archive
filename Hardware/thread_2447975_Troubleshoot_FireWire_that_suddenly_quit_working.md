---
title: "Troubleshoot FireWire that suddenly quit working"
date: 2020-07-29
forum: Hardware
---

### Post by Steve_Corman on 2020-07-29
I posted about this on General Help about a week ago, but I think I should have posted here because this is where other FireWire issues are posted (sorry for the cross-posting).  I had been using FireWire on an Ubuntu 16.04 machine to control channel changes on a cable set-top-box.  It worked fine for years, then suddenly stopped working.  I just upgraded to Ubuntu 18.04 and it is still not working.  lspci shows the device is there:  
```
06:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```
sudo plugreport gives:
```
Host Adapter 0
==============

Node 0 GUID 0x00e6bc100000241d
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

```
If memory serves me, when my setup was working there was a Node 1 where the cable box actually lived.

  Searching around on this error led me to an [old thread in a redhat bug tracker]("https://bugzilla.redhat.com/show_bug.cgi?id=240770") that says it's a problem with the OS not chowning the firewire device on boot up.  When I check permissions on /dev/fw0 I get:
```
crw------- 1 root root 241, 0 Jul 27 18:31 fw0
```
That matches what is in the bug report, though I never checked this permission when I had a working system so I don't know if this is really a problem. I also don't get why the OS would need to chown a device on startup.

Can anyone advise how to troubleshoot this, or have any guesses what the problem could be?

---

