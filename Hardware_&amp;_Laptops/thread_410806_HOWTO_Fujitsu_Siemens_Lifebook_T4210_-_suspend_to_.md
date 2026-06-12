---
title: "HOWTO: Fujitsu Siemens Lifebook T4210 - suspend to ram (sleep)"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by jayprakash on 2007-04-16
(this is for feisty, for edgy are minor changes that you'll find when you read everithing)

s2ram works with cvs version o uswsusp.
t4210 is in the whitelist now.

Read this [http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)
Read this [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

Download cvs like this [http://suspend.sourceforge.net/download.shtml](http://suspend.sourceforge.net/download.shtml)
cvs -z3 -d:pserver:anonymous@suspend.cvs.sf.net:/cvsroot/suspend co suspend

to compile you need
pciutils-dev and libx86-dev packages (in addition to build essentials)
(before compile... I installed uswsusp from repository and then the cvs on top of it. version from repository installs also working initrd image)


READ README and README.s2ram!
Edit Makefile and conf/suspend.conf acording to README
make s2disk
make s2ram
make s2both
make resume
sudo make install

(output here: 
$ sudo make install
install -D --mode=755 s2disk /usr/local/sbin/s2disk
cc -I/usr/local/include -DS2RAM -O2 -Wall -DCONFIG_BOTH -c s2ram.c -o s2ram-both.o
cc -g -I/usr/local/include -DS2RAM -O2 -Wall -DCONFIG_BOTH  vt.o md5.o encrypt.o config.o loglevel.o splash.o bootsplash.o vbetool/vbetool.o radeontool.o dmidecode.o s2ram-both.o suspend.c -o s2both -L/usr/local/lib -L/usr/local/lib -lpci -lz -lx86
install -D --mode=755 s2both /usr/local/sbin/s2both
install -D --mode=755 s2ram /usr/local/sbin/s2ram
install -D --mode=755 swap-offset /usr/local/sbin/swap-offset
install -D --mode=755 resume /usr/local/lib/suspend/resume
make: Warning: File `/dev/snapshot' has modification time 6,2e+03 s in the future
if [ -f /etc/suspend.conf ]; then \
                install --mode=644 conf/suspend.conf \
                        /etc/suspend.conf.new;\
        else \
                install -D --mode=644 conf/suspend.conf \
                        /etc/suspend.conf; \
        fi
make: warning:  Clock skew detected.  Your build may be incomplete.
)

looks like the suspend.conf is not instaled corectly, so edit it
sudo gedit /etc/suspend.conf
here write your swap partition: 
resume device = /dev/sda6

test it:
logout from X (gnome or KDE)
switch to vt1
login as user or root
sudo killall gdm (to be sure)
sudo s2ram

if it doesn't work try
sudo s2ram -f -v -a 3

If that doesn't work, than you have a problem :)

test s2disk:
logout from X (gnome or KDE)
switch to vt1
login as user or root
sudo killall gdm (to be sure)

sudo s2disk
Should work if you configured /etc/suspend.conf corectly


Now test both from X (loged in gnome or KDE)
sudo s2ram
sudo s2disk
(you can try also s2both, but this doesn't work correctly for now)


If all works continue with 
[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

edit the copied files:
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
find all /usr/bin/s2disk replace with /usr/local/sbin/s2disk (output of "which s2disk")

sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
find all /usr/bin/s2ram replace with /usr/local/sbin/s2ram (output of "which s2ram")



Now when you click on gnome or kde or kpowersave or anything... on suspend or hibernate, it will use s2ram and s2disk.


I personaly am using KDE with Beryl, wifi connection to internet.
With s2ram and s2disk it resumes so perfectly that I have set close-lid event to suspend to ram.

 

I hope this helps to all who were like me searching an trying all possible.

(I hope my comunication with [email]suspend-devel@lists.sourceforge.net[/email] will continue to a working s2both, because that is an ingenial architecture)

Jay

---

