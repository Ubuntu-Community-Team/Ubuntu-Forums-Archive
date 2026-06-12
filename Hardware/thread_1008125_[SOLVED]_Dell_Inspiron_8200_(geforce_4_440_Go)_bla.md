---
title: "[SOLVED] Dell Inspiron 8200 (geforce 4 440 Go) black screen"
date: 2008-12-11
forum: Hardware
---

### Post by deroby on 2008-12-11
Hi all, 
I've been reading all over the forums, but was unable to get a decent answer from it anywhere =( Since this is "common" hardware I do hope that there are others who suffered the same issue and managed to resolve it.

Hope this makes sense to someone as my work-around is kind of annoying =(

After some fiddling around in 8.10 I've managed to install the nvidia driver (96.43.09), which for a newby like me was quite a feat =) Anyway, when I start the machine, I get the progress-bar but then the screen simply turns black and does not come back up again. I do hear the 'drumroll' that says I should login, but noting can be seen. Doing a "blind" login does let me start up gnome etc, but the screen remains pitch-black. 

Work-around 1 : After logging in 'blind', CTRL-Alt-Backspace "sometimes" (yeah, I know) seems to help out, causing some flickering and (sometimes) resulting in a visible login-screen. When I log in again, things look OK, although Nautilus sometimes comes complaining about an error regarding "Bonobo" not responding.

Work-around 2 : I press CTRL-Alt-1 and login to tty1. Then use the command : sudo gdm stop
=> it complains about the GDM already running (!?!)
Next I do : sudo gdm start
=> some flickering and then a screen telling me that X is already running on display 0 and whether I want to add a new terminal, I press [Yes], it switches to graphical mode and tells me that it started the server on display number 1. This appears to be under Ctrl-Alt-F8. There everything runs perfectly!

I'm currently using work-around 2 as it seems that everything works 100% there, but I do wonder why it works on terminal 8 and not on terminal 7 when booting up. No config is changed in the meanwhile afaik, so shouldn't it react exactly the same ?

Hope somebody can shed some light on this. Please keep in mind that although I know my way around windows, I'm pretty much a newby in linux and learned most things by troubleshooting hardware from the forums, sigh... then again, we like to learn =)

---

### Post by deroby on 2008-12-11
UPDATE : after logging in 'blind' I was able to connect using VNC from another pc. Running the System/Nvidia X Server Settings app then showed me that the CRT screen is enabled (Huh, don't have external monitor attached (nor available for that matter)) and that the Default Panel (DFP-0) is disabled.
* I changed the config of the latter to TwinView, pressed [Apply] and hurray, the laptop screen came to life !
* I then configured the CRT-0 display to Disabled, pressed [Apply] again and the nvidia app appeared on the laptop screen !!

When I try to save this to the X config file, it complains about being unable to write to the file. I'm assuming this is a security issue, so I simply save it on my home directory and copy it afterwards to /etc/X11/xorg.conf using the terminal

Currently rebooting ... fingers crossed....:p

---

### Post by deroby on 2008-12-11
Hallelujah, it works !

Now properly boots up on the laptop screen

These forums are great ! =)

(at work we call this a 'Wooden Indian', one finds the solution by simply explaining it to someone without that person having to respond or interact... so it would even work when explaining it to a lifeless statue, or a forum for that matter =)


PS: I do still get the error that Nautilus can't connect to the Bonobo activation server, so I know what to look for next =)

cheers all.

---

