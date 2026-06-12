---
title: "[SOLVED] Notification Area is gone"
date: 2008-08-17
forum: General Help
---

### Post by kierpaul on 2008-08-17
Can anyone help me out here! Last night my Ubuntu Hardy locked up on me and I had to power down to get back in and when I got back in my Notification Area is gone! I have no Application, Places, or System on my Desktop. All my folders are still there, but the bar at the top and bottom seem to have disappeared. I can get to a terminal window if I boot into it from the boot menu. Any help would be greatly appreciated!

Joe

---

### Post by vishzilla on 2008-08-17
Do you have the panel on top? If not, right click on the bottom panel and select New Panel

Then on your new panel, right click and select Add to Panel. From that you have to add Menu Bar, Notification area

---

### Post by dje on 2008-08-17
press Alt+f2 and type:
```
gnome-terminal
```
in the terminal type:
```
gnome-panel
```
if there are any errors please post them here

dje

---

### Post by kierpaul on 2008-08-17
Thanks, but I have not had any success restoring my desktop. I have no bar at the top or bottom and when I right click on the desktop I only have the regular options there for setting the background and such. I tried CNTRL+ALT+F2 and gnome-terminal and gnome-panel in the terminal and it did not like it. I had to login as well to the desktop in terminal. Any help is appreciated and thank you thus far!

---

### Post by dje on 2008-08-17
> **kierpaul said:**
> Thanks, but I have not had any success restoring my desktop. I have no bar at the top or bottom and when I right click on the desktop I only have the regular options there for setting the background and such. I tried CNTRL+ALT+F2 and gnome-terminal and gnome-panel in the terminal and it did not like it. I had to login as well to the desktop in terminal. Any help is appreciated and thank you thus far!

what do you mean it did not like it? and it should be Alt + F2 **not** Ctrl + Alt + F2

dje

---

### Post by kierpaul on 2008-08-17
dje- 

I tried just alt+f2 and nothing....so I tried ctrl+alt+f2 and it took me into a terminal window for my desktop where I had to login. I typed gnome-terminal and it did not like the command...it acted as if I were missing some parameters. Also, gnome-panel directed me to try install by using the "sudo apt-get" command when I typed it in. Info: I am dual booting, but on separate hard drives so I have to move back and forth!....Thanks

joe

---

### Post by dje on 2008-08-17
ok i understand now. switch to the tty again (Ctrl + Alt + F2) and run this:
```
sudo adduser *new username*
```
this will create a new user, then run:
```
sudo /etc/init.d/gdm restart
```
login with the new user and see if everything works ok

dje

---

### Post by kierpaul on 2008-08-17
dje-

Thanks again for your help...I did exactly as you told me, but I had the same results with a new user. Also, all my desktop files were not their, but this is normal because it is a new user!

---

### Post by dje on 2008-08-17
ok right click on the desktop and click "Create launcher" in the command box put:
```
xterm
```
fill what you like in the others and click ok. double click the launcher, hopefully it will open a terminal, try this:
```
killall gnome-panel
```
if your panels don't appear try this after the above:
```
gnome-panel &
```

dje

---

### Post by kierpaul on 2008-08-17
dje-

I did a killall gnome-panel and it stated: "no process killed." I had the same results after trying these things. I think something went wrong with the install of Ubuntu or something. Thank you for your help, but I think I may reinstall. I do not want to go back to using Windows, but I do not want these kinds of things to keep happening either. It is very time consuming and I have to go outside and finish a retaining wall before it gets to hot! Any more ideas? I will talk to you later on....thanks again!

Joe

---

### Post by dje on 2008-08-17
did you try running:
```
gnome-panel &
```
i'm not sure because each time i've helped someone with this it is usually fixed by creating a new user and logging in as that user, but that didn't work for you? sorry i did not solve your problem

dje

---

### Post by kierpaul on 2008-08-17
dje-

 I will attempt gnome-panel &, but I am pretty sure that I did this....sorry short memory I have sometimes with everything going on! Thank you for your help!

Joe

---

### Post by kierpaul on 2008-08-17
dje-


    O.K. I got my panels back by going "sudo apt-get install gnome-panel" however, I now have these three errors at start-up asking me to delete the applet, and of course I said "no." Each error is separate though. Here it is:

The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".

The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet"

Do you want to delete the applet from your configuration?

---

### Post by dje on 2008-08-17
it doesnt delete it it just removes it from the panel try doing this:
```
sudo apt-get install gnome-applets
```
or:
```
sudo apt-get install --reinstall gnome-applets
```

dje

---

### Post by kierpaul on 2008-08-17
dje-

Hey thanks for all your help, installing the gnome-applets worked! I did what you directed me to do and all is working accept I now have a text editor that starts up when I boot up...gedit starts up when I boot up for some reason! Other than that everything is back to normal and I thank you very much for helping me out! It is very much appreciated! I would have replied earlier but we had to run to Menard's! Thanks!

Joe

---

### Post by dje on 2008-08-17
> **kierpaul said:**
> dje-

Hey thanks for all your help, installing the gnome-applets worked! I did what you directed me to do and all is working accept I now have a text editor that starts up when I boot up...gedit starts up when I boot up for some reason! Other than that everything is back to normal and I thank you very much for helping me out! It is very much appreciated! I would have replied earlier but we had to run to Menard's! Thanks!

Joe

no problem, i'm glad it's working. have a look in System >> Preferences >> Sessions at the startup programs, gedit is probably in there, just remove its entry or untick it

dje

---

