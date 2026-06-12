---
title: "Globesurfer icon 7.2 on Ubuntu"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by kestas.j on 2007-07-07
Hello all,

I've bought a USB GSM modem from my mobile service supplier. It works fine under XP, but the thing is - I don't like windows. Does anyone have it running? How to make it work properly? Thanks for help.

---

### Post by kestas.j on 2007-07-08
Hi again,

I found the way to connect this device in [http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,280/](http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,280/) ,but the thing is that my USB device is not listed as a ttyUSB. The system in /dev shows it as a usbdevx.x_epxx. The same was with my FSC PDA when I have tried to sincronize it on Ubuntu. How can I make the system recognise it as ttyUSB?
Thanks.

---

### Post by kestas.j on 2007-07-08
By the way,

As I found out, the prescribtion of ttyUSB* is connected with the 50-udev.rules file located in directory /etc/udev/rules.d . I have checked for that file, but it was not in there ?!?!? Can someone attach a copy of this file to the replay? Otherwise, pleae let me know if I'm thinking in wrong way.

---

### Post by kestas.j on 2007-07-18
Hi all,

Here is the way I made it working. Actually I have connected 4 posts from different websites, and made my iCON 7.2 to work properly.

First of all, this device contains memory disk and modem in it. When device is connected it is switched to memory device mode. To switch it to a modem mode icon_switch is needed.

1. Download the pre-compiled program:

$ wget icon_switch.c [http://www.frederick-reid.com/files/icon_switch.c](http://www.frederick-reid.com/files/icon_switch.c)

2. Open the file. Find and replace product id in it from 6600 to 6901.

$ sudo gedit icon_switch.c

3. To compile the program you will need libusb installed on your machine.

$ sudo apt-get install libusb-dev libusb++-dev
$ cc -l usb -o icon_switch icon_switch.c

4. After compilation the binary file icon_switch is created. You will need to move it to /usr/sbin/ :

$ sudo mv icon_switch /usr/sbin

5. Some rules to switch your device to modem mode on its connection are needed:

$ sudo gedit /etc/udev/rules.d/10-local.rules

Apperantly this file has not been in the system, so by running this command it will be created and opened. You should write in the following and save the file:

BUS=="usb", SYSFS{idProduct}=="1000", SYSFS{idVendor}=="05c6", RUN+="/usr/sbin/icon_switch"
BUS=="usb", SYSFS{idProduct}=="6901", SYSFS{idVendor}=="0af0", RUN+="/sbin/modprobe usbserial vendor=0x0af0 product=0x6901 maxSize=4096"

*saving a file without maxSize=4096 in the end of the second rule should enable your device, but I haven't got a full speed with this configuration. If you choose to do so, you should go to step 12.

6. Now you will have to download linux source:

$ sudo apt-get install build-essential linux-source

7. Untar the linux-source:

$ cd /usr/src
$ sudo tar xjvf linux-source-2.6.20.tar.bz2 (check for the correct version by listing folder content)

8. Get into the folder /linux-source-2.6.20/drivers/usb/serial and edit the file usb-serial.c :

$ cd linux-source-2.6.20/drivers/usb/serial
$ sudo gedit usb-serial.c

The file must be modified in this way: the line in [COLOR="SeaGreen"]GREEN[/COLOR] must be added in the context of black lines. [COLOR="Red"]RED[/COLOR] line in the fix number 2 must be replaced with the [COLOR="SeaGreen"]GREEN[/COLOR] line.

Fix number 1 :

 drivers depend on it.
 */

[COLOR="SeaGreen"]static ushort maxSize = 0;[/COLOR]
 static int debug;
 static struct usb_serial *serial_table[SERIAL_TTY_MINORS];     /* initially all NULL */
 static LIST_HEAD(usb_serial_driver_list);

Fix number 2 :

dev_err(&interface->dev, "No free urbs available\n");
                        goto probe_error;
                }
                [COLOR="Red"]buffer_size = le16_to_cpu(endpoint->wMaxPacketSize);[/COLOR]
               [COLOR="SeaGreen"] buffer_size = (endpoint->wMaxPacketSize > maxSize)?endpoint->wMaxPacketSize:maxSize;[/COLOR]
                port->bulk_in_size = buffer_size;
                port->bulk_in_endpointAddress = endpoint->bEndpointAddress;

Fix number 3 :

 module_param(debug, bool, S_IRUGO | S_IWUSR);
 MODULE_PARM_DESC(debug, "Debug enabled or not");
[COLOR="SeaGreen"]module_param(maxSize, ushort,0);
MODULE_PARM_DESC(maxSize,"User specified USB endpoint size");[/COLOR]

9. Compile driver :

$ sudo make -C /lib/modules/`uname -r`/build M=`pwd`

10. Replace the kernel driver:

$ sudo cp usbserial.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/usbserial.ko
$ sudo depmod -a

11. Reboot :

$ sudo reboot

12. Download UMTSmon program from [http://sourceforge.net/projects/umtsmon/]("http://sourceforge.net/projects/umtsmon/") , untar it.

13. Plug in device, run the UMTSmon, connect to the network, enjoy the full speed.

Hope it will be helpfull.

---

### Post by rautamiekka on 2007-11-27
Sorry for digging up rather old thread but my GlobeSurfer Icon doesn't connect. When it is trying to make connection, it stops to like 68% and on other tab it says modem hanged up, how to fix this ? I do have the icon_switch binary in the same folder as the app.

Hmm, typing **lsusb** says this

Bus 003 Device 007: ID 0af0:6600 Option

, that's not right ?

---

### Post by rautamiekka on 2007-11-27
I made everything from beginning with this and didn't change the 6600, I left it like that instead. Now also GNOME PPP is installed and configured to use the GS and this time the connecting-bar goes all the way to 100 but still gives the same error: modem hang up

---

### Post by trishacupra on 2008-01-11
Any ideas on how I can follow kestas.j's steps (from step 6 on) without an internet connection? I have Windows dual booting and only Windows is working with my Globesurfer icon 7.2 modem. I am travelling and have no other way to connect.

---

### Post by kestas.j on 2008-03-07
Hi there,

There were some updates in Icon module in Gutsy, so it is not needed to patch the source anymore to obtain the full speed. Steps 1 to 5 are necessary. The rules should be set as described in step 5 just without the *maxSize=2048* in the end of the second one. I don't use special application to connect to network anymore. It can be done with Gnome Network Manager's modem connection section:

enable the connection;
set dial number to *99# (if not otherwise stated by your ISP);
enter user name and password defined by your ISP (in my case omni ; omni);
set the modem to /dev/ttyUSB0;
check all boxes in connection settings preferences window.

After restart it should be possible to connect by left-clicking the network manager's applet icon and choosing Dial Up connection -> Connect to ppp0 via Modem
 
The light should go steady on your icon 7.2 indicating the successful connection.

Regards,
Kestas J.

---

