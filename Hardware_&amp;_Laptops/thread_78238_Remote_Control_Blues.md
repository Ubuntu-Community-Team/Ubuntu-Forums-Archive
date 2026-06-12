---
title: "Remote Control Blues"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by rpakdel on 2005-10-18
The upgrade to Breezy went smoothly. Lots of improvements, great job!

But, and I don't presume this is a Breezy problem per se, some of my ATI Remote Wonder I keys stopped working. 

I still have Hoary installed and all (except Channel +/-) the remote keys work and I can program them for various tasks. On Breezy, the "TV", "DVD" and "OK" keys are also dead (you can guess what those were being used for). 

I mean, they-don't-send-any-signal-to-xev dead. I tried running just xterm and xev and the keys just don't send any signals (in case metacity was grabbing them in Gnome). 

I think this is a bug in the ati_remote kernel module, so perhaps I should submit a bug. Anybody else tried this?

---

### Post by nightbikeman on 2005-11-11
Just some moral support really I suffering exactly the same thing. :) 

I have discovered that evtest works i.e. registers the key presses so I think that it is an X issue not a kernel issue. Not sure that makes it any better though..... 

It has also been reported in Debian. [http://lists.debian.org/debian-x/2005/08/msg00163.html](http://lists.debian.org/debian-x/2005/08/msg00163.html)

Happy hunting for a solution I'll let you know if I find one.....

---

### Post by teaker1s on 2005-11-12
just a thought can you see an output in dmesg as if you can the key press is detected and you may be able to work along the lines of multimedia keys wilki to get some sort of functioning keys until you find a better fix

---

### Post by nightbikeman on 2005-11-14
Having been playing at the weekend, I've found that the kernel is getting a scan code that isn't in its keyboard map.

The command showkey displays the scan codes when keys are pressed. They just aren't translated into keycodes, and thus things that print. The command to setup the keyboard map, i.e. scan code to key code translation, is the setkeycode command. 

The problem is I haven't worked out how to get setkeycode to accept 6 digit scan codes. It is possible because some of the other keys produce them and have got key codes associated with them.

I'll keep hunting....

Edit: changed loadkey->scankeycode because I got confused.

---

### Post by nightbikeman on 2005-11-14
Nothing in dmesg about the unknown scan codes....

---

### Post by nightbikeman on 2005-11-14
okay I've fixed it. It appears that the scan codes that don't work are > 255 not sure why they don't work it appears to be very deliberate. Im not sure what the long term fix is but recompiling the ati_remote kernel module does it for me

quick recipe to fix.

recompile your ati_remote module with the key codes < 255 

longer one
```

sudo bash
# Get the kernel source code and compiler
apt-get install linux-source-2.6.12-9 gcc-3.4

# unpack the kernel source code
cd /usr/src
tar xjf linux-source-2.6.12.tar.bz2
copy the attached ati-remote.c to /usr/src/linux-source-2.6.12/drivers/usb/input/ati_remote.c

# get the current kernels config, so we build the same config.
cp /boot/config-2.6.12-9-386 /usr/src/linux-source-2.6.12/.config

# Build the kernel this will take a while
cd /usr/src/linux-source-2.6.12
make 

# make a backup of the orginal kernel module
cp /lib/modules/2.6.12-9-386/kernel/drivers/usb/input/ati_remote.ko /lib/modules/2.6.12-9-386/kernel/drivers/usb/input/ati_remote.ko.orig 

# insert the new one
cp /usr/src/linux-source-2.6.12/drivers/usb/input/ati_remote.ko /lib/modules/2.6.12-9-386/kernel/drivers/usb/input/

# remove the old kernel module and insert the new one.
rmmod ati_remote
modprobe ati_remote

```
:p :p :p :p :p :cool:

If it  all goes wrong restore your original kernel module and reboot....
```

cp /lib/modules/2.6.12-9-386/kernel/drivers/usb/input/ati_remote.ko.orig /lib/modules/2.6.12-9-386/kernel/drivers/usb/input/ati_remote.ko

```

---

### Post by galorin on 2007-09-18
Sorry to bump an old thread, but this is still relevant to, well at least me as I am trying to get the same remote working on 7.04, kernel 2.6.17-12-generic, and the origional problem persists, in that the keys for tv, dvd, volume, etc do not function.

I have tried compiling the module for my running kernel, but get a compile error, as follows:

drivers/usb/input/ati_remote.c:303: error: unknown field ‘owner’ specified in initializer
drivers/usb/input/ati_remote.c:303: warning: initialization from incompatible pointer type
make[3]: *** [drivers/usb/input/ati_remote.o] Error 1
make[2]: *** [drivers/usb/input] Error 2
make[1]: *** [drivers/usb] Error 2
make: *** [drivers] Error 2


Commenting out the line in the code which contains the owner field, I wind up with a module that loads, but does not do anything as far as I can tell.

---

