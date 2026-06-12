---
title: "How do I get qt4 running especially qmake"
date: 2008-08-08
forum: General Help
---

### Post by harryliddic on 2008-08-08
I need to have **qt4** running and **qmake** to be configured into the **/bin** file. I am compiling Qdvdauthor 1.5.0 and I hang very time qmake is not in the /bin file. I downloaded qt3 and qt4 and the libs from the repos but that alone doesn't do it.

---

### Post by mc4man on 2008-08-08
i'll try building later but a .deb for hardy is available here
[http://www.getdeb.net/app/QDVDAuthor](http://www.getdeb.net/app/QDVDAuthor)

Edit: do you have libqt4-dev installed?

Re edit; didn't have any issues w/ build, can't say what difference is, have alot of libs, -devs installed.

---

### Post by harryliddic on 2008-08-08
yes I have libqt4-dev installed but it seems to have a bunch of qmake.conf files in the /usr/share/ directory. I will try the link you so gratefully provided Hoping it is version 1.5.0 which if it is for hardy it should be.

---

### Post by mc4man on 2008-08-09
I'm gathering the.deb was alright. As it happens another ? came up last night about qrender which is part of the source package but not included in the.deb. 
If you find you want it a solution is here (compiles with qt4.x)
I tend to think you could just build and install qrender and it would work with the Qdvdauthor 1.5.0 installed by .deb (don't know for sure

[http://ubuntuforums.org/showthread.php?p=5552449#post5552449](http://ubuntuforums.org/showthread.php?p=5552449#post5552449)

---

### Post by harryliddic on 2008-08-10
In the compile I am running into the error > simpledvd.cpp:20:26: error: ../../CONFIG.h: No such file or directory
make: *** [.obj/simpledvd.o] Error 1
g++ -c -pipe -Wall -W -O2 -D_REENTRANT -fPIC  -DPLUGIN_VERSION=1.2 -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/simpledvd.o simpledvd.cpp
simpledvd.cpp:29:26: error: ../../CONFIG.h: No such file or directory
make: *** [.obj/simpledvd.o] Error 1
g++ -c -pipe -Wall -W -g -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/menuslide.o menuslide.cpp
menuslide.cpp:18:50: error: ../../CONFIG.h: No such file or directory
menuslide.cpp: In member function &#8216;void Plugin::MenuSlide::loadBackgroundImage()&#8217;:
menuslide.cpp:84: error: &#8216;PREFIX_DIRECTORY&#8217; was not declared in this scope
menuslide.cpp:84: error: expected &#8216;,&#8217; or &#8216;;&#8217; before string constant
menuslide.cpp: In member function &#8216;QString Plugin::MenuSlide::getMenuXml()&#8217;:
menuslide.cpp:438: error: expected `)' before &#8216;PREFIX_DIRECTORY&#8217;
make: *** [.obj/menuslide.o] Error 1
make: Nothing to be done for `first'.
harry@harry-desktop:~/qdvdauthor-1.5.0/qdvdauthor/plugins$ 

 Should I declare it first? The file simpledvd is there and simpledvd.cpp is in it. the deb version gives of a "dpkg error- conflict with qdvdauthor-akirad"

---

### Post by KoolPenguin on 2008-08-10
The QDVDAuthor package at getdeb is missing qrender, but the simple way to do this would be to get the package from getdeb, install it and then compile qrender from source.  I had problems compiling qrender do to the script included for ffmpeg.  See this post to get qrender to installed correctly:

 [http://ubuntuforums.org/showpost.php?p=5552449&postcount=5]("http://ubuntuforums.org/showpost.php?p=5552449&postcount=5")

If you need more help just let us no...

---

### Post by harryliddic on 2008-08-10
the debian package will not compile after twenty odd tries. I keep getting a **dpkg** error saying that there are conflicting versions. I'm half way through the compile of version 1.5.0.2 with qrender in it. I'm zero the way with the getdeb package. I don't know which way to turn. Is there another linux dvd authoring system I can use? My project is due tomorrow and all I have are 40 avi files gathering dust.

---

### Post by MaindotC on 2008-08-10
It sounds to me like you have packages from an older version of Ubuntu installed, and apt will not auto-fix these.  Take [this thread]("http://ubuntuforums.org/showthread.php?t=804294") for example.  You can use the aptitude command to resolve them.  Try:
```

sudo aptitude install <packagename1> <packagename2>

```

where packagename 1 and 2 are packages you installed via the repositories to begin the installation of qmake.  It may even resolve by just doing:
```

sudo aptitude update && sudo aptitude upgrade

```

---

### Post by mc4man on 2008-08-10
I'm not sure what you've been doing but anyway it doesn't sound like you need qrender so for the moment forget compiling the source. You may not even need the latest ver. of qdvdvdauthor.

Try what strAlan mentioned , if no go  do this 
```
sudo aptitude purge ffmpeg dvdauthor qdvdauthor
``` followed by
```
sudo aptitude install ffmpeg dvdauthor qdvdauthor
```

If the first comm. produces any errors, post or try opening synaptic and 'fix broken packages' if any are shown.

After running the 2nd command you'll have the hardy ver. of qdvdauthor, you can if you wish then install ver. 1.5 from the getdeb. (just d. click on and let gdebi handle)

---

### Post by harryliddic on 2008-08-10
Thank you that sounds like it will work and I will try it after I figure out how to get back into linux without losing my avi files.

---

### Post by KoolPenguin on 2008-08-11
> **harryliddic said:**
> Thank you that sounds like it will work and I will try it after I figure out how to get back into linux without losing my avi files.

What's up with not getting back into linux?  If for some reason ubuntu won't boot up you can use the live cd to fix the problems or at least use it to recover your avi files.

Also, it looks like the QDVDAuthor package at getdeb.net now includes qrender with it.  Haven't tried it, but it has qrender in the deb package.

---

