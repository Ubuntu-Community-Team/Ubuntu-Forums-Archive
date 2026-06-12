---
title: "howto make vsync stick on"
date: 2008-08-13
forum: Hardware
---

### Post by davidmaxwaterman on 2008-08-13
I am running 8.04 on a Lenovo T61 which has &#65306;

nVidia Corporation Quadro NVS 140M (rev a1)

and I am driving two monitors with TwinView.

I enable vsync using the nvidia tool (System/Administrator/NVidia X Server Settings - X Screen 0/OpenGL Settings/Sync to VBlank), but my OpenGL app still tears.

If I restart the X Server (sudo /etc/init.d/gdm restart), the setting reverts to unset.

Anyone have any ideas how to make vsync stick (to enabled)?

Max.

---

### Post by Cresho on 2008-08-13
well, here is something I wrote up.

[http://ubuntuforums.org/showthread.php?t=646356&highlight=antiliasing](http://ubuntuforums.org/showthread.php?t=646356&highlight=antiliasing)

the information is dated.  I cannot update it for some wierd reason.

Your nvidia settings is not being loaded even though you have the drivers installed so you need to do this

1.
system->preferences->sessions add+

name: Nvidia
command: nvidia-settings --load-config-only
comment: Nvidia settings loader

reboot and settings will take effect.  just keek note that this part one will not work if you are running compiz-fusion.  You will need to look at my tutorial up ontop on that link if you are running it.

2.  Are you running compiz-fusion?  follow the above tutorial link

if not, then all you need to do is put everything in sync in the nvidia-settings    (install like sudo apt-get install nvidia-settings) and move the opengl slider to max or min.  Depends on the mood of the driver i guess.

settings will not usually take effect while compiz is running.  you will need to disable and enable it incase you are running it between nvidia-setting changes.

---

### Post by Cresho on 2008-08-13
info reupdated.

---

