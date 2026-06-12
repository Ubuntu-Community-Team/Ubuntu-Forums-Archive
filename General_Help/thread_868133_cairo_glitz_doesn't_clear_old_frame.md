---
title: "cairo glitz doesn't clear old frame"
date: 2008-07-23
forum: General Help
---

### Post by miousername on 2008-07-23
Hi,
i try to launch cairo-dock on ubuntu hardy-hoary with libcairo2 recompiled with glitz but it worked like in figure.
It seems that cairo doesn't clear old frame.
On gusty it worked and if i replace libcairo.so.2.17.3 on /usr/lib with libcairo.so.2.11.5 (libcairo2 on gusty) and link with libcairo.so.2 it worked perfectly but... it's no a very good solution!
Thanks soooo much!!

image
[http://img78.imageshack.us/my.php?image=glitzcairovc3.png](http://img78.imageshack.us/my.php?image=glitzcairovc3.png)

---

### Post by fabounet on 2008-07-24
recent libcairo version broke the compatibility with glitz.
there is a patch to apply to libcairo, and a new version of glitz to use (0.5.7), made by the dev of cairocompmgr.

---

### Post by miousername on 2008-07-26
Thank you very much for the answer! :)
I've downloaded  glitz-0.5.7 and patch my libcairo2 with "0001-cairo-1.6-Fix-glitz-support-for-24.8-fixed-point.patch" made by cairocompmgr team.
Now glitz works and frames show correctly but reflection on cairo-dock don't appear and the text above icons is unreadble..
I've also installed new pixman-0.11.8 but nothing..
:-kI'll continue to use the stupid trick i said above to show correctly the dock .. ](*,)
Thank you so much for your help!

---

### Post by miousername on 2008-07-31
I've found a workaround: i've installed the right library (gusty libcairo2) on /usr/local with this procedure: (it's an hold solution found by cairo-dock team to not overwrite system library but i modified it because didn't work) :

1.Download libcairo-1.4.10 (libcairo 2 gusty), glitz-0.5.6 (glitz gusty), pixman-0.9.4 (pixman gusty);

2. Now 
$ cd ~/pixman-0.9.4
$ ./configure --prefix=/usr/local && make
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
(nohup sleep $DELAY>/dev/null;    cairo-dock -g>~/.cairo-dock.log 2>&1) &

8. Make it executable with $ sudo chmod a+x ~/start-dock.sh
9. Move with $ sudo mv ~/start-dock.sh /usr/local/bin/
10. Add in gnome-session-properties  commands: start-dock.sh 12
----------------------------------------------------------------------------------------
N.B.If your ubuntu doesn't restart download pixman-0.10.0.tar.gz(pixman for HARDY) exctract and compile with:
$ ./configure --prefix=/usr && make
and install with:
$ sudo make install
without remove the old pixman installed before.
----------------------------------------------------------------------------------
Log out, log in and enjoy ^_^

---

