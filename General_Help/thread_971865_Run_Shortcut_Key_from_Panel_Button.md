---
title: "Run Shortcut Key from Panel Button"
date: 2008-11-05
forum: General Help
---

### Post by luceerose on 2008-11-05
Is there a way to run an assigned shortcut key from a panel button ?
I want to be able to click on a button on my bottom panel to initiate the Expo plugin, Instead of having to use the Win+E shortcut key all the time.

I can't just change the Expo bindings to initiate from wheel click or anything like that, because I also use the desktop cube (from wheel click).

The best thing for me would be a clickable shortcut/launcher/panelbutton that will just emulate the shortcut key.

Any Ideas ?

---

### Post by luceerose on 2008-11-05
I found it. [SOLVED]
This will only work for Expo. I still don't know if it's possible to make a launcher from any old keyboard shortcut.
Anyway this worked for me;

1) Make sure Dbus is enabled in Compiz-Settings
2) Make new file anywhere you want
3) Edit new file and paste this in it;
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/expo/allscreens/expo_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
4) Save file as whatever.sh (I called mine Expo.sh)
5) Put new application Launcher on your Panel with command /path/whatever.sh

Thanks to Kawaji, in the following thread;
[http://ubuntuforums.org/showthread.php?t=744668&highlight=expo+shortcut](http://ubuntuforums.org/showthread.php?t=744668&highlight=expo+shortcut)

---

### Post by kawaji on 2008-11-06
if your Ubuntu is Intrepid Ibex, "xdotool - fake keyboard/mouse input" package is available.
```
sudo apt-get install xdotool
```

[http://www.semicomplete.com/projects/xdotool/](http://www.semicomplete.com/projects/xdotool/)

the following command initiates EXPO,for example:
```
xdotool key super+e
```

Edit: 
oh.. I missed your sig line. 8.04..

---

### Post by KrimZon on 2009-05-02
xdotool is present in hardy-backports

settings->repositories->updates in synaptic, check unsupported updates, then reload, then what kawaji said will work.

I was having trouble with the dbus command, this works a treat.

---

