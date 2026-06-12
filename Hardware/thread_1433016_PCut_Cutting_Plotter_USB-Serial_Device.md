---
title: "PCut Cutting Plotter USB-Serial Device"
date: 2010-03-18
forum: Hardware
---

### Post by damianleuthold on 2010-03-18
Hello Ubuntu Forums,

This is my first message!  I hope you can help.

I just got a PCut Cutting Plotter for use in cutting vinyl and sand blast resist stencils.  Will design using inkscape and print using the Tux Plot program ([http://www.securetech-ns.ca/securetech.html](http://www.securetech-ns.ca/securetech.html)) or Bob Story's hpgl-distiller ([http://bobstory.fortunecity.com/vinylcutter.html](http://bobstory.fortunecity.com/vinylcutter.html)).

But first I need to get the plotter to respond to something, anything, that I send it.  When I plug the plotter in to a USB port the device seems to be detected and registered correctly but I haven't gotten any response from the plotter by either piping directly or setting up a RAW cups printer.

Any ideas on what I'm missing?  Thanks.

I'm hoping to avoid having to get my hands on a windows machine to see how things work there.

Here's all the gory detail:

--------------------------------------
***When I plug the USB from the plotter in to the computer
$ dmesg
[42999.312037] usb 5-2: new full speed USB device using uhci_hcd and address 2
[42999.490413] usb 5-2: configuration #1 chosen from 1 choice
[42999.635294] usbcore: registered new interface driver usbserial
[42999.635316] USB Serial support registered for generic
[42999.635356] usbcore: registered new interface driver usbserial_generic
[42999.635359] usbserial: USB Serial Driver core
[42999.652709] USB Serial support registered for FTDI USB Serial Device
[42999.652779] ftdi_sio 5-2:1.0: FTDI USB Serial Device converter detected
[42999.652820] usb 5-2: Detected FT232BM
[42999.652824] usb 5-2: Number of endpoints 2
[42999.652827] usb 5-2: Endpoint 1 MaxPacketSize 64
[42999.652830] usb 5-2: Endpoint 2 MaxPacketSize 64
[42999.652832] usb 5-2: Setting MaxPacketSize 64
[42999.654488] usb 5-2: FTDI USB Serial Device converter now attached to ttyUSB0
[42999.654527] usbcore: registered new interface driver ftdi_sio
[42999.654532] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver

$ lsusb
Bus 005 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ udevadm info -q all -n /dev/ttyUSB0
P: /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/ttyUSB0/tty/ttyUSB0
N: ttyUSB0
S: char/188:0
S: serial/by-path/pci-0000:00:1d.3-usb-0:2:1.0-port0
S: serial/by-id/usb-FTDI_USB__-__Serial-if00-port0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/ttyUSB0/tty/ttyUSB0
E: MAJOR=188
E: MINOR=0
E: DEVNAME=/dev/ttyUSB0
E: SUBSYSTEM=tty
E: ID_PORT=0
E: ID_PATH=pci-0000:00:1d.3-usb-0:2:1.0
E: ID_VENDOR=FTDI
E: ID_VENDOR_ENC=FTDI
E: ID_VENDOR_ID=0403
E: ID_MODEL=USB__-__Serial
E: ID_MODEL_ENC=USB\x20\x3c-\x3e\x20Serial
E: ID_MODEL_ID=6001
E: ID_REVISION=0400
E: ID_SERIAL=FTDI_USB__-__Serial
E: ID_TYPE=generic
E: ID_BUS=usb
E: ID_USB_INTERFACES=:ffffff:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_DRIVER=ftdi_sio
E: ID_IFACE=00
E: ID_VENDOR_FROM_DATABASE=Future Technology Devices International, Ltd
E: ID_MODEL_FROM_DATABASE=FT232 USB-Serial (UART) IC
E: DEVLINKS=/dev/char/188:0 /dev/serial/by-path/pci-0000:00:1d.3-usb-0:2:1.0-port0 /dev/serial/by-id/usb-FTDI_USB__-__Serial-if00-port0

---------------------------------
***Try to pipe to device directly:
$ cat at.hpg
IN;   ; <***or IN:***>
PS7000,5000;
SP1PA1000,100PD2500,100
PU650,1150PD1000,1150PU650,450PD1000,450
PU1000,100PD1000,1500,2500,1500
AT3200,800,2500,100PU3200,900PD
AT3300,800,3200,700PU3300,800PD3500,800
PUSP0PG

$ cat at.hpg > /dev/ttyUSB0
<***nothing***>

----------------------------------
***Try to sent to CUPs printer with Device URI: 
serial:/dev/ttyUSB0?baud=9600
usb:/dev/ttyUSB0

***I get status message "Printer "PCut" may not be connected"

---

### Post by kmrs75 on 2010-03-18
hi there i have been testing for the guy that has the website [http://www.securetech-ns.ca/securetech.html](http://www.securetech-ns.ca/securetech.html)) 

and i use it it works great 

ok first from your posting i cant tell what your cutter is 

plug cutter in and in a term type 

lsusb 

post 

then unplug cutter type same thing and post 

ok i have been on uscutter site and posted alot of info under inkscape you will see it there 

you have to get the cutter set up as a raw gen printer 

after that your good to go but with the very low end cutters MH series i couldnt get it to do anything - try that and go from there you might have to try to add a driver 
were using a graphtec now and its very easy to set up plug in the graphtec and it pops up as a printer but no driver we set it up as a raw printer and BANG !!!! its all set up and ready to roll

---

### Post by kmrs75 on 2010-03-18
FTDI USB Serial Device

o i just reread your post that is the problem i had mh series and that uses the same chipset 

there is a way to get it to work but it doesnt look easy i never messed with it since the graphtec worked i just sold the MH 

if you get the driver for that it should work just fine

---

### Post by damianleuthold on 2010-03-18
Thanks for the reply, happy I'm not alone in the universe.

You are at least helping me confirm the direction I need to go.  "Get a driver", would that mean getting/creating a udev rule for this FDTI Serial Device Converter VENDOR_ID=0403, MODEL_ID=6001?

---

### Post by kmrs75 on 2010-03-19
> **damianleuthold said:**
> Thanks for the reply, happy I'm not alone in the universe.

You are at least helping me confirm the direction I need to go.  "Get a driver", would that mean getting/creating a udev rule for this FDTI Serial Device Converter VENDOR_ID=0403, MODEL_ID=6001?

yep you got it 

not sure what will happen after that but that is the first step 

when I plug in my Graphtec it comes up with add printer that is what ya need to have happen 

not sure how much experience you have with Linux Ubuntu but if you can compile that drive I would think you should be able to make it work

If you get it to work please post how you did it it would be a help to others

---

### Post by GavSt on 2010-03-19
[http://www.ftdichip.com/Drivers/VCP.htm](http://www.ftdichip.com/Drivers/VCP.htm)

There are linux drivers available on the FTDI website..

I haven't used them but i have used the windows drivers from here and they work fine..

---

### Post by j4play on 2010-03-25
hey.  i'm using an older USB pcut currently.  i've got it working reasonable well, but there still some tweaking required.

anyhow, i'm using inkscape for designs.  then i save using the "HP Graphics Language Plot file [AutocCAD] (*.plt)".  note that i'm using a bleeding edge Inkscape, though i think the repo version should work.

then i use gtkterm to send the .plt file directly to the cutter. in the serial port config of gtkterm, you should have a /dev/ttyUSB port.  Make sure you set the baud etc to correspond to the cutter settings.  I also need to set the flow control to either Xon/Xoff, or RTS/CTS.  i think the latter works best.

i've just been plotting things so far, but i think perhaps some more tweaking will be required for cutting.

i had no luck with tuxplot.  well, i couldn't setup CUPS serial port printing.  

also, i didn't have any luck using inkscape_svg -> pstoedit -> hpgl-distiller.

---

### Post by damianleuthold on 2010-03-30
Thanks for all the good advice and interesting to hear other's experiences.  Have successfully loaded TuxPlot but still stuck on the driver.  Creating a driver is above my head.  Glad to see there's already a driver out there.  Tried to load it but unfortunately the driver does not compile on my system.

The driver is looking in the wrong places for some of the files that it needs.  I started to modify the make file so that it would find the include files, but it started getting ugly and I got intimidated.  Does this sound like the right direction to go?  Maybe I need to recompile the kernel?

Thx

----------------------
**The original make command:**
gcc -Wall -D__KERNEL__ -DMODULE -I/lib/modules/2.6.31-20-generic/build/include -D__SMP__ -DSMP -DMODVERSIONS -include /lib/modules/2.6.31-20-generic/build/include/linux/modversions.h -I/usr/src/linux-2.6.31-20-generic/drivers/usb/serial/ -O   -c -o ftdi_sio.o ftdi_sio.c

**Make errors:**
cc1: error: /lib/modules/2.6.31-20-generic/build/include/linux/modversions.h: No such file or directory
In file included from /lib/modules/2.6.31-20-generic/build/include/linux/kernel.h:11,
                 from ftdi_sio.c:251:
/lib/modules/2.6.31-20-generic/build/include/linux/linkage.h:5:25: error: asm/linkage.h: No such file or directory
In file included from /lib/modules/2.6.31-20-generic/build/include/linux/kernel.h:15,
                 from ftdi_sio.c:251:
...

**modversions.h is here:**
/usr/src/linux-headers-2.6.31-20-generic/include/config/modversions.h

**Kernel.h is here:**
/usr/src/linux-headers-2.6.31-20-generic/include/linux/kernel.h

----------------------------
[B]Modified make file:
[/B]$ make
gcc -Wall -D__KERNEL__ -DMODULE -I/usr/src/linux-headers-2.6.31-20-generic/config -D__SMP__ -DSMP -DMODVERSIONS -include /usr/src/linux-headers-2.6.31-20-generic/include/linux/modversions.h -I/usr/src/linux-headers-2.6.31-20-generic/include/config/ -I/usr/src/linux-2.6.31-20-generic/drivers/usb/serial/ -O   -c -o ftdi_sio.o ftdi_sio.c

[B]New make errrors:
[/B]$make
cc1: error: /usr/src/linux-headers-2.6.31-20-generic/include/linux/modversions.h: No such file or directory
ftdi_sio.c:253:24: error: linux/init.h: No such file or directory
ftdi_sio.c:254:24: error: linux/slab.h: No such file or directory
ftdi_sio.c:256:30: error: linux/tty_driver.h: No such file or directory
...

---

### Post by j4play on 2010-04-01
yep, i'm currently finding the same issues when trying to compile the FTDI drivers. i got past the modversion issue by modifying the Rules.make file, but there are other issues.

am hoping the newer driver versions might perform more consistently, but guessing there won't be much difference.

i've attached a plt file created with inkscape.  not sure what the difference is with hpgl, but this works when i send it to my pcut using gtkterm.  make sure you turn the flow control to RTS/CTS.
it should draw a circle.

---

### Post by kmrs75 on 2010-04-04
for us its not so much the driver its the equipment 

we had an MH series cutter that uses the serial to usb back when we had windows on that pc - it broke so we bought a Graphtec cutter and it doesn't require that driver - and from there i met a guy from Canada the one that made the software were in contact with him daily and I did allot of testing for him -- 

well back to what i was saying - when the graphtec is plugged into linux the OS sees it as a printer and everything gets installed on its own - but you have to set it up as a RAW printer so when the HPGL file gets sent to the cutter it does what its told to do 


it kinda looks as if all the china made cutters use the same serial to usb driver - I tried to install but couldn't get it to work. I don't have that cutter any more so i cant test anything out with it

---

### Post by kmrs75 on 2010-04-10
[http://www.inkscapeforum.com/viewtopic.php?f=31&t=4987]("http://www.inkscapeforum.com/viewtopic.php?f=31&t=4987")

try this its new it should work for ya

---

### Post by damianleuthold on 2010-04-18
Wow, well, this last solution worked for me.  A plotter extension to Inkscape.  I might try to rewrite it in Perl as an exercise to help me understand what's going on under the hood of inkscape and HPGL and to get more up to speed with Perl. 

I'm amazed that the good advice kept on coming, that this thread stayed alive, and that someone with the skills decided to make a solution for the obscure problem I was having.  I had given up.  This must be how communities work.  Thanks techbuddies!

---

### Post by kmrs75 on 2010-04-18
that doesn't work for all cutters just so you know - that plug in - as of right now will only work with MH P-cut and other china cutters - the graphtec and roland doesnt use the usb to serial - so it works differently those you have to use tux plot 

so your cutting now? thats great 

how does it look feel i have it but never really got to mess with it too much 

does it have any issues ?

congrats

---

### Post by vinylfil on 2012-06-04
hi folks, I am also trying to set up a plotter ( mimaki cg60sr) with ubuntu 12.04lts.
I have started going thru the debugging printer problems wiki and when I try 
$ lsmod | grep usb
[FONT=Arial]I dont get anything - just back to curser. Am I missing something obvious?[/FONT]

---

### Post by garyinspringhill on 2012-07-05
If you choose to try Tux Plot it should be a fairly easy install even if the mimaki/usb is not recognised by Ubuntu. Just follow the install help pages on the Tux Plot web site [http://securetech-ns.ca/camm-linux.html. ]("http://securetech-ns.ca/camm-linux.html")
Install a printer as your mimaki even if you use a printer port or any port it's ok as in Tux Plot you can "print direct to port" and over ride the port in cups.
If you need help email me.

---

