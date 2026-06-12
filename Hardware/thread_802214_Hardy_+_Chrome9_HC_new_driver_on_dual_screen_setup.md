---
title: "Hardy + Chrome9 HC new driver on dual screen setup"
date: 2008-05-21
forum: Hardware
---

### Post by slashbreak on 2008-05-21
Heya guys,

I've installed the latest driver from VIA and have 3d acceleration active now, which is great. However, I'm unable to use my laptop's monitor while this driver is installed - only the external one. Same story when no external monitor is connected, and when installed without 2nd monitor attached.

If I uninstall the driver I can get display working on laptop, and a badly mirrored copy unto the external display. However, no 3D graphics, etc are availble (obviously).

I've tried countless variations of the xorg.conf to no avail, so I thought I;d ask here and see if anyone can help me out? :)

Spec.

Fujitsu AMILO Pro v3515 (1280x800)
VIA Chrome9 HC chipset
AG Neovo F-15 external monitor
Ubuntu 8.04

Also, I dual boot with XP, and there I have a working dual screen setup + 3D accel. 

Regards, slashbreak

---

### Post by gnuslov on 2008-05-31
When you say  latest driver from via, I assume you mean from [here?]("http://linux.via.com.tw") Check out the viax.conf file from the tarball you download.  There are all manner of options for the driver listed there, a lot of them having to do with driving external displays.  Look through and experiment a bit, and see if any of them help (it'd be nice if there were more helpful comments in that file though. a lot of those options are awfully obscure).

---

