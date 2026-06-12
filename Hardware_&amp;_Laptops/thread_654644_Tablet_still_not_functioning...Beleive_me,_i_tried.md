---
title: "Tablet still not functioning...Beleive me, i tried..."
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by ~/Chromekaldra/~ on 2007-12-31
Basically i bought a book called hacking Ubuntu which is basiclly everything you need to know and follw to get ubuntu to be usable and user freindly. Problem is, they kinda assume you've used linux or other before as they never cover the con side of things (like if something didn't happen or isn't there...) That's why i'm here.

I followed the instructions to modify the Xorg file, adding a section for Synaptics Touchpad. Right above that, like a few lines above, there lies something interesting:

"#Uncomment if you have a Wacom Tablet" And what follows under are 3 lines of code starting with # (which i assumed was a null kinda thingy, that line of code will not run.) and so i deleted the # and saved...

Tablet still doesn't work....

I ddl the Wacom-Linux drivers for my tablet, but i'm having a hard time installing it seeing as i don't know HOW to install it....I have an archive, un-packed it, got a folder. In this folder are several files, let me show you a pic...

[hide][img]http://i110.photobucket.com/albums/n96/Female_Kaldra_is_hot/Screenshot.png[/img][/hide]

So there are a few files that i'd like to run but don't know how too, mainly the install-sh and the Configure...they are both X-shell type. 

PLEASE respond...i'm tired of getting pushed to the back and never answered...i'd like to ENJOY linux, not hate it for it's lack of newbie handout help...

*EDIT*

I ran the prebuilt thingy, but it complained that stuff wasn't install, mainly: [Please install tcl/tk then run this script again] I found that ironic as this is the prebuild...

*EDIT*

There is code for my tablet in the X-org file but not in /proc/bus/input/devices even thought the damn thing is plugged in.

---

### Post by LaRoza on 2007-12-31
I am unfamiliar with what you did, but usually you have to log out or restart for a change to be applied.

The # are comments. 

In source code, and configuration files, you can write comments and each language has a special symbol for this. In most cases, it will be a #.

"uncomment" and "comment" are verbs too, when used like this.

---

### Post by ~/Chromekaldra/~ on 2007-12-31
erh...okay (the verb part)

Yeah, i restarted, and when i did, got a lot of code on started up, most of it dealing with USb hub and an **error 71**, but once that was done, start up was normal and everything seems alright, minus the no Tablet function...

---

### Post by ~/Chromekaldra/~ on 2008-01-01
Bump....

It's a simple question, what's the code for installing certain file types?

---

### Post by ~/Chromekaldra/~ on 2008-01-02
Uh.....anyone out there?.....please?....:(

I mean, i bought a book that would invalidate my asking for help, but it's just a little more advanced than i am, in the sense that it tells me to install stuff and i don't know how...that about it....

---

### Post by popch on 2008-01-02
Hi and welcome.

Some Wacom tablets work quite well with Ubuntu Linux, and all it takes is to remove those # signs from xorg.conf, as you did. The software to support the tablets is already there.

It would help if you mentioned what kind of tablet you have. You could also find solutions to that problem faster if you had a look at the ***Hardware and Laptop*** section of this forum. There is quite a number of threads there on Wacom tablets and Tablet PCs.

---

### Post by ~/Chromekaldra/~ on 2008-01-03
Alright, thank you, is there an easy way to **move this thread to hardware and Laptops**? 

I'm using a Bamboo tablet, the installation CD failed to install the driver as when i try to run the Tablet Config option, i get a pop up; Driver not found. I've restarted, re-installed and used the downloaded drivers from the Wacom site that are supposed to be more up to date...still no luck. I'm starting to wonder if it;s an actual physical flaw with the tablet.

---

### Post by ~/Chromekaldra/~ on 2008-01-04
BUMP

i need to be super user, so i run the code 'su' as the readme txt file says to, and then i punch in my password, but no go, authentication fails, WHY? I need to be su in order to run the other code in the readme txt since as is, w/o being su, permission is denied...

---

### Post by band-aid on 2008-01-04
Ubuntu has the root count disabled by default for security reasons. Whenever something tells you to run as super user you have to use sudo before the command

E.G.

sudo nano xorg.conf

will as for your password and allow you to edit xorg.conf as root


As for installing the driver, you will want to browse to the folder that all the files are extracted to and then run the configure script.

do

./confgure

if it doesn't work, saying that its not executable or something like that try

sudo chmod +x ./configure

This will make it execuable


After that runs, it may ask you some questions I honestly have no experience whatsoever with tablets. This is just a generic installation procedure.

The configure script should create a make file, this is what we want to run next

do 

make install

this will run through the make file and install everything you need.

---

### Post by ~/Chromekaldra/~ on 2008-01-04
I get the following code at some point in time, some things didn't install, weren't 'there' so to speak, even though this is an updated package from the website...

```
*** WARNING:
*** The ncurses development library does not appear to be installed.
*** The header file ncurses.h does not appear in the include path.
*** Do you have the ncurses-devel rpm or equivalent package
*** properly installed?  Some build features will be unavailable.
***
***
*** WARNING:
*** Unable to compile wacdump without ncurses environment
*** wacdump will not be built
***
***
*** WARNING:
*** xidump will build without ncurses support.
***
***
*** WARNING:
*** libwacomxi requires tcl environment; libwacomxi will not be built.
***

```

any ideas?

---

### Post by popch on 2008-01-04
The recipe for satisfying those dependencies is in another thread:

[http://ubuntuforums.org/showthread.php?t=574310&page=3](http://ubuntuforums.org/showthread.php?t=574310&page=3)

What I do not quite understand: have you looked at other threads in this forum which deal with the Bamboo at length? Such as

[http://ubuntuforums.org/showthread.php?t=631881&highlight=wacom+bamboo](http://ubuntuforums.org/showthread.php?t=631881&highlight=wacom+bamboo)

---

### Post by band-aid on 2008-01-04
ok your missing ncurses. It allows programmers to make prettier console based programs.

look for ncurses in synaptic and install it. Or google ncurses and download the source and compile it using the same method.

Alternatively you could look for your wacom drivers in synaptic to see if anyone has compiled them already.

---

### Post by ~/Chromekaldra/~ on 2008-01-05
good point, i will try. This is all very different from Windows, so some 'common knowledge' things simply do not occur to me :(

---

