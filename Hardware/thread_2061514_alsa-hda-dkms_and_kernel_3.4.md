---
title: "alsa-hda-dkms and kernel 3.4"
date: 2012-09-22
forum: Hardware
---

### Post by mud2005 on 2012-09-22
hello fellow ubuntu users, I have a Toshiba p875 s7200 laptop and at first I had no sound (except through headphones), then I installed alsa-hda-dkms and had sound from speakers, but I was having another issue with the system freezing. So I installed latest kernel 3.4.4 and freezing problem is fixed, but I have no sound again and when I try to install alsa-hda-dkms I get error: 

Building only for 3.4.4-030404-generic
Building for architecture i686
Building initial module for 3.4.4-030404-generic
ERROR (dkms apport): kernel package linux-headers-3.4.4-030404-generic is not supported
Error! Bad return status for module build on kernel: 3.4.4-030404-generic (i686)
Consult /var/lib/dkms/alsa-hda/0.201209221211~precise1/build/make.log for more information.
dpkg: error processing alsa-hda-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 alsa-hda-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)


any help greatly appreciated, I ran the alsa-info script and uploaded the info here: [http://www.alsa-project.org/db/?f=966b93130af762594ff8bcea8f656e94bc1dba2f](http://www.alsa-project.org/db/?f=966b93130af762594ff8bcea8f656e94bc1dba2f)

---

### Post by mud2005 on 2012-09-22
I tried installing kernel 3.3.6 and then alsa-hda-dkms and it worked as far as no errors, but no sound at all even with headphones :(

---

