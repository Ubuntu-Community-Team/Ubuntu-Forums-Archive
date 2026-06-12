---
title: "Cups on bubuntu 11.04"
date: 2011-05-24
forum: Hardware
---

### Post by PascalNobus on 2011-05-24
Since a few days I cannot print from any ubuntu station to the cups. (Cups works on printing from a windows-desktop to the ubuntu with cups)

I presume I found the problem:

D [25/May/2011:00:47:01 +0200] [Job 1191] sfopen: gs_parse_file_name failed.
D [25/May/2011:00:47:01 +0200] [Job 1191] sfopen: gs_parse_file_name failed.
D [25/May/2011:00:47:01 +0200] [Job 1191] ./base/gsicc_manage.c:709: gsicc_open_search(): Could not find lab.icc 
D [25/May/2011:00:47:01 +0200] [Job 1191] | ./psi/zusparam.c:819: set_lab_icc(): cannot find default lab icc profile
D [25/May/2011:00:47:01 +0200] [Job 1191] End of messages
D [25/May/2011:00:47:01 +0200] [Job 1191] printer-state=3(idle)
D [25/May/2011:00:47:01 +0200] [Job 1191] printer-state-message="/usr/lib/cups/filter/cpdftocps failed"

Can anyone help me to find the solution?

Os:       ubuntu 11.04
Printer:  canon LBP3010
cups:     1.4.5-5ubuntu1
cndrvcups 2.20-1ubuntu7
cups-driver-gutenprint 5.2.6-1ubuntu1

---

### Post by dargaud on 2011-06-29
Bump

---

### Post by Martes13 on 2011-09-11
I have the same problem. I had in 10.10 this printer (LBP3010) configured, but now, when I have reinstalled the OS to 11.04 it doesn't work anymore. I have the same output that you in my cups logs.

Did you solve the problem? Anybody know what to do? I think that it has to be with the ghostscript... but I have the lastest versions.

Thanks anyway!

---

### Post by dargaud on 2011-09-11
I wouldn't say it's solved, but it currently works... until the next update of CUPS. EVERY friggin update of CUPS breaks my printing. So once every 2 months I have to spend hours on the web fishing for answers and modifying config files. You can search my username + CUPS, maybe you'll find some answers, I don't know, it's like CUPS is a big mess of random things meant for unrelated systems (why are there Mac paths hardcoded in it ?!?). Sorry for the rambling, I'm tired.

---

