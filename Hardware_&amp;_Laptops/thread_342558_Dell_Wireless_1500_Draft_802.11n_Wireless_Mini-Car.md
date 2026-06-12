---
title: "Dell Wireless 1500 Draft 802.11n Wireless Mini-Card and Edgy works !!!"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by OldGaf on 2007-01-20
I had tried to get this to work about 6 months ago with no success. I tried again last week and it worked strait away with no problem. I guess the new drivers from Dell and the the latest Ndiswrapper did the trick!

Here is a quick How to (Done on a fresh Edgy install and upgade):

1.Make sure you have the headers:
sudo apt-get install linux-headers-`uname -r`

2.Grab Ndiswrapper 1.34 from this link:
[Ndiswrapper-1.34]("http://www.nialm.com/Dell/ndiswrapper-1.34.tar.gz")

3. Grab these Dell drivers from this link:
[Dell Drivers]("http://www.nialm.com/Dell/DRIVER.tar.gz")

4. Go to the downloaded files and extract them:
tar -zxvf ndiswrapper-1.34.tar.gz
and
tar -zxvf DRIVER.tar.gz

5. The first will create the ndiswrapper-version directory. Change to that directory:
cd ndiswrapper-1.34

6. Once in the source-directory run:
make distclean

7. Then run:
make

8. making sure you are still in the source-directory, As root, run:
make install

9. Then run the following to install the drivers (change path if required):
ndiswrapper -i /DRIVER/bcmwl5.inf

10.  $ ndiswrapper -m

11. $ sudo depmod -a

12. $ sudo modprobe ndiswrapper

You may need to reboot.

-N-

---

### Post by heiNey on 2007-02-05
hi there, 

i followed your instructions, and my wifi light came on, and im able to do a iwlist scanning and it shows 4 networks...i can see my own network, and quality is 95/100...but i cant connect to it..ive tried disabling the WEP, but that doesnt seem to work either.

the strange part is that when i unplug the ethernet cable, i can still do a iwlist scanning, and itll still pick up the networks in the area...so it looks like the wireless card is able to detect networks, but cant connect to them...

im on an E1505 with Dell Wireless 1500 Draft 802.11n built in and Ubuntu Dapper Drake 6.06.1 LTS with ndiswrapper 1.37 and the windows drivers you posted above.

if you, or anyone, has an idea as to how to fix this, please let me know...im desperate and am aobut to head back to windows if i cant get this working :(

---

### Post by jml on 2007-02-05
You might want to download a copy of Ubuntu 6.10, (OldGaf notes using 6.10).  My experience is that it handles wireless networking better than 6.06.  Just my two cents worth.

Joe

---

### Post by heiNey on 2007-02-05
hmmm...if all else fails, i might do that...but i heard edgy was unstable, which is why i went with dapper

---

### Post by pépère on 2007-02-08
Hello !

I'm going to buy a new laptop, and my choice is a Dell XPS M1210.

I can choose a Dell Wireless 1500 802.11n card. 

heiNey, do you have solved your problem ? Does this card work well with edgy eft and ndiswrapper ?

Thank you for your answer.

---

### Post by heiNey on 2007-02-08
hey pepere,

nope, i couldnt solve the issue...i followed quite a few guides and did a fresh install each time...nothing worked

the furthest i could get was getting the wifi light to come on, and it found all the local networks whenever i did a 'iwlist scanning'.  it could even find the networks when i did 'iwlist scanning' after unplugging my ethernet cable...but i couldnt get it to connect to any of the wireless networks it detected...

i also removed the WEP from my router and i still couldnt get it to connect to my own network, even though it said the strength was 100/100 in the scanning results

i tried installing wifi-radar, and network-manager as well to see if it would make a difference...i read in other threads that these may work..but i got no results with them...i disabled my interfaces [by commenting out the connections in /etc/network/interfaces] like it says to do in the instructions and still got nothing.

i also went to the bios, as suggested by some in another thread [sorry, lost the bookmark to that certain thread], and set the wifi to always on and disabled the bluetooth fn keys, and it still didnt work

so for the time being, until ubuntu supports this card natively i guess, im back to windows :(

---

### Post by dannyboy79 on 2007-02-08
When you say you heard Edgy is unstable, that must have been a long time ago. Edgy is the latest Stable release. Fiesty is unstable. Most likely the problems you heard about were regarding wireless with Edgy anyway, and he is telling you that Edgy and your wireless card work out of the box.

---

### Post by heiNey on 2007-02-08
yea...i did some more reading and came across that..

but edgy and this card definitely dont work out of the box...at least not for me

---

### Post by dannyboy79 on 2007-02-09
> **heiNey said:**
> yea...i did some more reading and came across that..

but edgy and this card definitely dont work out of the box...at least not for me

you're right sorry, not out of the box but it does work. just follow his steps.

---

### Post by truelifestudio on 2007-02-14
Everything works for a couple of minutes then my kernel kicks it out.

I'm using Edgy 6.10 with everything that you had me download.

Is there any reason why the kernel would error after a couple of minutes of downloading?  It connects just fine and lets me browse the internet, but then I get kicked off.

How do I get back on?  I tried the following:

/etc/init.d/dcom down to up

rmmod ndiswrapper followed by modprobe ndiswrapper

The only way I can get it to work is reboot.  I can't get it to work any other way.

---

### Post by OldGaf on 2007-02-14
> **heiNey said:**
> hi there, 

i followed your instructions, and my wifi light came on, and im able to do a iwlist scanning and it shows 4 networks...i can see my own network, and quality is 95/100...but i cant connect to it..ive tried disabling the WEP, but that doesnt seem to work either.

the strange part is that when i unplug the ethernet cable, i can still do a iwlist scanning, and itll still pick up the networks in the area...so it looks like the wireless card is able to detect networks, but cant connect to them...

im on an E1505 with Dell Wireless 1500 Draft 802.11n built in and Ubuntu Dapper Drake 6.06.1 LTS with ndiswrapper 1.37 and the windows drivers you posted above.

if you, or anyone, has an idea as to how to fix this, please let me know...im desperate and am aobut to head back to windows if i cant get this working :(

Sorry for not getting back sooner. I was NOT able to get it to work with Dapper. Once I did a CLEAN install of edgy (not an upgrade from dapper) and followed the instructions above it worked like a charm.

---

### Post by OldGaf on 2007-02-14
> **heiNey said:**
> hmmm...if all else fails, i might do that...but i heard edgy was unstable, which is why i went with dapper

I have been using Edgy for some time now and find it MUCH better then Dapper...... no issues at all.

---

### Post by OldGaf on 2007-02-14
> **truelifestudio said:**
> Everything works for a couple of minutes then my kernel kicks it out.

I'm using Edgy 6.10 with everything that you had me download.

Is there any reason why the kernel would error after a couple of minutes of downloading?  It connects just fine and lets me browse the Internet, but then I get kicked off.

How do I get back on?  I tried the following:

/etc/init.d/dcom down to up

rmmod ndiswrapper followed by modprobe ndiswrapper

The only way I can get it to work is reboot.  I can't get it to work any other way.


What exactly do you mean when you say "the kernel kicks you out"? Are you using WEP ?

---

### Post by truelifestudio on 2007-02-14
I'm using WPA through Network-Manager.

Everything seems to work really well then all of a sudden I don't have internet.  If I'm in the terminal an error with a IRQ type number.  After more research I determined that it was my wireless card.

Let me boot up my linux box and add the error:

Feb 14 23:10:25 linksys dhcdbd: message_handler: message handler not found under
/com/redhat/dhcp/wlan0 for subpath
wlan0.dbus.get.host_name
Feb 14 23:10:25 linksys dhcdbd: message_handler: message handler not found under
/com/redhat/dhcp/wlan0 for subpath
wlan0.dbus.get.nis_domain
Feb 14 23:10:25 linksys dhcdbd: message_handler: message handler not found under
/com/redhat/dhcp/wlan0 for subpath
wlan0.dbus.get.nis_servers
Feb 14 23:11:15 linksys kernel: [17179680.412000] <c01499a4> __report_bad_irq+0x24/0x80
<c0149a9d> note_interrupt+0x9d/0x270
Feb 14 23:11:15 linksys kernel: [17179680.412000] <f8a3f07e> b44_interrupt+0x1e/0xc0 [b44]
<c0149323> handle_IRQ_event+0x33/0x60
Feb 14 23:11:15 linksys kernel: [17179680.412000] <c0149448> __do_IRQ+0xf8/0x110 <c0105c89>
do_IRQ+0x19/0x30
Feb 14 23:11:15 linksys kernel: [17179680.412000] <c010408a> common_interrupt+0x1a/0x20

and:

ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[17179587.172000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179587.172000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[17179587.188000] ndiswrapper: using IRQ 177
[17179587.728000] wlan0: ethernet device 00:16:cf:08:6b:c1 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4328.5.conf
[17179587.728000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179587.728000] usbcore: registered new driver ndiswrapper
[17179587.832000] fuse init (API version 7.6)
[17179587.852000] Adding 2040244k swap on /dev/disk/by-uuid/1156a4ee-51d5-4283-b4ad-da3137f12e27.  Priority:-1 extents:1 across:2040244k
[17179587.936000] EXT3 FS on sda2, internal journal
[17179589.112000] ACPI: AC Adapter [AC] (on-line)
[17179589.160000] ACPI: Battery Slot [BAT0] (battery present)
[17179589.172000] ACPI: Lid Switch [LID]
[17179589.172000] ACPI: Power Button (CM) [PBTN]
[17179589.172000] ACPI: Sleep Button (CM) [SBTN]
[17179589.264000] ibm_acpi: ec object not found
[17179589.308000] pcc_acpi: loading...
[17179589.416000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179589.416000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179589.416000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[17179592.684000] apm: BIOS not found.
[17179597.108000] Bluetooth: Core ver 2.8
[17179597.108000] NET: Registered protocol family 31
[17179597.108000] Bluetooth: HCI device and connection manager initialized
[17179597.108000] Bluetooth: HCI socket layer initialized
[17179597.120000] Bluetooth: L2CAP ver 2.8
[17179597.120000] Bluetooth: L2CAP socket layer initialized
[17179597.124000] Bluetooth: RFCOMM socket layer initialized
[17179597.124000] Bluetooth: RFCOMM TTY layer initialized
[17179597.124000] Bluetooth: RFCOMM ver 1.7
[17179598.812000] b44: eth0: BUG!  Timeout waiting for bit 00000002 of register 42c to clear.
[17179606.360000] NET: Registered protocol family 10
[17179606.360000] lo: Disabled Privacy Extensions
[17179606.360000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179606.360000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179606.360000] IPv6 over IPv4 tunneling driver
[17179624.128000] NET: Registered protocol family 17
[17179625.880000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17179643.484000] wlan0: no IPv6 routers present
[17179680.412000] irq 177: nobody cared (try booting with the "irqpoll" option)
[17179680.412000]  <c01499a4> __report_bad_irq+0x24/0x80  <c0149a9d> note_interrupt+0x9d/0x270
[17179680.412000]  <f8a3f07e> b44_interrupt+0x1e/0xc0 [b44]  <c0149323> handle_IRQ_event+0x33/0x60
[17179680.412000]  <c0149448> __do_IRQ+0xf8/0x110  <c0105c89> do_IRQ+0x19/0x30
[17179680.412000]  <c010408a> common_interrupt+0x1a/0x20 
[17179680.412000] handlers:
[17179680.412000] [<f8bc3f40>] (ndis_isr+0x0/0xc0 [ndiswrapper])
[17179680.412000] [<f8a3f060>] (b44_interrupt+0x0/0xc0 [b44])
[17179680.412000] Disabling IRQ #177

---

### Post by heiNey on 2007-02-14
> **OldGaf said:**
> I have been using Edgy for some time now and find it MUCH better then Dapper...... no issues at all.

well i tried edgy after i gave up on dapper...did a clean install, sudo install update, etc...followed these instructions verbatim...i get scan results when doing iwlist scanning..it sees all the networks around, but it cant actually connect to anything...so i think the card has been recognized and is working, it just cant connect

i disabled WEP, disabled every protection...had my network totally open to the public and it still woudlnt connect.  tried setting a static ip, tried ifdown wlan0, then ifup wlan0..all it did was tell me its not receiving any dhcp offers and sleeping message.  the only strange thing i noticed was when doing a dhclient, the DHCPOFFER would come from 192.168.1.1, but my router is 192.168.0.1.  the eth0 gets DHCPOFFER from 192.168.0.1 correctly though.

so then i tried setting the ip manually, still no luck :confused:

---

### Post by truelifestudio on 2007-02-15
To get mine to work I had install the Network Manager using the below directions then reboot.

I have to type modprobe ndiswrapper every time to get it to connect...well for the 2 minutes that it does work.

I ordered a USB network card that is approved by Ubuntu.  Hopefully when that comes it it will work.

If you want to setup the Network manager then:

Follow these directions and setup network manager.

Procedure to enable WPA Wireless in Ubuntu

To update the source list run the following command

sudo apt-get

sudo apt-get install wpasupplicant

sudo apt-get install network-manager-gnome network-manager

sudo gedit /etc/network/interfaces

Comment out everything other than “lo” entries in that file and save the file

Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant

Reboot your system or use the following command

sudo /etc/init.d/dbus restart

Once you login back in to your machine you need to left-click the network manager icon in Gnome and select your wireless network It should prompts for password, type, etc and It will ask you to choose a password for your new “keyring”.

After enterring all the details my wireless network was connected and working fine you can see in the follwoing screen

My wireless network also detected available wireless access point around my home you can see this in the following screen

If you want to connect an existing wireless point you can see the following popup box asking for details of wireless network

If you want to create a new wireless network you can see the following screen with the available options and after entering all the details you need to click on connect

Possible Error and Solution

If you see the following error

The NetworkManager applet could not find some required resources. It cannot continue.

Solution

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
Tags: enable WPA Wireless in Ubuntu, Other Linux, wireless ubuntu, wpa access point ubuntu, wpa wireless


[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by chchatham on 2007-02-15
This worked great for me, thanks.  One note to other clueless noobs like me:

If you don't get the path just right on this command:
ndiswrapper -i /DRIVER/bcmwl5.inf
... then it won't work. In fact it will appear to install, but if you do this:
sudo ndiswrapper -l
You'll see the phrase: "Invalid Driver!"  If that is the case, you should do this:
sudo ndiswrapper -e bcmwl5
Then do sudo ndiswrapper -l again and make sure the list is empty, and then navigate to the directory where the bcmwl5.inf file is.  Do this:
sudo ndiswrapper -i bcmwl5.inf

And then complete the rest of the steps OldGaf provides.  Good luck...

---

### Post by pépère on 2007-02-18
Hello !

I have a Dell XPS M1210 and this network controller : Dell Wireless 1500 Draft 802.11n Dual-Band Wireless Mini-Card, for Core 2 Processors

I'm on Ubuntu edgy eft. There is an lspci :

**0c:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev [b]01)**

I've tried OldGaf's procedure, but it's failed... Can you tell me if the driver "bcmwl5.inf" is the good driver for my network controller ? 

 - On the web site of ndiswrapper, I have found this driver :
[http://ftp.us.dell.com/network/R129083.EXE]("http://ftp.us.dell.com/network/R129083.EXE")
 - and on th dell web site : [[http://support.dell.com/support/downloads/download.aspx?fileid=187881](http://support.dell.com/support/downloads/download.aspx?fileid=187881),]("http://support.dell.com/support/downloads/download.aspx?fileid=187881")

I have download these two files and try to use cabextract. For example :
```

cabextract R129083.EXE
R129083.EXE: no valid cabinets found

All done, errors in processing 1 file(s)

```

I have the same result with the second .exe file.

Does anyone have the same network controller or could help me to configure it ?

I'm sorry for my english (I'm french), and I hope my description of my problem is enough clear. 

Thank you very much.

---

### Post by truelifestudio on 2007-02-18
What part failed the build of Ndiswrapper or the install.

Type ndiswrapper tell us what it comes up with.

---

### Post by pépère on 2007-02-19
Thank you.

I think the installation of ndiswrapper is ok :

```
david@david-laptop:~/wifi$ cd ndiswrapper-1.34/
david@david-laptop:~/wifi/ndiswrapper-1.34$ make distclean
make -C driver clean
make[1]: entrant dans le répertoire « /home/david/wifi/ndiswrapper-1.34/driver »
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: quittant le répertoire « /home/david/wifi/ndiswrapper-1.34/driver »
make -C utils clean
make[1]: entrant dans le répertoire « /home/david/wifi/ndiswrapper-1.34/utils »
rm -f *~ *.o loadndisdriver
make[1]: quittant le répertoire « /home/david/wifi/ndiswrapper-1.34/utils »
rm -f *~
rm -fr ndiswrapper-1.34 ndiswrapper-1.34.tar.gz patch-stamp
make -C driver distclean
make[1]: entrant dans le répertoire « /home/david/wifi/ndiswrapper-1.34/driver »
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h
make[1]: quittant le répertoire « /home/david/wifi/ndiswrapper-1.34/driver »
make -C utils distclean
make[1]: entrant dans le répertoire « /home/david/wifi/ndiswrapper-1.34/utils »
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: quittant le répertoire « /home/david/wifi/ndiswrapper-1.34/utils »
rm -f .\#*
david@david-laptop:~/wifi/ndiswrapper-1.34$ make
make -C driver
make[1]: entrant dans le répertoire « /home/david/wifi/ndiswrapper-1.34/driver »
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/david/wifi/ndiswrapper-1.34/driver
make[2]: entrant dans le répertoire « /usr/src/linux-headers-2.6.17-11-generic »
  LD      /home/david/wifi/ndiswrapper-1.34/driver/built-in.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/crt.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/hal.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/iw_ndis.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/loader.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/ndis.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/ntoskernel.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/ntoskernel_io.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/pe_linker.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/pnp.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/proc.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/rtl.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/wrapmem.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/wrapndis.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/wrapper.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/usb.o
  CC [M]  /home/david/wifi/ndiswrapper-1.34/driver/divdi3.o
  LD [M]  /home/david/wifi/ndiswrapper-1.34/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/david/wifi/ndiswrapper-1.34/driver/ndiswrapper.mod.o
  LD [M]  /home/david/wifi/ndiswrapper-1.34/driver/ndiswrapper.ko
make[2]: quittant le répertoire « /usr/src/linux-headers-2.6.17-11-generic »
make[1]: quittant le répertoire « /home/david/wifi/ndiswrapper-1.34/driver »
make -C utils
make[1]: entrant dans le répertoire « /home/david/wifi/ndiswrapper-1.34/utils »
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: quittant le répertoire « /home/david/wifi/ndiswrapper-1.34/utils »
david@david-laptop:~/wifi/ndiswrapper-1.34$ sudo make install
Password:
make -C driver install
make[1]: entrant dans le répertoire « /home/david/wifi/ndiswrapper-1.34/driver »
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/david/wifi/ndiswrapper-1.34/driver
make[2]: entrant dans le répertoire « /usr/src/linux-headers-2.6.17-11-generic »
  Building modules, stage 2.
  MODPOST
make[2]: quittant le répertoire « /usr/src/linux-headers-2.6.17-11-generic »
echo /lib/modules/2.6.17-11-generic/misc
/lib/modules/2.6.17-11-generic/misc
mkdir -p /lib/modules/2.6.17-11-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.17-11-generic/misc
/sbin/depmod -a 2.6.17-11-generic -b /
make[1]: quittant le répertoire « /home/david/wifi/ndiswrapper-1.34/driver »
make -C utils install
make[1]: entrant dans le répertoire « /home/david/wifi/ndiswrapper-1.34/utils »
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: quittant le répertoire « /home/david/wifi/ndiswrapper-1.34/utils »
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8

```

But for drivers... :


```
david@david-laptop:~/wifi/ndiswrapper-1.34$ cd /home/david/wifi/
david@david-laptop:~/wifi$ sudo ndiswrapper -i /DRIVER/bcmwl5.inf
installing bcmwl5 ...
couldn't open /DRIVER/bcmwl5.inf: Aucun fichier ou répertoire de ce type at /usr/sbin/ndiswrapper line 172.
```

It means "no file or directory at /usr/sbin..."

But I have retryed just after and :

```
david@david-laptop:~/wifi$ sudo ndiswrapper -i /DRIVER/bcmwl5.inf
driver bcmwl5 is already installed
```

It's a bit strange no ?

After :

```
david@david-laptop:~/wifi$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 720.
```

But I have retryed too :

david@david-laptop:~/wifi$ sudo ndiswrapper -m
module configuration already contains alias directive

Finally :

```

david@david-laptop:~/wifi$ sudo depmod -a
david@david-laptop:~/wifi$ sudo modprobe ndiswrapper
```

I have rebooted, but there is no wifi...

What do you think of this ? Did I make an mistake in the procedure ?
I have exactly the same result with ndiswrapper 1.37 (the last stable version).

Thank you for your help.

---

### Post by pépère on 2007-02-20
Sorry, I forgot :

```
david@david-laptop:~$ ndiswrapper -l
bcmwl5 : invalid driver!

```

Thank you for your help.

---

### Post by tschneiter on 2007-02-20
Hey there, thanks for this quick guide.

I, too, am using the 802.11n card (not really a great choice, imo), in a 640m. I followed the directions you put down and it all worked out. A question or two though: since installing ndiswrapper, boot has lagged heavily on wifi initialization. Past that, it takes ~2 minutes for a connection to get picked up.

Has anyone noticed these problems?

---

### Post by grogger13 on 2007-02-20
I have E1705 with draft n and i just installed Ubuntu today, so i was following your instructions and then i got to "make install" and this is what came up

  CC [M]  /home/mike/ndiswrapper-1.34/driver/crt.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/hal.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/iw_ndis.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/loader.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/ndis.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/ntoskernel.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/ntoskernel_io.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/pe_linker.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/pnp.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/proc.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/rtl.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/wrapmem.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/wrapndis.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/wrapper.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/usb.o
  CC [M]  /home/mike/ndiswrapper-1.34/driver/divdi3.o
  LD [M]  /home/mike/ndiswrapper-1.34/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/mike/ndiswrapper-1.34/driver/ndiswrapper.mod.o
  LD [M]  /home/mike/ndiswrapper-1.34/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: Leaving directory `/home/mike/ndiswrapper-1.34/driver'
make -C utils
make[1]: Entering directory `/home/mike/ndiswrapper-1.34/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:179: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:179: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:206: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:218: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:218: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:222: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:223: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:225: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:233: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:233: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:233: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:250: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:250: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:252: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:260: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:262: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:268: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:268: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:272: warning: implicit declaration of function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:281: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:281: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:283: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:285: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘stat’
loadndisdriver.c:288: error: dereferencing pointer to incomplete type
loadndisdriver.c:289: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:295: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:295: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:300: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:304: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:314: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:319: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:322: error: dereferencing pointer to incomplete type
loadndisdriver.c:283: warning: unused variable ‘statbuf’
loadndisdriver.c:345: error: expected expression before ‘struct’
loadndisdriver.c:347: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:349: warning: implicit declaration of function ‘free’
loadndisdriver.c:356: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:368: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:371: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:371: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:375: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:377: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:377: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:408: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:368: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:420: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:420: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:425: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:427: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:428: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:430: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:435: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:437: error: dereferencing pointer to incomplete type
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:449: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:466: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:466: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:474: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:474: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:475: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:475: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:490: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:491: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:491: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:491: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:492: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:497: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:513: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:513: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:515: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:517: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:519: warning: implicit declaration of function ‘printf’
loadndisdriver.c:519: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:529: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:544: warning: implicit declaration of function ‘atof’
loadndisdriver.c:551: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:558: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:592: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/mike/ndiswrapper-1.34/utils'
make: *** [all] Error 2
mike@mike-laptop:~/ndiswrapper-1.34$ su
Password: 
root@mike-laptop:/home/mike/ndiswrapper-1.34# make install
make -C driver install
make[1]: Entering directory `/home/mike/ndiswrapper-1.34/driver'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/mike/ndiswrapper-1.34/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
echo /lib/modules/2.6.17-11-generic/misc
/lib/modules/2.6.17-11-generic/misc
mkdir -p /lib/modules/2.6.17-11-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.17-11-generic/misc
/sbin/depmod -a 2.6.17-11-generic -b /
make[1]: Leaving directory `/home/mike/ndiswrapper-1.34/driver'
make -C utils install
make[1]: Entering directory `/home/mike/ndiswrapper-1.34/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:179: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:179: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:206: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:218: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:218: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:222: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:223: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:225: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:233: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:233: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:233: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:250: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:250: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:252: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:260: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:262: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:268: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:268: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:272: warning: implicit declaration of function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:281: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:281: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:283: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:285: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘stat’
loadndisdriver.c:288: error: dereferencing pointer to incomplete type
loadndisdriver.c:289: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:295: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:295: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:300: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:304: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:314: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:319: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:322: error: dereferencing pointer to incomplete type
loadndisdriver.c:283: warning: unused variable ‘statbuf’
loadndisdriver.c:345: error: expected expression before ‘struct’
loadndisdriver.c:347: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:349: warning: implicit declaration of function ‘free’
loadndisdriver.c:356: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:368: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:371: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:371: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:375: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:377: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:377: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:408: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:368: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:420: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:420: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:425: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:427: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:428: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:430: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:435: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:437: error: dereferencing pointer to incomplete type
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:449: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:466: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:466: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:474: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:474: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:475: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:475: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:490: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:491: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:491: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:491: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:492: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:497: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:513: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:513: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:515: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:517: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:519: warning: implicit declaration of function ‘printf’
loadndisdriver.c:519: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:529: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:544: warning: implicit declaration of function ‘atof’
loadndisdriver.c:551: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:558: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:592: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/mike/ndiswrapper-1.34/utils'
make: *** [install] Error 2



Thats probably alittle to long to post, but im not sure what is relevant in that.

---

### Post by pépère on 2007-02-21
I'm a beginner, but have you installed these packages befor installing ndiswrapper ?
```

sudo aptitude install linux-headers-`uname -r` dh-make fakeroot build-essential
```

Hope that help.

---

### Post by twarner776 on 2007-02-21
I have tried to install following the instructions and sget server error when running the 'make install" command

The errors state loadndisdriver.c:1520: error: stdlib.h: No such file or directory.

It does this for around 20 directories.  I also get the following error

loadndisdriver.c:519 : Warning: implicit declaration of function `atoi'
there is several of these also.  Please help I am fairly new to ubuntu but I have not gotten this card to work in SuSe  or fedora.

---

### Post by pépère on 2007-02-21
YES !

For my network card, the drivers proposed by OldGaf doesn't work on my laptop.
So, I tryed to find the correct driver...

I was trying to use cabextract to get the .inf and .sys files of the .exe downloaded on dell web site.
It didn't work...

But the solution was to use unzip :

```
unzip nameofmyfile.exe
```

And it works !

I have download the last stable version of ndiwrapper (1.37) too. But all others  instructions of OldGolaf are good. 

Thank you everybody !

---

### Post by twarner776 on 2007-02-21
OK WIFI light is on and I configured in Networking.Thanks everyone that previously posted.  Keep in mind that I am new to this when I ask the question.

Where do I go next?
This is a fresh install ad all I have done is the instructions to get the card working. Please help
If I type iwlist scan shows{interface scanning..Frequency.. ECT. But I dont know where to go from here.

Thanks
Travis

---

### Post by twarner776 on 2007-02-21
ok next step. if i do a iwlist wlan0 scan  it shows all of the networks that I can connect to.
it shows my signal at 89.
But in connection properties it shows status as disconnected, and nothing on the signal meter.
If i go to SYSTEM-ADMIN-NETWORK TOOLSand select the device it says that the state is active and shows link speed of 130Mbps with multicast enabled. I tried to ping my router 192.168.1.1 and says destination host unreachable.
which tells me it is not connected. Just dont know where to go from here

---

### Post by twarner776 on 2007-02-21
aslo every time it restart or reboots i have to type sudo iwconfig wlan0

---

### Post by Ek0nomik on 2007-02-24
I followed your guide exactly.  I am rather new to Linux, so bear with me.  :)

I have the Network Manager working.  When I click it, it shows a wired connection as being in use.  When I unplug my ethernet cable however, I don't get a wireless option.

I guess Linux hasn't yet recognized my wireless card.

I saw some people doing a iwlist scan.  When I do it, I haven't been getting the same as others.

```
fleur@fleur-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.
```

Any ideas on how to get the Dell 1500 to work?

---

### Post by Ek0nomik on 2007-02-24
This is some of my output when following the guide:

```
fleur@fleur-laptop:/home/src/ndiswrapper-1.34$ sudo make distclean
Password:
make -C driver clean
make[1]: Entering directory `/home/src/ndiswrapper-1.34/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/src/ndiswrapper-1.34/driver'
make -C utils clean
make[1]: Entering directory `/home/src/ndiswrapper-1.34/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/src/ndiswrapper-1.34/utils'
rm -f *~
rm -fr ndiswrapper-1.34 ndiswrapper-1.34.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/src/ndiswrapper-1.34/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h
make[1]: Leaving directory `/home/src/ndiswrapper-1.34/driver'
make -C utils distclean
make[1]: Entering directory `/home/src/ndiswrapper-1.34/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/src/ndiswrapper-1.34/utils'
rm -f .\#*
fleur@fleur-laptop:/home/src/ndiswrapper-1.34$ sudo make
make -C driver
make[1]: Entering directory `/home/src/ndiswrapper-1.34/driver'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/src/ndiswrapper-1.34/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  LD      /home/src/ndiswrapper-1.34/driver/built-in.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/crt.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/hal.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/iw_ndis.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/loader.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/ndis.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/ntoskernel.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/ntoskernel_io.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/pe_linker.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/pnp.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/proc.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/rtl.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/wrapmem.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/wrapndis.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/wrapper.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/usb.o
  CC [M]  /home/src/ndiswrapper-1.34/driver/divdi3.o
  LD [M]  /home/src/ndiswrapper-1.34/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /home/src/ndiswrapper-1.34/driver/ndiswrapper.mod.o
  LD [M]  /home/src/ndiswrapper-1.34/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: Leaving directory `/home/src/ndiswrapper-1.34/driver'
make -C utils
make[1]: Entering directory `/home/src/ndiswrapper-1.34/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/src/ndiswrapper-1.34/utils'
fleur@fleur-laptop:/home/src/ndiswrapper-1.34$ sudo make install
make -C driver install
make[1]: Entering directory `/home/src/ndiswrapper-1.34/driver'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/src/ndiswrapper-1.34/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
echo /lib/modules/2.6.17-11-generic/misc
/lib/modules/2.6.17-11-generic/misc
mkdir -p /lib/modules/2.6.17-11-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.17-11-generic/misc
/sbin/depmod -a 2.6.17-11-generic -b /
make[1]: Leaving directory `/home/src/ndiswrapper-1.34/driver'
make -C utils install
make[1]: Entering directory `/home/src/ndiswrapper-1.34/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/src/ndiswrapper-1.34/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
fleur@fleur-laptop:/home/src/ndiswrapper-1.34$ sudo ndiswrapper -i /DRIVER/bcmwl5.inf
driver bcmwl5 is already installed
fleur@fleur-laptop:/home/src/ndiswrapper-1.34$ 

```

Any ideas?  Thanks!

---

### Post by Ek0nomik on 2007-02-24
```
fleur@fleur-laptop:~/Desktop/bcmdrivers$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
fleur@fleur-laptop:~/Desktop/bcmdrivers$ sudo ndiswrapper -l
bcmwl5 : invalid driver!
fleur@fleur-laptop:~/Desktop/bcmdrivers$ 

```

---

### Post by OldGaf on 2007-03-04
> **Ek0nomik said:**
> ```
fleur@fleur-laptop:~/Desktop/bcmdrivers$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
fleur@fleur-laptop:~/Desktop/bcmdrivers$ sudo ndiswrapper -l
bcmwl5 : invalid driver!
fleur@fleur-laptop:~/Desktop/bcmdrivers$ 

```

Hey Boss, sorry for not checking in sooner!

Are you still having problems with this? if so,

1. Remove the current driver being used by ndiswrapper:
ndiswrapper -e <driver>

2. Uninstall ndiswrapper 1.34:
in the ndiswrapper folder type "make uninstall"

3. Install the newest ndiswrapper from here: [sourceforge.net]("http://sourceforge.net/project/showfiles.php?group_id=93482")

4. Get the latest 1500 driver from here:
[http://support.dell.com/]("http://support.dell.com/support/downloads/download.aspx?c=us&fileid=187881&l=en&s=gen")

Let me know if you do this and the problem persists.

Also, check that the device is seen by ubuntu:
lspci

---

### Post by Ek0nomik on 2007-03-04
Sorry, I should have told you I got it working.  Your HOW TO definitely got me going in the right track, and gave me a bit of a learning experience too, which is always a good thing.  :)

Cheers Mate!

---

### Post by pépère on 2007-03-06
Back again...

my wifi works... but not perfectly !

Very often, I have some freezes, and this is always when my wifi connexion works. 
The connexion is also very unstable.

Do you have any idea to fix it ?

---

### Post by pépère on 2007-03-15
I am now waiting for feisty fawn, to see if my problem persists.

---

### Post by redman0570 on 2007-04-06
> **tschneiter said:**
> Hey there, thanks for this quick guide.

I, too, am using the 802.11n card (not really a great choice, imo), in a 640m. I followed the directions you put down and it all worked out. A question or two though: since installing ndiswrapper, boot has lagged heavily on wifi initialization.

Has anyone noticed these problems?

I'm having this exact problem, did you solve this?

---

### Post by achill3z on 2007-04-07
I'm a newb so I have to have a lot of stuff explained to me, but when I run tar -zxvf ndiswrapper-1.34.tar.gz I get the following
[HTML]britt@britt-laptop:~$ tar -zxvf ndiswrapper-1.34.tar.gz
tar: ndiswrapper-1.34.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors[/HTML]

Any help would be appreciated

Edit: 
Per pepere's suggestion, I ran this before I tried to install ndiswrapper
[HTML]sudo aptitude install linux-headers-`uname -r` dh-make fakeroot build-essential [/HTML]
I don't really know what that did.... :-\ but I ran this because when I ran [HTML]sudo apt-get install linux-headers-'uname-r'[/HTML]I got the following...[HTML]britt@britt-laptop:~$ sudo apt-get install linux-headers-'uname-r'
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname-r
[/HTML]

---

### Post by smlsteve on 2007-04-25
Is there a complete step by step to get the latest ndiswrapper all the was to switching directories(ndiswrapper) etc to extracting the exe file from dell yo grab the required files necessary to operate the wifi card because i cant get it to work all i have in networking is eth0 (wired LAN) and lo ???????? i dont know what that is. any help would be appreciated.
Running Dell XPS M2010, intel core duo 2.7,4 g ram,radeon x1800 256, Thanks

---

### Post by redman0570 on 2007-04-25
> **smlsteve said:**
> Is there a complete step by step to get the latest ndiswrapper all the was to switching directories(ndiswrapper) etc to extracting the exe file from dell yo grab the required files necessary to operate the wifi card because i cant get it to work all i have in networking is eth0 (wired LAN) and lo ???????? i dont know what that is. any help would be appreciated.
Running Dell XPS M2010, intel core duo 2.7,4 g ram,radeon x1800 256, Thanks

Start from the top of this tread, it has all the info you need.

---

### Post by ijn on 2007-05-01
this post is for the guys who managed to work this chip in their machines under linux ubuntu.
can someone make a guide for beginners to make work this wireless card on a dell inspiron 6400/1505???

should include: ubuntu fesity, kernel 2.6.20.15, X server 7.2, dell inspiron 6400/1505 and a working configuration of ndiswrapper versions and the dell windows drivers(the last two  are R129083, R151517).

I thought that linux OS was hard for me to deal with....  but it turned out that making work a wireless card from broadcom inside linux was the real deal. in front of this installing fglx, beryl, and whatever ...is a piece of cake.I tried out the first page guide,,,,but nothing and also some other howtos, but zero.:( 

please help me....

---

