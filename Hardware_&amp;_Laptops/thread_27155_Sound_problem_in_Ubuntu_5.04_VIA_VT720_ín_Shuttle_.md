---
title: "Sound problem in Ubuntu 5.04: VIA VT720 ín Shuttle XPC SN25P"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by Elegantly on 2005-04-15
I have recently purchased the new [Shuttle XPC SN25P](http://global.shuttle.com/Product/Barebone/SN25P.asp) barebone PC for AMD64 CPUs (nForce4 chipset, Socket 939). The FN25 mainboard in the SN25P is equipped with an onboard sound card of type [VIA Envy24PT multi-channel audio controller (VIA VT1720/24)](http://www.via.com.tw/en/products/audio/controllers/envy24pt/), which is not yet supported in Ubuntu 5.04 "Hoary Hedgehog". The correct driver for the sound chip seems to be "ice1724", but modprobing it results in the following error message:

```
ice1724: Invalid EEPROM (size = 255)
ICE1724: probe of 0000:05:06.0 failed with error -5
```
The problem seems to be that the PCI Product/Vendor ID and/or the Subvendor PCI-ID is different from what was expected.

A number of Ubuntu users have found a way to fix the problem, which basically requires you to slightly modify the kernel source to recognize the card by changing the files /usr/src/linux/sound/pci/ice1712/vt1720_mobo.h and /usr/src/linux/sound/pci/ice1712/vt1720_mobo.c.

Links to their posts and articles:
[cat mind >> ff02::1: Shuttle SN25P Sound](http://www.nakack.net/?p=19) - good description about the problem and how to fix it
[cat mind >> ff02::1: SN25P sound patch](http://www.nakack.net/?p=20) - patch file
[Loren Bandiera’s weblog: SN25P / ice1724](http://people.mmgsecurity.com/~lorenb/?p=349) - another description about the problem and how to fix it
[Google Groups: Sound Chip IC Ensemble Inc ICE1724 [Envy24HT]](http://groups-beta.google.com/group/comp.os.linux.hardware/browse_frm/thread/249c69cf4862e7ec/57fb7498f509ec60?tvc=1#57fb7498f509ec60) - how to fix the PCI product/vendor ID for the vt1720 sound chip

I hope that my post in this forum will help to speed up the process to get the required fix for the problem into the Linux Kernel and, of course, Ubuntu. Not everyone likes to download kernel sources and compile a custom kernel when the only problem is just a missing ID entry to correctly recognize a chip (and more important: to do it everytime a kernel update is released).  :) 

The Shuttle SN25P is a really nice PC for the AMD64 architecture, and IMHO at least the sound chip should work out of the box with Ubuntu, eh?  :-P

---

### Post by Elegantly on 2005-04-15
Follow up: I have also filed a [bug report (#9734)](https://bugzilla.ubuntu.com/show_bug.cgi?id=9734) for the VT1720/24 sound chip and added an entry to the section about [sound cards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsSoundCards) on the Ubuntu wiki.

Hope this helps.

---

### Post by Z3K3 on 2005-04-29
I'm working on the patch for the 2.6.12 kernel.  I do not have the same mobo, but will compile a kernel if you are able to test it that would be great.

-- Chris

---

### Post by Abukaspar on 2005-04-30
Great! I have the same hardware since a few weeks, and I was also disappointed about that sound issue. I'll try to recompile the module following the information you kindly provided, and I'll keep you informed whether I succeed or not. (Note that I still run warty, but I plan to upgrade to hoary in the next few weeks).  I am also willing to test the patched 2.6.12 kernel.
Cheers
François

---

### Post by Elegantly on 2005-04-30
[QUOTE=Z3K3]I'm working on the patch for the 2.6.12 kernel.  I do not have the same mobo, but will compile a kernel if you are able to test it that would be great.

-- Chris[/QUOTE]
Unfortunately, I had to replace Ubuntu with SuSE. I am still available for testing though if possible. :)

---

### Post by Zapf on 2005-05-08
hi, im trying to set this up with my current hoary install (2.6.10), and i am coming across some difficulties. i apt-getted my kernel source and made the change in the header file as indicated in the "cat mind >> ff02::1" blog. it then said to compile the module. unsure of how to do that, i checked the google groups page. they said to do " make modules_install". i did that, and i got this

```

zapf@Bluebox:/usr/src/linux$ sudo  make modules_install
Makefile:484: .config: No such file or directory

The present kernel configuration has modules disabled.
Type 'make config' and enable loadable module support.
Then build a kernel with module support enabled.

make: *** [modules_install] Error 1

```

i then did a sudo make config, and i started being presented with a whole hell of a lot of questions that i really didnt know the answer for. i read make menuconfig would present them in cleaner manner, but i still would have no idea what to have on and off. could someone assist me?

---

### Post by Elegantly on 2005-05-09
[QUOTE=Zapf]hi, im trying to set this up with my current hoary install (2.6.10), and i am coming across some difficulties. i apt-getted my kernel source and made the change in the header file as indicated in the "cat mind >> ff02::1" blog. it then said to compile the module. unsure of how to do that, i checked the google groups page. they said to do " make modules_install". i did that, and i got this

```

zapf@Bluebox:/usr/src/linux$ sudo  make modules_install
Makefile:484: .config: No such file or directory

The present kernel configuration has modules disabled.
Type 'make config' and enable loadable module support.
Then build a kernel with module support enabled.

make: *** [modules_install] Error 1

```

i then did a sudo make config, and i started being presented with a whole hell of a lot of questions that i really didnt know the answer for. i read make menuconfig would present them in cleaner manner, but i still would have no idea what to have on and off. could someone assist me?[/QUOTE]

IIRC, I had the same problem with my SuSE installation. The problem was not the missing loadable module support though, but the fact that the kernel configuration file .config did not exist. I was able to get my current kernel configuration of the pre-built SuSE kernel via

```
$ zcat /proc/config.gz > .config
```

After that, I did a "make modules" and "make modules_install" to compile and install the updated modules.

---

### Post by Abukaspar on 2005-05-09
In Ubuntu the config file for your kernel(s) is in /boot :
```
sudo cp /boot/config-<version> /usr/src/linux-source-<version>/.config

```
After firing **make modules** just overwrite the modules you have patched with the newly compiled versions. In our case: 
```
sudo cp sound/pci/ice1712/*.ko /lib/modules/<version>/kernel/sound/pci/ice1712/

```

NB: In general, to recompile the kernel and/or modules in Ubuntu, it is generally advisable to use the Debian method: 
```
apt-get install kernel-package
cd /usr/src/linux-source-<version>
cp /boot/config-<version> .config
make menuconfig
make-kpkg --initrd kernel_image
```
(The option --initrd is necessary in Ubuntu, otherwise your kernel won't boot at all).

This will produce a *.deb file in the /usr/src directory, which you can then install with ```
dpkg -i kernel-image-<version>-<...>-<arch>.deb
```

See also the documentation in /usr/share/doc/kernel-package/

---

### Post by Abukaspar on 2005-06-04
This is a follow-up to my previous post. I have now upgraded to hoary (compliments to the ubuntu team! ;-) ) and my first task was to try to compile a patched 2.6.11 kernel so that the sound card on my Shuttle SN25P is recognized. That was my first adventure in this territory, and it was not totally pain-free (euphemism). But at the end I did succeed and I certainly learned a lot about the kernel, ALSA and other things. 

I have to warn everyone however **not to touch kernel 2.6.11 for the moment** (in universe under the name *linux-source-2.6.11*). It contains severa bugs!!! (I won't list them here, but basically they have to do with inotify and devpts). Use instead the latest 2.6.10 kernel supported in hoary (currently 2.6.10-5).

The way to have sound with hoary on the Shuttle SN25P is as follows:

[COLOR=Blue][[ OPTIONAL: apt-get install linux-image-2.6.10-5-686, then reboot in that kernel. 
Note that I still run my system in 32 bits. If you have Ubuntu for AMD64 then modify the following instructions accordingly.

Beware that if you install a new kernel you might have to recompile the nvidia driver first! For that you need to 
apt-get install nvidia-kernel-source 
and read the instructions in /usr/share/doc/nvidia-kernel-source/README.Debian . You should also run "depmod" to update the files in /lib/modules/<VERSION> (see man depmod for details), because /sbin/update-modules, which is called after installation, is spurious in Ubuntu. ]]
[/COLOR]
In case you don't have the headers:
**apt-get install linux-headers-2.6.10-5-686** (or -383 if you kept Hoary's default kernel).

Download recent sources of alsa-driver from [http://www.alsa-project.org/download.php](http://www.alsa-project.org/download.php). 
You can choose a mirror near you. In my case I did: 
wget [ftp://gd.tuwien.ac.at/opsys/linux/alsa/driver/alsa-driver-1.0.9rc4a.tar.bz2](ftp://gd.tuwien.ac.at/opsys/linux/alsa/driver/alsa-driver-1.0.9rc4a.tar.bz2)
(Alternatively you can also apt-get the package alsa-source in universe).

Then unpack it under /usr/src :
[B]
sudo mv alsa-driver-1.0.9rc4a.tar.bz2 /usr/src/
cd /usr/src
sudo tar -xvjf alsa-driver-1.0.9rc4a.tar.bz2
cd alsa-driver-1.0.9rc4a/alsa-kernel/pci/ice1712[/B]

modify the two files vt1720_mobo.c and vt1720_mobo.h following the instructions posted [here](http://www.nakack.net/?p=19) or [here](http://people.mmgsecurity.com/~lorenb/?p=349).
Then
[B]cd ../../..
sudo ./configure --with-cards=ice1724 --with-sequencer=yes
sudo make
sudo make install[/B]

Reboot your system and there you go!

Enjoy !

François 

&#1575;&#1604;&#1605;&#1593;&#1585;&#1608;&#1601; &#1576;&#1571;&#1576;&#1610; &#1603;&#1575;&#1587;&#1662;&#1575;&#1585;

---

### Post by Zapf on 2005-06-15
bagh, it was workin fine after that reply i got, but i just booted back in (i use window primarily) and the sound doesnt seem to be working anymore?!

any ideas, or better ways to check what is wrong?

---

### Post by roguetoad on 2005-10-24
Any idea how to patch it so that the spdif (digital out) will work on the SN25p? It's great that the sound now works; it would be even better if you could do digital (less wiring) and allow for passthru as well.

---

### Post by mckirkus on 2005-10-24
I have the same Motherboard/case combo and have sound working well with Breezy Badger.  The only problem was that the EasyUbuntu patches killed sound so I had to re-install.  

I know that this is a 5.04 forum but thought you might want to know that they fixed the problem in 5.10.

Here's a photo in case yours is different...
[IMG]http://static.flickr.com/32/43689352_4d39ca0636.jpg[/IMG]

---

### Post by tibrisch on 2006-05-30
Hi!
Ive recently become a huge fan of Ubuntu and im now running Dapper Drake...
However i have embeded Via VT1720 Envy24 chipset on my motherboard.

Can't this problem be fixed in an easier way?
It just feels wrong for me as a newbe to change sourcecode lines and then compile in order to make the module work. 

Thanks to all ppl that develop and share your great work!
/Tibrisch

---

### Post by Elegantly on 2006-05-31
[QUOTE=tibrisch]Hi!
Ive recently become a huge fan of Ubuntu and im now running Dapper Drake...
However i have embeded Via VT1720 Envy24 chipset on my motherboard.

Can't this problem be fixed in an easier way?
It just feels wrong for me as a newbe to change sourcecode lines and then compile in order to make the module work. 

Thanks to all ppl that develop and share your great work!
/Tibrisch[/QUOTE]
IIRC, chipset is supported in Ubuntu Dapper Drake 6.06, which will be released tomorrow (June 1st). I have already installed the Dapper Drake Beta on my Shuttle XPC, but I cannot remember whether the sound was recognized or not (I was in a hurry). :-k

---

### Post by Typhoe on 2007-02-18
> **roguetoad said:**
> Any idea how to patch it so that the spdif (digital out) will work on the SN25p? It's great that the sound now works; it would be even better if you could do digital (less wiring) and allow for passthru as well.

Hi,

I just installed Ubuntu Feisty (Herd 4) on my Shuttle SN25P... Is there any progress about having the spdif (digital out) working ?

Regards,
Typhoe

---

### Post by Rizlaw on 2007-02-25
> **roguetoad said:**
> Any idea how to patch it so that the spdif (digital out) will work on the SN25p? It's great that the sound now works; it would be even better if you could do digital (less wiring) and allow for passthru as well.

As my first post on this forum, I, too, would like to know when spdif out (coax and Toslink) on the Shuttle SN25P will be implemented/fixed.:(

---

### Post by bergoo on 2007-03-26
I have maybe found a way of getting the spdif out working with the integrated soundchip for my Shuffle SN25P. I have not time for some days to check if it is working but check this post at the Gentoo forum and see if it helps. 

[http://forums.gentoo.org/viewtopic-t-395086-highlight-vt1720.html](http://forums.gentoo.org/viewtopic-t-395086-highlight-vt1720.html)

I will reply when I have tested this.

Regards
Mathias

---

