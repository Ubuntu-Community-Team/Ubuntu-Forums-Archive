---
title: "iwl3945/iwl4965 with LED support, Hardy DKMS package"
date: 2008-09-19
forum: Hardware
---

### Post by IntuitiveNipple on 2008-09-19
I've built a DKMS (Dynamic Kernel Module Support) package containing the Intel WiFi iwl3945 and iwl4965 drivers with LED support for Hardy.

The package is based on the hardy linux-backports-modules source but, being DKMS, is automatically built and installed if the kernel is upgraded.

It is available from my Ubuntu PPA (Personal Package Archive). To install it add my PPA to apt's source list:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo apt-get update

```
and then install the package:
```

sudo apt-get install iwl-led-dkms

```
Remove my PPA from the apt sources to prevent unexpected upgrades of packages I maintain:
```

sudo rm /etc/apt/sources.list.d/intuitivenipple.list
sudo apt-get update

```

---

### Post by maxonline on 2009-02-26
Hi,
for my Dell Latitude D630 I'm trying your package ( Hardy 8.04.2 ) but unfortunately apt-get install end with following error :

```
Good news! Module version  for iwlwifi_rc80211_simple.ko
exactly matches what is already found in kernel 2.6.24-23-generic.
DKMS will not replace this module.
You may override by specifying --force.
dpkg: error processing iwl-led-dkms (--configure):
 subprocess post-installation script returned error exit status 101
Errors were encountered while processing:
 iwl-led-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Could you help me ?

Thanks

max

---

### Post by IntuitiveNipple on 2009-02-26
It looks as if kernel updates have made that module match the one created by the DKMS package and DKMS tries to be helpful by not replacing the kernel's version. It then quits which causes the package installation error.

I suspect the solution is to run the DKMS installation manually. First, find out what DKMS modules and versions are being managed:
```

dkms status

```
Then try to install it using:
```

sudo dkms install --force -m ... -v ...

```
Replace ... with the module-name and version determined by the previous 'status' operation.

If that fails it may be it needs the module building first, in which case:
```

sudo dkms build -m ... -v ...

```
followed by the 'install' operation should work

---

### Post by maxonline on 2009-02-26
Thanks for your prompt help.

I following your instruction, but due to the fact that I've not any skill on dkms, I need some help again.

So 

```
$ sudo dkms status
$ iwl-led, 1.2, 2.6.24-23-generic, i686: built
```

Then

```
$ sudo dkms --force -m iwl-led -v 1.2
```

but without any information/result/error ?!

This means that every thing was ok ? ( FYI WiFi led still off but I haven't reboot yet )

max

---

### Post by richbl on 2009-02-28
> **IntuitiveNipple said:**
> I've built a DKMS (Dynamic Kernel Module Support) package containing the Intel WiFi iwl3945 and iwl4965 drivers with LED support for Hardy.
...

Any chance that this will work with Ibex?

I'm dealing with a problematic iwl3945 driver, and am hoping to give this a try.

Also, what's the procedure for removing this package? A simple apt-get remove?

thanks,

rich

---

