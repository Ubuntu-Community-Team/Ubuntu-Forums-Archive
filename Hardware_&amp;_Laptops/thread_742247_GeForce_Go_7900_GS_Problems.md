---
title: "GeForce Go 7900 GS Problems"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by anthonyiacono on 2008-04-01
I am installing Ubuntu, but for some reason whenever I start it all I get is the black screen and the drum sound. I wait for something to come up, but nothing does. I have a GeForce SLI Go 7900 GS graphics card, and I think it may have something to do with this.

---

### Post by chewearn on 2008-04-02
After you hear the drum roll, key in your username, [enter] and password [enter]; (pretend that the screen is showing what you are typing).

Does the user login success, and you hear the welcome music?  And does the ubuntu desktop magically pops back up?

If yes, you have the long suffering bootup resolution problem:
[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

---

### Post by nonewmsgs on 2008-04-19
i have the problem where it does login success and hear welcome music but no magic desktop appears :( .  i have tried the following drivers (with and without fb)
nv
vesa

i actually have 2 9700s in SLI but it is using my main one and i have tried the other and the moniter does say no signal.  the black blank screen is apparantly a signal.

interestingly once this happens i can't even ctrl+alt+f1 to start a terminal.  the screen is just blank until i hit power key and i can read what is turning off

---

### Post by chewearn on 2008-04-19
> **nonewmsgs said:**
> i have the problem where it does login success and hear welcome music but no magic desktop appears :( .  i have tried the following drivers (with and without fb)
nv
vesa

i actually have 2 9700s in SLI but it is using my main one and i have tried the other and the moniter does say no signal.  the black blank screen is apparantly a signal.

interestingly once this happens i can't even ctrl+alt+f1 to start a terminal.  the screen is just blank until i hit power key and i can read what is turning off

Not sure if this will work.  I assumed you have a non-functional install and would mind trashing it while looking for a solution.  Try going into safe mode and install nvidia-glx-new.

---

### Post by nonewmsgs on 2008-04-19
i did a sudo apt-get install nvidia-glx-new but nothing seems to have changed.  does the install set xorg.conf to use those drivers or am i supposed to select nvidia or nv or something?

an annoying thing about recovery mode -- it seems like it does not accept either of my <ctrl> keys...so when i ping i have to do a full reboot and nano can't save or exit.

---

### Post by nonewmsgs on 2008-04-20
ok so i did the whole 
sudo dpkg-reconfigure xserver-xorg 
and seleced nvidia -frame buffer
interestingly i didn't get a signal from either videocard

rebooted to normal changed to nonfb and changed the pci bus address to 1:0:0 
(it was on 10) and when it finished loading and the nvidia spash screen followed by a viewable login screen/real screen was there!!! i nearly jumped for joy.

my problem is fixed, thank you very much.

---

### Post by nonewmsgs on 2008-04-20
on a final note:  this is very important to me, because although hardy is shortly coming out, and i do not have that problem there.  i have something equally as bad there.  on hardy it doesn't let me have wired internet from my ethernet ports, so i am not going to jump right into upgrading.

---

