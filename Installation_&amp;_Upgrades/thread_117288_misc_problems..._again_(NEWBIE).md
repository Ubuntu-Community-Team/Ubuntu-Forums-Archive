---
title: "misc problems... again (NEWBIE)"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by riwa on 2006-01-14
well... you guys probably figure out i'm a newbie so I wont (but am!) bother telling you... 

btw im running on an acer laptop <acer aspire 3003 lmi> or something like that. 

I try to launch firestarter from root. It tells me: 

(firestarter:8272): Gtk-WARNING **: cannot open display:

I get this warning several times in different situations (can't remember when though)
Also my soundcard doesn't work. I can't watch dvds. I can't get my hands on a c++ compiler. I can't see my battery status (luckily i have this little lamp telling me if im connected or not!). 

I've already posted a thread a couple of days ago about this (but can't seem to find it) and I don't have a readily available internet connection so I can only check this every now and then. I really appriciate (now how do i spell that?) help... On any of these matters. I keep getting this "certificate unknown message" and feel really 'unsafe' with it. Trying to get stable on ubuntu right now...

Regards
Richard

---

### Post by Zelut on 2006-01-14
are you running firestarter from the terminal or from the menu?  I seem to remember I saw that error when launching from the terminal but it seemed to still work ok.. 

for the rest of your issues take a look thru the [UbuntuGuide ]("http://www.ubuntuguide.org")& see what you can fix from there.

There should be options for [sound]("http://ubuntuguide.org/#configuresoundproperly"), DVD & [compilers]("http://ubuntuguide.org/#build-essential") all there..  tip on the DVD though.  do the following...

cd /usr/share/doc/libdvdread3/examples/
sudo ./install-css.sh

---

### Post by riwa on 2006-01-14
That dvd install seemed to work. Don't have a dvd here but its installing allright. Gonna check that ubuntuguide and see what i can find... Still nothing about the c++ compiler though ;/  Been looking a lot. just doesn't work. Also... (problem number 2²3) tried this zsnes donwload but cant isntall it.. My spm doesn't find it and i need to recompile it to get it to work... Well. Thanks alot anyway...

/Richard

---

### Post by Zelut on 2006-01-14
you need this package to compile programs:  build-essential

...it has all of the 'build-essential' packages needed for compiling, etc.. maybe you just missed it on the ubuntuguide.  There is a lot there :)

---

### Post by riwa on 2006-01-14
Yeah. I guessed i missed a lot there. Can i compile with the gcc command now (like ive seen in the bunch of c++ tut ive read). Awesome anyway. By the way i couldn't get find firestarter anywhere. I only tried it in the terminal...

---

### Post by Zelut on 2006-01-14
if you've installed build-essentials you should now be able to compile anything (./configure, make, make install, etc..)

On my machine firestarter was found in Applications > System Tools > Firestarter (gnome)  If it isn't I'd ask if you installed it using the ubuntu packages or...

---

### Post by riwa on 2006-01-14
i installed it from the terminal using the sudo apt.get command. I guess i didn't get the standard c library with the compile-package am i right? Got an error trying to compile a file with <iostream>

I've also been wondering how i can get rid of that anyoing startupscreen.(which is when you start the computer) If itrs like possible to login from terminal or something like that...

---

### Post by Zelut on 2006-01-14
build-essential should be everything you'd need...  What is the error you got when compiling?

---

### Post by riwa on 2006-01-23
It was nothing. I used gcc instead of c++/g++ for compiling c++ code. I only seem to have a Java interpreter. Can i still compile in that one? And i got another problem trying to compile 'zsnes' emulator. It asks me for nasm or something but i cant seem to find it.

I also get the following message when i start synaptic package manager:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)

Have no idea what it means except that it's wrong.

---

