---
title: "Getting Player Stage running"
date: 2008-10-02
forum: General Help
---

### Post by mmmFiesty on 2008-10-02
Hi, I am taking a robotics class this semester and we are using player stage. ([http://playerstage.sourceforge.net](http://playerstage.sourceforge.net)) I was trying to get this running on my ubuntu box and was having some problems with the install.  If anyone can let me know what I did wrong I'd appreciate it!

I found the following which is supposed to be an install guide for a slightly older version of ubuntu and Player / Stage.

[http://www.control.aau.dk/~ms/playerstage/playerstage_install](http://www.control.aau.dk/~ms/playerstage/playerstage_install)

I changed it slightly, there is now player 2.1.1 and stage 2.1.0, and updated the couple places the numbers appear.  I installed it as root - 'sudo su'

I wound up running this line by line. Early on there is a link trying to install all dependencies - it wasn't working so I installed them all one by one.  A couple of them were newer versions and 1 or two didn't install, but suggested a different file which usually was the next in the list so I just kept going.

It took a while to make / make install, but as far as I know it went OK.

Ran
```
#Setting the path be appending to .bashrc
echo "" >> ~/.bashrc 
echo "export PATH=\"\$PATH:/home/$USER/playerstage/bin\"" >> ~/.bashrc 
echo "export PLAYERPATH=\"\$PATH:/home/$USER/playerstage/share/stage/worlds\"" >> ~/.bashrc

source ~/.bashrc

```

and there was no output so I assume it was ok.

This didn't work though
#Checking if the colour description file is at the right place
```
if [ -f /usr/X11R6/lib/X11/rgb.txt ];
then
echo 
else
    echo "/usr/X11R6/lib/X11/rgb.txt does not exist - creating a symbolic link"
sudo ln -s /usr/lib/X11/rgb.txt /usr/X11R6/lib/X11/rgb.txt
fi


/usr/X11R6/lib/X11/rgb.txt does not exist - creating a symbolic link
ln: creating symbolic link `/usr/X11R6/lib/X11/rgb.txt': No such file or directory
```


I looked for this directory, but /usr/X11R6/lib/fglrx/ was a close as I could find with nothing in it.


Tried to just continue on and eventually there were 2 tests, the first one had errors and the second seemed to work. 

The failure:
```
:/home/root# player playerstage/share/stage/worlds/simple.cfg 
Registering driver
Player v.2.1.1

* Part of the Player/Stage/Gazebo Project [http://playerstage.sourceforge.net].
* Copyright (C) 2000 - 2006 Brian Gerkey, Richard Vaughan, Andrew Howard,
* Nate Koenig, and contributors. Released under the GNU General Public License.
* Player comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
* are welcome to redistribute it under certain conditions; see COPYING
* for details.

error   : Sorry, no support for shared libraries, so can't load plugins.
error   : You should install libltdl, which is part of GNU libtool, then re-compile player.
error   : failed to load plugin: libstageplugin
error   : failed to parse config file playerstage/share/stage/worlds/simple.cfg driver blocks
```

I assumed the following line
playerstage/share/player/examples/libplayerc++/./laserobstacleavoid
Failed since stage wasn't started yet anyways.

On the other hand the alternative test did work
```
:/home/root# stest playerstage/share/stage/worlds/simple.world robot1
```


Any suggestions on what I should install at this point?  I have libtool installed, but don't know what the libltdl wasn't part of it.

Thanks!

---

### Post by strupet on 2008-11-13
Hei!

If you didn't find an answer until now:
I'm in a robot course too (TU Vienna) and had to struggle with player-stage and the rgb problem. Here is what worked for me:
inspired by this link:
[http://osdir.com/ml/network.instant-messaging.amsn.devel/2006-03/msg00071.html](http://osdir.com/ml/network.instant-messaging.amsn.devel/2006-03/msg00071.html)

i downloaded the rgb.txt file from here:
[http://www.google.at/url?sa=t&source=web&ct=res&cd=5&url=http%3A%2F%2Fwww.iam.uni-bonn.de%2F~alt%2Flatex%2Frgb.txt&ei=8OEbSbqwMYie1waK5tCEDA&usg=AFQjCNGbF4Hh13LeWD_2xvpUle8pUUYG_A&sig2=cniKZ3qaUicdw6Fz-eYyNg](http://www.google.at/url?sa=t&source=web&ct=res&cd=5&url=http%3A%2F%2Fwww.iam.uni-bonn.de%2F~alt%2Flatex%2Frgb.txt&ei=8OEbSbqwMYie1waK5tCEDA&usg=AFQjCNGbF4Hh13LeWD_2xvpUle8pUUYG_A&sig2=cniKZ3qaUicdw6Fz-eYyNg)

and saved it here: /usr/share/X11/rgb.txt (i think it should be here in ubuntu)

then i linked it with: sudo ln -s -f /usr/X11R6...(see stage errormsg) /usr/share/X11/rgb.txt

Greetings from Vienna!

ßeta

---

