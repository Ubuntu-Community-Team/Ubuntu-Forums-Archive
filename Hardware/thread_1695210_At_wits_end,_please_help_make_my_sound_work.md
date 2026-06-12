---
title: "At wits end, please help make my sound work"
date: 2011-02-25
forum: Hardware
---

### Post by autoimmune on 2011-02-25
I recently decided to try ubuntu on my netbook, so i formatted my hard drive to ext 4 and installed. All has been going relatively well except i cant get the sound to work at all. Zero sound comes out of the speakers. The sound setup worked perfectly fine under windows 7. I have tried pretty much everything. I am not new to the world of computers but i am new to linux, so i am hoping its something easy. Here is all the relevant information. 

-Model number of laptop - hp 110-3135DX
-Version of OS - Ubuntu 10.04, upgrade from fresh install of 9.10 via flash drive
-Desktop environment - netbook edition
-Hardware tab of Sound Preferences - Internal Audio/Analog Stereo Duplex
-Sound is not muted
-using onboard speaker

-Results of "aplay -l"
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

-Results of "lspci -v"
PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 52000000-52ffffff
    Prefetchable memory behind bridge: 0000000051000000-0000000051ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

-find /lib/modules/`uname -r` | grep snd" returns many values

-http://www.alsa-project.org/db/?f=4fe92289d2a46396a7fdefac8a2cd554d44bb57a -- is a link that displays extensive information about my current setup, including kernel version and alsa version numbers

Im going to be at work from about 6:00pm EST till midnight today and tomorrow, so i will try and respond after i get off.
If any more information is needed than please let me know.

---

### Post by andymorton on 2011-02-25
Here's a thread from Linux Forums. Someone was having the same problem which was apparently solved. 

andy

[http://www.linuxquestions.org/questions/linux-newbie-8/sound-not-working-on-hp-mini-110-3135dx-838893/](http://www.linuxquestions.org/questions/linux-newbie-8/sound-not-working-on-hp-mini-110-3135dx-838893/)

---

### Post by autoimmune on 2011-02-26
Ok i have discovered that it is not a sound card problem but a speaker problem. Sound works with external speakers. I have found the driver that supposedly fixes the internal speakers. 

I found the info on [http://ubuntuforums.org/showthread.php?t=557031](http://ubuntuforums.org/showthread.php?t=557031),  thanks to the thread andymorton linked to me.

But i have a problem. The install directions are as follows:
Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Complied source code
    a. cd alsa-driver-1.0.xx
    b. ./configure --with-cards=hda-intel
    c. make
    d. make install

Step 3. reboot your machine

Step 4. Use the alsamixer the disable mute (All audio line default is mute)
        Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer



The following directions are verbatim from the readme.
After step one the directions appear to be gibberish.

p.s. the integrated auto installer does nothing.

---

### Post by cchhrriiss121212 on 2011-02-26
> After step one the directions appear to be gibberish.
Translated:
1. Unzip the package with a right click "extract here" option, you should get a folder
2. Right click the folder, then select "open terminal here"
3. type "./configure --with-cards=hda-intel", press enter
4. type "make", press enter
5. type "sudo make install", press enter
6. reboot
7. open terminal, type alsamixer, use arrow keys to unmute volume

Steps 3-5 may take a while so be patient.

---

### Post by Yellow Pasque on 2011-02-26
Have you tried using alsamixer without installing special drivers?

---

### Post by autoimmune on 2011-02-26
Success! 
The only problem i had was at first their was no option to open the folder in a terminal. I needed to install [B]Nautilus and use this thread [http://ubuntuforums.org/showthread.php?t=1472889](http://ubuntuforums.org/showthread.php?t=1472889) in order to be able to get the open in terminal context option.
But now i just tested youtube and sound played fine, so i have my fingers crossed that it will work
in all other instances as well

You guys have been awsome, thanks a ton.
[/B]

---

