---
title: "I can't set up my broadcom wireless in HP dv6000"
date: 2008-08-20
forum: Hardware
---

### Post by samathyr on 2008-08-20
Hi everyone!

I am quite new with Ubuntu, and after a summer using it I think it's great but I have a very big problem. Now I am starting the university year and I really need wireless in my laptop. I have been looking to so many posts in everywhere about this, doing step by step what they show and I have never get this working. This situation is pretty bad for me.

I have a HP Pavilion dv6000 laptop with AMD64 Turion.  

The one which looks better is this:
[http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/)

But still, I don't get anything and here is no error poping up, just the wireless light is always red. I am really desperate and I feel I have tried every single solution available throught google and forums like this one. Can you help me?

In other case... I really need this working, if not, Someone knows some technician or some computer shop in OSLO (Norway) where I can go and set this up by paying?

---

### Post by shak541 on 2008-08-20
that guide will probably not work for you.. I have an hp dv6622CA and well.. i have flawless wireless. use this guide and tell me if it works for you:
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

---

### Post by sergiom99 on 2008-08-20
which is your laptop exact model? and the wifi card?
please post the output of the command 'lspci'.

I set it up without any problems (twice) following this howto:
[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

it works great with my BCM4328

---

### Post by Coward on 2008-08-20
This is what I used.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by LateNiteTV on 2008-08-20
what is it.. i think the broadcom9430 or something... no support that i know of. wifi support under any *nix is pretty crappy right now. on my freebsd ive had to use ndiswrapper to make wireless work. maybe theres something like that for linux...? google is your friend.

---

### Post by sergiom99 on 2008-08-20
well, to help you in an efficient way, we first need to know which card do you have. lspci output will tell us that.

I got mine working perfectly with the basic howto I posted.
Good luck!

---

### Post by samathyr on 2008-08-20
Sorry, here is the detailed information


00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev
 a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra                                                                                                   nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address                                                                                                    Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con                                                                                                   troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella                                                                                                   neous Control
**03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev                                                                                                    01)**
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapte                                                                                                   r (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (re                                                                                                   v 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
luis@ubuntu:~$

Thanks!

---

### Post by sergiom99 on 2008-08-20
Hola Luis,
yes its the same card that Dark_stang has, so everything you need is in his tutorial:
[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

Let us know how it works.
saludos-

---

### Post by samathyr on 2008-08-20
I tried with your way, sergio, and stills...
```

root@ubuntu:/home/luis# dir
b43-fwcutter-011		 Desktop		tmpha0Mo9.wav
b43-fwcutter-011.tar.bz2	 Documents		tmpHjoNxa.wav
b43-fwcutter-011.tar.bz2.1	 Firefox_wallpaper.png	tmpHrbgBW.wav
b43-fwcutter-011.tar.bz2.2	 gretl			tmpIHzUGa.wav
b43-fwcutter-011.tar.bz2.3	 Incoming\ Files	tmpmx6wae.wav
Baskets_2008-07-31.tar.gz	 LimeWire		tmpPPM7ty.wav
BBA2Y				 Music			tmppTNqmp.wav
broadcom-wl-4.80.53.0		 myfile.syn~		tmpUN1eDO.wav
broadcom-wl-4.80.53.0.tar.bz2	 Pictures		Videos
broadcom-wl-4.80.53.0.tar.bz2.1  Programs		wifi
broadcom-wl-4.80.53.0.tar.bz2.2  tmp6C8GUq.wav		Workout\ preparation
checkgmail			 tmp_BDQ6Y.wav		Workout\ preparation~
cxoffice			 tmpCCD__Q.wav
root@ubuntu:/home/luis# cd wifi
root@ubuntu:/home/luis/wifi# dir
bcm1xsup.dll   bcmwl5.sys    bcmwls.ini    is.exe	 setup.iss
bcm43xx64.cat  bcmwliss.dll  bcmwlu00.exe  launcher.ini  sp34152.cva
bcm43xx.cat    bcmwlnpf.sys  data1.cab	   layout.bin
Bcmnpf64.sys   bcmwlpkt.dll  data1.hdr	   setup.exe
bcmwl564.sys   bcmwls32.exe  data2.cab	   Setup.ini
bcmwl5.inf     bcmwls64.exe  ikernel.ex_   setup.inx
root@ubuntu:/home/luis/wifi# sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
root@ubuntu:/home/luis/wifi# sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

root@ubuntu:/home/luis/wifi# sudo gedit /etc/modprobe.d/blacklist
root@ubuntu:/home/luis/wifi# sudo gedit /etc/modules

```

The only strange thing is "module configuration already contains alias directive". Be aware that I am telling you the truth when I say I have tested every single method. My Blacklist and Startup text files had "ndiswrapper" already. I am so desperate... Seriously, If I am not fixing this before the next week I will hire a technician. I have been 2 months struggling with this.

---

### Post by sergiom99 on 2008-08-20
well, i dont have my laptop now, so I cannot check things.
Before paying for it (and probably the tech-guy will just follow up a how-to in the forums) you might try to make a clean install and start from scratch, just following the tuto I told you.
First time I tried lots of things and couldn't remember every single file I touched. so i installed again and got things working.
I only reinstalled again when upgrade to HH f**ed some things up. And again, this tuto helped me a lot. (Thanks Dark_stang for it!)

---

### Post by shak541 on 2008-08-20
follow my post... i have the same wifi card!!! see my post above. it will take about 5 min top for your first time.. :D its easy as can be. :D

---

### Post by Ayuthia on 2008-08-20
> **samathyr said:**
> I tried with your way, sergio, and stills...
```

root@ubuntu:/home/luis# dir
b43-fwcutter-011		 Desktop		tmpha0Mo9.wav
b43-fwcutter-011.tar.bz2	 Documents		tmpHjoNxa.wav
b43-fwcutter-011.tar.bz2.1	 Firefox_wallpaper.png	tmpHrbgBW.wav
b43-fwcutter-011.tar.bz2.2	 gretl			tmpIHzUGa.wav
b43-fwcutter-011.tar.bz2.3	 Incoming\ Files	tmpmx6wae.wav
Baskets_2008-07-31.tar.gz	 LimeWire		tmpPPM7ty.wav
BBA2Y				 Music			tmppTNqmp.wav
broadcom-wl-4.80.53.0		 myfile.syn~		tmpUN1eDO.wav
broadcom-wl-4.80.53.0.tar.bz2	 Pictures		Videos
broadcom-wl-4.80.53.0.tar.bz2.1  Programs		wifi
broadcom-wl-4.80.53.0.tar.bz2.2  tmp6C8GUq.wav		Workout\ preparation
checkgmail			 tmp_BDQ6Y.wav		Workout\ preparation~
cxoffice			 tmpCCD__Q.wav
root@ubuntu:/home/luis# cd wifi
root@ubuntu:/home/luis/wifi# dir
bcm1xsup.dll   bcmwl5.sys    bcmwls.ini    is.exe	 setup.iss
bcm43xx64.cat  bcmwliss.dll  bcmwlu00.exe  launcher.ini  sp34152.cva
bcm43xx.cat    bcmwlnpf.sys  data1.cab	   layout.bin
Bcmnpf64.sys   bcmwlpkt.dll  data1.hdr	   setup.exe
bcmwl564.sys   bcmwls32.exe  data2.cab	   Setup.ini
bcmwl5.inf     bcmwls64.exe  ikernel.ex_   setup.inx
root@ubuntu:/home/luis/wifi# sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
root@ubuntu:/home/luis/wifi# sudo ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

root@ubuntu:/home/luis/wifi# sudo gedit /etc/modprobe.d/blacklist
root@ubuntu:/home/luis/wifi# sudo gedit /etc/modules

```

The only strange thing is "module configuration already contains alias directive". Be aware that I am telling you the truth when I say I have tested every single method. My Blacklist and Startup text files had "ndiswrapper" already. I am so desperate... Seriously, If I am not fixing this before the next week I will hire a technician. I have been 2 months struggling with this.
Here are some commands to try and see if your wireless card will turn on.  They will only work for the current session:
b43:
```
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl bcm43xx
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
After you do the ifconfig wlan0 up, the blue light should come on (it looks like you have installed the firmware for it).  The last command should produce a list of wireless sites in your laptop's range.

NDISwrapper:
```
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan
```
This should get your wireless up and running using the ndiswrapper driver.

If one of these options do work, let us know which one and please post the results of the following:
```
cat /etc/modprobe.d/blacklist|grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
cat /etc/modules|grep  -i -e b43 -e ssb -e bcm43xx -e ndiswrapper -e wl
cat /etc/modprobe.d/ndiswrapper|grep install
```
These commands will help us see what you have done to the module configuration files.

For ndiswrapper, some guides have you create a script.  Did you do that?  If so, we might need to modify it.  If you can attach that script, it would also be helpful.

Just in case you did not know, these commands need to be done in the Terminal.

If you are still unable to get your wireless going, please supply the results of the following from the Terminal:
```
lshw -C network
ls /lib/firmware
ndiswrapper -v
ndiswrapper -l
```
These commands will help us see what modules are being used, if the firmware has been installed, what version of ndiswrapper you are using, and if the device is present for ndiswrapper.

I also have a dv6000 series laptop with the 4311 rev 01 card.  I have been able to get the bcm43xx, b43, ndiswrapper, and wl drivers to work with this card so I am pretty sure that we should be able to get yours up and running soon.  Broadcom cards are sometimes hard to figure outthe first time around.

---

### Post by Ayuthia on 2008-08-20
> **shak541 said:**
> that guide will probably not work for you.. I have an hp dv6622CA and well.. i have flawless wireless. use this guide and tell me if it works for you:
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

I just went to shak541's link and found that it is for Gutsy and not Hardy.  This guide will most likely not work because it does not deal with the b43 and ssb module that is introduced in the Hardy kernel (2.6.24).  Also ndiswrapper 1.49 does not compile in Hardy.  You need to use a version that is 1.50 or higher.

---

### Post by shak541 on 2008-08-20
ohh ok... sorry about that guys. :(

---

### Post by samathyr on 2008-08-26
OHHHH MY GOD!! OHHHHH I CANNOT BELIEVE IT!!! OHHHH YESSSS!!!

I have been some days without any kind of internet and OH MY GOD!!! Sounds bad but this was becoming a major problem for my daily life.

This days I have been looking for USB Wireless in some retail stores like Expert or Elkjøp here in Norway (other dissapointment thing was the fact that I am from Spain and the cost of IT stuff here is almost double!!), almost bought one, but I decided to review this and

IT WORKED!!

Now I have the perfect laptop! I am so happy :D

What I did was what Ayuthia said about b43:
```

sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl bcm43xx
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

The first impression was pretty bad:
```
luis@ubuntu:~$ sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl bcm43xx
[sudo] password for luis:
FATAL: Module wl not found.

```

but after try with the following one:
```
luis@ubuntu:~$ sudo modprobe b43
```

I saw the blue light!!!!

```
luis@ubuntu:~$ sudo ifconfig wlan0 up
luis@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6A:16:CE:70
                    ESSID:"nsm_student"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=83/100  Signal level=-47 dBm  Noise level=-66 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000002e461d52da9
          Cell 02 - Address: 00:14:6A:16:DC:D3
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/100  Signal leve

```

A long list of connections (I am at the university right now)
And then I used the Network Manager (besides the clock) to connect to the University's Network, and I am posting from THERE!!!!!!!! THANKS !!!

I am going to celebrate this! Some special dinner tonight!
[SIZE="7"]**Thank you all, and specially Ayuthia and sergiom99!**[/SIZE]

---

### Post by sergiom99 on 2008-08-26
glad you make it luis!
it was not that hard, and never worth to pay for it in the first place.

bookmark the links we gave you for future reference and if you need to re-install Ubuntu, just follow them and you're done.

Felicitaciones y bienvenido!

---

