---
title: "How do I downgrade Audacity?"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by dwieberd on 2009-05-25
I'm having trouble with the latest version of Audacity (1.3.7) and would like to revert back to something like version 1.2.4 (which I know did not have the problem I'm experiencing) or maybe version 1.2.6 which is billed as a stable release.

It seems really hard to do for some reason. I always seem to be steered to the 1.3.7 version, which surprises me, especially since it's called a beta, rather than a stable release.

I'm using 8.04 LTS and have read about the 'force version' option in the package manager, but for me it's not available (grayed out) on the menu.

Can anybody help?  Thanks.

---

### Post by tgalati4 on 2009-05-25
You might try compiling from scratch and see if that fixes things.

---

### Post by dwieberd on 2009-06-01
I don't really know how to recompile Audacity. Seems like it should be easier just to install a version that I know works. Doesn't anyone have some advice for the larger question of why I'm not allowed to force a version of Audacity to install (a stable version, rather than the beta default)?

---

### Post by tgalati4 on 2009-06-01
Download the source code.

sudo apt-get install build-essential
tar -xzvf audacity-whatever.gz
cd audacity-whatever
./configure
make
sudo make install

There may be a few other packages to install.  I haven't built it in a while, but those are the basic steps.

A riskier approach, one that I DO NOT advocate, but has worked in frustration:

Remove current version of audacity (sudo apt-get remove audacity)
Change your repositories in /etc/apt/sources.list to an older version of ubuntu.  
sudo apt-get install audacity
Immediately change your repositories back to the correct one.  Make a backup of sources.list first.
WARNING, this can completely screw up your installation making further upgrades a nightmare.

That is why building from scratch is both a learning experience (admittedly forced) and safer than trying to force-install an older version from the current supported version.

Take it a step at a time.  According to the audacity homepage 1.3.7 and 1.2.6 can live together.

Go to [http://audacity.sourceforge.net](http://audacity.sourceforge.net)

These are the pre-built packages (*.deb) available for Ubuntu:

    *  dapper (sound): A fast, cross-platform audio editor [universe]
      1.2.4b-2ubuntu2.1 [security]: amd64 i386 powerpc
    * dapper-updates (sound): A fast, cross-platform audio editor [universe]
      1.2.4b-2ubuntu2.1: amd64 i386 powerpc
    * hardy (sound): A fast, cross-platform audio editor [universe]
      1.3.4-1.1ubuntu1: amd64 i386
    * hardy-backports (sound): A fast, cross-platform audio editor [universe]
      1.3.5-2~hardy1: amd64 i386
    * intrepid (sound): A fast, cross-platform audio editor [universe]
      1.3.5-2: amd64 i386
    * jaunty (sound): A fast, cross-platform audio editor [universe]
      1.3.7-2ubuntu1: amd64 i386
    * karmic (sound): A fast, cross-platform audio editor [universe]
      1.3.7-2ubuntu1: amd64 i386
--------------------------------------

So you see that 1.2.6 is not pre-built for Hardy.  Never will be.  So you have a choice, use 1.3.4 or 5 or build 1.2.6 yourself.

Download the source code:  (from audacity.sourceforge.net)

[http://sourceforge.net/project/downloading.php?group_id=6235&filename=audacity-src-1.2.6.tar.gz](http://sourceforge.net/project/downloading.php?group_id=6235&filename=audacity-src-1.2.6.tar.gz)

Open a terminal window:
cd Desktop
tar -xzvf audacity-src-1.2.6.tar.gz
cd audacity-src-1.2.6
cat README.txt
sudo apt-get install build-essential   (needed for any program building activity)

The instructions say that wxGTK2.4 is needed.  Let's search the repositories for them.  (I'm building this on a gutsy machine, because I'm too lazy to boot my hardy machine.)

apt-cache search wxgtk  (lots of libraries, so let's load all the 2.4 ones and hope to get lucky.)
sudo apt-get install libwxgtk2.4-dev libwxgtk2.4-dbg libwxgtk2.4-contrib-dev libwxgtk2.4-1-contrib libwxgtk2.4-1  python-wxgtk2.4

Hopefully that all loads correctly.  Now we are going to configure your build environment.  This checks that you are not missing anything required to build audacity.  If so, you will get errors.  When there are no errors, you can "make" the program.

./configure  (go grab some coffee)

Oops, I got a warning:

Note: portaudio v18 only supports OSS.  If your system supports
ALSA, you may want to reconfigure --with-portaudio=v19, though
portaudio v19 is newer and possibly less stable.

Run 'configure --help' for an explanation of these options,
otherwise run 'make' to build Audacity.

---------------------------------

Let's ignore the warning and push on.  Audacity works better with OSS anyway.  The downside is that it hogs the soundcard when using it.  Oh well.

Moving on:

make  (Grab a couple of beers.  This will take a while.)

---

### Post by tgalati4 on 2009-06-01
Well, got some errors.  Turns out some libraries are missing.  Reading the sourceforge page:  libmad, libsndfile, and ogg vorbis are optional.  But really may be required.

Let's find them:  (Using the shotgun approach--find and load anything that looks like libmad)

apt-cache search libmad
sudo apt-get install libmad0 libmad0-dev libmad-ocaml libmad-ocaml-dev

Hopefully that went well.  Need to find libsndfile.  moc is not needed but it's a cool program.  Again, shotgun approach, grab anything related to libsndfile.

apt-cache search libsndfile
sudo apt-get install mffm-libsndfilew-dev moc libsndfile1 libsndfile1-dev sndfile-programs

Hopefully, your system is still running, and you have some disk space left.

We need ogg vorbis.  

apt-cache search libvorbis
sudo apt-get install libvorbis-dev libvorbis0a libvorbisenc2  libvorbisfile3

As a generally rule, you will always need -dev versions of libaries when building from source code.

Let's try to remake our audacity 1.2.6.

make

More errors. Darn it.  Something about libsoundtouch.  Soundstretch is probably not needed, but sounds like a cools program.  It probably stretches sound.

apt-cache search libsoundtouch
sudo apt-get install libsoundtouch1-dev  libsoundtouch1c2 soundstretch

More errors:

error: #error "SSE instruction set not enabled"

There was a bug report that may not work on Pentium II hardware.  SSE instruction set sounds like something related to the instruction set of the processor.  I'm running on a seriously old Dell Pentium III, but on a PII-style chassis.  Better find out what the default compiler options are:

./configure --help
./configure --without-soundtouch  (since this seems to be causing errors)

Here's what I get:

Finished configure:
  with    libsndfile (system)
  with    libresample
  without libid3tag
  with    libmad (system)
  with    LADSPA plug-in support
  with    Nyquist plug-in support
  with    vorbis (system)
  with    portmixer
  with    portaudio v18
  without soundtouch
  with    help
prefix=/usr/local

Let's try again without soundtouch this time:

make (grab another beer or 2--Bud Light Lime in this case.)

If that doesn't completely blow up your machine, then:

sudo make install

Now, where did make put audacity?

whereis audacity

You should have two:

/usr/bin/audacity  (1.3.4  installed using Synaptic)
/usr/local/bin/audacity (1.2.6)

To run it:
/usr/local/bin/audacity

Hey, it actually works.

---

### Post by tgalati4 on 2009-06-01
So to answer your question:  Yes, there should be a simple way to downgrade an application to an earlier version.  However, there are major differences between 1.2.6 and 1.3.4 (and beyond).  If you read the release notes, you will see what they are.  Ubuntu tries to grab the near-latest code when it releases.  The old stuff gets dropped by the wayside, even if it works better in certain cases.

Hence, don't be afraid to build what isn't readily available.  Especially if it works for you.  Or wait for somebody else to build it.

Gee, 1.2.6 seems quicker!  1.4 MB versus 4.7 MB codebase.

---

### Post by kruegger on 2009-06-01
Clap, clap.

tgalati, I have enjoyed your hilarious yet useful chronicle. You made it look easy.

I have never been able to compile anything in Gutsy. To many errors to solve.
I stick to the official repositories as a way to preserve my mental health :D

but I am amazed to see in almost real-time that someone is able. 

Best Regards

PS: How come you are still in Gutsy?. I feel like a dinosaur. I tried to update to Hardy twice with no success. Grub instalation problems.
As usual ;-)

---

### Post by tgalati4 on 2009-06-01
I've got 9 different machines.  Each is running something different.  This just happened to be the one I was reading the forums with.  Gutsy runs OK on a 500 MHz, Pentium III machine with 768 MB (max 3 x 256 MB).  I'm actually running Linux Mint Darnya XFCE which is based on Gutsy.

I last built audacity in 2006 on a Dapper machine (1.2.4) because I was having trouble with newer versions.  I don't remember now what the problem was, but I know that 1.2.4 was stable and worked well in Dapper.

It's hard to give advice on the forums when you don't have the complete picture.  I also don't like to give advice unless I have personally suffered the anguish myself.

Building programs can be frustrating.  Many are familiar with "dependency hell".  It also takes a lot of time.  I did build 1.2.6 in real time, but I didn't really drink the beers.  It was too early in the day.  I normally don't drink before noon!

I did use the "switch repository" method (again NOT recommended) to get vagalume (a LastFM player) to work on Gutsy when it was only packaged for Intrepid.  Too many dependencies to fix to get it to build on gutsy, so it was quicker to trick the system and loaded the Intrepid version.  Works OK so far.

With each new release of Ubuntu, the newer kernels that are captured can sometimes drop support for older/unique hardware.  Or sometimes it's a simple regression.  Add new features for new motherboards, but pooch the really old machines.

Try Jaunty on your machine.  It may actually work.  Or try opensuse or Fedora.  Clean install is generally better than a dist-upgrade.

Good luck.

---

### Post by kruegger on 2009-06-02
I'm upgrading to Hardy right now. Third try. Fingers crossed.;)

I won't try Jaunty, thanks. Not even after eight beers (which is enough to knock me down). I read what others ubunters are going through and I don't feel like it. I'll stick to a LTS version.

I decided to take a break off Ubuntu. I mean I still use it but I don't stay up until down trying to set some driver and such. [-X
Too much frustration and anguish for me to bear.

PS: I didn't mind your drinking of beer while compiling. You are a grown-up. But still liked your laid-back style. (not being ironic).

bye

---

### Post by Barriehie on 2009-06-02
I too might have to try compiling on my own!  Audacity only likes to run correctly if it's config file is missing upon startup.  From then on it can't find the sound device.  Right now I've got a shell script that blows away the config file and then starts audacity.  Works for now but I know something is breaking somewhere!

Barrie

---

### Post by tgalati4 on 2009-06-02
Could be a conflict between what is stored in the configuration file and what is specificed in /etc/modprobe.d/alsa-base.

Could also be a conflict between OSS, ALSA, and pulseaudio.  I recall some workarounds in the forums, but you will have to search for them.

---

### Post by Barriehie on 2009-06-02
> **tgalati4 said:**
> Could be a conflict between what is stored in the configuration file and what is specificed in /etc/modprobe.d/alsa-base.

Could also be a conflict between OSS, ALSA, and pulseaudio.  I recall some workarounds in the forums, but you will have to search for them.

Wonderful!  I searched for 'audacity and modprobe.d' and found this [this link]("http://ubuntuforums.org/showthread.php?t=843012&highlight=audacity+modprobe.d").  Somewhere in there I was directed to, [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup) and found that:
```

pasuspender -- audacity

```was what I needed.   Per the pulsaudio wiki I installed the following:
> 
 Make sure to install all auxiliary GUI tools for the PulseAudio sound server: 
 
[LIST]
[*][PulseAudio Volume Control]("http://0pointer.de/lennart/projects/pavucontrol")
[*][PulseAudio Volume Meter]("http://0pointer.de/lennart/projects/pavumeter")
[*][PulseAudio Manager]("http://0pointer.de/lennart/projects/paman")
[*][PulseAudio Device Chooser]("http://0pointer.de/lennart/projects/padevchooser")
[*][PulseAudio Preferences]("http://0pointer.de/lennart/projects/paprefs")
[/LIST]
 The packages are [COLOR=Red]**pavucontrol pavumeter paman padevchooser paprefs.**[/COLOR] 
 
After several starts and stops of audacity, with the .conf file access times changing accordingly it works.

[COLOR=Red]**To the OP:  I'm running 8.04 LTS and my audacity version is 1.3.4-beta (1.3.4-1.1), from the repos.**[/COLOR]

Thank You,
Barrie

---

### Post by tgalati4 on 2009-06-02
Yes, that was the link that I was thinking of.  I'm glad you found it.

Everything is fixable in linux. You just need to keep chipping away at it.  That is why it's called hacking.

---

### Post by dwieberd on 2009-07-18
Thanks tgalati4 for the detailed Audacity instructions last month. I finally got around to trying it and it actually worked!

There was just one snag at the end where it didn't recognize an 'msgfmt' command, or something like that. I didn't know what to do so I just typed msgfmt at the prompt and it actually responded with an apt-get install suggestion which I tried and it worked. After that the 'make install' worked also.

Thanks again.

---

