---
title: "Help compiling MEKA"
date: 2008-10-25
forum: General Help
---

### Post by flatulant on 2008-10-25
Can somebody please help me compile MEKA, or at least point me to a .deb package?  Google does nothing.

---

### Post by ad_267 on 2008-10-25
From the sources.txt file:
> III. Compile for UNIX
 - You are smart guys, you can figure it out!
 - Install Allegro library, latest WIP.
   - [http://www.talula.demon.co.uk/allegro/wip.html#unstable](http://www.talula.demon.co.uk/allegro/wip.html#unstable)
   - $ ./configure --enable-static
   - $ make
   - $ make install
 - Install NASM
   - Get a package, or [http://nasm.sourceforge.net](http://nasm.sourceforge.net)
 - Install SEAL
   - Get a package, or [http://www.sonicspot.com/sealsdk/sealsdk.html](http://www.sonicspot.com/sealsdk/sealsdk.html)
 - Compile !
   - Use provided Makefile.
   - May have to edit some source code (unsure, will need to be worked out)
     - In sound/sound.h, may need to change <seal.h> by <audio.h>.
     - In Makefile, may need to change -lseal by -laudio.
 - Contact me thru the forum for any help. :)

You will need to install the liballegro4.2, liballegro4.2-dev, nasm, libseal1and  libseal-dev packages.

Then in a terminal use cd to change into the directory where you extracted the download. Then do:
```
cd srcs
make
make install
```

You might have to put a sudo in front of the last line to get it to install.

---

### Post by flatulant on 2008-10-25
> **ad_267 said:**
> From the sources.txt file:


You will need to install the liballegro4.2, liballegro4.2-dev, nasm, libseal1and  libseal-dev packages.

Then in a terminal use cd to change into the directory where you extracted the download. Then do:
```
cd srcs
make
make install
```

You might have to put a sudo in front of the last line to get it to install.

I did a cd into the srcs directory, and then tried to make, but I get this error

flatulant@flatulant-desktop:~/Music/srcs$ sudo make
./buildupd.exe
make: execvp: ./buildupd.exe: Permission denied
make: *** [obj/meka.o] Error 127

---

### Post by ad_267 on 2008-10-25
You shouldn't run make with sudo, only make install. You might have to delete the directory and re-extract it.

---

### Post by flatulant on 2008-10-25
Is there any chance that I can just get a .deb package, please?

---

### Post by ad_267 on 2008-10-25
You can download the compiled 0.70 version from the website and just extract it and run the meka.exe file. I tried compiling the 0.72 version but I'm just getting a whole lot of errors that seem to be problems with the code.

---

### Post by ad_267 on 2008-10-25
There's a debian package here: [http://www.smspower.org/forums/viewtopic.php?p=50791](http://www.smspower.org/forums/viewtopic.php?p=50791)

Another idea is to run MEKA through wine, according to the wine appdb it runs very well.

---

