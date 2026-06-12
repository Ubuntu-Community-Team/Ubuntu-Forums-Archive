---
title: "Pls help with a big problem"
date: 2008-10-25
forum: General Help
---

### Post by kostaz8 on 2008-10-25
Hello everyone i have a big problem and i cant solve it.Lets start a have been using ubuntu for a month now and i didn't had any problems but many times the pc couldn't open any software use terminal play music even reboot i had to restart it to make it stop. Today did it again and pissed me off i tried to find a solution searching the net i had found a threat for repairing the sound problem here on you forum [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) . I did the step "Getting the ALSA drivers from a *fresh* kernel" i don't know why i chosen why i to do what it said maybe because i am a noob in step 3 says reboot so i rebooted after the reboot ubuntu could not start after the loading screen o command screen like a terminal appeared saying kostas-ubuntu@ubuntu login: something like that and i don't know what to do.pls someone help me im a newbie and i cant do anything, i don't want to reinstall Linux because i have precious data on my hard drive with my family and friends and i don't want to lose it. so pls help i will appreciate what you will do for me. Thank you.

---

### Post by ddrichardson on 2008-10-25
Did you forget to reinstall GDM? Login at the prompt, using your username and password and try typing startx, if it comes up then you need to reinstall GDM.

---

### Post by kostaz8 on 2008-10-25
how to do that i cant connect to the internet and i dont know how to reinstall it

---

### Post by ddrichardson on 2008-10-25
You said you had a login prompt, the kostas-ubuntu@ubuntu login: bit.

Enter your username, then password and type startx. Then let us know.

---

### Post by kevstar31 on 2008-10-25
Type in the username and password you usally use.
type in startx and write down any errors given.

---

### Post by kostaz8 on 2008-10-25
sorry for being a noob but i cant understand .when i login i cant do nothing except for using terminal .im an noob i know.

---

### Post by kevstar31 on 2008-10-25
Type startx, hit enter and tell us what happens.

---

### Post by kostaz8 on 2008-10-25
it started thnx for your help but i have to do this every time i start my pc?

---

### Post by kevstar31 on 2008-10-25
Try reinstalling GDM

---

### Post by ddrichardson on 2008-10-25
If he hasn't internet than he cannot. If you can then:
```
sudo apt-get install gdm ubuntu-desktop
``` and reboot.

---

### Post by berriop on 2008-10-25
and don't be worried about your data (pictures, files,etc), you always can use the liveCD to boot the computer and retrieve all your data. In case that you cannot start your computer insert the unbuntu CD into the cd drive and restart the computer from the CD. You can have access to the liveCD desktop and from there you can copy all your data to eg. a external drive.

---

### Post by kostaz8 on 2008-10-26
ok i started my pc when then an erro appeared saying 

[CENTER]The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

Do you want to delete the applet from your configuration?[/CENTER]


and i reinstalled DGM

i shut down and restart buttons are not appearing and when the pc starts i have to login and type startx

---

### Post by ddrichardson on 2008-10-26
Its GDM, you probably need to manually add the service at boot, type:
```
sudo update-rc.d gdm defaults
```

---

