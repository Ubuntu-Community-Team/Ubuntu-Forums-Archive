---
title: "Thinkpad L420 Intel video card low resolution"
date: 2011-09-05
forum: Hardware
---

### Post by patrick.huang on 2011-09-05
Hi all,

I've got a thinkpad L420 with intel integrated video card. It displays however I only get to choose from 1024*768 or 800*600. The highest resolution should be 1366*768 as in windows. I don't know what I need to do to make this happen. Do I need a driver?

I am using 10.04. I don't like unity so please don't make me upgrade:P

$lshw -C display
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f03fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=64)

sysinfo application displays as:
VGA compatible controller
Intel Corporation Device 0126 (rev 09)
subsystem: lenovo Device 21dd

Big Thanks!

---

### Post by abtekk on 2011-09-05
You say you don't want to upgrade because of unity, but you do know you can switch it off and go back to the same gnome desktop as in 10.04?

---

### Post by patrick.huang on 2011-09-05
> **abtekk said:**
> You say you don't want to upgrade because of unity, but you do know you can switch it off and go back to the same gnome desktop as in 10.04?

Yes I do, as classic desktop AFAI remember. But sometimes the menu bar will disappear and mouse pointer seems shifted. I have to disable visual effect to make it stable. After all the trial and error I gave up.

---

### Post by realzippy on 2011-09-05
get a newer version of the intel driver and linux kernel:


```
sudo add-apt-repository ppa:glasen/intel-driver
```
```
sudo add-apt-repository ppa:kernel-ppa/ppa
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install linux-headers-2.6.38-8-generic linux-image-2.6.38-8-generic
```


Reboot or restart x server.
If it is still not working,show output from:

```
uname -a
```

---

### Post by patrick.huang on 2011-09-06
> **realzippy said:**
> get a newer version of the intel driver and linux kernel:


```
sudo add-apt-repository ppa:glasen/intel-driver
```
```
sudo add-apt-repository ppa:kernel-ppa/ppa
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install linux-headers-2.6.38-8-generic linux-image-2.6.38-8-generic
```


Reboot or restart x server.
If it is still not working,show output from:

```
uname -a
```
Thanks for the reply. The ppa seems to be successfully added.
But when I execute

$sudo apt-get install linux-headers-2.6.38-8-generic linux-image-2.6.38-8-generic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.38-8-generic

$uname -a

Linux l420 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux

After reboot nothing changes.

---

### Post by realzippy on 2011-09-06
try:
```
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty
```

---

### Post by patrick.huang on 2011-09-06
Thank you so much!!! It works now.

---

### Post by realzippy on 2011-09-06
Fine.
Thanks go to Stefan Glasenhardt who made those intel drivers available for 10.04.....
I know from his blog that he enjoys getting postcards from all over the world if you want to thank him...

---

