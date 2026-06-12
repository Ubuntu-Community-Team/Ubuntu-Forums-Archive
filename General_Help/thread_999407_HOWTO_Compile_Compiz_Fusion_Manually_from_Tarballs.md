---
title: "HOWTO: Compile Compiz Fusion Manually from Tarballs"
date: 2008-12-01
forum: General Help
---

### Post by collinp on 2008-12-01
[B]WARNING: These are packages direct from the Compiz Fusion website and are not from the Ubuntu repositories. They are not officially supported by Ubuntu.

What is Compiz Fusion?[/B]
Compiz Fusion is a OpenGL accelerated window manager that provides impressive effects for your eye candy pleasure. Compiz Fusion is free and open source, and it is free to distribute under the GNU General Public License (the license in full is [here]("http://www.gnu.org/copyleft/gpl.html")).

**What is "compiling"**
Compiling is the building of a program from its base files, which we call source code. All open-source programs make their source code freely availble for anyone to edit and distribute, under their relevant license. Generally a program is compiled with the Gnu Compiler Collection, or better known as the gcc. If you do not have that already installed, it will be installed for you in this tutorial.

[B]What is required for this tutorial:

[LIST]
[*]A working graphics card, preferably with at least or more than 32MBs of ram and with the correct drivers for your graphics card ([Envy](http://www.albertomilone.com/nvidia_scripts1.html) is a very good script for getting drivers for your graphics card)
[/LIST]
[/B]
The dependencies you will need, along with the command to install them, is listed below:
```
build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev python-dev python-pyrex libjpeg62-dev
```Start by running the following commands inside terminal (Applications - Accessories - Terminal):
```
cd ~/
mkdir compiz-compile
cd compiz-compile
```The first command ensures that you are in your home directory, where compiz will be compiled from. The second command created the directory "compiz-git", where the files we will compile will reside. The third command navigates into that directory. Now, to get the packages you will need for Compiz Fusion, go here and download any packages ending with "0.7.8.tar.gz": [http://releases.compiz-fusion.org/0.7.8/](http://releases.compiz-fusion.org/0.7.8/)
After you are finished with that, go here and download the file named "[COLOR=Black][compiz-0.7.8.tar.gz]("http://releases.compiz-fusion.org/compiz/0.7.8/compiz-0.7.8.tar.gz")[/COLOR]": [http://releases.compiz-fusion.org/compiz/0.7.8/](http://releases.compiz-fusion.org/compiz/0.7.8/)
Once you are finished, extract the source tarballs (enter your home directory, then enter compiz-compile, then right click and click "Extract Here" on each of the packages).
After your are finished with that, compile each of the packages with "./configure && make && sudo make install" **IN THIS ORDER:**

[LIST]
[*]compiz
[*]bcop
[*]libcompizconfig
[*]compizconfig-python
[*]ccsm
[*]compiz-fusion-plugins-main
[*]everything else
[/LIST]
And that is it! You now have a working install of Compiz Fusion, compiled by yourself! To run compiz fusion, go to Applications - System - Preferences - Appearance, then click on the "Visual Effects" tab, then select the level of eye candy you want. To change settings for compiz, go to Applications - System - Prefernces - CompizConfig Settings Manager.

**Troubleshooting**
**Q:** I get a error containing the word "blacklist". What should I do?
**A:** Please see this thread: [Blacklisted?](http://ubuntuforums.org/showthread.php?t=765875)

I hope this tutorial was a great help to you, and if you have any questions feel free to post them.

Tutorial Sources:
[The Compiz Fuson Wiki]("http://wiki.compiz-fusion.org/")

---

### Post by loomsen on 2008-12-02
Yah, well, but... actually... why? There are a lot of scripts out there doing exactly the same. And there are a couple of really good scripts, like omegas script for instance, which are always on the bleeding edge. 

Just updated my compile yesterday with omegas script, and again a couple of patches/new plugins have been added.
The actual build still happens on your PC, so what I wonder, do you see any further advantages I might not think of?

Did you install protobuf? 0.7.8 however is the same version available through the ubuntu-repos for quite some time now, so, thinking of the advantages of self-compiled packages it would probably be even more of an advantage (not to mention the ease of issuing one command) if one would use apt-build to get compiz sources and build them. 
Further, using this method, the pkges would even be apt-handled.
This, however, is the only reason I can make up why I would want to build them manually. To issue some more appropriate commands than make && make install, and finally get *.deb pkges and deb-srces out of the source code.

instead of 
./configure && make && make install
one could use 
**./configure && dh_make --createorig** to create debian sourcepkges from the code, and finally issue
**dpkg-buildpackage** to have a *.deb as well.

This would make sense imho, thinkin of applying patches in the future or so. But just building to build? I don't quite get that.

Don't get me wrong, no offense, I'm just wondering if I miss sth.

---

### Post by collinp on 2008-12-02
> **loomsen said:**
> Yah, well, but... actually... why? There are a lot of scripts out there doing exactly the same. And there are a couple of really good scripts, like omegas script for instance, which are always on the bleeding edge. 

Just updated my compile yesterday with omegas script, and again a couple of patches/new plugins have been added.
The actual build still happens on your PC, so what I wonder, do you see any further advantages I might not think of?

Did you install protobuf? 0.7.8 however is the same version available through the ubuntu-repos for quite some time now, so, thinking of the advantages of self-compiled packages it would probably be even more of an advantage (not to mention the ease of issuing one command) if one would use apt-build to get compiz sources and build them. 
Further, using this method, the pkges would even be apt-handled.
This, however, is the only reason I can make up why I would want to build them manually. To issue some more appropriate commands than make && make install, and finally get *.deb pkges and deb-srces out of the source code.

instead of 
./configure && make && make install
one could use 
**./configure && dh_make --createorig** to create debian sourcepkges from the code, and finally issue
**dpkg-buildpackage** to have a *.deb as well.

This would make sense imho, thinkin of applying patches in the future or so. But just building to build? I don't quite get that.

Don't get me wrong, no offense, I'm just wondering if I miss sth.

Compiling often gets you a more updated version than is in the repos, and it sometimes gives you features that are not yet in the version in the repos. Plus, compiling can sometimes give a small performance boost, and the install is built specifically for your system, not for someone else's.

---

### Post by loomsen on 2008-12-02
Well, actually I'm aware of these facts, and I didn't compare it to the repos anyway. I meant the scripts to get git-compiz installed. Omegas script for instance is maintained as well as possible for instance, pulling all (including the more recent plugins like putplus, unofficial-ccsm-icons, newton PLUS adding a nice option to add custom patches.)

Maybe you want to give it a try... Could save you a lot of time imho, I think I don't have to mention that compiling is still done by your machine (apt-build actually is an apt-tool to get src packages and rebuild them optimized for your architecture (core 2 duo) for instance. Hence, this offers even more optimizations than a manual compile, as the packages are compiled for generic amd64 rather than my intel core 2 duo...)

---

### Post by collinp on 2008-12-02
> **loomsen said:**
> Well, actually I'm aware of these facts, and I didn't compare it to the repos anyway. I meant the scripts to get git-compiz installed. Omegas script for instance is maintained as well as possible for instance, pulling all (including the more recent plugins like putplus, unofficial-ccsm-icons, newton PLUS adding a nice option to add custom patches.)

Maybe you want to give it a try... Could save you a lot of time imho, I think I don't have to mention that compiling is still done by your machine (apt-build actually is an apt-tool to get src packages and rebuild them optimized for your architecture (core 2 duo) for instance. Hence, this offers even more optimizations than a manual compile, as the packages are compiled for generic amd64 rather than my intel core 2 duo...)

Git is not the same as the tarballs from the Compiz website. Git is mainly a developer/tester tool to find bugs in buggy packages, the tarballs from the compiz website are the git files after they have passed bug inspection. Two really different things.

---

### Post by loomsen on 2008-12-02
Oh well, true that, maybe I just got so familiar with tracing bugs I don't even notice them anymore ^^

---

### Post by collinp on 2008-12-11
bump :popcorn:

---

### Post by Labello on 2009-05-10
> **loomsen said:**
> 
Maybe you want to give it a try... Could save you a lot of time imho, I think I don't have to mention that compiling is still done by your machine (apt-build actually is an apt-tool to get src packages and rebuild them optimized for your architecture (core 2 duo) for instance. Hence, this offers even more optimizations than a manual compile, as the packages are compiled for generic amd64 rather than my intel core 2 duo...)

I always edit my makefiles manually to fit my architecture better =)

simply invoke "make" and then checkout the makefile and look for the line CXXFLAGS. There you can customize your buildflags to fit your needs.

---

### Post by frangoitia on 2010-04-18
I did what described in this thread (although with 0.8.4) and it doesnt work.
I can access ccsm, emerald and all the things compiled. But effects aren activated. How do I activate them ?
When I put compiz --replace ccp &, the effects doesnt seem to work and I also dont have decorators.
Im in Lenny

This is a copy of my nvidia-xconfig:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Fri Mar 12 01:42:27 PST 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "dbe"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Ending finding the solution:
nvidia-xconfig -add-argb-glx-visuals -d 24 -composite -allow-glx-with-composite

Now it works perfectly.

---

