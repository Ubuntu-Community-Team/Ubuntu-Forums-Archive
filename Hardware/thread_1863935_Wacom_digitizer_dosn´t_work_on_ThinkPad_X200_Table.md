---
title: "Wacom digitizer dosn´t work on ThinkPad X200 Tablet"
date: 2011-10-18
forum: Hardware
---

### Post by Kaedo on 2011-10-18
Hello Guys,
i read this Thread in our Forum:
[http://ubuntuforums.org/showthread.php?t=1833248&page=1](http://ubuntuforums.org/showthread.php?t=1833248&page=1)
and try every hint in the Thread. But my Digitizer won´t work.
It is a fresh installation i didn´t do anything. I just install synaptic.

I realy need the tablet for the university.

```
uname -a 
Linux test 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux


```
```
lsb_release -a 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

```

```

cat /var/log/Xorg.0.log

 11.048] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[    11.048] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    11.048] (II) LoadModule: "wacom"
[    11.049] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    11.049] (II) Module wacom: vendor="X.Org Foundation"
[    11.049]     compiled for 1.10.4, module version = 0.11.0
[    11.049]     Module class: X.Org XInput Driver
[    11.049]     ABI class: X.Org XInput driver, version 12.3
[    11.049] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    11.049] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    11.049] (**) Serial Wacom Tablet: always reports core events
[    11.049] (**) Option "Device" "/dev/ttyS4"
[    11.049] (**) Option "StopBits" "1"
[    11.049] (**) Option "DataBits" "8"
[    11.049] (**) Option "Parity" "None"
[    11.049] (**) Option "Vmin" "1"
[    11.049] (**) Option "Vtime" "10"
[    11.049] (**) Option "FlowControl" "Xoff"
[    11.049] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    11.049] (II) Serial Wacom Tablet: other types will be automatically added.
[    14.303] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    14.303] (WW) Serial Wacom Tablet stylus: Query failed with 19200 baud. Trying 38400.
[    17.557] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    17.557] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    17.557] (EE) PreInit returned 8 for "Serial Wacom Tablet stylus"
[    17.557] (II) UnloadModule: "wacom"
[    17.557] (II) Unloading wacom

```

```
cat /usr/share/X11/xorg.conf.d/50-wacom.conf
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM|"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
        #Option "Button2" "2"
        #Option "Button3" "3"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "Device" "/dev/ttyS4"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
    Option "Device" "/dev/ttyS4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection

```


```
ls /usr/share/X11/xorg.conf.d/10-evdev.conf             50-synaptics.conf  50-wacom.conf~
11-evdev-quirks.conf      50-vmmouse.conf    51-synaptics-quirks.conf
11-evdev-trackpoint.conf  50-wacom.conf

```

```
cat /lib/udev/rules.d/40-inputattach.rules
# Attach Wacom W8001 devices
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="FUJ02e5", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 19200 --w8001 /dev/%k"
SUBSYSTEM=="tty", KERNEL=="ttyS[0-9]*", ATTRS{id}=="WACf00c", ACTION=="add|change", RUN+="/lib/udev/inputattach --daemon --baud 38400 --w8001 /dev/%k" 
```



```
dmesg | grep ttyS
[    0.954300] 00:0a: ttyS4 at I/O 0x200 (irq = 5) is a 16550A
[    0.974573] 0000:00:03.3: ttyS5 at I/O 0x1830 (irq = 17) is a 16550A

```



```
dmesg | grep ttyS4
[    0.954300] 00:0a: ttyS4 at I/O 0x200 (irq = 5) is a 16550A
```

```
cat /etc/serial.conf 
/dev/ttyS4 port 0x200 irq 5 baud_base 34800
```

```


kaedo@test:~$ sudo setserial -g /dev/ttyS4
/dev/ttyS4, UART: 16550A, Port: 0x0200, IRQ: 5
kaedo@test:~$ sudo setserial -g /dev/ttyS5
/dev/ttyS5, UART: 16550A, Port: 0x1830, IRQ: 17

root@test:/home/kaedo# setserial -g /dev/ttyS5
/dev/ttyS5, UART: 16550A, Port: 0x1830, IRQ: 17
root@test:/home/kaedo# setserial -g /dev/ttyS4
/dev/ttyS4, UART: 16550A, Port: 0x0200, IRQ: 5



```


when i do : xxd /dev/ttyS4
and get with the pen in the near of the tablet i got reaction

```
0000000: 001e 0cf8 600c 8060 ccf8 0080 8600 0000  ....`..`........
0000010: 1e0c f8f8 60c0 60c3 f800 00f8 0000 001e  ....`.`.........
0000020: 0cf8 0660 c060 3cf8 0080 fe00 0000 9e60  ...`.`<........`
0000030: cc06 3ccc 78fc 0080 f800 0000 9e60 fc66  ..<.x........`.f
0000040: 3c80 6000 f800 8086 0000 009e 60fc 1e30  <.`.........`..0
0000050: 8060 ccc3 0080 e000 0000 9e60 cc3c 1878  .`.........`.<.x
0000060: 3060 fc00 8080 0000 001e 03f8 783c 8060  0`..........x<.`
0000070: c3e0 0000 fe00 0000 1e03 989e 18f0 3006  ..............0.
0000080: fc00 00fe 0000 009e 8018 cce6 0603 fe00  ................
0000090: 8080 0000 009e 80f8 e098 06f3 f3fe 0080  ................
00000a0: fe00 0000 9e80 f878 007e 0386 e600 80e0  .......x.~......
00000b0: 0000 001e 00f8 6033 7e03 7830 0080 9800  ......`3~.x0....
00000c0: 0000 1e00 9818 f306 f33c fe00 00f8 0000  .........<......
00000d0: 001e 00f8 007e 031e 0c00 00fe 0000 009e  .....~..........
00000e0: 6000 e606 c306 ff00 00f8 0000 009e e060  `..............`
00000f0: 307e 03e6 8000 00f8 0000 009e e0e0 867e  0~.............~
0000100: 0386 8000 809e 0000 009e e080 603f 60c3  ............`?`.
0000110: c000 80f8 0000 009e e07e 007e 03fe 8000  .........~.~....
0000120: 8086 0000 001e ff30 7e7e 60c0 e000 80e0  .......0~~`.....
0000130: 0000 001e fff0 869e 7e03 780c 0000 f800  ........~.x.....
0000140: 0000 1eff f09e 663f 6030 f800 8098 0000  ......f?`0......
0000150: 001e ff30 7e66 3f60 0fcc 0000 fe00 0000  ...0~f?`........
0000160: 1eff f01e 307e 0306 e600 8098 0000 001e  ....0~..........
0000170: ff30 7ecc 0633 e600 0000 0000 1eff f060  .0~..3.........`
```

---

### Post by Favux on 2011-10-18
Hi Kaedo,

Welcome to Ubuntu forums!

There's a few other serial tablets reporting the same problem.

Let's try checking if there is a conflict between the pnp management and the IO chip providing the serial ports.  We'll add *pnpacpi=off* to the kernel command line boot options.  I think it is worth a shot even though there doesn't seem to be an IRQ conflict.  So edit the /etc/default/grub file.
```
gksudo gedit /etc/default/grub
```
and change:
```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash pnpacpi=off”
```
Then run:
```
sudo update-grub
```
and reboot.

---

### Post by Kaedo on 2011-10-18
thx you. i read in this forum since 2 years and never had a problem. But know i need the help.
I have grub 2 so i didn´t know exactly if i done it the right way:

```
root@test:/home/kaedo# cat /etc/grub.d/
00_header        20_linux_xen     40_custom        
05_debian_theme  20_memtest86+    41_custom        
10_linux         30_os-prober     README           
root@Dragoncorp:/home/kaedo# cat /etc/default/grub
grub   grub~  
root@Dragoncorp:/home/kaedo# cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=”quiet pnpacpi=off”
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



```


```
root@test:/home/kaedo# update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

nothing change i got the same Xorg log.

---

### Post by Favux on 2011-10-18
Alright, then that doesn't seem to be the problem.  Go ahead and remove it.  Just remember to add *splash* back in.

Not having much luck with this.  I don't know if it is a problem with the new serial stack Ubuntu introduced with Natty (11.04) or if they've introduced a bug in xf86-input-wacom.

Which version of xf86-input-wacom do you have?  The Oneiric default 0.11.0?
```
xsetwacom -V
```

---

### Post by Kaedo on 2011-10-18
```
root@test:/home/kaedo# xsetwacom -V
0.11.0
```

---

### Post by Favux on 2011-10-18
OK, my suggestion is to try to downgrade xf86-input-wacom.  Since the problem seemed to start with 0.10.11 let's see if you can compile the 0.10.10 tar with the 3.0 kernel and Xorg X server 1.10.4.  The tar is here:  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/)

The instructions for compiling the tar are in the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") part II. b).

If your X200 works then we know the problem is with xf86-input-wacom.

---

### Post by Kaedo on 2011-10-18
do i have to copy some files to a special location or is the make enaugh?

because after compiling and rebooting i got the same:
```

xsetwacom -V
0.11.0


```


I used:

xf86-input-wacom-0.10.10

---

### Post by Favux on 2011-10-18
The
```
sudo make install
```
should have copied the files into place.  Sounds like it compiled which is a good start!  :)

---

### Post by Kaedo on 2011-10-18
my xserver crashed on start, after rebooting.

i try to get the log
so i take a look in the log file:

It is in my opinion the same file like above but after the EE PreInit returned 8 for Serial Wacom Tablet stylus
It try to Backtrase and during this it got a segmentation fault.


So i got my X Server back online. I renamed my 50-wacom.conf to 50-wacom.conf.bak so that the x Server didn´t use it.

but i dosn´t know why it got killed by the .conf

I try to install a knewer xf86-input-wacom

---

### Post by Favux on 2011-10-18
You can just reinstall xserver-xorg-input-wacom to get the default back.
```
sudo apt-get install xserver-xorg-input-wacom
```
So even with the downgraded xf86-input-wacom you're still seeing?
```
[    14.303] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    14.303] (WW) Serial Wacom Tablet stylus: Query failed with 19200 baud. Trying 38400.
[    17.557] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    17.557] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    17.557] (EE) PreInit returned 8 for "Serial Wacom Tablet stylus"
[    17.557] (II) UnloadModule: "wacom"
[    17.557] (II) Unloading wacom
```
That would seem to argue it is not xf86-input-wacom that is the problem.  What do you think?


Edit:  I don't know if this problem with a Toshiba M200 in Maverick is related but I'll throw it into the mix:  [http://ubuntuforums.org/showthread.php?t=1703936](http://ubuntuforums.org/showthread.php?t=1703936)

---

### Post by Kaedo on 2011-10-18
i wouldn´t say that it is the xf86-input-wacom.

I install the 0.11.1 version and the X server is back and work. i try to add the 

Option "Device" "/dev/ttyS4"
statements to my 50-wacom.conf and will see if it crash.

---

### Post by Kaedo on 2011-10-18
i moved my old 50-wacom.conf back and restart X and the good news. my X server dosn´t crash. The bad news: it still won´t work.
I give the thread a hint from the toshiba m200

---

### Post by Kaedo on 2011-10-18
I go through the thread and try the things you advise.
But nothing seems to help:
i try to change the 
 gedit /lib/udev/rules.d/69-xserver-xorg-input-wacom.rules it dosn´t work
the creation of the xorg.conf with the few commands didn´t work either.

---

### Post by Kaedo on 2011-10-18
success!!!!! Thx you so much for the help. I will check if the new xf86-input-wacom (0.11.1) was the solution or the creation of the basic xorg.conf

```

 1591.471] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  1591.471] (**) Serial Wacom Tablet eraser: always reports core events
[  1591.471] (**) Option "Device" "/dev/ttyS4"
[  1591.471] (**) Option "BaudRate" "38400"
[  1591.471] (**) Option "StopBits" "1"
[  1591.471] (**) Option "DataBits" "8"
[  1591.471] (**) Option "Parity" "None"
[  1591.471] (**) Option "Vmin" "1"
[  1591.471] (**) Option "Vtime" "10"
[  1591.471] (**) Option "FlowControl" "Xoff"
[  1591.471] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=1 maxY=26338 maxZ=52 resX=100000 resY=100000  tilt=disabled
[  1591.471] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0a/tty/ttyS4"
[  1591.471] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
[  1591.471] (**) Serial Wacom Tablet eraser: (accel) keeping acceleration scheme 1
[  1591.471] (**) Serial Wacom Tablet eraser: (accel) acceleration profile 0
[  1591.471] (**) Serial Wacom Tablet eraser: (accel) acceleration factor: 2.000
[  1591.471] (**) Serial Wacom Tablet eraser: (accel) acceleration threshold: 4
[  1591.496] (WW) Serial Wacom Tablet eraser: bad data at 1 v=c7 l=9
[  1591.506] (WW) Serial Wacom Tablet eraser: bad data at 4 v=fb l=9
[  1591.732] (II) intel(0): EDID vendor "LEN", prod id 16401
[  1591.732] (II) intel(0): Printing DDC gathered Modelines:
[  1591.732] (II) intel(0): Modeline "1280x800"x0.0   71.04  1280 1332 1396 1451  800 803 806 816 -hsync -vsync (49.0 kHz)
[  1592.572] (II) intel(0): EDID vendor "LEN", prod id 16401
[  1592.572] (II) intel(0): Printing DDC gathered Modelines:
[  1592.572] (II) intel(0): Modeline "1280x800"x0.0   71.04  1280 1332 1396 1451  800 803 806 816 -hsync -vsync (49.0 kHz)
[  1593.210] (II) intel(0): EDID vendor "LEN", prod id 16401
[  1593.210] (II) intel(0): Printing DDC gathered Modelines:
[  1593.210] (II) intel(0): Modeline "1280x800"x0.0   71.04  1280 1332 1396 1451  800 803 806 816 -hsync -vsync (49.0 kHz)
[  1593.995] (II) intel(0): EDID vendor "LEN", prod id 16401
[  1593.995] (II) intel(0): Printing DDC gathered Modelines:
[  1593.995] (II) intel(0): Modeline "1280x800"x0.0   71.04  1280 1332 1396 1451  800 803 806 816 -hsync -vsync (49.0 kHz)
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=8c l=5
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=82 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 2 v=f9 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=82 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 2 v=fe l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=82 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=e0 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 2 v=fc l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 2 v=92 l=5
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=d8 l=5
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 2 v=fb l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=f8 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=90 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 2 v=82 l=5
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=e3 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=90 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=80 l=5
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=d8 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=ec l=5
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 3 v=90 l=5
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=fc l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=c7 l=5
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 2 v=8c l=5
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=d8 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 4 v=8c l=5
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=e0 l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=d8 l=5
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 3 v=8c l=9
[  1594.576] (WW) Serial Wacom Tablet eraser: bad data at 1 v=d8 l=9
[  1594.627] (WW) Serial Wacom Tablet eraser: bad data at 1 v=d8 l=5
[  1594.663] (WW) Serial Wacom Tablet eraser: bad data at 1 v=f0 l=9
[  1594.671] (WW) Serial Wacom Tablet eraser: bad data at 1 v=f0 l=9
[  1594.678] (WW) Serial Wacom Tablet eraser: bad data at 1 v=f0 l=9
[  1594.686] (WW) Serial Wacom Tablet eraser: bad data at 1 v=f0 l=9
[  1594.694] (WW) Serial Wacom Tablet eraser: bad data at 1 v=90 l=9
[  1594.701] (WW) Serial Wacom Tablet eraser: bad data at 1 v=f0 l=9
[  1594.711] (WW) Serial Wacom Tablet eraser: bad data at 1 v=90 l=9
[  1594.716] (WW) Serial Wacom Tablet eraser: bad data at 6 v=fe l=9
[  1594.800] (WW) Serial Wacom Tablet eraser: bad data at 1 v=d8 l=9
[  1594.820] (WW) Serial Wacom Tablet eraser: bad data at 3 v=ee l=9
[  1594.823] (WW) Serial Wacom Tablet eraser: bad data at 2 v=e0 l=9
[  1594.836] (WW) Serial Wacom Tablet eraser: bad data at 2 v=90 l=9
[  1594.836] (WW) Serial Wacom Tablet eraser: bad data at 1 v=ec l=5
[  1594.838] (WW) Serial Wacom Tablet eraser: bad data at 2 v=c0 l=9
[  1594.860] (WW) Serial Wacom Tablet eraser: bad data at 1 v=db l=9
[  1594.926] (WW) Serial Wacom Tablet eraser: bad data at 2 v=c3 l=5
[  1594.937] (WW) Serial Wacom Tablet eraser: bad data at 2 v=8e l=9
[  1594.937] (WW) Serial Wacom Tablet eraser: bad data at 1 v=d8 l=9
[  1594.942] (WW) Serial Wacom Tablet eraser: bad data at 2 v=8e l=9
[  1594.942] (WW) Serial Wacom Tablet eraser: bad data at 3 v=f0 l=9
[  1594.949] (WW) Serial Wacom Tablet eraser: bad data at 2 v=92 l=9
[  1594.949] (WW) Serial Wacom Tablet eraser: bad data at 3 v=e0 l=5
[  1594.982] (WW) Serial Wacom Tablet eraser: bad data at 2 v=c8 l=9
[  1594.987] (WW) Serial Wacom Tablet eraser: bad data at 1 v=dc l=9
[  1594.997] (WW) Serial Wacom Tablet eraser: bad data at 3 v=c3 l=9
[  1595.003] (WW) Serial Wacom Tablet eraser: bad data at 2 v=ec l=9
[  1595.012] (WW) Serial Wacom Tablet eraser: bad data at 3 v=c3 l=9
[  1595.017] (WW) Serial Wacom Tablet eraser: bad data at 1 v=8c l=9
[  1595.020] (WW) Serial Wacom Tablet eraser: bad data at 1 v=fb l=9
[  1595.027] (WW) Serial Wacom Tablet eraser: bad data at 1 v=e0 l=9
[  1595.044] (WW) Serial Wacom Tablet eraser: bad data at 1 v=c7 l=9
[  1595.050] (WW) Serial Wacom Tablet eraser: bad data at 4 v=fc l=9
[  1595.057] (WW) Serial Wacom Tablet eraser: bad data at 4 v=fc l=9
[  1595.063] (WW) Serial Wacom Tablet eraser: bad data at 3 v=fc l=9
[  1595.072] (WW) Serial Wacom Tablet eraser: bad data at 3 v=9e l=9
[  1595.072] (WW) Serial Wacom Tablet eraser: bad data at 1 v=f8 l=5
[  1595.078] (WW) Serial Wacom Tablet eraser: bad data at 2 v=92 l=9
[  1595.078] (WW) Serial Wacom Tablet eraser: bad data at 3 v=82 l=5
[  1595.084] (WW) Serial Wacom Tablet eraser: bad data at 1 v=f8 l=9
[  1595.085] (WW) Serial Wacom Tablet eraser: bad data at 2 v=ec l=9
[  1595.102] (WW) Serial Wacom Tablet eraser: bad data at 1 v=c3 l=9
[  1595.117] (WW) Serial Wacom Tablet eraser: bad data at 1 v=80 l=9
[  1595.117] (WW) Serial Wacom Tablet eraser: bad data at 1 v=d8 l=9
[  1596.022] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm

``````

xsetwacom --list
Serial Wacom Tablet stylus          id: 13    type: STYLUS    
Serial Wacom Tablet eraser          id: 14    type: ERASER 

```

---

### Post by Kaedo on 2011-10-18
Here are my final files, for those who have the same problem:

```
root@test:/home/kaedo# cat /etc/X11/xorg.conf 
Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"         "/dev/ttyS4"
    Option        "Type"           "stylus"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"         "/dev/ttyS4"
    Option        "Type"           "eraser"
EndSection

Section "ServerLayout"
    Identifier    "X.org Configured"
    InputDevice   "stylus"
    InputDevice   "eraser"
EndSection

``````
root@test:/home/kaedo# cat /usr/share/X11/xorg.conf.d/50-wacom.conf
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM|"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
        #Option "Button2" "2"
        #Option "Button3" "3"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "Device" "/dev/ttyS4"
        Option "BaudRate" "38400"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
    Option "Device" "/dev/ttyS4"
        Option "BaudRate" "38400"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection
``````

root@test:/home/kaedo# cat /etc/serial.conf 
/dev/ttyS4 port 0x200 irq 5 baud_base 34800
```

---

### Post by Kaedo on 2011-10-18
i don´t know what exactly happend but the problem is back:

```
[    23.712] (**) Option "FlowControl" "Xoff"
[    23.712] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    23.713] (II) Serial Wacom Tablet: other types will be automatically added.
[    26.966] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    26.966] (WW) Serial Wacom Tablet stylus: Query failed with 19200 baud. Trying 38400.
[    30.220] (WW) Serial Wacom Tablet stylus: Waited too long for answer (failed after 3 tries).
[    30.220] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    30.220] (EE) PreInit returned 8 for "Serial Wacom Tablet stylus"
[    30.220] (II) UnloadModule: "wacom"
[    30.220] (II) Unloading wacom

```

---

### Post by Favux on 2011-10-18
Shoot.  I'm stumped.  I'll go over it and see if I can think of something.

---

### Post by Kaedo on 2011-10-18
the /usr/share/X11/xorg.conf.d/50-wacom.conf was different.

i had to add again
```
    Option "Device" "/dev/ttyS4"
        Option "BaudRate" "38400"

``` 

now i got this
```
 329.753] (**) Option "xkb_rules" "evdev"
[   329.753] (**) Option "xkb_model" "pc105"
[   329.753] (**) Option "xkb_layout" "de"
[   329.753] (**) Option "xkb_variant" "nodeadkeys"
[   329.755] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[   329.755] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[   329.755] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[   329.755] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   329.755] (**) Serial Wacom Tablet: always reports core events
[   329.755] (**) Option "Device" "/dev/ttyS4"
[   329.755] (WW) Serial Wacom Tablet: device file already in use by stylus. Ignoring.
[   329.755] (EE) PreInit returned 8 for "Serial Wacom Tablet"
[   329.755] (II) UnloadModule: "wacom"
[   329.755] (II) Unloading wacom
[   329.772] (WW) eraser: bad data at 1 v=fc l=9
[   329.779] (WW) eraser: bad data at 1 v=fc l=9
[   329.794] (WW) eraser: bad data at 1 v=fc l=9
[   329.796] (WW) eraser: bad data at 4 v=fc l=9
[   329.876] (WW) eraser: bad data at 1 v=e0 l=9
[   329.973] (II) intel(0): EDID vendor "LEN", prod id 16401
[   329.973] (II) intel(0): Printing DDC gathered Modelines:
[   329.973] (II) intel(0): Modeline "1280x800"x0.0   71.04  1280 1332 1396 1451  800 803 806 816 -hsync -vsync (49.0 kHz)
[   330.280] (WW) eraser: bad data at 1 v=e0 l=9
[   330.280] (WW) eraser: bad data at 7 v=fc l=9
[   330.280] (WW) eraser: bad data at 1 v=fc l=9
[   330.280] (WW) eraser: bad data at 6 v=fc l=9
[   330.280] (WW) eraser: bad data at 3 v=fc l=9
[   330.280] (WW) eraser: bad data at 7 v=fc l=9
[   330.280] (WW) eraser: bad data at 1 v=fc l=9
[   330.280] (WW) eraser: bad data at 1 v=fc l=9
[   330.560] (WW) eraser: bad data at 3 v=e0 l=9
[   330.560] (WW) eraser: bad data at 1 v=e0 l=9
[   330.560] (WW) eraser: bad data at 1 v=e0 l=9
[   330.560] (WW) eraser: bad data at 1 v=e0 l=9
[   330.560] (WW) eraser: bad data at 3 v=e0 l=9
[   330.560] (WW) eraser: bad data at 3 v=e0 l=9
[   330.560] (WW) eraser: bad data at 3 v=e0 l=9
[   330.560] (WW) eraser: bad data at 1 v=fc l=9
```

but also

```
xsetwacom --list
stylus                              id: 6    type: STYLUS    
eraser                              id: 7    type: ERASER
```

How i can verify that the stylus still work?

---

### Post by Kaedo on 2011-10-18
I mv the /etc/X11/xorg.conf to /etc/X11/xorg.conf.bak

know i have 
cat /var/log/Xorg.0.log
```

...
[   109.074] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[   109.074] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[   109.074] (II) LoadModule: "wacom"
[   109.074] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   109.074] (II) Module wacom: vendor="X.Org Foundation"
[   109.074]     compiled for 1.10.4, module version = 0.11.1
[   109.074]     Module class: X.Org XInput Driver
[   109.074]     ABI class: X.Org XInput driver, version 12.3
[   109.074] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[   109.074] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   109.074] (**) Serial Wacom Tablet: always reports core events
[   109.074] (**) Option "Device" "/dev/ttyS4"
[   109.075] (**) Option "BaudRate" "38400"
[   109.075] (**) Option "StopBits" "1"
[   109.075] (**) Option "DataBits" "8"
[   109.075] (**) Option "Parity" "None"
[   109.075] (**) Option "Vmin" "1"
[   109.075] (**) Option "Vtime" "10"
[   109.075] (**) Option "FlowControl" "Xoff"
[   109.075] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[   109.075] (II) Serial Wacom Tablet: other types will be automatically added.
[   110.855] (WW) Serial Wacom Tablet stylus: Query failed with 38400 baud. Trying 19200.
[   111.360] (II) Serial Wacom Tablet stylus: serial tablet id 0x9F.
[   111.360] (--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
[   111.360] (--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=0 maxY=0 maxZ=0 resX=100000 resY=100000  tilt=disabled
[   111.360] (II) Serial Wacom Tablet stylus: hotplugging dependent devices.
[   111.360] (II) Serial Wacom Tablet stylus: hotplugging completed.
[   111.360] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0a/tty/ttyS4"
[   111.360] (II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS)
[   111.361] (**) Serial Wacom Tablet stylus: (accel) keeping acceleration scheme 1
[   111.361] (**) Serial Wacom Tablet stylus: (accel) acceleration profile 0
[   111.361] (**) Serial Wacom Tablet stylus: (accel) acceleration factor: 2.000
[   111.361] (**) Serial Wacom Tablet stylus: (accel) acceleration threshold: 4
[   111.361] (**) Option "BaudRate" "38400"
[   111.376] (**) Serial Wacom Tablet eraser: Applying InputClass "Wacom serial class"
[   111.376] (II) Using input driver 'wacom' for 'Serial Wacom Tablet eraser'
[   111.376] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   111.376] (**) Serial Wacom Tablet eraser: always reports core events
[   111.376] (**) Option "Device" "/dev/ttyS4"
[   111.376] (**) Option "BaudRate" "38400"
[   111.376] (**) Option "StopBits" "1"
[   111.376] (**) Option "DataBits" "8"
[   111.376] (**) Option "Parity" "None"
[   111.376] (**) Option "Vmin" "1"
[   111.376] (**) Option "Vtime" "10"
[   111.376] (**) Option "FlowControl" "Xoff"
[   111.376] (--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=0 maxY=0 maxZ=0 resX=100000 resY=100000  tilt=disabled
[   111.376] (**) Option "config_info" "udev:/sys/devices/pnp0/00:0a/tty/ttyS4"
[   111.376] (II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
[   111.377] (**) Serial Wacom Tablet eraser: (accel) keeping acceleration scheme 1
[   111.377] (**) Serial Wacom Tablet eraser: (accel) acceleration profile 0
[   111.377] (**) Serial Wacom Tablet eraser: (accel) acceleration factor: 2.000
[   111.377] (**) Serial Wacom Tablet eraser: (accel) acceleration threshold: 4
[   111.442] (WW) Serial Wacom Tablet eraser: bad data at 1 v=fc l=9
[   111.577] (II) intel(0): EDID vendor "LEN", prod id 16401
[   111.577] (II) intel(0): Printing DDC gathered Modelines:
[   111.577] (II) intel(0): Modeline "1280x800"x0.0   71.04  1280 1332 1396 1451  800 803 806 816 -hsync -vsync (49.0 kHz)
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 1 v=fc l=9
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 1 v=f8 l=9
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 1 v=c3 l=9
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 1 v=c3 l=9
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 4 v=fb l=9
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 1 v=df l=9
[   112.152] (WW) Serial Wacom Tablet eraser: bad data at 3 v=82 l=9
[   112.152] (WW) Serial Wacom Tablet eraser: bad data at 1 v=c3 l=9
[   112.238] (II) intel(0): EDID vendor "LEN", prod id 16401
[   112.238] (II) intel(0): Printing DDC gathered Modelines:
[   112.238] (II) intel(0): Modeline "1280x800"x0.0   71.04  1280 1332 1396 1451  800 803 806 816 -hsync -vsync (49.0 kHz)
[   112.899] (II) intel(0): EDID vendor "LEN", prod id 16401
[   112.899] (II) intel(0): Printing DDC gathered Modelines:
[   112.899] (II) intel(0): Modeline "1280x800"x0.0   71.04  1280 1332 1396 1451  800 803 806 816 -hsync -vsync (49.0 kHz)
[   113.522] (WW) Serial Wacom Tablet eraser: bad data at 3 v=fc l=9
[   113.555] (WW) Serial Wacom Tablet eraser: bad data at 2 v=e0 l=9
[   113.566] (WW) Serial Wacom Tablet eraser: bad data at 5 v=80 l=9
[   113.570] (WW) Serial Wacom Tablet eraser: bad data at 1 v=f8 l=9
[   113.575] (WW) Serial Wacom Tablet eraser: bad data at 6 v=f8 l=9
[   113.585] (WW) Serial Wacom Tablet eraser: bad data at 2 v=9c l=9
...

```and

```

kaedo@test:~$ xsetwacom --list
Serial Wacom Tablet stylus          id: 13    type: STYLUS    
Serial Wacom Tablet eraser          id: 14    type: ERASER 

```

With the following steps i got a working tablet:

1. normal boot => no tablet possible
2. enter ```
sudo pkill X
``` and during restart of X I put my stylus pen on my Tabletscreen

With this combination my X restart is noticeable faster.
After the restart i can put my stylus on the tabletscreen and in the /var/log/Xorg.0.log
i got new entries like

```
[    75.014] (WW) Serial Wacom Tablet eraser: bad data at 1 v=e2 l=9
```

i still couldn´t move my mouse after this steps. Does anyone know how?

---

### Post by Favux on 2011-10-19
> during restart of X I put my stylus pen on my Tabletscreen...i still couldn´t move my mouse after this steps.

That seems to indicate some sort of conflict as to what the core/slave pointers are.  What does the entire output of *xinput list* look like when the stylus is working but the mouse isn't?

Stuff like this:
```
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 1 v=fc l=9
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 1 v=f8 l=9
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 1 v=c3 l=9
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 1 v=c3 l=9
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 4 v=fb l=9
[   111.872] (WW) Serial Wacom Tablet eraser: bad data at 1 v=df l=9
[   112.152] (WW) Serial Wacom Tablet eraser: bad data at 3 v=82 l=9
[   112.152] (WW) Serial Wacom Tablet eraser: bad data at 1 v=c3 l=9

```
seems to indicate a problem with xf86-input-wacom.  Can you get useful output with isdv4-serial-debugger?
```
isdv4-serial-debugger -b 38400
```
The isdv4-serial-debugger executable should be in /usr/bin.

---

### Post by Kaedo on 2011-10-20
```
kaedo@test:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse             id=10    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; UVC Camera (17ef:480c)                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=13    [slave  keyboard (3)]
```

When i go randomly over my screen with the pen i go this:

```
kaedo@test:~$ isdv4-serial-debugger -b 38400 /dev/ttyS4
TABLET: version: 0
TABLET: x max: 387 y max 384
TABLET: tilt_x max: 254 tilt_y max 0
TABLET: pressure max: 62
TOUCH version: 13116
TOUCH x max: 15744 y max 8065
TOUCH panel resolution: 30
TOUCH capacity resolution: 255
TOUCH sensor id: 4
PEN    1319094799:49155/   24 | pressure: 972 |  224/128 |        |
TOUCH    1319094799:15600/ 3852 | capacity: 771 | 0 | 
PEN    1319094799:64512/ 1016 | pressure:   0 |  158/120 |    s e |
PEN    1319094799:  123/57536 | pressure: 992 |   48/ 12 |    s e |
PEN    1319094799:49155/   24 | pressure: 204 |    3/102 |    s e |
TOUCH    1319094799:  972/12291 | capacity: 31896 | 0 | 
PEN    1319094799: 3888/49167 | pressure: 134 |   96/ 48 |        |
TOUCH    1319094800: 3084/24728 | capacity: 3084 | 0 | 
TOUCH    1319094800: 3084/32408 | capacity: 3084 | 0 | 
TOUCH    1319094800:    0/   30 | capacity: 26160 | 0 | 
PEN    1319094800:15360/   27 | pressure: 972 |  224/152 |        |
PEN    1319094800:52737/12922 | pressure: 120 |  128/230 |    s e |
PEN    1319094801:12288/   24 | pressure: 972 |   96/240 |    s e |
PEN    1319094801:    3/   24 | pressure: 972 |   96/195 |    s e |
PEN    1319094802:52226/    1 | pressure: 542 |  240/ 30 |        |
PEN    1319094802:49968/64515 | pressure: 768 |  204/240 |        |
TOUCH    1319094802: 3324/  102 | capacity: 7884 | 0 | 
PEN    1319094802:49155/   24 | pressure: 204 |    3/ 96 |        |
PEN    1319094802: 3707/49763 | pressure: 768 |    0/  0 |    s e |
PEN    1319094804:12288/   24 | pressure: 204 |  248/158 |    s e |
PEN    1319094804:64525/61683 | pressure: 902 |  128/128 |        |
PEN    1319094804:64512/   27 | pressure: 204 |   96/ 15 |    s e |
TOUCH    1319094805: 1023/16536 | capacity: 31872 | 0 | 
TOUCH    1319094805:15600/28800 | capacity: 29568 | 0 | 
TOUCH    1319094805:15600/ 3084 | capacity: 29568 | 0 | 
PEN    1319094805:52227/    3 | pressure: 158 |   48/248 |        |
TOUCH    1319094805:15408/ 8166 | capacity: 15552 | 0 | 
TOUCH    1319094805:15408/ 1542 | capacity: 1932 | 0 | 
TOUCH    1319094805:28806/19590 | capacity: 16510 | 0 | 
TOUCH    1319094807:16368/  768 | capacity: 29568 | 0 | 
PEN    1319094807:    3/    3 | pressure: 926 |   48/102 |        |
TOUCH    1319094807:16176/ 8088 | capacity: 3888 | 0 | 
TOUCH    1319094807:12480/24582 | capacity: 12288 | 0 | 
TOUCH    1319094807:    6/  408 | capacity: 384 | 0 | 
PEN    1319094807:15363/  123 | pressure:   0 |    0/ 96 |        |
TOUCH    1319094807: 3843/ 1542 | capacity: 12543 | 0 | 
PEN    1319094807:12288/    0 | pressure:  30 |   24/ 15 |        |
PEN    1319094807:49347/61443 | pressure:   0 |    0/  0 |        |
PEN    1319094808:61440/   24 | pressure: 972 |   12/  6 |    s e |
TOUCH    1319094810:15600/    0 | capacity: 972 | 0 | 
PEN    1319094811:15363/   24 | pressure: 204 |   12/230 |    s e |
PEN    1319094811:    3/   24 | pressure: 204 |  134/128 |        |
```

Very interesting is, that my earaser (i mean the other side of the pen) wasn´t recognized by the isdv4-serial-debugger.

---

### Post by Favux on 2011-10-20
Interesting is right.  In fact beginning to become a little bizarre.

The *xinput list* looks correct.  When the stylus and eraser are showing in it what is the output of?
```
xinput list-props "Serial Wacom Tablet stylus"
```
and
```
xinput list-props "Serial Wacom Tablet eraser"
```

---

### Post by Kaedo on 2011-10-20
```
kaedo@test:~$ xinput list-props "Serial Wacom Tablet stylus"
Device 'Serial Wacom Tablet stylus':
    Device Enabled (132):    1
    Coordinate Transformation Matrix (134):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (258):    0
    Device Accel Constant Deceleration (259):    1.000000
    Device Accel Adaptive Deceleration (260):    1.000000
    Device Accel Velocity Scaling (261):    10.000000
    Wacom Tablet Area (282):    0, 0, 61952, 65048
    Wacom Rotation (283):    0
    Wacom Pressurecurve (284):    0, 0, 100, 100
    Wacom Serial IDs (285):    144, 0, 2, 0
    Wacom Capacity (286):    -1
    Wacom Pressure Threshold (287):    27
    Wacom Sample and Suppress (288):    2, 4
    Wacom Enable Touch (289):    1
    Wacom Hover Click (290):    1
    Wacom Enable Touch Gesture (291):    0
    Wacom Touch Gesture Parameters (292):    50, 20, 250
    Wacom Tool Type (293):    "STYLUS" (275)
    Wacom Button Actions (294):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Wacom Debug Levels (295):    0, 0
```


```
kaedo@test:~$ xinput list-props "Serial Wacom Tablet stylus"
Device 'Serial Wacom Tablet stylus':
    Device Enabled (132):    1
    Coordinate Transformation Matrix (134):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (258):    0
    Device Accel Constant Deceleration (259):    1.000000
    Device Accel Adaptive Deceleration (260):    1.000000
    Device Accel Velocity Scaling (261):    10.000000
    Wacom Tablet Area (282):    0, 0, 61952, 65048
    Wacom Rotation (283):    0
    Wacom Pressurecurve (284):    0, 0, 100, 100
    Wacom Serial IDs (285):    144, 0, 2, 0
    Wacom Capacity (286):    -1
    Wacom Pressure Threshold (287):    27
    Wacom Sample and Suppress (288):    2, 4
    Wacom Enable Touch (289):    1
    Wacom Hover Click (290):    1
    Wacom Enable Touch Gesture (291):    0
    Wacom Touch Gesture Parameters (292):    50, 20, 250
    Wacom Tool Type (293):    "STYLUS" (275)
    Wacom Button Actions (294):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Wacom Debug Levels (295):    0, 0
kaedo@Dragoncorp:~$ xinput list-props "Serial Wacom Tablet eraser"
Device 'Serial Wacom Tablet eraser':
    Device Enabled (132):    1
    Coordinate Transformation Matrix (134):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (258):    0
    Device Accel Constant Deceleration (259):    1.000000
    Device Accel Adaptive Deceleration (260):    1.000000
    Device Accel Velocity Scaling (261):    10.000000
    Wacom Tablet Area (282):    0, 0, 61952, 65048
    Wacom Rotation (283):    0
    Wacom Pressurecurve (284):    0, 0, 100, 100
    Wacom Serial IDs (285):    144, 0, 10, 0
    Wacom Capacity (286):    -1
    Wacom Pressure Threshold (287):    27
    Wacom Sample and Suppress (288):    2, 4
    Wacom Enable Touch (289):    1
    Wacom Enable Touch Gesture (291):    0
    Wacom Touch Gesture Parameters (292):    50, 20, 250
    Wacom Tool Type (293):    "ERASER" (297)
    Wacom Button Actions (294):    "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
    Wacom Debug Levels (295):    0, 0

```

---

### Post by Favux on 2011-10-20
Does your X200t have touch also?

---

### Post by Kaedo on 2011-10-20
no not that i know, with all drivers under windows i never had touch abilities. i only can use the pen.

---

### Post by Favux on 2011-10-20
OK.

I think you should post on linuxwacom-discuss and ask for help.  You've got plenty of diagnostics now.  Hopefully a developer will help you and this does have something to do with xf86-input-wacom and isn't Ubuntu specific.

linuxwacom-discuss registration:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

---

### Post by luisito on 2011-10-21
The error is not present in Natty. Everything stopped working when upgrading to Oneiric. The linux-wacom driver changed and that may be the source of the problem. But what does it mean that it is not Ubuntu specific? With that criteria, any question related to any part of the OS other than Unity would not be Ubuntu specific.

---

### Post by Favux on 2011-10-21
Ubuntu does not just package straight upstream stuff.  They add changes of their own.  For example if you *sudo ls /dev/ttyS** you'll see 32 serial ports in Natty or Oneiric.  But if you do it in Fedora 15 you'll just see the usual standard ttyS0 to ttyS3.  And devices that were on ttyS0 in Maverick or earlier can now be on ttyS4.  That's an example.  I haven't found any information about how or why the serial stack was changed and what the change does.  That's the kind of distribution thing I'm talking about.

Another example is Ubuntu broke the pads (express keys) on the Intuos and Graphire and Bamboo tablets in Natty because of some of the multi-touch code they added.  Once the Linux Wacom dev.s figured that out they lost interest in trying to solve the problem.  In other words they didn't see the problem in other distributions.

---

### Post by luisito on 2011-10-23
It is working!!!!!

Solution for the impatient: comment out the only line on
/lib/udev/rules.d/40-inputattach.rules 
and reboot.

The problem is worked out in [https://bugs.launchpad.net/ubuntu/+source/joystick/+bug/835634](https://bugs.launchpad.net/ubuntu/+source/joystick/+bug/835634)
One quick way to check that this solves your problem is killing inputattach and then restarting Xorg. This should have your touchscreen and stylus working again (at least until reboot).

There is also a Debian bug report: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=632961](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=632961)

Apparently that line is necessary to make things work on a Fujitsu laptop, but breaks compatibility with the Lenovo ones. The problem is NOT in the wacom driver.

Incidentally, I used to have a problem with upstart-udev-bridge taking 100% of my cpu that now seems magically solved. Coincidence?

---

### Post by Favux on 2011-10-23
lol  I found those bug reports yesterday(?) too, inspired by what I read in the Linux Console Tools new inputattach 1.4.2.  I checked and sure enough Oneiric had gone to 1.4.1 while Natty and earlier were using an old version from the joystick-20051019 package.  So I had new keywords to google.  I was busy clearing up the unbelievable number of tabs I'd spawned over the past week last night and was going to look them over closer today.

Nice work.  :)

---

### Post by luisito on 2011-10-23
Yes, it's great that these people from the buy report figured out what was going on. I was already considering a fresh install back to Natty.

I assume there will be an update soon that fixes the problem for everyone since the solution proposed in the Debian bug report is very clean.

---

### Post by Favux on 2011-10-23
Ah, that's a nice thought.  But just in case have you considered writing a little HOW TO for Lenovo Thinkpads (and possible other affected serial ISDV4 tablets?) to post in Hardware and Laptops?

Also I'm not sure, if someone compiles input-wacom, whether input-wacom's Make file installs the offending inputattach udev rule or not while it is installing inputattach.  Have to look at that.

---

### Post by luisito on 2011-10-23
I don't know that. It's a bit too much work to test it.

---

