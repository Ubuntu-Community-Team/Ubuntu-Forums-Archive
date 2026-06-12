---
title: "opening an app in a new xserver (xinit)"
date: 2008-08-28
forum: General Help
---

### Post by amirman on 2008-08-28
i've been trying to use xinit to open an application on a separate xserver that i could access with ctrl+alt+f8 but i run into some errors

> amir@amir-laptop:~$ xinit -- /usr/bin/sauerbraten-client  :1

init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: ATI Mobility Radeon X1400 (ATI Technologies Inc.)
Driver: 2.1.7412 Release
WARNING: Non-power-of-two textures not supported!
Rendering using the OpenGL 1.5 GLSL shader path.
init: console
init: gl: effects
init: world
init: sound
init: cfg
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.1 seconds)
Mining Station by metlslime

waiting for X server to begin accepting connections .
..
..
..
..
..
..
..game mode is ffa/default

.
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.


i'm thinking that it might have something to do something i discovered a few weeks ago, the authorization for x is different on ubuntu, the xauth file is created at boot and stored in /tmp so scripting something with xauth is impossible since the key or whatever is changed at each boot, i've thought about using sudo to run the xinit command but security seems to be an issue with opening a game that connects to the internet as root.

what should i do? what are my options?

---

### Post by lswb on 2008-08-28
I think the command line should be:

xinit /usr/bin/sauerbraten-client -- :1

Also if your are running ubuntu/gnome you could consider opening 
Main Menu/System/Administration/Login Window/General and uncheck the option 
"Disable multiple logins for single user" This will let you login to a separate session with the full DTE running.

---

### Post by amirman on 2008-08-28
you're right about that command but still...
it says that i'm not authorized to open a new x server
and i get the same errors..

---

### Post by lswb on 2008-08-28
Are you trying to run the command from a terminal window in a running xserver? If so, try opening a vt and running it from there. ( ctrl-alt-f1, then login, then run your command)

---

### Post by amirman on 2008-08-29
well i found another way that doesn't involve xinit.
i first used

sudo X -ac :1

which worked great

then...

DISPLAY=:1 /usr/bin/sauerbraten-client

at that point the screen went black and i could do anything, i tried ctrl+alt+f1 all the way to f9 and ctrl+alt+bkspc and i got nothing, the screen stayed black. there are many mysteries here. someone has to know what's going on.

---

