---
title: "Need help getting Canon Pixma iP90v printer to work"
date: 2010-04-03
forum: Hardware
---

### Post by Jammanuser on 2010-04-03
Hello,
I am trying to get my Canon Pixma iP90v printer to work in Ubuntu. Currently running two versions of Ubuntu (8.10 64 bit and 9.10 32 bit), and I need to get it working in both.

Please help.

Thanks in advance.

---

### Post by IcarusR on 2010-04-03
download driver from canon website

[http://software.canon-europe.com/software/0027214.asp?model=]("http://software.canon-europe.com/software/0027214.asp?model=")

You will need to install alien & use it to install.
For info on alien type in a terminal

```
man alien
```

Alternatively there is TurboPrint, which is commercial software with a free trial.

[http://www.turboprint.info/]("http://www.turboprint.info/")

---

### Post by speedygeo on 2010-04-03
> **Jammanuser said:**
> Hello,
I am trying to get my Canon Pixma iP90v printer to work in Ubuntu. Currently running two versions of Ubuntu (8.10 64 bit and 9.10 32 bit), and I need to get it working in both.

I use the Canon driver included in Kubuntu (for ubuntu is the same) for the BJC-8200 or for PIXMA iP 2000. The second is the best for colors.

---

### Post by Jammanuser on 2010-04-04
Thanks guys. :)
I had actually already downloaded that driver, and downloaded/installed/ran alien already before creating this thread, as per the info in [this thread]("http://ubuntuforums.org/showthread.php?t=662002"). Unfortunately, though, like the guy in that thread, alien gave me the message that it wouldn't work in 64 bit (this was in Ubuntu 8.10 64 bit). So that is why I'm looking for a different solution. Also, after installing Ubuntu 9.10 32 bit, I went ahead and tried to do:

```
sudo apt-get install alien
```

in the Terminal. But received a message saying the package could not be found. So that's on hold right now too...

-Jam Man

:guitar:

---

### Post by IcarusR on 2010-04-04
For the 64bit, once alien has converted to deb, you could 'force' the architecture to install.
```
dpkg -i --force -architecture /path/to/your.deb
``` 

I saw a thread yesterday talking about doing this on these drivers for 64bit, but can't find it now !

32bit.. are you in the same directory as the .rpm when you run alien ? Or give the path to it.

Another idea.. download & compile the source.

---

### Post by Jammanuser on 2010-04-04
> **IcarusR said:**
> For the 64bit, once alien has converted to deb, you could 'force' the architecture to install.
```
dpkg -i --force -architecture /path/to/your.deb
``` 

Thanks. But I couldn't get alien to convert the .rpm file to a .deb. Here is the output after I run 

```
sudo alien -d cnijfilter-ip90-2.70-1.i386.rpm
```

in the terminal:
> 
Warning: Skipping conversion of scripts in package cnijfilter-ip90: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/cnijfilter-ip90
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: couldn't find library libgtk-1.2.so.0 needed by debian/cnijfilter-ip90/usr/local/bin/printuiip90 (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: `cnijfilter-ip90-2.70': No such file or directory
And all it did was create a folder called "cnijfilter-ip90-2.70" which contains some (possibly all) of the files in the .rpm.
> 
I saw a thread yesterday talking about doing this on these drivers for 64bit, but can't find it now !

**32bit.. are you in the same directory as the .rpm when you run alien ? Or give the path to it.**

Another idea.. download & compile the source.
Well, the thing is I couldn't get alien to install in 32 bit of Ubuntu 9.10. It said it couldn't find the package.

---

### Post by IcarusR on 2010-04-09
To get missing file try installing these two...

```
sudo apt-get install libglib1.2-dev libgtk1.2-dev
```

---

### Post by Jammanuser on 2010-04-09
> **IcarusR said:**
> To get missing file try installing these two...

```
sudo apt-get install libglib1.2-dev libgtk1.2-dev
```

Ok, I installed them. Now what?

Thanks for the help.

-Jam Man

:guitar:

---

### Post by Jammanuser on 2010-04-09
Ok, tried the alien command again. Still the same error.

---

### Post by IcarusR on 2010-04-09
Is libglib1.2 installed ?

```
sudo apt-get install libgtk1.2
```

---

### Post by Jammanuser on 2010-04-09
Yep.
The newest version is already installed.

---

### Post by IcarusR on 2010-04-11
Sorry no further ideas.

---

### Post by Jammanuser on 2010-04-14
Ok, I got alien to finally install on ubuntu 9.10 32 bit.
Now I'm going to go try to convert the .rpm to .dev.

Hold on to your hats...

-Jam Man

:guitar:

---

### Post by Jammanuser on 2010-04-14
Nice! It worked. :) I converted to .deb, then installed the package.
Now time to find out if the printer will print...

---

### Post by Jammanuser on 2010-05-10
Unfortunately, it didn't. :(

Go [here]("http://ubuntuforums.org/showpost.php?p=9274161&postcount=2") to read what happened next.

-Jam Man

:guitar:

---

