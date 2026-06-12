---
title: "Help with 8800M GTS"
date: 2008-05-19
forum: Hardware
---

### Post by Luke has no name on 2008-05-19
Anyone had experience with this chip in Hardy? I can't get it working. i'm going to try getting Envy to do the work, but I'll update you on that when it comes about.

---

### Post by Luke has no name on 2008-05-20
Solved:

Ubuntu, for whatever reason, cannot properly configure this card. I don't know why, and I will likely file a bug report to give devs a heads up. Envy couldn't take care of the job, either. So I had toget down and dirty AAAAAAAND: download the binary, kill X, install, restart, configure xorg.conf.

1) Get the binary off of nvidia's elusive "Unix" dirvers page:
[http://nvidia.com/object/unix.html](http://nvidia.com/object/unix.html)

2) Through apt or Synaptic, install the libc6-dev package.

3) Once the proper .run package is downloaded, hit ctrl+alt+F1 to get into the CLI. Login.

4) Type in "sudo killall gdm" to kill the gnome desktop manager, and X.

5) Navigate to the folder where the .run is, and type "sudo sh <the file>"

6) Upon successful completion, try rebooting and logging in. If your driver is properly recognized, great! If not:

TROUBLESHOOTING

If you get a message saying you are in low-graphics mode, Try configure. Navigate to the driver by brand/type tab, and choose nVidia. Choose 8 series. Then go back and choose the "generic" monitor of the resolution you desire. Even if the "test" fails, try it out.

If it doesn't work, you will have to manually set your driver for the card to "nv" in xorg.conf. There are plenty of manuals on how to do that, searching through Google.

---

### Post by nicedude on 2008-05-20
Luke you will need to get the latest linux driver package directly from the Nvidia website and follow the directions there to install it if you find your card is not supported by envy. I have an 8400m in mine and that is what I did but for other reasons as I uninstalled the restricted driver manager to get the best driver for my wifi working. If you need further help you can PM me and I will try to help you out.

nicedude

---

