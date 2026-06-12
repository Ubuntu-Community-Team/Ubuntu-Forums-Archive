---
title: "Not even able to login..."
date: 2008-11-04
forum: General Help
---

### Post by Cronoadvan on 2008-11-04
Im new to Ubuntu, and was waiting for the 8.10 release. In fact, i haven't been able to even use it.. I "installed" Intrepid Ibex flawlessly, but when the system reboots after install and asks for username and password, i get a black screen and a lockup. I dont know what to do, and i really want to try and use this OS. Hope someone here could help me.

---

### Post by Peter09 on 2008-11-04
When the Grub prompt comes up type ESC. Then select recovery mode (normally the second one down). This should take you to a screen with some options. Initially try the reconfigure x-server (or words to that effect) see if that helps.

If not then drop to the command shell and type startx - see what happens.

Come back and tell us ;)

---

### Post by Cronoadvan on 2008-11-04
Whoa, that was fast. Thanks for your quick reply :p.

Itried what you said. As far as i can see, what u told me to do tries to reset the system configuration? 

Well, sadly, nothing happened. And after typing startx in the shell, it just hanged and my monitor went to sleep mode. So, am i having a video card problem with Ubuntu?

I also forgot to mention[silly me] that when i try to repair broken packeges, it says i have to download about 30mb to fix something, but when tell it to do it, it just says 'completed' instantly. This happens everytime i reinstall the system. 

Thanks again for your support, hope you're able to further help me :D.

---

### Post by sdowney717 on 2008-11-04
go back to the command prompt and type 
sudo dpkg-reconfigure -phigh xserver-xorg

then reboot

---

### Post by Peter09 on 2008-11-04
OK

drop back into recovery mode and command prompt.

type
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```


See what happens then

---

### Post by Cronoadvan on 2008-11-04
OK, first of all:

**sdowney717:**

I tried your suggestion, it warns me of overwriting a modified file and creating a backup in a folder i dont know a thing about, then it just stays there. I type xstart and it just hangs and my monitor goes to sleep. I tried this after:
```
sudo dpkg-reconfigure -au
```

Then it started checking a lot of things[packages, i pressume...] and only failed in one:

> Avahi mDNS/DNS-SD Daemon avahi daemon   FAIL

After that, it got me to configure the keyboard and stuff, until it gave me this:
It told me it was unable to 'compile' this
> gtk-theme-selector.desktop

I hope i didnt mess anything up :(.

**Peter09**

Then i tried your suggestion, heres what happened:

This one worked.
```
sudo apt-get clean
```


Said some index files have failed to download, and listed a bunch of files. 
```
sudo apt-get update
```

Said it couldn't resolve these addresses:

> do.archive.ubuntu.com

> security.ubuntu.com

And of course, this one failed too...
```
sudo apt-get upgrade
```


So, i cant update because i have no internet?[wich i do, obviously]

If  you need me to be more specific just tell me what you may need to know and its done :).

---

### Post by sdowney717 on 2008-11-04
"sudo dpkg-reconfigure -phigh xserver-xorg"

should run silently and ask for no feedback or prompt you much at all.

What this does is reconfigure xorg.conf to work with the free linux video driver.

your problem sounds like an issue with the video driver setup.

In location /etc/x11/ is a file called xorg.conf 
This file controls a lot of how ubuntu interacts with mouse, keyboard and video, so if it is not right, then bad things happen.
The dpkg-reconfigure command creates an xorg.conf that ubuntu free driver can work with. At that point, when you reboot, xorg everytime it boots, auto configures and auto detects monitors, keyboars, mice, etc... in real time and hopefully it just works

---

### Post by Paresh on 2008-11-04
Not sure what pc you have, but I had a similar problem on my Toshiba Tecra.

Shows the login screen correctly, but hangs after logging on.

For me, the problem was with the graphics card and with /etc/X11/xorg.conf using XAA.

In the section for my "Configured Video Device", changing the *AccellMethod* from *XAA* to *EXA* fixed this.

Co-incedentally, it also fixed my video playback problems.

---

### Post by Peter09 on 2008-11-04
another option is to move the file /etc/X11/xorg.conf in case there is some sort of compatibility problem and try reconfiguring again

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.saved
```]

---

### Post by Cronoadvan on 2008-11-05
Well, here it goes:

After a lot of time trying to get the code to work, i realized its CAPS sensitive.

So, after 'moving' the xorg.conf file, i tried to reconfigure. When i got it right, it was the first thing the shell did without complaining. I though i was finally done, typed 'startx' and...

Either:

-Got the same 'entering sleep mode' screen OR
-Got a static like screen.

The difference is that the computer seems to be responding, since in the second case numlock turns on and off. Maybe i just had to wait, but im  a bit impatient :p .

So, after that i tried to 'manually' configure it, repeating the steps above, but just with this code:
```
sudo dpkg-reconfigure xserver-xorg
```

It took me to a screen with choices, the first one being the video mode one. All of the other options were keyboard-related. I tried both video options and rebooted manually, via the 'reboot' command and 'startx'. The same thing happened.

I have no idea how to change the acelleration method to EXA, i dont even know what EXA means[:p], but now im pretty sure its a video card problem.

Here are my system specifications:

**Motherboard:** **[**[COLOR="Blue"]Gigabyte GA-8I845GV(-C)[/COLOR]**]**
**Video_Card:** **[**[COLOR="Blue"]Intel(R) 82845G/GL/GE/PE/GV Graphics Controller[/COLOR]**]**
**Processor:** **[**[COLOR="Blue"]Intel Pentium 4 Northwood[/COLOR]**]**

Am i forgetting  anything?....
Well, anything else needed, let me know.

Also, the fact the pc cant connect to ubuntu.com to download anything is kinda bugging me...

Thanks again for all of your help :).

---

### Post by Peter09 on 2008-11-05
It might be worth working at your internet connection as the download may fix your problems. What is exactly the problem?

---

