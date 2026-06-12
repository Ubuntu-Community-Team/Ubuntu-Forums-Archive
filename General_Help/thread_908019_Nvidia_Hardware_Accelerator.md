---
title: "Nvidia Hardware Accelerator"
date: 2008-09-02
forum: General Help
---

### Post by Null81 on 2008-09-02
Sigh, well today i just installed Ubuntu And i am having some trouble. 

Well, whenever i enable my nvidia accelerator thingymajig and i decide to set my resolution over 800x600 it is like the entire thing is zoomed in. i can move my mouse around to view the entire thing but nevertheless it makes games impossible

also. my damn 19 inch I-inc monitor isnt in the manufacturing list, could this be my problem? Whenever i set it to generic plug and play lcd panel above 800x600 it does the zoom.

specs

Intel pentium 4 2.4ghz
256mb RDR ram
Nvidia Geforce4 mx 420

obviously i know my cpu is anything but perfect, but i believe ubuntu should work.

can i get any help? When i tried out Xubuntu i got the same results.

Im goin to bed  now, it is 3:12 AM i hope this has responses by 2morro =)

see you all later, i am really looking forward to being a linux user.

---

### Post by Perfect Storm on 2008-09-02
First try if you can change the settings via nvidia;

Terminal;
```
gksudo nvidia-settings
```

May require you restart X to take effect when you have done the changing.

---

### Post by Null81 on 2008-09-02
what do you mean restart x?

---

### Post by kpkeerthi on 2008-09-02
> **Null81 said:**
> what do you mean restart x?

Press ctrl + alt + backspace

---

### Post by littletinman on 2008-09-02
> ctrl-alt-backspace

That resarts the X server, in other words, your graphics.


the little tin man

---

### Post by Null81 on 2008-09-02
thanks guys. i'm in the ubuntu half of my hard drive, i'll try the terminal right now

---

### Post by tuxxy on 2008-09-02
Open a terminal and type

```
sudo apt-get install nvidia-settings
```

Now run the program like this, it must be run as root to save the changes to the xorg.

```
gksu nvidia-settings
```

Finally select the **X display configuration **tab and edit resolution till your happy

---

### Post by Null81 on 2008-09-02
what do you mean by run it in root, i am not familiar how to.

---

### Post by tuxxy on 2008-09-02
> **Null81 said:**
> d'oh!

whenever i type in the terminal

```
gksudo nvidia-settings
```

the damned thing asks me for my password which i graciously give, and then it does nothing. =(

well, i am updating my ubuntu version with the 109 software updates available. 

so after that i will try to restart X then the cpu itself and try again, as i said i am a complete noobie to this so any help would be appreciated =)

You may not have to restart X and the password output you are entering as just not showing up for security reasons, just type it an is normal and hit enter

---

### Post by Null81 on 2008-09-02
> **tuxxy said:**
> Open a terminal and type

```
sudo apt-get install nvidia-settings
```

Now run the program like this, it must be run as root to save the changes to the xorg.

```
gksu nvidia-settings
```

Finally select the **X display configuration **tab and edit resolution till your happy

 sigh, i typed in sudo apt-get install nvidia-settings

and i got this
```

jake@jake-desktop:~$ sudo apt-get install nvidia-settings
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

i think this may because i am running the 109 software updates, so after that is done i will restart my machine and then try your advice

---

### Post by tuxxy on 2008-09-02
Yes that error is simply because you have another software update running, run the command when all other updates have finished and are closed eg Synaptic

---

### Post by Null81 on 2008-09-02
God dammit

well, i did all this and i changed my resolution to 1200x1024 i could run that on windows so i know it should work

anyway i restarted x server and etc and i got my resolution, but everything was zoomed in. lets say i moved my cursor to the right, the screen would go to the right and like that, it was like a magnifying glass on my screen and i can never zoom out.

HELP!!!! pleae

---

### Post by tuxxy on 2008-09-02
Before you restarted the X server, was the 1280x1024 resolution working

---

### Post by Null81 on 2008-09-02
no, honestly it didnt change a thing

---

### Post by tuxxy on 2008-09-02
You could try **envyng** to install the correct driver, be sure to disable the current one first though, envyng is in the repos and should select the correct driver for you, however that card isnt listed on the hardware support wiki and theres a few posts with people having problwems with that card.  Hopefully someone who owns one will enlighten us.

---

### Post by Null81 on 2008-09-02
i tried installing my monitor installation disc but wine is not proving to be useful with it. 

here is a screenshot of what it looks like 

NOTE: when i take a screenshot of the resolution it appears as it should be!

weird. 


but i will take a screenshot of this 

[[IMG]http://img161.imageshack.us/img161/2913/screenshotvs4.png[/IMG]](http://imageshack.us)
[[IMG]http://img161.imageshack.us/img161/screenshotvs4.png/1/w800.png[/IMG]](http://g.imageshack.us/img161/screenshotvs4.png/1/)

---

### Post by Null81 on 2008-09-02
what is envy? how can i use it???

---

### Post by Null81 on 2008-09-02
hey, would an older version of ubuntu like gutsy of fiesty work?

---

### Post by Null81 on 2008-09-02
anyone?

---

### Post by tuxxy on 2008-09-02
envy will install the drivers for your card, open synaptic and search for envy to install.

---

### Post by Null81 on 2008-09-02
downloading envy now.

---

### Post by Null81 on 2008-09-02
again though, would an Older version of Ubuntu work better?

---

### Post by Null81 on 2008-09-02
envy did not help


so i think im either gunna try a diferent distro or a older version of ubuntu. 

are there any good distros i can install without a cd like ubuntu?

---

### Post by Null81 on 2008-09-03
still no one to help =[

---

### Post by Perfect Storm on 2008-09-03
Never heard of this problem, but post your xorg.conf


```
cat /etc/X11/xorg.conf
```

---

### Post by Null81 on 2008-09-03
i gotta reinstall ubuntu i deleted it out of discouragement, heh

ill go at xubuntu again but i will need some help.

---

### Post by Null81 on 2008-09-03
Solved

it was my monitor!

---

