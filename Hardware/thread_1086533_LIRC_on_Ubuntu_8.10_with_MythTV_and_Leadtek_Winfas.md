---
title: "LIRC on Ubuntu 8.10 with MythTV and Leadtek Winfast XP TV Tuner Remote"
date: 2009-03-04
forum: Hardware
---

### Post by markdavidoff on 2009-03-04
[CENTER][COLOR="Red"][B]UPDATE:
I discovered that ubuntu has native support for this tv card, its infrared port and remote control (just not my remote)...and that LIRC probably never actually installed properly in the first place.
See post #6 below[/B][/COLOR][/CENTER]

I have been trying for about 6 hours to get LIRC to work properly with the remote that came with my winfast tuner card. I can't remember everything i have tried...

I installed lirc with
sudo apt-get install lirc

I chose my card in the list, and LIRC installed...however i got this in the console:

```
* Loading LIRC modules                                                  [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

```

I don't know if that's expected or not.
So anyways i then go about to try to use the remote. Volume up and down buttons trigger my volume up and down on the system - (ok...good)
hitting "0" enters a "0" in my application (good) as do the other numbers. Most of the other buttons don't work though...so i figured i will just make my own config.

unfortunately...mode2 gives me this:```

mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory
```

and irrecord remote_test.conf gives me this:
```
irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
```

so i enter: ps -e
but i don't see any lirc related processes

whenever i try to close it: /etc/init.d/lirc stop
i get:
```
 * Stopping remote control daemon(s): LIRC                               [fail] 
```
same goes with service lirc stop

Also, i noticed after the first install i tried that a reboot results in me not being able to use the remote until i do a complete remove and reinstall (without rebooting, of course)

I also tried compiling from the source using the setup.sh script included with the source after installing dialog with:
sudo apt-get install dialog

within setup.sh, I selected my card from the interface and hit "save configuration and run configure"

everything in configure seems ok except for these lines at the end:
```
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/Makefile
config.status: WARNING:  drivers/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_atiusb/Makefile
config.status: WARNING:  drivers/lirc_atiusb/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_bt829/Makefile
config.status: WARNING:  drivers/lirc_bt829/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_cmdir/Makefile
config.status: WARNING:  drivers/lirc_cmdir/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_dev/Makefile
config.status: WARNING:  drivers/lirc_dev/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_gpio/Makefile
config.status: WARNING:  drivers/lirc_gpio/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_i2c/Makefile
config.status: WARNING:  drivers/lirc_i2c/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_igorplugusb/Makefile
config.status: WARNING:  drivers/lirc_igorplugusb/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_ttusbir/Makefile
config.status: WARNING:  drivers/lirc_ttusbir/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_imon/Makefile
config.status: WARNING:  drivers/lirc_imon/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_it87/Makefile
config.status: WARNING:  drivers/lirc_it87/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_ite8709/Makefile
config.status: WARNING:  drivers/lirc_ite8709/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_mceusb/Makefile
config.status: WARNING:  drivers/lirc_mceusb/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_mceusb2/Makefile
config.status: WARNING:  drivers/lirc_mceusb2/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_parallel/Makefile
config.status: WARNING:  drivers/lirc_parallel/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_sasem/Makefile
config.status: WARNING:  drivers/lirc_sasem/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_serial/Makefile
config.status: WARNING:  drivers/lirc_serial/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_sir/Makefile
config.status: WARNING:  drivers/lirc_sir/Makefile.in seems to ignore the --datarootdir setting
config.status: creating drivers/lirc_streamzap/Makefile
config.status: WARNING:  drivers/lirc_streamzap/Makefile.in seems to ignore the --datarootdir setting
config.status: creating daemons/Makefile
config.status: WARNING:  daemons/Makefile.in seems to ignore the --datarootdir setting
config.status: creating tools/Makefile
config.status: WARNING:  tools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/Makefile
config.status: WARNING:  doc/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/man/Makefile
config.status: WARNING:  doc/man/Makefile.in seems to ignore the --datarootdir setting
config.status: creating config.h
config.status: executing default-1 commands

You will have to use the lirc_gpio kernel module.

Now enter 'make' and 'make install' to compile and install the package.
```

but i go and type make anyway but i get errors, so i can't make install.
```
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:55:47: error: ../drivers/media/video/bt8xx/bttv.h: No such file or directory
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:56:48: error: ../drivers/media/video/bt8xx/bttvp.h: No such file or directory
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:59:5: warning: "BTTV_VERSION_CODE" is not defined
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:60:2: error: #error "*******************************************************"
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:61:2: error: #error " Sorry, this driver needs bttv version 0.7.45 or       "
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:62:2: error: #error " higher. If you are using the bttv package, copy it to "
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:63:2: error: #error " the kernel					    "
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:64:2: error: #error "*******************************************************"
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:74: error: ‘BTTV_BOARD_UNKNOWN’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:103: error: ‘BTTV_BOARD_PXELVWPLTVPAK’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:105: error: ‘BTTV_BOARD_PXELVWPLTVPRO’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:107: error: ‘BTTV_BOARD_PV_BT878P_9B’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:109: error: ‘BTTV_BOARD_PV_BT878P_PLUS’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:115: error: ‘BTTV_BOARD_AVERMEDIA’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:119: error: ‘BTTV_BOARD_AVPHONE98’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:122: error: ‘BTTV_BOARD_AVERMEDIA98’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:139: error: ‘BTTV_BOARD_CHRONOS_VS2’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:143: error: ‘BTTV_BOARD_MIRO’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:145: error: ‘BTTV_BOARD_DYNALINK’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:151: error: ‘BTTV_BOARD_WINVIEW_601’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:158: error: ‘BTTV_BOARD_MAGICTVIEW061’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:160: error: ‘BTTV_BOARD_MAGICTVIEW063’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:162: error: ‘BTTV_BOARD_PHOEBE_TVMAS’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:171: error: ‘BTTV_BOARD_FLYVIDEO’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:173: error: ‘BTTV_BOARD_FLYVIDEO_98’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:175: error: ‘BTTV_BOARD_TYPHOON_TVIEW’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:187: error: ‘BTTV_BOARD_WINFAST2000’ undeclared here (not in a function)
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c: In function ‘build_key’:
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:240: error: implicit declaration of function ‘bttv_write_gpio’
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:244: error: implicit declaration of function ‘bttv_read_gpio’
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c: In function ‘get_queue’:
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:405: error: implicit declaration of function ‘bttv_get_gpio_queue’
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:405: warning: return makes pointer from integer without a cast
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c: In function ‘gpio_remote_init’:
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:455: error: implicit declaration of function ‘bttv_gpio_enable’
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c: In function ‘init_module’:
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:518: error: implicit declaration of function ‘bttv_get_cardinfo’
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:525: warning: comparison between pointer and integer
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:549: warning: comparison between pointer and integer
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:550: warning: assignment makes integer from pointer without a cast
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:552: warning: comparison between pointer and integer
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:553: warning: assignment makes integer from pointer without a cast
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:555: warning: comparison between pointer and integer
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:556: warning: assignment makes integer from pointer without a cast
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:558: warning: comparison between pointer and integer
/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.c:559: warning: assignment makes integer from pointer without a cast
make[6]: *** [/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[5]: *** [_module_/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio] Error 2
make[5]: Leaving directory `/usr/src/linux-headers-2.6.27-13-generic'
make[4]: *** [lirc_gpio.o] Error 2
make[4]: Leaving directory `/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/myth/Desktop/lirc-0.8.4a/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/myth/Desktop/lirc-0.8.4a/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/myth/Desktop/lirc-0.8.4a'
make: *** [all] Error 2
```



also, dmesg | grep IR gives me this
```
[   27.465821] input: bttv IR (card=34) as /devices/pci0000:00/0000:00:1e.0/0000:06:02.0/input/input4

```
and this from my secondary USB tuner (which is hidden behind the computer and has no access to remote anyways...also, i haven't configured it in LIRC, so i doubt it's a problem)
```
[   27.952552] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb5/5-7/input/input5
```

---

### Post by markdavidoff on 2009-03-04
[center]**bump!**
](*,)[/center]

---

### Post by markdavidoff on 2009-03-05
maybe someone can help me solve why:

1. the /dev/lirc device isn't created

2. i cannot compile from source

3. lircd doesn't appear in the process list when first installing, even though the remote works (until reboot of course)

---

### Post by markdavidoff on 2009-03-06
I tried a few more things:

1. completely removed lirc again...
2. reinstalled lirc with no options configured - no this time, however:
 a) /etc/init.d/lirc scripts don't work (such as start and stop)
 b) I can start lirc manually now by entering 'sudo lircd' in the terminal, and it shows up in the process list.
 c) Upon starting lircd, the /dev/lircd device is created - seemed like a good start.

3. I discovered that even when not running lircd, pressing the numbers on my remote still trigger numbers even though no config specified in install! It never did this before... very strange :/

4. As soon as i kill lircd, i have no access to /dev/lircd so I can't run irrecord or mode2! Attempting so gives me a connection refused error, even with sudo.

5. I thought i would go and try completely remove lircd again...then noticed that a package called liblircclient0 was installed with mythtv - maybe this is the cause of the problems? I don't know. I had mythtv on here the entire time, and it never registered buttons on its own without lirc.

6. Even though i completely removed lirc, it still registers buttons pressed on the remote now! it never did that before! This isn't good...i don't want to have to reformat and start again... i can't figure this out...

6. I thought i would try compile lirc from source with no configuration - this time, it compiles, and i also don't get the "You will have to use the lirc_gpio kernel module." message - rather a message such as "you don't have to install another kernel"
but lircd, mode2 and irrecord don't work without configuration (obviously), even though it was still registering buttons. So I uninstalled it.

The system Still registers buttons on my remote, which it didn't do before i reinstalled lirc with no config. How do i fix this? I seem to have dug a depper hole. How can the system register buttons on the remote without lirc??

BTW...when i say that the system is registering buttons on my remote, i mean that pressing "1" for instance generates a "1" on the terminal or in a text editor.

This behaviour is very peculiar...i need some SERIOUS help...

anyone? please? I have been using ubuntu for years and have never had a problem like this ever...

---

### Post by markdavidoff on 2009-03-06
is there a way to search for text in every file on the HDD?

I want to search for the term "0x00000000000048B7" which is a code for one of the remote buttons.

perhaps i can locate remnants of lirc somewhere...

---

### Post by markdavidoff on 2009-03-08
Last night i gave up and reformatted my computer...
As soon as ubuntu was reinstalled, and before installing any other packages, i went into a text editor...pointed my remote at the infrared receiver and pressed "1" on the remote.

What came up on the screen was a number "1" in the text editor.

**UBUNTU HAS NATIVE SUPPORT FOR THE TV TUNER AND ITS CARD!**

I also tried on the livecd, and pressing the numbers on the remote triggers numbers on the screen - without lirc!

So becuase ubuntu has kernel drivers for the tv card, it has kernel drivers for the infrared port and the remote that came with it.

Unfortunately, not all the buttons on my remote work properly with this built in support (they obviously didn't test all remotes that came with the card).

Also, unfortunately for me...i came to the conclusion that lirc was never working at all with the tv tuner and remote in the first place...in fact, it probably didn't even install properly, especially since some driver files (bttvp.h or something - shown above in the first post) are missing when trying to compile lirc for my card manually...

So now, i will have to settle for making my own serial IR receiver... if anybody knows any good USB ones that will work, that would be even better!
There's a schematic here that was on the LIRC website:
[http://stuff.nekhbet.ro/2006/07/10/make-an-infrared-remote-control-for-pc.html](http://stuff.nekhbet.ro/2006/07/10/make-an-infrared-remote-control-for-pc.html)

In fact, if anyone knows if i can get the infrared module that comes with card to work with either the card, or with the soundcard input, that would be great because it would mean that i don't have to go out and buy a new soldering iron (mine is stuffed :P) and look for parts

---

### Post by markdavidoff on 2009-03-09
[CENTER]
**BUMP!**
:roll:[/CENTER]

---

### Post by markdavidoff on 2009-04-06
Well, i went ahead and built my own IR receiver,

During the setup, i configured as a homebrew serial reciever

Lirc installed its device as /dev/lirc0 instead of /dev/lirc which was a minor complication.

Made my own config, and have been happy for about a month now.

I have submitted my config file to the LIRC developers in case others want to use it.

---

### Post by fillintheblanks on 2009-05-06
I am running 9.04 and have the same card with the same problem

the power button works, as do volume controls and number buttons

the rest of the buttons dont register at all

/etc/lirc/hardware.conf points to a /dev/lirc0 but there is no such module

any way to get this working ? :?


> cat /proc/bus/input/devices

I: Bus=0001 Vendor=107d Product=6606 Version=0001
N: Name="bttv IR (card=34)"
P: Phys=pci-0000:01:06.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/0000:01:06.0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=100003
B: KEY=10afc336 2150a48 0 0 0 404 80010007 80000190 4801 1e0000 4400 100000 10000ffc


---

### Post by fillintheblanks on 2009-05-08
finally.. I figured out how to get irw to register button presses


1. clean install of lirc

2. sudo lircd -H dev/input -d /dev/input/event4

3. irw


:guitar:

---

