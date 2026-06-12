---
title: "Change keyboard layout"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by Jeremy23 on 2007-02-27
Just this morning, I installed Feisty on my laptop, and managed to select the wrong keyboard layout in the setup (I used the alternate install CD).

I have set the layout to the correct one in GNOME (via the swanky new Control Centre), but I have no idea how to fix it in the console. Every time I type a colon ':' it comes out as a plus '+'. I wanted to run *base-config* or something, but no such command appears to exist in Feisty.

Does anyone have any idea how to globally change the keyboard layout?

---

### Post by louis_nichols on 2007-02-28
Maybe with [console-setup]("http://packages.ubuntu.com/feisty/utils/console-setup")? It offers 2 executables: bin/setupcon and usr/bin/ckbcomp	. One of them should do the trick. I've never used it myself, so this is just a fairly educated guess.

---

### Post by Jeremy23 on 2007-02-28
Thanks for that tip, it gave me an idea.

I found that */etc/init.d/keyboard-setup* calls *setupcon*, so I deleted the symlink */etc/rcS.d/S06keyboard-setup*, rebooted, and my console is back to normal.

Then, if I type *sudo /etc/init.d/keyboard-setup start*, my keyboard goes funky again.

This is a great start. Thanks for your help. :)

---

### Post by Jeremy23 on 2007-02-28
I'm just reading the [changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/c/console-setup/console-setup_1.13ubuntu6/changelog"). I might get some ideas in there.

---

### Post by Jeremy23 on 2007-03-06
OK, as a followup. I solved the problem a few minutes ago by typing this:

```
sudo dpkg-reconfigure -plow console-setup
```

It allowed me to select U.S. English as my keyboard layout instead of Japanese (!?) and turn off the Latin modifier stuff. I seriously don't remember selecting Japanese in the setup.

Thanks for your help, it certainly put me on the right track.

---

