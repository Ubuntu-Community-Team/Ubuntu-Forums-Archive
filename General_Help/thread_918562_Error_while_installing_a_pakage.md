---
title: "Error while installing a pakage"
date: 2008-09-13
forum: General Help
---

### Post by mmbathan on 2008-09-13
Hi there,

I am a biggener in ubuntu and linux and I want to istall iperf and I got an error. could any iny help me please.

Error message: 
```
bagside@bagvapp:~$ sudo apt-get install iperf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  iperf
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 46.4kB of archives.
After unpacking 184kB of additional disk space will be used.
Err http://archive.ubuntu.com gutsy/universe iperf 2.0.2-2
  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/i/iperf/iperf_2.0.2-2_i386.deb  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Regards,

---

### Post by Ryadt on 2008-09-13
> **mmbathan said:**
> Hi there,

I am a biggener in ubuntu and linux and I want to istall iperf and I got an error. could any iny help me please.

Error message: 
```
bagside@bagvapp:~$ sudo apt-get install iperf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  iperf
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 46.4kB of archives.
After unpacking 184kB of additional disk space will be used.
Err http://archive.ubuntu.com gutsy/universe iperf 2.0.2-2
  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/i/iperf/iperf_2.0.2-2_i386.deb  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Regards,
Try to update> sudo apt-get update
post back any errors if you get any.

---

