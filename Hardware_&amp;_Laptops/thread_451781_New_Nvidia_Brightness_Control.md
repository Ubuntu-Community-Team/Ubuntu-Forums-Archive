---
title: "New: Nvidia Brightness Control"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by IntuitiveNipple on 2007-05-22
[COLOR="RoyalBlue"]**A new Gnome panel applet to control Nvidia screen brightness:**[/COLOR]

Having recently bought a Sony Vaio laptop that has a Nvidia GeForce Go 7600, and installed Feisty, I found the existing brightness control (using *sonypi* interface) doesn't work.

I also tried the Gnome panel applet **VaioLCD Brightness** but it relies on the *sonypi* device too.
 
The **smartdimmer** package is the solution. It is a command-line program that can get, set, and increment/decrement brightness on many Nvidia chipsets.

I wanted a Gnome panel applet just like VaioLCD Brightness to make the task easy, so I have hacked VaioLCD into a new package, **[COLOR="DarkGreen"]SmartDimmerApplet[/COLOR]**, that makes calls to the *smartdimmer* program to adjust brightness.

This works with (at least) **Feisty** and **Gutsy**, and on **32-bit** and **64-bit** Intel/AMD architectures. If you have it working on other architectures please let us know.

To use it, first install smartdimmer from the Ubuntu repositories using Synaptic, or using the command-line, and then test it to ensure it works with your Nvidia chipset:
```
$ sudo apt-get install smartdimmer
$ smartdimmer -g
SmartDimmer level: 21
$ smartdimmer -s 10
$ smartdimmer -i
$ smartdimmer -d
```
If it's working then you can go ahead and use my **SmartDimmer** applet for Gnome.

If necessary, install the packages required to build Gnome applets

You also need to install the automake package and, if it isn't created, a symlink:
```
$ sudo apt-get install automake1.9
$ if [ ! -e /usr/share/automake ]; then sudo ln -s /usr/share/automake-1.9 /usr/share/automake; fi

```

Then install the required library development headers:
```
$ sudo apt-get install libglade2-dev libpanel-applet2-dev
```
[INDENT]**Note:** I have installed so many packages for building software I'm no longer sure precisely which packages are required, so if you build on a clean system please make a note of each package you install and post the list here. I'll add it to this first article to help others.
[/INDENT]
Now follow these steps to build and install the applet:
[LIST=1]
[*]Download the source package attached to this article
[*]Extract the source package
[*]Configure the build environment (errors here will indicate additional packages need installing)
[*]Make the applet
[*]Install the applet
[*]Add the applet to a Gnome panel
[/LIST]
```
$ cd ~
$ wget http://ubuntuforums.org/attachment.php?attachmentid=33182&d=1179871063
$ tar -xzvf gnome-smartdimmer-1.0.tar.gz
$ cd gnome-smartdimmer-1.0
$  ./configure
$ make
$ sudo make install
```
Now right-click on a Gnome panel and choose "**Add to Panel...**", scroll to "**System & Hardware**" and then drag "**Nvidia SmartDimmer Brightness Control**" onto a panel.

To alter brightness click the panel icon and drag the slider.

---

### Post by p1977p on 2007-05-23
smartdimmer gives error: "init_nvclock() failed!"
i'm running xubuntu 64 bit on an AMD turion64 laptop with an onboard nvidia geforce card
pl help

---

### Post by IntuitiveNipple on 2007-05-23
> **p1977p said:**
> smartdimmer gives error: "init_nvclock() failed!"
i'm running xubuntu 64 bit on an AMD turion64 laptop with an onboard nvidia geforce card
pl help
**init_nvclock()** fails if an nvidia kernel driver isn't loaded, or a call to **probe_devices()** fails to detect a supported chipset.

I'd guess that the Nvidia chipset on your system isn't supported by smartdimmer, but as you don't say what the model number is, or give the PCI ID of the card (found using **lspci**) it's difficult to be precise.

---

### Post by dreadlord_chris on 2007-05-23
> **IntuitiveNipple said:**
> **init_nvclock()** fails if an nvidia kernel driver isn't loaded, or a call to **probe_devices()** fails to detect a supported chipset.

I'd guess that the Nvidia chipset on your system isn't supported by smartdimmer, but as you don't say what the model number is, or give the PCI ID of the card (found using **lspci**) it's difficult to be precise.

Ya, I also get the same error. Here's my relevant lspci line:
```

01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)

```

---

### Post by IntuitiveNipple on 2007-05-23
I posted details of my SmartDimmer applet [in the Nvidia Linux forums]("http://www.nvnews.net/vbulletin/showthread.php?t=91965"), and someone there replied with information that there is now an updated **nvclock** backend, which smartdimmer was derived from originally.

I'm going to get the latest nvclock source, build it, and then adapt my SmartDimmer applet to  use it. If it works for me I'll modify SmartDimmer so by default it'll try to use nvclock, and only if it isn't found will it try to use smartdimmer.

That way SmartDimmer can support both utilities, and use whatever the user's PC has installed.

---

### Post by IntuitiveNipple on 2007-05-24
I've tested **nvclock** and it also works to control the brightness. I've asked the author for a couple of minor command-line alterations to make it easier for SmartDimmer to use it.

Once that is done I'll add support for nvclock and post and updated SmartDimmer applet here.

I'm also investigating having the applet remember the last-used setting and automatically restore it when the applet starts.

---

### Post by p1977p on 2007-06-05
> **IntuitiveNipple said:**
> **init_nvclock()** fails if an nvidia kernel driver isn't loaded, or a call to **probe_devices()** fails to detect a supported chipset.

I'd guess that the Nvidia chipset on your system isn't supported by smartdimmer, but as you don't say what the model number is, or give the PCI ID of the card (found using **lspci**) it's difficult to be precise.

here's my lspci output:
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)

isn't there a way to alter the 'brightness' file in proc/acpi/video/VGA/LCD directly or through a script. i mean, use the sony/toshiba scripts that are present by default and modify them? that would require catching the relevant key combination. can this be done?

---

### Post by IntuitiveNipple on 2007-06-05
I modified the ACPI brightness scripts to call smartdimmer which helps when the laptop goes between AC and battery modes. You could do the same using nvclock.

The VaioLCD Brightness panel applet is hard-coded to use sonypi though, and as far as I can make out that only works with Intel-based graphics chipsets. For Nvidia, brightness control can't be done via sonypi.

---

### Post by frank58 on 2007-06-21
./configure gives errror  cannot find install-sh or install.sh in . ./.. ./../..

---

### Post by IntuitiveNipple on 2007-06-21
> **frank58 said:**
> ./configure gives errror  cannot find install-sh or install.sh in . ./.. ./../..

You need to install additional packages as I mentioned:
> **IntuitiveNipple said:**
> If necessary, install the packages required to build Gnome applets

You also need to install the automake package:
```
$ sudo apt-get install automake
```

[INDENT]**Note:** I have installed so many packages for building software I'm no longer sure precisely which packages are required, so if you build on a clean system please make a note of each package you install and post the list here. I'll add it to this first article to help others.
[/INDENT]

---

### Post by pVilaça on 2007-07-05
thanks IntuitiveNipple!

It's very good.
I need to install libpanel-applet2-dev and libglade2-dev too.

---

### Post by Eibod on 2007-07-16
The Nvidia Brightness applet does not show up in the control panel when I try to add it to the top control panel bar.  I am able to manipulate the brightness in terminal, but I can't figure out why the add to panel does not show the Nvidia controller.  Any suggestions would be helpful

---

### Post by IntuitiveNipple on 2007-07-16
> **Eibod said:**
> The Nvidia Brightness applet does not show up in the control panel when I try to add it to the top control panel bar.  I am able to manipulate the brightness in terminal, but I can't figure out why the add to panel does not show the Nvidia controller.  Any suggestions would be helpful
That sounds as if the installation is silently failing. Have you examined the log files /var/log/messages and ~/.xsession-errors for clues?

---

### Post by Eibod on 2007-07-19
I am a bit new to ubuntu and I am not exactly sure how to examine those directories.  I remember that it seemed to fail when I was trying to extract the file from the ubuntu website, not sure if this makes sense, but I need to get my computer hooked back up to the internet, I am not getting wireless here.

---

### Post by Eibod on 2007-07-23
So as I am trying to follow the directions I get an error problem.  The below is the terminal  output.  If you can let me know what I am doing wrong, that would be great.  The automake installed without a problem.  It could be that I just don't know what I am doing, anyways, thanks for the help.

ryan@eibod:~$ cd ~
ryan@eibod:~$ wget [http://ubuntuforums.org/attachment.php?attachmentid=33182&d=1179871063](http://ubuntuforums.org/attachment.php?attachmentid=33182&d=1179871063)
[1] 10759
ryan@eibod:~$ --01:43:38--  [http://ubuntuforums.org/attachment.php?attachmentid=33182](http://ubuntuforums.org/attachment.php?attachmentid=33182)
           => `attachment.php?attachmentid=33182.1'
Resolving ubuntuforums.org... 82.211.81.186
Connecting to ubuntuforums.org|82.211.81.186|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [   <=>                               ] 33,679        57.99K/s             

01:43:39 (57.82 KB/s) - `attachment.php?attachmentid=33182.1' saved [33679]

tar -xzvf gnome-smartdimmer-1.0.tar.gz
tar: gnome-smartdimmer-1.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
[1]+  Done                    wget [http://ubuntuforums.org/attachment.php?attachmentid=33182](http://ubuntuforums.org/attachment.php?attachmentid=33182)

---

### Post by pavelkul on 2007-07-24
You have not downloaded gnome-smartdimmer-1.0.tar.gz (try to do it with your browser, by clicking on link).

---

### Post by Eibod on 2007-07-25
So, now that I have downloaded the attachment, what do I do? I am not that familiar with opening files in Linux, nor programming in terminal, so if you could make it basic step by step, I would greatly appreciate it.

---

### Post by Fridericus on 2007-07-26
I managed to come this far before failing..

```
fredrik@fredrik-laptop:~/gnome-smartdimmer-1.0$ sudo make install
Making install in src
make[1]: Entering directory `/home/fredrik/gnome-smartdimmer-1.0/src'
make[2]: Entering directory `/home/fredrik/gnome-smartdimmer-1.0/src'
/bin/bash ../mkinstalldirs /usr/lib/gnome-applets
/bin/bash: ../mkinstalldirs: No such file or directory
make[2]: *** [install-libexecPROGRAMS] Error 127
make[2]: Leaving directory `/home/fredrik/gnome-smartdimmer-1.0/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/fredrik/gnome-smartdimmer-1.0/src'
make: *** [install-recursive] Error 1

```

Whats wrong?

This is what the **make** command output shows.
```
fredrik@fredrik-laptop:~/gnome-smartdimmer-1.0$ make
make  all-recursive
make[1]: Entering directory `/home/fredrik/gnome-smartdimmer-1.0'
Making all in src
make[2]: Entering directory `/home/fredrik/gnome-smartdimmer-1.0/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/fredrik/gnome-smartdimmer-1.0/src'
Making all in icons
make[2]: Entering directory `/home/fredrik/gnome-smartdimmer-1.0/icons'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/fredrik/gnome-smartdimmer-1.0/icons'
make[2]: Entering directory `/home/fredrik/gnome-smartdimmer-1.0'
make[2]: Leaving directory `/home/fredrik/gnome-smartdimmer-1.0'
make[1]: Leaving directory `/home/fredrik/gnome-smartdimmer-1.0'

```

And the ./configure command.
```
fredrik@fredrik-laptop:~/gnome-smartdimmer-1.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for perl5... no
checking for perl... /usr/bin/perl
checking for glib-genmarshal... /usr/bin/glib-genmarshal
checking for gdk-pixbuf-csource... /usr/bin/gdk-pixbuf-csource
checking for gconftool-2... /usr/bin/gconftool-2
checking for perl... /usr/bin/perl
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking what warning flags to pass to the C compiler... -Wall -Wunused -Wmissing-prototypes -Wmissing-declarations
checking what language compliance flags to pass to the C compiler... 
checking for pkg-config... /usr/bin/pkg-config
checking for libglade-2.0 >= 2.0.0 libpanelapplet-2.0 >= 2.0.0... yes
checking SMARTDIMMER_CFLAGS... -DORBIT2=1 -pthread -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0  
checking SMARTDIMMER_LIBS... -Wl,--export-dynamic -pthread -lglade-2.0 -lxml2 -lpanel-applet-2 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnome-keyring -lgconf-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lpangoft2-1.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lbonobo-2 -lbonobo-activation -lgmodule-2.0 -ldl -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0  
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas/ as install directory for schema files
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating icons/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
config.status: executing default-2 commands
config.status: executing default-3 commands

```


Sorry for all the text, but the super-bright screen is driving me insane. :)

---

### Post by pavelkul on 2007-07-29
May be you should check if "mkinstalldirs" link is linked with automake "mkinstalldirs" file (I have the same problem, because my automake folder is /usr/share/automak-1.10, not /usr/share/automake)

---

### Post by pavelkul on 2007-07-29
> **Eibod said:**
> So, now that I have downloaded the attachment, what do I do? I am not that familiar with opening files in Linux, nor programming in terminal, so if you could make it basic step by step, I would greatly appreciate it.

1. install automake (if you have not it) :
```
 sudo apt-get install automake
```
2. extract files from gnome-smartdimmer ...
```
tar -xvf gnome-smartdimmer-1.0.tar.gz
```
3. in gnome-smartdimmer-1.0 folder:
```

./configure
make
sudo make install

```

(maybe you need relink automake files (INSTALL, install-sh, missing and mkinstalldirs, if you have them not in /usr/share/automake/ folder) by unlink / link commands.

---

### Post by rikbrown2k on 2007-07-31
I was having the same configure problems, to clarify, here's how I fixed it:

The issue is that as said, the INSTALL/mkinstalldirs/etc files are linked to nonexistant files.

1. Make sure automake is installed
```
apt-get install automake
```

2. Find out where your automake files are
```
cd /
find -name mkinstalldirs
```
This will (eventually) return something like **usr/share/automake-1.10/mkinstalldirs**
So you know automake is in **/usr/share/automake-1.10/**

3. Delete all the broken links
```

cd <directory where you extracted the source code>
rm INSTALL install-sh missing mkinstalldirs
```

4. Make new links.  _Replace **/usr/share/automake-1.10/** with the directory you found in step 2_!
```
ln -s /usr/share/automake-1.10/INSTALL INSTALL
ln -s /usr/share/automake-1.10/install-sh install-sh
ln -s /usr/share/automake-1.10/missing missing
ln -s /usr/share/automake-1.10/mkinstalldirs mkinstalldirs
```

5. And configure!
```
./configure
```

Hope that clears it up to anyone confused.
and to the author: thanks A LOT for this panel applet, works a charm, just what I wanted :)

---

### Post by dgl6666 on 2007-08-07
> **p1977p said:**
> smartdimmer gives error: "init_nvclock() failed!"
i'm running xubuntu 64 bit on an AMD turion64 laptop with an onboard nvidia geforce card
pl help

I definitely don't believe it is a chipset problem.
I have a VGN-AR370 and had 7600 GT on it. Had the same problem of init_nvclock() failed when I used 64 bit. When I switched to 32bit Feisty, smartdimmer works just fine. The only thing is that when I give sudo smartdimmer -g, it crashes my touchpad mouse. But sudo smartdimmer -s X and smartdimmer -d and -i are working just fine. May be you can give it a try at 32 bit.

---

### Post by gotomah on 2007-08-18
hey rikbrown2k
thank you very much for the explanation of the whole thing.
I'm sure there's still out there a bunch of people like me that comes back to linux after a long while or just newcomers that can't figure out what is going on when the system does not respond the way you expect even following strict guidelines and such.
I've finally been able to do a **make** after all the linking.
thanks again:)

edit:
sorry i forgot to mention the huge help from IntuitiveNipple towards this bothering issue, thank you very much

---

### Post by st_easy_rider on 2007-09-23
Excellent !!!

I installed yet, and works great !!!

Thank you, so much

Cheers

Francisco

---

### Post by dustingram on 2007-10-24
Worked perfectly on a Sony VGN-FE690P with Gutsy. Thanks!

---

### Post by inakie on 2007-11-04
Works perfectly on my Sony Vaio VGN-FE31Z with NVidia GeForce Go 7600 under Ubuntu Gutsy, thanks!!

---

### Post by fortegas on 2007-11-05
I am using Gusty with Sony Vaio FZ21S and can't use brightness control.

I have the same problem. Any suggest?
smartdimmer -g
init_nvclock() failed!

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)

some fn keys are running (volumen keys)

---

### Post by pascalc on 2007-11-05
same error on gutsy for a vaio vgn-FZ21E with a gforce 8400 :
smartdimmer -g
init_nvclock() failed!

---

### Post by fortegas on 2007-11-06
I have install the applet but it is the same as the brightness applet of ubuntu gutsy it does not work. Please is there any solution to control brightness in vaio FZ21S?
Thanks you very much.
Fernando

---

### Post by isenalim on 2007-11-07
Hi!
Good job, works perfectly for my Vaio FE41M.

There is only one thing: the icon doesn't support transparent panels. It remains 100% opaque. I have tried to use the standard gnome-brightness icon but doesn't work either. Do you think it can be fixed somehow?
Thanks!

---

### Post by pwn on 2007-11-07
init_nvclock() failed!

Model # : Vaio AR590E

---

### Post by correoadm on 2007-11-28
> **IntuitiveNipple said:**
> [COLOR="RoyalBlue"]**A new Gnome panel applet to control Nvidia screen brightness:**[/COLOR]

Having recently bought a Sony Vaio laptop that has a Nvidia GeForce Go 7600, and installed Feisty, I found the existing brightness control (using *sonypi* interface) doesn't work.

I also tried the Gnome panel applet **VaioLCD Brightness** but it relies on the *sonypi* device too.
 
The **smartdimmer** package is the solution. It is a command-line program that can get, set, and increment/decrement brightness on many Nvidia chipsets.

I wanted a Gnome panel applet just like VaioLCD Brightness to make the task easy, so I have hacked VaioLCD into a new package, **[COLOR="DarkGreen"]SmartDimmerApplet[/COLOR]**, that makes calls to the *smartdimmer* program to adjust brightness.

This works with (at least) **Feisty** and **Gutsy**, and on **32-bit** and **64-bit** Intel/AMD architectures. If you have it working on other architectures please let us know.

To use it, first install smartdimmer from the Ubuntu repositories using Synaptic, or using the command-line, and then test it to ensure it works with your Nvidia chipset:
```
$ sudo apt-get install smartdimmer
$ smartdimmer -g
SmartDimmer level: 21
$ smartdimmer -s 10
$ smartdimmer -i
$ smartdimmer -d
```
If it's working then you can go ahead and use my **SmartDimmer** applet for Gnome.

If necessary, install the packages required to build Gnome applets

You also need to install the automake package and, if it isn't created, a symlink:
```
$ sudo apt-get install automake1.9
$ if [ ! -e /usr/share/automake ]; then sudo ln -s /usr/share/automake-1.9 /usr/share/automake; fi

```

Then install the required library development headers:
```
$ sudo apt-get install libglade2-dev libpanel-applet2-dev
```
[INDENT]**Note:** I have installed so many packages for building software I'm no longer sure precisely which packages are required, so if you build on a clean system please make a note of each package you install and post the list here. I'll add it to this first article to help others.
[/INDENT]
Now follow these steps to build and install the applet:
[LIST=1]
[*]Download the source package attached to this article
[*]Extract the source package
[*]Configure the build environment (errors here will indicate additional packages need installing)
[*]Make the applet
[*]Install the applet
[*]Add the applet to a Gnome panel
[/LIST]
```
$ cd ~
$ wget http://ubuntuforums.org/attachment.php?attachmentid=33182&d=1179871063
$ tar -xzvf gnome-smartdimmer-1.0.tar.gz
$ cd gnome-smartdimmer-1.0
$  ./configure
$ make
$ sudo make install
```
Now right-click on a Gnome panel and choose "**Add to Panel...**", scroll to "**System & Hardware**" and then drag "**Nvidia SmartDimmer Brightness Control**" onto a panel.

To alter brightness click the panel icon and drag the slider.


I have reading i lot of things about this issue, but onlyt this has helped...
thanks a lot.
I have a VGN FE41E...

---

### Post by gurps on 2007-12-02
Smartdimmer for me seems to be useless... nothing happens !

I've read that Suspend/Resume and Brightness Control depend on nVidia driver !
I've got the 100.14.19 from Ubuntu, but I've seen that nVidia released 100.14.23 (but I cannot managed to install!)

[Ubuntu Gutsy on Sony Vaio VGN-FZ21S with 8600M GS gpu]

---

### Post by jonbeal on 2007-12-07
Have just followed your instructions for the brightness control on my sony vaio vgn-fe28b Nvidia geforce go 7400 and has worked perfectly thanks very much for teh hard work you have put in to this.

j

---

### Post by Brunolp12 on 2007-12-08
got it to work (Sony Vaio FE31M, Geforce Go 7600 - Ubuntu 7.10)

used to use smartdimmer for brightness adjustment, which actually worked - but the light bulb is much better ;)

first i had the "cannot find install-sh or install.sh in . ./.. ./../.."-problem

but i found out this:

if [ ! -e /usr/share/automake ]; then sudo ln -s /usr/share/automake-1.9 /usr/share/automake; fi

created a broken link since my /usr/share/automake is not the /usr/share/automake-1.9 - it's the /usr/share/automake-1.10

so i removed the broken automake link in /usr/share/ and made it point to the correct folder

perfect :guitar:

---

### Post by badwolf on 2007-12-20
Hello,

Thanks for your applet but is there any way to get the normal ubuntu power management system to use smartdimmer in its back end so that it can dim the lcd brightness as the battery charge is reduced or when the system is idle?

Cheers.

---

### Post by Maulwuff on 2007-12-28
I managed to install the applet by building myself a deb-package. Is the properties dialog working on a direct make install?
I have to disable settings below "smartdimmer -s 3", otherwise the backlight switches off and I have to close/open my lid to get the light back on..

---

### Post by Mikee22 on 2007-12-31
> **gurps said:**
> Smartdimmer for me seems to be useless... nothing happens !

The same problem, nothing happend for me :(

Where I can find download links of nVidia Linux drivers ?

[Ubuntu 7.10, nVidia Quadro NVS 320M]

---

### Post by badwolf on 2007-12-31
Mikee22,

You could apt-get install nvidia-glx-new or try downloading from 

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Cheers

---

### Post by XerxesXS on 2008-01-05
Firstly, I would like to thank you. I have been trying to get the brightness to work on my FE31M for a while now, and straight off your method worked. Kudos to you. :D

It's just a shame that it doesn't work with gnome-power-manager to dim when the AC power is removed.

---

### Post by pawsey on 2008-01-08
Thanks for this. A latecomer to this thread and Ubuntu, I just installed Ubuntu 7.1 on my Sony Vaio VGN-C1Z/B yesterday and this works for me. Thank you! Nvidia Geforce Go 7400

---

### Post by _Stevie_ on 2008-01-14
IntuitiveNipple, thanks for your work, man!
this applet works perfectly. wish this could be included into the gnone power applets.

---

### Post by KillaW0lf04 on 2008-02-04
hey i just saw this thread and was wodering if anyone could help me with a problem i have with smartdimmer....Everytime i try set something on it i get the following error:

init_nvclock() failed!

Anyone knows if theres a solution to this?

Thanks!:)

---

### Post by pwn on 2008-02-20
I have the same problem. Any help?

---

### Post by gurth4ng on 2008-03-04
Working perfectly on a Sony Vaio FE21B, thx so much!

this just solved one of my biggest problems on using Ubuntu on my vaio.

---

### Post by ganxo on 2008-03-04
I still not got it on my VGN-FZ21E, if someone  can please PM me.

---

### Post by Richard Hertz on 2008-03-21
I am also having the same error with smartdimmer. If I try to do anything with it, I get the error "init_nvclock() failed!". This is on a fresh install on my vaio FE770G. Could this be a driver issue?

---

### Post by starlily on 2008-03-30
Brand new Vaio FZ340E with a NVidia Geforce. Absolutely *blinding* bright LCD, and no control whatsoever. Fkeys have no effect. smartdimmer is installed, but I get the "init_nvclock() failed!" when I try it. Newest nvclock wont build (lots of ugly errors). 

Id really appreciate some help. This is literally the ONLY thing that did not work perfect out of the box. 

Thanks,
Lily

---

### Post by sabme on 2008-05-24
Works for me, Sony VAIO, nVidia Go 7400.

Except for the command:
$ wget [http://ubuntuforums.org/attachment.php?attachmentid=33182&d=1179871063](http://ubuntuforums.org/attachment.php?attachmentid=33182&d=1179871063)
not downloading the required file.

One suggestion for the applet:  the way the slider is colored seems upside down to me.  I would prefer it if the lower portion was the darker one but I see what you were thinking. 

Could I reverse the coloring somehow?

Thanks

---

### Post by IntuitiveNipple on 2008-07-14
> **sabme said:**
> One suggestion for the applet:  the way the slider is colored seems upside down to me.  I would prefer it if the lower portion was the darker one but I see what you were thinking. 


I've recently updated the source-code so the slider operates 'properly' I've also fixed it so the panel icon works with transparent panels.

The latest source is attached here.

---

### Post by azredwing on 2008-07-19
Works perfectly on my VGN-SZ110! It's about time, too! Thanks!

The final thing: is it possible to get this to work such that when I switch to battery power, the system automatically dims? It would be perfect if this is the case..!

Thanks again!

---

### Post by IntuitiveNipple on 2008-07-20
> **azredwing said:**
> 
The final thing: is it possible to get this to work such that when I switch to battery power, the system automatically dims? It would be perfect if this is the case..!
Thanks again!

Yes, this is simple. It just requires a UDEV rule. Create the file **/etc/udev/rules.d/80-smartdimmer.rules**
```

# NVidia backlight control using smartdimmer
# Copyright July 2008, TJ <ubuntu@tjworld.net>
# Licensed under the GNU General Public License, v2

ACTION=="change", SUBSYSTEM=="power_supply", ATTR{type}=="Battery", ATTR{status}=="Discharging", RUN+="/usr/bin/smartdimmer -s 12"
ACTION=="change", SUBSYSTEM=="power_supply", ATTR{type}=="Battery", ATTR{status}=="Charging", RUN+="/usr/bin/smartdimmer -s 21"

```

Reload the UDEV rules and then try switching the charger off/on:
```

 sudo udevadm control --reload_rules

```

---

### Post by IntuitiveNipple on 2008-07-20
I've prepared and built packages for Feisty, Gutsy, Hardy and Intrepid that are available from my Personal Package Archive.

To add my PPA to your sources list:
```

$ sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
$ sudo apt-get update

```
To install, use Synaptic, aptitude or apt-get:
```

$ sudo apt-get install gnome-smartdimmer

```
Don't forget to also install smartdimmer itself:
```

$ sudo apt-get install smartdimmer

```

---

### Post by steveneddy on 2008-07-20
It's good to know that this package is out there.

My lappie dims when on battery power and I can control it with the keyboard buttons, but still good to know for future reference.

---

### Post by Deten on 2008-07-22
Worked, and I love you.

2 Years trying to get that working!

---

