---
title: "Trying to compile sharpconstruct"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by zippyties on 2009-07-28
I am having a hard time installing Sharpconstruct. 

So far I have:
1) extracted the zipped up information to a folder called usr/local /sharpconstruct.

2)run "Configure"

the 3rd step is giving me trouble when i run "make" it works on it for about 3 minutes then returns an error

```
then mv -f ".deps/Scale.Tpo" ".deps/Scale.Po"; else rm -f ".deps/Scale.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I/usr/local/src/sharpconstruct-0.12/src -I../config -I../include -DDATADIR=\"/usr/local/share\"   -Wall -D_REENTRANT -I/usr/include/libglademm-2.4 -I/usr/lib/libglademm-2.4/include -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/libglade-2.0 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/cairomm-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/atk-1.0 -I/usr/include/libxml2   -D_REENTRANT -I/usr/include/gtkglextmm-1.2 -I/usr/lib/gtkglextmm-1.2/include -I/usr/include/gtkglext-1.0 -I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/lib/gtkglext-1.0/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/cairomm-1.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/atk-1.0 -I/usr/include/giomm-2.4 -I/usr/lib/giomm-2.4/include -I/usr/include/atkmm-1.6    -DENABLE_BINRELOC  -O3 -g -MT Shaders.o -MD -MP -MF ".deps/Shaders.Tpo" -c -o Shaders.o Shaders.cc; \
	then mv -f ".deps/Shaders.Tpo" ".deps/Shaders.Po"; else rm -f ".deps/Shaders.Tpo"; exit 1; fi
In file included from Shaders.cc:19:
../include/DataDir.hh: In function ‘Glib::ustring SharpConstruct::DataDir(const Glib::ustring&)’:
../include/DataDir.hh:47: error: ‘free’ was not declared in this scope
make[1]: *** [Shaders.o] Error 1
make[1]: Leaving directory `/usr/local/src/sharpconstruct-0.12/src'
make: *** [all-recursive] Error 1
####@###:/usr/local/src/sharpconstruct-0.12$ 

```

This is the first program that I have tried to compile from source, but I am guessing that I am missing one of the prerequisites.

any help would be appreciated,

thanks,

---

### Post by srilyk on 2009-08-11
I came across the same problem... I'll be looking around for solutions, I'm sure

---

### Post by mc4man on 2009-08-11
> /DataDir.hh:47: error:

That appears to be a c++ (g++) error
So assuming your using jaunty or intrepid try using an earilier compiler. You can install different versions of gcc and g++ than your system default and use from a ./configure

Either search synaptic for gcc-4.2 and g++-4.2 or this should do (i'm on hardy so already have

```
sudo apt-get install g++-4.2 gcc-4.2
```

Then cd to your source, run this (or use a fresh source instead
```
make distclean
```

Then use this configure and see if any joy there for the make
```
CC=gcc-4.2 CXX=g++-4.2 ./configure

```

If still a no go post the configure output

---

