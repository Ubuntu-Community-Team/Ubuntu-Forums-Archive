---
title: "Cairo Dock Doesn't Render Properly with Glitz Enabled"
date: 2008-11-26
forum: General Help
---

### Post by EnigMattic on 2008-11-26
Having a problem with Cairo Dock.

I originally install from the cairo-dock.org repo (I'm running Intrepid 64 with Geforce 9600 GT (nVidia driver 177 from repo)) but it was extremely slow.

I uninstalled it and compiled from the source at Berlios with glitz enabled. I used gandalfn's patched libcairo and glitz from [https://launchpad.net/~gandalfn/+archive]("https://launchpad.net/~gandalfn/+archive").

Now when I run ```
cairo-dock --glitz
``` it runs much faster, which is great, but the rendering is pretty screwed up.

SVG icons, for example seem to be missing layers and the background has weird artifacts.

Any ideas where I'm going wrong?

Thanks!!!

---

### Post by fabounet on 2008-11-27
did you follow scrupulously the wiki ?
the last time I've installed it, it gave me a quite nice result (10% CPU max and the only visual bug was with labels)
maybe the current glitz version has a bug ? it is still quite unstable.

---

### Post by EnigMattic on 2008-11-27
I'm pretty sure I did everything exactly as instructed.
I'll have another go to be sure.

---

### Post by EnigMattic on 2008-11-27
Nope. Still the same :(

---

### Post by fabounet on 2008-11-28
well, I'm currently on a full openGL backend for Cairo-Dock, before new year I think we'll have a beta version, maybe it will suit you better (the CPU is very low with this version, like a few %)

---

### Post by hihihi on 2008-11-28
just wanted to confirm:
yes, screwed up rendering with cairo-dock --glitz.
of course compiled with glitz...

for the rest it is head breaking rocket sience to install this cool app... that is a pitty... this thing should be the default in ubuntu with glitz. without glitz, my 64bit maschine has to think a lot...

thx

---

### Post by fabounet on 2008-11-28
seems things are moving on on the libcairo forums, net version may be compatible with glitz again, and perhaps compiled with by default.

---

### Post by EnigMattic on 2008-11-28
> **fabounet said:**
> well, I'm currently on a full openGL backend for Cairo-Dock, before new year I think we'll have a beta version, maybe it will suit you better (the CPU is very low with this version, like a few %)

Cool! Where can I get the version you're using?

---

### Post by Keyper7 on 2008-11-30
The same is happening to me: after patching cairo 1.8.0, installing glitz 0.5.7 and compiling cairo-dock 1.6.2.3 with glitz support, it's **almost** working with glitz, except for the fact that the SVG icons seem to be missing some layers.

Did someone around here managed to use cairo-dock in Intrepid with glitz, without resorting to compiling cairo 1.4?

---

### Post by EnigMattic on 2008-12-01
> **Keyper7 said:**
> The same is happening to me: after patching cairo 1.8.0, installing glitz 0.5.7 and compiling cairo-dock 1.6.2.3 with glitz support, it's **almost** working with glitz, except for the fact that the SVG icons seem to be missing some layers.

Did someone around here managed to use cairo-dock in Intrepid with glitz, without resorting to compiling cairo 1.4?

I'm still in the dark :-S

---

### Post by hihihi on 2008-12-03
so it means we  will have to wait...
it is a pitty because actually, even though i got a fast laptop, this cairo-dock without glitz is not usable.
it is way too slow and consumes lots of power,,,
hovering with mouse costs already 70%-90% CPU!!
this is a dual duo core maschine, it is insane if you think what the dock is doing: zooming little icons needs 4x 2ghz... the cooler starts to blow, the battery drawns, the lights of the city go out.
just to zoom an icon...

nevertheless, awn works much better zooming icons technically, but i do not like awn. so my only option is to go back to the old GNOME-pannel, or is there kiba-dock?
how much KiloWatt will kiba-dock use to zoom little icons?
1000? 3000?

ah...

no, i don want kiba. i want cairo-dock with glitz.
so now let's wait till things get sorted out, until than: back to gnome-panel,,,

---

### Post by Keyper7 on 2008-12-03
If you don't mind using a bleeding edge version, the latest Cairo Dock SVN already has OpenGL backend.

I'm using it right now and despite some glitches it's already working very well. fabounet is doing a fab job (pun intended).

---

### Post by hihihi on 2008-12-03
ah great, it is becoming quite old-school here,
GNOME-panel is doing a good job.

BUT i have to say, the cairo-dock-project is a very very great one, even if the lights of the city go off when hovering with the mouse over the zooming icons. i know that libcairo is to blame and glitz wich seems to be quite experimental so far...
so i hope nobody takes this as a winy-kind of thing... i was just joking.



I will download NOW the SVN-version,:
nevertheless i got a question:
will it need libcairo2 with glitz enabled, or will it use openGL?

thanks to the cairo-dock-creators

---

### Post by Keyper7 on 2008-12-03
It uses OpenGL, you can forget about recompiling libcairo.

---

### Post by hihihi on 2008-12-04
cool, going to try it out after work!

---

### Post by hihihi on 2008-12-04
much better!
i checked out svn and compiled it myself without glitz.
installed with checkinstall and everything went flawlessly.

now apart from the new, nice looking menu-layout with more overview,
the zooming of icons without --glitz is way much better than before.
it is not sluggish anymore and it does not hang..
but in the meantime i got myself the beta prop. drivers from nvidia 180.0something which solves this problem, aswell; so i do not know now where the openGL comes into this story, because hovering with mouse still costs 70%-80% CPU (Xorg)
so the improvement is probably caused by the two things: new cairo-dock, new nvidia drivers.

do i have to compile it with a special option enabled?

how do i enable openGL? 

thx!

---

### Post by Keyper7 on 2008-12-04
cairo-dock --opengl

---

### Post by EnigMattic on 2008-12-04
Anyone know how to add plugins to the new SVN version (cairo dock 2)?
Is there a way of changing the effects used on it?

EDIT:
Ah... how do I remove it!!!?

---

### Post by hihihi on 2008-12-04
WOW this is great!

it is really working smoothly and elegant, it never worked so good!
CPU is with --opengl now at 5% - 10% and thus lower than oldschool GNOME-panel!!! this is truly one step to save the world from global warming and stop power-failures in amsterdam-city for good! ..and save battery-live, 

plug-ins never worked really ok, but now HOHOHO it rocks!

all in all: this is becoming a wonderful sci-fi application and, it is far away from mac-thing. 

great job!!!


compilation and installation went without any problems!!
i installed all cairo-dock stuff with checkinstall,
-cairo-dock flawlessly,
-plug-ins i had to do:
$ sudo checkinstall -D --fstrans=no

thanks everyone for your time and application,
byebye

---

### Post by hihihi on 2008-12-04
> **EnigMattic said:**
> Anyone know how to add plugins to the new SVN version (cairo dock 2)?
Is there a way of changing the effects used on it?

EDIT:
Ah... how do I remove it!!!?


hello there!

what do u want to remove?

---

### Post by EnigMattic on 2008-12-05
> **hihihi said:**
> hello there!

what do u want to remove?

How did you manage to get the plugins working? I installed cairo-dock-2 from the branch and there aren't any plugins

---

### Post by hihihi on 2008-12-05
ok, this is how i did it all:

(MINI-INSTALLATION-GUIDE CAIRO_DOCK_SVN)

before you follow this instructions, you should really uninstall any cairo-dock-installations and themes, plugins and also remove .cairo-dock from your home-dir, so that at the end your system is cairo-dock-free. you should also have everything one needs to compile, like autoconf tools etcetc..

i highly recommend *checkinstall* instead of *make install*,
checkinstall keeps your system clean and you can easely find and uninstall your self-compiled packages under synaptic.
$ sudo apt-get install checkinstall


1)   
if you never downloaded svn or so, this is what you need:
open a terminal and type:
     $ sudo apt-get install subversion


2)   
now make a folder in your home-dir somewhere called 'cairo-dock-svn', in my case i did it under a folder i have, which i named 'apps' within my home-dir:
     $ mkdir ~/apps/cairo-dock-svn

enter into the new folder:
     $ cd ~/apps/cairo-dock-svn


3) 
go to:
[http://developer.berlios.de/svn/?group_id=8724](http://developer.berlios.de/svn/?group_id=8724)

the right brunch is for the normal people like me the 'Anonymous SVN Access via SVN'; you just need to paste the svn sentence into the terminal:
     $ svn checkout svn://svn.berlios.de/cairo-dock/trunk


4)
after the svn checkout is done you can 
**compile and install cairo-dock**:
     $ cd ~/apps/cairo-dock-svn/trunk/cairo-dock
     $ autoreconf -isvf
     $ ./configure
     $ make 
     $ sudo checkinstall

you need to go through the checkinstall-wizard inside the terminal and correct the name and version, otherwise it will abort.
it is very easy as the wizard is well done.
i named it "cairo-dock-svn" and set version to "1.7"

everything went flawlessly yesterday and you will end up with a nice build and installed .deb package which you can uninstall at anytime via synaptic.


5)
**compile and install plug-ins**:

     $ cd ~/apps/cairo-dock-svn/trunk/plug-ins
     $ autoreconf -isvf
     $ ./configure
     $ make 
     $ sudo checkinstall -D --fstrans=no

also here you need to set name and version,
i named it "cairo-dock-plugins-svn" and set version to "1.7"


6)
**compile and install themes**:

     $ cd ~/apps/cairo-dock-svn/trunk/themes
     $ autoreconf -isvf
     $ ./configure
     $ make 
     $ sudo checkinstall -D --fstrans=no

also here you need to set name and version,
i named it "cairo-dock-themes-svn" and set version to "1.7"


now you are all set.

to start with openGL backend you do:
$ cairo-dock --opengl
happy configuring!

---

### Post by Ng Oon-Ee on 2008-12-15
> **hihihi said:**
> ok, this is how i did it all:

(MINI-INSTALLATION-GUIDE CAIRO_DOCK_SVN)

...

Hi, thanks for the mini-install guide. Quick question, what's the difference between this and running the .sh script provided by the official website? Besides the checkinstall vs make install?

---

### Post by davidself1001 on 2008-12-15
> **hihihi said:**
> ok, this is how i did it all:

(MINI-INSTALLATION-GUIDE CAIRO_DOCK_SVN)

before you follow this instructions, you should really uninstall any cairo-dock-installations and themes, plugins and also remove .cairo-dock from your home-dir, so that at the end your system is cairo-dock-free. you should also have everything one needs to compile, like autoconf tools etcetc..

i highly recommend *checkinstall* instead of *make install*,
checkinstall keeps your system clean and you can easely find and uninstall your self-compiled packages under synaptic.
$ sudo apt-get install checkinstall


1)   
if you never downloaded svn or so, this is what you need:
open a terminal and type:
     $ sudo apt-get install subversion


2)   
now make a folder in your home-dir somewhere called 'cairo-dock-svn', in my case i did it under a folder i have, which i named 'apps' within my home-dir:
     $ mkdir ~/apps/cairo-dock-svn

enter into the new folder:
     $ cd ~/apps/cairo-dock-svn


3) 
go to:
[http://developer.berlios.de/svn/?group_id=8724](http://developer.berlios.de/svn/?group_id=8724)

the right brunch is for the normal people like me the 'Anonymous SVN Access via SVN'; you just need to paste the svn sentence into the terminal:
     $ svn checkout svn://svn.berlios.de/cairo-dock/trunk


4)
after the svn checkout is done you can 
**compile and install cairo-dock**:
     $ cd ~/apps/cairo-dock-svn/trunk/cairo-dock
     $ autoreconf -isvf
     $ ./configure
     $ make 
     $ sudo checkinstall

you need to go through the checkinstall-wizard inside the terminal and correct the name and version, otherwise it will abort.
it is very easy as the wizard is well done.
i named it "cairo-dock-svn" and set version to "1.7"

everything went flawlessly yesterday and you will end up with a nice build and installed .deb package which you can uninstall at anytime via synaptic.


5)
**compile and install plug-ins**:

     $ cd ~/apps/cairo-dock-svn/trunk/plug-ins
     $ autoreconf -isvf
     $ ./configure
     $ make 
     $ sudo checkinstall -D --fstrans=no

also here you need to set name and version,
i named it "cairo-dock-plugins-svn" and set version to "1.7"


6)
**compile and install themes**:

     $ cd ~/apps/cairo-dock-svn/trunk/themes
     $ autoreconf -isvf
     $ ./configure
     $ make 
     $ sudo checkinstall -D --fstrans=no

also here you need to set name and version,
i named it "cairo-dock-themes-svn" and set version to "1.7"


now you are all set.

to start with openGL backend you do:
$ cairo-dock --opengl
happy configuring!
I am a bit of a novice (to say the least) but... I followed your procedure without flaw until I reached the "autoreconfig -isvf" command and my system says it cant find that.  What do I need to do to be able to execute the autoreconfig command?

---

### Post by hihihi on 2008-12-15
@ davidself1001:

it seems that you do not have the compile-tools,

go to synaptic and install the following packages:
-autoconf 
-autotools-dev
-automake
-automake1.9
-f2c
-fort77

that should do the trick,

after that, start over again with my little how-to,
good luck
:)

---

### Post by hihihi on 2008-12-15
> **Ng Oon-Ee said:**
> Hi, thanks for the mini-install guide. Quick question, what's the difference between this and running the .sh script provided by the official website? Besides the checkinstall vs make install?


the provided .sh script did not work well for me and i do not know what is happening exactly.
it happened me once, that such an install-script did a very good job on installing something, but uninstalling was a pain in the iso...

if you want to know the difference, get the .sh script and open it with gedit. than you will be able to compare them side by side...

-when you do 'make install', the files go where?
and when you uninstall it, are the files all gone?
some make-install-scripts are very well done and some not..

i prefer checkinstall, because it does not just install the files,
it first makes a .deb package of your compiled piece of software;

that way, it will be very easy to just uninstall the beta-version of cairo-dock when the final release is available.


good luck,
):P

---

### Post by davidself1001 on 2008-12-15
> **hihihi said:**
> @ davidself1001:

it seems that you do not have the compile-tools,

go to synaptic and install the following packages:
-autoconf 
-autotools-dev
-automake
-automake1.9
-f2c
-fort77

that should do the trick,

after that, start over again with my little how-to,
good luck
:)
I get the following error in the ./configure step.  What am I missing?

checking for PACKAGE... configure: error: Package requirements ("gtk+-2.0 gthread-2.0 cairo librsvg-2.0 dbus-1 dbus-glib-1 libxml-2.0 gtkglext-1.0") were not met:

---

### Post by fabounet on 2008-12-16
you need the dev package of each of these packages.
install them with Synaptic

the advantage of the script is that it installs all the dependencies you will need. but you're right to want to do it yourself, it's very instructive anyway and the use of checkinstall is appreciable :-)

---

### Post by davidself1001 on 2008-12-16
I'm not following you.  I did istall all of the dev packages with Synaptic.  I am following the procedure to the letter but I get the above mentioned error in the ./configure step so I must be missing some other package related to gtk.  Any ideas?

---

### Post by davidself1001 on 2008-12-16
Any help would be greatly appreciated.  I am missing some gtk package based on the earlier message I posted.

---

### Post by fabounet on 2008-12-17
amongst gtk+-2.0 gthread-2.0 cairo librsvg-2.0 dbus-1 dbus-glib-1 libxml-2.0 gtkglext-1.0 there must be one or more packages that are not installed (dev version)

---

### Post by hihihi on 2008-12-17
> **davidself1001 said:**
> Any help would be greatly appreciated.  I am missing some gtk package based on the earlier message I posted.

hello there, yes, as fabounet said, you are probably missing other development files (dev).
this is now a very nice moment to learn some basic things on how to compile, and it is quite easy:

-on the terminal, when u do ./configure
it stops with some messages, error, blablabla, something not met...
but above that message u will find a list.
on the left u see the depending dev-packages that the comfigure-script has found on your system, followed with an "yes" or so on the right.
normally the last package-info on that list ends with something like "no" or "not available" "not found" or nothing on the right side.

for example you would read on the left side something like "libWHATEVER"
than u go first to synaptic, click on search and type in "lib whatever" and let it search. with some luck u can find it listed and than it could be called "whatever" or "ever-what" or "libwhatever". u will always need the -dev files for compilation and so u click, if available, on the repespective -dev files, like:
"whatever-dev" or "ever-what-dev" or "libwhatever-dev"

after that one is installed, u do ./configure again.
if it stops again, look again in that list.
normally u should be seeing different package missing, than repeat the synaptic-thing.
and so on till ./configure ends successfully...

good luck!!!

---

### Post by davidself1001 on 2008-12-17
Thanks for the response.  I will try what you say.  However, right now I am a bit screwed as I removed the Gnome panel and now I only get the Cairo-dock at the bottom of my screen with no desk top icons and no keyboard shortcuts (ie Alt/f2).  I am trying to figure that out in another thread.  Any ideas?

---

### Post by davidself1001 on 2008-12-17
I am making progress.  Got thru the prog process but then get the following error doing the autoreconfig in the plugin section.  Any ideas on what this is?


checking if f77 static flag -static works... yes
checking if f77 supports -c -o file.o... yes
checking whether the f77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
./configure: line 20059: syntax error near unexpected token `0.35.0'
./configure: line 20059: `IT_PROG_INTLTOOL(0.35.0)'

---

### Post by fabounet on 2008-12-18
I have the same issue on a Feisty I'm using for test.
I couldn't get intltool accept this macro, although it works on my Hardy, so I've just removed the 0.35.0 in the configure.ac
so the line will become :
IT_PROG_INTLTOOL()

---

### Post by davidself1001 on 2008-12-18
Thanks fabounet.  Finally got it working.  There seems to be a missing plugin.  The standard installation from synaptic had a plugin called dnum or gnum, or something like that, that gave you access to all of the main menus including preferences, system, etc.  Is there a way to get that plugin for this version?

---

### Post by davidself1001 on 2008-12-18
So is this version compatible with the plugins that you can download via synaptic?  In other words can I download the plugins from synaptic and run the cairo-dock-svn that I just compiled and installed?

---

### Post by davidself1001 on 2008-12-18
The plugin that I am looking for is called Gmenu.  That seems to be missing from the svn version.  Is there a way to just install a single plugin?

---

### Post by fabounet on 2008-12-19
if you switched to the svn version, you have to compile both dock and plug-ins with the same version.
I recommend you to install the SVN in a different folder (like /usr/local) so that you will have both the stable version (1.6.3) and the future release (2.0.0).

---

