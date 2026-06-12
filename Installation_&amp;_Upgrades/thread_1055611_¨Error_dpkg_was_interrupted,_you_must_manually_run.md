---
title: "¨Error: dpkg was interrupted, you must manually run¨"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by BrentonEccles on 2009-01-30
I was downloading the restricted formats applications through Terminal,
> sudo apt-get install ubuntu-restricted-extras


...and, my computer reset during... and now I&#7743; trying to re-do it so I can run those restricted files and ... I get the following:
> dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

How can I fix this?

Thank-you for your help.

---

### Post by snova on 2009-01-30
Open a terminal, and run:

```
sudo dpkg --configure -a
```

---

### Post by cdtech on 2009-01-30
I always like to force the install since it was interrupted and never completed using:
```
sudo dpkg --configure -a && sudo apt-get -f install
```
This will finish installing half installed packages.......

---

### Post by BrentonEccles on 2009-01-30
AH, darn!!!
Now I get: Ünable to lock the administration directory (/var/lib/dpkg/), are you root?

Help?

---

### Post by snova on 2009-01-30
Make sure you aren't running any package management programs.

If you're sure you aren't, then remove the lock file:

```
sudo rm /var/lib/dpkg/lock
```

---

### Post by BrentonEccles on 2009-01-30
Still getting the same issue.
This is so tear generatingly depressing.

---

### Post by BrentonEccles on 2009-01-30
Is there any way i can just rebegin the installation from scratch?

---

### Post by cdtech on 2009-01-31
Have you tried booting into recovery mode then try running the commands suggested.........

---

### Post by abn91c on 2009-01-31
> **BrentonEccles said:**
> Still getting the same issue.
This is so tear generatingly depressing.
Make sure synaptic is not open before you try the commands

---

### Post by albinootje on 2009-01-31
> **BrentonEccles said:**
> Still getting the same issue.
This is so tear generatingly depressing.
You need to practice a little bit more patience as a Linux beginner, because those new things can be useful later on, so take a deep breath, and try the following :

Boot into "recovery mode", by hitting <escape> when the Grub menu tells you about hitting <escape> to get into the Grub menu.
Then choose "recovery mode".
After that choose "drop to root shell prompt".
Then type in :
```

dpkg --configure -a <enter>
apt-get -f install <enter>
reboot <enter>

```

---

