---
title: "Intrepid to Jaunty upgrade interupted by power outage"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by Marius Derekus on 2009-07-17
Hello everyone, I was updating from ubuntu studio 8.10 (intrepid) to ubnut studio 9.04 (Jaunty) on my laptop, but during the update my power chord came out and my computer shutdown during the upgrade. When i rebooted and tried to log into ubuntu it initially didnt work. However...i booted into recovery mode and ran the "dpkg" option, then the "fsck" option and then "xfix". After that i was able to boot into ubuntu BUT...whenever i try to finish installing my upgrades (or install any other programs that require "dpgk") my computer says the following:
 

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

However...when i run the command "sudo dpkg --configure -a" i get the following errors:

```
cameron@cameron-laptop:~$ sudo dpkg --configure -a
[sudo] password for cameron: 
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up cupswrapperdcp7020 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperDCP7020-2.0.1: line 63: /usr/share/cups/model/DCP7020.ppd: No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
cp: cannot stat `/usr/share/cups/model/DCP7020.ppd': No such file or directory
dpkg: error processing cupswrapperdcp7020 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up dictionaries-common (1.0.0ubuntu1) ...
Can't locate Text/Iconv.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl5/Debian/DictionariesCommon.pm line 6.
BEGIN failed--compilation aborted at /usr/share/perl5/Debian/DictionariesCommon.pm line 6.
Compilation failed in require at /usr/sbin/update-default-ispell line 3.
BEGIN failed--compilation aborted at /usr/sbin/update-default-ispell line 3.
dpkg: error processing dictionaries-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-officebean:
 openoffice.org-officebean depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-officebean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on openoffice.org-common (>> 1:3.0.1); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gtk depends on openoffice.org-style-human; however:
  Package openoffice.org-style-human is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-binfilter:
 openoffice.org-filter-binfilter depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-filter-binfilter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-report-builder-bin:
 openoffice.org-report-builder-bin depends on openoffice.org-core (>> 1:2.3.0~oog680m1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-report-builder-bin depends on openoffice.org-base (>= 2.3.0~src680m225); however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base-core:
 openoffice.org-base-core depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on openoffice.org-base-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-base-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-report-builder-bin; however:
  Package openoffice.org-report-builder-bin is not configured yet.
 openoffice.org depends on openoffice.org-officebean; however:
  Package openoffice.org-officebean is not configured yet.
 openoffice.org depends on openoffice.org-filter-mobiledev; however:
  Package openoffice.org-filter-mobiledev is not configured yet.
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-vmlinuz-2.6.27-3-rt
Cannot find /lib/modules/vmlinuz-2.6.27-3-rt
update-initramfs: failed for /boot/initrd.img-vmlinuz-2.6.27-3-rt
dpkg: subprocess post-installation script returned error exit status 1
cameron@cameron-laptop:~$ lpadmin: No such file or directory

```

IS there anyway to fix this and get 9.04 installed properly or am i forced to reinstall ubuntu studio from disk.....

Thank you all for any replies

---

### Post by Marcus Derekus on 2009-07-18
Hey bro....still working on that issue?

---

