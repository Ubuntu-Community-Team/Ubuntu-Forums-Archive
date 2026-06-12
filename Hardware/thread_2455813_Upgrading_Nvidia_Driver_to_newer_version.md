---
title: "Upgrading Nvidia Driver to newer version"
date: 2020-12-28
forum: Hardware
---

### Post by linerman on 2020-12-28
Hi,

I would like to upgrade my installed and working Nvidia-driver to a newer version.

I am using Ubuntu 20.04. How to do it, to avoid mistakes and typical "black screen" ?

---

### Post by #&amp;thj^% on 2020-12-28
Open your terminal (Ctrl+Alt+T), and run the following command to get information about your graphic card and available drivers:

```
ubuntu-drivers devices
```

---

### Post by linerman on 2020-12-28
Yes, I did that. I have suggestion that my Card should use nvidia-driver-455 and I have -450. That is why I 'd like to upgrade. But how to do it without making mistakes?

---

### Post by #&amp;thj^% on 2020-12-28
Fingers Crossed....
```
sudo ubuntu-drivers autoinstall
```

---

### Post by CatKiller on 2020-12-28
FWIW, the failure mode of your driver failing to load seems much scarier than it actually is. You might get a black screen with a flashing cursor if you also had that when you were installing, or you might not be able to log in, but most likely you just wouldn't have decent acceleration.

Should you not be able to log in graphically, you can switch to a TTY with Ctrl-Alt-F2 and do your fixing from the command line. If you get the black screen you can add *nomodeset* to your Grub line, exactly the same as if you experienced that symptom when first installing. Either is a bit of a speed bump, but not that big a deal in the grand scheme of things.

Now, *sometimes* the presence of an earlier branch interferes with the installation of a later branch, so neither actually gets loaded. So the least-likely-to-go-wrong method is to completely remove the old driver branch before you install the new one. Something like ```
sudo apt-get purge nvidia* libnvidia*
``` before you install the newer branch ought to do it. *Most* of the time it's not necessary, and you'd be absolutely fine, but that's the belt-and-braces method.

---

### Post by bigmeme2 on 2020-12-28
If you had Nvidia drivers installed beforehand, it should still work, albeit a bit slow. If you want to update your drivers graphically, you should open your driver manager, navigate to additional drivers, and choose the newest option. Preferably one with the "tested" tag to the right of it. Otherwise, follow the advice of the replies above mine. May I ask what GPU you are currently running, and what GPU you are wanting to upgrade to?

---

### Post by Yellow Pasque on 2020-12-29
I prefer to use the terminal for these things, so you get a more specific error message should there be an issue with the nvidia driver building/installing.
```
sudo apt-get install nvidia-driver-455
```

Note that Ubuntu 20.04 currently offers 455.38
If you absolutely want the latest Nvidia driver all of the time, take a look at: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=focal](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=focal)

---

