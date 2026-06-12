---
title: "HP DV2310us not waking from sleep"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by lazc on 2007-04-27
The hardware in this system is AMD Turion X2, Nvidia Chipset, Nvidia Sata and Nvidia Go6150.  form what I know this is comparable with the hardware on a HP DV2000z, everything is detected.  I have Fiesty 7.04 installed.  It goes to sleep fine, but upon wake the drive is missing or the sata controller refuses to wake. Has anyone run into a situation like this?  What's messed up is that since the drive is missing I don't have anything on the logs to help me troubleshoot.  Can someone help me, I need to have suspend work due to my work.

---

### Post by lazc on 2007-04-30
I gave up on Fiesty.  They need to do more testing before releasing versions that are not ready, I mean I only saw one beta for it.    I went back and installed Edgy and almost everything works including suspend, the only thing that is not working is the Broadcom crappy wireless card even with the ndiswrapper.  I guess I have to compile the new ndiswrapper utils from fiesty to get them backported over to edgy, and or the new fwcutter too if this fails since the one in edgy does not work with my firmware.  If that fails I guess I will be running ubuntu inside a virtual machine.

---

