---
title: "[SOLVED] Wine and my graphics card"
date: 2008-11-25
forum: General Help
---

### Post by porchrat on 2008-11-25
Hi all I am looking for some information.

I'm thinking of removing XP from the last machine that I work with.  Dual booting isn't really desired, what I really want is to never have to look at a Microsoft product for a long time.

The only real thing standing in my way is that I do occasionally play some games (Warcraft3 and a few others), but nothing cutting edge.  I was wondering how Wine handles Warcraft3 and whether or not it is actually playable.

The second thing that is bothering me is that I have the dreaded ATI Xpress 200M integrated chip in this laptop.  I wanted to know what the drivers are like for this chip, so could anyone with personal experience with the 200M answer the following questions.  Which drivers are the best?  Does it handle compiz?  How is the 3D acceleration..or lack thereof?

Also does video playback have those same problems you get with the newer Catalyst drivers?

If I can think of anything else I'll ask at a later stage.

---

### Post by thereaper243 on 2008-11-25
I don't have very much experience with Ubuntu or Wine yet. On the other hand, I do have some experience with the ATI Xpress 200M onboard graphics system. The newest driver for this card is probably the best I've seen. I haven't used the 200M for gaming in a Linux OS, but I can say that as far as Windows goes, it's easily one of the best Onboard systems ever. I even have a Xpress 200/AMD Sempron system that runs beautifully. I hope that helped a bit.

TheReaper

---

### Post by roshanjose on 2008-11-25
just check this out.......

[http://www.void.gr/kargig/blog/2005/12/10/warcraft-3-on-linux/](http://www.void.gr/kargig/blog/2005/12/10/warcraft-3-on-linux/)



u can play in this way....

or do u have the cd of warcraft3

---

### Post by roshanjose on 2008-11-25
or if you have a Warcraft 3 cd...you can do this:


make sure you install winex


Warcraft 3 will only run with some restrictions. first of all, you will need a noCD-crack, to get the game running. Second point is, that the video intro cannot be displayed by winex, it crashes when it tries to. So we have to move or delete the videofiles, for that they are skipped. You can view them with a video-player, allthough. The important videos of the game are ingame, they are displayed without problems.


_Installation on GNU/Linux_:

The installation basicly works like on windows:

mount /mnt/cdrom

(or wherever your cdrom is mounted at)

cd /mnt/cdrom
wine Install.EXE

Install the game as used to in windows. the error about DirectX 8.1 may be ignored.

If the

"wine Install.EXE"

crashes (just doed 100% CPU usage), please follow the next few steps, if not, you can go straight to "configuration".

First of all, delete the old ~/.wine directory, if one is existent. (Remind to backup your config):

mkdir -p ~/.wine/fake_windows/windows/system

Now copy the example-config (or your backuped one, if existent):

cd 

(e.g. /home/william/wine)

cp ducumentation/samples/config ~./wine

Next step is changing directory to the regapi dir and compiling the program, also generating the registry:

cd programs/regapi
make
./regapi setValue < ../../winedefault.reg

Now, copy the files msvcrt* (whatever after the "t") and regsvr32.exe for a "working" (lol) Windows 98 to ~/.wine/fake_windows/windows/system (now you got the windows registry server, for any reason warcraft needs it;) ). At last you need to edit your ~/.wine/config. The section "[Drive C]" should look like this (just the path is interesting):

[Drive C]
"Path" = "/home/**your username**/.wine/fake_windows"
"Type" = "hd"
"Label" = "Windows"
"Filesystem" = "win95"

Now edit the other drives, so that they fit your configuration.

Next you can install the game with wine Install.EXE.

[U]
Configuration[/U]:

Now, rename the directory "Movies" in your install dir of Warcraft 3 in something like "Movies_old", so the movies cannot be found anymore.


 _Startscript_:

Create a startscript (as root): /usr/bin/war3 :

#!/bin/sh
# edit the next path
pushd /your/wc3/directory
wine -War3.exe -- War3.exe -opengl
popd

Remind to set the "executable" flag on the script:

chmod 755 /usr/bin/war3


The option "-opengl" runs Warcraft3 in opengl mode. Thats much better and faster for most people. If you expire any problems, replace "-opengl" with "-d3d" to use the standart direct3d implementation. You should try both and use that one, that works better.

---

### Post by roshanjose on 2008-11-25
or if you have a Warcraft 3 cd...you can do this:


make sure you install winex


Warcraft 3 will only run with some restrictions. first of all, you will need a noCD-crack, to get the game running. Second point is, that the video intro cannot be displayed by winex, it crashes when it tries to. So we have to move or delete the videofiles, for that they are skipped. You can view them with a video-player, allthough. The important videos of the game are ingame, they are displayed without problems.


_Installation on GNU/Linux_:

The installation basicly works like on windows:

mount /mnt/cdrom

(or wherever your cdrom is mounted at)

cd /mnt/cdrom
wine Install.EXE

Install the game as used to in windows. the error about DirectX 8.1 may be ignored.

If the

"wine Install.EXE"

crashes (just doed 100% CPU usage), please follow the next few steps, if not, you can go straight to "configuration".

First of all, delete the old ~/.wine directory, if one is existent. (Remind to backup your config):

mkdir -p ~/.wine/fake_windows/windows/system

Now copy the example-config (or your backuped one, if existent):

cd 

(e.g. /home/william/wine)

cp ducumentation/samples/config ~./wine

Next step is changing directory to the regapi dir and compiling the program, also generating the registry:

cd programs/regapi
make
./regapi setValue < ../../winedefault.reg

Now, copy the files msvcrt* (whatever after the "t") and regsvr32.exe for a "working" (lol) Windows 98 to ~/.wine/fake_windows/windows/system (now you got the windows registry server, for any reason warcraft needs it;) ). At last you need to edit your ~/.wine/config. The section "[Drive C]" should look like this (just the path is interesting):

[Drive C]
"Path" = "/home/**your username**/.wine/fake_windows"
"Type" = "hd"
"Label" = "Windows"
"Filesystem" = "win95"

Now edit the other drives, so that they fit your configuration.

Next you can install the game with wine Install.EXE.

[U]
Configuration[/U]:

Now, rename the directory "Movies" in your install dir of Warcraft 3 in something like "Movies_old", so the movies cannot be found anymore.


 _Startscript_:

Create a startscript (as root): /usr/bin/war3 :

#!/bin/sh
# edit the next path
pushd /your/wc3/directory
wine -War3.exe -- War3.exe -opengl
popd

Remind to set the "executable" flag on the script:

chmod 755 /usr/bin/war3


The option "-opengl" runs Warcraft3 in opengl mode. Thats much better and faster for most people. If you expire any problems, replace "-opengl" with "-d3d" to use the standart direct3d implementation. You should try both and use that one, that works better.

---

### Post by porchrat on 2008-11-25
> **thereaper243 said:**
> I don't have very much experience with Ubuntu or Wine yet. On the other hand, I do have some experience with the ATI Xpress 200M onboard graphics system. The newest driver for this card is probably the best I've seen. I haven't used the 200M for gaming in a Linux OS, but I can say that as far as Windows goes, it's easily one of the best Onboard systems ever. I even have a Xpress 200/AMD Sempron system that runs beautifully. I hope that helped a bit.

TheReaper

I have had endless trouble with the 200M on windows.  I agree that the new drivers have helped a great deal, but any program that attempts to utilise opengl still underperforms.  I've been using this laptop for around 3 years and basically up until a few months ago I couldn't play opengl games at all, now I can play them, but at nowhere near the level I know that graphics system is capable of.

Directx was great, but opengl was terrible.  I'm really hoping that the Linux drivers don't have these same problems.

> The option "-opengl" runs Warcraft3 in opengl mode. Thats much better and faster for most people. If you expire any problems, replace "-opengl" with "-d3d" to use the standart direct3d implementation. You should try both and use that one, that works better.

I'm glad to hear that warcraft3 will run in Wine, because realistically it is one of the few games I play.  Luckily that seems like a pretty simple install and I can easily live without the movies.  I won't even need to worry about the CD as the new Warcraft3 updates from Blizzard no longer require that you use a CD with the game.  How does it handle networking?  (Bearing in mind that I've never used Wine either)

So basically I think all I need to discover now is whether or not my 200M will handle the 3D acceleration (I'll probably try it out with those new catalyst drivers as reaper suggested as they did make a big improvement on the opengl side in windows)

Thanks a lot everyone.

---

