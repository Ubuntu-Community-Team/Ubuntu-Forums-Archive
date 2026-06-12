---
title: "Quitting X for driver installation (8.10 AMD 64)"
date: 2008-11-09
forum: General Help
---

### Post by Athiril on 2008-11-09
Ctrl+Alt+Bksp just logs me out to the graphical X login screen for ubuntu.

/etc/inti.d/gdm stop just quits X but does not take me to bash or a login termnial, it just returns me to where the runlevel or whatever finishd, the last thing stating a battery check or something then an [ok] or something along those lines, bunch of other run previous checks before it.

How do I quit X *and* get to a terminal?

---

### Post by Skripka on 2008-11-09
1)  ctrl+alt+f1, will get you to a login prompt--login

2) at prompt, type you /etc/init.d/gdm stop command

3) install your driver...whatever steps needed (I jumped the ATi ship a while back)

4) at prompt type your /etc/init.d/gdm start

---

### Post by Athiril on 2008-11-09
> **Skripka said:**
> 1)  ctrl+alt+f1, will get you to a login prompt--login

2) at prompt, type you /etc/init.d/gdm stop command

3) install your driver...whatever steps needed (I jumped the ATi ship a while back)

4) at prompt type your /etc/init.d/gdm start

Thanks, that was a missing step other posts didnt specify, got it working, also hode to remove /tmp/.X0-lock (i think that was the file from memory so the nvidia installer stop saying there was an xserver running when there wasnt (if thats not the right file and nvidia still complains about xserver running startx should say which is the offending file).

For other users here is how I got it working (NVidia 64-bit driver for GTX 260).

1)  ctrl+alt+f1, will get you to a login prompt--login

2) sudo /etc/init.d/gdm stop

3) sudo sh /home/dan/NVIDIA-Linux-x86_64-177.80-pkg2.run (replace with where you saved driver file and driver version, you use tab auto complete after typing NV).

4) If NVidia still says Xserver is running, type startx (or sudo startx), and startx should say it also, and say there is a file that needs to be removed.

sudo rm /etc/.X0-lock (or whichever file it says needs to be removed).

Repeat step 3.

5) 
sudo /etc/init.d/gdm start
sudo startx (sudo startx failed for me, restarting worked fine though).

---

