---
title: "Nvidia drivers seem to break laptop lcd"
date: 2010-06-26
forum: Hardware
---

### Post by rasperin on 2010-06-26
Hey Guys!
    I recently bought a new sony vaio for all things linux and everything worked great except that x didn't seem to "fit to screen" (things were hanging off of the that were not visible) and I couldn't get multi-monitor to work. So I installed the nvidia drivers and Boom, display no longer works on my laptop. It looks like it tries to boot them but fails majorly. With my LCD hooked up to the HDMI slot it outputs to that just fine, just not my laptop lcd.

Any ideas? I bought this exclusively for Linux.

Specs:
   Kubuntu 10.4
   Nvidia drivers 192
   Nvidia 330M
   Sony Vaio VPCF127FX

---

### Post by rasperin on 2010-06-27
Solved with [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) need to set to DFP, but it's now not detecting the second monitor... irritating. What I want to know is how can you call this complete when all nvidia cards need some freaking hacking to have to be done. How can you call this a serious product? I thought that was the point to actually try to get a serious product released but you have to explain to your users that they have to hack around it. How hard would it be for you to run a filter, hell point me to the sources and I'll throw if(sysCtl.batteryState!=0 && driver=="nvidia"){ addDFPToXorg();restartX();} (hooray for psuedo code).

---

