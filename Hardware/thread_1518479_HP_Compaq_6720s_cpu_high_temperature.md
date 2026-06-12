---
title: "HP Compaq 6720s cpu high temperature"
date: 2010-06-26
forum: Hardware
---

### Post by janton on 2010-06-26
Hi every one!
I have a problem with my laptop (HP Compaq 6720s). It has quite high cpu temperature, sensors-applet shows 60-65 C as average. And situation doesn't change in init3 mode,the fan is always running. Under other OS like windows or Slackware cpu does not seem to warm up that much. Seems like Ubuntu 10.04 has problem with my hardware. Does any one know how can I solve this issue?

Thanks!

---

### Post by corrytonapple on 2010-07-26
Unfortunately. most HPs and Compaqs have this issue with Ubuntu. We are hoping for a solution still. If I knew code python, I would help.

---

### Post by claracc on 2010-08-06
I have the same laptop and I had this same problem with ubuntu 9.04 jaunty jackalope (problems with intel video drivers), when i installed karmic koala this problem disappeared.

Perhaps it also helps that i haven't installed compiz but metacity.

---

### Post by TBABill on 2010-08-06
A couple things can help. 
 
1. Remove the open source Java and install Sun Java in Synaptic
2. If a proprietary video driver is available, make sure you use it
3. Use Adobe Flash, not gnash. Neither is great, but Adobe Flash will help you run a little cooler.
3. Install CPUFREQ-UTILITIES (think that's the name, but search Synaptic for CPUFREQ). This allows you to use frequency scaling if your CPU can support it (most can). Once installed you can set your system for "ondemand" mode, which scales down the CPU to its slowest speed and steps up whenever system demand requires it. It's imperceptible that it is running slower because it jumps up as needed faster than you will notice.
 
To enable ondemand mode in a terminal:> CPUFREQ-SET --governor ondemand
 
Then type: > cpufreq-info and it will come up almost with a full screen of info, but somewhere in the text you will see "ondemand" or "performance". If it says ondemand you are all set. Just exit, restart (I think) and enjoy.

---

