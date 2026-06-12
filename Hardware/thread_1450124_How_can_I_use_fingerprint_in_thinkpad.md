---
title: "How can I use fingerprint in thinkpad?"
date: 2010-04-08
forum: Hardware
---

### Post by fered on 2010-04-08
Hi;
how can i use fingerprint in lenovo thinkpad sl510 for authentication and etc. ?

---

### Post by tgalati4 on 2010-04-08
apt-cache search thinkfinger

sudo apt-get install thinkfinger-tools

You can use it to lock yourself out of your computer.  I don't have one on my thinkpad, but reading the forums, they are not easy to use.

Please share your experience.

---

### Post by map7 on 2010-04-09
I've setup my thinkpad fingerprint reader for sudo and gdm.  I've got a T400s so I followed the settings on [http://www.thinkwiki.org/wiki/Integrated_Fingerprint_Reader](http://www.thinkwiki.org/wiki/Integrated_Fingerprint_Reader)

If you login using the fingerprint reader you still have to type a password for your keyring (unless you have it unecrypted).

I've found it handy for sudo and the screensaver though.

You can still type the password to login, sudo or get out the screensaver so you don't run the risk of locking yourself out.

As you're setting it up though I recommend having a terminal (VT2 or something) logged in as root and having a separate password for root just incase you have to set things back to what they were.

---

### Post by fered on 2010-04-09
Thanks.

you mean than if i lock out myself i can't log in again?

---

### Post by fered on 2010-04-09
after running "*sudo tf-tool --acquire*" i saw this message:

[I]ThinkFinger 0.3 ([http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/))
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing...USB device not found.

[/I] output of "lsusb":[I]
Bus 002 Device 004: ID 17ef:4815 Lenovo
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 147e:1001 Upek
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 0a5c:217f Broadcom Corp.
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


[/I] someone says me this driver not working by sl series.

---

### Post by kannan.csea on 2010-04-21
> **tgalati4 said:**
> apt-cache search thinkfinger

sudo apt-get install thinkfinger-tools

You can use it to lock yourself out of your computer.  I don't have one on my thinkpad, but reading the forums, they are not easy to use.

Please share your experience.


hi friends, 

I got Thinkpad SL410. I followed this instructions. And that resulted in this. 

kannan@kannan-laptop:~$ apt-cache search thinkfinger
libpam-thinkfinger - PAM module for the STMicroelectronics fingerprint reader
libthinkfinger-dev - development files for libthinkfinger
libthinkfinger-doc - documentation for libthinkfinger
libthinkfinger0 - library for the STMicroelectronics fingerprint reader
thinkfinger-tools - utilities for the STMicroelectronics fingerprint reader
kannan@kannan-laptop:~$ sudo apt-get install thinkfinger-tools
[sudo] password for kannan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libthinkfinger0
The following NEW packages will be installed:
  libthinkfinger0 thinkfinger-tools
0 upgraded, 2 newly installed, 0 to remove and 279 not upgraded.
Need to get 33.2kB of archives.
After this operation, 205kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libthinkfinger0 0.3+r118-0ubuntu3 [17.0kB]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main thinkfinger-tools 0.3+r118-0ubuntu3 [16.2kB]
Fetched 33.2kB in 0s (46.8kB/s)         
Selecting previously deselected package libthinkfinger0.
(Reading database ... 101998 files and directories currently installed.)
Unpacking libthinkfinger0 (from .../libthinkfinger0_0.3+r118-0ubuntu3_i386.deb) ...
Selecting previously deselected package thinkfinger-tools.
Unpacking thinkfinger-tools (from .../thinkfinger-tools_0.3+r118-0ubuntu3_i386.deb) ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
 * Restarting Hardware abstraction layer hald                            [ OK ] 
Processing triggers for man-db ...
Setting up libthinkfinger0 (0.3+r118-0ubuntu3) ...

Setting up thinkfinger-tools (0.3+r118-0ubuntu3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kannan@kannan-laptop:~$ 

I read all this but couldn't understand anything. Is everything ok. Whether the Fingerprint reader got installed. Or is there any problem??

Sorry, I am a absolute noob.

---

### Post by trelirodia on 2010-04-22
Hi there, 

I've also had problems getting thinkfinger working on my laptop, Ideapad U550. My reader is UPEK and lsusb gives 
Bus 006 Device 002: ID 147e:1001 Upek

I tried installing the UPEK drivers, but my system is 64-bit and it wasn't working properly.

I emailed UPEK about this (thought it was worth a shot) and they were very helpful. They pointed out that I should try using fingerprintGUI and set up nvm emulation.

And guess what ... it worked!!! 
[http://www.n-view.net/Appliance/fingerprint/](http://www.n-view.net/Appliance/fingerprint/)

Good luck
M

---

### Post by K. Hendrik on 2010-04-23
> I emailed UPEK about this (thought it was worth a shot) and they were very helpful. They pointed out that I should try using fingerprintGUI and set up nvm emulation.

And guess what ... it worked!!! 

Hi, i just bought a Sony Vaio VPCS11C5E which uses the same sensor, I already setup fingerprintGUI but it doesn't recognize my sensor, is that because I didn't configure nvm emulation? and if so how do i set it up?

(It may be that sony modified the firmware to prevent non-sony-programms from accessing the sensor, I'm not sure, but they did that before)

---

### Post by trelirodia on 2010-04-24
Hi Hendrik, 

I guess you can try the nvm emulation first and if that doesn't work you can also contact the fingerprintGUI developer. 

Setting up is actually really simple (even though the BSAPI instructions read very complicated)

The default value for nvmprefix is /var/upek/

Check if this directory exists and if you have full read/write access:
$ ls -ld /var/upek/

If not, change the permissions:
$ chmod 777 /var/upek/

That did the trick for me and I also made sure that any file that was created in /var/upek/ had read/write access for everyone that uses it. 

Hope that helps :-)

---

### Post by K. Hendrik on 2010-04-29
hmmm, doesn't work for me, the directory wasn't created so I created it and did chmod 777 for it but it just doesn't work. (i guess i blame that on the sony firmware)

---

