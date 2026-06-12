---
title: "Help in Installation and with updates"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by swap007 on 2009-10-14
I downloaded Adobe Flash player from Adobe site.According to Adobe I should run following command to install Flashplayer
```
./flashplayer-installer
``` but it never worked for me.There was  "libflashplayer.so" file so I changed name accordingly but it still failed to install flash player.

Also updates mess up with Nautilus. With fresh install it opens 'Computer' location but after updates it says Nautilus can't handle Computer locations. Is there any workaround for this?
I'm newbie in Linux so anyhelp regarding this is welcome.

Regards
SWAP

---

### Post by mac9416 on 2009-10-14
Here's a better way to install Flash Player:

```
$ sudo apt-get install flashplugin-nonfree
```

Regarding the second problem, you're not the only one who this has happened to. One solution I've read about is running:

```
$ sudo mv /usr/local /usr/local.old & sudo mkdir /usr/local
```

Good luck!

---

