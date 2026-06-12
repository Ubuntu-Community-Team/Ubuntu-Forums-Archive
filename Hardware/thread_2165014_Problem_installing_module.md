---
title: "Problem installing module"
date: 2013-08-02
forum: Hardware
---

### Post by Murdoc_of_puts on 2013-08-02
Hello,

So I am having trouble integrating a module into my kernel.  The module that I'm looking to install is wistron_btns , I apparently need this module to turn on my wifi switch, as this key maps the led switches that control these things.  I have tried several different ways of doing this including:
sudo modprobe wistron_btns
modprobe fsam7400(another module that is supposed to do the same thing)
installing 12.10 & 13.04(which has video problems and won't load, but looking in the config file for the kernel, it's not set up for wistron_btns either)
I have looked at the dependencies listed for this module in the kernel, but can't find them(make xconfig)
here is the module information:
x86 Wistron laptop button interface (INPUT_WISTRON_BTNS)

CONFIG_INPUT_WISTRON_BTNS:

Say Y here for support of Wistron laptop button interfaces, used on
laptops of various brands, including Acer and Fujitsu-Siemens. If
available, mail and wifi LEDs will be controllable via /sys/class/leds.

To compile this driver as a module, choose M here: the module will
be called wistron_btns.

Symbol: INPUT_WISTRON_BTNS [=n]
Type : tristate
Prompt: x86 Wistron laptop button interface
Defined at drivers/input/misc/Kconfig:204

type: tristate
unknown property: symbol
    dep: !S390 && !UML && INPUT && INPUT_MISC && X86 && !X86_64
prompt: x86 Wistron laptop button interface
    dep: !S390 && !UML && INPUT && INPUT_MISC && X86 && !X86_64
select: INPUT_POLLDEV
    dep: !S390 && !UML && INPUT && INPUT_MISC && X86 && !X86_64
select: INPUT_SPARSEKMAP
    dep: !S390 && !UML && INPUT && INPUT_MISC && X86 && !X86_64
select: NEW_LEDS
    dep: !S390 && !UML && INPUT && INPUT_MISC && X86 && !X86_64
select: LEDS_CLASS
    dep: !S390 && !UML && INPUT && INPUT_MISC && X86 && !X86_64
select: CHECK_SIGNATURE
    dep: !S390 && !UML && INPUT && INPUT_MISC && X86 && !X86_64

defined at drivers/input/misc/Kconfig:204

CONFIG_INPUT_WISTRON_BTNS:
Say Y here for support of Wistron laptop button interfaces, used on
laptops of various brands, including Acer and Fujitsu-Siemens. If
available, mail and wifi LEDs will be controllable via /sys/class/leds.

To compile this driver as a module, choose M here: the module will
be called wistron_btns.

Location:
-> Device Drivers
-> Input device support
-> Generic input layer (needed for keyboard, mouse, ...) (INPUT [=y])
-> Miscellaneous devices (INPUT_MISC [=y])
Selects: INPUT_POLLDEV [=m] && INPUT_SPARSEKMAP [=m] && NEW_LEDS [=y] && LEDS_CLASS [=y] && CHECK_SIGNATURE [=y]

I've found all of them except the CHECK_SIGNATURE , and the NEW_LEDS( however there are other options that are activated that depend on this so I'm guessin it's enabled).

any help in this matter would be appreciated.

Or if anyone knows of a better easier way to do this I would be all ears.

Toshiba a665d-s091
ubuntu 12.04
kernel 3.2.0-51

---

### Post by ian-weisser on 2013-08-02
According to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346586](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346586) , the wistron_btns module has been included in the Ubuntu kernel since 2009.
You should not need to install it. 

```
    # Let's see if it's on my system
$ modprobe --list | grep wistron   
kernel/drivers/input/misc/wistron_btns.ko

    # Let's see which package installed it
$ dpkg -S /lib/modules/3.0.0-12-generic/kernel/drivers/input/misc/wistron_btns.ko
[COLOR=#ff0000]linux-image-3.0.0-12-generic[/COLOR]: /lib/modules/3.0.0-12-generic/kernel/drivers/input/misc/wistron_btns.ko

```
And sure enough, it is already in the Ubuntu kernel, installed by the main kernel package (not some add-on)

Normally, the kernel should recognize hardware and load the module for you.
If it's not doing so, you may have a different problem, or you may have uncovered a bug.

To load kernel modules manually, use the 'modprobe' command.
For example, 
```
sudo modprobe wistron_btns
```

---

### Post by Murdoc_of_puts on 2013-08-03
Yes, I know it's supposed to be there, but alas, c'est mon live'.

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module wistron_btns not found.


this is what happens when I modprobe the wistron_btns module

---

### Post by Murdoc_of_puts on 2013-08-03
So one update, I tried to recompile the kernel with "don't allow firmware to be made" unchecked, thinking that might help.

It didn't, and I got the exact same error message.

---

### Post by Murdoc_of_puts on 2013-08-05
SO doing a little tooling arround , and I found out that this wifi card will not work on a toshiba laptop, windows or linux, it's just a hardware incompatability.  I have no idea why, it's just one of those things.  
so the 
intel centrino advanced N 6235 card will not work on any toshiba laptop (from what I've found, esp a665d-so91 which is what i have).

---

