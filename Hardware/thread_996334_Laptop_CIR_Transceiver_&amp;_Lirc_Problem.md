---
title: "Laptop CIR Transceiver &amp; Lirc Problem"
date: 2008-11-28
forum: Hardware
---

### Post by sokairyk on 2008-11-28
Hello!

I have a Hauppage TV Tuner and I want to use its remote with my Acer 5920G Laptop, which has a built-in IR device.

The remote works fine with lirc on my desktop PC.

My Laptop runs Ubuntu Gutsy x64 with the 2.6.22-16-generic kernel.
I use the same lircd.conf file with my desktop PC as I'm using the same remote.

I installed lirc and selected SIR (Built-in IrDA) and played around a little with my serial ports and /etc/lirc/hardware.conf but I didn't get any results when running irw...

When I run "sudo cat /proc/tty/driver/serial" I get:

serinfo:1.0 driver revision:
0: uart:unknown port:000003F8 irq:4
1: uart:unknown port:000002F8 irq:3
2: uart:unknown port:000003E8 irq:4
3: uart:unknown port:000002E8 irq:3

whether the lirc_sir module is loaded or not.

I have turned the LOAD_MODULES to "false" on hardware.conf so I can load the lirc_sir module with io, irq parameters (e.g. sudo modprobe lirc_sir io=0x03F8 irq=4) but none of the above serial ports gave any results with either "sudo irw" or "sudo mode2 -d /dev/lirc0"

I booted from my Vista partition and I got the CIR Transceiver driver resources which are:

I/O 0600-0607
I/O 0620-063F
IRQ 4

I tried:

"sudo modprobe lirc_sir io=0x0600 irq=4"
"sudo modprobe lirc_sir io=0x0620 irq=4"

but neither worked.

The on-board CIR chipset is a Winbond WPC876xL

On every try my actions are:
-stop lirc daemon
-unload lirc_sir module
-load lirc_sir module with new parameters
-start lirc
-test with irw/mode2

Below is my hardware.conf

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="SIR IrDA (built-in IR ports)"

# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=false

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE="/dev/lirc0"
MODULES="lirc_dev lirc_sir"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""

```

---

### Post by sokairyk on 2008-11-30
Help!! :confused: Anyone???

---

### Post by sokairyk on 2008-11-30
I've found out that the IR interface of the chipset is listed as PNP Device (WEC1020) under device manager.

Ubuntu Device Manager Details:

```

############
## Device ##
############

Vendor:		Unknown
Device:		Unknown
Status:		Status
Bus Type:	PNP
Device Type:	Unknown
Capabilities:	Unknown

##############
## Advanced ##
##############

==================	======		========================================
KEY			TYPE		VALUE
==================	======		========================================
info.bus		string		pnp
info.parent		string		/org/freedesktop/Hal/devices/computer
info.product		string		PnP Device (WEC1020)
info.subsystem		string		pnp
info.udi		string		/org/freedesktop/Hal/devices/pnp_WEC1020
linux.hotplug_type	int		2 (0x2)
linux.subsystem		string		pnp
linux.sysfs_path	string		/sys/devices/pnp0/00:08
pnp.id			string		WEC1020

```

The windows driver states: 

BIOS PnP ID - WEC1020: Receive-Only MCE functionality for system without TV tuner.

Any ideas?

---

### Post by FokkerCharlie on 2008-12-11
Hi Sokairyk

Did you make any progress with this?  Would be cool to have it working!

Charlie

---

### Post by sokairyk on 2008-12-23
Unfortunately I think that the lirc_sir module does not support this chipset...

If anyone with similar problems has a solution it would be great to post it :)

---

### Post by mohr tutchy on 2009-02-18
Yesterday i had the cir working! :D
You need to build and install lirc from the latest cvs.
In [[COLOR="Blue"]this discussion[/COLOR]]("http://www.nabble.com/CIR-chipset-Winbond-WPC876xL-td21483483.html") you can find some other details.
Sorry for bad english

One love

---

### Post by sokairyk on 2009-03-13
I made some progress testing the new module for the WPC876xL chipset.

First I uninstalled lirc and removed the lirc folder from /lib/modules/2.6.22-16-generic/ubuntu/media

```

sudo apt-get --purge remove lirc
sudo rm -rf /lib/modules/2.6.22-16-generic/ubuntu/media/lirc

```

Then I logged to the cvs on sourgeforge, downloaded and updated the latest version of lirc

```

cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
cvs update

```

Finally I compiled lirc while selecting the WPC876L (Acer) in the setup.sh menu only with the X-Windows tools option checked

```

./autogen.sh
./setup.sh
make
sudo make install

```

After the installation I have the following lirc devices listed on /dev/

```

ls -l /dev/lirc*

crw-r--r-- 1 root root 61, 0 2009-03-13 21:08 /dev/lirc
prw-r--r-- 1 root root     0 2009-03-13 21:09 /dev/lircd
prw-r--r-- 1 root root     0 2009-03-13 21:09 /dev/lircm

```

When I load the module lirc_wpc8769l

```

sudo modprobe lirc_wpc8769l

```

the modules lirc_wpc8769l and lirc_dev load normally

```

lsmod | grep lirc

lirc_wpc8769l          13200  0 
lirc_dev               20296  1 lirc_wpc8769l

```

and lirc0 is added in the /dev/

```

ls -l /dev/lirc*

crw-r--r-- 1 root root 61, 0 2009-03-13 21:08 /dev/lirc
crw-rw---- 1 root root 61, 0 2009-03-13 21:25 /dev/lirc0
prw-r--r-- 1 root root     0 2009-03-13 21:09 /dev/lircd
prw-r--r-- 1 root root     0 2009-03-13 21:09 /dev/lircm

```

So then I start mode2, press some buttons and I get output :D

```

sudo mode2

pulse 950
space 850
pulse 1850
space 800
pulse 950
space 850
pulse 950
space 850
pulse 900
space 850
pulse 950
space 850
pulse 900
space 900
pulse 900
space 850
pulse 950
space 850
pulse 900
space 850
pulse 950
space 850
pulse 900
space 1750
pulse 950

```

So far so good. Now I start lirc

```

sudo lircd
ps -A | grep lirc

12942 ?        00:00:00 lircd

```

I don't know why but lirc does not have a folder in /etc/ and has no script in /etc/init.d/ to control it from there. It only has a lircd.conf file in /etc/ which I changed to the one I use on my desktop PC for the same remote.

Then I check with irw the remote

```

sudo irw 

000000000000102e 00 FULL_SCREEN Hauppauge
0000000000001021 00 CH- Hauppauge
0000000000001020 00 CH+ Hauppauge
0000000000001010 00 VOL+ Hauppauge
0000000000001011 00 VOL- Hauppauge

```

After a while I cannot run irw. Sometimes I'm able to run it more than once so I cannot tell why this is happening.

```

sudo irw 

connect: Connection refused

```

Also I cannot unload the module cause after I run

```

sudo modprobe -r lirc_wpc8769l

```

the command never completes. The system is not affected but when I restart or shutdown, the system closes as if I forced power down manually through the power button.

When that happens before I restart the system I check the modules

```

lsmod | grep lirc

lirc_wpc8769l          13200  0 
lirc_dev               20296  3 lirc_wpc8769l

```

the "Used by" column has increased to 3.

It seems some kind of deadlock to me. So in every test the problem starts after I load the lircd.

After a system restart I load the modules again but mode2 cannot start

```

sudo mode2

mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory

```

and the lirc files in /dev/ are

```

ls -l /dev/lirc*

crw-rw---- 1 root root 61, 0 2009-03-13 22:39 /dev/lirc0

```

If I start lircd

```

sudo lircd

```

the files in /dev/ are

```

ls -l /dev/lirc*

crw-rw---- 1 root root 61, 0 2009-03-13 22:39 /dev/lirc0
srw-rw-rw- 1 root root     0 2009-03-13 22:40 /dev/lircd

```

I tried to create lirc in /dev/ with

```

sudo mknod /dev/lirc c 61 0

```

but still the problem with mode2 continues. Also if I start irw after I started the lirc daemon I don't get any output.

I tried this a couple of times and always I start to have problems after I load the lirc daemon. The "Used by" count in the lsmod output for lirc_wpc8769l is always 3 after the lock of the modules. The only way to make things work again with mode2 is to enter the cvs lirc directory and

```

sudo make uninstall
sudo make install

```

Somehow make creates the correct lirc files in /dev/ and mode2 starts again after I load the modules.

If it helps below is my lircd.conf

```

#
# this config file was automatically generated
# using lirc-0.5.5pre8 on Sun Apr 18 11:43:45 1999
#
# contributed by Jens Leuschner <leuschner@gmx.net>
#
# brand:             Hauppauge
# model:             
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and 
# original Hauppauge TV cards !!!
#

begin remote

  name  Hauppauge
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100

  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2

      begin codes
          TV                       0x000000000000100F
          RADIO                    0x000000000000100C
          FULL_SCREEN              0x000000000000102E
          CH+                      0x0000000000001020
          CH-                      0x0000000000001021
          VOL-                     0x0000000000001011
          VOL+                     0x0000000000001010
          MUTE                     0x000000000000100D
          SOURCE                   0x0000000000001022
          1                        0x0000000000001001
          2                        0x0000000000001002
          3                        0x0000000000001003
          4                        0x0000000000001004
          5                        0x0000000000001005
          6                        0x0000000000001006
          7                        0x0000000000001007
          8                        0x0000000000001008
          9                        0x0000000000001009
          0                        0x0000000000001000
          RESERVED                 0x000000000000101E
          MINIMIZE                 0x0000000000001026
      end codes

end remote

```

---

### Post by mohr tutchy on 2009-03-16
I suspect you are using a wrong lircd.conf. Try to create your own lircd.conf with
```
irrecord
```

One love

---

### Post by sokairyk on 2009-03-16
Yeeeeeeyy :D

My lircd.conf file was the problem indeed! Once I ran irrecord and replaced my lircd.conf file everything worked!

So to summarize the whole procedure: 

1) Remove the lirc package and the modules (if it's installed)

```

sudo apt-get --purge remove lirc
sudo rm -rf /lib/modules/`uname -r`/ubuntu/media/lirc

```

2) Download the latest version from CVS (which includes the WPC876L module)

```

cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
cd lirc
cvs update

```

3) Configure, compile the source and install

```

./autogen.sh
./setup.sh
make
sudo make install

```

4) Load the module

```

sudo modprobe lirc_wpc8769l

```

5) Check your output with mode2

```

sudo mode2

```

6) Run irrecord to create a configuration file for your remote

```

sudo irrecord --disable-namespace lircd.conf

```

7) Copy the configuration file to /etc/

```

sudo cp lircd.conf /etc/lircd.conf

```

8) Now start the lirc daemon with:

```

sudo lircd --permission=666 --device=/dev/lirc0 /etc/lircd.conf

```

If you want to run the lirc daemon on boot continue with the following:

9) Add the following line to /etc/modules

```

lirc_wpc8769l

```

10) Because there isn't any lirc script in /etc/init.d/ I wrote a very simple one. So create a file in /etc/init.d/ named lirc and copy the following:

```

#!/bin/bash

case "$1" in
  start)
    echo -n "Starting lirc daemon..."
    ARGS=' --permission=666 --device=/dev/lirc0 /etc/lircd.conf'
    start-stop-daemon --start --exec /usr/local/sbin/lircd -- $ARGS
    echo "."
    ;;
  stop)
    echo -n "Stopping lirc daemon..."
    start-stop-daemon --stop --exec /usr/local/sbin/lircd
    echo "."
    ;;
  *)
    echo "Usage: /etc/init.d/lircd {start|stop}"
    exit 1
esac

exit 0

```

10) Give the right permissions to the file

```

sudo chmod 775 /etc/init.d/lirc

```

11) Update system's scripts

```

sudo update-rc.d lirc multiuser

```

If you have a .lircrc file in your home folder to use with irexec you can add to the startup programs in sessions:

```

irexec -d

```

:D:D:D

---

### Post by mohr tutchy on 2009-03-17
Very good howto :D
[s]I will merge it with [the one]("http://ubuntuforums.org/showthread.php?t=1077437") I wrote some time ago ;)[/s]
Done ;)

One love

---

### Post by krisstaar on 2009-04-04
I have an ene0100 chipset. Does anyone know of a driver I can use, and how to set it up so I can use my CIR-reciever?

---

### Post by sokairyk on 2009-06-22
After updating to Ubuntu 9.04 and following the same procedure everything was working except irexec.

lircd was created in /dev/ with the correct permissions and irw was working just fine with the lircd.conf file in my /etc/ but I had to define the socket (I had to run: irw /dev/lircd)

The problem was that irexec does not have an argument to specify a socket, so I looked a bit at config.h in the sources and I found out that the default socket which irexec looks for is /var/run/lirc/lircd

Then all I had to do was to change the script in /etc/init.d/ to this:

```
#!/bin/bash

case "$1" in
  start)
    echo -n "Starting lirc daemon:"
    echo -n " lircd"
    echo -n " "
    if [ ! -d /var/run/lirc ]
    then
        mkdir /var/run/lirc
    fi
    LIRCD_ARGS=' --output=/var/run/lirc/lircd --permission=666 --device=/dev/lirc0 /etc/lircd.conf'
    start-stop-daemon --start --exec /usr/local/sbin/lircd -- $LIRCD_ARGS
    echo ""
    ;;
  stop)
    echo -n "Stopping lirc daemon:"
    echo -n " lircd"
    echo -n ""
    start-stop-daemon --stop --exec /usr/local/sbin/lircd
    if [ -d /var/run/lirc ]
    then
        rm -rf /var/run/lirc
    fi
    echo " "
    ;;
  *)
    echo "Usage: /etc/init.d/lircd {start|stop}"
    exit 1
esac

exit 0
```

and everything was back to normal :D

Also for some reason I had to create the folder lirc in /var/run/ otherwise the lirc daemon wouldn't start because it couldn't create the folder even when running the script with root permissions.

Anyway if someone had a problem with Ubuntu 9.04 I hope this helped.

---

### Post by daehenoc on 2009-09-11
I've got an Acer Aspire 5920G as well, I am going to try installing Karmic Koala Ubuntu 9.10 Alpha5 on it this weekend and see if the kernel module and lirc version work correctly for this hardware :)

(Here is a search on packages.ubuntu.com for wpc8796l in all filenames: **[http://packages.ubuntu.com/search?searchon=contents&keywords=wpc8769l&mode=filename&suite=karmic&arch=any]("http://packages.ubuntu.com/search?searchon=contents&keywords=wpc8769l&mode=filename&suite=karmic&arch=any")**

---

### Post by FokkerCharlie on 2009-12-10
Cool- works for me!

---

### Post by FokkerCharlie on 2009-12-12
Actually, it works until I suspend:

After that, there's no output from irw, sudo mode2 returns:

```
$ sudo mode2
mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory
```

I can stop/start the script in init.d OK, but no joy.  However, the modules do seem to be loaded (starting / stopping by the script doesn't make a difference to this)

```
$ lsmod | grep lirc
lirc_wpc8769l           9936  0 
lirc_dev               13992  1 lirc_wpc8769l
```

After a reboot, all is well.  So any idea what's going on here?

Charlie

---

