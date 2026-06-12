---
title: "GpsDrive installation .deb Error/ CMake Error"
date: 2008-09-08
forum: General Help
---

### Post by insanity54 on 2008-09-08
Lately I've been experimenting with gps software, and I thought I would try GpsDrive from [http://www.gpsdrive.de/](http://www.gpsdrive.de/) because it looked like a handy tool for gps navigation on linux. 

I have been trying to install the latest version of Gps drive for my computer. I am running Ubuntu Hardy Heron. First I checked synaptic. GpsDrive is there, but unfortunately it is out of date. I downloaded and installed it, but it is missing features and functionality that the newest version offers.

Next I downloaded the latest .deb package from the gpsdrive website. I was unnable to install it because I received the following error:

```
Error: Dependency is not satisfiable: libboost-thread1.34.1
```

I thought, "easy fix right? just run 'sudo apt-get install libboost-thread1.34.1"

No, that didn't work. I already had libboost-thread1.34.1!

I searched the web a bit and from [this thread]("http://ubuntuforums.org/showthread.php?t=878813") I thought that the install could be requiring some dev packages of libboost-thread as well.

I installed a couple dev packages of libboost-thread (I don't think that was the right thing to do) It didn't help, the deb package still needed "libboost-thread1.34.1" which is already installed!

Is this fixable by me, or is it a bug that I can't do anything about?

I decided to move on and attempt compiling from source. I've been using ubuntu for over a year and never actually compiled something from source, so I thought this would be a good time to try it. I downloaded gpsdrive-2.10pre6.tar.gz from the GpsDrive website, and with guidance from the README, I did the following:

(Extracted tarball)

```

$ cd gpsdrive
$ mkdir build
$ cd build
$ cmake -DCMAKE_BUILD_TYPE=debug
The program 'cmake' is currently not installed.  You can install it by typing:
sudo apt-get install cmake
bash: cmake: command not found

```

I installed cmake with apt-get, and figured out (with $cmake --help) that I had to point cmake to 'CMakeCache.txt'

```
$ cmake -DCMAKE_BUILD_TYPE=debug ..
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Looking for include files HAVE_LIBINTL_H
-- Looking for include files HAVE_LIBINTL_H - found
-- Looking for dgettext
-- Looking for dgettext - found
-- Found Gettext: built in libc
-- Looking for include files HAVE_CRYPT_H
-- Looking for include files HAVE_CRYPT_H - found
-- Looking for include files HAVE_LINUX_INET_H
-- Looking for include files HAVE_LINUX_INET_H - not found.
-- Looking for include files HAVE_UNISTD_H
-- Looking for include files HAVE_UNISTD_H - found
-- Looking for include files HAVE_LOCALE_H
-- Looking for include files HAVE_LOCALE_H - found
-- Can not find gtk includes
CMake Error: Could NOT find GTK2
CMake Error: Could not find XML2
-- Configuring done
```

I received two errors-- "CMake Error: Could NOT find GTK2", and "CMake Error: Could not find XML2"

I searched the web some more and found [this forum thread]("http://vegastrike.sourceforge.net/forums/viewtopic.php?t=11582&sid=26f023a6fffd8efdbc2f08f1c8fe55f9") from another website, in which a user says that, "...ubuntu insists on shipping this outdated cmake and it really aggravates me..."

That makes me think, maybe my cmake (2.4.7-build1) is outdated and is causing the problem with compiling from tarball? Is cmake ok, it just needs to be directed to GTK2 and XML2? I really have no idea, but it's all I have to go off of, since my google-fu has hit a dead end.

Does anyone know a fix/ workaround for either the .deb package dependency or compiling from tarball?

---

### Post by insanity54 on 2008-09-09
bump

---

### Post by insanity54 on 2008-09-10
bump

---

### Post by Johees on 2009-04-19
Hey,
This thread seems dead, but here goes:

I seem to have the same problem with the outdated cmake.
I'm trying to install the newest version of QLandkarteGT, simply because I liked QLandkarte more than GpsDrive. QLandcarteGT also has to be compiled from source from a tar ball.

This is the error I receive when I try to make CMake build the app from source:

[FONT="Courier New"]> WARNING: This project requires version 2.6.0 of CMake.  You are
 running version 2.4.7.


 CMake Error: Qt qmake not found!

 CMake Error: You have requested backwards compatibility with CMake
 version 1.2 or earlier. This version of CMake only supports backwards
 compatibility with CMake 1.4 or later. For compatibility with 1.2 or
 earlier please use CMake 2.0

 CMake Error: You have requested backwards compatibility with CMake
 version 1.2 or earlier. This version of CMake only supports backwards
 compatibility with CMake 1.4 or later. For compatibility with 1.2 or
 earlier please use CMake 2.0
[/FONT]

And I just installed cmake today using "apt-get install cmake", and that gave me version 2.4.7. In synaptic that is also the newest version.

What to do?
can I download the source code for CMake 2.6.0 and try to compile that?
I have been using Linux for a couple of months now but have not really moved beyond "point-and-click" manoeuvres.

Thanks for any help

---

### Post by insanity54 on 2009-04-19
Yeah yeah, this thread died. I ended up giving up on GPS drive, and I found TangoGPS, which installed and worked perfect for what I needed it for.

Anyway, If you need a newer version of cmake, you can get one through Synaptic, without having to bother with tarballs (eww, messy!) :P

I'm assuming you're still using Hardy Heron as it says in your profile.

[LIST]
[*]First, open Synaptic.
[*]Go to Settings>Repositories
[*]Click the Updates Tab
[*]Under, "Ubuntu Updates" check the, "Unsupported Updates (hardy-backports)" box.
[*]Push the "Close" button.
[*]In Synaptic, search for "cmake"
[*]If you already have cmake, then select the package and go to Package>Force Version, and select version 2.6.2
[*]If you don't have cmake yet, install it then do the above instruction.
[/LIST]

I'm assuming it will work, even though it's not 2.6.0 like the one QLandkarteGT wants.

---

### Post by Johees on 2009-04-21
Hey.
Thank you, I got the newest version of Cmake now. 
But I haven't successfully finished the installation though.

I'm now stuck here:
[http://ubuntuforums.org/showthread.php?p=7114281#post7114281](http://ubuntuforums.org/showthread.php?p=7114281#post7114281)

Anyway, at least this solved the "newest version of Cmake" issue.:)

J

---

