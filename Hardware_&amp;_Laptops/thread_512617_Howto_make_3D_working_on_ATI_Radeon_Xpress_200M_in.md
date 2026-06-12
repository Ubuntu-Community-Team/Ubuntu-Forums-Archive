---
title: "Howto make 3D working on ATI Radeon Xpress 200M in Feisty"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by Penthius_NL on 2007-07-29
I have had alot of people that asked me how to get the 3D stuff working on a ATI 200M card. Here's how I did it on Feisty with Beryl running:

**Step 1.**
Open the restricted drivers manager included in 7.04 "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver"

**Step 2.**
Type this code in your terminal

```
glxinfo | grep direct
```

It shoud answer "Yes" on direct redering

**Step 3.**
Edit you sources.list

```
sudo gedit /etc/apt/sources.list
```

and add the following:
**deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main**
Save it and close it.

**Step 4.**
Type this code in your terminal:
```
sudo wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

**Step 5.**
Type this code in your terminal
```
sudo apt-get update
```

**Step 6.**
Type this code in your terminal
```
sudo apt-get install beryl beryl-manager beryl-ubuntu emerald-themes xserver-xgl
```

**Step 7.**
Type this code in your terminal
```
sudo gedit /usr/local/bin/startxgl.sh
```

And add these lines to the file:
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

Save this file and close it

**Step 8.**
Give the file you have just created permission to execute by typing this code in your terminal
```
sudo chmod a+x /usr/local/bin/startxgl.sh
```

**Step 9.**
Now we edit another file by typing the following code in your terminal:
```
sudo gedit /usr/share/xsessions/xgl.desktop
```

add the folling lines:
```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

Save it and close it

**Step 10.**
Edit another file again by typing the following code in your terminal:
```
sudo gedit /etc/apt/preferences
```

add the following lines
```
Package: *
Pin: release o=lupine
Pin-Priority: 1000
```

Save it and close it

**Step 11.**
Type the following code in your terminal
```
sudo apt-get update
```

then type the following in your terminal
```
sudo apt-get install beryl-core=0.2.0~0beryl1
```

then type the following in your terminal
```
sudo apt-get install beryl-manager
```

Now your done!

I could have written what all codes etc. mean but as i found out from alot of people that they just want the darn thing working so i left that out. Ohh by the way it is better after all this code etc to reboot, some work right away some don't so if yours does not work reboot. 

To make Beryl work at start up instead of clicking it each time you go to SYSTEM -> PREFERENCES you will find where you can make programms startup on boot.

---

### Post by shaft350x on 2007-08-01
Thanks for this post, I was finally able to get Beryl working!  Even Fusion now.  Thanks!

---

### Post by junkalam on 2007-08-06
Worked like a charm. 
THANKS!

---

