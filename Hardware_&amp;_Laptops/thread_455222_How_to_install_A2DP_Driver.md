---
title: "How to install A2DP Driver ??"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by frojnd on 2007-05-26
I wanna to download bluetooth-alsa driver so I could use headset. I was installing it by this tutorial: [http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html)  All fine and good untill I came to part where u have to install A2DP Driver. I can't find it I can find. I should make command: cp alsa-plugins/sample.a2dprc ~/.a2dprc but I don't have sample.a2dprc neither a2dprc. List of files that are in alsa-plugins: 

a2dpd        BUILD       CVS                          Makefile     pcm_sco.lo
a2dp.h       ctl_sco.c   headsetd                     Makefile.am  pcm_sco.o
asound.conf  ctl_sco.lo  libasound_module_ctl_sco.la  Makefile.in
avrcp.h      ctl_sco.o   libasound_module_pcm_sco.la  pcm_sco.c

And files that are in the folder alsa-plugins/a2dpd/

a2dpd                      a2dpd_ipc.o          com.access.a2dpd.service
a2dpd-a2dpd_avrcp.o        a2dpd_mixer.c        com.access.a2dpd.service.in
a2dpd-a2dpd_dbus.o         a2dpd_mixer.h        ctl_a2dpd.c
a2dpd-a2dpd_mixer.o        a2dpd_output_a2dp.c  ctl_a2dpd.lo
a2dpd-a2dpd.o              a2dpd_output_a2dp.h  ctl_a2dpd.o
a2dpd-a2dpd_output_a2dp.o  a2dpd_output_alsa.c  CVS
a2dpd-a2dpd_output_alsa.o  a2dpd_output_alsa.h  liba2dpdcommon.la
a2dpd-a2dpd_output_sco.o   a2dpd_output_sco.c   libasound_module_ctl_a2dpd.la
a2dpd-a2dpd_sdp.o          a2dpd_output_sco.h   libasound_module_pcm_a2dpd2.la
a2dpd-a2dpd_uinput.o       a2dpd_protocol.h     libasound_module_pcm_a2dpd.la
a2dpd_avrcp.c              a2dpd_sdp.c          Makefile
a2dpd_avrcp.h              a2dpd_sdp.h          Makefile.am
a2dpd.c                    a2dpd_timer.c        Makefile.in
a2dpd.conf                 a2dpd_timer.h        pcm_a2dpd2.c
a2dpd_ctl                  a2dpd_timer.lo       pcm_a2dpd2.lo
a2dpd_ctl-a2dpd_ctl.o      a2dpd_timer.o        pcm_a2dpd2.o
a2dpd_ctl.c                a2dpd_tools.c        pcm_a2dpd.c
a2dpd_dbus.c               a2dpd_tools.h        pcm_a2dpd.lo
a2dpd_dbus.h               a2dpd_tools.lo       pcm_a2dpd.o
a2dpd_ipc.c                a2dpd_tools.o        sample.a2dprc
a2dpd_ipc.h                a2dpd_uinput.c
a2dpd_ipc.lo               a2dpd_uinput.h


Can someone tell me how to install or edit this driver since I didn't find any forum on the official page of bluetooth-alsa.

Tnx in advance.

---

### Post by Ubu-Slack on 2007-08-22
Any Make error/warning output?

for me, remove automake pkg and instal automake-1.9 resolve the pb.

---

