---
title: "[SOLVED] No sound on Toshiba A25-S4587"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by sci-fi guy on 2007-06-09
I somehow managed to disable the sound on my old computer about a week ago, and decided to forgo fixing it in anticipation of getting this one.  Unfortunately, sound does not work on this one, either.  I supposedly have a Realtek HD Audio chipset, although I don't know how to find out.  When I tried to install Realtek's Linux driver, it ruined my logging on and I had to reinstall Ubuntu.  Any ideas on what I can do to remedy my sound issues?

---

### Post by DagMan on 2007-06-10
maybe this
[http://ubuntuforums.org/showthread.php?t=416207&highlight=toshiba+sound+fix](http://ubuntuforums.org/showthread.php?t=416207&highlight=toshiba+sound+fix)
both the first and eigth post work on my Sattelite A100

---

### Post by sci-fi guy on 2007-06-15
No good. Thanks anyways.

---

### Post by sci-fi guy on 2007-06-15
I made a mistake identifying my computer.  It is a A205, not a A25.

---

### Post by SwannyJ on 2007-06-23
Same machine, same problem.  Another noob looking for a resolution!

TIA,

J

---

### Post by hsuwb on 2007-10-19
Hey if any of you guys are still having problems with sound, I have the exact same model and I got sound to work on Gusty(7.10) with the instructions here: [http://ubuntuforums.org/showthread.php?t=568463]("http://ubuntuforums.org/showthread.php?t=568463")

Since the original instructions were written for Feisty, the fix should probably also work on Fiesty, But if you guys have upgraded to Gusty, I added the changes I made to the original instructions to the end of that thread.

---

### Post by sci-fi guy on 2007-10-31
Very simple solution found on Launchpad:
```
sudo apt-get install linux-backports-modules-generic
``` Restart afterwards

---

