---
title: "Getting switchable graphics chipsets to work"
date: 2009-01-18
forum: Hardware
---

### Post by Mocker on 2009-01-18
Hi folks,

My Asus U3S has a switch to select one of two graphics chipsets (integrated Intel video for power saving, and a discrete Nvidia chipset for high performance). I've been trying to get this to work under Intrepid. 

While Googling, I found a thread at [http://forum.notebookreview.com/showthread.php?t=181032&page=2](http://forum.notebookreview.com/showthread.php?t=181032&page=2) that had some good info, as well as a link to this old thread on the Ubuntu forums: [http://ubuntuforums.org/showthread.php?t=419841&highlight=xorg_conf](http://ubuntuforums.org/showthread.php?t=419841&highlight=xorg_conf)

I've set up the script to switch the xorg.conf files, but the second link also talks about changing the symbolic links to the GL libs. Unfortunately, the libs seemed to have changed dramatically since these posts. I've not been able to get 3D acceleration to work in either chipset (I had it working for Nvidia, which is what I had enabled when I installed Ubuntu, so the Nvidia libraries and settings are there).

Any ideas on what libraries need to be switched between the non-free Nvidia drive drivers and the Intel ones?

And, is there an easier way to support switchable graphics chipsets in Intrepid than this kludge?

---

