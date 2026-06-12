---
title: "Wireless issues"
date: 2009-02-02
forum: Hardware
---

### Post by SpitfireSMS on 2009-02-02
Since I installed ubuntu 8.10 about 3 days ago, there has been nothing but issues with wireless.

ndisgtk would not work for any of the xp drivers I downloaded.
The system>hardware drivers found my wireless driver, but it does not work either.

I had madwifi hal 10.something installed and it was working. I had to do sudo modprobe ath_pci and sudo modprobe wlan_scan_sta at each boot to find wireless networks.

I suspended the machine, and upon boot it no longer finds any networks.

Its an Acer 5520 with  Atheros AR5007EG (AR242x).

lspci shows it as AR242x, the system>hardware drivers calls it Atheros 802.11g/b support.

Any help would be very appreciated, I keep having to restart and boot my Windows OS and try to find a fix then reboot into ubuntu and have nothing work. Very annoying.

And I also cannot seem to make myself root, its rather infuriating having the UAC-like prompt asking for the password.

---

### Post by sp0nge on 2009-02-02
The first issue here is being able to gain super user access. Please make sure you can use the command as follows:

```
me@home:/$ sudo su
```

When you're asked for a password, please enter YOUR user/login password. Note you will now be operating as root and should immediately close the terminal and re-open it. We just want to make sure this works. 

Secondly, try this [link]("http://linuxwireless.org/en/users/Download"). I have the same chip in my card and it worked like a charm.

Hope this helps.

---

### Post by SpitfireSMS on 2009-02-02
Well thanks kindly, I got the wifi working properly.

Now my issue is that when I made myself root, and rebooted, i got errors(ill edit the post with them later). And it will boot up and show the desktop, but with no taskbars or anything.
Im able to ctrl+alt+left over to the other desktop, but right clicking wont do anything and theres nothing to click on.
I was able to ctrl+alt+4 or something similar to get into the CLI, but I dont know enough of the syntax or interface to undo what I have done.


Error 1: "User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 664 permissions. User's $HOME directory must be owned by user and not writable by any other user."

Error 2: "Could not update ICEauthority file /root//.ICEauthority"

Error 3: "There is a problem with the configuration server. (usr/lib/libconfig2-4/gconf-sanity-check-2 exited with status 256)"

Error 4: "Cannot create the directory "/root/.gnome2/share/fonts". There is needed to allow changing of the mouse pointer theme."

---

### Post by SpitfireSMS on 2009-02-02
Well as I was playing around with it I noticed that ctrl+alt+delete allows me to log out.

I still cannot log into my username.

Is there any other accounts I can access to try to fix my user account?

---

