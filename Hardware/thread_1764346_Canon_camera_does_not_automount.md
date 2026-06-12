---
title: "Canon camera does not automount"
date: 2011-05-21
forum: Hardware
---

### Post by MKe2 on 2011-05-21
Hi,

We have a Canon EOS1000D camera. On Ubuntu 10.04 and Mint Julia, automount works fine. When I attach the camera and turn it on, an icon will appear by which I can access the memory card. On Xubuntu 11.04 32bits no such luck. USB-flash sticks and other USB stuff works fine, only the camera does not.
When I attach the camera, nothing seems to happen. With the command dmesg | tail I could see an error message (don't remember which). I also didn't see the camera with lsusb. This I could solve by using the commands:
```

sudo killall gvfs-gphoto2-volume-monitor
sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
```I can now download the photos by using the program 'Camera' which is in the repo's.
However, I would like to have the automount back. Camera doesn't allow me to see the photos or download just a couple, or delete just a couple. So it's not an ideal solution.

BTW, I tried the Ubuntu live-version and it had the same problem, so it's not Xubuntu specific.
I'm stuck, can anyone help me?

---

### Post by shosto on 2011-07-09
My wife had a similar problem.  After a bit of research, came up with a shell script to use with nautilus to mount the camera.  In our case it's a Canon too, but should work with others.  The script is dependent on the camera showing up in "lsusb" output.

---

### Post by hannada on 2012-07-09
This solution also worked for me, using Ubuntu 12.04.  Just a few minor edits to the script were required, so that the script would have actual values returned by lsusb and to incorporate the correct model name for my camera.

Everything now works for me just as it used to work for earlier Ubuntu versions.  In particular, after the camera is recognized and mounted, I am given the choice of whether to open the camera as a mounted data drive or as an image source for a picture importing application.

---

