---
title: "32bit Version of Wine on 64 bit Intrepid"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by bocajuniors12 on 2009-02-21
Hey,

I'm completely new here and new to Linux, so hello.

I'm trying to build 32-bit Wine on a 64-bit (x86-64) Ubuntu Intrepid system as per the WineHQ instructions see below:

> 
If you're running a 64 bit version of your distro, building Wine the usual way yields... 64 bit wine! This usually isn't what you want. Building a 32 bit Wine on a 64 bit system requires a few extra steps.

On supported distributions (currently, just Ubuntu 8.10), you can just do

wget [http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh](http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh)

sudo sh install-wine-deps.sh

to install all the needed packages and fix the missing symlinks in /usr/lib32, and

./configure 
make

as normal to build 32 bit wine. (To build 64 bit wine, do the same thing, but add the --enable-win64 argument to configure... and, until a new version of gcc comes out, use a gcc built from fresh sources as described at Wine64.) 

The first two lines :

wget [http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh](http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh)

and 

sudo sh install-wine-deps.sh

seem to run okay, but I have no idea what ./configure or make do, because when I type them in I get errors 

bash: ./configure: No such file or directory

and 

make: *** No targets specified and no makefile found. Stop.

I guess I'm a little out of my depth, but I assume they will compile the code but I have no idea how to do it. 

Can anyone help this stranded noob?

cheers

Mungo

---

### Post by logos34 on 2009-02-21
Is that even necessary?  Can't you run the 64-bit version?  That's what I do.

> 
[http://wiki.winehq.org/FAQ#head-b89ca9d7cdf2bc2ddfb23b3e5829219df48524f8](http://wiki.winehq.org/FAQ#head-b89ca9d7cdf2bc2ddfb23b3e5829219df48524f8)

2.4. Does Wine run on 64-bit?

Yes. Normally, installation should be the same as with 32-bit: simply install the Wine package for your distribution. Check the Downloads page. If you need to build Wine from source, see WineOn64bit.

Note that Wine for 64-bit actually runs in 32-bit mode. This is necessary, as virtually all Windows applications are 32-bit. Support for 64-bit Windows applications is planned for the distant future (see Wine64).

---

### Post by bocajuniors12 on 2009-02-21
I think so.

I'm trying to get Rosetta stone to run and I know it won't work for 64bit Windows.

unless anyone else has got it to work on Wine64.

cheers

---

### Post by bocajuniors12 on 2009-02-22
Sorted!

I installed the latest developer release of wine see [here]("http://winehq.org/download/deb")

and Robert's your father's brother ... it works a charm.

I even ran a windows patch through Wine, so I could erm.. 'evaluate' it properly at my leisure.

---

