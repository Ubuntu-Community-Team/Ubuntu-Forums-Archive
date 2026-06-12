---
title: "Compiz causing flickering?"
date: 2008-07-27
forum: General Help
---

### Post by anj on 2008-07-27
Hey all, I've been experimenting with using Compiz. I use VLC a lot and at first Compiz was causing it to become extremely slow in fullscreen playback but I found that turning on Unredirect Fullscreen Windows helped with that.

But if I run a game like SuperTux or Xmoto, I get flickering no matter whether I'm in full screen or windowed, which disappears as soon as I disable desktop effects entirely.

Any suggestions? :confused:

---

### Post by Cresho on 2008-07-27
I have one.  I run a script (well, too many) that disables compiz and activates a game.  After the game is closed, compiz automatically activates the compiz.  I also have a tutorial that makes compiz run as smooth as silk.

anyway, here is what i do.

let us say you are running doom3

my script looks like this

```
#!/bin/bash
#Script Compiz/on/off

# Compiz off;
killall compiz.real &
metacity --replace &

#run game;
sleep 3 &&doom3;

#Compiz on;
compiz --replace &
metacity --replace &
```

anyway, right click on the screen, create document empty file.  open this up with text editor and place that script in the text file and save. save it as yourgamename.sh  then right click and go to properties and hit the permissions tab and click or tick the allow as executable.
now right click on the start launcher or applications os to say or open menu editor under system->prefferences->main menu find the game you want and double click on it to see the command.  If my game is foobilliard and i copy the command foobilliard, then

```
#!/bin/bash
#Script Compiz/on/off

# Compiz off;
killall compiz.real &
metacity --replace &

#run game;
foobillard

#Compiz on;
compiz --replace &
metacity --replace &
```

save the file.  at this point you can double click on it or replace the executable command of that file in the main menu.  place the sh file you made in a place like "installed_programs"(this is where i put all my custom junk.) and in the main menu where you opened the launch properties for the game under command there is a browse button.  navigate to the location of the sh file and choose that game.sh file you made.  close it all and now you can launch it from the start menu no problems.

if you are using emerald instead of metacity, replace name metacity with emerald.  this is the border manager.  if you havent modified it, don't sweat it.

---

### Post by anj on 2008-07-27
Yeah I'm running emerald and using a script like that just makes GNOME hang. Could only escape to terminal.

---

### Post by Cresho on 2008-07-27
hmmm.  I installed all the supertux stuff.  they run fine on my rigg.  I did notice I removed the tick on the workaround under compiz config manager.  I found that having it checked on caused problems for me.  Also, my pc is perty fast so I don't know if performance is an issue here.

I did not set up scripts for these games btw.

---

