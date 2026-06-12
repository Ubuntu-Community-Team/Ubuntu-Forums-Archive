---
title: "dual monitor"
date: 2008-11-02
forum: General Help
---

### Post by DrClaw27 on 2008-11-02
I just did a fresh install of 8.10 and when I go to system > administration > Nvidia X server settings I can add the enable my second monitor no problem. As soon as I reboot I'm back to one monitor. Any ideas?

---

### Post by tuxxy on 2008-11-02
Did you click the **"save to X configuration** **file**" button, also you could try running it as root if no luck

```
sudo nvidia-settings
```

---

### Post by DrClaw27 on 2008-11-02
> **tuxxy said:**
> Did you click the **"save to X configuration** **file**" button, also you could try running it as root if no luck

```
sudo nvidia-settings
```

I've tried both of those things and no luck.

---

### Post by Ng Oon-Ee on 2008-11-02
Does the 'save to configuration' button cause your nvidia-settings window to close down?

This is a crash that indicates your current xorg.conf file is invalid according to nvidia-settings (yes, its a bug I just found out about the other day).

If you're comfortable editing your xorg.conf, you can just add the "ServerLayout" section to it.

Run this:-

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```

After the starting comments, put something like:-

```
Section "ServerLayout"
    Identifier  "Layout0"
    Screen      0 "Screen0" 0 0

```

You'll have to change "Screen0" to the actual Identifier for your screen, it could be "Configure Screen", just scroll down the file to find out.

After that, try running "sudo nvidia-settings" again, should work this time.

---

### Post by DrClaw27 on 2008-11-02
That worked. Thanks.

---

### Post by jTips on 2008-11-02
Thanks for the tip!

Works great!

---

### Post by Ng Oon-Ee on 2008-11-03
You're both welcome :)

---

