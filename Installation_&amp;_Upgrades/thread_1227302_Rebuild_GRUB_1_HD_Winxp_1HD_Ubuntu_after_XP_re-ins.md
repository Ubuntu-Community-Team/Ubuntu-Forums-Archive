---
title: "Rebuild GRUB 1 HD Winxp 1HD Ubuntu after XP re-install"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by sandman3838 on 2009-07-30
Hello
I have done this before about a year ago and for the hell of me I can't remember.  Can anyone help?

My system, I have 4 HD, SADA1 Winxp, SADB1 Ubuntu, the other two are just files.  I need to re-install Winxp!  As for UBUNTU 904 it's just fine I want to leave it alone.

I know that the Winxp installation will undo GRUB menu.

I was planning on switching off the two extra HD as they have files I don't want them to be touched. PERHAPS THE UBUNTU HD AS WELL UNTIL AFTER WINXP INSTALLS, BUT I'M NOT SURE?

After the WINXP installation what is the easiest way to let ubuntu rebuild the grub menu.  Before if I remember correctly I used the Ubuntu CD?

Suggestions?

Thanks everyone.

---

### Post by merlinus on 2009-07-30
Boot from the live cd, open a terminal and

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)  #use the number from the previous command
quit 
```

---

