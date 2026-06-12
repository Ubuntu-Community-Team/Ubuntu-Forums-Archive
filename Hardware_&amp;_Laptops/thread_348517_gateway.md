---
title: "gateway"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by linex on 2007-01-28
hi
i had posted this couple months back but had no replies so i'll try this again.

I have a gateway mx6454. the audio device is sigmatel audio device. the wireless card is broadcom 802.11g.
i have two problems
1) no sound
2) no wireless card detected

please note i'm a noob and need step by step help
thanks

---

### Post by huocp on 2007-01-29
I am using MX6453, the wireless card and sound card are likely same as yours.
The following guide should work same for i386 or AMD64 version ubuntu.

for wireless:
1.
The default driver 'bcm43xx' is not working for the laptop. Disable it first:
In a terminal, key in ```
sudo rmmod bcm43xx
``` to unload the driver.
edit /etc/modprobe.d/blacklist, append a line ```
blacklist bcm43xx
```. This will prevent to autoload the drive next time.

2.
You need ndiswrapper to load winXP driver. The one provided in apt source is version 1.22.
It works fine on 32bits ubuntu, but not works on 64bits ubuntu as my experience.
Recommand to build from latest ndiswrapper source.

3.
Before build ndiswrapper, make sure you installed gcc & kernel header files.
```
sudo aptitude install build-essential linux-headers-generic
```

4.
dowload latest ndiswrapper source 1.35 from sourceforge:
[http://sourceforge.net/project/showfiles.php?group_id=93482]("http://sourceforge.net/project/showfiles.php?group_id=93482")
extract it and build
```

tar xfvz ndiswrapper-1.35.tar.gz
cd ndiswrapper-1.35/
make uninstall
make
sudo make install
```
#note: the uninstall is just safely to clean up the old version may already be installed.

make sure you have a file called ```
/etc/modprobe.d/ndiswrapper
``` which contains one line
```
alias wlan0 ndiswrapper
```

5.
Download winXP driver:
[ftp://ftp.gateway.com/pub/hardware_support/drivers/win_xp/portable/BCM40100.exe]("ftp://ftp.gateway.com/pub/hardware_support/drivers/win_xp/portable/BCM40100.exe")
You probably need to extract it under windows first.
this pack contains both 32bits & 64bits drivers.

6.
Goto the directory which has the winXP driver files. Install winXP driver for linux.
```
ndiswrapper -i bcmwl5.inf
```

you may check if it succeeded:
```
ndiswrapper -l
```
If it works, you shall see somthing like:
```
bcmwl5 : driver installed
        device present
```

7.
Recommend install networkmanager
```
sudo aptitude install network-manager-gnome
```
This tool will install an applet in the planel through which you can easily switch from wired network and wireless network

Reboot.
Hope it works for you.

for audio:
The Sigmatel 9250 is too new to be supported in ALSA driver.
However, the newest alsa-driver-1.0.14rc2 has an experimental sigmatel patch which began to work for my laptop.

1.
download source code:
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2")
build and install:
```
tar xfvj alsa-driver-1.0.14rc2.tar.bz2
cd alsa-driver-1.0.14rc2/
./configure
make
sudo make install
```

2.
The rc2 driver still has problem for some Gateway laptops, you need add one line to file /etc/modprobe.d/options
```
options snd-hda-intel probe_mask=1
```

now reboot, enjoy the sound.

---

### Post by linex on 2007-01-30
working on sound right now; where do i save the alsa driver file when i download it? what directory?

---

### Post by huocp on 2007-02-01
Anywhere, better save in your home dir.
If you try audio before wireless, you do need to run this command first.

sudo aptitude install build-essential linux-headers-generic

---

### Post by zdeth on 2007-02-04
thank you so much for the solution!!! i've been trying to get audio working on my mx6454 since i got it (black friday 06)

---

### Post by linex on 2007-02-10
thanks

one last thing, whenever i start a new session my mouse doesn't work. any ideas why it's not working?

thanks

---

### Post by blk_jack on 2007-05-25
This has been tried many months ago by people using the Gateyway 34XX and it doesn't work.

To my knowledge there is NO workaround for this bug and it's up to ALSA to release a new version with the fixes before anything changes.

---

### Post by linex on 2007-06-23
> **huocp said:**
> 
for audio:
The Sigmatel 9250 is too new to be supported in ALSA driver.
However, the newest alsa-driver-1.0.14rc2 has an experimental sigmatel patch which began to work for my laptop.

1.
download source code:
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2")
build and install:
```
tar xfvj alsa-driver-1.0.14rc2.tar.bz2
cd alsa-driver-1.0.14rc2/
./configure
make
sudo make install
```

2.
The rc2 driver still has problem for some Gateway laptops, you need add one line to file /etc/modprobe.d/options
```
options snd-hda-intel probe_mask=1
```

now reboot, enjoy the sound.

hi
i'm trying diffrent distros to get to see more. i'm trying open suse and can't get the sound to work.
i downloaded the alsa drivers and the extraction worked. but when i do ./configure i get the following
> checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


why isn't it working?

thanks

---

### Post by Kleber on 2007-07-03
huocp.

I needed to set up a Gateway MX6453 laptop, because they (wireless card and sound card) were not working.
I followed your clue and the wireless card and sound card are working fine now.

Thanks so much.

Regards,
Kleber Rodrigo de Carvalho

---

### Post by pwn2king on 2008-03-19
*looking around first time on forum* 
I have Gateway M6312 with the same problem, no sound. No drivers installed, although it recocgnizes "something" as a sound device. I will try this fix see if it works, if anyone else has a M6312, let me know. I finally blew a fuse w/Victim, err Vista since it would not recognize a rinky dink flash drive. Ubuntu is great, but the learning curve is so steep i need a helicopter. Happy though, it's such an elegant OS. Thanks for the help.

---

