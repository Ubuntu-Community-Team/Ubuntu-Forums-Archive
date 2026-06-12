---
title: "Microsoft LifeCam VX-6000 Help"
date: 2008-09-15
forum: Hardware
---

### Post by CTConqueror on 2008-09-15
I just installed the latest version of Ubuntu (Hardy Heron) today, and I was wondering if there had been any drivers released yet?  I tried searching and all, but I didn't find anything useful.

---

### Post by CTConqueror on 2008-09-16
Just bumping cause this got into farther pages really quickly.

---

### Post by cmb12352 on 2008-09-16
[size=2][font=Times New Roman][size=3]hi,everyone,need guitar effects pedals? take a look at [guitar effects pedals shop](http://www.myguitarpedals.com/), may be u will find ur favorite...This is an excellent thread!**The good:** The optional Bowers and Wilkins audio system in the 2009 Jaguar XF offers exceptional separation and clarity for music playback. We like the interior materials in the XF, along with the tech touches. The engine offers a good amount of power for the car while delivering acceptable fuel economy.[runescape gold](http://www.runescapecoin.net/) **The bad:** The touch-screen interface for audio, navigation, and other car systems is too slow, and it is not well organized. The navigation system is unremarkable.[age of conan gold](http://www.buy-age-of-conan-gold.com/)**The bottom line:** The 2009 Jaguar XF offers a lot of luxury for the money, with many unique high-tech touches and an exceptional audio system. But it doesn't always deliver on its apparent promise, [color=#008000][age of conan money](http://www.ageofconanmoney.net/) [/color]with a run-of-the-mill suspension and navigation system.[runescape money](http://www.runescapemoney.ws/). [/size][/font][/size]

---

### Post by thirstyghost on 2008-09-20
Not that I know of.    You'll have to keep it for Windows use and get a Logitech for Linux (see the list).   I have a Quickcam STX that works out of the box great.    Try Ebay or Craigslist for some good deals (as in half-price).

---

### Post by IntuitiveNipple on 2008-09-20
I've built the microdia driver as a DKMS (Dynamic Kernel Module Support) package for Hardy. It includes support for the device ID 0c45:624f which is, I understand, the Lifecam VX-6000. It supports these device IDs:
```

 045E:00F4 
 04F2:A128
 0C45:6240 0C45:6242 0C45:6243 0C45:6248
 0C45:624B 0C45:624C 0C45:624E 0C45:624F
 0C45:6253 0C45:6260 0C45:6262 0C45:6270
 0C45:627A 0C45:627B 0C45:627C 0C45:627F
 0C45:6280 0C45:6282 0C45:6283 0C45:6288
 0C45:628A 0C45:628B 0C45:628C 0C45:628E
 0C45:628F 0C45:62A0 0C45:62A2 0C45:62B0
 0C45:62B3 0C45:62BA 0C45:62BB 0C45:62BC
 0C45:62BE
 145F:013D

```
It is available from my Ubuntu PPA (Personal Package Archive). To install it add my PPA to apt's source list:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo apt-get update

```
and then install the package:
```

sudo apt-get install microdia-dkms

```
Remove my PPA from the apt sources to prevent unexpected upgrades of packages I maintain:
```

sudo rm /etc/apt/sources.list.d/intuitivenipple.list
sudo apt-get update

```

---

### Post by Kirill_1985 on 2008-09-21
Hi, I have a web camera ID 0c45: 6248 Microdia (COSY PS 679)
Do everything as you said, but:

dmesg | tail-l
[5400.873059] usbcore: registered new interface driver usb_microdia_driver
[5400.873521] microdia: v2008.09: Microdia USB 2.0 Webcam Driver
[6020.747971] usb 5-1: USB disconnect, address 4
[6029.283234] usb 5-4: new high speed USB device using ehci_hcd and address 5
[6029.416793] usb 5-4: configuration # 1 chosen from 1 choice
[6029.417386] microdia: Camera 0C45: 6248 not supported.
[7257.312336] usb 5-4: USB disconnect, address 5
[7259.863926] usb 5-4: new high speed USB device using ehci_hcd and address 6
[7260.001313] usb 5-4: configuration # 1 chosen from 1 choice
[7260.001714] microdia: Camera 0C45: 6248 not supported.

in /dev/video0 device does not appear. What to do?

---

### Post by IntuitiveNipple on 2008-09-21
> **Kirill_1985 said:**
> Hi, I have a web camera ID 0c45: 6248 Microdia (COSY PS 679)

[7260.001714] microdia: Camera 0C45: 6248 not supported.

As the driver says, that device isn't supported.

I'm not sure why it does that since it declares itself as capable of handling that device in the **usb_device_id** table, but then a supplementary internal table (struct microdia_camera cameras[]) doesn't include product 0x6248, which causes a call to find_camera() to fail, which in turn causes the "not supported" message.

You should contact the authors and ask about that. The contact details are in the manual page:
```

man microdia

```

---

### Post by CTConqueror on 2008-09-24
I did what you said with installing the package from your list, but the webcam still isn't recognized.

---

### Post by IntuitiveNipple on 2008-09-25
Please report the entries from /var/log/kern.log when inserting the camera so we know what the system found and did.

---

### Post by CTConqueror on 2008-09-25
This is from the log when I plugged my camera in:

```
Sep 25 09:37:11 brian-desktop kernel: [40720.552809] usb 3-1: new high speed USB device using ehci_hcd and address 5
Sep 25 09:37:11 brian-desktop kernel: [40720.687903] usb 3-1: configuration #1 chosen from 1 choice
Sep 25 09:37:11 brian-desktop kernel: [40720.688887] microdia: Camera 045E:00F4 not supported.
```

---

### Post by IntuitiveNipple on 2008-09-25
The same situation I explained in [comment #6](http://ubuntuforums.org/showpost.php?p=5831598&postcount=6) applies to 045E:00F4 as well.

As I said, I have no idea why the driver declares support for device IDs and then doesn't have the internal structures in place.

The author of the code in microdia-usb.c is Nicolas Vivien. If you do
```

man microdia

```
you'll find I put the contact information for the project in there.

---

### Post by XanTrax on 2008-10-06
> **IntuitiveNipple said:**
> I've built the microdia driver as a DKMS (Dynamic Kernel Module Support) package for Hardy. It includes support for the device ID 0c45:624f which is, I understand, the Lifecam VX-6000. It supports these device IDs:
```

 **_045E:00F4 _**
 04F2:A128
 0C45:6240 0C45:6242 0C45:6243 0C45:6248
 0C45:624B 0C45:624C 0C45:624E 0C45:624F
 0C45:6253 0C45:6260 0C45:6262 0C45:6270
 0C45:627A 0C45:627B 0C45:627C 0C45:627F
 0C45:6280 0C45:6282 0C45:6283 0C45:6288
 0C45:628A 0C45:628B 0C45:628C 0C45:628E
 0C45:628F 0C45:62A0 0C45:62A2 0C45:62B0
 0C45:62B3 0C45:62BA 0C45:62BB 0C45:62BC
 0C45:62BE
 145F:013D

```


Hi, firstly I would like to thank you for this.  I have ran into a problem.  The Device ID that is highlighted above (045E:00F4) is my webcams device ID (microsoft life cam vx-6000) but it seems your package still does not recognize it.

As you can see:

> 
[15:13:42][eax@kozler-linux:~]$ dmesg | grep "micro"
[   46.843020] microdia: Microdia USB 2.0 webcam driver loaded
[   46.843069] microdia: Camera 045E:00F4 not supported.
[   46.843084] usbcore: registered new interface driver usb_microdia_driver
[   46.843088] microdia: v2008.09 : Microdia USB 2.0 Webcam Driver
[15:13:43][eax@kozler-linux:~]$ 


I hope you can help.  As you can see there, it says it is not supported.

---

### Post by IntuitiveNipple on 2008-10-06
> **XanTrax said:**
> Hi, firstly I would like to thank you for this.  I have ran into a problem.  The Device ID that is highlighted above (045E:00F4)
See my comments in [comment #10](http://ubuntuforums.org/showpost.php?p=5853166&postcount=10)

---

### Post by XanTrax on 2008-10-06
> **IntuitiveNipple said:**
> See my comments in [comment #10](http://ubuntuforums.org/showpost.php?p=5853166&postcount=10)

And I have done so :p.

[https://groups.google.com/group/microdia/browse_thread/thread/4e0dde7df35ce9dc](https://groups.google.com/group/microdia/browse_thread/thread/4e0dde7df35ce9dc)

Also, I did not contact that guy directly.  I figured id let the group sort it out.  Weird that they were able to get some peoples Life Cams working without a single problem.

---

### Post by amp0303 on 2008-12-18
I tried to copy and paste but it says:

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by amp0303 on 2008-12-18
mine doesn't even say it's not supported:

[ 3079.306855] usb 1-1: USB disconnect, address 5
[ 3143.592024] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 3143.755445] usb 1-1: configuration #1 chosen from 1 choice
[ 3143.870530] 6:2:1: cannot get freq at ep 0x84
[ 3144.813511] 6:2:1: cannot get freq at ep 0x84

---

### Post by amp0303 on 2008-12-18
it also couldnt find package microdia-dkms

---

### Post by XPuntu on 2008-12-21
I have a new NX3000 but thought I would give this a try. The install seems ok. Here's the last part of the output:

```
DKMS: add Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.24-22-generic KVER=2.6.24-22-generic src=/var/lib/dkms/microdia/2008.09/build................
cleaning build area....

DKMS: build Completed.
Installing module...
Running module version sanity check.

microdia.ko:
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.24-22-generic/updates/dkms/

depmod.......

DKMS: install Completed.
```

Here's my output from the kern.log

```
Dec 21 21:47:46 jasong-desktop kernel: [48943.315636] usb 2-1: new full speed USB device using uhci_hcd and address 4
Dec 21 21:47:46 jasong-desktop kernel: [48943.563800] usb 2-1: configuration #1 chosen from 1 choice
Dec 21 21:47:46 jasong-desktop kernel: [48943.571815] uvcvideo: Found UVC 1.00 device Microsoft LifeCam NX-3000 (045e:0721)
Dec 21 21:47:46 jasong-desktop kernel: [48943.579586] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
```


So it seems to detect ok but I guess it's just not going to be configured properly. Should I bother with this camera or just move it to my windows machine?

Thanks.

---

### Post by craigsn on 2009-01-16
```

sudo apt-get install microdia-dkms

```

When I try to do this, after running the other code you listed, I get this message

> 
craig@UberAni:/dev$ sudo apt-get install microdia-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package microdia-dkms


Any help here?

Thakns

---

### Post by mikebravo on 2009-05-11
> **IntuitiveNipple said:**
> I've built the microdia driver as a DKMS (Dynamic Kernel Module Support) package for Hardy. It includes support for the device ID 0c45:624f which is, I understand, the Lifecam VX-6000. It supports these device IDs:
```

 045E:00F4 
 04F2:A128
 0C45:6240 0C45:6242 0C45:6243 0C45:6248
 0C45:624B 0C45:624C 0C45:624E 0C45:624F
 0C45:6253 0C45:6260 0C45:6262 0C45:6270
 0C45:627A 0C45:627B 0C45:627C 0C45:627F
 0C45:6280 0C45:6282 0C45:6283 0C45:6288
 0C45:628A 0C45:628B 0C45:628C 0C45:628E
 0C45:628F 0C45:62A0 0C45:62A2 0C45:62B0
 0C45:62B3 0C45:62BA 0C45:62BB 0C45:62BC
 0C45:62BE
 145F:013D

```
It is available from my Ubuntu PPA (Personal Package Archive). To install it add my PPA to apt's source list:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo apt-get update

```
and then install the package:
```

sudo apt-get install microdia-dkms

```
Remove my PPA from the apt sources to prevent unexpected upgrades of packages I maintain:
```

sudo rm /etc/apt/sources.list.d/intuitivenipple.list
sudo apt-get update

```

Dear Nip,
Things seem to have been lost in the shuffle, now that it is May 2008. Does the source referenced still exist? Will it work with Jaunty?  It sounds like what I need to get my VX-6000 [045e:00f4] working with Skype.

MikeBravo

---

### Post by AdNZL on 2009-10-05
Intuitive, is your repo still working? I followed the steps you laid out but it says that it can't find the microdia when it trys to download it. I just copied and pasted everything so there shouldn't be any typos.

Edit* Ah looks like a few people have already noticed this some time ago. Bit of a bugger really I was hoping to get it working.

---

### Post by sdowney717 on 2009-10-10
[http://ubuntuforums.org/showthread.php?t=1118056](http://ubuntuforums.org/showthread.php?t=1118056)

i had done this with jaunty. 
And had a working webcam

but now i just tried it with karmic and get a compiler error

web page with instructions
[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)

---

### Post by Arup on 2009-11-04
Karmic supports the VX-6000 via kernel so you don't need any drivers.

---

### Post by the8thstar on 2009-11-07
The webcam works in Cheese but doesn't in Skype... pity.

---

### Post by beyercj on 2010-03-30
This is how I got my Microsoft LifeCam VX-6000 to work under Ubuntu 9.10 on a [Gericom Frontman]("http://download.gericom.com/LCD-PC/FrontmanForce-L372/DATASHEET/L732.pdf") computer:



Download Skype from website and install
 

 Locate libv4l (Library video for linux)
 user@desktop:~$ locate libv4l  
 /usr/lib/libv4l  
 /usr/lib/libv4l1.so.0  
 /usr/lib/libv4l2.so.0  
 /usr/lib/libv4lconvert.so.0  
 /usr/lib/libv4l/ov511-decomp  
 /usr/lib/libv4l/ov518-decomp  
 /usr/lib/libv4l/v4l1compat.so  
 /usr/lib/libv4l/v4l2convert.so  
 /usr/share/doc/libv4l-0  
 /usr/share/doc/libv4l-0/README.gz  
 /usr/share/doc/libv4l-0/README.multi-threading 
 /usr/share/doc/libv4l-0/TODO  
 /usr/share/doc/libv4l-0/changelog.Debian.gz 
 /usr/share/doc/libv4l-0/changelog.gz  
 /usr/share/doc/libv4l-0/copyright  
 /usr/share/lintian/overrides/libv4l-0  
 /var/lib/dpkg/info/libv4l-0.list  
 /var/lib/dpkg/info/libv4l-0.md5sums  
 /var/lib/dpkg/info/libv4l-0.postinst  
 /var/lib/dpkg/info/libv4l-0.postrm  
 /var/lib/dpkg/info/libv4l-0.shlibs  
 /var/lib/dpkg/info/libv4l-0.symbols  
 user@desktop:~$  
 

if not already installed, you need to install [libv4l]("https://launchpad.net/ubuntu/+source/libv4l"), a collection of libraries which adds a thin abstraction layer on top of video4linux2 devices presumably best via Synaptec (System > Administration > Synaptec Package Manager, enter "libv4l" into Quick search, reload, rightclick to mark for installation and apply)



 change entry skype in System>Preferences>Main Menu>Internet>Skype>Properties>Command to  
 env LD_PRELOAD=/location/v4l1compat.so skype, I.e.
 env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
 

 Close
 Start Skype by double clicking icon in Applications>Internet


This worked ok for me although the picture quality with the original driver under Windows XP is much better.

---

### Post by browneej on 2011-06-24
So I had to shift from /usr/lib to /usr/lib32, even though the file is located in both places.  I'm running 64bit ubuntu 11.04:

~$ locate libv4l
/usr/lib/libv4l
/usr/lib/libv4l1.so.0
/usr/lib/libv4l2.so.0
/usr/lib/libv4lconvert.so.0
/usr/lib/libv4l/ov511-decomp
/usr/lib/libv4l/ov518-decomp
[COLOR=Red]/usr/lib/libv4l/v4l1compat.so[/COLOR]
/usr/lib/libv4l/v4l2convert.so
/usr/lib/vlc/plugins/access/libv4l2_plugin.so
/usr/lib32/libv4l
/usr/lib32/libv4l1.so.0
/usr/lib32/libv4l2.so.0
/usr/lib32/libv4lconvert.so.0
/usr/lib32/libv4l/ov511-decomp
/usr/lib32/libv4l/ov518-decomp
/[COLOR=Red]usr/lib32/libv4l/v4l1compat.so[/COLOR]
/usr/lib32/libv4l/v4l2convert.so
/usr/share/doc/libv4l-0
/usr/share/doc/libv4l-0/README
/usr/share/doc/libv4l-0/README.lib-multi-threading
/usr/share/doc/libv4l-0/README.lib.gz
/usr/share/doc/libv4l-0/TODO
/usr/share/doc/libv4l-0/changelog.Debian.gz
/usr/share/doc/libv4l-0/copyright
/usr/share/lintian/overrides/libv4l-0
/var/lib/dpkg/info/libv4l-0.list
/var/lib/dpkg/info/libv4l-0.md5sums
/var/lib/dpkg/info/libv4l-0.postinst
/var/lib/dpkg/info/libv4l-0.postrm
/var/lib/dpkg/info/libv4l-0.shlibs
/var/lib/dpkg/info/libv4l-0.symbols

~$ cat /usr/local/bin/skype-cam-fix 
#! /bin/sh
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Once I made this change, Skype 2.2 displayed video in Options->Video->Test.

---

