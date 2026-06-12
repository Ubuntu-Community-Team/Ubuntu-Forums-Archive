---
title: "Sony Vaio VPCS11C5E and WWAN"
date: 2010-04-08
forum: Hardware
---

### Post by Darkav on 2010-04-08
Hi guys, 

I cannot see the WWAN hardware using lsusb.
I tried with 2.6.31-14-generic and 2.6.32-19-generic
I think that i should use an adapted version of sony_laptop modules...but the one that I found here ([http://www.logic.at/people/preining/software/](http://www.logic.at/people/preining/software/)) it didn't work (no suprise, it's for the z-series). 

Does anyone succeded in turning on the wwan hardware?

---

### Post by K. Hendrik on 2010-04-19
I just bought the same laptop, so I'm interested in getting the WWAN too. Did you have any luck by now? And did you get the Graphics too work with the NVIDIA-Driver? I've got a NVIDIA GeForce 310m. The fingerprintreader doesn't seem to be supported either, a lot of work to do... but in a week or so I'll have some time to test. I'll keep you informed if something new happens.

---

### Post by Darkav on 2010-04-19
> **K. Hendrik said:**
> I just bought the same laptop, so I'm interested in getting the WWAN too. Did you have any luck by now? And did you get the Graphics too work with the NVIDIA-Driver? I've got a NVIDIA GeForce 310m. The fingerprintreader doesn't seem to be supported either, a lot of work to do... but in a week or so I'll have some time to test. I'll keep you informed if something new happens.

I suspect that we have the same configuration :)

To make the nvidia works, I added to the xorg.conf:
    Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/IGPU/LCD0/EDID"

About the WWAN: if you see, the device is not recognized with lsusb. The reason is that the card is switched off by default. To make the car swith on, i have to use the 2.6.33 kernel. With this kernel i see the qualcomm card (ID 05c6:9224 Qualcomm, Inc. ).
To make the card work, i then loaded a modified version of qcserial, installed the gobi loader and added the correct firmware to the /lib/formware/gobi location. Now i see the wwan, i can start a communication with the SIM but an AT command returns me an error. I'm investigating about that, but i think that it's a SIM issue...

Abou the fingerprint: i can set and test it with this: [http://www.n-view.net/Appliance/fingerprint/](http://www.n-view.net/Appliance/fingerprint/) 
The device is: ID 147e:1001 Upek 
I don't know how to use it (i will investigate about that either)...i want to use it for the lock screen feature.

Notice that currently I'm running lucid lynx with a 2.6.33 kernel...

---

### Post by K. Hendrik on 2010-04-22
Hi again,

I just read this about fprint, it's a different fingerprint-sensor but it's sony perhaps they did the same thing [fprint/wiki/Unsupported_devices#UPEK_devices_in_Sony_laptops]("http://reactivated.net/fprint/wiki/Unsupported_devices#UPEK_devices_in_Sony_laptops")

And I've got another question, do you own the black-model with the keyboard-backlight? It's not really working properly with linux it's always on when i type, it doesn't use the room-light-sensor did you manage to aktivate the sensor, or do you know how i could turn the light on and off?

Anotherthing, do you have a link to a how to setup the WWAN?

---

### Post by Darkav on 2010-04-26
> **K. Hendrik said:**
> (...)

And I've got another question, do you own the black-model with the keyboard-backlight? It's not really working properly with linux it's always on when i type, it doesn't use the room-light-sensor did you manage to aktivate the sensor, or do you know how i could turn the light on and off?

Anotherthing, do you have a link to a how to setup the WWAN?

Sorry, i don't have the keyboard-backlight...

---

### Post by K. Hendrik on 2010-04-26
OK.

But back to the topic, I tried to install WWAN this weekend, i tried Karmic and Lucid, I also installed the 2.6.33 Kernel and tried again. What i did ist this:

1. get the kernel source with "*sudo apt-get install linux-source*"
2. create an entry for the sony card (9224 and 9225)
3. compile and load with depmod -A (reboot)

At this point I think a device /dev/ttyUSB0 is supposed to show up but it doesn't.

4. install gobi-loader 0.5 

when trying to load gobi-loader manually "*sudo ./gobi-loader /dev/ttyUSB0 /lib/firmware/gobi*" it complains about the missing device.

Ps: I copied the firmware from *C:\Program Files (x86)\QUALCOMM\Images\Sony\UMTS\*

---

### Post by zerohero on 2010-05-19
I feel your pain, as I struggled many days with this (on a t410s). However, I am posting this successfully using gobi_2000 on lucid :) Ok, on to business:

Assuming you are familiar with this thread [http://www.madox.net/blog/2010/01/06/hp5310m-un2420-wireless-gobi2000-module-in-ubuntu/]("http://www.madox.net/blog/2010/01/06/hp5310m-un2420-wireless-gobi2000-module-in-ubuntu/"), download the patched and attached qcserial.

then
```

tar zxfv qcserial_27Apr10.tar.gz
cd qcserial_27Apr10
sudo make install

```
(You should of course take a quick look in the Makefile first, to make sure that I am not trying to make you install malware :) )

You also need to install the latest gobi_loader: [http://aur.archlinux.org/packages.php?ID=30943]("http://aur.archlinux.org/packages.php?ID=30943").

Ensure your modem's first (the one it reports with lsusb before gobi-loader is run) usb-id is in /etc/udev/rules.d/60-gobi.rules, if not, just copy/paste an entry and change the id.

Then you can run gobi_loader as such:
```

sudo /lib/udev/gobi_loader -2000 /dev/ttyUSB0 /lib/firmware/gobi/

```


Then do
```

sudo pkill modem-manager

```
and pray :)

To debug after running gobi-loader, and verify that your modem responds properly, see [3Gprobing]("https://wiki.kubuntu.org/NetworkManager/Hardware/3G/Probing#Probe%20script%20for%20modem%20capabilities")

I, for one, had to insert the sim-card in a phone and change the pin-code before it would work.

Tested on 2.6.32-21-generic

P.S
Lucid seems to sometimes boot too fast for gobi-loader to run properly. 
Then i just load gobi_loader manually as described above and kill modem-manager. If all else fails, do a cold reboot (shutdown, then restart)

---

### Post by albein on 2010-05-19
ok, but where to download the firmware if you already deleted the Windows 7 on the laptop ?

---

### Post by zerohero on 2010-05-20
It's illegal to distribute the firmware, so maybe you can order restore cd's from Sony?

However, it seems there is an easier solution for sony laptops,  see this thread: [http://ubuntuforums.org/showthread.php?t=1478684&highlight=sony+wwan]("http://ubuntuforums.org/showthread.php?t=1478684&highlight=sony+wwan")

You could try that, and see what happens.

---

### Post by zerohero on 2010-05-20
See also this thread for Gobi 2000 on lucid, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554099") contains link to firmware if necessary. (Maybe it is not illegal?)

The patch above is a convenience-version of Viktor Petrovs patching, but still requires the firmware placed in /usr/lib/firmware

---

### Post by K. Hendrik on 2010-06-07
Status Update:

I've updated to a mainline 2.6.35 Kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/") which has a working qcserial and loads it succesfull at boot. After installing gobi-loader 0.6 from [http://www.codon.org.uk/~mjg59/gobi_loader/download/]("http://www.codon.org.uk/~mjg59/gobi_loader/download/") the modem is "kindof" usable, it shows up in the modem manager but after I configured it (vodafone germany websessions) and try to connect by klicking on "Vodafone (D2) WebSessions 1" i get an "Connection Seperated" (my translation from german) but this is so fast there couldn't have been a connection test.
The 3G probing mentioned before fails because /dev/ttyUSB0 ist in use.
Really could need some help here.


The fingerprint however works fine with the new fingerprint-gui 0.14 from [http://www.n-view.net/Appliance/fingerprint/downloads.php]("http://www.n-view.net/Appliance/fingerprint/downloads.php")

---

### Post by K. Hendrik on 2010-06-08
Another Update + Bump

I tried the Probe.txt/Chat methode again with Mobile Broadband disabled (which seems to release the ttyUSB0 device from use) but now all I get as an response is "Failed". I also tried removing the SIM-Pin with my mobilephone and trying again but still only "Failed" as a response.

really need help here.

---

### Post by K. Hendrik on 2010-07-30
Still not solved

---

