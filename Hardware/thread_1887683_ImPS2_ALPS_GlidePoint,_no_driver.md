---
title: "ImPS/2 ALPS GlidePoint, no driver"
date: 2011-11-27
forum: Hardware
---

### Post by aeronutt on 2011-11-27
My trackpad on my Dell Vostro laptop has never been recognized as anything other than a generic mouse for several versions of Ubuntu (since 10.04). 

I look at //mnt/bdmpartition/bdm_dir/Linux to see what track pad I have, and it shows:

ImPS/2 ALPS GlidePoint.

How could I go about looking for a driver for this, and
How would I know if anyone is even working on one?

Or best, anyone know of a fix?

---

### Post by scarleo on 2011-11-28
Try [this driver]("http://people.canonical.com/%7Esforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb") for ALPS touchpad. Install and then restart.

I have tested this with 11.10. It works for me and gave me mulitouch   with my ALPS touchpad, I can have edge scrolling or two finger   scrolling, set sensitivity and speed. Didn't try anything else.
  Source: [[regression] Alps touchpad detected, but scrolling not working LP bug #737051]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/737051")

---

### Post by aeronutt on 2011-11-28
Scarleo, thanks! I'll give it a try when I get back to my laptop, and report back.

---

### Post by aeronutt on 2011-11-28
Yep, installed, and it works for me in Mint12, aka 11.10, awesome!!!

---

### Post by ufugu on 2011-12-13
I am SO THANKFUL to whoever made this. 

My touchpad is finally configurable on my Dell Inspiron N5110. I can actually type without the cursor moving every which way when my palm is near the touchpad.

---

### Post by fklavye on 2011-12-14
Yes, my Dell Inspiron 5110 (Kubuntu 11.10) touch pad is configurable now. Thanks. But in configuration options I still couldn't find how to disable it.

---

### Post by Argovia on 2012-03-12
I am running 12.04 Beta 1 on a Dell Inspiron N5110.

In Update Manager, the install of the above recommended deb seemed OK, but after restarting I still don't have any touchpad in System Settings.  I then ran sudo dpkg -i  psmouse-alps-dkms_0.10_all.deb in the terminal and got this:

Setting up psmouse-alps-dkms (0.10) ...

Loading tarball for psmouse-alps-0.10
Loading /var/lib/dkms/psmouse-alps/0.10/2.6.38-11-generic/x86_64...

DKMS: ldtarball completed.

Creating symlink /var/lib/dkms/psmouse-alps/0.10/source ->
                 /usr/src/psmouse-alps-0.10

DKMS: add completed.
First Installation: checking all kernels...
Building only for 3.2.0-18-generic-pae
Building for architecture i686
Building initial module for 3.2.0-18-generic-pae
Error! Bad return status for module build on kernel: 3.2.0-18-generic-pae (i686)
Consult /var/lib/dkms/psmouse-alps/0.10/build/make.log for more information.

The make.log looks like this:

DKMS make.log for psmouse-alps-0.10 for kernel 3.2.0-18-generic-pae (i686)
Mon Mar 12 19:54:46 CET 2012
make: Entering directory `/usr/src/linux-headers-3.2.0-18-generic-pae'
  LD      /var/lib/dkms/psmouse-alps/0.10/build/src/built-in.o
  CC [M]  /var/lib/dkms/psmouse-alps/0.10/build/src/psmouse-base.o
  CC [M]  /var/lib/dkms/psmouse-alps/0.10/build/src/synaptics.o
  CC [M]  /var/lib/dkms/psmouse-alps/0.10/build/src/alps.o
/var/lib/dkms/psmouse-alps/0.10/build/src/alps.c:135:33: error: expected ‘)’ before ‘int’
make[2]: *** [/var/lib/dkms/psmouse-alps/0.10/build/src/alps.o] Error 1
make[1]: *** [/var/lib/dkms/psmouse-alps/0.10/build/src] Error 2
make: *** [_module_/var/lib/dkms/psmouse-alps/0.10/build] Error 2
make: Leaving directory `/usr/src/linux-headers-3.2.0-18-generic-pae'

I've looked at line 135 in the file alps.c:

module_param(alps_dump_packets, int, 0644);

I don't know nearly enough to try and put the expected ')' in the right place!  Or am I doing something completely wrong??  Maybe this deb doesn't work with 12.04??

Thanks in advance for any help!

---

### Post by jmfrank63 on 2012-03-12
Hello, I was having exactly the same problem. I "fixed" the compile error, but probably will get shot for my "solution":
In alps.c an #include "linux/moduleparam.h" is missing. I can unpack the package fix the error but the I do not know how to build the package again, since this is not a source package. Therefor I took a lib from /usr/src/linux-headers-3.2.0.18-generic/include/linux and included an #include "moduleparams.h" in it and installed the package.
Well at least it works, and with the next update of the kernel headers it will be overwritten.
But remember its dirty, very dirty, very very dirty!!!
**Update**: well the module compiled but two finger scrolling still does not work. Hope you have more luck.

---

### Post by Argovia on 2012-03-13
Hi jmfrank63

Thanks for the answer, even though I'm a little hesitant to try it with my very limited linux skills.  Maybe I'll get up enough courage or get frustrated enough to try it...

Thanks!

---

### Post by themacmeister on 2012-03-20
Did NOT work for me using Ubuntu 11.10 Desktop AMD64

It was only ever shown as mouse, although it did work OK as just a pointing/clicking device. I really wanted multitouch tho. The loss of two finger scroll, and no working prefs tab, was a deal breaker. Back to Win7 for now...

Anyone have a foolproof method for this yet? I don't care if I have to replace .conf files or whatever. Someone solved this with a three-part kernel argument on boot, unloading and reloading i1802 or something?!

Cheers for any help!

---

### Post by aeronutt on 2012-03-20
> **Argovia said:**
> I am running 12.04 Beta 1 on a Dell Inspiron N5110.

In Update Manager, the install of the above recommended deb seemed OK,......

FYI, the track pad on my Dell Vostro is recognized as a trackpad in 12.04 beta, without the need to load this .deb.

---

### Post by oc666 on 2012-03-25
> **themacmeister said:**
> Did NOT work for me using Ubuntu 11.10 Desktop AMD64

It was only ever shown as mouse, although it did work OK as just a pointing/clicking device. I really wanted multitouch tho. The loss of two finger scroll, and no working prefs tab, was a deal breaker. Back to Win7 for now...

Anyone have a foolproof method for this yet? I don't care if I have to replace .conf files or whatever. Someone solved this with a three-part kernel argument on boot, unloading and reloading i1802 or something?!

Cheers for any help!

Hey
I've dell e6220 and I'm also wondering if we can enable the multi-touch feature, cause it's mandatory for me.
Here is my kernal details:
```
$ uname -a
Linux name-Latitude-E6220 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```
Here is lspci output:
```
$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
09:00.0 SD Host controller: O2 Micro, Inc. Device 8221 (rev 05)
09:00.1 Mass storage controller: O2 Micro, Inc. Device 8231 (rev 03)
```

---

### Post by z4k4ri4 on 2012-04-18
> **jmfrank63 said:**
> Hello, I was having exactly the same problem. I "fixed" the compile error, but probably will get shot for my "solution":
In alps.c an #include "linux/moduleparam.h" is missing. I can unpack the package fix the error but the I do not know how to build the package again, since this is not a source package. Therefor I took a lib from /usr/src/linux-headers-3.2.0.18-generic/include/linux and included an #include "moduleparams.h" in it and installed the package.
Well at least it works, and with the next update of the kernel headers it will be overwritten.
But remember its dirty, very dirty, very very dirty!!!
**Update**: well the module compiled but two finger scrolling still does not work. Hope you have more luck.

Well here's a more cleaner approach:
```
sudo dpkg -i psmouse-alps-dkms_0.10_all.deb
sudoedit /usr/src/psmouse-alps-0.10/src/alps.c
```

Add ```
#include <linux/moduleparam.h>
```
below ```
#include <linux/slab.h>
#include <linux/input.h>
#include <linux/input/mt.h>
#include <linux/serio.h>
#include <linux/libps2.h>
```

Then finish it with: ```
sudo dkms build -m psmouse -v alps-0.10
sudo dkms install -m psmouse -v alps-0.10
```

---

### Post by joneberger on 2012-04-23
Worked like a champ for me on 11.10 on a Dell Latitude E5520.  Thanks!

Jon

---

### Post by digitaleagle on 2012-08-07
I think I need this driver to get my touchpad working, but I can't find it anywhere.  Does anyone know of a new location to get that driver?

This link returns 404 for me:
[http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10](http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10)

---

### Post by martin.bartlett on 2012-08-31
The driver is now : [here]("http://people.canonical.com/~sforshee/lp877666/psmouse-alps-dkms/"). Works great on My Dell E6420, Ubuntu 11.10.

---

### Post by boot_sectorz on 2012-09-06
This driver is hard to find. Keeps getting 404 errors. Any permanet location we can get it from?

---

### Post by batevladi on 2012-09-14
Hi Guys! I am also getting 404 on the Stated URL. Is this driver now completely removed? 
Uname:
Linux 
Inspiron-N5110 3.2.0-30-generic #48-Ubuntu SMP 
Fri Aug 24 16:52:48 UTC 2012 
x86_64
x86_64 
x86_64 
GNU/Linux
12.04 (with the latest updates)

I cant get the alps pad to work on this inspiron n5110 - it is recognized as PS2 mouse (as all the posts show). 

xinput shows this: 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD                 id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]

Dmsg shows: 
[    1.736884] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    1.739155] mousedev: PS/2 mouse device common for all mice
[   14.888279] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input7
[31739.494179] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input12


I have tried to affect the pad with tpconfig but that did not help either. 

The driver seems to have been withdrawn, not sure if it had something to do with the issue stated in the [LP877666]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/877666") - the stick not working. It seemed that the pad was ok but the stick not... (from the feedback in the forums). Almost all tickets and posts stating some success are pointing to the .deb package. And I could not find a single ticket (neither kernel [upstream]("https://bugzilla.kernel.org/show_bug.cgi?id=23502") nor launchpad) which referred to the issue as solved (also [LP678103]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/678103")). 

So where can we get this driver to try and fix the infamous ALPS Glidepad auto click... ??](*,)

Help with the annoying ALPS glidepad!!

V

PS - we should may maybe remove the [SOLVED] tag from this post - issue is not solved.

---

### Post by Shekoufa on 2012-09-22
Grrrrrr! This problem is killing me too! It's been almost a year I'm trying to fix this problem on my Inspiron N5110! I can't believe it but I can insanely YELL that "THERE HAS BEEN NO SUCCESS YET!!" These days I can't find that .deb file anywhere, however two months ago I gave a try to that package too but it changes nothing except for after installing it with some modifications in alps.c file I have this result for the commant xinput --list: 

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]

```
A PS/2 Mouse and AlpsPS/2 ALPS GlidePoint recognized together!! And the funny part is that the ALPS GlidePoint device captures no interrupts at all! 

I am gone insane! I'm serious about! I'm a web-developer and I need to use Ubuntu in my everyday life! Yet I doubt in calling that "LIFE!" It sure ain't life!!!

---

### Post by shlomi on 2012-10-27
> **boot_sectorz said:**
> This driver is hard to find. Keeps getting 404 errors. Any permanet location we can get it from?

yes, i cannot find this driver anywhere.. can anyone post a working link please?

---

### Post by sir4taye on 2012-10-30
> **z4k4ri4 said:**
> Well here's a more cleaner approach:
```
sudo dpkg -i psmouse-alps-dkms_0.10_all.deb
sudoedit /usr/src/psmouse-alps-0.10/src/alps.c
```

Add ```
#include <linux/moduleparam.h>
```
below ```
#include <linux/slab.h>
#include <linux/input.h>
#include <linux/input/mt.h>
#include <linux/serio.h>
#include <linux/libps2.h>
```

Then finish it with: ```
sudo dkms build -m psmouse -v alps-0.10
sudo dkms install -m psmouse -v alps-0.10
```

After sudoediting, this returns this and it won't build or install....
 @laptop-Lenovo-G550:~$ sudo dkms build -m psmouse -v alps-0.10
[sudo] password for taylor: 

Error! DKMS tree does not contain: psmouse-alps-0.10
Build cannot continue without the proper tree.


Any suggestions on how to modify my tree appropriately?

I'm just trying to get my alps glidepoint to verticle scroll.

---

### Post by skilia on 2013-05-15
Have the same issue with Dell Vostro 3360, nothing is working. and I can't find the driver... Please, help me

---

### Post by skilia on 2013-05-15
What do you think about this driver [http://www.dahetral.com/public-download/alps-psmouse-dlkm-for-3-2-and-3-5/view](http://www.dahetral.com/public-download/alps-psmouse-dlkm-for-3-2-and-3-5/view) ?

---

