---
title: "Ubuntu start up cheatcodes"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by Albretch Mueller on 2009-10-13
Hi,

 I start knoppix using the cheatcode:

 knoppix init 2 xmodule=vesa fb1280x1024 depth=16 bootfrom=/dev/hdb5

 in order to redefine the user home dirs in for "knoppix" and "root" in 

 /etc/passwd

 then I mount the partition where the user directories lie and I run "init 5" to finish the start up process

 How can I do this using Ubuntu?

 From Ubuntu's BootOptions ([https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions))

 I think that "root=" and "xforcevesa" work similar to "bootfrom=" and "xmodule=vesa"

 But I don't know how to stop initiallization before entering init 5 (break=init?), nor do I know how to specify parameters for my graphic card to work: fb1280x1024 depth=16

 The thing is that it doesn't make any sense to run a liveCD from the CD at all times (instead of using the liveCD to just start up). It runs faster, spares RAM and keeps your configuration when you rewrite user home dirs

 Thank you
 lbrtchx

---

