---
title: "problem with compiz in vmware w/ intel 965 chipset"
date: 2009-04-16
forum: Hardware
---

### Post by qUanTuM-fLuX on 2009-04-16
Hello,
  Having trouble getting compiz to work..
  I tried the SKIP_CHECK=yes workaround on the compiz website but nothing happened
  I looked in the /usr/bin/compiz file but i didn't see 965 on the blacklist (i commented out all the other lines anyways though)

some info:
  Ubuntu Intrepid on VMware workstation 6.5 (windows xp pro host)
  mobile Intel Express 965 family chipset (from host display properties)

lspci  | grep VGA
00:0f.0 VGA compatible controller: VMware Inc Abstract SVGA II Adapter

glxinfo  | grep rendering
direct rendering: Yes

cat /usr/bin/compiz | grep WHITE
WHITELIST="nvidia intel ati radeon i810 fglrx"

compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

glxgears works (spins the gears)

I'm not sure if it's the VM or the intel 965 giving me problems.. any ideas?

---

