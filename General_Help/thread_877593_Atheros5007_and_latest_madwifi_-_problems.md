---
title: "Atheros5007 and latest madwifi - problems"
date: 2008-08-01
forum: General Help
---

### Post by DSP8000 on 2008-08-01
Hi guys,

I downloaded some updates and after that my wireless did not work at all. I got the latest madwifi-hal-0.10.5.6-r3835-20080801 from madwifi, installed it but the problem is that the driver it's not autoloading like before. After every restart I have to do modprobe ath_pci and then the wireless gets enabled. Any solutions for this problem? 

Also, is there easier way to install the driver? I think ubuntu should include this driver in the repos as a 1 click install because there's a lot of people that have to go thru this lengthy procedure over and over.

Any help appreciated.
Cheers,
DSP8000

---

### Post by DSP8000 on 2008-08-02
Anyone guys?

---

### Post by ibuclaw on 2008-08-02
Doesn't it require the ath5k drivers, and not the ath_pci ones?

```
find /lib/modules/$(uname -r)/ -iname "*ath*" -print | rev | cut -f 1 -d '/' | rev | grep ".ko"
```
What does that output?

Also, did you run "ifconfig up" on the device?

```
iwconfig
```

Regards
Iain

---

### Post by DSP8000 on 2008-08-02
This is what says on the madwifi web site:

A new HAL has been made available by Sam Leffler (0.10.5.6) that supports AR2425 chips (AR5007* chipsets). This is a full HAL release so it should work for all platforms - that means x86-64.

The new HAL is currently in a branch, but should hopefully, barring any other issues, be migrated to trunk soon. Tarballs are available from [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/) and Subversion access is at [http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](http://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6).

Please use the instructions as in UserDocs/FirstTimeHowTo to compile the code, but substituting the relevant parts for acquiring the source.

Also, it appears that you must reboot if you have loaded a HAL of a different version (this makes me deeply sad - it's not Windows).

Please only report issues other to those in trunk to this ticket. This does not mean issues in the compilation or normal use of the driver.

---

### Post by DSP8000 on 2008-08-03
OK, all up and running.

I had to unload, un-install, reinstall, do modprobe, MANUALLY add ath_pci+ath_hal in /etc/modules after modprobe, enable hardware restricted hardware drivers, restart, viola. Works OK now.

Cheers,
DSP8000

---

