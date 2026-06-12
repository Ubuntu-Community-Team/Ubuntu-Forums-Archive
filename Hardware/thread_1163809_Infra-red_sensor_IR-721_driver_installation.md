---
title: "Infra-red sensor IR-721 driver installation"
date: 2009-05-19
forum: Hardware
---

### Post by 7x1x on 2009-05-19
Hi,
I have an IR-721 infra-red sensor and can't figure out how to get it working. 
Can anyone help with this. Here is the readme, which I don't understand.

```
These driver files are here to help you get started.  You will at least 
need to install the driver into the kernel loadable modules directory
for IrDA (.../kernel/drivers/net/irda) and then insert the module (insmod).

The following modules are incompatible with this driver and on some
versions of Linux, these modules must be removed from the kernel:

   ir-usb
   irda-usb

You might need to insmod the "irda" module before starting.

Before running "make," check the values of LINUX_VERSION,
INLUDEDIR and MODPATH.

Before releasing anything, update the IRDA4210_VERSION string, which
gets embedded in the module.

All devices supported by this driver require a firmware patch to run.
Failing to install a patch into the device (or installing the wrong
patch) can result in a lockup of the USB bus (and the entire system).
For your protection, the driver will not allow you to open the device
unless you first apply the patch.

The "stir42xx" utility in the "tools" directory will install a patchfile.
The patch files are firmware that run in the device and are not available
with this distribution, since they are not covered under the GNU GPL.
Run "stir42xx --help" for more information.

The "sgtlpatch" script attemps to determine the version of the attached
device and will select the appropriate patch file that it finally passes
to the stir42xx utility.
```Any help would be appreciated, thanks.

---

### Post by stderr on 2009-05-19
Hi, welcome to Ubuntu Forums.

I'm not familiar with your IR sensor, but it would appear you have downloaded the source code for the driver. I'm assuming it's the correct source code for the receiver, your OS (32/64)... etc!

It sounds like you just have to compile, install and load the kernel module. If there's a file named INSTALL in the same dir as the README, read that, as it'll give you the process for compilation & installation. It normally involves steps like this, but you may not need all of them, or they may differ:

```

./configure
make 
sudo make install
```

( configure checks you have all the dependencies & configures the makefiles
( make does the compilation
( make install moves the compiled files to their correct places

As I say, check the INSTALL file (if there is one) to see what you need to do.

You can check the modules they say shouldn't be loaded aren't loaded - use something like this and if there's no output, that means they aren't loaded:

```
lsmod | grep ir-usb
lsmod | grep irda-usb
```

Then to insert a module you'd typically modprobe it:

```
sudo modprobe irda
```

That only inserts it temprarily until reboot; to make it permanent (i.e. when you've tested it & found it works OK), run this:

```
echo irda | sudo tee -a /etc/modules
```

( The equivalent of typing "sudo modprobe irda" every boot

It looks like you'll need to run whatever patch they've made before it works though. 

Bear in mind I haven't tried my suggestions with the code you have, and don't have that piece of hardware to test: I'm just trying to shed some light on the general process for you! Hope it helps.

;)

---

### Post by 7x1x on 2009-05-20
Hi, [stderr]("http://ubuntuforums.org/member.php?u=557294")

Thank you for the help, however I have run into a problem with the make command.

```
make: *** No rule to make target `/usr/src/linux-2.4/include/linux/irda.h', needed by `irda-usb.o'.  Stop.
```Would this be because I'm running a 2.6 kernel?

---

### Post by 7x1x on 2009-08-27
I fixed that error by editing makefile to say:
```

IRDA4210_VERSION = 0.1
LINUX_VERSION = 2.6.28-15-generic
SRC=/usr/src
INCLUDEDIR = $(SRC)/linux-headers-$(LINUX_VERSION)/include
MODPATH=/lib/modules/$(LINUX_VERSION)/kernel/drivers/net/irda
```And now receive the error:
```

make: *** [irda-usb.o] Error 1
```
which was preceded by a large amount of text.

---

