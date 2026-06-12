---
title: "AMD Mobility HD 4200 and cgminer."
date: 2014-03-02
forum: Hardware
---

### Post by lakeshore2985 on 2014-03-02
Hello! Not exactly an intermediate-expert Linux user so bare with me.

I have a dual-core notebook which has embedded AMD HD 4200 graphics and have been trying to get this thing to mine Litecoins alongside my main mining rig but no success so far. I know this GPU is a pain in ass when it comes to Linux driver support and will probably get me irrelevant kH/s but I've managed to install the AMD Catalyst 12.6 Legacy driver after downgrading to Ubuntu 12.04.1 anyways. Not quite sure it installed correctly though since I've been experiencing 90-100% CPU usage on Youtube 1080p playback (it's Turion II x2 M500 Mobile CPU so something's off).

'sudo aticonfig --lsa' lists my HD 4200 fine but 'sudo aticonfig --adapter=all --odgt' returns error trying to get temperature for the adapter. Then when finally trying to use cgminer it says "Error -1: Getting Device IDs (num)".

Help!

---

