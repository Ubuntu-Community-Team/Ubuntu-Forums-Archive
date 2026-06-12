---
title: "Uninstalled then Re-installed and now there's 2 startups"
date: 2008-06-17
forum: Hardware
---

### Post by Lilszamora on 2008-06-17
ok I uninstalled ubuntu because I was aggravated that it didn't seem to work, then I tried re-installing it and when I did, there was 2 options for ubuntu at startup...it will really annoy me so is there any way to get rid of one of the options, they both do the same thing, start up to ubuntu.

---

### Post by Lilszamora on 2008-06-17
oops sorry wrong bored..can someone move this to a more appropriate location

---

### Post by lisati on 2008-06-17
The two entries can happen for a couple of different reasons. If you're not using "dual boot" the following might be of some help:

From a terminal, type:
```
sudo gedit /boot/grub/menu.lst
```Scroll down the file until you find a line which reads
> #hiddenmenuthen change it to read
```
hiddenmenu
```(i.e. remove the "#").

Save the file, exit the editor, and type:
```
sudo update-grub
```The next time you boot the menu items will be hidden. If you need to see them again, you can always call them up by pushing the "ESC" button at the appropriate time in the boot-up sequence.

---

### Post by lisati on 2008-06-17
When you reinstalled and were asked about partitions, did you specify "Use entired disk", or did you use some other option? (Knowing this might help other people who have other ideas on helping you through this)


EDIT: p.s. sometimes having what looks like two menu entries for the same thing is normal, particularly if you've just done some updates.

---

### Post by Lilszamora on 2008-06-17
I installed inside of windows both times, but I've done it on my other computer and it never did this...I hope that that helps

---

