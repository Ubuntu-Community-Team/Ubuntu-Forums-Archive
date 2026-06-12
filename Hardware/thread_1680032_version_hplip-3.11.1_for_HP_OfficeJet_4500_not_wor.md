---
title: "version hplip-3.11.1 for HP OfficeJet 4500 not working"
date: 2011-02-01
forum: Hardware
---

### Post by freesparks on 2011-02-01
Hello all,

   Well, Ive tried and tried and have had no luck configuring my HP OfficeJet 4500 multifunctional printer.  I ran  sh hplip-3.11.1.run and went through the entire install and opted to restart, when the machine rebooted I ran hp-setup inside the newly created hplip-3.11.1 directory, went though that setup, then temporarily connected the printer to the cpu via usb only to get after specifying my SSID:

```
error: GetHostname returned an error: executionfailed
```

Can anyone tell me what is causinf this?  In the past I remember successfully setting up a similar printer using http:localhost:631/, only to later go through the install process located:

[http://hplipopensource.com/](http://hplipopensource.com/)

Any help on this would be greatly appreciated.

Best Regards,

freesparks

---

### Post by vikrang on 2011-02-17
I have a hp 1050 j 410 (All in one)..I am not able to scan any document ..The hp site suggests to install the latest driver 3.11 ..This is not currently available in Synaptic (10.04 or 10.10) ..I am not comfortable in doing the make install way as in my limited experience , I have found that packages installed this way are detached from the main stream of applications in Synaptic and the Icons dont show up in the menu...Also I do not know how to convert source tarball to deb (.deb)..I read the dpkg tutorial but sort of difficult for me..
 
Is there any app like src2pkg (in slack) wherein you give the tarball address and it gets converted to .deb immly?

---

