---
title: "MCI DVB-T for TV on USB stick"
date: 2011-12-20
forum: Hardware
---

### Post by honeybear on 2011-12-20
Hello, 

I have a : 

```
[ 1177.922817] usb 2-1.6: USB disconnect, address 4
[ 1215.182963] usb 2-1.6: new high speed USB device using ehci_hcd and address 5
[ 1215.276808] usb 2-1.6: New USB device found, idVendor=048d, idProduct=9135
[ 1215.276813] usb 2-1.6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 1215.276933] usb 2-1.6: configuration #1 chosen from 1 choice
```

lsusb gives:
Bus 002 Device 005: ID 048d:9135 Integrated Technology Express, Inc. Zolid Mini DVB-T Stick


However no /dev/video* is there. How could I get one please? 

thank you

---

### Post by zniavre on 2012-04-01
hello
same problem here with differents kernel on oneiric 

3.2 and 3.3 (from kernel team ) loads modules it913x but no firmwares are loaded.

no /dev/dvb are created and device still unusable ...

hope it will quite soon

---

### Post by Nirro on 2012-04-14
I have the same problem with Precise 12.04

lsusb :
```

Bus 005 Device 002: ID 048d:9135 Integrated Technology Express, Inc. Zolid Mini DVB-T Stick

```

dmesg :
```

[   10.080592] it913x: Chip Version=02 Chip Type=9135
[   10.082054] it913x: Dual mode=0 Remote=5 Tuner Type=88
[   10.246396] it913x: DEV it913x Error
[   10.246436] usbcore: registered new interface driver it913x

```

---

### Post by honeybear on 2012-04-16
the problem is that there is no support from ubuntu for dvb-t
and the wiki ubuntu about that posts fake information :(

any dvb-t from stores are likely not to work with a plug n play, contrary to the wiki.

---

### Post by Nirro on 2012-04-21
> **Nirro said:**
> I have the same problem with Precise 12.04

lsusb :
```

Bus 005 Device 002: ID 048d:9135 Integrated Technology Express, Inc. Zolid Mini DVB-T Stick

```

dmesg :
```

[   10.080592] it913x: Chip Version=02 Chip Type=9135
[   10.082054] it913x: Dual mode=0 Remote=5 Tuner Type=88
[   10.246396] it913x: DEV it913x Error
[   10.246436] usbcore: registered new interface driver it913x

```

I succeeded to install driver to this device and make it work (done on Precise but also other versions might work).

This is how :

First of all, download Video4Linux (V4L which holds all the development drivers):
```

sudo apt-get git
mkdir v4l
cd v4l
git clone git://linuxtv.org/media_build.git

```

now compile :
```

cd media_build/
sudo apt-get install libproc-processtable-perl
./build

```

Check that it compiled successfully, if not download missing packages and repeat the ./build command until it succeeds (I was needed to install libproc-processtable-perl so I already wrote it above )

When compiled successfully, install it with :
```

sudo make install

```

get the firmware, unzip, inflate and install it :
```

cd ..
wget http://www.ite.com.tw/uploads/firmware/v3.6.0.0/dvb-usb-it9135.zip
unzip dvb-usb-it9135.zip
dd if=dvb-usb-it9135.fw ibs=1 skip=64 count=8128 of=dvb-usb-it9135-01.fw
dd if=dvb-usb-it9135.fw ibs=1 skip=12866 count=5817 of=dvb-usb-it9135-02.fw
sudo cp dvb-usb-it9135-0* /lib/firmware/

```

Now reboot,
If all goes well you should see a success in dmesg (it might be slightly different for you but should not see Error line) :
```

dmesg |grep it913x

[    9.662488] it913x: Chip Version=02 Chip Type=9135
[    9.662971] it913x: Firmware Version 52887808
[    9.664347] it913x: Dual mode=0 Remote=5 Tuner Type=88
[   10.440743] it913x-fe: ADF table value	:00
[   10.444620] it913x-fe: Crystal Frequency :12000000 Adc Frequency :20250000 ADC X2: 01
[   10.480838] it913x-fe: Tuner LNA type :38
[   10.689092] it913x: DEV registering device driver
[   10.689119] usbcore: registered new interface driver it913x


```

and the device /dev/dvb/ should exist.

---

### Post by daymz on 2012-09-18
Thanks for the tip.  It seems to work fine, now the driver is able to upload the firmware.

Note: I had to remove and re-insert by DVB-T USB dongle, as on reboot, it failed to identify the driver (the dongle may have been in an unstable state of some kind).

By the way, I had found this guide which explains how to install DVB-T (MediaBuild) also:
[https://help.ubuntu.com/community/DVB-T_%28USB%29]("https://help.ubuntu.com/community/DVB-T_%28USB%29")
But it was missing the firwmare part.

Next step, find a player and be able to scan channels !

---

### Post by JMED106 on 2012-10-22
Hi,

I already can watch live tv in ubuntu 12.10 using either kaffeine or mythtv. But I am not able to use the remote.

I tried using lirc and irrecord, and despite irrecord detects the remote, when I use irw nothing happens.

If you know any way to make the remote works ...

Thanks in advance.

---

### Post by ionraedt on 2012-10-28
I can also watch DVB-T using Kaffeine under Ubuntu 12.10.
Following Nirro's directions was easy and efficient !
Thank you Nirro

---

### Post by ionraedt on 2012-10-28
I forgot to mention: my USB DVB-T tuner:
model : CTX1938 V2.1.1 (distributed through Medion/Aldi).
ID : 048d:9135
Firmware : dvb-usb-it9135-02.fw
Recognised (lsusb) as : ITE Inc. Zolid Mini DVB-T stick

As I told in earlier message, it works fine now with Nirro's tips !

---

### Post by ionraedt on 2012-10-29
> **ionraedt said:**
> I forgot to mention:

my USB DVB-T tuner:
model : CTX1938 V2.1.1 (distributed through Medion/Aldi).
ID : 048d:9135
Firmware : dvb-usb-it9135-02.fw
Recognised (lsusb) as : ITE Inc. Zolid Mini DVB-T stick

As I told in earlier message, it works fine now with Nirro's tips !

To make things more complete, I received message from Creatix Support with pre-release of the driver attached (The driver is for ITEtech 9135 based USB TV modules) :

"Hallo Herr Onraedt,
im Anhang ein nicht freigegebener ungetesteter Linux Treiber. Bitte auf einem Testsystem ausprobieren.
mit freundlichen Grüßen
Peter Hirschmann 
attachment : linux.zip"

I don't know how to attach this zipfile here but if anyone is interested please ask : [email]ivo.onraedt@advalvas.be[/email]

---

### Post by kevinl on 2012-11-06
This is small error in these instructions relating to installing git, namely, the author says "sudo apt-get git".  This will not work.

I suggest rewording to:
"In order to proceed with the following it is firstly necessary that you have an application called "git" installed on your PC.  To do that you have to type at the command line within a terminal screen:
sudo apt-get install git
When you do that you will be asked to type in your password to have the necessary privileges to install the software."

Hope this helps.  Otherwise it is great  post and very helpful.  I would strongly recommend to the Ubuntu crew (who do such a fabulous job) to include this in the installation of the operating system as, more and more, people are looking to use their PC with packages like MythTV to watch TV and have a "Home Theatre PC" system.

---

### Post by ekhaat on 2013-01-06
Hmm, make fails with this:

```

make -C firmware install
make[2]: Entering directory `/home/ekhaat/v4l/v4l/media_build/v4l/firmware'
make[2]: *** No rule to make target `../../linux/firmware/ihex2fw.c', needed by `ihex2fw'.  Stop.
make[2]: Leaving directory `/home/ekhaat/v4l/v4l/media_build/v4l/firmware'
make[1]: *** [firmware_install] Fejl 2
make[1]: Forlader katalog '/home/ekhaat/v4l/v4l/media_build/v4l'
make: *** [install] Fejl 2

```And I DID put "install" in the "sudo apt-get git" line.


Any Idea??

Cheers

---

### Post by alek66 on 2013-06-02
HEy... I am bit stucked on getting mine to work.

Here the specs:
Lsusb
```
Bus 001 Device 005: ID 048d:9135 Integrated Technology Express, Inc. Zolid Mini DVB-T Stick

```

Dmesg:
```
[ 1188.530649] usb 1-6: USB disconnect, device number 5
[ 1190.308134] usb 1-6: new high-speed USB device number 6 using ehci_hcd
[ 1190.442191] usb 1-6: New USB device found, idVendor=048d, idProduct=9135
[ 1190.442204] usb 1-6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 1190.445909] it913x: Chip Version=02 Chip Type=9135
[ 1190.448022] it913x: Dual mode=0 Remote=5 Tuner Type=e
[ 1190.448383] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try to load a firmware
[ 1190.452031] usb 1-6: firmware: agent aborted loading dvb-usb-it9137-01.fw (not found?)
[ 1190.452031] it913x: DEV it913x Error

```

Any ideas how to get out of this ?

THanks!

---

### Post by alek66 on 2013-06-02
Got the firmware done:

> [    9.563956] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try to load a firmware
[   10.248015] Registered led device: rt2800usb-phy0::radio
[   10.248015] Registered led device: rt2800usb-phy0::assoc
[   10.248015] Registered led device: rt2800usb-phy0::quality
[   10.248015] usbcore: registered new interface driver rt2800usb
[   10.490825] usb 1-6: firmware: agent loaded dvb-usb-it9137-01.fw into memory
[   11.976295] usbcore: registered new interface driver it913x
[   33.278660] rt2800usb 1-4:1.0: firmware: agent loaded rt2870.bin into memory


Any idea now how to make it work under mplayer or VLC???

---

### Post by The_Cunning_Stunt on 2013-08-02
> **ekhaat said:**
> Hmm, make fails with this:

```

make -C firmware install
make[2]: Entering directory `/home/ekhaat/v4l/v4l/media_build/v4l/firmware'
make[2]: *** No rule to make target `../../linux/firmware/ihex2fw.c', needed by `ihex2fw'.  Stop.
make[2]: Leaving directory `/home/ekhaat/v4l/v4l/media_build/v4l/firmware'
make[1]: *** [firmware_install] Fejl 2
make[1]: Forlader katalog '/home/ekhaat/v4l/v4l/media_build/v4l'
make: *** [install] Fejl 2

```And I DID put "install" in the "sudo apt-get git" line.

Any Idea??

Cheers
I got a similar problem. What I did was to take the instructions that [COLOR=#000000]daymz referred to and then [/COLOR][COLOR=#000000]Nirro's instructions
[/COLOR]So, in total
> #To get the device recognised
#In terminal, you are in your home folder type
sudo mkdir v4l
cd v4l
sudo apt-get install git linux-headers-$(uname -r) build-essential patchutils libproc-processtable-perl
sudo git clone git://linuxtv.org/media_build.git
#this will create a folder called media_build within the folder v4l
cd media_build
sudo ./build
sudo make install


#To run the appropriate driver for the device
cd ..
sudo wget [http://www.ite.com.tw/uploads/firmware/v3.6.0.0/dvb-usb-it9135.zip](http://www.ite.com.tw/uploads/firmware/v3.6.0.0/dvb-usb-it9135.zip)
unzip dvb-usb-it9135.zip
sudo dd if=dvb-usb-it9135.fw ibs=1 skip=64 count=8128 of=dvb-usb-it9135-01.fw
sudo dd if=dvb-usb-it9135.fw ibs=1 skip=12866 count=5817 of=dvb-usb-it9135-02.fw
sudo cp dvb-usb-it9135-0* /lib/firmware/
cd ..
#for me I deleted the folder as any necessary files have already been installed
sudo rm v4l -r


#Then reboot and type 
Dmesg | tail 
#to check, and you should get 
[  176.526508] DVB: registering new adapter (ITE 9135(9005) Generic)
[  176.630108] it913x-fe: ADF table value       :00
[  176.634163] it913x-fe: Crystal Frequency :12000000 Adc Frequency :20250000 ADC X2: 01
[  176.674645] it913x-fe: Tuner LNA type :38
[  176.729007] usb 1-6: DVB: registering adapter 0 frontend 0 (ITE 9135(9005) Generic_1)...
[  176.800102] Registered IR keymap rc-it913x-v2
[  176.800473] input: ITE 9135(9005) Generic as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/rc/rc0/input15
[  176.800739] rc0: ITE 9135(9005) Generic as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/rc/rc0
[  176.800759] usb 1-6: dvb_usb_v2: schedule remote query interval to 250 msecs
[  176.800774] usb 1-6: dvb_usb_v2: 'ITE 9135(9005) Generic' successfully initialized and connected

---

### Post by Keith_Beef on 2013-10-17
I recently got a USB DVB-T tuner
```

Bus 001 Device 003: ID 048d:9135 Integrated Technology Express, Inc. Zolid Mini DVB-T Stick

```

I went through the steps given in this thread, and got Kaffeine working by scanning on the fr-Paris list.

I get five channels, listed below.
France 2	GR1 B	-1
France 3	GR1		-1
France 5	GR1 B	-1
France Ô	GR1 B	-1
LCP		GR1 B	-1

Sometimes the image pixellates and the sound garbles, but no more than the TV over Internet that was in the rented house I lived in last year.

---

### Post by Keith_Beef on 2013-11-07
> **Keith_Beef said:**
> I recently got a USB DVB-T tuner
```

Bus 001 Device 003: ID 048d:9135 Integrated Technology Express, Inc. Zolid Mini DVB-T Stick

```

I went through the steps given in this thread, and got Kaffeine working by scanning on the fr-Paris list.

I get five channels, listed below.
France 2	GR1 B	-1
France 3	GR1		-1
France 5	GR1 B	-1
France Ô	GR1 B	-1
LCP		GR1 B	-1

Sometimes the image pixellates and the sound garbles, but no more than the TV over Internet that was in the rented house I lived in last year.

Well, since upgrading to 12.04 LTS I have lost the use of this DVB-T tuner.

The driver is present already, but seems to be unable to load the firmware .
I downloaded a firmware and created the file dvb-usb-it9137-01.fw as per [the LinuxTV instructions]("http://www.linuxtv.org/wiki/index.php/Kworld_UB499-2T"), but still no joy.

I now have three firmware files for the it913x tuners:
```
ls -al /lib/firmware/ | grep it913
-rw-r--r--  1 root root    8128 Oct 17 17:15 dvb-usb-it9135-01.fw
-rw-r--r--  1 root root    5817 Oct 17 17:15 dvb-usb-it9135-02.fw
-rw-r--r--  1 root root    5731 Nov  6 22:09 dvb-usb-it9137-01.fw
```

the driver seems to try to load the it9137 firmware, but fails. The output from dmesg is below.
```
[ 4441.866130] usb 1-4.1.1: USB disconnect, device number 7
[ 4458.704267] usb 1-4.1.1: new high-speed USB device number 10 using ehci_hcd
[ 4458.799002] it913x: Chip Version=02 Chip Type=9135
[ 4458.800505] it913x: Dual mode=0 Remote=5 Tuner Type=8a
[ 4458.801630] dvb-usb: found a 'ITE 9135 Generic' in cold state, will try to load a firmware
[ 4458.802976] dvb-usb: downloading firmware from file 'dvb-usb-it9137-01.fw'
[ 4458.803388] it913x: FRM Starting Firmware Download
[ 4459.284011] it913x: FRM Firmware Download Failed (ffffffed)
[ 4459.484133] it913x: Chip Version=00 Chip Type=0000
[ 4460.320143] it913x: DEV it913x Error
```

---

