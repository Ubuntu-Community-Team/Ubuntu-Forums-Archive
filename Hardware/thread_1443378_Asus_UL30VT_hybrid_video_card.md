---
title: "Asus UL30VT hybrid video card"
date: 2010-03-31
forum: Hardware
---

### Post by t0lkman on 2010-03-31
My laptop has two videocard one is integrated intel 4500mhd and one is dedicated nvidia gm210.

1) how can I switch between them?
2) at least how can I know what video card is used currently?

Thanks for your help

---

### Post by Fafler on 2010-03-31
Don't know the answer to the first one, but i think there's another thread about just that. As for how to tell which one you are using now, look in /var/log/Xorg.0.log

---

### Post by dabby_yo on 2010-03-31
Hybrid graphics have only just started to be supported in Linux. I think you will have to wait at least a year for decent, matured support.

---

### Post by dakilla on 2010-05-02
you can check the /etc/X11/xorg.conf if you have any.

you probably use the intel card.

to get the nvidia card to work you have to do this:

this is how you get g210m to work on ubuntu 9.10 / 10.04.

1. download and install nvidia drivers. (i have only tested the ones in the repos)

2. make sure you got an Xorg.conf that is correct. ( if not, run nvidia-xconfig )

3. reboot into bios (press delete while booting)

4. change the SATA option in the bios from enhanced to compatibility. ( yea, this makes sense? NOT! )

5. boot into linux and smile!

---

### Post by bryce123 on 2010-05-02
worked for me. previous problems (serious problems) occured because i did not run nvidia-xconf from the commandline (with gdm stopped) after installing the nvidia driver and BEFORE rebooting.

---

