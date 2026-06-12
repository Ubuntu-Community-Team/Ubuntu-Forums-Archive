---
title: "Problem with ATI 5650"
date: 2011-08-23
forum: Hardware
---

### Post by ziocane1 on 2011-08-23
Hi guys,

I have got a notebook acer aspire 5553g, with 2 graphic cards: 5650 and the integrated one.

```
marco@marco-laptop:~$ lshw -c display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: M880G [Mobility Radeon HD 4200]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:c0000000-cfffffff ioport:9000(size=256) memory:d8100000-d810ffff memory:d8000000-d80fffff
  *-display
       description: VGA compatible controller
       product: Redwood [Radeon HD 5600 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:46 memory:d0000000-d7ffffff memory:d8300000-d831ffff ioport:a000(size=256) memory:d8340000-d835ffff
marco@marco-laptop:~$ lspci | grep -i vga
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]

```I'm using Lucid 32 bit with the kernel 2.6.39. The drivers in use are the radeon because the catalyst doesn't works with that kernel.

```
marco@marco-laptop:~$ lshw -c display | grep driver
WARNING: you should run this program as super-user.
       configuration: driver=radeon latency=0
       configuration: driver=radeon latency=0
marco@marco-laptop:~$ dpkg -l | grep fglrx
iF  fglrx                                             2:8.723.1-0ubuntu5                                Video driver for the ATI graphics accelerato
iU  fglrx-amdcccle                                    2:8.723.1-0ubuntu5                                Catalyst Control Center for the ATI graphics
ii  fglrx-modaliases                                  2:8.723.1-0ubuntu5                                Identifiers supported by the ATI graphics dr

```I think that the system is using the integrated graphic card, how can I solve this problem and the other one about the drivers?

Thank you

---

### Post by ziocane1 on 2011-08-25
Nobody can help me? Some news:

 lucid 32 bit, kernel pae 2.6.32-34 o 2.6.39 (non-pae).
My machine has the Radeon 5650, but the system is using the 4200 as the default. The 5650 is there, the system can see it, I just can't use it. It's very frustrating, am I just wasting my time?


```
System > administration > driver hardware > no propretary driver are in use in that system
System > preferencee > there is AMD ccc but I can't open it: Impossible open «AMD Catalyst Control Center» can't esecute "amdcccle"  (File o directory don't exist)
```


I would install the new AMD fglrx 11.8 but I can't for a precedent installation.
I installed it: 



```
chmod a+x ati-driver-installer-11-8-x86.x86_64.run
sudo sh ./ati-driver-installer-11-8-x86.x86_64.run
```I can't unistall it.. I  removed all about fglrx by synaptic and I followed that how to:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Locate:


```
marco@marco-laptop:~$ dpkg -l '*fglrx*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Nome           Versione       Descrizione
+++-==============-==============-============================================
un  fglrx          <non definita> (nessuna descrizione disponibile)
un  fglrx-amdcccle <non definita> (nessuna descrizione disponibile)
un  fglrx-control  <non definita> (nessuna descrizione disponibile)
un  fglrx-control- <non definita> (nessuna descrizione disponibile)
un  fglrx-modalias <non definita> (nessuna descrizione disponibile)
marco@marco-laptop:~$ locate fglrx
/etc/profile.d/ati-fglrx.sh
/lib/modules/2.6.39-020639-generic/updates/dkms/fglrx.ko
/usr/X11R6/lib/modules/dri/fglrx_dri.so
/usr/lib/fglrx
/usr/lib/libfglrx_dm.a
/usr/lib/libfglrx_dm.so.1.0
/usr/lib/fglrx/FGL.renamed.libGL.so.1.2
/usr/lib/fglrx/etc
/usr/lib/fglrx/fglrx-libGL.so.1.2
/usr/lib/fglrx/libXvBAW.so.1
/usr/lib/fglrx/switchlibGL
/usr/lib/fglrx/switchlibglx
/usr/lib/fglrx/etc/ati
/usr/lib/fglrx/etc/ati/amdpcsdb
/usr/lib/fglrx/etc/ati/inst_path_default
/usr/lib/fglrx/etc/ati/inst_path_override
/usr/lib/xorg/modules/extensions/fglrx
/usr/lib/xorg/modules/extensions/fglrx/fglrx-libglx.so
/usr/lib/xorg/modules/linux/libfglrxdrm.so
/usr/share/app-install/desktop/fglrx-driver.desktop
/usr/share/apport/package-hooks/source_fglrx-installer.py
/usr/share/ati/fglrx-install.log
/usr/share/ati/fglrx-uninstall.sh
/usr/share/doc/fglrx-modaliases
/usr/share/jockey/handlers/fglrx.py
/usr/share/jockey/handlers/fglrx.pyc
/usr/share/jockey/modaliases/fglrx-modules.alias.override
/usr/src/fglrx-8.881
/usr/src/ati/fglrx_sample_source.tgz
/usr/src/fglrx-8.881/2.6.x
/usr/src/fglrx-8.881/Makefile
/usr/src/fglrx-8.881/dkms.conf
/usr/src/fglrx-8.881/drm.h
/usr/src/fglrx-8.881/drmP.h
/usr/src/fglrx-8.881/drm_compat.h
/usr/src/fglrx-8.881/drm_os_linux.h
/usr/src/fglrx-8.881/drm_proc.h
/usr/src/fglrx-8.881/fglrxko_pci_ids.h
/usr/src/fglrx-8.881/firegl_public.c
/usr/src/fglrx-8.881/firegl_public.h
/usr/src/fglrx-8.881/kcl.c
/usr/src/fglrx-8.881/kcl.h
/usr/src/fglrx-8.881/kcl_acpi.c
/usr/src/fglrx-8.881/kcl_acpi.h
/usr/src/fglrx-8.881/kcl_agp.c
/usr/src/fglrx-8.881/kcl_agp.h
/usr/src/fglrx-8.881/kcl_config.h
/usr/src/fglrx-8.881/kcl_debug.c
/usr/src/fglrx-8.881/kcl_debug.h
/usr/src/fglrx-8.881/kcl_io.c
/usr/src/fglrx-8.881/kcl_io.h
/usr/src/fglrx-8.881/kcl_ioctl.c
/usr/src/fglrx-8.881/kcl_ioctl.h
/usr/src/fglrx-8.881/kcl_iommu.c
/usr/src/fglrx-8.881/kcl_iommu.h
/usr/src/fglrx-8.881/kcl_osconfig.h
/usr/src/fglrx-8.881/kcl_pci.c
/usr/src/fglrx-8.881/kcl_pci.h
/usr/src/fglrx-8.881/kcl_str.c
/usr/src/fglrx-8.881/kcl_str.h
/usr/src/fglrx-8.881/kcl_type.h
/usr/src/fglrx-8.881/kcl_wait.c
/usr/src/fglrx-8.881/kcl_wait.h
/usr/src/fglrx-8.881/libfglrx_ip.a
/usr/src/fglrx-8.881/make.sh
/usr/src/fglrx-8.881/2.6.x/Makefile
/var/cache/jockey/fglrx.noconf
/var/crash/fglrx.0.crash
/var/lib/dkms/fglrx
/var/lib/dkms/fglrx/8.881
/var/lib/dkms/fglrx/kernel-2.6.39-020639-generic-i686
/var/lib/dkms/fglrx/8.881/2.6.39-020639-generic
/var/lib/dkms/fglrx/8.881/build
/var/lib/dkms/fglrx/8.881/source
/var/lib/dkms/fglrx/8.881/2.6.39-020639-generic/i686
/var/lib/dkms/fglrx/8.881/2.6.39-020639-generic/i686/log
/var/lib/dkms/fglrx/8.881/2.6.39-020639-generic/i686/module
/var/lib/dkms/fglrx/8.881/2.6.39-020639-generic/i686/log/make.log
/var/lib/dkms/fglrx/8.881/2.6.39-020639-generic/i686/module/fglrx.ko
/var/lib/dkms/fglrx/8.881/build/2.6.x
/var/lib/dkms/fglrx/8.881/build/Makefile
/var/lib/dkms/fglrx/8.881/build/dkms.conf
/var/lib/dkms/fglrx/8.881/build/drm.h
/var/lib/dkms/fglrx/8.881/build/drmP.h
/var/lib/dkms/fglrx/8.881/build/drm_compat.h
/var/lib/dkms/fglrx/8.881/build/drm_os_linux.h
/var/lib/dkms/fglrx/8.881/build/drm_proc.h
/var/lib/dkms/fglrx/8.881/build/fglrxko_pci_ids.h
/var/lib/dkms/fglrx/8.881/build/firegl_public.c
/var/lib/dkms/fglrx/8.881/build/firegl_public.h
/var/lib/dkms/fglrx/8.881/build/kcl.c
/var/lib/dkms/fglrx/8.881/build/kcl.h
/var/lib/dkms/fglrx/8.881/build/kcl_acpi.c
/var/lib/dkms/fglrx/8.881/build/kcl_acpi.h
/var/lib/dkms/fglrx/8.881/build/kcl_agp.c
/var/lib/dkms/fglrx/8.881/build/kcl_agp.h
/var/lib/dkms/fglrx/8.881/build/kcl_config.h
/var/lib/dkms/fglrx/8.881/build/kcl_debug.c
/var/lib/dkms/fglrx/8.881/build/kcl_debug.h
/var/lib/dkms/fglrx/8.881/build/kcl_io.c
/var/lib/dkms/fglrx/8.881/build/kcl_io.h
/var/lib/dkms/fglrx/8.881/build/kcl_ioctl.c
/var/lib/dkms/fglrx/8.881/build/kcl_ioctl.h
/var/lib/dkms/fglrx/8.881/build/kcl_iommu.c
/var/lib/dkms/fglrx/8.881/build/kcl_iommu.h
/var/lib/dkms/fglrx/8.881/build/kcl_osconfig.h
/var/lib/dkms/fglrx/8.881/build/kcl_pci.c
/var/lib/dkms/fglrx/8.881/build/kcl_pci.h
/var/lib/dkms/fglrx/8.881/build/kcl_str.c
/var/lib/dkms/fglrx/8.881/build/kcl_str.h
/var/lib/dkms/fglrx/8.881/build/kcl_type.h
/var/lib/dkms/fglrx/8.881/build/kcl_wait.c
/var/lib/dkms/fglrx/8.881/build/kcl_wait.h
/var/lib/dkms/fglrx/8.881/build/libfglrx_ip.a
/var/lib/dkms/fglrx/8.881/build/make.sh
/var/lib/dkms/fglrx/8.881/build/make.sh.log
/var/lib/dkms/fglrx/8.881/build/2.6.x/.fglrx.ko.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.fglrx.mod.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.fglrx.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.firegl_public.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.kcl.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.kcl_acpi.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.kcl_agp.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.kcl_debug.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.kcl_io.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.kcl_ioctl.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.kcl_iommu.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.kcl_pci.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.kcl_str.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.kcl_wait.o.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.libfglrx_ip.a.cmd
/var/lib/dkms/fglrx/8.881/build/2.6.x/.tmp_versions
/var/lib/dkms/fglrx/8.881/build/2.6.x/Makefile
/var/lib/dkms/fglrx/8.881/build/2.6.x/Module.symvers
/var/lib/dkms/fglrx/8.881/build/2.6.x/drm.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/drmP.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/drm_compat.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/drm_os_linux.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/drm_proc.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/fglrx.ko
/var/lib/dkms/fglrx/8.881/build/2.6.x/fglrx.mod.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/fglrx.mod.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/fglrx.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/fglrxko_pci_ids.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/firegl_public.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/firegl_public.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_acpi.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_acpi.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_acpi.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_agp.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_agp.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_agp.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_config.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_debug.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_debug.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_debug.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_io.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_io.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_io.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_ioctl.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_ioctl.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_ioctl.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_iommu.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_iommu.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_iommu.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_osconfig.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_pci.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_pci.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_pci.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_str.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_str.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_str.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_type.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_wait.c
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_wait.h
/var/lib/dkms/fglrx/8.881/build/2.6.x/kcl_wait.o
/var/lib/dkms/fglrx/8.881/build/2.6.x/libfglrx_ip.a
/var/lib/dkms/fglrx/8.881/build/2.6.x/modules.order
/var/lib/dkms/fglrx/8.881/build/2.6.x/.tmp_versions/fglrx.mod
/var/lib/dpkg/info/fglrx-modaliases.list
/var/lib/dpkg/info/fglrx-modaliases.md5sums
marco@marco-laptop:~$ 

```Ls:



```
marco@marco-laptop:~$ ls /usr/share/ati/amdcccle          drv.list            lib           postun_drv.sh
amd-uninstall.sh  fglrx-install.log   libGLdir.txt  postun_km.sh
cp.list           fglrx-uninstall.sh  LICENSE.TXT   preun_doc.sh
doc.list          km.list             postun_cp.sh  preun_km.sh
```
But if I try to install the amd 11.8:



```
a previous install of fglrx has been detected. Please unistall the old version...etc.
```Any Ideas? Tnx

---

### Post by .... on 2011-08-25
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by ziocane1 on 2011-08-28
Finally I solved:

1- disabled the 4200 card in the bios
2- forced the reinstallation of the catalyst 11.8
3- completely removed that driver by this how-to:

- Problem: Need to fully remove -fglrx and reinstall -ati from scratch
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

4- removed the kernel 2.6.39 and  2.6.33 pae
5- installed the 2.6.32 pae kernel
6- installed the propretary driver by jockey

Tnx for the help

---

### Post by .... on 2011-08-28
No, I think you mostly helped yourself. :KS

Please mark the thread solved then.

---

### Post by jamie.nicholson on 2011-08-30
Same problem, using
Radeon HD 4850 

However I was running Lucid with no problems for a long time.  Looks like a recent changed has caused this.

Upgraded from Lucid to 10.10 and then found this after a lot of Googling.  After removing the Catalyst/FGLRX drivers everything just kicked up.

It was really annoying because it wouldn't boot and I had to jump into livecd a lot to remove and add packages......

4 hours later fixed too

---

### Post by Barsoianu Radu on 2011-09-10
Hy my lspci | grep VGA is the following 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)

i have ubuntu 11.04 64 bit and the latest catalyst 11.8 installed. All works fine including swithing graphics, but with a little(big) bug/error/whatever. I get horizontal artefacts everytime i move the mouse. Here is a print screen. Can anyone please help me ? I've followed all steps installed and reinstalled from scrath drivers. My notebook is a Marasst NBLB5. If i stay on the Intel card everything is fine, i move to ati and artefacts all over.

---

### Post by Barsoianu Radu on 2011-09-13
> **Barsoianu Radu said:**
> Hy my lspci | grep VGA is the following 
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)

i have ubuntu 11.04 64 bit and the latest catalyst 11.8 installed. All works fine including swithing graphics, but with a little(big) bug/error/whatever. I get horizontal artefacts everytime i move the mouse. Here is a print screen. Can anyone please help me ? I've followed all steps installed and reinstalled from scrath drivers. My notebook is a Marasst NBLB5. If i stay on the Intel card everything is fine, i move to ati and artefacts all over.

eh...3 days now...no ideea ? anyone ?

---

### Post by howefield on 2011-09-13
> **Barsoianu Radu said:**
> eh...3 days now...no ideea ? anyone ?

You might get more takers with your own thread rather than hijacking someone elses. :)

---

### Post by Barsoianu Radu on 2011-09-14
> **howefield said:**
> You might get more takers with your own thread rather than hijacking someone elses. :)
srry, saw a similar problem with notebook/ati 5650 so i thought it will be solved here :). will post a new thread thx for the advice

---

### Post by SeePU on 2011-09-14
Check the Phoronix forum, too.   There's a section for ATI fglrx and ATI open source drivers there.  Many are very knowledgeable there.

I would upgrade the kernel to at least 2.6.38, also.

---

