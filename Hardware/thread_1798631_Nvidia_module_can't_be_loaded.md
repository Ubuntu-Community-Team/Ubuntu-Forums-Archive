---
title: "Nvidia module can't be loaded"
date: 2011-07-06
forum: Hardware
---

### Post by zee on 2011-07-06
Hi.
  A few weeks ago I removed my graphics card and lent it to a friend of mine. After returning it I tried to do some GPU calculations only to find that the binary was not working any more.

  A closer inspection revealed the nvidia module is not loaded at all but the nouveau flavor is loaded instead.

  A "sudo modprobe nvidia" shows:
FATAL: Module nvidia not found.

  I tried removing the drivers and reinstalling them but nothing seems to help.

  The computer is a dual Xeon 5620 workstation with a Nvidia 470GTX graphics card.

  What else could I try? I don't need any fancy graphics because I use the card to perform calculations.

  I use ubuntu 10.04.2 with "uname -a":
Linux erwin 2.6.32-32-server #62-Ubuntu SMP Wed Apr 20 22:07:43 UTC 2011 x86_64 GNU/Linux

EDIT:
  I removed all traces (apt-get purge ...) of the nouveau module yet it is still loaded at boot time. What is going on?

Thanks,
zee

---

### Post by CMOS4081 on 2011-07-06
Look in to forums and on the net on how to remove the nouveau module first. Then reboot the system and install the current nvidia driver from [www.nvidia.com](www.nvidia.com) while running in pure text mode.

Follow the prompts the Nvidia driver provides as it should detect the older nvidia driver and remove it besides updating your xorg.conf file.

One last reboot should be sufficient after this.
You should check that the Nvidia control panel comes up from the icon or by running nvidia-settings. Then your CUDA based application should work.
Good Luck!:P

---

### Post by zee on 2011-07-06
I have no X installed, because this workstation is chilling in the server room. But I saw in the logs the modules was loaded.

Will try the relevant application now.

Thnks for the reply!
zee

---

