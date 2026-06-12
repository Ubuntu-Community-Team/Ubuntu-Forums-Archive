---
title: "HowTo: ATI 8.21.7 Linux"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by s0n0fagun on 2006-02-01
First of all, I would like to point out that there are mutiple ways of doing this however, many experienced different results.  Also, I don't know if this would go under howto because it could not work on your machine.

My laptop has a ATI Mobility 9700.  Running the terminal command, Ubuntu identified it as mesa3d.org and using their drivers.  Many guides will tell you to try reinstalling it.  I did, but this did not work.  But for some odd reason, the installer did work doing and making sure the following:

1) Enable Universal Respertories
2) Launch the termnal and type:
sudo sh ./ati-driver-installer-8.21.7.run
3) A box should open up.  Choose Automatic
4) Costomize the options and make sure everyone is selected and continue to install
5) It will then tell you to enter the termal to apply extra stuff
6) Open up a second terminal and type this command in:
sudo aticonfig --initial
This will write to the xorg file/create it, updating all the neccessary info and so forth.
7) Restart
8) Launch terminal and type fglrxinfo to confirm changes were made.

If this process didn't work try launching the config (sorry I forgot the command it's the one that has small success) and try my steps again.  If this yields to be successful, post this in the HowTo forums please.  Or move it or whatever. :-)  Anyways I hope this helps ATI users out there.

---

### Post by Joriz on 2006-02-03
I get this error:

```
 sudo aticonfig --initial
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

```

My card: ATI 9000 Mobility 64MB
Ubuntu 5.10

---

### Post by henshu70 on 2006-02-03
[QUOTE=Joriz]I get this error:

```
 sudo aticonfig --initial
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

```

My card: ATI 9000 Mobility 64MB
Ubuntu 5.10[/QUOTE]
Same problem as Joriz here. Seems it doesn't work at all (from what you can find in other threads).

---

### Post by Joriz on 2006-02-03
It's working now, i followed these steps:
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

greetz

---

### Post by Minilek on 2006-02-03
I tried the steps at [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584), but they did not help me.  Xorg.0.log says "no screens found".  I'm running amd 64-bit with a radeon x1800.

---

