---
title: "display &quot;UNCLAIMED&quot;? Ati Radeon 9700 Pro"
date: 2009-02-18
forum: Hardware
---

### Post by fdm on 2009-02-18
i am using ubuntu 8.10, updated. i was looking for the reason why fglrx refuses to work with my card(about to give up) and i found the "lshw" command. it returns my agp card as unclaimed and i dont even see mention of the onboard sis controller(it showed up in windows' device manager for me to disable, maybe linux knows not to bother with it?)

"It means the kernel did not recognize it and no module is mounted."

that being so, lspci  returns the kernel module "radeonfb". suse used the "radeon" module for my card which seemed to be better for it since i could actually get a good resolution with it. aiglx seems to work decently with the card. what is happening for it both to be operational and unrecognised and could this be the reason fglrx cant load with my card?


 sudo lshw -C display

>   *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Radeon R300 ND [Radeon 9700 Pro]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=32 mingnt=8
  *-display:1 UNCLAIMED
       description: Display controller
       product: Radeon R300 [Radeon 9700 Pro] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=32 mingnt=8

---

### Post by fdm on 2009-02-18
i must of been sleep typing. their is no onboard video in this box(its on my older computer with winxp, ick), but i still want to know if "UNCLAIMED" could be the issue with my card and the proprietary driver that for the life in me wont load.

ill even take suggestions for a new agp card that has been proven to install without error and fully supporting 3d(i wouldnt guess out-of-the-box :p)

---

### Post by fdm on 2009-02-23
ati catalyst 9.2 just just got released from ati and it has solved most of my problems. after installing the new driver, hardware drivers pops up saying it has found my card(although it installs useless repository drivers and was ignored, it is cool that it actually recognized my card as opposed to the other, older drivers out their). no more crashing from open source radeon drivers :) new issues include video playback is slow/choppy when in fullscreen(likely my fault), not all compiz effects work, and fglrx completely ignores resolutions given to it(even with aticonfig). apart from that, games play millions of times faster and with full opengl 2.1 support. THANKS ATI!!!

>   *-display:0             
       description: VGA compatible controller
       product: Radeon R300 ND [Radeon 9700 Pro]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
  *-display:1 UNCLAIMED
       description: Display controller
       product: Radeon R300 [Radeon 9700 Pro] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=32 mingnt=8

---

### Post by nixIT on 2009-02-23
how did you install the catalyst 9.2 drivers?  Are you using a widescreen monitor?

---

### Post by fdm on 2009-02-23
by building and installing the packages from the file "ati-driver-installer-9.2-x86.x86_64.run" on ati's site. way too many things are broken in this driver in regards to my card, but at least they support it now(at least half of it, they forgot to add tv-out support). maybe xv will be fixed next month so i can watch videos in fullscreen, lol.

edit: nope, just a regular crt. the issue with the resolution is from fglrx probing my monitor at startup, ignoring preset values. havent found a workaround for that yet.

---

