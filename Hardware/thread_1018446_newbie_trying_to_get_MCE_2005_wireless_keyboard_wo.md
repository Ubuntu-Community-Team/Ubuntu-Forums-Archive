---
title: "newbie trying to get MCE 2005 wireless keyboard working"
date: 2008-12-22
forum: Hardware
---

### Post by Sniperman2012 on 2008-12-22
im new to linux in general and im trying to get my wireless keyboard working.
running intrepid

uname -r = 2.6.27-9-generic
this is a fresh install, i havent done anything but run the update manager and let it finish.

so far i have done the following.

1.Install the lirc packages
sudo apt-get install lirc lirc-modules-source 

then i download lirc_mod_mce which should allow the use of both the mce remote controller and the keyboard itself as well.

its on my desktop, i untar it

from her eim not really sure what to do, if i type make it just gives me errors, that i cant find more information on.

any and all help appreciated greatly.



sniperman@sniperman-Ubuntu:~/Desktop/lirc_mod_mce$ make
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/sniperman/Desktop/lirc_mod_mce modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/sniperman/Desktop/lirc_mod_mce/lirc_mod_mce.o
/home/sniperman/Desktop/lirc_mod_mce/lirc_mod_mce.c: In function ‘usb_remote_probe’:
/home/sniperman/Desktop/lirc_mod_mce/lirc_mod_mce.c:1301: error: ‘struct input_dev’ has no member named ‘cdev’
make[2]: *** [/home/sniperman/Desktop/lirc_mod_mce/lirc_mod_mce.o] Error 1
make[1]: *** [_module_/home/sniperman/Desktop/lirc_mod_mce] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [default] Error 2
sniperman@sniperman-Ubuntu:~/Desktop/lirc_mod_mce$

---

### Post by BroadArrow on 2009-01-08
Most likely it's the problem described in [this guide]("http://www.mythtv.org/wiki/index.php/MCE_Remote#Download_a_lirc_CVS_SnapShot") and you need to install LIRC from a CVS snapshot (ie: the latest bleeding edge version of LIRC).

I've followed those instructions and got the remote working, but not the keyboard... :-(

---

### Post by Sniperman2012 on 2009-01-08
thanks for your reply.
im not really interested in the remote functions just wanted my wireless keyboard to work with ubuntu, ill prolly just end up buying something new for it.

---

### Post by BroadArrow on 2009-01-08
> **Sniperman2012 said:**
> thanks for your reply.
im not really interested in the remote functions just wanted my wireless keyboard to work with ubuntu, ill prolly just end up buying something new for it.

I'm sure there's a way to get it going as I've seen other references to the keyboard working with Mythbuntu. I just haven't found out the solution myself yet as I've only just moved my media centre over to Linux (it was the last hold out in our house for a few years now).

---

### Post by Sniperman2012 on 2009-01-08
yeah, ive heard of ppl doing it also, but mostly on older version of ubuntu, so maybe someone will figure it out, im pretty new to ubuntu and linux in a whole so just adds to the difficulty for me.

---

### Post by BroadArrow on 2009-01-16
I've got my keyboard working following all (and I mean ALL) the instructions in [this post]("http://ubuntuforums.org/showthread.php?t=1037667"). 

My config needs to be tweaked as I'm getting a lot of repeat key presses but it is working -- and I'm writing this using my MCE keyboard -- so there's light at the end of the tunnel.

---

### Post by north_pole on 2009-04-30
YEEES! Finally I've made it all work. Here's an HOW-TO for Ubuntu Jaunty Jackalope 9.04:
 
1. Install some required modules with
 
```
$ sudo apt-get install lirc lirc-modules-source module-assistant 
```2. and then run the following command
 
```
$ sudo dpkg-reconfigure lirc-modules-source 
```3. Open the the hardware.conf file with this command
 
```
$ sudo gedit /etc/lirc/hardware.conf 
```4. Change two of the lines so they look like this:
 
```
REMOTE_MODULES="lirc_mod_mce"
 
LOAD_MODULES="true" 
```Save and exit.
 
5. Run the following commands
 
```
$ sudo m-a update,prepare
 
$ sudo m-a clean lirc
 
$ sudo m-a a-i -f lirc    (if this one fails, choose "skip and continue with the next operation")
 
$ sudo depmod -a
```6. Download and unpack the attached files "lircd.conf" and "lircrc". Put them in /etc/lirc.
 
7. Now download the lirc_mod_mce v.0.1.5 file from [http://sourceforge.net/project/showf...kage_id=203215]("http://sourceforge.net/project/showfiles.php?group_id=171688&package_id=203215"), but be sure to download version 0.1.5 and NOT the v0.2.0. The later one has the famous "keypress repeats forever"-bug and should be avoided. Unpack the archive on e.g. your desktop.
 
8. Replace the "lirc_dev.h" file with the one located in "/usr/src/%YOUR_LIRC_VERSION%/drivers/lirc_dev"
 
9. In the file named "lirc_mod_mce.c", you have to change one of the lines:
 
```
input_dev->cdev.dev = &dev->dev;
 
to
 
input_dev->dev.parent = &dev->dev; 
```Save and exit.
 
10. Now, execute
 
```
$ sudo make 
```11. Create a new directory in "/lib/modules/%YOUR_CURRENT_KERNEL%" and name it "misc".
 
12. Some extra files have been created in the "lirc_mod_mce" directory.
One of them is "lirc_mod_mce.ko". Copy it to the new directory you've just created.
 
13. Run
 
```
sudo depmod -a
 
modprobe lirc_mod_mce 
```14. At last we have to blacklist the "lirc_mceusb2" module. Otherwise it will
interfere with the "lirc_mod_mce" one and make all of our work useless. Execute:
 
```
$ sudo gedit /etc/modprobe.d/blacklist.conf 
```and add the line
 
```
blacklist lirc_mceusb2
```on an own row e.g. in the bottom of the file. Save and close.
 
15. Reboot
 
16. And VOILA! Your MCE Keyboard should now be working!

---

