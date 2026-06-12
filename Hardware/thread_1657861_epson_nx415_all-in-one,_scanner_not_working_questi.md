---
title: "epson nx415 all-in-one, scanner not working question"
date: 2011-01-01
forum: Hardware
---

### Post by Heeter on 2011-01-01
Hi all,

I am trying to get the scanner part working with my Ubuntu10.10 32bit.

The printer was picked up and working flawlessly, but cannot get the scanner part.

Xsane was not able to pick it up when scanning for a device.

I found a scanner driver called "iscan-network-nt_1.1.0-2_i386.deb" from the epson site, but the software center is giving me errors when I tried installing it.

Any assistance with be greatly appreciated.



Heeter

---

### Post by GaryUK on 2011-02-24
> **Heeter said:**
> Hi all,

I am trying to get the scanner part working with my Ubuntu10.10 32bit.

The printer was picked up and working flawlessly, but cannot get the scanner part.

Xsane was not able to pick it up when scanning for a device.

I found a scanner driver called "iscan-network-nt_1.1.0-2_i386.deb" from the epson site, but the software center is giving me errors when I tried installing it.

Any assistance with be greatly appreciated.



Heeter

Heeter,

You need the iscan-network-nt, iscan and iscan-data packages from the Avasys site - google "epson linux drivers" for the english site.

Install these by using GDebi - double-click on the downloaded package entries in Nautilus should cause them to be opened by linux within GDebi and then you should get the option to install.

See my post:

[http://ubuntuforums.org/showthread.php?p=10491257]("http://ubuntuforums.org/showthread.php?p=10491257")

You should only need to edit the blacklist if your all-in-one is not officially supported - if it is supported, then just edit the epkowa.conf file and the dll.conf file as I describe.

Good Luck!!

Gary.

---

### Post by Heeter on 2011-02-24
Yahoo!

Thanks Gary!

***runs off to go try it out***


Heeter

---

### Post by GaryUK on 2011-02-24
> **Heeter said:**
> Yahoo!

Thanks Gary!

***runs off to go try it out***


Heeter

Pleasure - I am sure that I can get it fixed for you if it still does not work - let me know how you get on.

Good Luck!!

---

### Post by Heeter on 2011-03-05
Hi gary,

Sorry about late with this post. I did not have access to this machine scanner since a while ago.

I did hit a snag:

The package installer is telling me:

```
Dependency is not satisfiable: iscan (>= 2.21.0)
```

This is with the "iscan-network-nt_1.1.0-2_i386.deb" package I downloaded from Avysis.

I cannot locate a iscan-network-nt version 2.21.0 around.


As well,

I don't need to edit the epkowa.conf file, because I am using USB, correct?

I don't see my NX415 in the blacklist file.


Thanks a million for your assistance so far, Gary.



Heeter

---

### Post by GaryUK on 2011-03-18
Heeter,

You should not need the "iscan-network-nt_1.1.0-2_i386.deb" package as it is for networked scanning. If you have installed it, then remove it with synaptic.

You should just require the appropriate iscan (not nt) and iscan-data packages from [here]("http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do").

In the epkowa.conf file you should have "usb" uncommented out at line 10 and the scanner should autodetect if you are connected via usb - if it does not autodetect, then you should be able to manually configure according to the second section of the epkowa.conf file.

Hope this Helps.....

Gary.

---

### Post by Heeter on 2011-03-27
Thanks GaryUK,

I was mistakingly editing the wrong epkowa.conf file.

Now I got the right one, it is working like a charm!!!

Thanks a million, again, GaryUK



Heeter

---

