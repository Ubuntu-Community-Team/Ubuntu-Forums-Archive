---
title: "Sli Issue with 9800 GTX on ubuntu 9.10"
date: 2010-02-11
forum: Hardware
---

### Post by lukaszr on 2010-02-11
hey, i'm hoping someone will be able to help me with this issue i'm having. 

Ok so on my ubuntu 9.10 system, I have two 9800 GTX cards running in Sli. I installed a fresh os of ubuntu 9.10 and all worked fine. I ran all the updates, rebooted, and then proceeded by activating the 185 restricted nvidia drivers. Installation completed successfully. I proceeded with a reboot....

I see the ubuntu little icon as its booting, but then just as its supposed to load the "Login Screen" it hangs on a black screen. 

Can anyone help me or guide me how I can go about fixing this? Its driving me insane, and I'd love to start being able to use my Ubuntu with full accelerated video performance. 

Thanks in advance!

---

### Post by lukaszr on 2010-02-11
BUMP 4 help!

---

### Post by Xog on 2010-02-11
I experience the same thing. I'd like to know what's causing it. I've yet to find the solution, so I haven't updated my drivers on this new install.

---

### Post by lukaszr on 2010-02-11
> **Xog said:**
> I experience the same thing. I'd like to know what's causing it. I've yet to find the solution, so I haven't updated my drivers on this new install.

yeah...


Well im still trying to figure it out myself. If i come across a solution i'll happily post it!

---

### Post by lukaszr on 2010-02-11
Here is a possible solution. I know its for the kde desktop, but try it with gnome...cause i think the detail is in the xorg configuration file. 

I haven't tried it yet, but i will when i get home tonight from school. 


here's the link...

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

---

### Post by lukaszr on 2010-02-11
> **lukaszr said:**
> Here is a possible solution. I know its for the kde desktop, but try it with gnome...cause i think the detail is in the xorg configuration file. 

I haven't tried it yet, but i will when i get home tonight from school. 


here's the link...

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

didn't work for me... :(


any solutions guys?

---

### Post by lukaszr on 2010-02-11
OK I FOUND A FIX!!!

Here step by step what i did to get the Nvidia Drivers to work with Sli 9800 GTX...

1) I installed a "Fresh" copy of Ubuntu, just to be sure. 

2) Updated the sytem (rebooted)   *DO NOT APPLY THE RESTRICTED DRIVERS*

3) Went into Applications> Ubuntu Software Center and searched "Nvidia"

4) Select and install "NVidia binary X.Org driver ('version 185' driver)

5) Open terminal and run "sudo nvidia-xconfig"

6) After step 5 immediately type "sudo service gdm restart"
*you will be logged out and X server will restart*

7) And thats ALL!!! You should be able to open the nvidia control panel in administrative section and see the sli!!

ENJOY PEOPLE!! 

*Mods mark this as "SOLVED"*

---

### Post by Xog on 2010-02-13
I get an error when I try to login to the computer. It says I may need to reconfigure my video settings. It also said it can't find a video driver. I clicked OK

Then it gave me a bunch of options,
Run ubuntu in low-graphics mode once
Create new configuration file
and a few other things..

anyways, the Nvidia control panel is in system > admin. see below.

[http://img194.imageshack.us/img194/7008/screenshothf.png](http://img194.imageshack.us/img194/7008/screenshothf.png)

I tried what it said and then it just did the same thing.

---

### Post by lukaszr on 2010-02-13
> **Xog said:**
> I get an error when I try to login to the computer. It says I may need to reconfigure my video settings. It also said it can't find a video driver. I clicked OK

Then it gave me a bunch of options,
Run ubuntu in low-graphics mode once
Create new configuration file
and a few other things..

anyways, the Nvidia control panel is in system > admin. see below.

[http://img194.imageshack.us/img194/7008/screenshothf.png](http://img194.imageshack.us/img194/7008/screenshothf.png)

I tried what it said and then it just did the same thing.

Well its giving you that error because you haven't ran "nvidia-xconfig" in terminal. 

So open a terminal and run "sudo nvidia-xconfig" and then right after run "sudo service gdm restart"

Login, and then open the nvidia settings through terminal running "sudo nvidia-settings" and then locate GPU 0 and click on DFP-O and click "Acquire EDID" and reboot and it should work!

---

### Post by Xog on 2010-02-13
made my own thread, hopefully u can help me there.

---

### Post by Xog on 2010-02-13
> **lukaszr said:**
> Well its giving you that error because you haven't ran "nvidia-xconfig" in terminal. 

So open a terminal and run "sudo nvidia-xconfig" and then right after run "sudo service gdm restart"

Login, and then open the nvidia settings through terminal running "sudo nvidia-settings" and then locate GPU 0 and click on DFP-O and click "Acquire EDID" and reboot and it should work!

I am. Here, look:

```

logan@logan-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

when I execute sudo service gdm restart, it just brings me back to the error message.

But you know what? After the first error message, I can't reproduce it. It's just a black screen. I had to log in thru an older kernel to post on here. This is my last one. The other two kernels are all used up. Not functioning.

I select the kernel from the grub menu, hit enter. It proceeds to login, to where I get to the black screen with the white circle thing, then it dissappears and nothing happens!

---

### Post by lukaszr on 2010-02-13
> **Xog said:**
> I am. Here, look:

```

logan@logan-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

when I execute sudo service gdm restart, it just brings me back to the error message.

But you know what? After the first error message, I can't reproduce it. It's just a black screen. I had to log in thru an older kernel to post on here. This is my last one. The other two kernels are all used up. Not functioning.

I select the kernel from the grub menu, hit enter. It proceeds to login, to where I get to the black screen with the white circle thing, then it dissappears and nothing happens!

check the thread you made, i've responsed. 

and you can log with terminal using "Ctrl + Alt + F1"

---

