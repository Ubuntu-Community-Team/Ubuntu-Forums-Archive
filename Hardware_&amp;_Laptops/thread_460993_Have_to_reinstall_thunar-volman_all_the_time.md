---
title: "Have to reinstall thunar-volman all the time"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by Jodokos on 2007-06-01
Hello!

I'm using feisty with xfce from the repos.
Every time I reboot my machine, the automount feature doesn't work anymore.
Thunar doesn't show the available drives in the bookmarks sidebar and drive icons are not shown on the desktop.

So I have to go into synaptic and reinstall thunar-volman and it works again. It also works when I reinstall "hal".

But only until the next reboot - thats really annoying.

I hope you can help, thx!
Josef

---

### Post by simonn on 2007-06-01
What does the following return?

```

ls /etc/rc?.d/*udev

```

---

### Post by Jodokos on 2007-06-01
> **simonn said:**
> What does the following return?

```

ls /etc/rc?.d/*udev

```

It shows the following:

```

josef@asterix:~$ ls /etc/rc?.d/*udev
/etc/rcS.d/S10udev

```

Your help is much apprechiated!

---

### Post by Jodokos on 2007-06-05
I hate to bump it up, but the problem still exists...

---

### Post by simonn on 2007-06-14
I am basically stabbing in the dark here, but, I suspect that for some reason your personal config file(s) are not being saved when you log out or are you not loging out before rebooting.

Sorry I am using a windoze PC at work at the mo and do not have access to xfce to check, but you should be able to set this in the settings menu somewhere.

Alternatively or also, what does the following return (the $ at the beginning it the prompt :)):

```

$ cat $HOME/.config/Thunar/thunarrc

```

---

### Post by Jodokos on 2007-06-17
> **simonn said:**
> I am basically stabbing in the dark here, but, I suspect that for some reason your personal config file(s) are not being saved when you log out or are you not loging out before rebooting.

Sorry I am using a windoze PC at work at the mo and do not have access to xfce to check, but you should be able to set this in the settings menu somewhere.

Alternatively or also, what does the following return (the $ at the beginning it the prompt :)):

```

$ cat $HOME/.config/Thunar/thunarrc

```

I guess that it is not in the thunarrc!

Because: ```
MiscVolumeManagement=TRUE
``` is always set to true.


The really funny thing I noticed: EVERY time I install or remove a package (ANY package), the volume-management suddenly works again. So it doesn't seem to be started at boot!

---

### Post by merlinus on 2007-06-17
If you have set xfce to manage your desktop, then you much uncheck Save Session Settings when you logout, reboot, or shut down.

-merlin

---

