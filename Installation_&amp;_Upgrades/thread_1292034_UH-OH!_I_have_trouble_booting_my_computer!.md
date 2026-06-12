---
title: "UH-OH! I have trouble booting my computer!"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by Chestna on 2009-10-15
(Using LiveCD at the moment)
Hi! I've been happily using Ubuntu 9.10 on my 5-year-old Dell desktop for just over a month. I've learned some cool stuff by lurking and searching on these forums and other Linux websites.

Now I've screwed something up. 

I had tried KDE for a while to get the feel of Kubuntu, and then went back to my Gnome desktop. I discovered I still had the KDM as my default desktop manager and I wanted to change it. Somewhere I read that I just needed to edit etc/X11/default-display-manager to read 
[B]
/usr/bin/gdm[/B]        (instead of kdm)  and that's what I did.

When I rebooted, I saw this (or something like it - I copied by hand, tried to be as accurate as possible):

[B]Boot from (hd0,0) ext3dc1c3da9-a9cd-4d6a-80df-3ffba9d899d

Starting up...

Loading, please wait


19+0 records in

19+0 records out

kinit: name_to_dev_t(/dev/disk/by-uuid/2b414fac-35f3-47bd-8552-97a2be2782fc) = dev (8,5)

kinit: trying to resume from [/B][B]/dev/disk/by-uuid/2b414fac-35f3-47bd-8552-97a2be2782fc

kinit: No resume image, doing normal boot...
*Checking battery state...
                                                                  [OK]
Ubuntu 9.04 chestna-desktop tty1

[/B]After that, the screen doesn't respond to anything I do, except when I go to Ctrl+Alt+F2 (or F3-F6)
Then I am prompted for my login and password.
After I do that, the screen does not respond to anything I do - except for when I press enter, and it does that "chestna@chestna-desktop" thing.

[SIZE=2]Is there no other option besides backing up everything and reinstalling Ubuntu from scratch?[/SIZE]

---

### Post by az on 2009-10-15
Use the live cd and change it back to KDM.

If that doesn't fix it, then we can rule out other problems.

---

### Post by Chestna on 2009-10-15
az,

Thanks for the speedy reply! I did change it back to "kdm" and the computer rebooted beautifully. 
_________________________________________________________
Now I've just got to:

1. Find out what else it was I did (like tweaking to speed up the computer) that jacked this machine up, and/or

2. Find a "safe" way to change to gdm.

---

### Post by prshah on 2009-10-15
> **Chestna said:**
> 
2. Find a "safe" way to change to gdm.

Open a terminal (in KDE, Konsole) and give the command
```
sudo dpkg-reconfigure gdm
``` You will need to restart X for changes to take effect.

---

