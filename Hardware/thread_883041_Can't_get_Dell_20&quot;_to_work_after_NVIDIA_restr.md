---
title: "Can't get Dell 20&quot; to work after NVIDIA restricted driver"
date: 2008-08-07
forum: Hardware
---

### Post by Umbrello on 2008-08-07
Hello,  I'm almost completely new to Ubuntu (have tried it before, but not much)

I installed Ubuntu today and everything was going smoothly, I got a nice big picture up on my Dell 20" screen, then i decided to install a restricted driver for my graphics gard, NVIDIA 7600Go I think it is. I'm running Ubuntu on a laptop, Compal HEL80 to be exact. After the reboot my Dell screen went black and Ubuntu wouldnt detect it anymore. Now Im sitting in front of my laptop screen with what is to become sore eyes :)

I don't know where to begin in solving this problem. Ive read a few threads around, but I dont understand much yet.

Can anyone help me with this?

---

### Post by astroboy78 on 2008-08-07
Hello Umbrello

Did you install the driver from the "restricted drivers" window or installed it manually (from nVidia.com) ? If you installed from the restricted drivers window, you have the following option to troubleshoot it:

1. start a terminal window and type:
```
nvidia-settings
```

You will have a Linux version of the nVidia Control panel on Windows. You "should" be able to manage the 2nd monitor.

Give me news if you did or didn't get it to work!

P.S.: If you want to make the changes permanent, you will have to start nvidia-settings with "sudo nvidia-settings" then type your login password. You will be able to write your new configuration in the xorg.conf file (the button is in the lower right corner of the window). Then if you reboot, your changes will not be lost and you will not have to redo this procedure again!

---

