---
title: "Mainpine IQ Express 4 port fax board"
date: 2009-09-04
forum: Hardware
---

### Post by dsa411 on 2009-09-04
I am trying to install a mainpine iq express 4 port fax board on ubuntu desktop 8.04 so that I can run a hylafax server. If I lspci i can see that ubuntu does see the device but it has it tagged as an unknown device. According to mainpine their hardware is compatible with linux as long as the distro is using linux kernel 2.4 or higher. The site also states that because it relies on a serial driver the kernel just needs to be configured with "multiport support" and the CONFIG_SERIAL_EXTENDED option needs to be enabled in the kernel ( [http://www.mainpine.com/linuxsupport.html](http://www.mainpine.com/linuxsupport.html) ) . Is this enable by default in ubuntu? Im not exactly sure how to check. Is the problem possibly more complex then what they are saying? Lastly if i do need to recompile the kernel would this be the best way? [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) or is their an easier way . I know the board gets detected under centos 4 but onboard lan adapter does not and I am more comfortable / confident with ubuntu. Thanks.

ps. I have also tried ubuntu 8.04 server and it yielded the same results.

---

