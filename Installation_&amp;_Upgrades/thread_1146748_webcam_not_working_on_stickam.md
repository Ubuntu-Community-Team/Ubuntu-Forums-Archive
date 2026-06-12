---
title: "webcam not working on stickam"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by xfearxnxloathing on 2009-05-02
using logitech usb webcam, works with cheese but not with flash tho i have flash 10 installed and working.  i just can rightclick and go to setting when on stickam.  anyone know?!

i followed this [http://www.swift-tools.net/Flashcam/]("http://www.swift-tools.net/Flashcam/")

and this is my result: > envy@Elemented:~$ cd /home/envy/Desktop/
envy@Elemented:~/Desktop$ tar xvf flashcam-1.3.tgz 
flashcam-1.3/Makefile
flashcam-1.3/COPYING
flashcam-1.3/flashcam.c
flashcam-1.3/flashcamhook.c
flashcam-1.3/wrapper.in
flashcam-1.3/fcinit.in
flashcam-1.3/Test/
flashcam-1.3/Test/webcamtest.html
flashcam-1.3/Test/webcamtest.swf
flashcam-1.3/vloopback/
flashcam-1.3/vloopback/README
flashcam-1.3/vloopback/COPYING
flashcam-1.3/vloopback/vloopback.c
flashcam-1.3/vloopback/Makefile
envy@Elemented:~/Desktop$ cd flashcam-1.3
envy@Elemented:~/Desktop/flashcam-1.3$  sudo make install
[sudo] password for envy: 
cc -O -shared -fPIC -o flashcamhook.so flashcamhook.c
cc -O -o flashcam flashcam.c
(cd vloopback; make);
make[1]: Entering directory `/home/envy/Desktop/flashcam-1.3/vloopback'
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/home/envy/Desktop/flashcam-1.3/vloopback modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /home/envy/Desktop/flashcam-1.3/vloopback/vloopback.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/envy/Desktop/flashcam-1.3/vloopback/vloopback.mod.o
  LD [M]  /home/envy/Desktop/flashcam-1.3/vloopback/vloopback.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make[1]: Leaving directory `/home/envy/Desktop/flashcam-1.3/vloopback'
Creating wrapper
sed 's:%FCPATH%:/usr/local/flashcam:' wrapper.in > flashcamwrap
chmod +x flashcamwrap
Done.
Creating startup script
sed 's:%BINDIR%:/usr/local/bin:' fcinit.in > fcinit
Done.
install -d /usr/local/flashcam
install -d /usr/local/flashcam/bin
ln -s /usr/local/bin/flashcamwrap /usr/local/flashcam/bin/firefox
ln -s /usr/local/bin/flashcamwrap /usr/local/flashcam/bin/flashplayer
install -m 755 flashcamhook.so /usr/local/flashcam
install -m 755 flashcam flashcamwrap /usr/local/bin
install -m 755 fcinit /etc/init.d
(cd vloopback; make install);
make[1]: Entering directory `/home/envy/Desktop/flashcam-1.3/vloopback'
install -d /lib/modules/2.6.24-23-generic/kernel/drivers/misc
install -m 644 -c vloopback.ko /lib/modules/2.6.24-23-generic/kernel/drivers/misc
/sbin/depmod -a
make[1]: Leaving directory `/home/envy/Desktop/flashcam-1.3/vloopback'
if [ -x /sbin/chkconfig ]; then chkconfig --add fcinit; fi
if [ -x /usr/sbin/update-rc.d ]; then update-rc.d fcinit start 98 3 4 5 . stop 10 0 1 2 6 .; fi
 Adding system startup for /etc/init.d/fcinit ...
   /etc/rc0.d/K10fcinit -> ../init.d/fcinit
   /etc/rc1.d/K10fcinit -> ../init.d/fcinit
   /etc/rc2.d/K10fcinit -> ../init.d/fcinit
   /etc/rc6.d/K10fcinit -> ../init.d/fcinit
   /etc/rc3.d/S98fcinit -> ../init.d/fcinit
   /etc/rc4.d/S98fcinit -> ../init.d/fcinit
   /etc/rc5.d/S98fcinit -> ../init.d/fcinit
envy@Elemented:~/Desktop/flashcam-1.3$ cd ..
envy@Elemented:~/Desktop$ cd..
bash: cd..: command not found
envy@Elemented:~/Desktop$ cd ..
envy@Elemented:~$ sudo flashcam -L
Scanning devices
------
Found V4L2 Capture device: /dev/video0 (uvcvideo/UVC Camera (046d:09c1))
------
Executing: 'modprobe vloopback pipes=1'


---

### Post by dewmanstl on 2009-12-23
I know this is a old thread, but did anyone get this to work correctly? This is identical to what I am running into.

---

### Post by dewmanstl on 2009-12-26
bump

---

### Post by Flying Mandarine on 2010-01-05
I've got the exact same problem: my webcam is dark on Stickam and I can only right-click and have the Settings and About options. Cheese works perfectly, and I also have a Logitech.

Anyone have any idea?

Also, the Click here to enter room button on other's pages doesn't work, so I cannot enter other rooms I think.

Thanks!

---

### Post by horseradish on 2010-01-12
My problem seems similar. Webcam works ok in tests and skype, but not with flashplayer. Seems to be the v4l2 problem ?

---

### Post by teledyn on 2010-10-05
sorry to get your hopes up, but this is yet another place where the proprietary software world ghetto-izes Linux: The Adobe Flash has only very very limited support for V4L2, which includes only supporting the lowest resolution, and the V4L is only supported on some cameras.  So basically we're screwed, again.

There is a ubuntu ppa for the flashcam, it can work, but not for all cameras and apparently not for any of the cameras that I own.  you can find the details at [https://launchpad.net/~irving-popovetsky/+archive/ppa](https://launchpad.net/~irving-popovetsky/+archive/ppa)

in the instructions there, you need to do sudo aptitude update before you try the apt-get install, and you also need to install his vloopback package before the flashcam will being to work.  In my case it sees the camera(s), reports the manufacturer, loads the modules, says it redirects, but when I attempt to run the flashcamwrapper, I get the error that LD_PRELOAD cannot load the shared object file.

---

