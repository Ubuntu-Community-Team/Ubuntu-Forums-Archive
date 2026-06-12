---
title: "WMV doens't work anymore after update"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by i386DX on 2006-02-16
Since a update of the w32codecs and libdvd some wmv-files/streams doesn't work anymore. I don't know how to fix it.
When I try to open a tv-stream I always watch I get these errors:

Totem says: "Video codec 'MS WMV 9 (win32)' is not handled. You might need to install additional plugins to be ableto play some types of movies

VNC says: "Error Loading library WMVDMOD.DLL"

---

### Post by Statik on 2006-04-06
So, I'm still waiting for a solution to this. None of my ASFs in WMV8 are playing now. Says that wmvdmod.dll is not there or something, yet it is there. I even tried several sources, including my XP box to copy it over and none of them fix the problem. Any ideas?

Statik

---

### Post by VosaxAlo on 2006-04-08
Hi,

I have the same problem that I have posted in this thread:

[http://ubuntuforums.org/showthread.php?p=897246#post897246]("http://ubuntuforums.org/showthread.php?p=897246#post897246")

here you can download some WMV v.9 video clips to testing your installation

---

### Post by Statik on 2006-04-08
I tried them in browser, they work fine. I downloaded one and I get an error in Xine:
> 
The stream '/home/statik/Desktop/sub_14226.wmv' use an unsupported codec:
Video Codec: MS WMV 9 (win32)(WMV3)
Start playback anyway ?

> 
A problem occur while loading a library or a decoder:
wmvdmod.dll
MORE/QUOTE]

[QUOTE]
xine: found demuxer plugin: Elementary MPEG stream demux plugin
xine: found input plugin : file input plugin
video_decoder: no plugin available to handle 'Windows Media Video 9'
w32codec: decoder failed to start, Is 'wmvdmod.dll' installed?
w32codec: DMO_VideoDecoder failed! unknown codec 33564d57 / wrong parameters?
w32codec: DMO_VideoDecoder failed! unknown codec 33564d57 / wrong parameters?
xine: found demuxer plugin: ASF demux plugin
xine: found input plugin  : file input plugin


Thats the same thing I get from all of them. Unless its Windows Media 8, and then the 9 is an 8 at all the sections. That's it.

Statik

---

### Post by uross on 2006-04-21
The following worked for me (I'm using Xine)

add "deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main" to /etc/apt/sources.list

[FONT="Courier New"]$ sudo apt-get update[/FONT]

copy the gpg-key that apt-key complains about, and do the following

[FONT="Courier New"]$ gpg --recv-keys [PASTE_KEY_HERE]
$ gpg --armor --export  | sudo apt-key add -

$ sudo apt-get update
$ sudo apt-get install w32codecs
[/FONT]
that should about do it ...

by the way, it would be a good idea to add deCSS (this will make it possible to play 'proctected' DVDs)

[FONT="Courier New"]$ sudo apt-get install libdvdcss2[/FONT]

best regards, and good luck

---

### Post by Statik on 2006-04-21
Actually, the last w32codec update seemed to fix it . . . as of yesterday so far.

Statik

---

### Post by VosaxAlo on 2006-04-22
I have discovered that the problem is not in the w32codecs itself, but in the last version of him.

In my Synaptic package list, I have actually the following w32codecs versions:
[LIST]
[*]1:20050412-0.3 (unstable)
[*]1:20050412-0.0 (now)
[*]20050412-1plf4 (packages.freecontrib.org)
[/LIST]

The **unstable** version is the last one and if installed, the WMV video don't play anymore. So I have forced the **now** version and all function well.
Maybe in the **unstable** package is present a bug?

bye

---

### Post by Nunana on 2006-11-16
I had the problem with Xine and Kaffeine. I downloaded codecs from [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
and put the files in /usr/lib/win32
works fine for me.
(Ubuntu 6.06)

---

