---
title: "Need help installing VLC"
date: 2005-11-06
forum: General Help
---

### Post by babyboy77 on 2005-11-06
Can some one help me how i should install that file
i searched other places and they told me to type in "sudo .." but i couldnt get it to work and the file i am trying to install is vlc player

---

### Post by RAOF on 2005-11-06
If you are just trying to install VLC player, might I suggest you use synaptic/apt-get?

System->Administration->Synaptic package manager

Search for "vlc".  Select the vlc package for installation.  Click "apply".  Watch as synaptic downloads, installs, and sets up VLC for you.

There's a help page for installing stuff [here]("http://help.ubuntu.com/starterguide/C/ch02.html").

---

### Post by babyboy77 on 2005-11-06
ty, i was able to get the vlc player working but the video wouldnt work plz help

---

### Post by RAOF on 2005-11-07
Have you tried the [sound and video howto]("http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies")?

---

### Post by babyboy77 on 2005-11-08
yes but still i can see the picture but cant hear anything, and any help installing tar.gz

---

### Post by RAOF on 2005-11-08
But sound works in general?  Ok.  Building the .tar.gz is reasonably complex, and definitely not the recommended way to do things.  Try other media players on your file first (totem, mplayer, whatever).

Installing from the .tar.gz will be a pain.  You'd **really** be better off trying something else.  This should be an absolute last resort.

---

### Post by Bachstelze on 2005-11-08
Is there a HowTo or something about compiling it yourself ? I'd really like to have it read my MKV files too so I have to use only ONE player for everything.

---

### Post by RAOF on 2005-11-08
VLC has to be the most complicated to configure build I've ever tried to do (and it didn't work, but that's because I'm running Breezy64).

There **is** a compile howto on the VLC site.  That you can find [here]("http://developers.videolan.org/vlc/nix-compile.html").  However, I'll point you to the sample ./configure line:
> ./configure --enable-x11 --enable-xvideo --disable-gtk --enable-sdl --enable-ffmpeg --with-ffmpeg-mp3lame --enable-mad --enable-libdvbpsi --enable-a52 --enable-dts --enable-libmpeg2 --enable-dvdnav --enable-faad --enable-vorbis --enable-ogg --enable-theora --enable-faac --enable-mkv --enable-freetype --enable-fribidi --enable-speex --enable-flac --enable-livedotcom --with-livedotcom-tree=/usr/lib/live --enable-caca --enable-skins --enable-skins2 --enable-alsa --disable-kde --disable-qt --enable-wxwindows --enable-ncurses --enable-release

It's complex.

---

### Post by kingsidy on 2005-11-08
the easiest way to install is to get it from the "add application" from the applications menu. just go to sound and slelect "VLC for GTK" and install. you'll get both picture and sound

---

### Post by Dotrig on 2005-11-08
Do this one:

sudo apt-get install vlc-*

---

### Post by Bachstelze on 2005-11-08
> **kingsidy]the easiest way to install is to get it from the "add application" from the applications menu. just go to sound and slelect "VLC for GTK" and install. you'll get both picture and sound[/QUOTE]

The problem with this is that whoever built the Ubuntu VLC package didn't enable the MKV playback. S&#181 said:**
> checking for C compiler default output file name... configure: error: C compiler cannot create executables

I think I need to install other packages but I dunno which ones. Can anyone help me here ?

---

### Post by ljamie82 on 2005-11-08
have you tried to go into synaptic and search for JUST vlc?  there's alot of extra plugins that aren't installed by default that you can manually choose to install.

---

### Post by babyboy77 on 2005-11-08
well tried every thing that everyone of u told me but none of them would work,
so i have the source code and its in tar.gz format
so need help installing that and my sound does work with other things.

---

### Post by Bachstelze on 2005-11-08
HEY ! I wondered something. Ubuntu is based on Debian, right ? So is there a way to install the Debian VLC package instead of the non-mkv-compatible Ubuntu one ?

---

### Post by RAOF on 2005-11-08
[QUOTE=babyboy77]well tried every thing that everyone of u told me but none of them would work,
so i have the source code and its in tar.gz format
so need help installing that and my sound does work with other things.[/QUOTE]
What extra vlc plugins do you have?  Specifically, do you have one of:
[list]
[*]vlc-plugin-alsa
[*]vlc-plugin-esd
[*]vlc-plugin-sdl
[/list]
installed?  Try installing them all, and try each of them as the preferred audio output of VLC.  I think that's under preferences->audio.  You may have to check "show advanced settings"

---

### Post by acorrigan on 2005-11-08
also, what about it being ugly as heck?  (bit tornado is too)  I looked through bugzilla but couldn't find anything regarding either.  I checked synaptic and I don't have an old version.  The lack of MKV support is also not good.

Is a bug report appropriate? (I'm hesitant to since I'm a noob)

---

### Post by RAOF on 2005-11-08
[QUOTE=HymnToLife]HEY ! I wondered something. Ubuntu is based on Debian, right ? So is there a way to install the Debian VLC package instead of the non-mkv-compatible Ubuntu one ?[/QUOTE]
Actually, you could probably compile the Ubuntu source package for yourself, and change the configure options.  To do that, you would go:
```
cd ~
mkdir Temp
cd Temp
sudo apt-get build-dep vlc
sudo apt-get source vlc
```
The first will install all the build-dependencies, the second will get the source for the VLC package.
Now, under your current directory should have a directory vlc-0.8.4-svn20050920.  In that directory will be a "debian" directory.  Edit the "rules" file in there - that contains all the configure options for the VLC that the package will build.  Find the line "--disable-mkv", and change it to "--enable-mkv".

Now, do
```

cd ~/Temp
sudo apt-get source -b vlc

```
This will build the VLC packages, with your new configure options.  You'll end up with a bunch of .debs in the Temp directory.

Finally
```

sudo dpkg -i *.deb

```
will install all the VLC packages.

---

### Post by acorrigan on 2005-11-08
that's very helpful, thanks a lot!

---

### Post by Bachstelze on 2005-11-10
Dammit, it still won't read mkv files...

---

### Post by RAOF on 2005-11-10
Are you sure you modified the debian/rules file to change "--disable-mkv" to "--enable-mkv" before building the packages?

I don't have any mkv files to check, but I think I built mine with mkv support...

---

### Post by Nrvnqsr on 2005-11-17
I followed all the steps until I tried gedit the rules file, it just won't let me edit the file, is there anything I can do to edit the file?

---

### Post by RAOF on 2005-11-17
Yes.  The rules file will be owned by root, so you'll need to "sudo gedit debian/rules"

---

### Post by Nrvnqsr on 2005-11-19
hmm... appreciated that tip, now I have this new problem when compiling

> make[7]: Entering directory `/home/danny/Temp/vlc-0.8.4-svn20050920/modules/codec/ffmpeg'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../..   -DSYS_LINUX -I../../../include `top_builddir="../../.." ../../../vlc-config --cflags plugin ffmpeg` -Wsign-compare -Wall  -pipe -MT libffmpeg_plugin_a-ffmpeg.o -MD -MP -MF ".deps/libffmpeg_plugin_a-ffmpeg.Tpo" -c -o libffmpeg_plugin_a-ffmpeg.o `test -f 'ffmpeg.c' || echo './'`ffmpeg.c; \
then mv -f ".deps/libffmpeg_plugin_a-ffmpeg.Tpo" ".deps/libffmpeg_plugin_a-ffmpeg.Po"; else rm -f ".deps/libffmpeg_plugin_a-ffmpeg.Tpo"; exit 1; fi
ffmpeg.c:49:44: error: libpostproc/postprocess.h: No such file or directory
make[7]: *** [libffmpeg_plugin_a-ffmpeg.o] Error 1
make[7]: Leaving directory `/home/danny/Temp/vlc-0.8.4-svn20050920/modules/codec/ffmpeg'
make[6]: *** [all-modules] Error 1
make[6]: Leaving directory `/home/danny/Temp/vlc-0.8.4-svn20050920/modules/codec/ffmpeg'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/danny/Temp/vlc-0.8.4-svn20050920/modules/codec'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/home/danny/Temp/vlc-0.8.4-svn20050920/modules/codec'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/danny/Temp/vlc-0.8.4-svn20050920/modules'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/danny/Temp/vlc-0.8.4-svn20050920'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/danny/Temp/vlc-0.8.4-svn20050920'
make: *** [build-stamp] Error 2
Build command 'cd vlc-0.8.4-svn20050920 && dpkg-buildpackage -b -uc' failed.
E: Child process failed


is there something that I'm missing?

---

### Post by RAOF on 2005-11-19
Yes.  It looks like you may be missing libpostproc-dev.  You could run "sudo apt-get install libpostproc-dev" to get it.

---

### Post by Nrvnqsr on 2005-11-19
well, aside of libpostproc-dev is there any other lib packages that I should have, because I still get error when compiling? appreciated again.

> demux.c:36:32: error: ffmpeg/avformat.h: No such file or directory
In file included from demux.c:41:
ffmpeg.h:44: error: syntax error before ‘AVCodecContext’
ffmpeg.h:50: error: syntax error before ‘AVCodecContext’
ffmpeg.h:80: error: syntax error before ‘AVFrame’
make[7]: *** [libffmpeg_plugin_a-demux.o] Error 1
make[7]: Leaving directory `/home/danny/vlc-0.8.4-svn20050920/modules/codec/ffmpeg'
make[6]: *** [all-modules] Error 1
make[6]: Leaving directory `/home/danny/vlc-0.8.4-svn20050920/modules/codec/ffmpeg'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/danny/vlc-0.8.4-svn20050920/modules/codec'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/home/danny/vlc-0.8.4-svn20050920/modules/codec'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/danny/vlc-0.8.4-svn20050920/modules'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/danny/vlc-0.8.4-svn20050920'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/danny/vlc-0.8.4-svn20050920'
make: *** [build-stamp] Error 2
Build command 'cd vlc-0.8.4-svn20050920 && dpkg-buildpackage -b -uc' failed.
E: Child process failed


---

### Post by Bachstelze on 2005-11-19
it says

 demux.c:36:32: error: ffmpeg/avformat.h: No such file or directory


So I guess the package you need is something like "avformat-dev".


Anyway, I gave up on this. I converted my mkv files to avi :p

---

### Post by RAOF on 2005-11-20
[QUOTE=Nrvnqsr]well, aside of libpostproc-dev is there any other lib packages that I should have, because I still get error when compiling? appreciated again.[/QUOTE]
That ffmpeg file should be in the source download.  I don't know what went wrong.  Maybe you could try again, from the beginning?

---

### Post by Nrvnqsr on 2005-11-20
[QUOTE=RAOF]That ffmpeg file should be in the source download.  I don't know what went wrong.  Maybe you could try again, from the beginning?[/QUOTE]

well right now, I deleted the vlc source code package and redownload a new one from the repositories, I checked the ubuntu folder and the source package from the VLC site and both don't have avformat.h :(
and another thing, I'm using the K7 kernel on Turion64 so I don't think this might be and issue.

and another question, how do I print out a error report if any so we can clearly see what is the problem?

appreciated again

---

