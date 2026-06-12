---
title: "Scanner not recognized"
date: 2020-05-09
forum: Hardware
---

### Post by lwalper on 2020-05-09
I'm still struggling to get my scanner to work. I had hoped that the update to 20.04 would correct the problem. I've plugged the scanner into the USB port and opened Document Scanner. It recognizes the scanner (that's progress from before), but tells me that I need to install drivers. I have the Epson drivers (last updated 2011) and have unzipped the tarball into a folder with this list of files.

```
iscan-2.10.0$ ls
ABOUT-NLS     config.h.in   debian      intl           Makefile.am    po
aclocal.m4    config.rpath  depcomp     iscan.spec     Makefile.in    README
AUTHORS       config.sub    doc         iscan.spec.in  missing        README.ja
backend       configure     frontend    lib            mkinstalldirs  sanei
ChangeLog     configure.ac  include     libltdl        NEWS           utils
compile       COPYING       INSTALL     ltmain.sh      NEWS.ja
config.guess  COPYING.LIB   install-sh  m4
```

Where do I go from here? Just click on INSTALL? Doesn't seem right from everything else I've seen installed here.

---

### Post by Holger_Gehrke on 2020-05-09
This look like source code to me. INSTALL is probably a text file explaining how to compile this stuff and what libraries need to be installed to get it to work. If you've got the C compiler,  make and all the libraries it needs, it should be as simple as './configure && make && sudo make install'. Alternatively you could try vuescan from hamrick.com.

Holger

---

### Post by lwalper on 2020-05-09
OK, so I've downloaded the VueScan deb file and unzipped it. Now what? The website says "In the window that opens, double click VueScan to                                         install it."


I don't see the VueScan file to double click??

---

### Post by CelticWarrior on 2020-05-09
.deb files arfe not to be "unzipped". Double-clicking it should open the software store app. Then, just click install.
All Epson drivers are already packaged for Debian/Ubuntu as, of course, .deb files. There's no point in downloading and compiling the source code.

---

### Post by lwalper on 2020-05-09
OK, so I've downloaded the VueScan deb file and unzipped it. Now what? The website says "In the window that opens, double click VueScan to                                         install it."

The .deb file is in my downloads folder. I double click on it and am prompted to extract it. No software store app???

And in the unzipped .deb file I don't see the VueScan file to double click as instructed on the VueScan web site. Again?? Is there a command line to install the .deb file?

---

### Post by lwalper on 2020-05-09
I go to my downloads folder, locate the .deb file --
ls
control.tar.gz              iscan_2.10.0-1.tar.gz
data.tar.xz                 iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm
debian-binary               userg_revG_e.pdf
iscan-2.10.0                    **vuex6497.deb**

and in terminal enter
**sudo dpkg -i /vuex6497.deb**

which returns the error
**dpkg: error: cannot access archive '/vuex6497.deb': No such file or directory**

---

### Post by CelticWarrior on 2020-05-10
Why are you running 'sudo dpkg -i /vuex6497.deb'? The "/" there is wrong, obviously. Were you thinking perhaps of "./<package>" which by the way isn't needed?
And a .deb file *not* having association with at least ONE package manager is symptomatic of other problems, something not really surprising, considering this thread.

---

### Post by Artim on 2020-05-10
It's in your downloads folder because you downloaded it from some web site, I assume (correct me if I'm wrong).  The files you need are in the Ubuntu repositories, no need to get them from someplace else.  Search for the driver you need in the Software Center and use that one.

Also, in case I'm wrong about the downloaded deb, consider booting to a different kernel.  20.04 upgrades the kernel and borks some drivers.

---

### Post by lwalper on 2020-05-11
> **CelticWarrior said:**
> Why are you running 'sudo dpkg -i /vuex6497.deb'? The "/" there is wrong, obviously. Were you thinking perhaps of "./<package>" which by the way isn't needed?
And a .deb file *not* having association with at least ONE package manager is symptomatic of other problems, something not really surprising, considering this thread.

Since I know virtually -0- about installing software in a Linux box, I used the "/" because that was the string given on the vuescan website for installing the .deb file.

---

### Post by lwalper on 2020-05-11
> **Artim said:**
> It's in your downloads folder because you downloaded it from some web site, I assume (correct me if I'm wrong).  The files you need are in the Ubuntu repositories, no need to get them from someplace else.  Search for the driver you need in the Software Center and use that one.

I *would* use drivers from the repository if VueScan were listed there, but sadly, I don't seem to be able to locate it there. I've also checked synaptic. No joy. There are some ..sane files reported as already having been installed. Since I couldn't get Vuescan to install I did install Xsane which didn't work either. The scanner is recognized as being plugged into the USB port, but the software doesn't want to play nicely with it.

---

### Post by slickymaster on 2020-05-11
*Thread moved to **Hardware**.*

---

### Post by lwalper on 2020-05-12
[Saw this comic strip today]("https://dilbert.com/strip/2020-05-10"). Sort of mirrors my experience trying to get this scanner to work.

---

