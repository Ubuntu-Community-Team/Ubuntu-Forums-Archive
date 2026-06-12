---
title: "white screen after fglrx installed"
date: 2008-07-30
forum: General Help
---

### Post by whalogreg on 2008-07-30
I just installed 8.04 and updated the system. the first thing I did after doing so, was installed the fglrx driver for my ati driver (the same I used for 7.10) and after rebooting, after the login screen, I get a white screen and a working mouse cursor. I tried all of the options in the "recovery boot" menu (Xfix and repair broken packages) and don't know where to go from here.. maybe uninstall the driver from the shell menu (although I don't know how). plus what driver could I use for my ati card (all the ones I could find are for 64 bit systems including the driver from ati's site, and i'm runnung a 32 bit)..

---

### Post by david_lynch on 2008-07-30
I had the same problem when I installed the fglrx drivers. I went to the console and uninstalled them with apt-get remove, then restarted X and got the old desktop back. 

At that point I installed the fglrx-envy drivers, and they worked without any problem. I don't know all the details of what is different between the two, but the envy driver install took awhile building stuff on my machine during the install.

So bottom line, the fglrx-envy drivers worked fine for me, after the plain fglrx drivers were found to result in a white screen.

---

### Post by tuxxy on 2008-07-30
If the system > admin > hardware drivers dont work then use Envy

---

### Post by whalogreg on 2008-07-30
> **david_lynch said:**
> I had the same problem when I installed the fglrx drivers. I went to the console and uninstalled them with apt-get remove, then restarted X and got the old desktop back. 

At that point I installed the fglrx-envy drivers, and they worked without any problem. I don't know all the details of what is different between the two, but the envy driver install took awhile building stuff on my machine during the install.

So bottom line, the fglrx-envy drivers worked fine for me, after the plain fglrx drivers were found to result in a white screen.

what is the exact code to remove the driver? and whar directory should I be in to do so?

---

### Post by tuxxy on 2008-07-30
This maybe of use;

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by whalogreg on 2008-07-30
> **tuxxy said:**
> This maybe of use;

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

thanks, but that's where I went to figure out how to properly install the driver and that's what lead me to where I am now with the white screen.. like I said before the fglrx driver is giving me the white screen and the one from ati's site is for 64 bit machines, not 32's such as mine...

---

### Post by whalogreg on 2008-07-30
> **whalogreg said:**
> what is the exact code to remove the driver? and whar directory should I be in to do so?

so if I were in a terminal, what directory should I be in and what would the command be to remove fglrx?

---

### Post by whalogreg on 2008-07-30
> **tuxxy said:**
> If the system > admin > hardware drivers dont work then use Envy

I plan on it.. just looking for a way to get rid of the white screen now..

---

### Post by david_lynch on 2008-07-31
> **whalogreg said:**
> so if I were in a terminal, what directory should I be in and what would the command be to remove fglrx?
You don't need to be in any specific directory to run a linux command. I don't remember the exact name of the fglrx driver, but it's called something like **xorg-driver-fglrx**. In any case you can find out exactly what it's called by running the command

```
sudo dpkg -l | grep fglrx
```

Note the output that looks most obviously to be the video driver in question. Copy and paste that string, or type it exactly (let's assume it's called xorg-driver-fglrx) into the command which follows

```
sudo dpkg --remove xorg-driver-fglrx
```

Upon which you should be rewarded with the removal of said driver. (I don't remember if ubuntu wanted me to reboot at that point, I may have just given the CTL-ALT-BKSP to restart X), but after that I was back to the vanilla X GUI.

Once you get back to the original GUI you can install the envy drivers.

---

### Post by whalogreg on 2008-07-31
> **david_lynch said:**
> You don't need to be in any specific directory to run a linux command. I don't remember the exact name of the fglrx driver, but it's called something like **xorg-driver-fglrx**. In any case you can find out exactly what it's called by running the command

```
sudo dpkg -l | grep fglrx
```

Note the output that looks most obviously to be the video driver in question. Copy and paste that string, or type it exactly (let's assume it's called xorg-driver-fglrx) into the command which follows

```
sudo dpkg --remove xorg-driver-fglrx
```

Upon which you should be rewarded with the removal of said driver. (I don't remember if ubuntu wanted me to reboot at that point, I may have just given the CTL-ALT-BKSP to restart X), but after that I was back to the vanilla X GUI.

Once you get back to the original GUI you can install the envy drivers.

Well, I installed the envy driver and ran into the same problem with the white screen after logging in... Should I just go back to 7.10?

---

