---
title: "No image after booting, please ehlp!"
date: 2008-06-17
forum: Hardware
---

### Post by Charlypv on 2008-06-17
I'm running Ubuntu 8.04. After a regular autoupdate I reset my computer and then when it re-start it take me directly to a screen with the following message:
kinit: name _to_dev_t(/dev/disk/by-uuid/fe98f06e-66a3-4961-9f93-bd0dcde8f364da5(8,5)
kinit:trying to resume from /dev/disk/by-uuid/fe98...
kinit:No resume image, doing nrmal boooot ...

And the ask me for my user name and password. I log in however it stay in a terminal mode and nver goes t the normal ubuntu window mode.
I been trying searching in difernt post without sucess.
Any help will be appreiated.

Charlypv

---

### Post by Odrodzona-Sarmacja on 2008-06-18
Try booting up in recovery mode.
Then use "fix xorg" option from recovery menu.
It should fix your gdm issues.

---

### Post by Charlypv on 2008-06-19
How do I run the recovery mode?

---

### Post by Odrodzona-Sarmacja on 2008-06-21
When your computer boots up you get on screen for 5 seconds a notice from grub for "press esc for menu" or something alike. You press esc and then you choose the Ubuntu os to boot with "(recovery mode)" beside its name. It's simple. Then you should go on until you get another menu with three options "fix x server, resume, root-shell". You scroll with keyboard to "fix x" and press enter. Then you should return to the same menu. You scroll to "resume" and the os should load up normally.

Ok?

---

### Post by WombatForest on 2008-07-20
I thought that this thread was going to answer my problem.
However, Odrodzona-Sarmacja, When I attempted the fix X server and reboot it did not fix the problem.
Any other suggestions?
Wombat

---

### Post by WombatForest on 2008-07-20
Found a solution on another thread: command startx, worked a treat
Wombat

---

### Post by warp99 on 2008-07-20
> **WombatForest said:**
> Found a solution on another thread: command startx, worked a treat
Wombat

If you want you graphical login back make you sure you have a good internet connection then issue the following command:

```
sudo apt-get remove --purge gdm
```

Apt-get may ask to remove the package ubuntu-desktop, but that's fine because it only removes a meta-package and not the actual desktop. Once that's completed:

```
sudo apt-get install gdm
```

Now when you reboot your graphical login should return.

---

