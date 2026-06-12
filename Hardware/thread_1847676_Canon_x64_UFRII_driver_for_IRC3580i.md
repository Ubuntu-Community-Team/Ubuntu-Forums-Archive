---
title: "Canon x64 UFRII driver for IRC3580i"
date: 2011-09-21
forum: Hardware
---

### Post by pirulo on 2011-09-21
I had some problem configuring a Canon irc3580i printer on Ubuntu 11.04.

Here is the procedure that worked for me, if this can help somebody.

1. I downloaded the UFR II drivers v2.20 from Canon site and unpacked the files
2. As only RPM files was present for the 64-bits, I converted them:
```

alien cndrvcups-common-2.20-1.x86_64.rpm
alien cndrvcups-ufr2-uk-2.20-1.x86_64.rpm

```
3. Installation:
```

dpkg -i cndrvcups-common_2.20-1_amd64.deb
dpkg -i cndrvcups-ufr2-uk_2.20-1_amd64.deb

```
4. As it seems that part of the drivers are still in 32-bits, I installed the adhoc libraries:
```

apt-get install ia32-libs

```
5. Add the printer, e.g. through the control center -> printers
6. Then I used the Canon apps to configure the printer:
```

sudo cngplp (to configure the properties)
sudo cnjatool -e [Printer Name] (to enable job accounting)
cnjatool -p [Printer Name] (to set the params for job accounting)

```

Ref:
[https://bugs.launchpad.net/ubuntu/+bug/502920]("https://bugs.launchpad.net/ubuntu/+bug/502920")
[https://wiki.edubuntu.org/HardwareSupportComponentsPrintersCanon]("https://wiki.edubuntu.org/HardwareSupportComponentsPrintersCanon")

---

### Post by pki on 2012-03-13
Hi!

I tried aliening the package, tried compiling from source and many other ways in 12.04 beta 64bit. The only way i get the UFR driver to work was reinstalling the system to 32bit (with pae). Then installed the .deb from canon (2.20) and it;s working out of the box. ):P

---

### Post by pirulo on 2012-04-04
It seems that the drivers are not fully 64bits, so it is important to do step 4.

---

