---
title: "Mce keyboard in ubuntu"
date: 2008-05-05
forum: Hardware
---

### Post by kubuch on 2008-05-05
Hello guys ;)
I just start with Ubuntu. all work great but i have some problems with config of "Microsoft Remote Keyboard for WinXP MCE v1.0" 
I install lirc and lirc_mod_mce drives.. 
i try with "irw" and i see commands i set up is to VLC and work great but..
but only media keys.
I wonder how to make Mce keyboard to work in system,openoffice generaly in ubuntu. Now I type with my old usb key but i wanna get MCE keys to work.
its my   dmesg | grep -i lirc
```
[   35.846905] lirc_dev: IR Remote Control driver registered, major 61 
[   35.856824] lirc_mceusb2: no version for "lirc_get_pdata" found: kernel tainted.
[   35.860593] lirc_mceusb2: Philips eHome USB IR Transciever and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.36 $
[   35.860598] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   36.236794] lirc_dev: lirc_register_plugin: sample_rate: 0
[   36.240775] lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb4:2
[   36.240806] usbcore: registered new interface driver lirc_mceusb2
[   36.284305] lirc_mod_mce: Input driver for Microsoft MCE 2005 keyboard v0.2.0
[   36.284309] lirc_mod_mce: Florian Demski
[   36.308099] usbcore: registered new interface driver lirc_mod_mce

``` 

pls help 
peace

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

### Post by Villu on 2009-10-19
Can this setup be used with an ordinary MCE remote as well? How about XBox DVD remote?

---

### Post by leeko on 2009-11-08
Unfortunately, this guide no longer works for Karmic Koala (9.10) - it fails at the "make" command. 

Has anyone had any luck with this keyboard/mouse in 9.10? 

Thanks,

Lee

---

### Post by mukulakivi on 2009-11-23
I have got the same problem with ubuntu Karmic Koala installed yesterday. Make fails and it seems that there are mainly different names for the functions. I try to rename them, but there is also lirc_driver structure member ioctl missing in official lirc_dev.h and I tryed to comment the line in lirc_mod_mce.c. After that make succeeded, but lirc do no work anyway. Remote is working like it worked before this too. I try lirc_mod_mce version 0.2.1, because I had 0.2.0 in Hardy and it was working just fine - no repeat problem. 
here is the result
lsmod | grep lirc
lirc_mod_mce           14880  0 
lirc_dev               10804  1 lirc_mod_mce

but in previous distro Hardy I had as follows:
lsmod | grep lirc 
 lirc_mod_mce 17924 1  
 lirc_dev 16132 1 lirc_mod_mce 
 usbcore 125448 7
usbhid,usb_storage,uhci_hcd,lirc_mod_mce,ohci_hcd,ehci_hcd 

so - I'm wondering where is usbcore now - should it be there also in Karmic Koala distro?

It would be nice to hear if it's possible to use the MCE keyboard and mouse too in Karmic. The distro drivers lirc_mceusb worked only with remote control keys.

Otherwise I have to install 9.04 and try with it.

---

### Post by leeko on 2009-11-24
Can anyone help us figure this out? 

Thanks

---

### Post by ryanolf on 2009-11-25
I have also found that lirc_mod_mce no longer compiles in Karmic. There are other threads mentioning this problem, and I've filed a bug on the lirc_mod_mce sourceforge page, though it looks like not much is happening there. Has anyone found a workaround in Karmic to get the keyboard working?

---

### Post by jon47 on 2010-07-23
I've solved this :-)

see [http://wwww.ubuntuforums.org/showthread.php?p=9628326#post9628326](http://wwww.ubuntuforums.org/showthread.php?p=9628326#post9628326)

Cheers
Jon

---

