---
title: "compiling wxGTK-2.4.2 from source"
date: 2008-11-24
forum: General Help
---

### Post by motoperpetuo on 2008-11-24
i'm trying to compile wxGTK-2.4.2 from source. when i run ./configure, i get the following error:

```

checking for GTK - version >= 1.2.3... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: 
Please check that gtk-config is in path, the directory
where GTK+ libraries are installed (returned by
'gtk-config --libs' command) is in LD_LIBRARY_PATH or
equivalent variable and GTK+ is version 1.2.3 or above.

```

i tried going into synaptic and installing every package that mentions GTK that looked like it might be relevant, but that shot in the dark didn't work. i'm guessing i just need to install something (since there currently is no file called gtk-config on my computer) and maybe adjust the environment variables mentioned in the error. i'd greatly appreciate any advice.

---

### Post by taurus on 2008-11-24
You need the -dev (developing package) as well, not just the library.

---

### Post by houbysoft.xf.cz on 2008-11-24
See if you have gtk-config but it isn't in your path:
```

which gtk-config

```. If it returns something then add its dir to your path or just do a
```

sudo apt-get install gtk-dev

``` or something like that, just UTFG.

---

### Post by mc4man on 2008-11-24
Many times when you get an error in a configure or make you need to put lib in front of whats shown.
In this case probably libwxgtk2.4-dev

(or any available libwxgtk-dev may do the trick, you didn't mention what version of ubuntu your using

---

### Post by motoperpetuo on 2008-11-25
> **houbysoft.xf.cz said:**
> See if you have gtk-config but it isn't in your path:
```

which gtk-config

```. If it returns something then add its dir to your path or just do a
```

sudo apt-get install gtk-dev

``` or something like that, just UTFG.

```

which gtk-config

```

doesn't return anything, so i guess i don't have gtk-config.

```

sudo apt-get install gtk-dev

```

generates an error ("Couldn't find package gtk-dev"). i also tried 
```

sudo apt-get install libwxgtk2.4-dev

```
which seems to have installed something, but i still get my original error when i try to run ./configure.

i'm trying to do this to learn how to install software from source. actually, wxwidgets 2.4 is required for the tutorial for installing audacity from source at [http://www.linuxformat.co.uk/wiki/index.php/Compiling_Made_Easy](http://www.linuxformat.co.uk/wiki/index.php/Compiling_Made_Easy), but 2.4 doesn't seem to be available in the ubuntu repositories anymore, hence my trying to install it from source.

this is probably still all a bit above my head. i'll do some more figuring later. i really appreciate all of you who posted trying to help.

---

### Post by specvthis on 2008-11-25
I would first see what packages you have access too.

sudo apt-cache search wxgtk

then if you want to build your own packages you can grab all dependencies by running

sudo apt-get build-dep libwxgtk2.4 

just replace libwxgtk2.4 from the right package that you saw in the return from the first statement.

---

### Post by mc4man on 2008-11-25
If your using 8.04 or 8.10 libwxgtk-2.4 isn't used though you can install the -dev.

If you want to try to build 1.2.6 you will want to start here.
Note that i need to build a few things tommorrow so I'm not going to fool around till they're done.

In terminal

```
doug@doug-desktop:~$ sudo update-alternatives --config wx-config

There are 5 alternatives which provide `wx-config'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/wx/config/base-unicode-release-2.6
          2    /usr/lib/wx/config/gtk2-unicode-release-2.6
          3    /usr/lib/wx/config/base-unicode-release-2.8
*+        4    /usr/lib/wx/config/gtk2-unicode-release-2.8
          5    /usr/bin/wxgtk-2.4-config

Press enter to keep the default[*], or type selection number: 

```
You'd pick 5 and then your configure will proceed (any other errors will be due to other missing deps. (tested here and  default configure went fine

Edit: if you don't have 5 choices the # doesn't matter, just choose "/usr/bin/wxgtk-2.4-config'

don't forget to change back to build more recent sources

A note on the configure
you may want to consider adding at least this to your ./configure

--with-portaudio=v19
otherwise I believe there will be no alsa support (default is v18 (oss)

---

### Post by mc4man on 2008-11-25
Builds and runs just fine. I used the portaudio=v19.

After running make you can test and or use without installing by running from the build folder prompt,

doug@doug-desktop:~/audacity-src-1.2.6$ ./audacity

---

