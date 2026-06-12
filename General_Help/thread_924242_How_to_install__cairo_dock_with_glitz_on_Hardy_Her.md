---
title: "How to install  cairo dock with glitz on Hardy Heron"
date: 2008-09-19
forum: General Help
---

### Post by miousername on 2008-09-19
I've found a workaround to install cairo-dock with glitz on hardy: i've installed the right library (gusty libcairo2) on /usr/local with this procedure: (it's an old solution found by cairo-dock team not to overwrite system library but i modified it because it didn't work) :

1.Download libcairo-1.4.10 (libcairo 2 gusty), glitz-0.5.6 (glitz gusty), pixman-0.9.4 (pixman gusty) and pixman-0.10.0 (pixman Hardy);

2. Now
$ cd ~/pixman-0.9.4
$ ./configure --prefix=/usr/local && make
$ sudo make install

$ cd ~/pixman-0.10.0
$ ./configure --prefix=/usr && make
$ sudo make install

3. $ cd ~/glitz-0.5.6
$ ./configure --prefix=/usr/local && make
$ sudo make install

4. $ cd ~/libcairo-1.4.10
$ ./configure --prefix=/usr/local --enable-glitz --enable-directfb && make clean && make
$ sudo make install


5.Now open an other terminal and type:
$ export LD_LIBRARY_PATH=/usr/local/lib:${LD_LIBRARY_PATH}
$ export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:${PKG_CONFIG_PATH}


6. $ cd ~/cairo-dock-<last-release>
$ ./configure --prefix=/usr --enable-glitz && make clean && make
$ sudo make install

$ cd ~/cairo-dock-plugins-<last-release>
$ ./configure --prefix=/usr --enable-glitz && make clean && make
$ sudo make install

$ cd ~/cairo-dock-themes-<last-release>
$ ./configure --prefix=/usr && make clean && make
$ sudo make install

IMPORTANT: you have to do the operations 6 in same console you put the commands at passage 5.

7.Now create a file called "start-dock.sh", copy and paste this script into the file:


#!/bin/sh
export LD_LIBRARY_PATH=/usr/local/lib:${LD_LIBRARY_PATH}
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:${PKG_CONFIG_PATH}
DELAY=${1:-30} #wait 30 seconds
echo starting cairo-dock in $DELAY seconds.
(nohup sleep $DELAY>/dev/null; cairo-dock -g>~/.cairo-dock.log 2>&1) &

8. Make it executable with $ sudo chmod a+x ~/start-dock.sh
9. Move with $ sudo mv ~/start-dock.sh /usr/local/bin/
10. Add in gnome-session-properties commands: start-dock.sh 12
Log out, log in and enjoy ^_^

---

### Post by nkri on 2008-09-19
This is good, but in my opinion it is much easier to just add the repo in synaptic and download from there.  Much faster than compiling.  For more information: _[https://help.ubuntu.com/community/CairoDock]("https://help.ubuntu.com/community/CairoDock")_

---

### Post by miousername on 2008-09-20
Ok, but if you download cairo-dock from repo in synaptic  (.deb package) you can't recompile the dock!!In hardy heron you can't use glitz because licairo2 in hardy broke the compatibility with glitz!!!

---

### Post by fabounet on 2008-09-20
you're right, but the method to fix it is a bit more complicated ^_^
on [the cairo-dock forum]("http://www.cairo-dock.org/bg_forumlist.php") you should find the way to do it (needs glitz 0.5.7, the post is in english if I remember well)
it's not perfect yet, but better than nothing.

---

### Post by miousername on 2008-09-22
I tried to follow the wiki on cairo-dock forum but my ubuntu crashed because if you install the library glitz, libcairo and pixman with: 
$ export LD_LIBRARY_PATH=/usr/local/lib:${LD_LIBRARY_PATH}
$ export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:${PKG_CONFIG_PATH}
the system uses the new library cairo you install in /usr/local/lib and forgets the right library of the system (libaciro-1.6.0, ecc..) installed in /usr/lib

... so i modified the wiki and now cairo-dock works with glitz in my ubuntu hardy heron...
if you try to install 0001-Fix-glitz-support-for-24.8-fixed-point.patch and glitz 0.5.7 cairo-dock doesn't work correctly (you can't see the reflection of the icon ), i've just tried it before.

In my ubuntu it works well but thank you for the answers.

---

### Post by hihihi on 2008-11-28
blablabla, at the end your suggestion is the best, compile all with glitz, the repo stuff does not help.
glitz makes wonders, the rest is boring.
thx for your post.

---

### Post by hihihi on 2008-11-29
what we need is a libcairo2 pkg with glitz enabled

---

### Post by miousername on 2008-12-04
Yes, what we need is only a libcairo2 pkg with glitz enabled, it's true.
If you wants you can try to install glitz-0.5.7 and pixman-0.12.0 instead of glitz-0.5.6 and pixman-0.10.0, in my opinion cairo-dock is faster than the solution with glitz-0.5.6 and pixman-0.10.0.
You can find them here [http://download.tuxfamily.org/ccm/glitz/](http://download.tuxfamily.org/ccm/glitz/)

:)

---

