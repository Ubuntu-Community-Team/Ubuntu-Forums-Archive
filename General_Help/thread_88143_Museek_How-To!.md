---
title: "Museek How-To?!"
date: 2005-11-09
forum: General Help
---

### Post by Mosey on 2005-11-09
Could someone please either post a quick Museek install walk-thru on Ubuntu or give me a link to one that someone with minor knowledge could easily follow.

Thanks in advance. I've been trying to get this program running all morning.

---

### Post by Mosey on 2005-11-09
There have been a few requests for Museek install help, but no one ever answers. Nicotine is quickly becoming less and less functional.

---

### Post by Mosey on 2005-11-09
Suppose I'll keep answering my own posts here...

I 'cd' to the directory where I upacked the tarball file for the Museek app.

Then I ran python scons/scons.py

It went thru some kind of system check or something then gave me an error:

"Package vorbisfile was not found in the pkg-config search path.
Perhaps you should add the directory containing `vorbisfile.pc'
to the PKG_CONFIG_PATH environment variable
No package 'vorbisfile' found
Checking for ov_clear(0) in C++ library ... no
Checking for C++ header file qapplication.h... no

Couldn't find Qt. Make sure the QTDIR environment variable is set, or
disable building of the Qt client by adding MUSEEQ=0 to the scons
commandline."

So I added python scons/scons.py MUSEEQ=0

I went thru pages and pages of things I didn't understand...though this line kept appearing:

"./Muhelp/Mulog.hh:28: warning: 'class MulogSink' has virtual functions but non-virtual destructor
./Muhelp/Mulog.hh:33: warning: 'class MulogConsole' has virtual functions but non-virtual destructor"

It looked like it was on some kind of loop for at least ten minutes then it told me:

"scons: done building targets."

So I used killall gnome-panel to see If there'd be an icon in my Internet folder. No luck. So I searched the folder to try and find some way to start it up. I didn't. I'm quite frustrated. :mad:

---

### Post by bionnaki on 2005-11-09
[QUOTE=Mosey]There have been a few requests for Museek install help, but no one ever answers. Nicotine is quickly becoming less and less functional.[/QUOTE]

you think?
what version are you running?
I am on 1.0.8 & it runs well
(not as well as the win32 slsk client
but good enough).

I do hope there are updates
either to nicotine or other linux clients
as the official clients are moving forward.
I wish soulseeX could work in linux...

is museeek the most up-to-date?

---

### Post by Mosey on 2005-11-09
Nicotine is no longer being developed. The guy who was working on the project moved to the Museek team or something.

Nicotine has given me nothing but grief. The Soulseek team upgraded some key elements to searching a while back....

I NEED MUSEEK! I NEED HELP!

---

### Post by bionnaki on 2005-11-09
have you tried the forums?
[http://forums.slsknet.org/ipb/index.php?showforum=38](http://forums.slsknet.org/ipb/index.php?showforum=38)

---

### Post by ivanhelguera on 2005-11-10
[QUOTE=bionnaki]have you tried the forums?
[http://forums.slsknet.org/ipb/index.php?showforum=38](http://forums.slsknet.org/ipb/index.php?showforum=38)[/QUOTE]
This is OK
BUT!!!!!!
You need to set env variables differently: 
```
export QTDIR=/usr/share/qt3
export QT_LIB=qt-mt
```
otherwise it wo't be able to find qt
I'll try to prepare more exhaustive info, but that worked for me
BAsically, i just applied the info from debian section of museek site: 
[http://thegraveyard.org/daelstorm/museekfaq.php#q3]("http://thegraveyard.org/daelstorm/museekfaq.php#q3")
Best, 
IH

---

