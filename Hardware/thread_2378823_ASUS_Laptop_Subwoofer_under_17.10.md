---
title: "ASUS Laptop Subwoofer under 17.10"
date: 2017-11-27
forum: Hardware
---

### Post by klundermann on 2017-11-27
In the past, I've got the external subwoofer that came with my ASUS Q550 laptop to work by following the instructions posted in [this thread]("https://ubuntuforums.org/showthread.php?t=2217683").  It does not work, however, for the clean install of 17.10 that I recently did,  The first problem was that I could not run  [FONT=System]hdajackretask[/FONT] .  I solved that by following the instructions here for running [FONT=System]synaptic[/FONT] under 17.10.  Then, with  [FONT=System]hdajackretask[/FONT]  open, I made the necessary selections and clicked "Apply now," whereupon I received the error message
[INDENT]tee: /sys/class/sound/hwC1D0/reconfig: Device or resource busy[/INDENT]

Doing a little more digging, I found out that all   [FONT=System]hdajackretask[/FONT]   does is create and execute a shell script called  /tmp/hda-jack-retask-*XXXXXXX,* where *XXXXXXX,* is a more-or-less random string.  All that script does, in turn, is echo a bunch of lines to  [FONT=System]/sys/class/sound/hwC1D0/user_pin_configs[/FONT] .  Each line of that file is of the form   0x*hh* 0x*hhhhhhhh* , where each *h* is a hexadecimal digit. So, I thought, all I need to do is edit  [FONT=System]user_pin_configs [/FONT] manually.

It was easy enough to open  [FONT=System]/sys/class/sound/hwC1D0/user_pin_configs[/FONT]  with  [FONT=system]vi[/FONT] , but here's the weird thing:  the edits I make don't seem to stick.  I write my changes, close the editor and then look at the file, and it is unchanged.

Why can't I alter  [FONT=System]/sys/class/sound/hwC1D0/user_pin_configs[/FONT] ?

Is there another way I could try to get my subwoofer working again?

---

