---
title: "Intel HD audio in Hoary??"
date: 2005-03-16
forum: Hardware &amp; Laptops
---

### Post by mal on 2005-03-16
I was really hoping that Hoary would include a driver for the Intel HD audio chipset on my 915 motherboard.  However, I have justed loaded the preview release of Hoary and, sadly, still no sound!

The following line appears in lspci:

0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

Can anyone suggest how I should go about trying to get this sound system working?

In a previous thread there was some discussion about compiling the snd-azx module.  Is this what I need to do?  Or is it possible that this will be available out of the box in the final release of Hoary?

Any guidance or comments will be appreciated.

I note also that my Nvidia 6600 based video card also does not seem to be recognised, so any thoughts on this would also be valuable.

Mal

---

### Post by mal on 2005-03-18
An update:

The Intel 915 series motherboards apparently use a Realtek ALC860 chipset for on-board audio.  It seems that this is also known as an Azalia chipset and the driver required for this is snd-azx.

Apparently snd-azx is not provided with the alsa-base (1.0.8-4-ubuntu2) package in Hoary.  I understand that alsa version 1.0.8 is supposed to include this driver, so I dont' know why it does not seem to be in the Hoary package.

Based on various threads that I've read, I have attempted to compile the necessary driver from the alsa source package (alsa-source in Universe).  Using the instructions in the debian readme supplied with this package, I finally managed to complete this process using the command:

$ sudo fakeroot debian/rules binary_modules \
KSRC=/usr/src/linux-headers-2.6.10-5-686/ KVERS=2.6.10-5-686

However, I still don't have any sound!!

The file snd-azx.ko is in the /usr/src/modules/alsa-driver/azx/ directory, but the snd-azx driver is not loaded on boot -up and if I try "modprobe snd-azx", I get a "file not found" error.  I've also added snd-azx to /etc/modules with no effect.

Any advice on the next step would be greatly appreciated.

Mal

---

### Post by mumbles on 2005-07-12
I have an intel desktop board D915PGN  with the ALC860 chipset  and am having the same problems. is there a way around ?

---

### Post by dorris on 2005-07-13
Sure theres a way around it, it just requires a little skill.
the driver exists in the 2.6.12 kernel tree, just unsure whether ubuntu decided to compile it or not.
I have a laptop with intel HD audio, I got it working by downloading the 2.6.12  kernel sources from the breezy repos, 
In the make xconfig (make menuconfig)
browse down to audio devices, there will be a section for PCI, and in that list, you should find Intel HD audio.

don't forget to ensure your other drivers are available in your new kernel!
recompile, and enjoy the audio.

Good Luck

---

### Post by GrootBrak on 2005-07-13
I have the same problem. Solution: Intel and Ubuntu won't work, get something else. Sorry  for being so grumpy, but ever since I tried Ubuntu on my D915GEV I had problems. At first, I cannot get Xwindows to work, so no desktop. Then I had my desktop up, no nothing else. I am greeted by silence, bad graphics, and a zillion other things amongst others, no Internet dialup. To say I'm fed-up is an under statement.

Back to sound. I have just sat for another two odd hours tryng to install the Intell driver from Intel. Everything works as the help file say. Then I get to the bit of compiling.  The command ./build.sh install return with a "no such directory." Now what? I felt like throwing all my Linux CD's out the window... Same goes for Graphics from Intel. It won't work as explained in the guides that comes with it.

BTW. I have a Bluetooth modem, with a generic Bluetooth dongle in my USB port. Device manager show a Bluetooth dongle, but that's so pointless if you can't do zilts with it.

---

### Post by ridvan on 2005-07-16
[QUOTE=GrootBrak]I have the same problem. Solution: Intel and Ubuntu won't work[/QUOTE]

Wait, I have the same sound equipment on my Clevo D900T and I have managed to get it work. The HowTo was explaining howto recompile the alsa from ubuntu suppoerted sources and create a deb. But unfortunately I can not find this howto anymore ](*,) 

Let's carry on googling

---

### Post by ridvan on 2005-07-16
[QUOTE=ridvan]Wait, I have the same sound equipment on my Clevo D900T and I have managed to get it work. The HowTo was explaining howto recompile the alsa from ubuntu suppoerted sources and create a deb. But unfortunately I can not find this howto anymore ](*,) 

Let's carry on googling[/QUOTE]

I've got it

[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto)

---

### Post by mal on 2005-07-16
[QUOTE=GrootBrak]I have the same problem. Solution: Intel and Ubuntu won't work, get something else. Sorry  for being so grumpy, but ever since I tried Ubuntu on my D915GEV I had problems. At first, I cannot get Xwindows to work, so no desktop. Then I had my desktop up, no nothing else. I am greeted by silence, bad graphics, and a zillion other things amongst others, no Internet dialup. To say I'm fed-up is an under statement.

Back to sound. I have just sat for another two odd hours tryng to install the Intell driver from Intel. Everything works as the help file say. Then I get to the bit of compiling.  The command ./build.sh install return with a "no such directory." Now what? I felt like throwing all my Linux CD's out the window... Same goes for Graphics from Intel. It won't work as explained in the guides that comes with it.
[/QUOTE]

I have an Intel 915GAV motherboard with ALC860 sound and had a lot of problems trying to get it working.  At first, I gave up and installed an old ens1371 card from another computer and got sound working.  Obviously, the version of alsa in Hoary does not include a suitable driver for this chip set.  However, I eventually managed to get the on-board sound working by downloading and installing an updated alsa driver.  If it's any use to anyone else, I include below the procedure I used:

- make sure to load build-essential and appropriate kernel headers packages for the kernel that is running.
- download alsa-driver-1.0.9b.tar.bz2 and extract it into home directory (using "extract here" in nautilus).
- change directory to alsa-driver-1.0.9b
$ ./configure
$ make
$ sudo make install

I then needed to add "snd-hda-intel" to the end of the /etc/modules file.

After rebooting the new driver should work OK.

Note that I am running 2 sound cards, so I found that I have to put the appropriate drivers in /etc/modules in the right order to make sure that the my preferred card is associated with /dev/dsp, which some applications use by default.

Note, also that I often have to repeat this procedure when I perform an apt-get upgrade, or load a different kernel image.

I also found that the sound quality from the on-board sound is not very good.  I get a lot of background noise, so I tend to use the ens1371 as the default sound.

Hope this is of some use.

Mal

---

### Post by almostlinux on 2005-10-07
[QUOTE=ridvan]I've got it

[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto)[/QUOTE]


I've followed this 'Howto'...

```
# apt-get install alsa-source

# apt-get install linux-headers-2.6.10-5-686

# apt-get install kernel-package ## installs make-kpkg

# apt-get install ncurses-dev ## I am not sure if this is really needed

$ less /usr/share/doc/alsa-source/README.Debian

# dpkg-reconfigure alsa-source ## choose azx as driver

# apt-get install fakeroot

# cd /usr/src

# tar jxf alsa-driver.tar.bz2

# cd linux-headers-2.6.10-5-686

# make-kpkg --rootcmd=fakeroot --append-to-version=-5-686 modules-image
[B]
# dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb [/B]
```

I seem to have problem with the last line. I get this output when i execute the last line..
```


$:/usr/src/linux-headers-2.6.10-5-686 # dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb
dpkg: error processing alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb

```

I checked the directory /usr/src there was this file:

alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb

do i have to move it to the linux-headers-2.6.10-5-686 directory? :???:


edit: my motherboard is Intel 915 GAV ... HD audio (realtek chipset)

---

### Post by snaga on 2005-10-14
Does any one know if Intel HD Audio works out-of-the-box in Breezy?

dm

---

### Post by almostlinux on 2005-10-22
I certainly hope so :-? I'm still without sound on my hoary

---

### Post by ridvan on 2005-12-12
Yes it works out of the box in breezy.
But remember to turn on the volume ;)

---

