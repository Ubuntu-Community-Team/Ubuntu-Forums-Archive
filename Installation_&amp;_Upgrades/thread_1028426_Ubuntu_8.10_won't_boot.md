---
title: "Ubuntu 8.10 won't boot"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by joshag1 on 2009-01-02
I have 2 hard drives (1) 400G Partitioned with XP and (1) 160G drive. I have been trying different distros but I am still committed to Ubuntu.

The problem is this.....it doesn't matter where Ubuntu is loaded, either on the first drive or the second, as soon as the new distro is loaded Ubuntu can no longer boot. Every distro I have tried (Fedora, Mandriva, currently SuSE) recognize Ubuntu, list it on their Grub menu, but it never loads/runs. Drops out to a blinking cursor. Did not write down exact but something like "file not found".

Most if not all have the gui Grub and prefer it to Ubuntu text. Still doesn't matter because everything always works except Ubuntu. Ubuntu being the distro I would like to keep this becomes a problem.

Any help would be appreciated, Thanks

---

### Post by joshag1 on 2009-01-02
Alright I am back in Ubuntu but........
This is how it goes down. I get to the gui and choose Ubuntu 8.10 and it kicks me to a second screen with the different kernal options. I choose the default or any other and it drops to a cursor saying "Error 15:File not found. Hit any key to continue". Hit a key and it kicks me to the Ubuntu grub text menu. Choose any and the result (except xp) is the same "error 15.........."
If you choose winxp you are kicked to a text screen with 2 choices xp or ubuntu. choose ubuntu and your in??? This is also the same with the suse gui screen. Pick windows, get kicked to a 2 choice text screen and choose ubuntu....success. 

Anybody???

---

### Post by dstew on 2009-01-02
It sounds like your Ubuntu distribution has its own grub boot loader with its own menu. If you want to start ubuntu directly from your grub GUI that comes up first, you need to edit the menu for the GUI booter to boot the Ubuntu kernel directly. Or, you could edit the second (Ubuntu text) menu to boot Ubuntu properly.

It sounds like you have a multi-boot loader for XP also (grub for DOS?), so when you choose XP, it gives you another menu. That menu boots the Ubuntu kernel directly.

---

### Post by joshag1 on 2009-01-04
In theory, yes, but this is the problem that I have. It seems that through installing and uninstalling multiple distros I have quite a few grub menus. How do I solve this without wiping out an entire os?

It seems that when I choose ubuntu from the open suse menu, I am presented with a menu featuring snow and sliding penguins. I need to get rid of this. If I choose ubuntu from the snow menu it kicks it to the original ubuntu text grub menu (need to get rid of this). There also appears to be a dos boot loader??? 

In the end, I just want the one open suse menu!

---

### Post by dstew on 2009-01-05
The problem you have is because each distribution installs its own grub menu and boot loader. You have to consolidate them all into one menu. You will have to edit the suse menu by hand, putting in menu items for each distribution. I do not know any automatic way to do it.

---

### Post by joshag1 on 2009-01-05
Suse has a way of denying me permission. I've tried but will continue.

Thanks

---

