---
title: "xmms, m4a files, and taking up all memory/crashing"
date: 2005-11-28
forum: General Help
---

### Post by GreatestGravity on 2005-11-28
So, after upgrading to Breezy, xmms is having problems with m4a files. It can see the tags now, unlike before, but it's having some problems playing them.

Occasionally, when starting a new m4a song, it'll crash. (Tells me it segfaults.) There are some songs which do this; clicking on them to play them works, but if you continue from a previous song onto that one then xmms dies. This is often reproducible.  

Also, occasionally XMMS decides to suddenly freeze the computer by trying to take up gigabytes of memory. (Have never been able to reproduce that intentionally. It's happened at least wtice though.)

So, anyone have any suggestions? What should I try, besides trying a different media player or converting format of all of my songs? Anyone heard of this problem before?

---

### Post by GreatestGravity on 2005-11-29
Anyone have any ideas? It keeps doing it, and it's being really frustrating. 

Occasionally when playing m4as, it either segfaults or takes up all avaliable memory.  Looking at the output that xmms gives when run from a terminal, it occasionally gives a "read error" before crashing. 

Someone, please help? Or is this in the wrong section of the forum? I'd really like to get this sorted out...

---

### Post by gingermark on 2005-11-29
OK, I don't know for certain the answer (I only have 1 m4a file, but it plays fine in Breezy), but you asked for suggestions so here they are:

Pop into Synaptic and do a search for "faad". Check that you have libfaad2-0 installed. You may as well have the gstreamer plugin and the other faad package installed too if you're gonna play a lot of m4a files. I don't think you'll need the dev files of the lib package. Also check that the xmms-mp4 package is installed.

The reason I've suggested that is some reading I came accross suggested that it is a combination of the faad library and the mp4 plugin that allows xmms to play m4a files.

It's worth a go anyways.

Other than that, maybe try installing beep-media-player. I know you said you didn't want to install another player, but as bmp is a fork of xmms they are quite similar, and if the files play in bmp fine then it might suggest that your xmms installation didn't quite come through the upgrade perfectly.

Hopefully someone will come along with other ideas of what might be wrong, as I say, I don't play these files very often. Best of luck.

---

### Post by dezier on 2006-11-04
I have the same problem in booth xmms and beep media player. The mentioned libraries are installed. It's very frustrating not being able to play all my Miles Davis albums. ;-)

Anyone else that might have a clue?

---

### Post by jmmcd on 2007-12-02
Hello all. I had the same problem: xmms suddenly taking up loads of memory, usually *between* two mp4 tracks. I reinstalled the xmms-mp4 plugin from source and this seems to have fixed the problem for me at least -- no guarantees of course.

Briefly, this is what I had to do:

Install these using your favourite package manager: libtool, xmms-dev, and libid3-3.8.3-dev (if you don't already have them).

Go to audiocoding.com, download the libfaad2 .tar.gz and unpack.

Look at README.linux in the libfaad2 directory. It just says to run 

$ autoreconf -vif

$ ./configure --with-mp4v2 --with-xmms --with-drm

$ make

$ sudo make install

Restart xmms and hope for the best.

---

### Post by disturbedite on 2007-12-02
why not just use audacious?  xmms has been dead for a long time and audacious has replaced it.

---

