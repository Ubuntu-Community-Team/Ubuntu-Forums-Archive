---
title: "config.xorg permissions for GeForce4 440Go fix"
date: 2010-06-03
forum: Hardware
---

### Post by Spook50 on 2010-06-03
I just installed 10.04 on my old Dell Inspiron 8200, which uses an NVIDIA GeForce4 440Go. When I installed the proprietary NVIDIA drivers, I got the (what seems to be common) TFT screen shutoff after bootup. I still got the login sound, so I knew my machine hadn't locked up. After searching the forums, it looks like adding the line
> Option   "UseDisplayDevice"  "DFP-0"to my xorg.conf file should hopefully do the trick. The problem is, I'm clueless on how I can edit the file in a way that'll let me save it after editing. I've looked around and tried different methods for accessing it with root/owner permissions, but nothing seems to work. The latest method I've tried is by typing
> gksudo nautilusinto the terminal, but then nothing happens at all. Any suggestions? I'm completely stumped, but I have a feeling there's something simple that I'm missing. I'm in recovery mode now so I can see what I'm doing.


EDIT: Well, not being totally sure what I did wrong and since this was a fresh install of Lucid with nothing to worry about backing up, I just formatted the partition and started over. Not really a viable solution for the issues I was having, but at least now sudo is functional for me again.

---

### Post by K. Hendrik on 2010-06-03
sudo gedit /etc/X11/xorg.conf

---

### Post by Spook50 on 2010-06-03
> **K. Hendrik said:**
> sudo gedit /etc/X11/xorg.conf

Tried that, but I got this response in the Terminal:
> sudo: /etc/sudoers is owned by gid 1000, should be 0
sudo: no valid sudoers sources found, quittingNow I'm totally confused :confused:

Edit: I think somewhere along the line I got ahead of myself and attempted to give my login ownership of the /etc/ directory by using the chown command and screwed it up. While still in recovery mode, I tried to set it back to root using
[HTML]chown root:root /etc/sudoers
chmod 440 /etc/sudoers[/HTML]

But then I got this response when I tried the chown command
[HTML]chown: changing ownership of `/etc/sudoers': Operation not permitted[/HTML]

So much for that idea ](*,)

---

### Post by K. Hendrik on 2010-06-03
Try:
```

chown root:root /etc/sudoers
chmod 440 /etc/sudoers

```

and than reboot after that again the:
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Spook50 on 2010-06-03
> **K. Hendrik said:**
> Try:
```

chown root:root /etc/sudoers
chmod 440 /etc/sudoers

```and than reboot after that again the:
```
sudo gedit /etc/X11/xorg.conf
```

Well it seems I was on the right track. You were quicker than my edit, though....

---

### Post by K. Hendrik on 2010-06-03
I forgot, you need to do that in the recoverymode, or from a live cd

---

### Post by Spook50 on 2010-06-03
> **K. Hendrik said:**
> I forgot, you need to do that in the recoverymode, or from a live cd

By recovery mode, you mean booting into the root shell prompt, right? I tried that, typed in the chown and chmod commands, then nothing. Is there an extra step or option I need to type in on the root shell?

---

