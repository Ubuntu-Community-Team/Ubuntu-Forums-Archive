---
title: "[SOLVED] Autoclean removed LibGL.so.1"
date: 2008-11-18
forum: General Help
---

### Post by Duranxl on 2008-11-18
So after running sudo apt-get autoremove to clean some stuff up (250mb~), i'm getting 
```
 error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

``` while starting OpenGL games/apps.
The libGL.so.1 is definitely there in /usr/lib and lib32/64..?

I installed the newest 180.08 nvidia drivers to no avail..! 
The GPU & driver works fine though, compiz works great too.
Any help?
thanks

GPU: 8600M GT
Intrepid 64-bit

---

### Post by Yellow Pasque on 2008-11-18
So the file is in /usr/lib and is not a broken link? What's the output of:
```
cd /usr/lib; ls -la | grep GL
```

---

### Post by Duranxl on 2008-11-18
There's a LibGL.so in /usr/lib and in /usr/lib64, they are not broken links (no cross), they all point to LibGL.so.180.08

There's no LibGL.so.1 in lib32 though..so i copied the LibGL.so.180.08 to lib32 and renamed it.
Now i get some a "wrong ELF class: ELFCLASS64".
I think this means that i've copied a 64bit libGL version into the 32bit folder..I guess autoclean removed the file because it's not needed by a 64bit OS? It looks like the programs search for a 32bit file.

This is the result of the command:
```
lrwxrwxrwx   1 root root       19 2008-11-18 20:32 libGLcore.so.1 -> libGLcore.so.180.08
-rwxr-xr-x   1 root root 18145352 2008-11-18 20:32 libGLcore.so.180.08
lrwxrwxrwx   1 root root       16 2008-07-16 23:47 libGLEW.so.1.5 -> libGLEW.so.1.5.0
-rw-r--r--   1 root root   273488 2008-02-11 17:49 libGLEW.so.1.5.0
-rw-r--r--   1 root root      653 2008-11-18 20:32 libGL.la
lrwxrwxrwx   1 root root       10 2008-11-18 20:32 libGL.so -> libGL.so.1
lrwxrwxrwx   1 wp   wp         15 2008-11-18 21:07 libGL.so.1 -> libGL.so.180.08
-rwxrwxrwx   1 root root   900408 2008-11-18 21:05 libGL.so.180.08
-rw-r--r--   1 root root   935154 2008-10-22 06:01 libGLU.a
lrwxrwxrwx   1 root root       11 2008-11-04 14:08 libGLU.so -> libGLU.so.1
lrwxrwxrwx   1 root root       20 2008-11-04 14:08 libGLU.so.1 -> libGLU.so.1.3.070200
-rw-r--r--   1 root root   465528 2008-10-22 06:01 libGLU.so.1.3.070200
```

Maybe worth mentioning: i also removed some unimportant stuff with..
[http://doc.ubuntu-fr.org/maintenir_systeme](http://doc.ubuntu-fr.org/maintenir_systeme)

---

### Post by Duranxl on 2008-11-18
It seems there's more files missing.......arg
```
wp@wp-laptop:~/google-earth$ ./googleearth-bin
./googleearth-bin: error while loading shared libraries: libQt3Support.so.4: cannot open shared object file: No such file or directory
```

anyway to get these back...?

---

### Post by Yellow Pasque on 2008-11-18
/usr/lib64 is just a link to /usr/lib (your main library folder on a 64-bit OS)
As you've discovered, /usr/lib32 should only contain 32-bit libs.

If Google Earth is a 32-bit program, it will look for libs in /usr/lib32, so to figure out if it's a 32-bit program:
```
file ~/google-earth/google-earth-bin
```

Also, you can see what libs it's linked to with the ldd command
```
ldd ~/google-earth/google-earth-bin
```

---

### Post by Duranxl on 2008-11-18
Thanks, Google earth is indeed 32bit.
Here's the list of 'dependencies'
```
linux-gate.so.1 =>  (0xf7f6b000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7f42000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7e54000)
	libQtCore.so.4 => /usr/lib32/libQtCore.so.4 (0xf7c25000)
	libQtGui.so.4 => /usr/lib32/libQtGui.so.4 (0xf7322000)
	libQt3Support.so.4 => not found
	libQtNetwork.so.4 => /usr/lib32/libQtNetwork.so.4 (0xf7221000)
	libQtXml.so.4 => /usr/lib32/libQtXml.so.4 (0xf71dd000)
	libQtSql.so.4 => not found
	libgoogleearth_lib.so => not found
	libm.so.6 => /lib32/libm.so.6 (0xf71b6000)
	libc.so.6 => /lib32/libc.so.6 (0xf7058000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf703f000)
	/lib/ld-linux.so.2 (0xf7f6c000)
	libbase.so => not found
	libge_net.so => not found
	libgeobase.so => not found
	libz.so.1 => /usr/lib32/libz.so.1 (0xf7028000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf7022000)
	librt.so.1 => /lib32/librt.so.1 (0xf7018000)
	libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf6f61000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf6f5d000)
	libaudio.so.2 => /usr/lib32/libaudio.so.2 (0xf6f45000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf6f1f000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf6f15000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf6efd000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf6ef3000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6ee9000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6ee2000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf6e6c000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf6e3e000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6e2f000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6d40000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf6d16000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf6cc5000)
	libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf6c9d000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf6c9a000)
	libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf6c97000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf6c7e000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6c79000)
```

As you can see, some files have been removed by the autoremove..
Is there any way to get them back? I've no idea to what package the files belong etc..

---

### Post by Yellow Pasque on 2008-11-18
Chances are that you never had the 32-bit libs. If you need 32-bit libraries, use getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

BTW, if you want to see exactly what autoremove took out, you can examine /var/log/dpkg.log

getlibs will be able to get the Qt stuff, but I doubt it will be able to get the libs for google earth. How did you install, G.E., from the medibuntu .deb's?

---

### Post by Duranxl on 2008-11-18
The problem is, all these programs (like google earth) have always worked...until i ran sudo apt-get autoremove.
So yes, I did have the 32bit files before..
I installed googleearth via .deb.
But it's just not google earth:(.

There's nothing about 'libGL.so.1"  in the log.
edit: i know it says 'autoclean' in the title, but I meant 'autoremove' 

Getlibs actually found some files:
```
The following i386 packages will be installed:
libqt4-qt3support
libqt4-sql
```

However, now google earth also comes up with:
```
libGL.so.1: cannot open shared object file: No such file or directory
```

So i tried:
```
wp@wp-laptop:~/google-earth$ getlibs -l libGL.so.1
libGL is installed from video drivers, please install or reinstall your video drivers
```

What now:confused:.. My nvidia display driver works just fine..
thanks

---

### Post by Duranxl on 2008-11-18
So i 'unpacked' the nvidia installer .run and found a lib32 folder with the files i needed. (libGL.so.1) etc..
So i copied them, but now i get "Segmentation fault" instead of file not found..
ARG! I thought autoremove was safe........

---

### Post by Duranxl on 2008-11-18
i'm confused.
I just did another sudo apt-get update and it found some libxml files..
I installed it and..for some reason all my problems have disappeared. I've no idea why, because i already did apt-get update 100x after i got the problem..
I don't understand linux..:S

Edit; none of the files in lib32 have changed after the update...or lib..
The update was called:libxml2

---

### Post by Duranxl on 2008-11-28
WTf, the problem has returned again after updating the kernel (just via update manager :confused::confused::confused::confused::confused:)
Google earth etc have stopped working once again...many missing libraries:S

---

### Post by Duranxl on 2008-11-28
Okai, i think i solved the problem for good now.
I needed to install NVIDIA*.pkg2.run instead of NVIDIA*.pkg0.run
I find it weird that it is assumed that everyone knows this..i figured pkg0.run would open pkg1, then pkg2...like a rar file..

Nothing in the readme either, how was i supposed to know?

---

### Post by Yellow Pasque on 2008-11-29
You should probably mark the thread solved.
> Nothing in the readme either, how was i supposed to know?
I would expect better documentation from "professional" developers, but this is nvidia we're talking about so...

---

