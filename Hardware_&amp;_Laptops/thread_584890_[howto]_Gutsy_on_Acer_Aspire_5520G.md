---
title: "[howto] Gutsy on Acer Aspire 5520G"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by mare_ on 2007-10-21
Hi guys!

This is my first attempt to write a howto (as well as my first attempt to install linux on a laptop). Anyway, as I found almost no information on how to solve the problems with this laptop on google, I thought I'd share what I had managed to do - maybe somebody will find it useful ;)

The laptop I have is Acer Aspire 5520G - it has Turion 64 x2 CPU, nvidia 8400M G, 2GB RAM, 160GB hard disk, wireless card, built-in card reader, webcam ... The main problems were:
- no sound,
- no wireless,
- the webcam didn't work,
- hibernation didn't work, i couldn't set lcd brightness...

Graphics work nicely once you enable restricted drivers, the resolution is correct and desktop effects work. The card reader also seems to work.

Ok, so how to solve those problems (btw, although this is a 64 bit machine, I have the 32 bit version of ubuntu installed, so this instructions are (probably) for 32 bit ubuntu only):

**ACPI**
Install [acer_acpi module]("http://code.google.com/p/aceracpi/") according to [these instructions.]("http://code.google.com/p/acer-acpi-deb/"). You should now be able to set lcd brightness, put the laptop to sleep...

**WIRELESS**
Basically, you have to use ndiswrappwer with windows drivers. Follow the instructions in this topic [HOWTO: Atheros AR5007EG on Feisty Fawn (with ndiswrapper)]("http://ubuntuforums.org/showthread.php?t=512828") (don't worry if the sticker underneath your laptop says atheros arbxb63 - it is the same card). And i'm not sure, but I think you need to have acer_acpi module installed for this to work. ;)

**SOUND**
You have to compile and install the latest alsa - 1.0.15.
[LIST=1]
[*]First of all, stop alsa-utils and alsasound```
sudo /etc/init.d/alsa-utils stop
sudo /etc/init.d/alsasound stop
```
[*]Download and extract alsa-driver, alsa-lib and alsa-utils from [http://www.alsa-project.org]("http://www.alsa-project.org")
[*]Compile and install them according to INSTALL file in each folder (basically, run ./configure, make and sudo make install in each folder)
[*]run ```
alsaconf
```
[*]Copy /lib/modules/*(kernel version)*/kernel/sound/pci/hda/snd-hda-intel.ko to /lib/modules/*(kernel version)*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko.
Copy following files from modules sub folder of your alsa installation folder to /lib/modules/*(kernel version)*/kernel/sound:
```
snd-hda-intel.ko
snd-hwdep.ko
snd-mixer-oss.ko
snd-page-alloc.ko
snd-pcm-oss.ko
snd-rtctimer.ko
snd-seq-device.ko
snd-seq-midi-event.ko
snd-seq-midi.ko
snd-seq-oss.ko
snd-seq.ko
snd-timer.ko
snd.ko

```

Now run ```
depmod -a
```
[*]Start alsasound and alsa-utils```

sudo /etc/init.d/alsa-utils start
sudo /etc/init.d/alsasound start
```
[*]Run ```
alsamixer
```, unmute channels and set the volume
[*]It should work ;) 
[/LIST]

**WEBCAM**
You need to compile the latest uvcvideo driver.

[LIST=1]
[*]Remove uvcvideo module; run ```
sudo rmmod uvcvideo
```
[*]Install subversion (you need this to checkout the uvcvideo source code from their servers) ```
sudo apt-get install subversion
```
[*]Checkout (="download") the source:```
 svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk linux-uvc
```
[*]Go to linux-uvc folder and edit the Makefile file; change ```
INSTALL_MOD_DIR	:= usb/medi
``` to ```
INSTALL_MOD_DIR	:= ubuntu/media/usbvideo
```.
[*]Run ```
make
``` and ```
sudo make install
```
[*] Run ```
sudo modprobe uvcvideo
```

And it should work ;) aMsn gave me an error when I tried to configure the web cam, but I clicked Next it worked anyway :P
[/LIST]

Ok, I hope I haven't forgotten anything... If I have, or if you have any problems (or if my instructions are incomprehensible :P) or if I've written/done something utterly stupid, please do tell ;)

---

### Post by iansen on 2007-10-21
Thanks  for the tips ....I have the same laptop but I can't get the video card to work ( I get a xserver error)- if I update the the driver it works fine.
The problem is that when I restart the computer and try Ubuntu again xserver stops working and I have to reinstall the video driver and and restart x  - it seem that it can not load the kernel modules for the video driver - the driver version differs from the module version .

Any ideas?
BTW did you keep the Vista installation the laptop came with ? If so does it still work if you have a dual boot  Ubuntu/ Vista ?

Thanks again for the tips .

---

### Post by zkeng on 2007-10-27
Just wanted to thank you for posting this howto. It helped me alot to get the last few things, the webcam and the front panel head phones, working on my new Acer Travelmate 7520G.

I downloaded and installed the ati 8.41 driver from amd website and it works fine even though it&#347; not detected by the restricted drivers manager. Now everything exept sleep and hibernate is working just fine, but what the heck i disabled them in gconf-editor, the computer is a fast rebooter anyway. Still got the vista install on the machine for running archicad, but Gutsy Studio is what i use for everything else.

Iansen, ubuntu will not mess with your vista install as long as you do not make it :) . I keep windows for running som apps that i use at work, and do a little special when it comes to mounting my windows files. In fstab i mount the windows partition in /media/restricted/vista. Then i set the permission so that no one but root can access the restricted folder and finally do a bind mounting in fstab of my vista user directory so that it is mounted in my ubuntu home directory. In that way i can reach my windows documents from ubuntu but no one will have permission to mess up the windows installation from ubuntu.

/chers

---

### Post by mpetrovic on 2007-11-05
Huhh..

After installing Ubuntu 7.10, the only problem i've had on my Acer 7720G is with sound. I've followed your instructions, but still cannot hear anything (and nothing is muted). I know that the sound driver is now correct as the Audacity's microphone monitor shows activity when I tip the built-in microphone, but it just doesn't work.

Should I change something at System>Preferences>Sound, or I'm missing something else?

Right now, the sound preferences looks like this:

[IMG]http://img232.imageshack.us/img232/8139/screenshotsoundpreferenpi3.png[/IMG]



[COLOR="Red"]**EDIT:**[/COLOR]

I've just made it work by editing /etc/modprobe.d/alsa-base and adding a line at the end "options snd-hda-intel model=acer"

---

### Post by porcosuino on 2007-11-19
i have your same laptop, but i can install acer-acpi, because i receive an error when i try to insert module. what can i do? i use last acer-acpi version.

the error is:
FATAL: Error inserting acer_acpi (/lib/modules/2.6.22.3/extra/acer_acpi.ko): No such device

with all kernel version that i try.

thanks in advice
Luigi

---

### Post by creoiD on 2007-12-25
i have the same laptop, but unfortunately i received error
> ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

is this error critical and so what should i do?

---

### Post by cathectic on 2007-12-25
> **mare_ said:**
> **ACPI**
Install [acer_acpi module]("http://code.google.com/p/aceracpi/") according to [these instructions.]("http://code.google.com/p/acer-acpi-deb/"). You should now be able to set lcd brightness, put the laptop to sleep...
acer_acpi has nothing to do with suspend - all it does is toggle the radio on the wireless card, enable/ disable bluetooth and can control the LCD panel backlight.

In some cases, the wireless button on the laptop, or even the wireless driver, can handle turning the card on - in many cases, they can't, which is where acer_acpi comes in.

---

### Post by sharelove on 2008-02-15
Hi Mare,
thanks it seems really nice what you've done. However, you lose me at instruction #3...could you please post more explicit instructions? Saying just do the sudo/make/install doesn't work for me as I am a noob...I really want to get this sound card working!! then I can get rid of vista too - look forward to that!
Pierce

---

### Post by Angel4Life on 2008-06-30
Hello, I hope this helps.I have a acer 5520G and I tried doing it your way but had no luck and when I found the solution it was easy.To get your bluetooth working try this - 
Windows Mobility Center
The Windows Mobility Center collects key mobile-related system settings in one
easy-to-find place, so you can quickly configure your Acer system to fit the
situation as you change locations, networks or activities. Settings include display
brightness, power plan, volume, wireless networking on/off, external display
settings, display orientation and synchronization status.
Windows Mobility Center also includes Acer-specific settings like Bluetooth Add
Device (if applicable), sharing folders overview/sharing service on or off, and a
shortcut to the Acer user guide, drivers and utilities.
To launch Windows Mobility Center:
&#8226; Start Windows Mobility Center from the Accessories program group in the
Start menu.Then click on the add button on the bluetooth section( please make sure that your mobile phones bluetooth is activated before clicking on add) and then you should be up and running.

Kind regards
K.Wright

---

