---
title: "remote issue on feisty using lirc pvr-150"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by lawson23 on 2007-07-21
I have no need for the blaster I just want to use the standard remote provided with 150.

After reading a few post of everyone failing at this but saying that you must use the lirc drivers I decided to give it my own shot.

I followed this guide ([https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)) as I could tell to the T.

I get this when trying to start lirc though:
sudo /etc/init.d/lirc start
Password:
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.

It appears that lirc doesn't even exist.

---

### Post by luciodj on 2007-07-25
I have just tried the same steps and gotten the exact identical message.
I am pretty new to Ubuntu and Linux in general but I have found a very recent post on another forum:
[http://forums.gentoo.org/viewtopic-t-571712.html?sid=0f488008dca1b8a782603ab17fec8c62](http://forums.gentoo.org/viewtopic-t-571712.html?sid=0f488008dca1b8a782603ab17fec8c62)
See if it makes sense to you... and let me know, if you can, how to apply it...
thx

---

### Post by lawson23 on 2007-07-29
luciodj,
FYI, I'm also a newb.
I don't think this situation is the same as mine.  So I'm not sure if you have the same issue as myself or not.

Here is the weird part:
It acts as if it isn't installed.

nano /etc/init.d/lirc
Shows in it:
  GNU nano 2.0.2                                                          File: lirc

#! /bin/sh
#
#

load_modules ()
{
        local MODULES_MISSING=false

        for mod in $*
        do
                modprobe -k $mod 2> /dev/null || MODULES_MISSING=true
        done

        if $MODULES_MISSING; then
                echo "#####################################################"
                echo "## I couldn't load the required kernel modules     ##"
                echo "## You should install lirc-modules-source to build ##"
                echo "## kernel support for your hardware.               ##"
                echo "#####################################################"
                echo "## If this message is not appropriate you may set  ##"
                echo "## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##"
                echo "#####################################################"
                START_LIRCMD=false
                START_LIRCD=false


So this says if modules are missing return the message which is what I'm getting.

What I don't understand is I followed that guide installed lirc and built the modules according to the guide.

---

### Post by lawson23 on 2007-07-29
my hardware.conf
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
#LIRCD_ARGS=""
LIRCD_ARGS="--device=/dev/lirc0"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_i2c lirc_pvr150"

```

dmesg | grep -i lirc 
doesn't return anything.

uname -r
Returns:
2.6.20-15-generic

---

### Post by idomagic on 2007-07-29
Had a similiar problem, although for me it seemed like the gpio module was unable to load and thus resulted in the "couldn't load modules" error. (I've got an avermedia hybrid (a16ar) card)

Couldn't find any solution for the gpio-module (after reading around some I can conclude I'm not alone though), but I did find this alternate solution which worked like a charm for me: [http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers](http://www.linuxtv.org/v4lwiki/index.php/Remote_controllers)

---

### Post by lawson23 on 2007-08-02
Ok real weird.  As I have done this before I just did it again FOR THE HELL OF IT and this time it actually did something and now I can start LIRC.

Build Modules
[https://help.ubuntu.com/community/Install_Lirc_Feisty#head-a84c67cfbbccdb26c0bc1007b5702bb7c7031fac](https://help.ubuntu.com/community/Install_Lirc_Feisty#head-a84c67cfbbccdb26c0bc1007b5702bb7c7031fac)

So now for the testing.

---

### Post by lawson23 on 2007-08-02
Testing:
[https://help.ubuntu.com/community/Install_Lirc_Feisty#head-d27d54bb51b8dc22949ee1182b4873d56ae8743e](https://help.ubuntu.com/community/Install_Lirc_Feisty#head-d27d54bb51b8dc22949ee1182b4873d56ae8743e)
Well testing doesn't return anything in terminal so I need to keep looking.
I did act as it was supposed to but wouldn't return anything to the console when hitting the remote buttons.

---

### Post by lawson23 on 2007-08-07
dmesg | grep -i lirc
```
[   37.092552] lirc_dev: IR Remote Control driver registered, at major 61
[   37.100499] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[   37.252527] lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
[   37.252846] lirc_dev: lirc_register_plugin: sample_rate: 10
[   37.342591]  [<f977a0b8>] init_module+0x48/0x50 [lirc_pvr150]
```

Kernal Tainted:
[http://www.tux.org/lkml/#s1-18](http://www.tux.org/lkml/#s1-18)

I removed the module pvr_150 and built modules so I only had the i2c as all I'm trying to do is get the remote working not the blaster.

---

