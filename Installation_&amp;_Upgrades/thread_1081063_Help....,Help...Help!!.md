---
title: "Help....,Help...Help!!"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2009-02-26
Hi Guys!!

Please help me get out of this Mess..!!
Yesterday, I got entangled with KDM & GDM issue after my donwload & install of KGet-The KDE based Download Manager!

Now Iam not even able to access the Ubuntu? On entering my username & password(both of which reflects on a dark screen), screen reflects 3 messages like:

1)The programs included wth Ubuntu system are free....& yada yada..

2)Ubuntu comes with absoultely No Warranty....

3)To access official help, visit so & so....

Then I get this :
myname@myname-desktop:~$ _(Blinking Cursor)

& after this, I become absolutely DUMBSTRUCK! I have to press Ctrl+Alt+Del to Reboot my machine to choose Windows as OS to get my work done!

Please help?

---

### Post by aquavitae on 2009-02-26
It sounds linke the Xserver (graphical display manager) is not starting for some reason, so its dropping you directly into the command line. What happens if you do this:  Log in as you've described above, then type in the command ```
sudo \etc\rc.conf\gdm restart
```
It will then ask for your password.  Enter it, it won't show any stars or anything while you're typing, but it goes in anyway.  What happens then?

---

### Post by Saurabhdua on 2009-02-26
I'll let you know in a shortwhile.

Update: That returned with command not found option.

Here to be specific:

sudo: etcrc.confgdm:command not found

---

