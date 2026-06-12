---
title: "nVidia Drivers 9800gtx"
date: 2009-03-07
forum: Hardware
---

### Post by FoXoF on 2009-03-07
I'm using Ubuntu 8.10 with a nVidia GeForce 9800gtx+.

I recently installed the 177 nvidia proprietry drivers for my graphics card.

After that xserver cannot find displays and so I dont get a desktop environment. Just a shell. I've tried startx but that does not help.

I've tried the following (in order but with restarts between)
```

sudo apt-get remove nvidia-glx-177
sudo apt-get purge nvidia-glx-177
sudo apt-get install nvidia-glx-173
sudo apt-get remove nvidia-glx-173
sudo apt-get purge nvidia-glx-173
sudo apt-get install nvidia-glx-180
startx

```

Whatever I do I cannot get xserver running again.

Help would be greatly appreciated.

---

### Post by Skripka on 2009-03-07
> **FoXoF said:**
> I'm using Ubuntu 8.10 with a nVidia GeForce 9800gtx+.

I recently installed the 177 nvidia proprietry drivers for my graphics card.

After that xserver cannot find displays and so I dont get a desktop environment. Just a shell. I've tried startx but that does not help.

I've tried the following (in order but with restarts between)
```

sudo apt-get remove nvidia-glx-177
sudo apt-get purge nvidia-glx-177
sudo apt-get install nvidia-glx-173
sudo apt-get remove nvidia-glx-173
sudo apt-get purge nvidia-glx-173
sudo apt-get install nvidia-glx-180
startx

```

Whatever I do I cannot get xserver running again.

Help would be greatly appreciated.

have you tried:

```

sudo /etc/init.d/gdm start

```

---

### Post by FoXoF on 2009-03-07
My problem seems to be fixed now but it may not have been 100% that command.

This is what happened:

```

startx  //failed
sudo /etc/init.d/gdm start   //succeeds
startx //failed
sudo apt-get purge nvidia-glx-180  // removes nothing but alerts me something is still installed
sudo apt-get autoremove // removes some more of the nvidia drivers
startx //failed
sudo /etc/init.d/gdm start   //succeeds
startx //failed
sudo shutdown -r 0 // restarts system - works again after restart

```

Thanks for the help.

Now I just need to get hold of some working drivers for my 9800gtx.

---

