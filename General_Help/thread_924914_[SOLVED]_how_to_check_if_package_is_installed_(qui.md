---
title: "[SOLVED] how to check if package is installed (quickly)"
date: 2008-09-20
forum: General Help
---

### Post by pwaugh on 2008-09-20
Let's say I want to see if I have installed the "bridge-utils" package previously (say with sudo apt-get bridge-utils).

I know I can start up the Synaptic Package Manager, and search for it and see if it is "checked", but is there a quick way to do it from the terminal?

Also, is there a way I can tell how a package was installed (ie. with apt-get, aptitude, or manually)?

Thanks,

Patrick

---

### Post by iaculallad on 2008-09-20
On your terminal:

```
apt-cache policy bridge-utils
```

If it's installed, it will display the version installed, if it's not, it will display the lines of text below:
```

bridge-utils:
  Installed: (none)
  Candidate: 1.2-1build1
  Version table:
     1.2-1build1 0
        500 http://archive.ubuntu.com gutsy/main Packages

```

---

### Post by todak on 2008-09-20
In terminal: ```
whereis **packagename**
``` Of course, replace **packagename** with the, well, the name of the package! :lolflag: If the package is not installed, then the name of the package followed by a colon will be displayed. If it is installed, then a listing of directories will be displayed. Example: ```
dave@ubuntu:~$ whereis vlc
vlc: /usr/bin/vlc /usr/lib/vlc /usr/share/vlc /usr/share/man/man1/vlc.1.gz
``` shows package **vlc** is installed. ```
dave@ubuntu:~$ whereis foo
foo:
``` shows package **foo** is not installed.

---

### Post by Chris_82 on 2010-03-15
Hi there,

I realize that this is marked as solved but I have found out the following:
```
whereis wicd
wicd: /etc/wicd
```
but:
```
apt-get remove wicd
Package wicd is not installed, so not removed

```
so I conclude that whereis is not the right command to do the "is-this-installed" test..

I confirm that the following is the right way to do it:
```
apt-cache policy package_name
```

cheers,
rosch.

---

### Post by pbrane on 2010-03-15
One more way to check for installed packages...
```

dpkg -l | grep bridge-utils

```
-OR-
```

dpkg -l | grep bridge-utils | awk '{print $2, $3}'

```
the second version prints just the name and version of the package.
If the package is not installed nothing is printed to the terminal.

---

### Post by ratcheer on 2010-03-15
I use "aptitude show <package_name>". I assume apt-get would do the same thing, but I don't use it. Example:

```

aptitude show vlc
Package: vlc
State: installed
Automatically installed: no
Version: 1.0.2-1ubuntu2.1
Priority: optional
Section: universe/graphics
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 3,899k
Depends: vlc-nox (= 1.0.2-1ubuntu2.1), libaa1 (>= 1.4p5), libc6 (>= 2.8), libdbus-1-3 (>=
         1.0.2), libfreetype6 (>= 2.2.1), libfribidi0 (>= 0.10.9), libgcc1 (>= 1:4.1.1),
         libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.8.0),
         libnotify1 (>= 0.4.5), libnotify1-gtk2.10, libqtcore4 (>= 4.5.1), libqtgui4 (>=
         4.5.1), libsdl-image1.2 (>= 1.2.5), libsdl1.2debian (>= 1.2.10-1), libstdc++6 (>=
         4.2.1), libtar, libvlccore2 (>= 1.0.0~rc1), libx11-6, libx264-67 (>=
         1:0.svn20090502), libxcb-keysyms1 (>= 0.3.6), libxcb1, libxext6, libxinerama1,
         libxv1, libxxf86vm1, zlib1g (>= 1:1.2.3.3.dfsg), ttf-dejavu-core
Recommends: vlc-plugin-pulse (= 1.0.2-1ubuntu2.1)
Suggests: mozilla-plugin-vlc, videolan-doc
Conflicts: vlc-nox (< 0.9.2-1)
Replaces: vlc-nox (< 0.9.2-1)
Provides: mp3-decoder
Description: multimedia player and streamer
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4, DivX, MOV, WMV,
 QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia streams from various network
 sources. 
 
 VLC can also be used as a streaming server that duplicates the stream it reads and multicasts
 them through the network to other clients, or serves them through HTTP. 
 
 VLC has support for on-the-fly transcoding of audio and video formats, either for
 broadcasting purposes or for movie format transformations. Support for most output methods is
 provided by this package, but features can be added by installing additional audio plugins
 (vlc-plugin-pulse, vlc-plugin-sdl) or video plugins (vlc-plugin-sdl, vlc-plugin-ggi,
 vlc-plugin-svgalib). There is also a web browser plugin in the mozilla-plugin-vlc package.
Homepage: http://www.videolan.org/vlc

```Tim

---

### Post by reddot on 2010-09-13
Next command could be used:

```

apt-get install -s packagename

```

it will gives reply that package is already installed or will emulate install package process if not.

---

