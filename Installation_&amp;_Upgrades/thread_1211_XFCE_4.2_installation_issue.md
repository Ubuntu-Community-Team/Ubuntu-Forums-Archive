---
title: "XFCE 4.2 installation issue"
date: 2004-10-19
forum: Installation &amp; Upgrades
---

### Post by ErikN on 2004-10-19
Hi all

im trying to install the XFCE 4.2 beta to see what its like and getting the following error all the time:

The following packages have unmet dependencies:
  xfce4: Depends: xfce4-mcs-plugins (&gt;= 4.1.90) but it is not going to be installed
         Depends: xfce4-session (&gt;= 4.1.90) but it is not going to be installed
         Depends: xfcalendar (&gt;= 4.1.90) but it is not going to be installed
         Depends: xfce4-iconbox (&gt;= 4.1.90) but it is not going to be installed
         Depends: xfce4-mixer (&gt;= 4.1.90) but it is not going to be installed
         Depends: xfprint4 (&gt;= 4.1.90) but it is not going to be installed
         Depends: xfwm4 (&gt;= 4.1.90) but it is not going to be installed
         Depends: xfwm4-themes (&gt;= 4.1.90) but it is not going to be installed
         Depends: xfce4-appfinder (&gt;= 4.1.90) but it is not going to be installed
         Depends: xfce4-systray (&gt;= 4.1.90) but it is not going to be installed
         Depends: xfce4-utils (&gt;= 4.1.90) but it is not going to be installed
         Depends: xfdesktop4 (&gt;= 4.3.3+cvs.20040808-3) but it is not going to be installed

I removed all the old xfce packages but still no avail, anyone have any idea how to get around this?

thanks

---

### Post by cybrjackle on 2004-10-20
Have you tried there installer, or are you trying these debian packages?

[ftp://os-cillation.com/installers/xfce4-4.2beta1-installer.bin](ftp://os-cillation.com/installers/xfce4-4.2beta1-installer.bin)

[http://www.os-cillation.com/article.php?sid=37](http://www.os-cillation.com/article.php?sid=37)

---

### Post by cybrjackle on 2004-10-20
I used the installer, removed any package that had to do with xfce4 first, used synaptic so i wouldn't miss
 any ;)

sudo apt-get install a2ps libdbh1.0-dev

sudo sh xfce4-4.2beta1-installer.bin

You might find other packages you need to install first.

[img]ftp://65.28.47.173/xfce4.2.jpg[/img]

---

### Post by ErikN on 2004-10-20
Thanks lads, i will give the installer a try, didnt know it would work on Ubuntu yes or no =)

---

### Post by HungSquirrel on 2004-10-20
```
# ./xfce4-4.2beta1-installer.bin
Extracting the installer...

bzcat&#58; &#40;stdin&#41;&#58; trailing garbage after EOF ignored
Autodetecting Xfce installation... Checking installer requirements...
You need Gtk+ &gt;= 2.2.0 to use the installer.
Cleaning up...
```

Ummm...don't I already have GTK 2.2.0 or better?   :?

---

### Post by ErikN on 2004-10-20
I had the same gtk error as well, i installed a few gtk packages and it worked after that , the installer actually worked, however at 85% or so it does the xfwm4 config which fails with XPM library not installed on your system, anyone know what package installs the xpm library?

thanks

---

### Post by HungSquirrel on 2004-10-20
I searched Synaptic and I believe the package you're looking for is libxpm4.

By the way, I got the installer working.  I had to install libgtk2.0-dev and libxml2-dev to satisfy dependencies.  Hope this helps someone.

---

### Post by ErikN on 2004-10-21
THanks HungSquirrel, i will give that a try

---

### Post by ErikN on 2004-10-21
ok, got the installer working, thanks for that all, now one more thing, how do i add it to my session menu? it didnt add it?

---

### Post by HungSquirrel on 2004-10-21
sudo mkdir /etc/X11/sessions

Then, in your favorite text editor under sudo, make a file called /etc/X11/sessions/xfce.desktop and put this in it:

```
&#91;Desktop Entry&#93;
Encoding=UTF-8
Name=XFCE4
Comment=This logs you into XFCE4.
Exec=/usr/local/bin/startxfce4
TryExec=/usr/local/bin/startxfce4
Icon=
Type=Application
```

---

### Post by ErikN on 2004-10-21
I had that done already but still nothing =(

---

### Post by zeos on 2004-10-21
the xsessions folder is in  /usr/share
 
edit: but that still doesnt get it. i found this of the xfce forum [http://forum.xfce.org/viewtopic.php?t=916&amp;highlight=gdm](http://forum.xfce.org/viewtopic.php?t=916&amp;highlight=gdm) but i cant find any gdm.conf

---

### Post by HungSquirrel on 2004-10-21
[quote=ErikN]I had that done already but still nothing =([/quote]
Make sure it points to /usr/**local**/bin/startxfce**4** .  I had a .desktop file for the Ubuntu package of XFCE and it pointed to /usr/bin/startxfce so of course it didn't work.

---

### Post by ErikN on 2004-10-22
[quote=HungSquirrel][quote=ErikN]I had that done already but still nothing =([/quote]
Make sure it points to /usr/**local**/bin/startxfce**4** .  I had a .desktop file for the Ubuntu package of XFCE and it pointed to /usr/bin/startxfce so of course it didn't work.[/quote]

You rule !!

[img]http://www.emeraldwizard.com/xfce.png[/img]

---

### Post by zeos on 2004-10-25
ok so i got gdm to see it finally, but now i get some error when trying to load xfce.  ill try to post a screenshot or log or something when i get home from work.

---

### Post by zeos on 2004-10-25
here is the output from ~/.xsession-errors

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jake"
/etc/gdm/Xsession: Beginning session setup...
/usr/share/xfce-beta/bin/startxfce4: X server already running on display :0
Agent pid 5208
/usr/share/xfce-beta/etc/xdg/xfce4/xinitrc: line 82: xfce-mcs-manager: command not found
/usr/share/xfce-beta/etc/xdg/xfce4/xinitrc: line 83: xfwm4: command not found
/usr/share/xfce-beta/etc/xdg/xfce4/xinitrc: line 95: xftaskbar4: command not found
/usr/share/xfce-beta/etc/xdg/xfce4/xinitrc: line 96: xfdesktop: command not found
/usr/share/xfce-beta/etc/xdg/xfce4/xinitrc: line 97: xfcalendar: command not found
```

---

### Post by alexis on 2004-10-28
I've been trying tonstall xfce4 with the installer and, I've been receiving this error:

```
### Initializing for application with prefix=/usr/local
###
### Working on libxfce4util
###
### Running ./configure  --prefix=/usr/local
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for AIX... no
checking for library containing strerror... none required
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
``` 

please help.

---

### Post by alexis on 2004-10-28
the installer now fails at about 60% during the compilation of xsession manager. please help.

---

### Post by anshu on 2004-12-24
[QUOTE=][/QUOTE]
 my oscillation installation stops at 10 percent and gives same error message as alexis is getting ... 

does someone knows bout it?

---

### Post by yentingchen on 2004-12-25
Hi, dear all :)

I'm using XFCE 4.2 RC3 now, but I don't install it with the installer, I just add
[PHP]
deb http://www.os-cillation.de/debian binary/
deb-src http://www.os-cillation.de/debian source/
[/PHP]
to my sources.list, and then use aptitude to install xfce4, then I can see it in my gdm menu.

Hope this helps.  :mrgreen:

---

### Post by Valavien on 2005-01-17
Ok so I have tried to install 4.2 through synaptic with:

deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

But when I do there are missing files.
I also tried to install xfce4-4.2.0-installer.bin through the install.

It gets to 5% and XFCE Utility Library when I get this message in the log:

C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
!! Failed to configure libxfce4util

I have done some searching on this but as far as I can tell I have cpp and gcc installed.

Any ideas?

---

### Post by Valavien on 2005-01-17
Well after mucking around for ages I found the solution in another thread about something else.

I installed build-essential from synaptic and it fixed it.  I guess gcc wasn't installed after all.

Processing as I type.  Hopefully there are no further problems... 

 8-)

---

