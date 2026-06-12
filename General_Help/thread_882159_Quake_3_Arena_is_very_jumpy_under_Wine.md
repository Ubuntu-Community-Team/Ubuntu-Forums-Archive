---
title: "Quake 3 Arena is very jumpy under Wine"
date: 2008-08-06
forum: General Help
---

### Post by jras20 on 2008-08-06
Is there a way I can make Quake 3 Arena run smooth under Ubuntu with Wine?  I like that game, its way to jumpy right now.  Maybe it might fix if I change the resolution?

---

### Post by jonian_g on 2008-08-06
Why use wine? Quake 3 arena runs natively on Linux.

1.Download the linux installer from ID software:

[ftp://ftp.idsoftware.com/idstuff/quake3/linux/](ftp://ftp.idsoftware.com/idstuff/quake3/linux/)

Download file: linuxq3apoint-1.32b-3.x86.run

2. Open a terminal, navigate to the folder that you saved the installer and type:
```
sh linuxq3apoint-1.32b-3.x86.run
```

3. After the install is finished, navigate to the folder that you installed the game (probably /home/[your username]/quake3) and copy in the folder baseq3 the file pak0.pk3 that is in your game CDrom in the folder baseq3.

4. Run the game by double clicking the quake3 executable that is located in the folder that you installed the game (probably /home/[your username]/quake3), or create a shortcut in gnome panel or applications menu.

Enjoy Quake running natively on linux. I have Quake 4 and it runs smoothly with a geforce 7600gs. It never ran so good with windows.

Info on installing other id software games on linux here:

[http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/)

---

### Post by jras20 on 2008-08-06
Thanks I'll give it a shot when I get some time.

---

### Post by jras20 on 2008-08-07
Actually I feel kind of dumb, I didn't have the 3d Graphics drivers installed.  I installed them now it runs like a charm! :KS

---

