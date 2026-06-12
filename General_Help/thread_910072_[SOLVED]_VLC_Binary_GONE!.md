---
title: "[SOLVED] VLC Binary GONE!"
date: 2008-09-04
forum: General Help
---

### Post by ashmew2 on 2008-09-04
Hi....I just installed Hardy 64 Bit on my Athlon X2. I was trying to compile the latest tarballs for vlc from videolan.org/vlc . I couldnt install it from the tarball. ( I did ./configure but it gave errors in make). So i deleted all the configuration files and tar files of vlc and then installed it using apt-get. Now whenever i try to run vlc it gives me no output.
Running vlc from terminal gives :

bash: /usr/local/bin/vlc: No such file or directory

```
What should i do ? :(
```

Thanks.

---

### Post by Linteg on 2008-09-04
Run "which vlc" in a terminal and post what it returns.

---

### Post by ashmew2 on 2008-09-04
OMG ! 

```
which vlc
```
doesnt give any output...

---

### Post by Sycron on 2008-09-04
There are dependency problems but i don't really know. Did you tried```
sudo apt-get build-dep vlc
``` ?

---

### Post by ashmew2 on 2008-09-04
```
sudo apt-get build-dep vlc
```

returns :


> The following packages will be REMOVED:
  libdvbpsi3-dev
The following NEW packages will be installed:
  autoconf automake autotools-dev cvs debhelper dh-buildinfo diffstat dpatch gettext html2text intltool-debian
  liba52-0.7.4-dev libaa1-dev libapr1 libaprutil1 libarts1-dev libarts1c2a libartsc0 libartsc0-dev libasound2-dev
  libatk1.0-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev libavc1394-dev libcaca-dev libcairo2-dev
  libcdio-dev libcucul-dev libcupsys2-dev libdbus-glib-1-dev libdirectfb-dev libdirectfb-extra libdts-dev libdvbpsi4-dev
  libdvdnav-dev libdvdread-dev libebml-dev libesd0-dev libfaad-dev libfaad0 libflac-dev libggi2 libggi2-dev libgif-dev
  libgif4 libgii1 libgii1-dev libgii1-target-x libgnutls-dev libgnutlsxx13 libgtk2.0-dev libid3tag0-dev libimlib2
  libimlib2-dev libiso9660-dev libjack-dev liblircclient-dev liblivemedia-dev libltdl3-dev liblzo2-dev libmad0-dev
  libmatroska-dev libmodplug-dev libmozjs-dev libmozjs0d libmpcdec-dev libmpeg2-4-dev libncurses5-dev libnotify-dev
  libnspr4-dev libnss3-dev libopencdk10-dev libpango1.0-dev libpixman-1-dev libpulse-dev libpulse-mainloop-glib0
  libqt3-headers libqt3-mt libqt3-mt-dev libsdl-image1.2-dev libsdl1.2-dev libslang2-dev libsmbclient-dev libspeex-dev
  libsvn1 libsysfs-dev libtar-dev libtasn1-3-dev libtiff4-dev libtiffxx0c2 libtool libvcdinfo-dev libwxbase2.6-dev
  libwxgtk2.6-dev libxcomposite-dev libxdamage-dev libxml2-dev libxosd-dev libxul-common libxul-dev libxul0d libxv-dev m4
  nasm po-debconf qt3-dev-tools quilt subversion wx2.6-headers x11proto-composite-dev x11proto-damage-dev
  x11proto-video-dev xlibmesa-gl-dev xulrunner yasm
The following packages will be upgraded:
  libnss3-1d libpango1.0-0 libpango1.0-common libtiff4 libxml2
5 upgraded, 116 newly installed, 1 to remove and 106 not upgraded.
Need to get 50.5MB/53.0MB of archives.
After this operation, 211MB of additional disk space will be used.
Do you want to continue [Y/n]? 



I installed the libdvbpsi3-dev for compiling the tarball.. Maybe it broke the system..Itll take me around 20 mins to download the 50 MB it needs so , ill be back then!

---

### Post by Sycron on 2008-09-04
After that try to recompile vlc. Maybe you'll find the altest version of vlc on [www.getdeb.com](www.getdeb.com) .

---

### Post by ashmew2 on 2008-09-04
Recompile ? I think itll break again...cant i just reinstall via synaptic/apt-get ?

---

### Post by Sycron on 2008-09-04
Yes you can. 
```
sudo apt-get --reinstall install vlc
```

---

### Post by ashmew2 on 2008-09-04
Doesnt work as yet...

```
ashish@H4xX0R:~$ sudo apt-get --reinstall install vlc
[sudo] password for ashish: 

```

returns :

> 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdvbpsi3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 106 not upgraded.
Need to get 0B/1169kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 
dpkg: serious warning: files list file for package `vlc-plugin-esd' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libvlc0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `vlc-nox' missing, assuming package has no files currently installed.
116943 files and directories currently installed.)
Preparing to replace vlc 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1 (using .../vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1_amd64.deb) ...
Unpacking replacement vlc ...
Setting up vlc (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1) ...

After that :

ashish@H4xX0R:~$ vlc
bash: /usr/local/bin/vlc: No such file or directory

Back to the starting point...

---

### Post by kpkeerthi on 2008-09-04
What happens when you type 
```
/usr/bin/vlc
``` at the prompt?

---

### Post by ashmew2 on 2008-09-04
No such File or Directory...

---

### Post by Joeb454 on 2008-09-04
You could also try ```
sudo apt-get install -f
```

---

### Post by ashmew2 on 2008-09-04
```
 sudo apt-get install -f
```

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdvbpsi3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 106 not upgraded.

```
sudo apt-get autoremove
```
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdvbpsi3
The following packages will be REMOVED:
  libdvbpsi3
0 upgraded, 0 newly installed, 1 to remove and 106 not upgraded.
After this operation, 106kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 
dpkg: serious warning: files list file for package `vlc-plugin-esd' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libvlc0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `vlc-nox' missing, assuming package has no files currently installed.
116942 files and directories currently installed.)
Removing libdvbpsi3 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place


---

### Post by prshah on 2008-09-04
> **ashmew2 said:**
> 
dpkg: serious warning: files list file for package `vlc-plugin-esd' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libvlc0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `vlc-nox' missing, assuming package has no files currently installed.


You can ignore these "serious" errors; to get rid of this message, either reinstall the packages in question (good idea) or delete the entries related to these names from /var/lib/dpkg/info/

Can you also post the output of ```
sudo updatedb && sudo locate vlc
``` (Note that updatedb will take some time)

---

### Post by ashmew2 on 2008-09-04
> **prshah said:**
> You can ignore these "serious" errors; to get rid of this message, either reinstall the packages in question (good idea) or delete the entries related to these names from /var/lib/dpkg/info/

Can you also post the output of ```
sudo updatedb && sudo locate vlc
``` (Note that updatedb will take some time)

 Here it is :



> 
/home/ashish/vlc-0.9.1.tar.bz2
/home/ashish/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fashish%2FDesktop%2Fvlc-0.9.1%2Finclude.xml
/home/ashish/Desktop/vlc deps~
/usr/bin/svlc
/usr/bin/wxvlc
/usr/lib/vlc
/usr/lib/mime/packages/vlc
/usr/lib/vlc/access
/usr/lib/vlc/audio_filter
/usr/lib/vlc/audio_mixer
/usr/lib/vlc/audio_output
/usr/lib/vlc/codec
/usr/lib/vlc/control
/usr/lib/vlc/demux
/usr/lib/vlc/gui
/usr/lib/vlc/misc
/usr/lib/vlc/video_chroma
/usr/lib/vlc/video_filter
/usr/lib/vlc/video_output
/usr/lib/vlc/visualization
/usr/lib/vlc/access/libscreen_plugin.so
/usr/lib/vlc/audio_output/libpulse_plugin.so
/usr/lib/vlc/codec/libsdl_image_plugin.so
/usr/lib/vlc/gui/libskins2_plugin.so
/usr/lib/vlc/gui/libwxwidgets_plugin.so
/usr/lib/vlc/misc/libnotify_plugin.so
/usr/lib/vlc/video_output/libaa_plugin.so
/usr/lib/vlc/video_output/libcaca_plugin.so
/usr/lib/vlc/video_output/libglx_plugin.so
/usr/lib/vlc/video_output/libopengl_plugin.so
/usr/lib/vlc/video_output/libx11_plugin.so
/usr/lib/vlc/video_output/libxvideo_plugin.so
/usr/lib/vlc/visualization/libxosd_plugin.so
/usr/share/vlc
/usr/share/applications/vlc.desktop
/usr/share/doc/vlc
/usr/share/doc/vlc-plugin-pulse
/usr/share/doc/videolan-doc/vlc-user-guide-de.pdf.gz
/usr/share/doc/videolan-doc/vlc-user-guide-de.txt.gz
/usr/share/doc/videolan-doc/vlc-user-guide-en.pdf.gz
/usr/share/doc/videolan-doc/vlc-user-guide-en.txt.gz
/usr/share/doc/videolan-doc/vlc-user-guide-fr.pdf.gz
/usr/share/doc/videolan-doc/vlc-user-guide-fr.txt.gz
/usr/share/doc/videolan-doc/html/vlc-user-guide
/usr/share/doc/videolan-doc/html/vlc-user-guide/de
/usr/share/doc/videolan-doc/html/vlc-user-guide/en
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/apa.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/ch01.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/ch02.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/ch03.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/ch04.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/ch05.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/ch06.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/ch07.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/images
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/index.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/screen.css
/usr/share/doc/videolan-doc/html/vlc-user-guide/de/vlc-user-guide-de.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/apa.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/ch01.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/ch02.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/ch03.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/ch04.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/ch05.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/ch06.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/ch07.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/images
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/index.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/screen.css
/usr/share/doc/videolan-doc/html/vlc-user-guide/en/vlc-user-guide-en.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/apa.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/ch01.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/ch02.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/ch03.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/ch04.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/ch05.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/ch06.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/ch07.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/images
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/index.html
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/screen.css
/usr/share/doc/videolan-doc/html/vlc-user-guide/fr/vlc-user-guide-fr.html
/usr/share/man/man1/svlc.1.gz
/usr/share/man/man1/wxvlc.1.gz
/usr/share/menu/vlc
/usr/share/pixmaps/vlc.png
/usr/share/vlc/pda-forwardb16x16.xpm
/usr/share/vlc/pda-openb16x16.xpm
/usr/share/vlc/pda-pauseb16x16.xpm
/usr/share/vlc/pda-playb16x16.xpm
/usr/share/vlc/pda-playlistb16x16.xpm
/usr/share/vlc/pda-preferencesb16x16.xpm
/usr/share/vlc/pda-rewindb16x16.xpm
/usr/share/vlc/pda-stopb16x16.xpm
/usr/share/vlc/skins2
/usr/share/vlc/vlc.xpm
/usr/share/vlc/vlc16x16.xpm
/usr/share/vlc/vlc48x48.ico
/usr/share/vlc/wxvlc.xpm
/usr/share/vlc/skins2/default.vlt
/usr/share/vlc/skins2/fonts
/usr/share/vlc/skins2/skin.catalog
/usr/share/vlc/skins2/skin.dtd
/usr/share/vlc/skins2/winamp2.xml
/usr/share/vlc/skins2/fonts/FreeSans.ttf
/usr/share/vlc/skins2/fonts/FreeSansBold.ttf
/var/cache/apt/archives/mozilla-plugin-vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1_amd64.deb
/var/cache/apt/archives/vlc-plugin-pulse_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1_amd64.deb
/var/cache/apt/archives/vlc_0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1_amd64.deb
/var/lib/dpkg/info/vlc-plugin-pulse.list
/var/lib/dpkg/info/vlc-plugin-pulse.md5sums
/var/lib/dpkg/info/vlc.list
/var/lib/dpkg/info/vlc.md5sums
/var/lib/dpkg/info/vlc.postinst
/var/lib/dpkg/info/vlc.postrm


---

### Post by ashmew2 on 2008-09-04
Can someone upload the vlc executable for me ? :((

---

### Post by kpkeerthi on 2008-09-04
I see **/usr/bin/wxvlc** in the locate command output above.

You should just be able to run it by typing **wxvlc** at the prompt.

---

### Post by ashmew2 on 2008-09-24
A reinstall after a couple of restarts using apt-get fixed it..Thanks..

---

### Post by Sycron on 2008-09-25
You're welcome :P.

---

