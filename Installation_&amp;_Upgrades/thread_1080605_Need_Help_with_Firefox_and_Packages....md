---
title: "Need Help with Firefox and Packages..."
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by Dbzdude707 on 2009-02-25
A few problems...

Note: I have Ubuntu 8.10 Desktop.

1. My Firefox is the latest version and it came with Ubuntu, and I just installed Ubuntu yesterday (or the day before, I forget). Yet half the videos on Youtube cause it to stop responding, and no videos on Veoh will load, period. So I downloaded and installed the latest Flash Player from the Flash site and it still doesn't work. I then uninstalled Totem and tried MPlayer, thinking that might work. No dice... I tried rebooting the computer, it still doesn't work.

2. Next I figured I would uninstall and reinstall Firefox. So I got rid of it successfully. Then when I wanted to install it again... Well, I went into Synaptic to get it and once I clicked "Mark for Installation" it again failed to respond. This happens every time I try to install anything in Synaptic now...

3. So after that I went into the Terminal and tried "Sudo Apt-Get Install Firefox-3.0" and I get this:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I'm at a loss... I can't fix the problem and more problems just keep popping up. This is a new installation of Ubuntu and basically the only real modification I've done to the system was to install the "ubuntu-restricted-extras" package which provides me with support for several file formats that Ubuntu didn't come with support for.

Rebooting won't fix any of this...

Please tell me what could be wrong... Thanks in advance.

---

### Post by Dbzdude707 on 2009-02-25
Hm... Does anyone know what's wrong?

---

### Post by Partyboi2 on 2009-02-25
Make sure you only have one package manager running at a time eg synaptic, update-manager apt-get.

---

### Post by sgosnell on 2009-02-25
You can't run apt-get if Synaptic is running, because Synaptic is just a GUI front-end for apt-get.  Close Synaptic, then run apt-get from the terminal.  As a last resort, you can download firefox directly from Mozilla, and do a manual install.

---

### Post by absolutezero1287 on 2009-02-25
Also, about the error with firefox (or any program for that matter), start FF from the terminal and then post output.

---

