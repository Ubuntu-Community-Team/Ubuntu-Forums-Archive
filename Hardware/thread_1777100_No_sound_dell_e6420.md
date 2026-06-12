---
title: "No sound dell e6420"
date: 2011-06-07
forum: Hardware
---

### Post by jeremyk on 2011-06-07
Hi,

I am running ubuntu 11.04 on a new dell e6420. There is a serious sound problem. 

First the built-in mic was not working. Now it is worse. For no apparent reason, there is no sound at all. 

Nothing seems to be mute. 

Any help would be much appreciate. 

Many thanks.
Jeremy.

---

### Post by Toz on 2011-06-08
Try deleting .pulse and .asoundrc from your home directory. 

From the File Manager, make sure that you have Hidden Files shown (look for a setting in the menu bar) and delete the .pulse directory and .asoundrc file.

From the command line (Terminal window) type in the following:```
rm -rf ~/.pulse && rm -rf ~/.asoundrc
```(ignore any error messages that might show).

Reboot.

---

