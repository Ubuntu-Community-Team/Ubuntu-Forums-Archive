---
title: "[SOLVED] Clone Winchiphead USB/Serial cable (1a86:7523). Help needed with Makefile."
date: 2008-09-16
forum: Hardware
---

### Post by alanmilne on 2008-09-16
I have recently purchased a cheap USB/Serial cable from a supplier on eBay and would like some help getting it recognised by Ubuntu. The cable has no markings but is silver with a turquoise plug at either end.

I have done quite a lot of investigation through this forum ( and other sources ) but am having a problem when it comes to recompiling a driver.

It might be best to start at the beginning:

When the cable is inserted lsusb gives:

```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID [COLOR="Red"]1a86:7523[/COLOR]  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 047d:101f Kensington PocketMouse Pro
Bus 001 Device 001: ID 0000:0000
```

and dmesg gives:

```
[ 9632.271712] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 9632.675793] usb 2-2: generic converter now attached to ttyUSB0
```

you can see that I have followed various threads and got the device attached to /dev/ttyUSB0.

If I use Minicom and attach the cable to my own build PIC programmer, I can talk to it!!:) However, it would appear that the default speed is 19.2kbps (the same as my PIC programmer) and devices working at other speeds [COLOR="Red"]cannot[/COLOR] be seen.

By scouring the USB vendor and product ID lists I have discovered that this device is a clone of the Winchiphead USB/Serial cable and behaves as an HL-340, although the vendor is "unknown". With this in mind I went back to the internet and discovered that the driver required was for a CH341 so I downloaded the drivers to make this work with 'Windows' :( and, after much head scratching, finally got the cable to work in this "environment". But I want it to work with Ubuntu!! :confused:

Searching the internet again I came across:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/235459]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/235459")

where Jonathan Ernst has had a similar problem. I also came across:

[http://ubuntuforums.org/showpost.php?p=4390820&postcount=27]("http://ubuntuforums.org/showpost.php?p=4390820&postcount=27")

where cdcase describes how to compile the CH341 driver.

Using this information I downloaded [COLOR="Red"]ch341.tar.gz[/COLOR] and extracted it. I then edited the [COLOR="Red"]usb_device_id[/COLOR] structure within ch341.c thus:

```
static struct usb_device_id id_table [] = {
		{ USB_DEVICE(0x4348, 0x5523) },
[COLOR="Red"]+      		{ USB_DEVICE(0x1a86, 0x7523) },[/COLOR]
		{ },
	};
MODULE_DEVICE_TABLE(usb, id_table);
```

All seems well so far, but now for the problem!! When I run the makefile I get:

```
~/Desktop/CH341$ make
make -C /lib/modules/2.6.24-19-386/build SUBDIRS=/home/alan/Desktop/CH341 modules
make: *** /lib/modules/2.6.24-19-386/build: No such file or directory. Stop.
make: *** [default] Error 2
```

It would appear that the directory /build is not there. I am afraid that I am not very knowledgeable about makefiles (all my PIC c programming is done in an IDE that produces them for me).

So, eventually, here are the questions:

1. Should the makefile be edited to point to a different directory?
 
2. Is there another way to make Ubuntu recognise that device 1a86:7523 should use the CH341 driver?

Please note that I have been using Ubuntu (any form of Linux or Unix) for about three weeks so have little knowledge of its internals. Any help would be greatly appreciated.

---

### Post by alanmilne on 2008-09-16
**Bump**

---

### Post by alanmilne on 2008-09-17
How come there's never a guru around when you need one? :)

---

### Post by alanmilne on 2008-09-19
Bump

---

### Post by IntuitiveNipple on 2008-09-19
I've hopefully made this easy for you. I've created a DKMS (Dynamic Kernel Module Support) package containing the ch341 driver patched to include the device ID 1a86:7523.

DKMS ensures that if the kernel is updated the module will be automatically rebuilt without user intervention to match the new kernel ABI (Application Binary Interface).

The package is ch341-dkms. To install it add [my Ubuntu PPA (Personal Package Archive)](https://launchpad.net/~intuitivenipple/+archive) to apt's source list:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo apt-get update

```
and install the package:
```

sudo apt-get install ch341-dkms

```
Now remove my PPA (since you won't want to accidentally upgrade other packages I maintain there):
```

sudo rm /etc/apt/sources.list.d/intuitivenipple.list
sudo apt-get update

```
To check the supported device IDs:
```

modinfo ch341

filename:       /lib/modules/2.6.24-21-generic/updates/dkms/ch341.ko
license:        GPL
srcversion:     114760D4AECC70A16DA83DF
alias:          usb:v1A86p7523d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4348p5523d*dc*dsc*dp*ic*isc*ip*
depends:        usbserial,usbcore
vermagic:       2.6.24-21-generic SMP mod_unload 
parm:           debug:Debug enabled or not (bool)

```
You'll notice the **alias v1A86p7523** which in more human-readable form is Vendor 0x1A86 Product 0x7523.

---

### Post by alanmilne on 2008-09-20
> **IntuitiveNipple said:**
> I've hopefully made this easy for you. I've created a DKMS (Dynamic Kernel Module Support) package containing the ch341 driver patched to include the device ID 1a86:7523. etc...

Many, many thanks for this - I was wondering if a 'Knight on a Shining White Horse' would appear :-).

I have tried this, but appear to not to get any changes. Having followed your instructions to the letter (this cut and paste thing is very useful), I noticed the following:
```
alan@lilputa:~$ sudo apt-get install ch341-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-pexpect libgksu1.2-1 libxine1-x g++-4.2 libxine1-misc-plugins
  libxcb-xv0 libxine1-bin g++ dar libdar64-4 libxine1-ffmpeg libxcb-shape0
  libtimedate-perl dpkg-dev libstdc++6-4.2-dev libxine1-plugins libxvmc1
  pmount libmodplug0c2 libxcb-shm0 libxine1-console
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dkms
Recommended packages:
  fakeroot
The following NEW packages will be installed
  ch341-dkms dkms
0 upgraded, 2 newly installed, 0 to remove and 23 not upgraded.
Need to get 61.3kB of archives.
After this operation, 451kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  dkms ch341-dkms
Install these packages without verification [y/N]? y
Get: 1 http://ppa.launchpad.net hardy/main dkms 2.0.20.3-0ubuntu1~ppa1h [55.2kB]
Get: 2 http://ppa.launchpad.net hardy/main ch341-dkms 1.1-0ubuntu1~ppa2h [6062B]
Fetched 61.3kB in 0s (139kB/s)   
Selecting previously deselected package dkms.
(Reading database ... 111625 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.0.20.3-0ubuntu1~ppa1h_all.deb) ...
Selecting previously deselected package ch341-dkms.
Unpacking ch341-dkms (from .../ch341-dkms_1.1-0ubuntu1~ppa2h_all.deb) ...
Setting up dkms (2.0.20.3-0ubuntu1~ppa1h) ...
Setting up ch341-dkms (1.1-0ubuntu1~ppa2h) ...
Loading new ch341-1.1 DKMS files...

Creating symlink /var/lib/dkms/ch341/1.1/source ->
                 /usr/src/ch341-1.1

DKMS: add Completed.
[COLOR="Red"]Installing prebuilt kernel module binaries (if any)

Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.[/COLOR]

```

The last three lines (coloured in red) worry me slightly.

When I try to check the module I still get:

```
alan@lilputa:~$ modinfo ch341
filename:       /lib/modules/2.6.24-19-386/kernel/drivers/usb/serial/ch341.ko
license:        GPL
srcversion:     823CB9B1C5041DE4C83B53B
alias:          usb:v4348p5523d*dc*dsc*dp*ic*isc*ip*
depends:        usbserial,usbcore
vermagic:       2.6.24-19-386 mod_unload 486 
parm:           debug:Debug enabled or not (bool)

```

This tends to indicate that I still have the *old* Ch341 driver in place. Am I missing a trick here? Is there something I need to have installed first to make this work? As I have already said, please be aware that my knowledge of Linux internals is very scant.

---

### Post by IntuitiveNipple on 2008-09-20
> **alanmilne said:**
> 
```

DKMS: add Completed.
[COLOR="Red"]Installing prebuilt kernel module binaries (if any)

Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.[/COLOR]

```

The last three lines (coloured in red) worry me slightly.
This tends to indicate that I still have the *old* Ch341 driver in place. Am I missing a trick here? Is there something I need to have installed first to make this work? As I have already said, please be aware that my knowledge of Linux internals is very scant.
No you haven't missed anything, but I am slightly surprised! This also explains why your attempts to build the module manually failed.

For a kernel module to build on its own it requires, at a minimum, the header files (include files with declarations, etc.). These are supposed to be installed as part of the standard install. The dkms package depends on them and it has installed. Maybe they've been uninstalled at some point.

Let's check what is installed. Here's the command with example output from a system with Hardy and recent updates installed:
```

dpkg-query -W -f='${Package;-35}\t${Version;-15}\t${Status}\n' 'linux-headers*'

linux-headers                      	               	unknown ok not-installed
linux-headers-2.6                  	               	unknown ok not-installed
linux-headers-2.6.24-16            	               	purge ok not-installed
linux-headers-2.6.24-16-generic    	               	purge ok not-installed
linux-headers-2.6.24-19            	2.6.24-19.41   	install ok installed
linux-headers-2.6.24-19-generic    	2.6.24-19.41   	install ok installed
linux-headers-2.6.24-20            	2.6.24-20.38   	install ok installed
linux-headers-2.6.24-20-generic    	2.6.24-20.38   	install ok installed
linux-headers-2.6.24-21            	2.6.24-21.42   	install ok installed
linux-headers-2.6.24-21-generic    	2.6.24-21.42   	install ok installed
linux-headers-generic              	2.6.24.21.23   	install ok installed

```
Doing some exploration it seems even Ubuntu's package-management server doesn't know about these *meta* packages. I need to dig further.

For now, try installing the headers matching the running kernel as a stop-gap to get you going:
```

uname -r

sudo apt-get install linux-headers-$(uname -r)

```
If that is successful try re-building ch341-dkms:
```

sudo dkms install -m ch341 -v 1.1

```
If that gets confused, start again from the beginning by removing the package entirely and starting again with my original instructions (adding my PPA first):
```

sudo dpkg -r ch341-dkms

```

---

### Post by alanmilne on 2008-09-20
Once again, many thanks. I don't know what has happened here, but this is the terminal output from getting these headers.....


```
alan@lilputa:~$ dpkg-query -W -f='${Package;-35}\t${Version;-15}\t${Status}\n' 'linux-headers*'
linux-headers                      	               	unknown ok not-installed
linux-headers-2.6                  	               	unknown ok not-installed
linux-headers-2.6.24-16            	               	purge ok not-installed
linux-headers-2.6.24-16-generic    	               	purge ok not-installed
linux-headers-2.6.24-19            	2.6.24-19.41   	install ok installed
linux-headers-2.6.24-19-generic    	2.6.24-19.41   	install ok installed
linux-headers-generic              	2.6.24.19.21   	install ok installed

alan@lilputa:~$ uname -r
2.6.24-19-386

alan@lilputa:~$ sudo apt-get install linux-headers-$(uname -r)
[sudo] password for alan: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  linux-headers-2.6.24-19-386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 642kB of archives.
After this operation, 7418kB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com hardy-updates/main linux-headers-2.6.24-19-386 2.6.24-19.41 [642kB]
Fetched 642kB in 1s (540kB/s)                       
Selecting previously deselected package linux-headers-2.6.24-19-386.
(Reading database ... 110555 files and directories currently installed.)
Unpacking linux-headers-2.6.24-19-386 (from .../linux-headers-2.6.24-19-386_2.6.24-19.41_i386.deb) ...
Setting up linux-headers-2.6.24-19-386 (2.6.24-19.41) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.24-19-386                                                           
 *  ch341 (1.1)...                                                                                                           ch341 (1.1): Installing module.
...........
............
                                                                                                                      [ OK ]

alan@lilputa:~$ modinfo ch341
filename:       /lib/modules/2.6.24-19-386/updates/dkms/ch341.ko
license:        GPL
srcversion:     114760D4AECC70A16DA83DF
alias:          usb:v1A86p7523d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4348p5523d*dc*dsc*dp*ic*isc*ip*
depends:        usbserial,usbcore
vermagic:       2.6.24-19-386 mod_unload 486 
parm:           debug:Debug enabled or not (bool)

```

It would appear that the package built itself once the headers were installed. Now all I have to do is try the cable and see what happens:)!!

Am I correct in my assumption that Linux Headers are similar to the <*.h> files used in c programming, and link the calls required into the kernel?

---

### Post by alanmilne on 2008-09-20
Thought you might like to see this as well:

```
alan@lilputa:~$ dmesg | grep USB
[   19.425593] USB Universal Host Controller Interface driver v3.0
[   19.426325] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   19.426666] hub 1-0:1.0: USB hub found
[   19.530867] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   19.531171] hub 2-0:1.0: USB hub found
[   19.634854] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   19.635158] hub 3-0:1.0: USB hub found
[   19.770168] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   21.505887] input,hidraw0: USB HID v1.10 Mouse [Kensington Kensington PocketMouse Pro] on usb-0000:00:1d.0-1
[   21.505937] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   45.508240] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   45.508272] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[13554.827881] usb 2-2: new full speed USB device using uhci_hcd and address 2
[13555.141060] usb 2-2: generic converter now attached to ttyUSB0
[13555.194224] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for ch341-uart
[13622.565435] usb 2-2: USB disconnect, address 2
[13622.566130] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[13642.447989] usb 2-2: new full speed USB device using uhci_hcd and address 3
[13642.685296] [COLOR="Red"]usb 2-2: ch341-uart converter now attached to ttyUSB0[/COLOR]

```

---

### Post by IntuitiveNipple on 2008-09-20
> **alanmilne said:**
> 
It would appear that the package built itself once the headers were installed. Now all I have to do is try the cable and see what happens:)!!

Am I correct in my assumption that Linux Headers are similar to the <*.h> files used in c programming, and link the calls required into the kernel?
Exactly. The kernel is written in C, so to build modules requires the headers (modules are part of the kernel even if built separately). You can inspect the files the package installs by doing (warning, a *lot* of output will result):
```

dpkg-query -L linux-headers-$(uname -r)

```

---

### Post by IntuitiveNipple on 2008-09-20
> **alanmilne said:**
> Thought you might like to see this as well:

Snap!
```

kernel: [55861.779512] usb 1-2: configuration #1 chosen from 1 choice
kernel: [55861.892915] usbcore: registered new interface driver usbserial
kernel: [55861.893129] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
kernel: [55861.893291] usbcore: registered new interface driver usbserial_generic
kernel: [55861.893294] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
kernel: [55861.921132] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for MCT U232
kernel: [55861.921338] mct_u232 1-2:1.0: MCT U232 converter detected
kernel: [55861.921541] usb 1-2: MCT U232 converter now attached to ttyUSB0
kernel: [55861.921655] usbcore: registered new interface driver mct_u232
kernel: [55861.921658] /build/buildd/linux-2.6.24/drivers/usb/serial/mct_u232.c: Magic Control Technology USB-RS232 converter driver z2.1

```

---

### Post by alanmilne on 2008-09-20
Well you appear to have solved this little mystery. The cable is now working properly with Minicom and I can change the bit rates as required.
 
This is a real boost as I have been very impressed so far with Ubuntu, but was starting to get disillusioned as to why a simple comms issue could cause so much trouble. I just hope that this 'patch' is incorporated into future upgrades so that others can benefit from it!!

When talking about the headers not being available I should point out that this system was built from the live install CD about three weeks ago and that I have accepted all the updates provided by the update manager. Maybe they were just not installed in the first place:confused:!!

You say that this is a dynamic build. Can I be sure that a future kernel update will not "blow it away"?

---

### Post by IntuitiveNipple on 2008-09-20
> **alanmilne said:**
> 
This is a real boost as I have been very impressed so far with Ubuntu, but was starting to get disillusioned as to why a simple comms issue could cause so much trouble. I just hope that this 'patch' is incorporated into future upgrades so that others can benefit from it!!

I suggest you post a [bug on launchpad](https://bugs.launchpad.net/ubuntu) against the 'linux' package with a pointer to this thread. Use the "Subscribe someone else" link to add me (intuitivenipple) and I'll try to ensure an Ubuntu patch is included if Intrepid doesn't already have it (Intrepid is based kernel 2.6.27 so many recent 'mainline 'changes are incorporated).
> **alanmilne said:**
> 
When talking about the headers not being available I should point out that this system was built from the live install CD about three weeks ago and that I have accepted all the updates provided by the update manager. Maybe they were just not installed in the first place:confused:!!

That is the strange bit since the system *did* have dkms installed and it depends on linux-headers.

> **alanmilne said:**
> 
You say that this is a dynamic build. Can I be sure that a future kernel update will not "blow it away"?
This is the beauty of DKMS. When a new kernel version starts DKMS checks if the modules it is managing are built for that kernel during start-up, and if not, builds them.
If there's another header problem after an update then follow the manual header installation procedure again, and then investigate why the headers seem to be going AWOL.

---

### Post by IntuitiveNipple on 2008-09-20
I've just checked the Intrepid source and it is included:
```

static struct usb_device_id id_table [] = {
        { USB_DEVICE(0x4348, 0x5523) },
        { USB_DEVICE(0x1a86, 0x7523) },
        { },
};

```
Post that bug and I'll nominate the change for hardy-updates since it is so trivial. Hardy being an LTS (long term support) release it would make sense to have it.

---

### Post by alanmilne on 2008-09-20
IntuitiveNipple: Once again, many thanks for your help in this and in helping me to understand the internals of Linux a bit more. I will post the bug report (once I have worked my way through how to use Launchpad :)) and hopefully everyone can benefit from your hard work in this case.

---

### Post by IntuitiveNipple on 2008-09-20
> **alanmilne said:**
> ...and in helping me to understand the internals of Linux a bit more. 
One of the beauties of Debian-based distributions is the requirement on package maintainers to include a manual page (man-page) for every application and many important configuration files, internal C functions, and so on.

It is usually my first stop in trying to understand an issue. For example, you can learn a lot about DKMS by skimming its page:
```

man dkms

```
From that, this output can be useful:
```

dkms status

```
When pages aren't available locally there's a great web-site resource for all man-pages at [linux.die.net](http://linux.die.net/man/) that includes the library functions in man section 3, such as **strcpy**.

---

### Post by IntuitiveNipple on 2008-09-20
I've now posted an SRU (Stable Release Update) request for the kernel. I'll let you know if it is accepted.

---

### Post by Ollied on 2008-09-22
I believe that I too have one of these particular Winchiphead USB/Serial cables (with turquoise connectors), however when I issue an 'lsusb' command in a terminal (with and without the cable attached) there are no vendor/product id's for the cable in the list. 

I am guessing that the cable is not recognised by the kernel and the output from 'dmesg' provides the following:

[30122.969297] usb 3-1: new full speed USB device using uhci_hcd and address 34
[30123.092784] usb 3-1: device descriptor read/64, error -71
[30123.313263] usb 3-1: device descriptor read/64, error -75

Any help would be greatly appreciated!

---

### Post by IntuitiveNipple on 2008-09-22
> **Ollied said:**
> 
[30122.969297] usb 3-1: new full speed USB device using uhci_hcd and address 34
[30123.092784] usb 3-1: device descriptor read/64, error -71
[30123.313263] usb 3-1: device descriptor read/64, error -75

Those messages tell you the device is failing in some way; possibly not answering the USB queries correctly.

Is it connected directly to the PC, or via a hub?

Try monitoring the kernel log whilst connecting the device:
```

tail -f /var/log/kern.log

```
Once it is done press Ctrl+C to stop 'tail'. If there is much difference in the messages to what you already reported, copy them here.

---

### Post by IntuitiveNipple on 2008-09-22
**FAO Alan**: I think I worked out why the headers weren't found when you tried to build the module. I just looked back over your reports and noticed:
```

alan@lilputa:~$ uname -r
2.6.24-19-386

```
Notice the system is running the **-386** variant of the kernel, not *-generic*. If you look at the report of installed linux-headers-* packages you'll notice **-generic** packages are there but no mention of *-386*.

I work with 64-bit generic most of the time so I've never tinkered with intricacies of the variants but I suspect that is the root-cause of the problem. Hopefully this will help you to figure out why the system is running the -386 variant rather than -generic - maybe it is a very *old* CPU?

---

### Post by Ollied on 2008-09-22
> **IntuitiveNipple said:**
> Those messages tell you the device is failing in some way; possibly not answering the USB queries correctly.

Is it connected directly to the PC, or via a hub?

Try monitoring the kernel log whilst connecting the device:
```

tail -f /var/log/kern.log

```
Once it is done press Ctrl+C to stop 'tail'. If there is much difference in the messages to what you already reported, copy them here.

Thanks for the quick response.

It is directly connected to the PC and the same/similar response to those that I have already posted irrespective of which usb port that I use.

---

### Post by IntuitiveNipple on 2008-09-22
> **Ollied said:**
> Thanks for the quick response.

It is directly connected to the PC and the same/similar response to those that I have already posted irrespective of which usb port that I use.
It looks like the device is broken in some way. Do you have a Windows PC and the drivers to test it on? Try to discover if the device works :)

---

### Post by Ollied on 2008-09-22
> **IntuitiveNipple said:**
> It looks like the device is broken in some way. Do you have a Windows PC and the drivers to test it on? Try to discover if the device works :)


The thing is that I purchased two of these new only recently and they both produce the same results. Windows can't see them properly either and they sit in the device manager as an unknown device even after installing the Windows PL2303 driver. If nobody has an idea then I may just have to send them back to the seller.

Thanks for your help so far. :)

---

### Post by IntuitiveNipple on 2008-09-22
> **Ollied said:**
> The thing is that I purchased two of these new only recently and they both produce the same results. Windows can't see them properly either and they sit in the device manager as an unknown device even after installing the Windows PL2303 driver. If nobody has an idea then I may just have to send them back to the seller.

Thanks for your help so far. :)
That tells me they're broken - send them back!

---

### Post by alanmilne on 2008-09-23
> **IntuitiveNipple said:**
> **FAO Alan**: I think I worked out why the headers weren't found when you tried to build the module. I just looked back over your reports and noticed:
```

alan@lilputa:~$ uname -r
2.6.24-19-386

```
Notice the system is running the **-386** variant of the kernel, not *-generic*. If you look at the report of installed linux-headers-* packages you'll notice **-generic** packages are there but no mention of *-386*.

I work with 64-bit generic most of the time so I've never tinkered with intricacies of the variants but I suspect that is the root-cause of the problem. Hopefully this will help you to figure out why the system is running the -386 variant rather than -generic - maybe it is a very *old* CPU?


Just to let you know that I am testing out Ubuntu on my sister's old Toshiba Satellite S3000-X11. This is about 6-7 years old and uses a Celeron running at 1.066 GHz. I think you are right in that this is an *old* CPU. I am currently playing with this system to learn more about Linux and for use on our Hill-Walking activities (GPS and Photographs, etc.). To see more visit [http://www.alanlmilne.co.uk/]("http://www.alanlmilne.co.uk/").

My PIC/Atmel/Altera/Xilinx development system is a much faster desktop and hopefully I will be upgrading this soon to an AMD 64-bit solution, but I must ensure that I can get everything to work with Ubuntu first.

---

### Post by alanmilne on 2008-09-23
> **Ollied said:**
> I believe that I too have one of these particular Winchiphead USB/Serial cables (with turquoise connectors), however when I issue an 'lsusb' command in a terminal (with and without the cable attached) there are no vendor/product id's for the cable in the list. 

I am guessing that the cable is not recognised by the kernel and the output from 'dmesg' provides the following:

[30122.969297] usb 3-1: new full speed USB device using uhci_hcd and address 34
[30123.092784] usb 3-1: device descriptor read/64, error -71
[30123.313263] usb 3-1: device descriptor read/64, error -75

Any help would be greatly appreciated!

The fact that you are not getting vendor/product IDs indicates that the initial USB set up is failing. According to USB V1.0/1.1/2.0 specs, the host controller should interrogate the USB device upon insertion, and the device should respond with its PID/VID as part of the Device Descriptor. This enables the host controller to load any required driver for the newly inserted device.

The fact that you are getting device descriptor errors indicates that the device is not responding. I am in agreement with IntuitiveNipple when he thinks these are broken devices. If you can see other USB devices via the lsusb command, then there is nothing wrong with your system, it *must* be these cables.

---

### Post by wgbuntu on 2008-10-04
Finally an answer that works for HL-340 on 8.04 kernel 2.6.24-19

---

### Post by psypher on 2008-11-17
Hi all,

I cannot seem to get this installed. the repo does not seem to have the intrepid package. Luanchpad claims this has been added to the Intrepid Proposed repo but I have no idea how to install the driver i want. Also cannot compile the driver despite being sure I have all the deps. I get this error when trying to compile:

make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/ch341 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /ch341/ch341.o
/ch341/ch341.c: In function 'ch341_open':
/ch341/ch341.c:248: warning: passing argument 1 of 'usb_serial_generic_open' from incompatible pointer type
/ch341/ch341.c:248: warning: passing argument 2 of 'usb_serial_generic_open' from incompatible pointer type
/ch341/ch341.c:248: error: too few arguments to function 'usb_serial_generic_open'
/ch341/ch341.c: In function 'ch341_set_termios':
/ch341/ch341.c:260: error: 'struct usb_serial_port' has no member named 'tty'
/ch341/ch341.c:266: error: 'struct usb_serial_port' has no member named 'tty'
/ch341/ch341.c:266: error: 'struct usb_serial_port' has no member named 'tty'
/ch341/ch341.c: At top level:
/ch341/ch341.c:317: error: unknown field 'num_interrupt_in' specified in initializer
/ch341/ch341.c:317: error: 'NUM_DONT_CARE' undeclared here (not in a function)
/ch341/ch341.c:318: error: unknown field 'num_bulk_in' specified in initializer
/ch341/ch341.c:318: warning: initialization makes pointer from integer without a cast
/ch341/ch341.c:319: error: unknown field 'num_bulk_out' specified in initializer
/ch341/ch341.c:319: warning: initialization makes pointer from integer without a cast
/ch341/ch341.c:321: warning: initialization from incompatible pointer type
/ch341/ch341.c:322: warning: initialization from incompatible pointer type
make[2]: *** [/ch341/ch341.o] Error 1
make[1]: *** [_module_/ch341] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

Any ideas? I need this cable to configure Cisco routers.

I'm running Intrepid x86_64


Thanks

---

### Post by wgbuntu on 2009-01-03
> **wgbuntu said:**
> Finally an answer that works for HL-340 on 8.04 kernel 2.6.24-19

Had to do this for Intrepid too.  The DKMS part was all good, update to new kernel but require modprobe and insmod to completely install to ttyUSB0

---

### Post by DiegoFerreira on 2009-01-15
Hi there,

Got ch341 working in kernel 2.6.27.9-generic. Problem is:
For some reason the usb-serial structures were remolded some kernel revisions ago.


> **psypher said:**
> Hi all,

I cannot seem to get this installed. the repo does not seem to have the intrepid package. Luanchpad claims this has been added to the Intrepid Proposed repo but I have no idea how to install the driver i want. Also cannot compile the driver despite being sure I have all the deps. I get this error when trying to compile:

make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/ch341 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /ch341/ch341.o
/ch341/ch341.c: In function 'ch341_open':
/ch341/ch341.c:248: warning: passing argument 1 of 'usb_serial_generic_open' from incompatible pointer type
/ch341/ch341.c:248: warning: passing argument 2 of 'usb_serial_generic_open' from incompatible pointer type
/ch341/ch341.c:248: error: too few arguments to function 'usb_serial_generic_open'
/ch341/ch341.c: In function 'ch341_set_termios':
/ch341/ch341.c:260: error: 'struct usb_serial_port' has no member named 'tty'
/ch341/ch341.c:266: error: 'struct usb_serial_port' has no member named 'tty'
/ch341/ch341.c:266: error: 'struct usb_serial_port' has no member named 'tty'
/ch341/ch341.c: At top level:
/ch341/ch341.c:317: error: unknown field 'num_interrupt_in' specified in initializer
/ch341/ch341.c:317: error: 'NUM_DONT_CARE' undeclared here (not in a function)
/ch341/ch341.c:318: error: unknown field 'num_bulk_in' specified in initializer
/ch341/ch341.c:318: warning: initialization makes pointer from integer without a cast
/ch341/ch341.c:319: error: unknown field 'num_bulk_out' specified in initializer
/ch341/ch341.c:319: warning: initialization makes pointer from integer without a cast
/ch341/ch341.c:321: warning: initialization from incompatible pointer type
/ch341/ch341.c:322: warning: initialization from incompatible pointer type
make[2]: *** [/ch341/ch341.o] Error 1
make[1]: *** [_module_/ch341] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

Any ideas? I need this cable to configure Cisco routers.

I'm running Intrepid x86_64


Thanks

This may have some issues, and I tested it only on gtkterm with a serial port RS232-RS485 (Novus ISO485-1). Would appreciate if anyone give it a try.

Cya

---

### Post by cmavr8 on 2009-02-13
Hi everybody.
I've been reading your messages and:

[LIST]
[*]Can't find ch341 package when trying:
sudo apt-get install ch341-dkms
(offcourse after adding ppa repos + key).

[*]modprobe -l |grep ch341 gives back: 
/lib/modules/2.6.27-11-generic/kernel/drivers/usb/serial/ch341.ko
Does this mean I have it already?

[*]How do I verify the adapter is working? I want to connect a BasicStamp2 but can't get it to work. Is there a way to debug and decide if it's the cable/adapter's problem or the Stamp's?
[/LIST]


Thanks a lot for your time

---

### Post by IntuitiveNipple on 2009-02-13
> **cmavr8 said:**
> Hi everybody.
I've been reading your messages and:

[LIST]
[*]Can't find ch341 package when trying:
sudo apt-get install ch341-dkms
(offcourse after adding ppa repos + key).

[*]modprobe -l |grep ch341 gives back: 
/lib/modules/2.6.27-11-generic/kernel/drivers/usb/serial/ch341.ko
Does this mean I have it already?

[*]How do I verify the adapter is working? I want to connect a BasicStamp2 but can't get it to work. Is there a way to debug and decide if it's the cable/adapter's problem or the Stamp's?
[/LIST]

[list]
  [*] The package in my PPA is **only for Hardy** (kernel 2.6.24):
```

 Show details   ch341-dkms - 1.1-0ubuntu1~ppa2h   	 (changesfile)   	2008-09-19  	Published  	Hardy  	Misc  	 All builds were built successfully.

```
  [*] **modinfo ch341** will report the installed module *and* the VENDOR:DEVICE IDs it supports.
  [*] Check the VENDOR:DEVICE ID of the device you have against what the module supports (see above) using **lspci -nn**
[/list]
See my [original comment #5](http://ubuntuforums.org/showpost.php?p=5819347&postcount=5) for more details.

---

### Post by cmavr8 on 2009-02-13
```
$ modinfo ch341
filename:       /lib/modules/2.6.27-11-generic/kernel/drivers/usb/serial/ch341.ko
license:        GPL
srcversion:     CB68E4DB7078F2C50CD227F
alias:          usb:v1A86p7523d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v4348p5523d*dc*dsc*dp*ic*isc*ip*
depends:        usbserial,usbcore
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 
parm:           debug:Debug enabled or not (bool)
```

I can see no 1a86:7523 ...

Thanks for the immediate answer...

---

### Post by IntuitiveNipple on 2009-02-13
alias:          usb:v**[color=red]1A86[/color]p[color=blue]7523[/color]**d*dc*dsc*dp*ic*isc*ip*

---

### Post by cmavr8 on 2009-02-13
Thanks, my bad...

Is there some easy way to verify that it's correctly recognized?
It SHOULD be ok, but I have no way to check it.

I'll look towards the other direction, the basic stamp, assuming the usb2com is working.

---

### Post by duke149 on 2009-08-13
Why is the zip password protected?

---

### Post by DiegoFerreira on 2010-02-22
My zip got corromped =/

Well, lots have happened since I posted this zip. Got my worstation's HD gone dead, lost lot's of stuff and with it my solution to winchiphead =/

I'll try looking at it some more. For what I recall it's all about the refacturing made in the usb-serial, where some files changed names and the directory structure was redone.

I also remember setting the PID and VID in some files and changing some minor details to adapt funtions and PRESTO. 

Enough cheap chat, I'll see what can be done =]

Cya soon

---

### Post by mclightning on 2010-03-29
hi everybody
i got same driver and i have been trying to get it work with my device.we've been discussing on talk.maemo.org and we couldnt figure out what to do to get it working.
[http://talk.maemo.org/showthread.php?p=586607#post586607](http://talk.maemo.org/showthread.php?p=586607#post586607)
please help this linux newbie :(

---

### Post by mclightning on 2010-03-29
[IMG]http://img532.yfrog.com/img532/8166/snapshot3m.png[/IMG]
here is a screenshot

[IMG]http://img163.yfrog.com/img163/8766/snapshot2fc.png[/IMG]
to make a summary
i did these
insmod usbserial.ko
insmod pl2303.ko
insmod ftdi_sio.ko #i installed both pl2303 ftdi_sio drivers to be sure.
but still no ttyUSB0
im running all these on a maemo device.Maemo is a debian derived OS.but it is also possible to install Ubuntu,Fedore,Debian
[IMG]http://farm3.static.flickr.com/2458/3767980577_6d5427dbed_m.jpg[/IMG]
[IMG]http://farm4.static.flickr.com/3611/3694192324_1d588854b3_m.jpg[/IMG]

---

### Post by mclightning on 2010-03-30
heyyy nobody here??????

---

