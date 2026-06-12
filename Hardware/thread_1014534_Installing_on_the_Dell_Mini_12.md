---
title: "Installing on the Dell Mini 12"
date: 2008-12-17
forum: Hardware
---

### Post by rigormotis on 2008-12-17
I recently bought the Dell Mini 12 (unfortunately the Vista version, ubuntu hadn't been offered yet) and have been trying to install various distros on it for quite a while but have had no success.  Dell just started selling the Ubunutu version so the laptop should support it, but I can never get the installer to load X.  I've been copying the image to a USB drive and booting from it.  It loads, but when it goes to start X it stops and simply brings up the commmand prompt.  Trying to start X the usual way ("startx") simply gives an error message along the lines of "Screen found, but none have usable configuration....Fatal server error: no screens found".

I know that this laptop has the somewhat unusual GMA 500 chipset, but if Dell is selling a Ubuntu version, there must be a way to make it work.

On a side note, I've also tried the Ubuntu Mobile version as I thought it might have better hardware support, but still no dice.

---

### Post by kylecronan on 2008-12-19
*** READ THIS *** READ THIS *** READ THIS *** READ THIS ***

Please help to keep this thread down to a manageable size.

Read the wiki first: [http://gma500.wiki-site.com](http://gma500.wiki-site.com)
Use the "Search this Thread" feature (you need to be logged in for the "Search this Thread" link to appear up top)
Try Google.
If all else fails, post your question here.

Also, consider adding the information you were looking for to the wiki.

Thank you.

*** READ THIS *** READ THIS *** READ THIS *** READ THIS ***

> **rigormotis said:**
> 
I know that this laptop has the somewhat unusual GMA 500 chipset, but if Dell is selling a Ubuntu version, there must be a way to make it work.


You would think so, wouldn't you?  No one has actually been shipped an Ubuntu-loaded Mini 12 yet.  Who knows, someone at Tungsten may still be furiously coding away.

See also this thread: [http://ubuntuforums.org/showthread.php?p=6300992](http://ubuntuforums.org/showthread.php?p=6300992)

It suggests using VESA for now (ie, adding 'Driver "vesa"' to the "Device" section of xorg.conf).  I haven't tried it yet, because I left my power adapter across town tonight.

Kyle

---

### Post by CrazyDesi on 2008-12-19
I'm sorry for coming in on your thread.  However, is there a way you could post a picture of your 12 next to something familiar to get a size comparison?  Is it really as small as the Macbook Air because if so I might be getting it! :)

---

### Post by kylecronan on 2008-12-19
CrazyDesi, just check the picture here: [http://blog.wired.com/gadgets/2008/10/dell-mini-inspi.html](http://blog.wired.com/gadgets/2008/10/dell-mini-inspi.html)

I think I found the driver (xf86-video-psb) on the moblin site:

[http://git.moblin.org/cgi-bin/gitweb/gitweb.cgi?p=projects/xf86-video-psb.git;a=summary](http://git.moblin.org/cgi-bin/gitweb/gitweb.cgi?p=projects/xf86-video-psb.git;a=summary)

This code hasn't changed in a while- maybe it's just an early dev version.  There's a lot of technical info under doc/ although I think it's outdated.  I can't tell yet if this supports DRM.

---

### Post by marduk667 on 2008-12-19
any news here? just tried to start the live-cd but it cannot start the x-server.
i have to get rid of this vista ;)

---

### Post by marduk667 on 2008-12-19
I just installed the .deb file from

[https://launchpad.net/ubuntu/intrepid/i386/xserver-xorg-video-psb/0.2.1-1ubuntu3](https://launchpad.net/ubuntu/intrepid/i386/xserver-xorg-video-psb/0.2.1-1ubuntu3)

and set this driver in the xorg.conf (also had to set IgnoreABI to true) but it still does not work, i now get an undefined symbol while starting X.

Anyone got the VESA-driver working?

---

### Post by kylecronan on 2008-12-19
Here is the real issue:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/269611](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/269611)

Intrepid has a regression that breaks support for Poulsbo.  I'm going to try Hardy now, I think it should work out of the box.

And no, VESA doesn't work because Dell neglected to initialize the VESA modes in the BIOS.

---

### Post by marduk667 on 2008-12-19
ok i will also try hardy now but first i have to download the image...is there any chance that this driver will run in jaunty? perhaps i will try the daily-live later, too

---

### Post by kylecronan on 2008-12-19
I doubt it.  The issue seems to be an incompatibility with some interface in newer kernel versions:

[http://www.linuxquestions.org/questions/linux-mobile-81/atom-processor-z5xx-series-and-intel-us15w-chipset-need-graphics-driver...-683448/](http://www.linuxquestions.org/questions/linux-mobile-81/atom-processor-z5xx-series-and-intel-us15w-chipset-need-graphics-driver...-683448/)

Perhaps we should ask the Moblin folks if they have any plans to maintain this driver.  I doubt Intel/Tungsten will ever touch it again.

---

### Post by marduk667 on 2008-12-19
hm...hardy boot-cd stops in initramfs, any idea?

---

### Post by marduk667 on 2008-12-19
the live-cd starts now, but it does not find the hard-disk to install :(

it also seems that it does not recognize the wifi, and to my surprise it starts with the vesa-driver :confused:

so i give up for now, hope you find out something new

---

### Post by kylecronan on 2008-12-19
Yikes, what a mess.  My net connection is being quite slow right now- as soon as I get this LiveCD downloaded I'll see what I can find out.

---

### Post by marduk667 on 2008-12-19
on monday i will try to contact dell, perhaps they can help...

vista is so slooooow

---

### Post by kylecronan on 2008-12-19
I was using an 8.04 CD (err, usb stick, actually).  Adding "all_generic_ide" to the kernel arguments allows it to install.  This must be some kind of kernel bug that was fixed by the time 8.10 came out.  Maybe even 8.04.1 would work, I think that's what the Dell website says they're using.  The behavior is very strange: sda cannot even be accessed by fdisk, and sdb1, the fat partition on the flash drive, doesn't mount...

---

### Post by marduk667 on 2008-12-19
i will try this with the 8.04.1 now

edit: the kernel-parameter helped, it is installing now.

still no wifi and only the 1024x768 screen resolution

---

### Post by kylecronan on 2008-12-19
Yeah I think it turns out I used 8.04.1 after all.  If you do a distribution upgrade after the install it will of course break xorg.  But I'm going to see if I can still fix it afterward, maybe manually downgrade X and the kernel. :)

---

### Post by marduk667 on 2008-12-19
I am now writing this post from the installed Ubuntu 8.04.1!

Just installing all the patches.

Sound and Bluetooth are working, the VESA driver has the wrong resolution i will look for that next. Also the Wifi driver is not loading, i also can't find the Wireless Interface in lspci, thats kind of strange as in the 8.10 live cd the wireless seemed to work (it showed up as eth1).

Well now first i will patch the system and then i will look for the problems ;)

But...it is really fast now :)

---

### Post by kylecronan on 2008-12-19
Hah!  The wireless is the Broadcom BCM4310 "USB controller".  The bcm43xx driver fails to recognize it.  Probably just needs to know some new PCI ID.

---

### Post by marduk667 on 2008-12-19
Wireless is working using this HowTo (sorry it is german):
[http://wiki.ubuntuusers.de/WLAN/Broadcom_bcm43xx?highlight=broadcom](http://wiki.ubuntuusers.de/WLAN/Broadcom_bcm43xx?highlight=broadcom)

Now i will check the display resolution problem.

---

### Post by kylecronan on 2008-12-19
from the linuxwireless site:

[INDENT]BCM 4310 USB - This device has an LP PHY. We think that means low power. In any case, previous code does not work. The reverse engineers have translated a great deal of the code and are currently generating specs for the code writers. Note: This card uses the PCI buss, despite its name.[/INDENT]

I guess ndiswrapper will have to do for now.

My guess on the resolution thing is that a tool similar to "915resolution" is needed.

---

### Post by marduk667 on 2008-12-19
i now have set the driver "psb" in the xorg.conf and it starts, but then it fails because it cannot load the psb.ko kernel driver (which it needs for dri).

I am not sure how i can get this module as it seems not to be in the modules-packages :(

but it recognizes the hardware, it also recognizes the correct resolution, it just does not start ;)

---

### Post by marduk667 on 2008-12-19
Hey what do you think about the MID Image?

[http://ftp5.gwdg.de/pub/linux/debian/ubuntu/iso/intrepid/](http://ftp5.gwdg.de/pub/linux/debian/ubuntu/iso/intrepid/)

I have not tried it but perhaps the correct driver is included?

> For devices using the Low-Power Intel Architecture, including the A1xx and Atom processors.

---

### Post by kylecronan on 2008-12-19
Try downgrading the kernel following this:

[http://linuxd.wordpress.com/2008/11/26/how-to-downgrade-the-kernel-in-ubuntu-810-the-easy-way/](http://linuxd.wordpress.com/2008/11/26/how-to-downgrade-the-kernel-in-ubuntu-810-the-easy-way/)

Which kernel version to use may require some experimentation: if we're lucky 2.6.26 will fix the SATA issue (improving performance) while still allowing psb drivers to work.

Then it should be possible to enable hardy repos to grab just the psb driver.  But X may need to be downgraded as well, I'm not sure.

Ah, a MID image, I didn't see that!  I'll check it out.

edit: or are you still at 8.04.1?  I wasn't sure what you meant by "patches", before.  If it's hardy, I don't get why X would work in the LiveCD and not after the install.

---

### Post by kylecronan on 2008-12-19
btw, does your hard drive click at all?  I've been hearing this occasionally and am worried I might have a drive that is already failing.

---

### Post by kylecronan on 2008-12-19
In other news, Intrepid fixes sound but breaks the wired NIC.  *sigh*

---

### Post by marduk667 on 2008-12-20
hey,

sorry, i went to bed last night (it was 0:30 here ;) ).

So at the moment i am still at 8.04.1 with all available hardy patches, but there is the problem with the X-Server.

And yes, i also have the clicking of the harddrive, hope it is not a defect

---

### Post by kylecronan on 2008-12-20
Hey, that's a big relief to me about the hard drive- I think it must be normal then.

I'm still trying to figure it all out, but my guess so far is that the xorg psb video drivers can be made to work with 2.6.24 by compiling the psb-kmd source package here:

[http://v1.moblin.org/build-results/projects/psb-kmd/lpia/](http://v1.moblin.org/build-results/projects/psb-kmd/lpia/)

I found that the tar.gz there and the drm-poulsbo included in ubuntu kernel sources are both much earlier versions (it will complain about not having a firmware file- could there really be a firmware image for a graphic chipset?), whereas the binary packages won't work because of the different kernel architecture.

I didn't find any psb.ko on that MID image.

---

### Post by marduk667 on 2008-12-20
I tried to boot the MID-Image but it also cant start the graphical mode as VESA fails. I will now try to compile the module!

edit: i tried the standby/hibernate, but it does not work :(

---

### Post by marduk667 on 2008-12-20
ah the forums back up.

So i tried to install the kernel module but i get symbol errors when trying to load either the new drm.ko or the psb.ko.

I try to contact the moblin irc now...

---

### Post by kylecronan on 2008-12-20
Ok, so here is info on the _actual_ latest version of the code:

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/291582](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/291582)

You have to enable hardy-proposed, fetch source with 'apt-get source', and then do a fakeroot build of the linux-ubuntu-modules-2.6.24-23-generic package.  Don't know yet- it's taking a while to compile because of some unrelated module changes, but I have high hopes this one will do it!

edit: also, it needs CONFIG_DRM_PSB=m added to the debian/config/i386 file.  This is the reason the binary package doesn't include psb.ko, even in hardy-proposed.

---

### Post by marduk667 on 2008-12-20
Ok i will try this too, not sure if i understand all that but i will try it.

As i see in the bug report, this seems to work for intrepid too?

Please keep me up2date!

---

### Post by kylecronan on 2008-12-20
There wasn't any updated 'linux-ubuntu-modules' in intrepid-proposed.  I'm not sure why it said that.

If this new DRM code works with 2.6.27, that would be great!  I'm really wondering whether Dell's image will use the same all_generic_ide hack, since all we know right now is that they made some kind of customized version of hardy, whose kernels have an issue there.  Probably by starting with the lpia stuff, rather than staying on i386 as we are attempting to do.

I don't understand the need for a new architecture- whether it's more for UMPCs or also makes sense on the 12.

---

### Post by marduk667 on 2008-12-20
previously i talked to a guy from the moblin project, he got this thing running with mandriva on a 2.6.27 kernel (he wrote a patch for it), so perhaps that could also be a solution

So did the build finish on your mini? does it work now?

---

### Post by kylecronan on 2008-12-20
No, it didn't fix it.  But I suspect there's still something wrong with my version of xorg.  I can only load psb_drv.so if I have IgnoreABI in my config file- did you have to do this?  Then I get "(EE) [drm] Could not uninstall irq handler" and X exits.

Some kind of chipset initialization is definitely taking place, though, because when I load the psb DRM it switches me over from a text console to frame buffer.

It would be useful to know if this is not working only because I upgraded most of my system to intrepid.  You should try the compile on your install.  Also, is your version of xserver-xorg-core 2:1.4.1~git20080131-1ubuntu9.2?

That's interesting about Mandriva.

---

### Post by marduk667 on 2008-12-20
I also need the IgnoreAbi!

I have to install the linux-source first, then i will start the compile.

And yes, i have the same xserver-core version

---

### Post by marduk667 on 2008-12-20
Do you know what i have to do in this case:

> The file /lib/modules/2.6.24-22-386/build/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.24-23-generic/build).


the file exists....

---

### Post by kylecronan on 2008-12-20
Btw here is the build command I used:

```
fakeroot debian/rules binary-arch arch=i386 flavours="generic"
```

At the very end, it will fail while trying to make the package.  That's alright: you can just find drm.o and psb.o and copy them to /lib/modules/2.6.24-23-generic/kernel/drivers/char/drm.  depmod -a, then modprobe.

Gotta get some sleep, best of luck!

---

### Post by kylecronan on 2008-12-20
> **marduk667 said:**
> Do you know what i have to do in this case:



the file exists....

make sure you have both the kernel-image for 2.6.24-23-generic and the linux-headers package (both from hardy-proposed, I believe).  Best to reboot into that kernel before starting the build.

---

### Post by marduk667 on 2008-12-20
it seems to work with your command, i used another one, now i hope everythings compiles.

Could you change the resolution with the vesa-driver?

So, now sleep well, what timezone are you btw?

---

### Post by marduk667 on 2008-12-20
Okay, now the build has finished and i copied the new drm and the psb module to the lib/modules.

Now the driver loads and it also starts x but it looks very strange.

on the strg+alt+f1 it changes the resolution which looks much better.

I also get the firmware-message in dmesg.

I will try my luck in #moblin again

---

### Post by marduk667 on 2008-12-20
Well the Xserver started with the vesa driver and it looked strange, if i try the psb i get the follwing in the xorg.log:

> (II) PSB(0): [drm] installed DRM signal handler
(WW) PSB(0): [drm] DRM is not compatible with this driver.
	Kernel DRM version: 4.12.0
	and I can work with versions 0.1.x - 0.x.x
	Please update either this 2D driver or your kernel DRM.
	Disabling DRI.
(EE) [drm] Could not uninstall irq handler.
(EE) [drm] Could not uninstall irq handler.
(EE) PSB(0): This driver currently needs DRM to operate.

---

### Post by marduk667 on 2008-12-20
#moblin: they say that we have to patch the libdrm, but i am absolutely not sure how. it seems that all these patches are already made in the UME, so perhaps it really would be better to use that

---

### Post by marduk667 on 2008-12-20
i found a ppa where the psb driver is maintained, try this one now

[https://launchpad.net/~ubuntu-mobile/+archive?field.name_filter=xserver-xorg-video-psb&field.status_filter=any](https://launchpad.net/~ubuntu-mobile/+archive?field.name_filter=xserver-xorg-video-psb&field.status_filter=any)

---

### Post by marduk667 on 2008-12-20
Yeeeehaaa....with the launchpad-driver it works.
It seems that this driver is also available for intrepid, so if you want to try it ;)

Be sure to use the libdrm from the ppa, otherwise it won't work.

I will now check the standby/hibernate and connect my mobile via BT

**Update:**

- Webcam works out of the box with cheese
- 3G Connection via BT/Sony Mobile works perfect
- Wireless works perfect
- X-Server with 2D works, but seems a bit slow, not really sure about that. Also not sure if there exist drivers for the 3D-Support

**Update 2**
- Suspend kills the machine on wakeup :(

---

### Post by kylecronan on 2008-12-20
That's great news!

Seems ubuntu-mobile doesn't actually have intrepid packages, though maybe they're planning for that in the future.  I tried the hardy video-psb package on my intrepid install, but it forced me to upgrade back to an incompatible version of xorg for some reason.  My system is in a highly undefined state right now, so I'll probably start over now that we know what software to use.

---

### Post by marduk667 on 2008-12-20
Well for me it's now time to go to bed again ;)

The steps now were:

- Install Hardy (8.04.1) with the all_generic_ide
- Activate the proposed Repo
- Install all patches
- build the psd.ko and the new drm.ko module from linux-ubuntu-modules-2.6.24-23
- add the psd-repo from launchpad
- install all patches from psd-repo
- activate the psd-driver in xorg.conf

That should do the trick.

Good Luck and Reading you tomorrow :)
Dennis

---

### Post by bennychee on 2008-12-22
Cool deal. That's alot of hardwork summarized.

> **marduk667 said:**
> Well for me it's now time to go to bed again ;)

The steps now were:

- Install Hardy (8.04.1) with the all_generic_ide
- Activate the proposed Repo
- Install all patches
- build the psd.ko and the new drm.ko module from linux-ubuntu-modules-2.6.24-23
- add the psd-repo from launchpad
- install all patches from psd-repo
- activate the psd-driver in xorg.conf

That should do the trick.

Good Luck and Reading you tomorrow :)
Dennis

---

### Post by marduk667 on 2008-12-22
I have opened a thread in the DELL-Forums now, waiting for an answer.

[http://en.community.dell.com/forums/p/19248008/19393966.aspx#19393966](http://en.community.dell.com/forums/p/19248008/19393966.aspx#19393966)

---

### Post by Sinsinnati on 2008-12-22
I didn't read all of the posts, but have you tried hooking up a more conventional  monitor by VGA?

---

### Post by marduk667 on 2008-12-22
Hi,

why should we connect a Monitor to the VGA?
I don't really understand that, sorry.

Regards,
Dennis

---

### Post by takoyaki on 2008-12-22
VESA worked on intrepid. but Screen size was 1024x786.

I only editted xorg.conf.

My xorg.conf is

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30.0 - 80.0
	VertRefresh	50.0 - 70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes 	"1280x800" "1024x640"
	EndSubSection
EndSection

at your own risk

I want to work Screen of 1280x800

---

### Post by kylecronan on 2008-12-22
Yep, Intrepid xorg will start up if you add the HorizSync and VertRefresh lines.  I could have sworn I'd tried this before- I guess I didn't do VertRefresh as well.

This is probably the most serious bug in Intrepid affecting the Mini 12, since it screws up the install process.  I've opened a report:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/310674](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/310674)

---

### Post by marduk667 on 2008-12-22
and is it possible to use 1280x800 with the vesa driver?

I subscribed the bug report Kyle

---

### Post by kylecronan on 2008-12-22
> **marduk667 said:**
> and is it possible to use 1280x800 with the vesa driver?

No, the only VESA modes configured in the BIOS are VGA, SVGA and XGA.

---

### Post by kylecronan on 2008-12-23
The psb DRM code will not work in its current state with the 2.6.27 kernel.  The reason (aside from trivial fixes) is mentioned in a comment in psb_fb.c:

```
/*
 * FIXME: Before kernel inclusion, migrate nopfn to fault.
 * Also, these should be the default vm ops for buffer object type fbs.
 */
```

This relates to the change in the page fault interface discussed here:

[http://lwn.net/Articles/203725/](http://lwn.net/Articles/203725/)

It doesn't look terribly complicated to migrate to the new interface- I'll give it a shot.

Kyle

---

### Post by Sinsinnati on 2008-12-23
> **marduk667 said:**
> Hi,

why should we connect a Monitor to the VGA?
I don't really understand that, sorry.

Regards,
Dennis

...Went back and read. The suggestion was for the original topic which seems to have progressed beyond getting the GUI running. 

All of the driver issues don't say much for Dell's repositories.

---

### Post by marduk667 on 2008-12-23
Hey Kyle, you could have a look at this patch i previously mentioned:

[http://people.mandriva.com/~blino/patches/psb-kmd-2.6.27.patch](http://people.mandriva.com/~blino/patches/psb-kmd-2.6.27.patch)

Perhaps it helps.

---

### Post by kylecronan on 2008-12-24
Thank you, Dennis.  That was exactly what I needed to get the kernel module working with 2.6.27.  Of course, there was a bunch more to figure out before it actually worked with Xorg!  Here are my notes from the process:

```

shrink vista volume as much as possible and delete recovery partition
boot livecd from USB MSD (unetbootin ubuntu 8.10):
sudo /bin/bash
sed -i 's/"Device"/"Device"\nDriver "vesa"/;s/"Monitor"/"Monitor"\nHorizSync 30-80\nVertRefresh 50-70/' /etc/X11/xorg.conf
killall gdm ; sleep 10
gdm
complete install as usual

install updates and reboot, connect wireless
DRM module:
wget http://archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.24/linux-ubuntu-modules-2.6.24_2.6.24-23.36.tar.gz
tar zxvf linux-ubuntu-modules*.tar.gz
wget http://people.mandriva.com/~blino/patches/psb-kmd-2.6.27.patch
sudo aptitude install patch
patch -d lum/ubuntu/media/drm-poulsbo -p1 < psb-kmd-2.6.27.patch
cd lum/ubuntu/media/drm-poulsbo
sed -i 's/u*ret = NOPFN_REFAULT.*\n/unsigned long ret = VM_FAULT_NOPAGE;/;s/NOPFN_SIGBUS/VM_FAULT_SIGBUS/g;s/NOPFN_REFAULT/VM_FAULT_NOPAGE/g;727D;728D;729D' drm_vm.c
sed -i '36a#include <asm/cacheflush.h>' psb_drv.c
sed -i 's/change_page_attr/set_pages_uc/g;s/, PAGE_KERNEL_NOCACHE//g' psb_drv.c
make -C /lib/modules/2.6.27-9-generic/build M=`pwd` CFLAGS=-UDRM_IDR_COMPAT_FN
sudo cp drm.ko psb.ko /lib/modules/2.6.27-9-generic/kernel/drivers/gpu/drm/
sudo depmod -a

xorg driver:
sudo sh -c 'echo deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted >> /etc/apt/sources.list'
sudo sh -c 'echo deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted >> /etc/apt/sources.list'
sudo sh -c 'echo deb http://ppa.launchpad.net/ubuntu-mobile/ubuntu/ hardy main >> /etc/apt/sources.list'
sudo apt-get update
sudo aptitude install xserver-xorg-video-psb (say 'n' to first solution; say 'Y' to second)
sudo aptitude install xserver-xorg-video-psb (this time say 'Y' to first solution)
sudo dpkg --force-all -r xserver-xorg-video-ati
sudo aptitude install xserver-xorg-video-psb (one more time)
wget http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/libd/libdrm/libdrm2_2.3.0.16-0ubuntu2~804um3_i386.deb
sudo dpkg -i libdrm2*.deb

xorg.conf:
sudo sed -i 's/vesa/psb/' /etc/X11/xorg.conf
reboot

```

It seems to have messed up my keyboard (the arrow keys and some others don't work).  But I've finally got full screen resolution on Intrepid, so no need for all_generic_ide.  The keyboard thing is probably just some package that is the wrong version.

glxgears gets 96 fps- not bad.

---

### Post by kylecronan on 2008-12-25
I was able to get the keyboard working by adding this to xorg.conf:

```

Section "ServerFlags"
        Option "AutoAddDevices" "no"
EndSection

Section "InputDevice"
        Identifier "Keyboard0"
        Driver "evdev"
        Option "Device" "/dev/input/event1"
        Option "XkbModel" "evdev"
        Option "XkbRules" "xorg"
EndSection

```

Although this seems to break setxkbmap.

---

### Post by runoo on 2008-12-25
hi!

I did the steps

add 
   sudo apt-get install patch

changing

  sudo sh -c 'echo deb [http://ppa.launchpad.net/ubuntu-mobile](http://ppa.launchpad.net/ubuntu-mobile) hardy main >> /etc/apt/sources.list'

  sudo dpkg -r xserver-xorg-video-ati

with this

   sudo sh -c 'echo deb [http://ppa.launchpad.net/ubuntu-mobile/ubuntu/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/) hardy main >> /etc/apt/sources.list'

sudo dpkg -r xserver-xorg-video-ati xserver-xorg-video-all

all ok, but when reboot:

Starting GNOME Display Manager..
Starting System Tools Backends system-tools-backends
Starting anac(h)ronistic cron anacron
Starting deferred execution scheduler atd
Starting periodic command scheduler crond
Enabling additional executable binary formats binfmt-support

halt on in >>>>>>>  Checking battery state...                          

any ideas?

---

### Post by kylecronan on 2008-12-26
runoo, did you definitely get the xserver-xorg-video-psb package installed?  Also, when you boot, can you at least switch to a text console (press alt-F1)?  If so, post a copy of /var/log/gdm/:0.log.1.

If you are having trouble installing xserver-xorg-video-psb, you can also download it directly from ppa.launchpad.net and install it with 'dpkg --force-all -i'.  Make sure you have the xorg from Hardy properly installed though.

---

### Post by marduk667 on 2008-12-27
Kyle, thanks for all your help, perhaps i will reinstall the mini next week with Intrepid

---

### Post by rolfepope on 2008-12-27
So has anybody gotten an install to work on the Mini 12?

I cannot find the 8.04 download on the dell site.

If one were to do an 8.04 install from a dell image, could you then do the 8.10 upgrade process?

Thanks guys.

Rolfe Pope

---

### Post by kylecronan on 2008-12-27
I had much better results when I installed 8.10 directly than when I upgraded.  For instance, the wireless drivers don't seem to work after an upgrade, even though 8.10 has a compatible version of Broadcom's STA driver.

To get 8.10 to install, though, you have to make some changes to /etc/X11/xorg.conf.  Just follow the instructions in those notes I posted.

---

### Post by kylecronan on 2008-12-27
The one thing I still can't get to work is AIGLX, which means no compiz visual effects.  FYI, I posted to the moblin-dev list about this:

[http://marc.info/?l=moblin-dev&m=123043465414564&w=2](http://marc.info/?l=moblin-dev&m=123043465414564&w=2)

---

### Post by floquet on 2008-12-29
First of all thanks to kylecronan for the great process to install ubuntu on the Mini 12.
I've followed it and I have had the same problem that runoo. After rebooting the system halts on "checking the battery state".
I think that the problem is generated when running the patching. Some errors appear.

```
patching file Makefile 
Hunk #1 FAILED at 295.
1 out of 1 hunk FAILED -- saving rejects to file Makefile.rej
patching file drmP.h
patching file drm_agpsupport.c
patching file drm_compat.c
patching file drm_compat.h
patching file drm_ttm.c
patching file drm_vm.c
Hunk #16 FAILED at 723.
1 out of 22 hunks FAILED -- saving rejects to file drm_vm.c.rej
patching file psb_fb.c
```

---

### Post by marduk667 on 2008-12-30
has anybody used suspend2ram successfully?

---

### Post by kylecronan on 2008-12-30
Suspend2ram doesn't work for me either.

Floquet and runoo, thanks for being beta testers ;)
The fix is to add "CFLAGS=-UDRM_IDR_COMPAT_FN" to the "make" line, where you build the kernel modules.  I'm not sure why I didn't have to do this the first time around.  (Btw, those patch errors are expected- I work around them with the call to sed that follows)

I've updated the notes back on page 6.

---

### Post by floquet on 2008-12-31
Hi Kilecronan

Thanks a lot for the answer. I'll try as soon as I finish downloading the ubuntu8.10. I've lost my previous iso file. 

One more question. Should we enable the ubuntu-proposed repositories before doing the system update at the end of the first step of the installation?. I've read that there are some improvements-fixes in the poulsbo drm modules in the ubuntu-proposed repositories.

Floquet

---

### Post by kylecronan on 2008-12-31
As far as I can tell, Intrepid's ubuntu-proposed doesn't have anything relevant to the Poulsbo hardware.  Only Hardy.

---

### Post by floquet on 2009-01-01
Hi Kilecronan

I still can not make the x to work. Attached the 0.log from xorg
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux aurora-nettop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan  1 11:19:12 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) PSB: Failed to load module "Xpsb" (module does not exist, 0)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
WARNING: Error inserting drm (/lib/modules/2.6.27-9-generic/kernel/drivers/gpu/drm/drm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting psb (/lib/modules/2.6.27-9-generic/kernel/drivers/gpu/drm/psb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
(EE) [drm] drmOpen failed.
(EE) PSB(0): [dri] DRIScreenInit failed. Disabling DRI.
(EE) [drm] Could not uninstall irq handler.
(EE) PSB(0): This driver currently needs DRM to operate.

Fatal server error:
AddScreen/ScreenInit failed for driver 0


```

It seems that it is not able to load the drm and the psb modules.

---

### Post by kylecronan on 2009-01-01
Hmmm, try running 'modprobe drm' and then 'dmesg'.  Does it complain about incorrect versions of 'idr_for_each' and 'idr_remove_all'?  Did you start over completely or just recompile the modules?  If you just recompiled, make sure to 'rm *.o' before running the make command again.

Or if you want to PM me with your email address I'll send you my drm.ko and psb.ko binaries.

---

### Post by floquet on 2009-01-02
Thanks Kilecronan.

It works!. Installing the right psb.ko and drm.ko the system is able to initialize x and gdm.

It was mentioned in some previous posts that the suspend-to-ram did not work. Suprisingly it works for me. I do not use the susp2ram program but the /usr/sbin/pmi action sleep script. I'm able to suspend and resume the system with no problems.

---

### Post by kylecronan on 2009-01-02
Somehow the suspend to RAM is working totally normally for me now...  Even with a KVM virtual machine running!  The Intel VT stuff is a great feature of the new Atom in the Mini 12.

---

### Post by marduk667 on 2009-01-03
Well if Suspend works in Intrepid i will do a reinstall on monday

---

### Post by jabronioh on 2009-01-04
Kylecronan,
I am having the same issue as floquet. Would you send me the two binaries as well?
[email]kdove2oh@yahoo.com[/email]
Thanks

---

### Post by marduk667 on 2009-01-05
Ok i am just reinstalling Ubuntu Intrepid and have the same problem with X as the others.

Do we make any mistake in building the drm-kernel-module?
I also have the unknow symbol (idr_remove_all, idr_for_each)

It seems the CFLAGS=-UDMR_IDR.... does not work

Edit 2: I got it, you have to remove the EXPORT_SYMBOL for the idr_for_each and idr_remove_all

Another question: Qhat about the updates now? It immediately wants to update libdrm2 and some x-packages now but i think i should not do it, how did you solve this?

Edit 3: The scrolling function of the touchpad does not work, any idea of how to solve that?

---

### Post by marduk667 on 2009-01-05
I have the touchpad running, had to insert it in the xorg.conf.
But, when i press the UP button on the keyboard it opens the screenshot dialog.

Also i don't know what to do with the updates

---

### Post by kylecronan on 2009-01-05
See post #59: that should fix the keyboard.

You are correct that those updates should not be allowed to run.  I think they could be masked from the updater with some calls to dpkg.  See this page:

[http://www.debian-administration.org/articles/67](http://www.debian-administration.org/articles/67)

But with the exception of X, you should be current now.  To run a newer version of xorg, as I understand it- that will have to wait for some changes in xf86-video-psb.

---

### Post by marduk667 on 2009-01-05
Hi Kyle,

this is what i have in my xorg.conf now:

```
ection "Device"
	Identifier	"Configured Video Device"
	Driver "psb"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync 30-80
	VertRefresh 50-70
EndSection

Section "InputDevice"
	Identifier "Keyboard0"
	Driver "evdev"
	Option "Device" "/dev/input/event1"
	Option "XkbModel" "evdev"
	Option "XkbRules" "xorg"
	Option "XkbLayout" "de"
	Option "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Protocol"              "autodev"
        Option          "SHMConfig"             "on"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Keyboard0"
        InputDevice     "Synaptics Touchpad" "CorePointer"
EndSection

Section "ServerFlags"
	Option "AutoAddDevices" "no"
EndSection

```

But it does not work, every key is alright but not the UP button

---

### Post by kylecronan on 2009-01-05
Oh, it's _just_ the up key.  Hmm, it's probably because of your German keyboard layout.  I had similar problems actually, when I was trying to use the dvorak layout.  Seems that xorg forces you to use the evdev keyboard driver when psb is present.  And evdev is extremely buggy when it comes to any sort of "alternative" layout (you'll notice that the gnome keyboard settings are completely broken with evdev).  I don't know of any fix for this.  You might want to try posting to the xorg mailing list- somebody ought to be able to tell you how to do a manual xmodmap or something, to fix that one key.

I'll be interested to see how Dell dealt with this issue in their Ubuntu install.  If anyone out there has gotten their Ubuntu Mini 12 already, let us know!

---

### Post by marduk667 on 2009-01-06
[http://en.community.dell.com/forums/p/19248008/19403438.aspx#19403438](http://en.community.dell.com/forums/p/19248008/19403438.aspx#19403438)

---

### Post by jabronioh on 2009-01-06
I had the same problem as Marduk with the keyboard. However, when I used Kyles changes, it worked fine.

I have a Dell Ubuntu mini 12. I used this website to install 8.10 on another partition because I hoped it would run faster, but it is not much better. Eventually, I will do a complete new install with 8.10 and format the entire drive, which may gove me better performance.

Here is the xorg.conf file that came with Dell's 8.04.1:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode 0666
EndSection

---

### Post by kylecronan on 2009-01-06
Hi Jabronioh, would be great if you could post your /var/log/Xorg.0.log file from the Dell Ubuntu install (it's long, but just put it in a code block).  Oh, and please post the output of "uname -a" and "glxinfo | grep render"!  Thanks, Kyle

---

### Post by jabronioh on 2009-01-06
Log file:

```

(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan  6 15:55:13 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ce8e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,8100 card 1028,02b1 rev 06 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,8108 card 1028,02b1 rev 06 class 03,00,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,811b card 1028,02b1 rev 06 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,8110 card 0000,0000 rev 06 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,8112 card 0000,0000 rev 06 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,8114 card 1028,02b1 rev 06 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,8115 card 1028,02b1 rev 06 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,8116 card 1028,02b1 rev 06 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,8117 card 1028,02b1 rev 06 class 0c,03,20 hdr 00
(II) PCI: 00:1f:0: chip 8086,8119 card 1028,02b1 rev 06 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,811a card 1028,02b1 rev 06 class 01,01,80 hdr 00
(II) PCI: 02:00:0: chip 10ec,8136 card 1028,02b1 rev 02 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 14e4,4315 card 14e4,04b5 rev 01 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd8400000 - 0xd84fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xd80fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation unknown chipset (0x8108) rev 6, Mem @ 0xd8100000/19, 0xd0000000/27, 0xd8380000/17, I/O @ 0x1800/3
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[1] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[2] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[3] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[4] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[5] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[10] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[11] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[12] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[13] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[1] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[2] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[3] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[4] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[5] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[10] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[11] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[12] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[13] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[5] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[6] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[7] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[8] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[9] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[16] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[17] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[18] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[19] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched psb from file name psb.ids in autoconfig
(==) Matched psb for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "psb"
(II) Loading /usr/lib/xorg/modules/drivers//psb_drv.so
(II) Module psb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.14.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) Debug: psbSetup
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) PSB: driver for Intel GMA500 chipsets: Intel GMA500
(II) Primary Device is: PCI 00:02:0
(II) Debug: psbProbe
(--) Assigning device section with no busID to primary device
(--) Chipset Intel GMA500 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[5] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[6] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[7] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[8] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[9] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[16] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[17] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[18] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[19] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) PSB(0): Debug: Allocating new device
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[5] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[6] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[7] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[8] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[9] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[18] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[19] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[20] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[21] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[22] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) PSB(0): Debug: psbPreInit
(II) PSB(0): psb_drv - 2.2.0.32L.0020
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) PSB(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) PSB(0): Depth 24, (==) framebuffer bpp 32
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(--) PSB(0): Linear framebuffer at 0x0
(==) PSB(0): RGB weight 888
(==) PSB(0): Default visual is TrueColor
(==) PSB(0): Use hardware cursor.
(==) PSB(0): Using ACPI for LVDS detection.
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so
(II) PSB(0): Debug: psbPreinitXpsb
(II) Loading sub module "Xpsb"
(II) LoadModule: "Xpsb"
(II) Loading /usr/lib/xorg/modules/drivers//Xpsb.so
(II) Module Xpsb: vendor="Tungsten Graphics Inc."
	compiled for 1.4.0.90, module version = 0.1.0
(II) PSB(0): Debug: psbDeviceScreenInit
(II) PSB(0): Debug: Initializing device
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) PSB(0): Debug: MMIO virtual address is 0xb7ae0000
(--) PSB(0): Mapped PCI MMIO at physical address 0xd8100000
	with size 512 kiB
(--) PSB(0): Detected 8060 kiB of "stolen" memory set aside as video RAM.
(--) PSB(0): Mapped graphics aperture at physical address 0x3f800000
	with size 7 MiB
(II) PSB(0): Debug: DRM device init
(II) PSB(0): Poulsbo MemClock 533, CoreClock 200
(II) PSB(0): Poulsbo Latencies 324 744 210 450
(II) PSB(0): sku_value is 0x00800000, sku_bSDVOEnable is 1, sku_bMaxResEnableInt is 0
(II) PSB(0): Debug: psbInitOutputs
(II) PSB(0): Debug: psbLVDSInit
(II) PSB(0): Output LVDS0 using monitor section Configured Monitor
(II) Debug: i830_psbOutputInit
(II) PSB(0): I2C bus "LVDSBLC_B" initialized.
(II) PSB(0): I2C bus "LVDSDDC_C" initialized.
(II) PSB(0): I2C device "LVDSBLC_B:BLC Control" registered at address 0x58.
(II) PSB(0): Debug: i830_psbDDCGetModes
(II) PSB(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.10  1280 1328 1360 1419  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) PSB(0): initializing int10
(WW) PSB(0): Bad V_BIOS checksum
(II) PSB(0): Primary V_BIOS segment is: 0xc000
(II) PSB(0): VESA BIOS detected
(II) PSB(0): VESA VBE Version 3.0
(II) PSB(0): VESA VBE Total Mem: 8000 kB
(II) PSB(0): VESA VBE OEM: Intel(r)Poulsbo Graphics Chip Accelerated VGA BIOS
(II) PSB(0): VESA VBE OEM Software Rev: 1.0
(II) PSB(0): VESA VBE OEM Vendor: Intel Corporation
(II) PSB(0): VESA VBE OEM Product: Intel(r)Poulsbo Graphics Controller
(II) PSB(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) PSB(0): Found panel mode in BIOS VBT tables:
(II) PSB(0): Modeline "1280x800"x0.0   70.10  1280 1328 1360 1419  800 803 809 823 (49.4 kHz)
(II) PSB(0): BLC Data in BIOS VBT tables: datasize=0 paneltype=13                      type=0x00 pol=0x01 freq=0x00c8 minlevel=0x00                         i2caddr=0x58 cmd=0xaa 
(WW) PSB(0): BIOS panel mode data doesn't match probed data, continuing with probed.
(II) PSB(0): BIOS mode:
(II) PSB(0): Modeline "1280x800"x0.0   70.10  1280 1328 1360 1419  800 803 809 823 (49.4 kHz)
(II) PSB(0): probed mode:
(II) PSB(0): Modeline "1280x800"x0.0   70.10  1280 1328 1360 1419  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) PSB(0): Lid state timer is enabled!
(II) Debug: i830_psbPtrAddToList
(II) PSB(0): Debug: i830_psbSDVOInit
(II) PSB(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) PSB(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) PSB(0): I2C bus "SDVOB DDC Bus" initialized.
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: sdvo_get_capabilities, caps.output_flags=3e
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 12 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Output SDVO-1 has no monitor section
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 10 00                      (i830_SDVO_CMD_SET_TARGET_INPUT)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 1D                         (i830_SDVO_CMD_GET_INPUT_PIXEL_CLOCK_RANGE)
(II) PSB(0): SDVO: R: C4 09 74 40             (Success)
(II) PSB(0): SDVO device VID/DID: 02:42.02, clock range 25.0MHz - 165.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
(II) Debug: i830_psbPtrAddToList
(II) Debug: i830_psbOutputCompat
(II) PSB(0): Debug: i830_psbOutputTypesToIndex
(II) PSB(0): Debug: Output crtc mask is 0x00000002, compat mask is 0x00000001
(II) PSB(0): Debug: i830_psbOutputTypesToIndex
(II) PSB(0): Debug: Output crtc mask is 0x00000001, compat mask is 0x00000002
(II) PSB(0): Debug: xxi830_psbInitCrtcs
(II) PSB(0): Debug: xxi830_psbCrtcInit
(II) PSB(0): Debug: xxi830_psbCrtcInit
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 0 as available for all screens.
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 1 as available for all screens.
(II) PSB(0): Debug: psbDeviceFinishInit
(II) Debug: Really running psbDeviceFinishInit
(++) PSB(0): i830_psbSaveHWState
(II) PSB(0): Debug: xxi830_psbOutputSave
(II) PSB(0): Debug: psbLVDSSave
(II) PSB(0): Debug: xxi830_sdvo_save
(II) PSB(0): Debug: SDVO: W: 20                         (i830_SDVO_CMD_GET_CLOCK_RATE_MULT)
(II) PSB(0): SDVO: R: 01                      (Success)
(II) PSB(0): Current clock rate multiplier: 1
(II) PSB(0): Debug: SDVO: W: 04                         (i830_SDVO_CMD_GET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug:  --save_active_outputs is 0
(II) PSB(0): Debug: SDVO: W: 10 00                      (i830_SDVO_CMD_SET_TARGET_INPUT)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 12                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 13                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART2)
(II) PSB(0): SDVO: R: 00 00 00 00 16 20 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 11 00 00                   (i830_SDVO_CMD_SET_TARGET_OUTPUT)
(II) PSB(0): SDVO: R:                         (Invalid arg)
(II) PSB(0): Debug: SDVO: W: 18                         (i830_SDVO_CMD_GET_OUTPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Target not specified)
(II) PSB(0): Debug: SDVO: W: 06 00 00 00 00             (i830_SDVO_CMD_GET_IN_OUT_MAP)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 0.
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 1.
(==) PSB(0): Shadow framebuffer disabled
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) PSB(0): Acceleration enabled
(==) PSB(0): [EXA] Allocate 32768 kiB for EXA pixmap cache.
(==) PSB(0): [EXA] Allocate 4 kiB for scratch memory.
(II) Debug: i830_psbOutputAssignToScreen
(II) PSB(0): Output "SDVO-1" is assigned to this screen.
(II) Debug: i830_psbOutputAssignToScreen
(II) PSB(0): Output "LVDS0" is assigned to this screen.
(II) PSB(0): Searching for matching Poulsbo mode(s):
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.10  1280 1328 1360 1419  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Target not specified)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Output LVDS0 connected
(II) PSB(0): Output SDVO-1 disconnected
(II) PSB(0): Output LVDS0 using initial mode 1280x800
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 0 as available for all screens.
(II) Debug: i830_psbOutputDisableCrtcForOtherScreens
(II) Debug: Grabbing crtc 1 for screen 0
(==) PSB(0): Using gamma correction (1.0, 1.0, 1.0)
(**) PSB(0): Display dimensions: (260, 160) mm
(**) PSB(0): DPI set to (125, 203)
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd8380000 - 0xd839ffff (0x20000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] 0	0	0xd8100000 - 0xd817ffff (0x80000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[8] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[9] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[10] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[11] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[12] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] 0	0	0x00001800 - 0x00001807 (0x8) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[22] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) PSB(0): Debug: psbScreenInit
(II) PSB(0): Debug: psbDRIScreenInit with the firefox fix
(II) PSB(0): Debug: SAREA size is 8192
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:0:2:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "psb" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) PSB(0): [drm] Using the DRM lock SAREA also for drawables.
(II) PSB(0): [drm] framebuffer handle = 0x3f800000
(II) PSB(0): [drm] added 1 reserved context for kernel
(II) PSB(0): X context handle = 0x1
(II) PSB(0): [drm] Allocated device DRM context 2.
(II) [drm] Irq handler installed for IRQ 17.
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: Shadow
(II) PSB(0): Debug: Calling fbScreenInit.
(II) PSB(0): Debug: Fix up visuals.
(II) PSB(0): Debug: fbPictureInitInit
(II) EXA(0): Offscreen pixmap area of 33554432 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II) PSB(0): Debug: Backing store
(==) PSB(0): Backing store disabled
(==) PSB(0): Silken mouse enabled
(II) PSB(0): DPMS enabled
(WW) PSB(0): Option "UseFBDev" is not used
(II) PSB(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) PSB(0): Debug: psbLVDSCreateResources
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: psbLVDSSetProperty  panelfitting 0
(II) PSB(0): Debug: SDVO: W: 27                         (i830_SDVO_CMD_GET_SUPPORTED_TV_FORMATS)
(II) PSB(0): SDVO: R: FF FF FF FF FF 1F       (Success)
(II) PSB(0): Debug: SDVO: W: 84                         (II) PSB(0): SDVO: R: FA DF                   (Success)
(II) PSB(0): Debug: SDVO: W: 61                         (II) PSB(0): SDVO: R: 00 00 00 00             (Target not specified)
(II) PSB(0): Debug: SDVO: W: 67                         (II) PSB(0): SDVO: R: 00 00 00 00             (Target not specified)
(II) PSB(0): Debug: TVStandard is 1, TVStdBitmask is 1
(II) PSB(0): Debug: i830_sdvo_set_tvoutputs_formats, format is NTSC_M
(II) PSB(0): Debug: SDVO: W: 5A 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_hue, hue is 0
(II) PSB(0): Debug: SDVO: W: 5D 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_brightness, brightness is 0
(II) PSB(0): Debug: SDVO: W: 60 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_contrast, contrast is 0
(II) PSB(0): Debug: SDVO: W: 63 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_horzontal_overscan, x overscan is 0
(II) PSB(0): Debug: i830_sdvo_set_vertical_overscan, y overscan is 0, status is 144
(II) PSB(0): [DRI] installation complete
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: Buffer 0 rotation 0 handle 0xb630ea04
Xpsb - 2.2.0.32L.0020
(II) PSB(0): [Xpsb] Started kernel request thread.
(II) PSB(0): Xpsb extension for 3D engine acceleration enabled.
(II) PSB(0): Set up textured video
(II) PSB(0): Xv video acceleration enabled.
(II) PSB(0): Initializing HW Cursor.
(II) PSB(0): Debug: psbEnterVT 1
(EE) PSB(0): has_fbdev is false
(++) PSB(0): i830_psbSaveHWState
(II) PSB(0): Debug: xxi830_psbOutputSave
(II) PSB(0): Debug: psbLVDSSave
(II) PSB(0): Debug: xxi830_sdvo_save
(II) PSB(0): Debug: SDVO: W: 20                         (i830_SDVO_CMD_GET_CLOCK_RATE_MULT)
(II) PSB(0): SDVO: R: 01                      (Success)
(II) PSB(0): Current clock rate multiplier: 1
(II) PSB(0): Debug: SDVO: W: 04                         (i830_SDVO_CMD_GET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug:  --save_active_outputs is 0
(II) PSB(0): Debug: SDVO: W: 10 00                      (i830_SDVO_CMD_SET_TARGET_INPUT)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 12                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 13                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART2)
(II) PSB(0): SDVO: R: 00 00 00 00 16 20 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 11 00 00                   (i830_SDVO_CMD_SET_TARGET_OUTPUT)
(II) PSB(0): SDVO: R:                         (Invalid arg)
(II) PSB(0): Debug: SDVO: W: 18                         (i830_SDVO_CMD_GET_OUTPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Target not specified)
(II) PSB(0): Debug: SDVO: W: 06 08 E8 69 B9             (i830_SDVO_CMD_GET_IN_OUT_MAP)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 0.
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 1.
(II) PSB(0): Debug: psbSetVGAOff
(II) PSB(0): Debug: i830_psbCrtcSetupCursors
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 0 ARGB addresses 0x3fe40000, 0x00000000
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 1 ARGB addresses 0x3fe45000, 0x00000000
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0xc0000008
(II) Debug: Pipe B PLL 0xd8027203
(II) Debug: Pipe B Enabled 0x80000000
(II) PSB(0): Debug: BLCType=0 Backlightg level = 0
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 0
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): Debug: xxi830_psbCrtcLock
(II) PSB(0): Debug: psbLVDSModeFixup
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 0 as available for all screens.
(II) Debug: i830_psbOutputDisableCrtcForOtherScreens
(II) Debug: Grabbing crtc 1 for screen 0
(II) PSB(0): Debug: xxi830_psbCrtcModeFixup, NULL
(II) PSB(0): Debug: i830_psbOutputPrepare, output->dpms,off
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0x08000001
(II) Debug: Pipe B PLL 0x58027203
(II) Debug: Pipe B Enabled 0x00000000
(II) PSB(0): Debug: BLCType=0 Backlightg level = 0
(II) PSB(0): Debug: xxi830_psbCrtcPrepare
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): Debug: xxi830_psbCrtcModeSet
(II) PSB(0): Debug: i830_psbCrtcModeSet
(II) PSB(0): Debug: chosen: dotclock 69942 vco 1958400 ((m 102, m1 17, m2 5), n 3, (p 28, p1 2, p2 14))
(II) PSB(0): Debug: clock regs: 0xd8027200, 0x00031105
(II) PSB(0): Debug: psbPipeSetBase
(II) PSB(0): Debug: psbLVDSModeSet
(II) PSB(0): Debug: xxi830_psbCrtcCommit, crtc->dpms
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS On / Sb /SS 
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: i830_psbOutputCommi, output->dpms, ont
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0x48000001
(II) Debug: Pipe B PLL 0xd8027200
(II) Debug: Pipe B Enabled 0x80000000
(II) Debug: psbLVDSSetPanelPower: lidState= 0
(II) PSB(0): Debug: BLCType=0 Backlightg level = 100
(II) PSB(0): Debug: xxi830_psbCrtcUnlock
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 0
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): xxi830_Output configuration:
(II) PSB(0):   Pipe A is off
(II) PSB(0):   Display plane A is now disabled and connected to pipe A.
(II) PSB(0):   Pipe B is on
(II) PSB(0):   Display plane B is now enabled and connected to pipe B.
(II) PSB(0):   Output LVDS0 is connected to pipe B
(II) PSB(0):   Output SDVO-1 is connected to pipe none
(II) PSB(0): Debug: psbAdjustFrame
(II) PSB(0): Debug: psbPipeSetBase
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:0:2:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/psb_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) PSB(0): Setting screen physical size to 261 x 163
(II) PSB(0): Debug: psbXf86CrtcResize 1280 800
(II) PSB(0): Debug: i830_psbCrtcSaveCursors
(II) PSB(0): Debug: i830_psbCrtcHWCursorSave
(II) PSB(0): Debug: i830_psbCrtcHWCursorSave
(II) Debug: psbScanoutDestroy
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: Buffer 0 rotation 0 handle 0x1d9cd004
(II) PSB(0): Debug: i830_psbCrtcSetupCursors
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 0 ARGB addresses 0x3fbe8000, 0x00000000
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 1 ARGB addresses 0x3fbed000, 0x00000000
(II) PSB(0): Debug: psbAdjustFrame
(II) PSB(0): Debug: psbPipeSetBase
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event5
(**) Option "Device" "/dev/input/event5"
(**) Option "SHMConfig" "true"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event5
(**) Option "Device" "/dev/input/event5"
(--) Synaptics Touchpad touchpad found
(II) PSB(0): Debug: psbSaveScreen
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS On / Sb /SS 
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0xc0000008
(II) Debug: Pipe B PLL 0xd8027200
(II) Debug: Pipe B Enabled 0x80000000
(II) Debug: psbLVDSSetPanelPower: lidState= 0
(II) PSB(0): Debug: BLCType=0 Backlightg level = 100
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.10  1280 1328 1360 1419  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.10  1280 1328 1360 1419  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.10  1280 1328 1360 1419  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.10  1280 1328 1360 1419  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.10  1280 1328 1360 1419  800 803 809 823 -hsync -vsync (49.4 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "AUO", prod id 14100
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
SetGrabKeysState - disabled
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
(II) PSB(0): Debug: psbLoadPalette
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x82102e8 
(II) PSB(0): Debug: xxi830_psbCrtcGammaSet
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210d80 
SetGrabKeysState - enabled


```

---

### Post by jabronioh on 2009-01-06
uname:

Linux ken 2.6.24-19-lpia #1 SMP Mon Nov 3 15:25:26 UTC 2008 i686 GNU/Linux

GLXINFO:

direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) GMA500 20080421 - 2.2.0.32L.0020 x86/MMX/SSE2

---

### Post by kylecronan on 2009-01-06
That's great, thanks.  Interesting- looks like they used the lpia kernel from Ubuntu Mobile but kept the architecture as i686.  I see that the DRM kernel module has the same version as what we're using.  The Xorg video driver also has the same module version. 

You have at least one file that would be helpful to those of us without this image preinstalled.  It is /usr/lib/dri/psb_dri.so.  Check and see if there's a LICENSE file in that directory, or maybe one for the whole distribution in / or /etc or something.  I would hope that Dell would not have a problem with redistribution of this part of the driver.  However, IANAL and I certainly am not asking you to perhaps post that file to imagehost.org and provide a link. ;)

Oh and as to your question about performance, I don't think that your partition size will have much effect on that.  I can only suggest the usual stuff: disable search indexing, maybe use a lightweight window manager, etc.

---

### Post by jabronioh on 2009-01-06
PSB_DRI.SO

[here:]("<a target="_blank" href="http://e.imagehost.org/download/0337/psb_dri">psb_dri.so (2.4 MB)</a>")

Download

[http://e.imagehost.org/download/0337/psb_dri](http://e.imagehost.org/download/0337/psb_dri)

Not sure this is the right License...

[http://e.imagehost.org/0300/Binary_License.txt](http://e.imagehost.org/0300/Binary_License.txt)

---

### Post by brteag00 on 2009-01-07
Actually, according to [https://wiki.ubuntu.com/mobile-hw-decode]("https://wiki.ubuntu.com/mobile-hw-decode"), there are three closed-source bits to enable accelerated 3D and video decode on the Poulsbo chipset.  The first is psb_dri.so, above.  The second is a sub-module for psb_drv.so: it's installed at /usr/lib/xorg/modules/drivers/Xpsb.so.  The final bit is the driver firmware that's loaded by the psb.ko kernel module: it's installed at /lib/firmware/<something>/msvdx_fw.bin.  I also purchased an early Mini 12, and promptly nuked the Vista installation - but now I'm pining away for good 3D and video support.

Yes, this seems a tad bit sketchy from a legal standpoint, though the license you posted explicitly allows binary redistribution.  (I'd love to find an official source for those binaries, though.)  I'm working on pulling the same stuff out of the Intel embedded graphics driver package - I'll post if I have any success.

Also, about the hard-drive clicking - it seems to be related to the drive's power management settings.  If I run "sudo hdparm -B 254 /dev/sda", the clicking goes away.  Of course, this turns off all power management and the drive never spins down - not good for battery life!  I'm hoping a BIOS upgrade (or maybe an upgraded kernel - have to try the 2.6.27 patch above) fixes it.

---

### Post by marduk667 on 2009-01-07
jabronioh: Could you also post the firmware file and the Xpsb.so? That would be absolutely great :)

@brteag00: The 2.6.27-kernel does not fix the harddrive clicking

---

### Post by jabronioh on 2009-01-07
Xpsb.so

[http://e.imagehost.org/download/0532/Xpsb](http://e.imagehost.org/download/0532/Xpsb)

msvdx_fw.bin

[http://e.imagehost.org/download/0820/msvdx_fw](http://e.imagehost.org/download/0820/msvdx_fw)

---

### Post by marduk667 on 2009-01-07
Thank you very much :)

I went a bit in the upgrade procedure of intrepid and this what you have to do to force the needed paket-versions:

- Create a file /etc/apt/preferences

- Fill in the following:

```
Package: libdrm2
Pin: version 2.3.0.16-0ubuntu2~804um3
Pin-Priority: 1000

Package: x11-common
Pin: version 1:7.3+10ubuntu10.2
Pin-Priority: 1000

Package: xserver-xorg-core
Pin: version 2:1.4.1~git20080131-1ubuntu9
Pin-Priority: 1000

Package: xserver-xorg
Pin: version 1:7.3+10ubuntu10.2
Pin-Priority: 1000

Package: xserver-xorg-input-evdev
Pin: version 1:1.2.0-1ubuntu2
Pin-Priority: 1000

Package: xserver-xorg-input-kbd
Pin: version 1:1.2.2-3ubuntu1
Pin-Priority: 1000

Package: xserver-xorg-input-mouse
Pin: version 1:1.2.3-2
Pin-Priority: 1000

Package: xserver-xorg-input-synaptics
Pin: version 0.14.7~git20070706-1ubuntu4
Pin-Priority: 1000

Package: xserver-xorg-input-vmmouse
Pin: version 1:12.4.3-1ubuntu1
Pin-Priority: 1000

Package: xserver-xorg-input-wacom
Pin: version 1:0.7.9.8-0ubuntu3
Pin-Priority: 1000

Package: xserver-xorg-video-apm
Pin: version 1:1.1.1-10
Pin-Priority: 1000

Package: xserver-xorg-video-ark
Pin: version 1:0.6.0-9
Pin-Priority: 1000

Package: xserver-xorg-video-chips
Pin: version 1:1.1.1-9
Pin-Priority: 1000

Package: xserver-xorg-video-cirrus
Pin: version 1:1.1.0-8ubuntu1
Pin-Priority: 1000

Package: xserver-xorg-video-fbdev
Pin: version 1:0.3.1-4
Pin-Priority: 1000

Package: xserver-xorg-video-geode
Pin: version 1:2.9.0-1ubuntu2.5
Pin-Priority: 1000

Package: xserver-xorg-video-i128
Pin: version 1:1.2.1-4
Pin-Priority: 1000

Package: xserver-xorg-video-i740
Pin: version 1:1.1.0-7
Pin-Priority: 1000

Package: xserver-xorg-video-intel
Pin: version 2:2.2.1-1ubuntu13.7
Pin-Priority: 1000

Package: xserver-xorg-video-mga
Pin: version 1:1.4.8.dfsg.1-1
Pin-Priority: 1000

Package: xserver-xorg-video-neomagic
Pin: version 1:1.1.1-8
Pin-Priority: 1000

Package: xserver-xorg-video-nv
Pin: version 1:2.1.8-1ubuntu1
Pin-Priority: 1000

Package: xserver-xorg-video-geode
Pin: version 2.9.0-1ubuntu2.5
Pin-Priority: 1000

```

That did the job for me :)

Now i will try the 3D!

---

### Post by marduk667 on 2009-01-07
Okay the X-Server loads the Xpsb.so and starts AIGLX, but still glxinfo says:

> direct rendering: Yes
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2


Anybody knows what we are missing? Do we have the wrong Mesa-libs installed?

@jabronioh: Could you please post your complete glxinfo?
And do you have the recovery Image from Dell? I am very interested in that, too.

---

### Post by brteag00 on 2009-01-07
Et voila, Hardy has working 3D.  Woot!

Here's an explicit rundown of what I did.

[LIST=1]
[*]I started with an install of the Hardy Ubuntu Netbook Remix (UNR).  See [https://wiki.ubuntu.com/UNR]("https://wiki.ubuntu.com/UNR") for links to the installation images.  Using the UNR gets me the right architecture (lpia) and a working kernel modules (psb.ko and drm_psb.ko).  Unfortunately, it also uses a Clutter-based UI (ume-launcher, SLOW without accelerated OpenGL) and some weird window management stuff (maximus) - I disabled both of these by running gnome-session-properties and removing them from the list of enabled startup programs.

[*]Unfortunately, the UNR doesn't come with an up-to-date Xorg driver.  For that, I added the ubuntu-mobile PPA to my /etc/apt/sources.list:

```

deb http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main

```

and then used synaptic to update my xserver-xorg-video-psb package (and all the other goodies in that PPA.)  

Restart X.  At this point, you should have a fully functioning, full-resolution (2D only) X setup.  You may also need to add

```

Driver "psb"

```

to the "Device" section of /etc/X11/xorg.conf, if the X server doesn't auto-detect the PCI ID and load the right driver.

[*] Drop the firmware file, msvdx_fw.bin, into /lib/firmware/2.6.24-19-lpia/ (or the directory corresponding to your running kernel).  Restart the system to reload the psb.ko kernel module; it doesn't want to reload on a running system.  Run 'dmesg' (or check your system logs): you will see a line that says 

```

[drm:psb_do_init] *ERROR* Debug is 0x00000000

```

You should **NOT** see a line following that says
```

[drm:psb_setup_fw] *ERROR psb: No valid msvdx_fw.bin firmware found.

```

If you see this line, your firmware file is in the wrong place.  Move it to the firmware directory for your running kernel (check with uname -a), then try it again.  The 3D and video acceleration won't work without a loaded firmware.

[*] Copy psb_dri.so into /usr/lib/dri

[*] Copy Xpsb.so into /usr/lib/xorg/modules

Restart X.  Look at your /var/log/Xorg.0.log, and search for "Xpsb".  Instead of

```

(WW) PSB(0): Poulsbo Xpsb driver not available.  XVideo and 3D acceleration will not work.

```,

you should see

```

(II) Loading /usr/lib/xorg/modules/Xpsb.so

```

and a little further down the file
```

(II) PSB(0): Xpsb extension for 3D engine acceleration enabled.

```

You can verify 3D works by calling 'glxinfo | grep direct' and making sure you get back 'direct rendering: Yes'.

[/LIST]

Frankly, I'm satisfied with the Hardy-based UNR install.  I'm not going to try upgrading this to Intrepid (though thanks for the pointers, marduk!) - hopefully things will have settled down enough that Jaunty will be workable.  Intel seems to be investing a lot in the Poulsbo chipset, so hopefully the out-of-box support will improve.

Also, according to the release notes, the Intel Embedded Graphics Drivers kit (IEGD) ver. 9.1.1 has working Hardy drivers.  Alas, the latest binary available on the Intel site is 9.0.2.  Hopefully when this shows up, we'll have a more legitimate source for the binary-only bits.

Finally, while this provides immediate support for 3D, Xv and XvMC, there are a few more pieces to get fully hardware-accelerated video playback working.  I've pulled a copy of libva.so out of the IEGD; supposedly, there are Helix media player codecs available that will work with it.  Also, early libva support just landed in FFmpeg (and thus mplayer).  I'll be back when I've got more information.

---

### Post by brteag00 on 2009-01-07
> **marduk667 said:**
> 
And do you have the recovery Image from Dell? I am very interested in that, too.

Alas, the Dell recovery image has the Fluendo codecs and some DVD playback software installed (as per [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04))  Please, let's stick with things that are plausibly redistributable (but hard to find) instead of things that are bona fide illegal (at least here in the US.)

---

### Post by brteag00 on 2009-01-07
> **marduk667 said:**
> Okay the X-Server loads the Xpsb.so and starts AIGLX, but still glxinfo says:

direct rendering: Yes
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2 


AFAICT, you want libgl1-mesa-glx and libgl1-mesa-dri, but NOT libgl1-mesa-swx11 (the software renderer.)  I don't think Ubuntu has an easy way to switch OpenGL implementations (like 'eselect' from Gentoo), so you might have the wrong one installed.  Try running

```

dpkg-query -S libGL.so.1

```

For me, this returns
```

libgl1-mesa-glx: /usr/lib/libGL.so.1
libgl1-mesa-glx: /usr/lib/libGL.so.1.2

```

Also, you can get some more information by doing
```

export LIBGL_DEBUG=verbose

```

before running glxinfo.  This may provide a clue.  Finally, there may still be something screwy with your X install - if you can't figure it out, post your Xorg.0.log and we'll have a gander.

---

### Post by kylecronan on 2009-01-07
Thanks for the info, and thanks to Jabronioh for providing the files!  Here's my current status with Intrepid:  After installing the dri module, Xpsb and the firmware, AIGLX is initialized and it is actually possible to start compiz (after adding 'psb' to WHITELIST in /usr/bin/compiz).  But it is horribly slow, due to the software rasterizer I assume.  Your LIBGL_DEBUG=verbose shows the reason!

```

$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 0.1.0 psb (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tls/psb_dri.so
libGL: OpenDriver: trying /usr/lib/dri/psb_dri.so
libGL error: driver exports no extensions (/usr/lib/dri/psb_dri.so: undefined symbol: __driDriverExtensions)
libGL: OpenDriver: trying /usr/lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/dri/swrast_dri.so
...

```

Perhaps this is a symbol that's not needed by Xorg itself for the initialization, but only by applications that load the dri shared object?  I'm not sure how this whole DRM architecture is supposed to work- anyone have any suggestions?

---

### Post by brteag00 on 2009-01-07
@kylecronan -

It looks to me like Jabronioh's psb_dri.so was built against a different version of libGL than you have installed.  (Not a surprise, seeing as the Dell image is based on Hardy.  marduk, this might be your problem too.)  Perhaps try downgrading libgl1-mesa-glx to the one in Hardy: on my system, it's 7.0.3~rc2-1ubuntu3.

---

### Post by marduk667 on 2009-01-07
Downgrading Mesa helps, but compiz still does not start:

> /usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


---

### Post by jabronioh on 2009-01-07
Marduk - does your apt/preferences file allow you to install updates?

Breat - I would love to try your install, but I am afraid I would screw it up! I have a partition on my mini 12 where I could try it though...

kylecron - Do I need to add files from my 8.04.1 install to my 8.10 install to get 3D?

Here is the complete glxinfo output:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) GMA500 20080421 - 2.2.0.32L.0020 x86/MMX/SSE2
OpenGL version string: 2.0 Mesa 7.0.3
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_framebuffer_object, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_separate_stencil, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x59 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


```

---

### Post by kylecronan on 2009-01-07
Same problem with compiz here.  We're getting close, though- no more software rendering and glxgears now gives around 400fps.

I've tried different depths of 16 (no change) and 32 (won't start), downgrading _all_ the different mesa packages, UseFBDev in xorg.conf...  I think it is something to do with the coexistence of X and the fbdev console, and may have to do with this xorg error message in the log:

(EE) PSB(0): has_fbdev is true

Jabronioh, yes, you will need to install those 3 files in your other Ubuntu install, and also copy over the "DRI" section of xorg.conf so that you have the right permissions in /dev/dri.  And add 'WHITELIST="psb"' to /etc/xdg/compiz/compiz-manager, downgrade mesa packages, and something else that we haven't figured out yet!

---

### Post by jabronioh on 2009-01-07
Does anyone know approximately when Jaunty will be released?

---

### Post by kylecronan on 2009-01-07
Around the end of April, according to wiki.ubuntu.com/JauntyReleaseSchedule.

---

### Post by brteag00 on 2009-01-07
@jabronioh - you do have 3D!  Real, live, hardware-accelerated 3D - 
```

direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

```

That's why we were mooching files from you - yours works.  (And thanks again!)

I don't agree with kylecronan - I think that your current install is as close as anyone to having Compiz working (which, I assume, is your goal.)  I don't think you need to change anything - except maybe the update to xserver-xorg-video-psb that I referred to in post #94.  (But if it ain't broke, don't fix it.)

@kylecronan, marduk - I get the same Compiz error too.  (I'm sorry if I implied above that Compiz was working for me - it's not.)  From what I can tell, the driver isn't providing the ARGB visuals that Compiz wants.  It could simply be that the driver doesn't support them.  However, the has_fbdev error is something I hadn't noticed - I'll poke at the source code and see if I can't figure out what it means.

---

### Post by kylecronan on 2009-01-07
@brteag, thanks for clarifying about compiz on your hardy install.  I don't know if this is of interest really, but I compiled the version of glxgears from mesa-utils that uses FBConfig, and it works ok.  Shows 8 bits per channel RGB and alpha for several available configs (so compiz wants something very particular here?):

```

~/mesa-7.2/progs/xdemos$ ./glxgears_fbconfig 
GLX 1.3 is not supported.
GLX_SGIX_fbconfig is supported.

The following fbconfigs meet the requirements.  The first one will be used.

0x23        TrueColor     32   0   y   .  y    .    8  8  8  8  24  8 0  0  0  0     0     0       .       .
0x2b        DirectColor   32   0   y   .  y    .    8  8  8  8  24  8 0  0  0  0     0     0       .       .
0x27        TrueColor     32   0   y   .  y    .    8  8  8  8  24  8  16 16 16 16     0     0       .       .
0x2f        DirectColor   32   0   y   .  y    .    8  8  8  8  24  8  16 16 16 16     0     0       .       .
1866 frames in 5.0 seconds = 373.200 FPS
2220 frames in 5.0 seconds = 444.000 FPS

```

@jabronioh, I agree with brteag that you should leave your Dell install of hardy in a nice pristine condition.  I was just letting you know what will bring you up to date on your intrepid partition.  So are visual effects enabled on the Dell partition, btw?

edit: one other thing, could you attach the output of 'xdpyinfo -queryExtensions', thanks!

---

### Post by kylecronan on 2009-01-08
I just caught a fatal error in X.  Here it is in case it affects anyone else.  If Hardy doesn't do this when similarly configured I may go back!  Or perhaps the earlier version of the psb driver that's in Hardy doesn't have this?  Or maybe I've managed to screw up my own system in a special way- entirely possible!  FYI:

```

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux amelia 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan  7 21:16:32 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
Xpsb - 2.2.0.32L.0020
(EE) PSB(0): has_fbdev is true
libhal.c 1397 : wrong reply from hald.  Expecting an array.
libhal.c 1397 : wrong reply from hald.  Expecting an array.
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
[repeats many times...]

Fatal server error:
Driver failed PrepareAccess on a pinned pixmap

(EE) Failed locking memory manager: "Device or resource busy".

```

---

### Post by floquet on 2009-01-08
Same error here

---

### Post by brteag00 on 2009-01-08
> **kylecronan said:**
> I just caught a fatal error in X. 

Hmmm.  I've been "stress-testing" mine all afternoon (videos playing, glxgears or rss-glx screensavers running, web browser refreshing things) - and things seem rock-solid.  I would be really wary of running psb_dri.so and Xpsb.so on an X server they weren't compiled for, and with a patched, forward-ported DRM kernel module - but YMMV.

Also, I have bad news about Compiz.  When it finds the GL_EXT_framebuffer_object GLX extension (which the Poulsbo DRI driver supports), it expects to be able to bind pixmaps to MIP-mapped textures -- which the DRI driver *doesn't* support.  (See the compiz source's screen.c, lines 2044-2066 and 2179-2189).

I'm not by any means an OpenGL person, so I'm hacking around with things I don't understand.  The best possible scenario would be to find a way to disable the GL_EXT_framebuffer_object extension server-wide - but I don't know if you can just turn those things off.  Alternately, I might be able to hack compiz to ignore that extension's presence.  I've played with that a bit, but havn't yet had any luck.

At this point, I don't expect to have any more time to poke at this until this weekend (at the earliest.)  I'll keep tabs on this thread, though.

---

### Post by Dialog287 on 2009-01-08
[http://refoweb.net?p=40342]("http://refoweb.net?p=40342")

---

### Post by marduk667 on 2009-01-08
I also had several lockups now, so i think i will remove the 3D drivers :(

@brteag00: Is it illegal to send me a copy of the Dell/Ubuntu image from the U.S.? I did not know that, so sorry for that.

@all: [https://blueprints.launchpad.net/ubuntu-mobile/+spec/poulsbo-packaging/](https://blueprints.launchpad.net/ubuntu-mobile/+spec/poulsbo-packaging/) perhaps this is interesting for us

---

### Post by jabronioh on 2009-01-08
Somehow, I whacked both my installs yesterday and rebuilt the 8.10 partition today. I will try and restore the 8.04.1 tomorrow. 

The Hardy factory install will not start X. It complains about drm and the psb.ko module. If I get the recovery dvd onto a bootable stick, I can restore it rather quickly.....

I have no idea how it happened, unless it was when I uploaded some of the files...

---

### Post by irwnfv on 2009-01-09
I guess im joining the thread a little late. Also have a mini12 with Dell's version of Ubuntu, was wondering what exactly was not working with 8.10 versus 8.04.1, since I'd like to update to run VirtualBox on here.
Also, Dell put in some speedups? Dell's Ubuntu boots to desk in 1min 45secs if someone wanted to compare.

@Kyle
Visual Effects are not enabled, and when installed via the repos, don't appear to change anything. Though after reading the description it said it was for KDE so I quickly removed it.
$ xdpyinfo -queryExtensions
```
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10400090
X.Org version: 1.4.0.90
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x1e00021, revert to Parent
number of extensions:    33
    BIG-REQUESTS  (opcode: 130)
    Composite  (opcode: 158)
    DAMAGE  (opcode: 159, base event: 117, base error: 189)
    DOUBLE-BUFFER  (opcode: 142, base error: 153)
    DPMS  (opcode: 137)
    Extended-Visual-Information  (opcode: 139)
    GLX  (opcode: 143, base event: 77, base error: 154)
    MIT-SCREEN-SAVER  (opcode: 132, base event: 67)
    MIT-SHM  (opcode: 146, base event: 94, base error: 170)
    MIT-SUNDRY-NONSTANDARD  (opcode: 129)
    RANDR  (opcode: 156, base event: 115, base error: 186)
    RECORD  (opcode: 144, base error: 167)
    RENDER  (opcode: 155, base error: 181)
    SECURITY  (opcode: 152, base event: 112, base error: 178)
    SGI-GLX  (opcode: 143, base event: 77, base error: 154)
    SHAPE  (opcode: 128, base event: 64)
    SYNC  (opcode: 131, base event: 65, base error: 128)
    TOG-CUP  (opcode: 138)
    X-Resource  (opcode: 141)
    XAccessControlExtension  (opcode: 151)
    XC-APPGROUP  (opcode: 150, base error: 177)
    XC-MISC  (opcode: 133)
    XFIXES  (opcode: 153, base event: 113, base error: 180)
    XFree86-Bigfont  (opcode: 154)
    XFree86-DGA  (opcode: 136, base event: 68, base error: 145)
    XFree86-DRI  (opcode: 145, base error: 168)
    XFree86-Misc  (opcode: 135, base error: 137)
    XFree86-VidModeExtension  (opcode: 134, base error: 130)
    XINERAMA  (opcode: 157)
    XInputExtension  (opcode: 147, base event: 95, base error: 171)
    XKEYBOARD  (opcode: 149, base event: 111, base error: 176)
    XTEST  (opcode: 148)
    XVideo  (opcode: 140, base event: 75, base error: 150)
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1280x800 pixels (261x163 millimeters)
  resolution:    125x125 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x5b
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfac033
    KeyPressMask             KeyReleaseMask           EnterWindowMask          
    LeaveWindowMask          KeymapStateMask          ExposureMask             
    StructureNotifyMask      SubstructureNotifyMask   SubstructureRedirectMask 
    FocusChangeMask          PropertyChangeMask       ColormapChangeMask       
  number of visuals:    17
  default visual id:  0x23
  visual:
    visual id:    0x23
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x24
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x25
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x26
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x27
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x28
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x29
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x30
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x31
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x32
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x59
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits

```

p.s. New to Ubuntu, coming from Arch...so I'm not quite sure of how this distro is laid out yet.

---

### Post by brteag00 on 2009-01-09
@irwnfv - The long and short of it is that 8.10 (Ibex) doesn't support the video hardware (Poulsbo US15W) as well as 8.04 (Hardy).  The kernel DRM driver hasn't been forward-ported (at least, not officially), so you're stuck with VESA framebuffer driver.  

You also don't get any hardware-accelerated 3D or video playback - in addition to the kernel driver, you need a DRI module, a firmware file and a binary blob (see post #94.)  People have tried to graft them onto Ibex, but they only seem to be stable running on Hardy.

So.  If you have the Dell-provided version of Ubuntu, then you already have working 3D and video acceleration.  Unfortunately, Compiz still doesn't work, due to a mismatch between what Compiz expects from the 3D driver and what the 3D driver actually provides.  Hopefully, a workaround will be found - when I (or someone else) has time to poke at it.

Also, thanks for the xdpyinfo output - its more confirmation that my install looks pretty much like yours.

---

### Post by kylecronan on 2009-01-09
Yeah Intrepid is not looking so good right now.  I haven't been able to identify anything in userland related to X that's not the exact same binary as what works with Hardy (if xserver-xorg-video-psb 0.16.0+repack-0ubuntu1~804um6 is ok there- the only other version I found is 0.2.1-1ubuntu3, which needs an earlier xorg).

Dennis, the guy you talked to who provided that kernel patch for Mandrake, do you know if he's had any X crashes?  The only other changes I made to get the modules to compile with the Ubuntu kernel were quite trivial fixes (the patch itself made a couple changes that were only slightly more complicated).  I don't see where the issue is coming from, since I would expect any problems with the kernel port to cause an oops or maybe system hang, not internal errors in xorg.  Maybe there is something we're missing that is still the wrong version.  I'm going to see if Hardy will run ok with a 2.6.27 kernel, then if the failures still occur we'll know the problem is with this klugy DRM port.  2.6.27 does have two advantages: working suspend and SATA support (or does the need for all_generic_ide go away when you have an lpia kernel?).  Here's another interesting spec in development:

[http://blueprints.launchpad.net/ubuntu/+spec/lpia-versus-i386](http://blueprints.launchpad.net/ubuntu/+spec/lpia-versus-i386)

---

### Post by marduk667 on 2009-01-10
Hey Kyle,

no he did not mention anything :(
Perhaps you can ask him in #moblin on freenode. 

I removed the 3D drivers and everything is stable now, but no 3D.
When i can get the DELL Image i think i will have a look at it.

Regards,
Dennis

---

### Post by jabronioh on 2009-01-10
irwnfv- I need your help! I sent you a private message...

---

### Post by hubick on 2009-01-10
Hmm, this looks like it might help my quest to get Linux working on my Menlow/Poulsbo based Panasonic CF-U1: [http://forums.fedoraforum.org/showthread.php?t=201018](http://forums.fedoraforum.org/showthread.php?t=201018) :)

---

### Post by jabronioh on 2009-01-11
Has anyone installed 8.04 on their mini 12 with success? Are the steps similar to 8.10?

I have tried for days to get the Dell recovery DVD to boot from a USB stick but cannot make it happen. I can make regular 8.10 iso's boot, but not the Dell recovery DVD. Maddening.

---

### Post by brteag00 on 2009-01-11
> **jabronioh said:**
> Has anyone installed 8.04 on their mini 12 with success? Are the steps similar to 8.10?

There are instructions for installing the Netbook Remix at [https://wiki.ubuntu.com/UNR]("https://wiki.ubuntu.com/UNR"), which is Hardy-based, including instructions for using a USB image instead of an ISO.  I ended up doing a PXE-based network install, but only because I had the infrastructure (DHCP, TFTP servers) already set up (not for the faint of heart!)

---

### Post by jabronioh on 2009-01-11
The PXE network install sounds fun! I'll have to research it.

Thanks for the link...I may give that a shot if I can't get Dell to help me..

---

### Post by jabronioh on 2009-01-12
brteag00 - Thanks for the UNR link. They had a tool called image creator or some such and I used that to copy the belmont.....lpia.img file from the recovery DVD to a USB stick and viola', it is all back the way it was. What a relief. 

It's too bad I couldn't just share the image with Dell Mini owners as the install basically just installs Ubuntu...

---

### Post by kylecronan on 2009-01-12
Although, what's to stop someone with Dell's image from using it to create a modified image with those parts that are illegal to distribute removed?  The modified image should be legal to distribute.  The Intel license would seem to apply to the 3 files that are needed for the psb drivers, and allows redistribution under the same terms- with that license file included.  The modified image would probably just be missing some Fluendo codecs and stuff like that, nothing essential.  I would think Dell would be happy with it, since they would be saved the trouble of preparing a similar download on their site.

---

### Post by llavalle on 2009-01-13
> **kylecronan said:**
> Although, what's to stop someone with Dell's image from using it to create a modified image with those parts that are illegal to distribute removed?

I'll be happy to do exactly this... when my Mini 12 gets here... I ordered in late December and haven't received anything yet.

It is my understanding that the restore disk image provided by dell (well, created by the user) simple unpack a disk image.  If this is the case... is it created using the currently installed partitions?  I don't believe so... they must be using an image located on the restore partition.  If it's using a pre-packaged image... it might be hard to create a new image not containing the restricted software.

---

### Post by irwnfv on 2009-01-14
No I am pretty sure it wipes the whole drive and puts everything back the exact same way you received it. I'd like to help you with that image, but I dont have time to mess with an image, nor do i have the bandwidth to up the 1.2gigs.

Out of curiosity are your systems pretty stable? Mine is crashing minimum of once a day, often with multiple X crashes. Not quite sure the problem, and the only error messages that are really thrown are complaints about the gma 500. I think for the time being I may have to run XP until this driver thing settles. (Have school work to do, and cant fight my system as well.) If anyone rarely ever crashes and doesn't have slow performance let me know...Maybe its the system, or maybe its Dells official version. (I've already tried recovering.)

---

### Post by marduk667 on 2009-01-14
Now that i have removed 3D drivers it is very stable, just move the Xpsb.so to another place and restart X, it should be more stable then.

---

### Post by floquet on 2009-01-14
If Xpsb.so is removed then the performance of video playing is terrible (lost frames), isn't it?. I think we have here a temporary trade-off.

---

### Post by marduk667 on 2009-01-14
in totem videos dont work, but in vlc it's okay

---

### Post by monkey186 on 2009-01-14
Hi guys, newbie here. I had the same problem as OP on my mini 12 (but after tryig to install Xubuntu 8.10 using alternative cd iso), and this is how i came upon this thread. Neeldes to say i didn't understand a thing, but i followed the instructions of kylecronan in post [#58]("http://ubuntuforums.org/showpost.php?p=6432527&postcount=58"), to install Ubuntu 8.10 using live cd iso.

So far I did the following steps:

boot livecd from USB MSD (unetbootin ubuntu 8.10):
sudo /bin/bash
sed -i 's/"Device"/"Device"\nDriver "vesa"/;s/"Monitor"/"Monitor"\nHorizSync 30-80\nVertRefresh 50-70/' /etc/X11/xorg.conf
killall gdm ; sleep 10
gdm
complete install as usual

Then rebooted the computer and everything seems to work normally. My question is: do i need to follow the rest of the steps as per kylecronan's instructions? 

I'm not sure but i think i don't need Compiz/3D stuff, as we are going to make the system as light as possible (basically will be creating Xubuntu out of Ubuntu).

Thanks!

---

### Post by kylecronan on 2009-01-14
Well, the rest of the steps in that thread will give you the correct screen resolution in X and accelerated 2D graphics (you are currently using 1024x768 vesa).  They will not give you 3D- that requires more steps than are in that post, and does not work very well on 8.10 anyway.  For full hardware support, follow brteag00's instructions on installing 8.04.

If you're okay without 3D, you might want to give installing the xorg psb module a try: it will improve regular graphics performance and fix the screen resolution.  But this process also downgrades the xorg version and is something of a hack.  The 8.04 netbook remix doesn't require any such kluge and should probably be used on any system that has an actual purpose aside from tinkering with Linux on new hardware.

---

### Post by marduk667 on 2009-01-14
I also can give you the DELL image, if interested send me a PM (this is 8.04)

---

### Post by kylecronan on 2009-01-15
> **irwnfv said:**
> No I am pretty sure it wipes the whole drive and puts everything back the exact same way you received it. I'd like to help you with that image, but I dont have time to mess with an image, nor do i have the bandwidth to up the 1.2gigs.

It does this if you boot the image, but inside that vfat disk image is a squashfs image that contains the exact root filesystem to restore.  The contents of /boot are also included in another img file.  The restore script is at /install.sh.  But you can bypass this script by simply extracting rootfs.img to a partition that you install grub onto.

> **irwnfv said:**
> Out of curiosity are your systems pretty stable? Mine is crashing minimum of once a day, often with multiple X crashes. Not quite sure the problem, and the only error messages that are really thrown are complaints about the gma 500. I think for the time being I may have to run XP until this driver thing settles. (Have school work to do, and cant fight my system as well.) If anyone rarely ever crashes and doesn't have slow performance let me know...Maybe its the system, or maybe its Dells official version. (I've already tried recovering.)

I'd get it exchanged for a new one if you're having frequent crashes with Dell's Ubuntu.

edit: Never mind, don't return your box to Dell.  I get the crash too, with Dell's image ("Belmont").  It's the same as before: "Driver failed PrepareAccess on a pinned pixmap" shows up in /var/log/gdm/:0.log.1.  How could Dell have missed this?  I hit this bug after using it for a couple hours!

---

### Post by Belveder on 2009-01-15
Hi, :guitar:

I wanna say thanks to everybody who helped in getting this thing to work, especially to brteag00 for posting this great instruction guide and to jabronioh for uploading the files. 

I've exactly followed post #94 to get it to run on our Panasonic CF-U1 Toughbook - and it works great (glxgears running at approximately 105 fps in full screen mode for 1024x600).

There are just two things that I have to note here concerning the Toughbook:

1. I figured out that I have to turn off the splash screen in menu.lst and to update grub, otherwise X starts up, but X and all terminals are simply a blank screen. Turning the splash screen off gets everything to work.

2. Currently the touchscreen is not working. This surely is due to missing drivers in the kernel. Currently we simply have to live with that.

Thanks again!
Regards

Clemens :popcorn:

PS: I used the UNR image (Hardy 8.04.1), the additional repositories mentioned and simply updated everything prior to configuring X.

---

### Post by kylecronan on 2009-01-15
[https://bugs.launchpad.net/belmont/+bug/317390](https://bugs.launchpad.net/belmont/+bug/317390)

@brteag and others who have enabled 3D on the UNR image,
You guys haven't seen this bug where X hangs and then exits with a fatal error?  If it happens even on the Dell version of Hardy but is stable with the same drivers on UNR 1.0.1 that would be something interesting.

-
Clemens, glad to hear that this stuff is useful for your Panasonic too!  Not long ago my old toughbook T-2 finally gave out on me after a good 4-5 years, or I wouldn't be here!

---

### Post by kylecronan on 2009-01-15
FYI, here are the differences in the packages installed in UNR 1.0.1 versus Belmont 20081121:

```

3,4c3,4
< acpid 1.0.4-5ubuntu9
< acpi-support 0.109netbook0unr1
---
> acpid 1.0.4-5ubuntu9netbook1
> acpi-support 0.109
5a6,7
> adobereader-enu 8.1.2_SU1-1netbook1
> aircraft-manager belmont11
26a29
> belmont-config-travel 0.42
31,34c34,37
< bluez-audio 3.26-0ubuntu6
< bluez-cups 3.26-0ubuntu6
< bluez-gnome 0.25-0ubuntu2~804um1msg9
< bluez-utils 3.26-0ubuntu6
---
> bluez-audio 3.26-0ubuntu6netbook1
> bluez-cups 3.26-0ubuntu6netbook1
> bluez-gnome 0.25-0ubuntu2~804um1msg10
> bluez-utils 3.26-0ubuntu6netbook1
37a41
> brasero 0.7.1-3ubuntu1
49c53,54
< cheese 2.22.3-0ubuntu1usg6
---
> cdrdao 1:1.2.2-8ubuntu3
> cheese 2.22.3-0ubuntu1usg7
50a56
> close-window-applet 0.1-1
76,77c82,83
< dbus 1.1.20-1ubuntu2
< dbus-x11 1.1.20-1ubuntu2
---
> dbus 1.1.20-1ubuntu3.1netbook0belmont1
> dbus-x11 1.1.20-1ubuntu3.1netbook0belmont1
84,85c90,94
< desktop-file-utils 0.15-1ubuntu3
< desktop-switcher 0.3.2
---
> dell-launcher 0.8.16
> dellvideochat 6.0.6557-1
> deskbar-applet 2.22.3-0ubuntu1
> desktop-file-utils 0.15-1ubuntu4netbook0belmont1
> desktop-switcher 0.3.0
91a101
> diveintopython 5.4-2ubuntu2
98a109
> dvb-utils 1.1.1-3
101a113
> edict 2007.09.14-1
102a115
> ekiga 2.0.12-0ubuntu2
104c117
< esound-common 0.2.38-0ubuntu9
---
> esound-common 0.2.40-0ubuntu1~netbook1
109,110c122,123
< evolution 2.22.3.1-0ubuntu1netbook7
< evolution-common 2.22.3.1-0ubuntu1netbook7
---
> evolution 2.22.3.1-0ubuntu1netbook8
> evolution-common 2.22.3.1-0ubuntu1netbook8
113c126,127
< evolution-plugins 2.22.3.1-0ubuntu1netbook7
---
> evolution-exchange 2.22.3-0ubuntu2
> evolution-plugins 2.22.3.1-0ubuntu1netbook8
121,124c135,139
< firefox-3.0 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
< firefox 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
< firefox-3.0-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
< firefox-gnome-support 3.0.3+build1+nobinonly-0ubuntu0.8.04.1
---
> firefox-3.0 3.0.3+build1+nobinonly+nb1-0ubuntu0.8.04.1netbook1
> firefox 3.0.3+build1+nobinonly+nb1-0ubuntu0.8.04.1netbook1
> firefox-3.0-gnome-support 3.0.3+build1+nobinonly+nb1-0ubuntu0.8.04.1netbook1
> firefox-gnome-support 3.0.3+build1+nobinonly+nb1-0ubuntu0.8.04.1netbook1
> flashplugin-nonfree 9.0.124.0ubuntu2
135a151
> fuse-utils 2.7.2-1ubuntu2
137a154
> gcc-3.3-base 1:3.3.6-15ubuntu6
148c165
< gdm 2.20.7-0ubuntu1.1netbook2
---
> gdm 2.20.7-0ubuntu1.1netbook3belmont2
156a174,176
> gimp 2.4.5-1ubuntu2netbook2
> gimp-data 2.4.5-1ubuntu2netbook2
> gimp-gnomevfs 2.4.5-1ubuntu2netbook2
158a179
> gimp-python 2.4.5-1ubuntu2netbook2
162c183
< gnome-app-install 0.5.2.8-0ubuntu1
---
> gnome-app-install 0.5.2.8-0ubuntu1netbook0belmont1
165c186
< gnome-cards-data 1:2.22.3-0ubuntu2netbook1
---
> gnome-cards-data 1:2.22.3-0ubuntu2netbook3
169,170c190,191
< gnome-games 1:2.22.3-0ubuntu2netbook1
< gnome-games-data 1:2.22.3-0ubuntu2netbook1
---
> gnome-games 1:2.22.3-0ubuntu2netbook3
> gnome-games-data 1:2.22.3-0ubuntu2netbook3
176c197
< gnome-menus 2.22.2-0ubuntu2netbook1unr1
---
> gnome-menus 2.22.2-0ubuntu1.1usg4
182,186c203,209
< gnome-panel 1:2.22.2-0ubuntu1.1netbook2
< gnome-panel-data 1:2.22.2-0ubuntu1.1netbook2
< gnome-power-manager 2.22.1-1ubuntu4netbook4
< gnome-screensaver 2.22.2-0ubuntu1netbook0unr1
< gnome-session 2.22.1.1-0ubuntu2
---
> gnome-panel 1:2.22.2-0ubuntu1.1netbook2belmont1
> gnome-panel-data 1:2.22.2-0ubuntu1.1netbook2belmont1
> gnome-pilot 2.0.15-2ubuntu3
> gnome-pilot-conduits 2.0.15-1ubuntu2
> gnome-power-manager 2.22.1-1ubuntu4usg2
> gnome-screensaver 2.22.2-0ubuntu1
> gnome-session 2.22.1.1-0ubuntu2netbook1belmont1
190c213
< gnome-system-tools 2.22.0-0ubuntu9usg2
---
> gnome-system-tools 2.22.0-0ubuntu9usg3
198c221
< go-home-applet 0.1ubuntu16
---
> go-home-applet 0.2
199a223,225
> gpsd 2.36-2
> gpsd-clients 2.36-2
> gpstrans 0.40-3.1
204,207c230,240
< gstreamer0.10-alsa 0.10.18-3
< gstreamer0.10-gnomevfs 0.10.18-3
< gstreamer0.10-plugins-base 0.10.18-3
< gstreamer0.10-plugins-base-apps 0.10.18-3
---
> gst-fluendo-vadec1 0.10.13-1
> gstreamer0.10-alsa 0.10.18-3netbook2
> gstreamer0.10-fluendo-plugins-aac 0.10.6+belmont-0netbook0belmont3
> gstreamer0.10-fluendo-plugins-mms 0.10.6+belmont-0netbook0belmont3
> gstreamer0.10-fluendo-plugins-mp3 0.10.6+belmont-0netbook0belmont3
> gstreamer0.10-fluendo-plugins-mpeg2 0.10.6+belmont-0netbook0belmont3
> gstreamer0.10-fluendo-plugins-mpeg4 0.10.6+belmont-0netbook0belmont3
> gstreamer0.10-fluendo-plugins-wmv 0.10.6+belmont-0netbook0belmont3
> gstreamer0.10-gnomevfs 0.10.18-3netbook2
> gstreamer0.10-plugins-base 0.10.18-3netbook2
> gstreamer0.10-plugins-base-apps 0.10.18-3netbook2
210,211c243,244
< gstreamer0.10-tools 0.10.18-4ubuntu1
< gstreamer0.10-x 0.10.18-3
---
> gstreamer0.10-tools 0.10.18-4ubuntu1netbook1
> gstreamer0.10-x 0.10.18-3netbook2
226c259
< hal-info 20080508+git20080601-0ubuntu0.8.04
---
> hal-info 20080508+git20080601-0ubuntu0.8.04netbook1belmont1
235d267
< human-netbook-theme 0.7
241d272
< icedtea-gcjwebplugin 1.0-0ubuntu5
254a286,297
> kalgebra 0.5-1
> kalzium 4:3.5.9-0ubuntu2netbook1
> kalzium-data 4:3.5.9-0ubuntu2netbook1
> kanagram 4:3.5.9-0ubuntu2netbook1
> kanjidic 2007.09.14-1
> kdeedu-data 4:3.5.9-0ubuntu2netbook1
> kdelibs4c2a 4:3.5.9-0ubuntu7.1
> kdelibs-data 4:3.5.9-0ubuntu7.1
> khangman 4:3.5.9-0ubuntu2netbook1
> kiten 4:3.5.9-0ubuntu2netbook1
> klettres 4:3.5.9-0ubuntu2netbook1
> klettres-data 4:3.5.9-0ubuntu2netbook1
256a300,305
> kmplot 4:3.5.9-0ubuntu2netbook1
> kolf 4:3.5.9-0ubuntu1
> ktouch 4:3.5.9-0ubuntu2netbook1
> ktuberling 4:3.5.9-0ubuntu1
> kwordquiz 4:3.5.9-0ubuntu2netbook1
> kworldclock 4:3.5.9-0ubuntu1.1usg1
262a312,313
> language-pack-kde-en 1:8.04+20080708
> language-pack-kde-en-base 1:8.04+20080527
271a323
> lesstif2 1:0.95.0-2.1
274d325
< libaccess-bridge-java 1.22.0-0ubuntu5
276a328
> libao2 0.8.8-3
280a333,334
> libarts1c2a 1.5.9-0ubuntu2
> libartsc0 1.5.9-0ubuntu2
286a341
> libaudio2 1.9.1-1
293a349,350
> libavahi-qt3-1 0.6.22-2ubuntu4
> libavahi-ui0 0.6.22-2ubuntu4
294a352,354
> libavcodec1d 3:0.cvs20070307-5ubuntu7.1
> libavutil1d 3:0.cvs20070307-5ubuntu7.1
> libbeagle1 0.3.0-2ubuntu1
315c375
< libck-connector0 0.2.3-3ubuntu5
---
> libck-connector0 0.2.3-3ubuntu5belmont1
330c390
< libdbus-1-3 1.1.20-1ubuntu2
---
> libdbus-1-3 1.1.20-1ubuntu3.1netbook0belmont1
333a394
> libdirectfb-1.0-0 1.0.1-7ubuntu3
337c398
< libdrm2 2.3.0.16-0ubuntu2~804um1
---
> libdrm2 2.3.0.16-0ubuntu2~804um3
351c412
< libesd-alsa0 0.2.38-0ubuntu9
---
> libesd-alsa0 0.2.40-0ubuntu1~netbook1
379a441,442
> libgda3-3 3.0.2-2ubuntu1
> libgda3-common 3.0.2-2ubuntu1
382a446,448
> libgdl-1-0 0.7.11-1
> libgdl-1-common 0.7.11-1
> libgdl-gnome-1-0 0.7.11-1
386c452
< libgif4 4.1.6-4
---
> libgimp2.0 2.4.5-1ubuntu2netbook2
388a455
> libgl1-mesa-dri-psb 0.19
414c481
< libgnome-menu2 2.22.2-0ubuntu2netbook1unr1
---
> libgnome-menu2 2.22.2-0ubuntu1.1usg4
437a505
> libgps17 2.36-2
443,444c511,513
< libgstreamer0.10-0 0.10.18-4ubuntu1
< libgstreamer-plugins-base0.10-0 0.10.18-3
---
> libgsm1 1.0.12-1
> libgstreamer0.10-0 0.10.18-4ubuntu1netbook1
> libgstreamer-plugins-base0.10-0 0.10.18-3netbook2
459a529
> libgtk-vnc-1.0-0 0.3.4-0ubuntu2
488a559,560
> libkdeedu3 4:3.5.9-0ubuntu2netbook1
> libkdegames1 4:3.5.9-0ubuntu1
489a562
> libkiten1 4:3.5.9-0ubuntu2netbook1
499a573,574
> liblua50 5.0.3-3
> liblualib50 5.0.3-3
501a577
> libmad0 0.15.1b-2.1ubuntu1
503a580
> libmatchbox1 1.9-3
505c582,584
< libmetacity0 1:2.22.0-0ubuntu4.netbook1
---
> libmetacity0 1:2.22.0-0ubuntu4.netbook2
> libmng1 1.0.9-1
> libmodplug0c2 1:0.7-7
527a607
> libmpcdec3 1.2.2-1build1
545a626
> libntfs-3g23 1:1.2216-1ubuntu2
548a630
> libopal-2.2 2.2.11~dfsg1-3ubuntu2
559c641
< libpanel-applet2-0 1:2.22.2-0ubuntu1.1netbook2
---
> libpanel-applet2-0 1:2.22.2-0ubuntu1.1netbook2belmont1
578a661,663
> libpostproc1d 3:0.cvs20070307-5ubuntu7.1
> libpt-1.10.10 1.10.10-1ubuntu6
> libpt-1.10.10-plugins-alsa 1.10.10-1ubuntu6
585a671,673
> libqt3-mt 3:3.3.8-b-0ubuntu3
> libqt4-core 4.3.4-0ubuntu3
> libqt4-gui 4.3.4-0ubuntu3
598a687,692
> libsdl1.2debian 1.2.13-1ubuntu1
> libsdl1.2debian-alsa 1.2.13-1ubuntu1
> libsdl-gfx1.2-4 2.0.13-3
> libsdl-image1.2 1.2.6-3
> libsdl-mixer1.2 1.2.8-1ubuntu0.1
> libsdl-ttf2.0-0 2.0.9-1
621a716
> libstdc++5 1:3.3.6-15ubuntu6
638c733
< libusplash0 0.5.19netbook1
---
> libusplash0 0.5.19netbook3
639a735
> libva1 0.29-9
641c737
< libvolume-id0 117-8
---
> libvolume-id0 117-8msg6
643a740
> libvorbisfile3 1.2.0.dfsg-2
664a762,763
> libxcb-shape0 1.1-1ubuntu1
> libxcb-shm0 1.1-1ubuntu1
665a765
> libxcb-xv0 1.1-1ubuntu1
676a777,783
> libxine1 1.1.11.1-1ubuntu3.1
> libxine1-bin 1.1.11.1-1ubuntu3.1
> libxine1-console 1.1.11.1-1ubuntu3.1
> libxine1-ffmpeg 1.1.11.1-1ubuntu3.1
> libxine1-misc-plugins 1.1.11.1-1ubuntu3.1
> libxine1-plugins 1.1.11.1-1ubuntu3.1
> libxine1-x 1.1.11.1-1ubuntu3.1
697a805
> libxvmc1 2:1.0.4-2ubuntu1
702,703d809
< libzlcore 0.8.14-1ubuntu1
< libzlui-gtk 0.8.14-1ubuntu1
707,708c813,814
< linux-restricted-modules-2.6.24-19-lpia 2.6.24.13-19.45netbook4
< linux-restricted-modules-common 2.6.24.13-19.45netbook4
---
> linux-restricted-modules-2.6.24-19-lpia 2.6.24.13-19.45netbook5
> linux-restricted-modules-common 2.6.24.13-19.45netbook5
711c817,818
< linux-ubuntu-modules-2.6.24-19-lpia 2.6.24-19.29netbook13
---
> linux-ubuntu-modules-2.6.24-19-lpia 2.6.24-19.29netbook16
> lmarbles 1.0.7-1
721a829
> matchbox-window-manager 1.2-1ubuntu1
723a832
> mbr 1.1.9-3ubuntu1
726,727c835,836
< metacity 1:2.22.0-0ubuntu4.netbook1
< metacity-common 1:2.22.0-0ubuntu4.netbook1
---
> metacity 1:2.22.0-0ubuntu4.netbook2
> metacity-common 1:2.22.0-0ubuntu4.netbook2
732c841
< module-init-tools 3.3-pre11-4ubuntu5
---
> module-init-tools 3.3-pre11-4ubuntu5.8.04.1
740d848
< mtp-tools 0.2.6.1-2ubuntu1
744a853
> nautilus-cd-burner 2.22.1-0ubuntu1
756a866,867
> ntfs-3g 1:1.2216-1ubuntu2
> ntp 1:4.2.4p4+dfsg-3ubuntu2
759,760c870,872
< oem-config 1.37.2netbook9
< oem-config-gtk 1.37.2netbook9
---
> odbcinst1debian1 2.2.11-16build1
> oem-config 1.37.2netbook9belmont2
> oem-config-gtk 1.37.2netbook9belmont2
762,764d873
< openjdk-6-jre 6b11-2ubuntu2+build1
< openjdk-6-jre-headless 6b11-2ubuntu2+build1
< openjdk-6-jre-lib 6b11-2ubuntu2+build1
796c905,907
< pm-utils 0.99.2-3ubuntu10
---
> planetpenguin-racer 0.3.1-10
> planetpenguin-racer-data 0.3.1-10
> pm-utils 0.99.2-3ubuntu10belmont2
805c916,917
< procps 1:3.2.7-9ubuntu1netbook0unr3
---
> procps 1:3.2.7-5ubuntu3
> psb-video 0.23-0netbook1
816a929
> python-4suite-xml 1.0.2-1ubuntu1
828c941
< python-gmenu 2.22.2-0ubuntu2netbook1unr1
---
> python-gmenu 2.22.2-0ubuntu1.1usg4
830a944
> python-gnome2-extras 2.19.1-0ubuntu7
858c972
< readahead 1:0.20050517.0220-0ubuntu14
---
> rdesktop 1.5.0-3+cvs20071006
860,861c974
< rhino 1.6.R7-2
< rhythmbox 0.11.5-0ubuntu8netbook1
---
> rhythmbox 0.11.5-0ubuntu8netbook1belmont3
873a987
> serpentine 0.9-5ubuntu2
878a993
> sound-juicer 2.22.0-1ubuntu2
884,888d998
< stardict 3.0.1-3
< stardict-common 3.0.1-3
< stardict-gnome 3.0.1-3
< stardict-plugin 3.0.1-3
< stardict-plugin-spell 3.0.1-3
889a1000,1001
> stellarium 0.9.1-2
> stellarium-data 0.9.1-2
890a1003,1005
> sun-java6-bin 6-06-0ubuntu1
> sun-java6-jre 6-06-0ubuntu1
> sun-java6-plugin 6-06-0ubuntu1
902a1018
> tcl8.4 8.4.16-4ubuntu1
905,909c1021,1030
< totem 2.22.1-0ubuntu2
< totem-common 2.22.1-0ubuntu2
< totem-gstreamer 2.22.1-0ubuntu2
< totem-mozilla 2.22.1-0ubuntu2
< totem-plugins 2.22.1-0ubuntu2
---
> totem 2.22.1-0ubuntu2netbook0belmont3
> totem-common 2.22.1-0ubuntu2netbook0belmont3
> totem-dvb-scanner 3
> totem-gstreamer 2.22.1-0ubuntu2netbook0belmont3
> totem-mozilla 2.22.1-0ubuntu2netbook0belmont3
> totem-plugins 2.22.1-0ubuntu2netbook0belmont3
> totem-tv 2.22.2-6-0ubuntu2
> transmission-common 1.06-0ubuntu6
> transmission-gtk 1.06-0ubuntu6
> tsclient 0.150-1ubuntu1
915a1037
> ttf-dustin 20030517-6
921d1042
< ttf-liberation 1.0-0ubuntu1
923a1045
> ttf-sil-andika 0.001.desrev-5
925a1048,1050
> tuxmath 1.5.8-2
> tuxpaint 1:0.9.17-1ubuntu3netbook1
> tuxpaint-data 1:0.9.17-1ubuntu3netbook1
927c1052
< ubufox 0.5-0ubuntu1unr3
---
> ubufox 0.5-0ubuntu1belmont6
928a1054
> ubuntu-desktop 1.102belmont3
930c1056
< ubuntu-gdm-themes 0.29
---
> ubuntu-gdm-themes 0.29usg6
932,933c1058
< ubuntu-minimal 1.102netbook0unr6
< ubuntu-netbook-remix 1.102netbook0unr6
---
> ubuntu-minimal 1.102belmont3
937,939c1062,1063
< udev 117-8
< ume-config-netbook 0.35
< ume-launcher 0.6.15
---
> udev 117-8msg6
> ume-config-belmont 0.100
940a1065
> unixodbc 2.2.11-16build1
943,944c1068,1069
< update-manager 1:0.87.30netbook0unr1
< update-manager-core 1:0.87.30netbook0unr1
---
> update-manager 1:0.87.30netbook0belmont2
> update-manager-core 1:0.87.30netbook0belmont2
951c1076,1077
< usplash 0.5.19netbook1
---
> user-setup 1.16ubuntu5
> usplash 0.5.19netbook3
958a1085
> vinagre 0.5.1-0ubuntu1
966d1092
< window-picker-applet 0.4.5
969a1096
> w-scan 20080105-0ubuntu1
982c1109
< xdg-user-dirs 0.10-1ubuntu1
---
> xdg-user-dirs 0.10-1ubuntu1netbook0belmont2
994a1122,1124
> xorg-modules-xpsb 0.11
> xsane 0.995-1ubuntu1
> xsane-common 0.995-1ubuntu1
1000a1131
> xserver-xorg-input-evtouch 0.8.7-3ubuntu1
1024a1156
> xserver-xorg-video-psb 0.16.0+repack-0ubuntu1~804um5netbook1
1048a1181
> yahoo-toolbar-extension 1.0

```

Most of this is available in .deb form at [http://dell-mini.archive.canonical.com/](http://dell-mini.archive.canonical.com/).  These are the packages that are not in the archive:

```

adobereader-enu
dell-launcher
dellvideochat
gst-fluendo-vadec1
gstreamer0.10-fluendo-plugins-aac
gstreamer0.10-fluendo-plugins-mms
gstreamer0.10-fluendo-plugins-mp3
gstreamer0.10-fluendo-plugins-mpeg2
gstreamer0.10-fluendo-plugins-mpeg4
gstreamer0.10-fluendo-plugins-wmv
libdns35
libgl1-mesa-dri-psb
libva1
psb-video
totem-dvb-scanner
xorg-modules-xpsb
yahoo-toolbar-extension

```

---

### Post by marduk667 on 2009-01-15
Is this a fact that it also locks up with the Ubuntu Image?

---

### Post by kylecronan on 2009-01-15
It has happened to irwnfv and myself.  I've hit it twice now.  Not really surprising given all those 0.x version numbers in the Intel stuff.  This code is just not ready.

---

### Post by marduk667 on 2009-01-15
well then i will not reinstall, intrepid now runs okay without 3D, so i am happy.

I only have one real strange thing:

When i wake up the Mini from Hibernate and don't touch anything, it won't do anything (Network Connection e.g.). I have to move the mouse so it connects to my wireless again...

---

### Post by kylecronan on 2009-01-15
Btw everyone, it seems there is a somewhat official place to ask questions about Dell's versions of Ubuntu for the Mini:

[https://answers.launchpad.net/dell-mini](https://answers.launchpad.net/dell-mini)

---

### Post by jabronioh on 2009-01-15
I have reinstalled the Dell belmont image and it is better now than when I got it from the factory. HOWEVER, it will reboot itself and it has happened once when using Synaptic.

I just hope we get a better image in the future for this laptop, cuz I really like it!

---

### Post by brteag00 on 2009-01-15
> **kylecronan said:**
> [https://bugs.launchpad.net/belmont/+bug/317390](https://bugs.launchpad.net/belmont/+bug/317390)

@brteag and others who have enabled 3D on the UNR image,
You guys haven't seen this bug where X hangs and then exits with a fatal error?  If it happens even on the Dell version of Hardy but is stable with the same drivers on UNR 1.0.1 that would be something interesting.

Mine is rock-solid.  I had it running an rss-glx screensaver in windowed mode, playing a video and refreshing washingtonpost.com every few minutes for an entire afternoon, with no apparent problems.

It stinks that the Dell image is giving you trouble - but, as someone pointed out, there's still a lot of beta code here.  Hopefully this stuff will get sorted out soon.

---

### Post by jabronioh on 2009-01-15
I am tempted to install Brteag00's UNR install from post #94 on another partition but may wait a day or two! In hindsight, I should have traveled this route rather than reinstalling from the Dell image.

Oh well, isn't that half the fun of Linux? The journey?

---

### Post by marduk667 on 2009-01-15
> oh well, isn't that half the fun of linux? The journey?

yes! :)

---

### Post by kylecronan on 2009-01-15
brteag00, just curious: do you have bios revision 01 or 02?

Now that I've let it be known there's a bios update, to anyone who's thinking of flashing their bios- beware!  I just ran the update program on my Vista install and it bricked it!  The "WinPhlash" program froze up halfway through and now on boot I just get beeps- nothing!  Called up Dell support and their servoids don't even have scripts yet for this model.  I have to wait for some special request to work its way through the bureaucracy.

Oh yeah, the journey, it's a blast.

---

### Post by brteag00 on 2009-01-15
> **kylecronan said:**
> brteag00, just curious: do you have bios revision 01 or 02?

I ordered mine the afternoon it was released on an unsuspecting public, so it's BIOS ver. A01.

> **kylecronan said:**
> Now that I've let it be known there's a bios update, to anyone who's thinking of flashing their bios- beware!

Yikes!  The A02 download says it's supposed to work in real mode (ie, FreeDOS booted from a flash drive), but it doesn't.  And I'm not brave (stupid) enough to try a third-party flash tool.

I'm so sorry to hear that shiny new laptop is now a shiny new paperweight.  My support experiences with Dell have (usually) been positive - I hope they get it resolved soon!

---

### Post by jabronioh on 2009-01-15
I love Dell and their support EXCEPT as it pertains to this laptop, in which case they have been useless.

Kyle - may I ask what you were hoping to improve with the BIOS upgrade?

---

### Post by kylecronan on 2009-01-15
> **brteag00 said:**
> 
I'm so sorry to hear that shiny new laptop is now a shiny new paperweight.  My support experiences with Dell have (usually) been positive - I hope they get it resolved soon!

Thanks.  Actually once I went through the returns dept (on the last possible day!) they just arranged for a tech to come out and swap the mainboard, so I can't complain.  But tech support had no idea what to do with me because the service tag printed on my laptop wasn't in their database yet.

---

### Post by kylecronan on 2009-01-15
> **jabronioh said:**
> I love Dell and their support EXCEPT as it pertains to this laptop, in which case they have been useless.

Kyle - may I ask what you were hoping to improve with the BIOS upgrade?

I was hoping it would load a video bios also, and so possibly fix the xorg driver bug I've been seeing.  That's probably not the case though.  Plus maybe fix that annoying clicking of the hard drive.  I got the update from Dell's ftp site and it was packaged up to run this WinPhlash thing from Phoenix.  If there is a way to do it in real mode that would definately be preferable, but be very careful!

---

### Post by jabronioh on 2009-01-16
brteag00 - Would you say that your install is fairly comparable in terms of speed to other 8.04 installs? Mine is rather slow and it is all due to the Xorg drivers hogging my poor little Atom processor. I say poor little processor but can remember not so long ago the Pentium 60 mHz processors or the 8088's of yesteryear, which truly were itty bitty.

Anyway, I have a long weekend and a very easy way to restore the mini 12, so what the heck...

I guess I already know your answer since you refer to running several intensive apps at once, but guess I wanted your written assurance! HA.... thanks

---

### Post by brteag00 on 2009-01-16
> **jabronioh said:**
> brteag00 - Would you say that your install is fairly comparable in terms of speed to other 8.04 installs?

I'm not quite sure how to answer that.  Is it as fast as my year-old 2.6 Ghz Core 2 Duo desktop?  No, obviously not.  I've got a 933 Mhz PIII that's still in service, and the Atom/Poulsbo combination seems to have a substantial edge on it in terms of raw processing power, though the graphics responsiveness (dragging windows around, for example) seems a touch slower.

As far as the Xorg drivers in particular, I saw a substantial speedup when I moved from the VESA drivers to the Poulsbo-specific drivers - I guess this comes as no surprise, seeing as the psb driver uses EXA to accelerate the 2d parts.

I'm not sure that I particularly see the point in the comparison with other installs.  I would rather ask, "is it fast enough to do the things I want to do with it?"  For my tasks - web browsing, reading PDFs, a little remote access, the occasional presentation - the answer is a full-throated 'yes' - it sure beats the pokey PII-400 laptop that it succeeds!

I hope your rebuild this weekend goes well.

---

### Post by jabronioh on 2009-01-16
brteag00 - Thanks. I realized it was a subjective question but you answered it for me.

I just have never run Linux before and had such a slow system. Sometimes I can watch Xorg use 60% of the CPU...sometimes I can watch the windows redraw slowly, which makes me crazy. I use the laptop for similar reasons as you and do not think I am trying to stress the system...oh well.. I am gonna give the UNR image a shot and see if I like it better....

Thanks again..

---

### Post by jabronioh on 2009-01-16
OK, got everything going except it says no 3D. Everything I did matched brteag00's output in post 94 , so I am a little puzzled.

ken@ken:~$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa DRI Intel(R) GMA500 20080421 - 2.2.0.32L.0020 x86/MMX/SSE2


Where would I change the LIBGL_DEBUG parameter?

It seems stable so far and at least twice as fast as the Dell belmont image, so I happy for that. I think it looks pretty good too...

---

### Post by brteag00 on 2009-01-16
> **jabronioh said:**
> 
Where would I change the LIBGL_DEBUG parameter?


LIBGL_DEBUG is an environment parameter.  To set it just for the program you're running, just prepend it to the command line, like so:
```

brian@pol:~$ LIBGL_DEBUG=1 glxinfo
name of display: :0.0
libGL error: 
Can't open configuration file /etc/drirc: No such file or directory.
libGL error: 
Can't open configuration file /home/brian/.drirc: No such file or directory.
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
...

```

(by the way, the 'Can't open configuration file...' errors are nothing to worry about.  Other errors, like 'Can't open /dev/dri/card0', are more worrisome.)

Did you check your 'dmesg' output to make sure the firmware was loaded, and your /var/log/Xorg.0.log to make sure the psb.so module was loading the Xpsb.so sub-module?  If both of those are working, but you still don't have 3D, then you might have the wrong version of the Mesa 3D library installed - check that you have packages libgl1-mesa-dri and libgl1-mesa-glx, but NOT libgl1-mesa-swx11.

I'm glad that it seems to be faster!

Edit, 10:03 CST -
If you want, I'm happy to look at your 'dmesg' output and /var/log/Xorg.0.log file - put them up on [http://pastebin.com](http://pastebin.com), and shoot me a PM.

---

### Post by jabronioh on 2009-01-17
brteag00 - I did check the dmesg and the var/log/Xorg.0.log and everything was copasetic. So I ran the LIBGL_DEBUG=1 glxinfo command like you said and found problems with permissions on the psb_dri.so file. I just changed these permissions and it works now! 

Thanks for your help, I appreciate it. This install works much better than Dell's and now the laptop is more like what I have been used to over the past 12 years...you would think that I would know a little more since I have used UNIX for 26 years, but once I get a system running, I usually don't mess with it much. I used to install RedHat before the nice GUI installs we have today and remember having to tweak the "X" files to get the screen resolution correct.

Anyway, thanks to everyone who knows so much more than I and is willing to help out. I do recommend the brteag00 install for anyone who got the Ubuntu install from Dell. I still find it hard to believe that Dell actually shipped the laptop out with such a poor image. I also cannot believe that Dell initially shipped this laptop with Vista. I bought this laptop initially with Vista, but sent it back because it was so awful and slow.

---

### Post by marduk667 on 2009-01-17
Hey,
so the UNR image is lpia architectur, isn't it? Are all packages available for lpia? Does the gdebi install 386 packages without problems?

What networkmanager version is installed? If it is <0.7 have you tried to install 0.7?

---

### Post by jabronioh on 2009-01-17
> **marduk667 said:**
> Hey,
so the UNR image is lpia architectur, isn't it? Are all packages available for lpia? Does the gdebi install 386 packages without problems?

What networkmanager version is installed? If it is <0.7 have you tried to install 0.7?

Yes, it is lpia and gdebi works fine. The longer I use this, the better I like it. The mini 12 is now working like I thought it would from the beginning.

All the packages I use are available.

The network manager is 0.6.6 which I am not crazy about. I have not tried installing 0.7 yet...

---

### Post by brteag00 on 2009-01-17
> **jabronioh said:**
> 
The network manager is 0.6.6 which I am not crazy about. I have not tried installing 0.7 yet...

The great thing about the Launchpad infrastructure is that all the personal package archives (PPAs) are automatically built for all supported releases, for all supported architectures.  So to get NetworkManager 0.7, all you have to do is add the NM PPA to your /etc/apt/sources.list, like so:

```

deb http://ppa.launchpad.net/network-manager/ubuntu hardy main
deb-src http://ppa.launchpad.net/network-manager/ubuntu hardy main

```

Makes VPNs and wireless much nicer.

---

### Post by marduk667 on 2009-01-18
ah great, so i will also install UNR on mine, that sounds great :)

---

### Post by ronewolf on 2009-01-19
This thread documents quite an adventure. I'm still not scared off nor by [http://www.sticksite.com/linux/](http://www.sticksite.com/linux/).

But the reason I haven't ordered the Mini 12 yet is that I would also like the capability to support an external monitor at least at 1400x1000. Not sure if the limit as quoted by Dell (in the spec and by phone) of 1280x800 is due to the GMA 500 itself or the driver. If the driver, then I would hope that more would be possible at some point. Would be interested in your comments or to pointers as where I could research futher.

BTW, since I last shopped Dell a couple of weeks ago, they have added an intermediate config Catalog Number: 29DNDWYA5. Which with 6cell, 60GB, and the 1.33GHz Atom comes out to $429.

---

### Post by jabronioh on 2009-01-19
Still running rock solid. I am quite pleased.

I did get the updated network manager, but for some reason, it is not quite like what I had with the Dell install. A left click on the network icon used to list all available wireless networks, but I do not see that now. 

The good news for me though is the automatic mobile broadband connection with my Verizon USB phone stick. That is a nice feature which used to be available only in 8.10, I think.

I would say that if I could get the network manager to display the wireless nets available, then I would have the perfect install! I have no trouble connecting to my wireless network at home though.

---

### Post by brteag00 on 2009-01-19
> **ronewolf said:**
> 
But the reason I haven't ordered the Mini 12 yet is that I would also like the capability to support an external monitor at least at 1400x1000.


I am happy to report that I plugged my Mini 12 into my 21" Apple Studio Display CRT (old, I know), and it drives that display at 1600x1200, 60Hz.  The slow refresh at this resolution seems to be a limitation of the hardware - the spec sheet gives a 130 Mhz pixel clock.  The refresh is too slow for a CRT (1280x1024, 85Hz is much easier on the eyes), but on an LCD it should be fine.

There was some oddness when trying to get both the internal and external displays working at once ("big desktop" mode, not "cloned") - it worked some of the time, but I'm sure that's just a configuration issue.  I didn't take the time to dig into it, this was just a quick hardware compatibility check.

So.  I'm not sure why Dell told you what they did, but my hardware and driver combo gives good results with this setup.

---

### Post by ronewolf on 2009-01-19
brteag00, 

thank you! thank you very much!:guitar: that's great news especially as i will, of course, use it with an LCD monitor. i am going to place my order shortly then.

what release are you running? any mods?

---

### Post by brteag00 on 2009-01-19
> **ronewolf said:**
> 
what release are you running? any mods?

Look back up at [[COLOR="Red"]post #94[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6512181&postcount=94") - it describes my setup in detail.  Several other posters on this thread have had success with it, as well.

---

### Post by Zappastián on 2009-01-19
Hi there... quite a thread you guys got here. Congratulations.
My girlfriend just got a mini 12 with vista and we want to install ubuntu. I read the now 'famous' post #94 by brteag00 and am preparing to follow his isntructions.
I have some questions though: 
1. Most of what is written concerns video and 3D issues. Are those 'crucial' issues? Will they disturb a simple openoffice user?
2. Is the video output working? I mean: can I plug a data projector for Impress presentations?
3. Are there any other problems to annoy a standard user?

Thanks

Zappa

---

### Post by brteag00 on 2009-01-19
> **Zappastián said:**
> 
1. Most of what is written concerns video and 3D issues. Are those 'crucial' issues? Will they disturb a simple openoffice user?


The 3D and video stuff aren't 'crucial', per se - what is crucial is that you are using the Poulsbo-specific drivers.  If you use a vanilla Hardy or Intrepid install, then you're stuck with the VESA drivers, which only do 1024x768, not the native 1280x800.  However, if you use the UNR image (for the psb.ko kernel driver) and install the latest xserver-xorg-video-psb package from the ubuntu-mobile PPA, then you don't have to worry about the rest if you don't need 3D and accelerated video.

> **Zappastián said:**
> 
2. Is the video output working? I mean: can I plug a data projector for Impress presentations?


Yes, cloning the desktop to the external output works great.  Using Impress's "presentation mode" (ie, sending the full-screen presentation to the external output and leaving slide, notes, timer on the LCD) didn't work for me in the 30 seconds I spent trying.  See my above post about getting a large monitor to work.

> **Zappastián said:**
> 
3. Are there any other problems to annoy a standard user?


All the rest of the hardware works out-of-box, which is pretty amazing.  Upgrading to NetworkManager 0.7.x makes wireless networking easier - see one of the above posts for instructions.  The only other thing that's a little weird for me is some slightly buggy power-management scheme for the hard disk.  It makes an odd clicking sound regularly, which sounds like the heads parking.  It goes away when you disable the disk's power management settings, like so
```

sudo hdparm -B 254 /dev/sda

```

I havn't had the time to sit down and figure out a permanent fix for this yet.  Soon...

---

### Post by Zappastián on 2009-01-19
WOW that was quick! Thanks pal. There will never be a support team as good as ubuntu community. Another question: at point 3 in your instructions you mention a firmware file. Where am I supposed to get that?

Zappa

---

### Post by brteag00 on 2009-01-19
> **Zappastián said:**
> WOW that was quick! Thanks pal. There will never be a support team as good as ubuntu community. Another question: at point 3 in your instructions you mention a firmware file. Where am I supposed to get that?


Oh, the joys of being stuck at work on MLK day ...

The three files that post #94 references are linked earlier in the thread.

---

### Post by Zappastián on 2009-01-19
I'm installing now. Will post results.

---

### Post by jetpeach on 2009-01-19
i have a dell mini 12 with hardy from dell, i haven't change the configuration at all, except to update packages from the dell lpia repos.

i am also having this x-crash error
from the syslog
"gdm_slave_xioerror_handler: FatalX error - Restarting :0"
but my understanding is that is just a generic gdm crashing error.

so from the X gdm logs,  /var/log/gdm/:0.log.1 contains
"
Fatal server error:
Driver failed PrepareAccess on a pinned pixmap

(EE) Failed locking memory manager: "Device or resource busy".
"

i was reading through, but it wasn't clear. 
1st- this -is- happening to other people with the clean dell provided ubuntu, correct? it seems to some it is, but others it is not.
2nd- it's -not- improved by upgrading to the 2nd bios revision, correct?
3rd- and most importantly, is there a fix for it?

any help would be greatly appreciated!
thanks,
jetpeach

ps. should i start a separated thread perhaps for this issue? if it is common, i should think it to have its own thread, but maybe once i know what is causing it another thread is already out there... so i'll wait to see what advice people can give here, since ya'll seem to be pros on this :)

---

### Post by Zappastián on 2009-01-20
Just posting again to thank the people who had colaborated in this thread. Installation went OK.
Zappa

---

### Post by marduk667 on 2009-01-20
I also did the UNR installation as described in Post 94. Everything went fine, it is a bit faster than intrepid/386 and also 3D and Suspend/Hibernate works.

But...does anyone of you use pulseaudio? I have not one machine on which it works, so i also removed it from the Mini 12 (Skype does not work with it here).

Ahh...and does right-click on the desktop work for you? i dont get the context menu

Edit: Ahaa Zattoo is also working full screen, great :)

---

### Post by brteag00 on 2009-01-20
> **marduk667 said:**
> 
But...does anyone of you use pulseaudio? I have not one machine on which it works, so i also removed it from the Mini 12 (Skype does not work with it here).


Yeah, PulseAudio was giving me fits, too, so I removed it.  No complaints.
> **marduk667 said:**
> 
Ahh...and does right-click on the desktop work for you? i dont get the context menu


No problem here.  Did you somehow disable Nautilus in your session properties?

---

### Post by marduk667 on 2009-01-20
Hm no, well that is no show stopper, i was just wondering. I can switch the Theme and Background by using the Settings Menu.

Everything else is working fine now. Bluetooth and 3G (you can use blueman, thats better than the standard BT applet), 3D, Suspend/Hibernate, Webcam...

That's really great :)

---

### Post by marduk667 on 2009-01-20
Okay it seems i have removed Nautilus from the Startup.

Do i just have to add nautilus to the session?

---

### Post by brteag00 on 2009-01-20
> **marduk667 said:**
> Okay it seems i have removed Nautilus from the Startup.

Do i just have to add nautilus to the session?

Yup, that's what's responsible for the desktop.

---

### Post by marduk667 on 2009-01-20
Solved this one. Don't know why that was set but i had to enable

show_desktop

in gconf_editor in apps -> nautilus -> preferences

---

### Post by brteag00 on 2009-01-20
> **marduk667 said:**
> Solved this one. Don't know why that was set but i had to enable

show_desktop

in gconf_editor in apps -> nautilus -> preferences

Probably a UNR-specific setting - you don't need the desktop if you're using ume-launcher.

---

### Post by kylecronan on 2009-01-20
> **jetpeach said:**
> 
...
so from the X gdm logs,  /var/log/gdm/:0.log.1 contains
"Fatal server error:
Driver failed PrepareAccess on a pinned pixmap

(EE) Failed locking memory manager: "Device or resource busy".

i was reading through, but it wasn't clear. 
1st- this -is- happening to other people with the clean dell provided ubuntu, correct? it seems to some it is, but others it is not.
2nd- it's -not- improved by upgrading to the 2nd bios revision, correct?
3rd- and most importantly, is there a fix for it?


1) Yes, this has also happened to me and at least one other person, with a clean Dell install.  2) It's unknown whether the bios update fixes this, but unlikely.  In any case, I don't recommend you try it because the bios updater turned my Mini 12 into a useless brick.  3) There have not yet been any reports of this bug with the UNR 1.0.1 install + Poulsbo 3D- see brteag00's post for instructions on this install.  However, I'm beginning to wonder if this is a hardware issue that only affects some  of the Mini 12s that Dell has shipped out (there's not much that is different in UNR to explain the resolution of such a serious bug).  You should try the UNR install and see if it still happens.  That's what I plan to do when I get mine back from Dell with a working bios!

> 
ps. should i start a separated thread perhaps for this issue? if it is common, i should think it to have its own thread, but maybe once i know what is causing it another thread is already out there... so i'll wait to see what advice people can give here, since ya'll seem to be pros on this :)

It might be good to have another thread, especially if this bug occurs in all Ubuntu variants.  Definitely post a comment to the bug I entered in launchpad: if lots of people report being affected by the bug they may just fix it quickly.

[https://bugs.launchpad.net/belmont/+bug/317390](https://bugs.launchpad.net/belmont/+bug/317390)

---

### Post by floquet on 2009-01-20
To Kylecronan

This may be the fix for the clicking noise of your hard disk. I will try the fix over the weekend
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)
This web explains how to apply the fix (sorry it's in spanish)
[http://www.muylinux.com/2009/01/19/el-problema-de-ubuntu-en-portatiles-resuelto/](http://www.muylinux.com/2009/01/19/el-problema-de-ubuntu-en-portatiles-resuelto/)

---

### Post by kylecronan on 2009-01-20
Yeah, brteag suggested that workaround earlier.  Thanks for the link though, the comments contain a few nuggets that could be useful to us:

[INDENT]Default value for APM is 128 after a clean install of Gutsy Gibbon. A value of 192 or bigger, set with "hdparm -B", seems to be the range of values with no load cycles.[/INDENT]

[INDENT]Keep in mind that you can change the acpi spindown time in /etc/defaults/acpi-support. restarting the acpi-support service should enable the new times.[/INDENT]

Looks like changing the spin-down time might be preferable to turning off power management on the drive entirely.

---

### Post by Zappastián on 2009-01-21
I am getting errors when updating (did the #94 UNR install). It seems that the ubuntu repos specific for the mini architecture are not available? When unchecking the boxes in the Ubuntu tab (software origins) the error messages are gone but then of course no actualization is made.
Besides that, everithing seems to be working fine.

Zappa

---

### Post by marduk667 on 2009-01-21
Here all updates went fine

---

### Post by jabronioh on 2009-01-21
kylecronan - I had system crashes regularly with the Dell install, even after I re-installed myself and now with UNR, I have not had one crash...just a bad image from Dell, in my opinion.

---

### Post by kylecronan on 2009-01-21
This is amazing.  UNR and Belmont have the same exact kernel.  Belmont has xserver-xorg-video-psb version 0.16.0+repack-0ubuntu1~804um5netbook1 (most absurd version number ever, btw) and the one from ubuntu-mobile PPA is 0.16.0+repack-0ubuntu1~804um6.  The xorg versions are identical.  We use the same modules for 3D since they came from Belmont originally.

The only difference I see to explain this is the new um6 version of the xorg driver.  Ah, here is the changelog for this revision- this could be the fix:

```

xserver-xorg-video-psb (0.16.0+repack-0ubuntu1~804um6) hardy; urgency=low

  * New patch, 108_smaller-exa-pixmaps, Use smaller EXA pixmaps; fixes a video
    corruption in Mahjongg; LP: #262308

```

And the bug report: [https://bugs.launchpad.net/moblin-other/+bug/262308](https://bugs.launchpad.net/moblin-other/+bug/262308)
If this is it, it affects a whole lot more than Mahjongg.

---

### Post by kylecronan on 2009-01-21
I didn't realize that bug report was set to private.  Here is the link again, for anyone who has seen the xorg crash in the Dell image and would like to report it:

[https://bugs.launchpad.net/belmont/+bug/317390](https://bugs.launchpad.net/belmont/+bug/317390)

---

### Post by marduk667 on 2009-01-22
Hey Kyle,

i also subscribed to the bug.
Did you here anything from DELL about your Mini? Will you get it repaired?

---

### Post by kylecronan on 2009-01-22
Well, after Dell told me they were sending out a tech to swap my mainboard, it turned out that I don't qualify for that service.  So I sent it in to Dell for service.  They promised not to mess with my hard drive, but I'm really worried about that because it has unsaved data on there!

---

### Post by marduk667 on 2009-01-23
ok, please keep us uptodate, i am very interested in how the dell support works

btw: has anybody tried to use the support tag in the support portal? mine did not work.

---

### Post by CrazyDesi on 2009-01-23
Any word on if 9.04 will fix this?

---

### Post by marduk667 on 2009-01-24
Right now i got updates for libdrm and the pulsbo graphics driver.
I think it was from the mobile ppa, anybody else got these updates?

Regards,
Dennis

PS: With the UNR-image i had 2 lockups since the installation. So its not as bad as in Intrepid, but still it is not completely stable.

---

### Post by marduk667 on 2009-01-24
After the installation of the patches and a reboot, 3D does not work any more:

> ERROR!  sizeof(PsbDRIRec) does not match passed size from device driver
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering


any idea?

Edit: So it was the psb-driver update, i reverted that and it seems to work fine again now.

---

### Post by jabronioh on 2009-01-24
marduk - I have the exact same thing....How did you revert?

---

### Post by marduk667 on 2009-01-24
create a file /etc/apt/preferences and add

Package: xserver-xorg-video-psb
Pin: version 0.15.0-0ubuntu1~804um4
Pin-Priority: 1000

Save the file and run apt-get update & apt-get upgrade then it will downgrade. But i still have a strange behaviour in X, sometimes windows are closing unexpectedly...

---

### Post by marduk667 on 2009-01-24
> But i still have a strange behaviour in X, sometimes windows are closing unexpectedly...

this is very annoying, anybody else with this problem?

---

### Post by jabronioh on 2009-01-24
marduk - I could not get the apt update to work...here is the output:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 99D6B21CC6598A30
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


any ideas?

---

### Post by marduk667 on 2009-01-24
It seems you are having problems in reaching the US Ubuntu mirrors, perhaps you should try another mirror...

---

### Post by brteag00 on 2009-01-24
> **marduk667 said:**
> create a file /etc/apt/preferences and add

Package: xserver-xorg-video-psb
Pin: version 0.15.0-0ubuntu1~804um4
Pin-Priority: 1000

Save the file and run apt-get update & apt-get upgrade then it will downgrade. But i still have a strange behaviour in X, sometimes windows are closing unexpectedly...

I think you've still got mismatched driver/binary bits.  The working version from the ubuntu-mobile PPA is 0.16.0+repack-0ubuntu1~804um6.  You might have to download and install it manually:

```


brian@pol:~$ wget http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xserver-xorg-video-psb/xserver-xorg-video-psb_0.16.0+repack-0ubuntu1~804um6_lpia.deb 
brian@pol:~$ sudo dpkg -r xserver-xorg-video-psb
brian@pol:~$ sudo dpkg -i xserver-xorg-video-psb_0.16.0+repack-0ubuntu1~804um6_lpia.deb 

```

I'm not familiar with the /etc/apt/preferences trick you use - what I've been doing is going into synaptic, selecting that package and hitting "Lock version."  Stops the automatic updates from bugging me about the new release.

I can also confirm that the 0.20.0 version breaks 3D - probably a mismatch with psb_dri.so.  Still waiting for Intel to release this stuff for real...

---

### Post by jabronioh on 2009-01-24
Fixed and Locked! 

Back to 3D and I can really tell the difference.

Thanks guys, I owe ya.....again!

---

### Post by kdubya on 2009-01-25
Has anyone been able to compile VA-API enabled mplayer?  The video chip in this thing can decode 1080p MPEG2/h264/DIVX/WMV/VC-1.  I cannot get it to compile. I keep getting an undefined reference in the VA-API stuff, so I think it isn't linking to the libraries correctly.  Someone that knows more than me try it out, you can get the patches and instructions here: [http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/)

compiling mplayer is painfully slow on a 1.3ghz atom...

---

### Post by marduk667 on 2009-01-25
> brian@pol:~$ wget [http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xserver-xorg-video-psb/xserver-xorg-video-psb_0.16.0+repack-0ubuntu1~804um6_lpia.deb](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xserver-xorg-video-psb/xserver-xorg-video-psb_0.16.0+repack-0ubuntu1~804um6_lpia.deb) 
brian@pol:~$ sudo dpkg -r xserver-xorg-video-psb
brian@pol:~$ sudo dpkg -i xserver-xorg-video-psb_0.16.0+repack-0ubuntu1~804um6_lpia.deb

They have deleted the file, i found it in my apt cache.

---

### Post by planeoldjim on 2009-01-25
I don't guess there is a install ubuntu on a mini 12 for dummies, I have read all your threads and am not linux savy enough to understand what you are talking about. has anyone posted a link to the dell image or at least a working image for the mini 12 without having to modify all those settings? 

Thanks for any help and your patience...
(FIRST experience with linux)

---

### Post by marduk667 on 2009-01-25
I can REALLY not recommend to use the DELL image, as it is very unstable!
If you really want it contact me via PM.

It is not very hard to install the UNR-image and do the changes you need, and i think everybody here will help you if you are stuck...

---

### Post by brteag00 on 2009-01-25
> **planeoldjim said:**
> has anyone posted a link to the dell image or at least a working image for the mini 12 without having to modify all those settings? 

Thanks for any help and your patience...
(FIRST experience with linux)

First off, welcome to Ubuntu, and Linux in general!  These forums are a great place to look for answers to your questions - if you have a problem, it's most likely that other people have, too.

As for Ubuntu on the Dell Mini 12, here's the current state of things.
[LIST]
[*]If you're asking for the Dell image, I assume you didn't order your Mini 12 with Ubuntu pre-installed.  Unfortunately, the Dell image includes several pieces of software that are not redistributable - a set of codecs from Fluendo, and a DVD player are the most obvious.  So noone can (legally) set you up with a copy.
[*]You probably don't want the Dell image anyway.  Several people on this thread have reported that it's unstable.
[*]The hardware in the Mini 12 is surprisingly well-supported.  If you wanted to install the latest version of Ubuntu (Intrepid Ibex, ver. 8.10), then you would have a mostly-working system.
[*]The only thing that would be working less-than-perfectly is the video card, which would not give you (quite) the full resolution of the screen and would be rather slow.  Depending on your needs, this might be okay - though dragging windows, etc. is noticeably slow.
[*]If want fully working 2D graphics, there are several bits you need - a couple of Linux kernel drivers and a new driver for the X server (windowing system on top of the Linux kernel, like Windows on top of DOS).  The easiest way to get these is to install the Ubuntu Netbook Remix as described on [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR).  The only settings you need to tweak if you do this is to disable "ume-launcher" and "maximus" in the Session settings - they're useful on little Eee PCs, but not so much on the Mini 12 (which has a "real" screen.)
[*]You can probably ignore the rest of the thread - it's mostly about getting 3D graphics and accelerated video working, which requires some additional finagling.
[/LIST]

Depending on your background, if this is your very first Linux experience, maybe I would steer away from trying it on the Mini 12.  The issue, as always, is hardware support - most desktop hardware is phenomenally well-supported nowadays, and I would whole-heartedly recommend the latest version of Ubuntu.  Unfortunately, the video card in the Mini 12 is still really new on the market, and it hits at a bad time - the state of video drivers in the Linux world is kind of in flux right now.  We're all hoping that things settle down over the next 6 months or so so that we won't have to go through these contortions!

Of course, if you're a geek who's interested in getting started with this stuff and is willing to put up with a little frustration along the way, feel free to give it a go.  Post #94 in this thread is the most relevant, Google is your friend, and if you can't figure it out after some looking, post here and we'll puzzle over it.  Good luck!

---

### Post by brteag00 on 2009-01-25
> **kdubya said:**
> Has anyone been able to compile VA-API enabled mplayer?  The video chip in this thing can decode 1080p MPEG2/h264/DIVX/WMV/VC-1.  I cannot get it to compile.

Out of curiosity, where did you get your libva1 and libva-dev packages?

As with other experiences on this thread, it seems the person who did the FFmpeg integration had access to code (or at least a different setup) than we do.  First, the configure script is looking for headers and packages files in different places than are installed on my system.  Second, there are a number of VA-API structure members that the code refers to, but aren't available in the public code.

The configure script changes were easy.  The other stuff I just ripped out wholesale.  In doing so, I have managed to compile mplayer against libva.

When I try to use it, though, it's looking for yet another binary blob.  jabronioh and marduk667, could you dig through the Dell image for yet another file?  /usr/X11R6/lib/modules/dri/psb_drv_video.so is what mplayer is asking for, though it might also be in /usr/lib/xorg somewhere.

> **kdubya said:**
> compiling mplayer is painfully slow on a 1.3ghz atom...

It is that.  I'm 1.6 Ghz, which is a little better ... but it's still ~45 min.

---

### Post by brteag00 on 2009-01-25
> **brteag00 said:**
> 
When I try to use it, though, it's looking for yet another binary blob.  jabronioh and marduk667, could you dig through the Dell image for yet another file?  /usr/X11R6/lib/modules/dri/psb_drv_video.so is what mplayer is asking for, though it might also be in /usr/lib/xorg somewhere.


Additionally, it might be fun to tar up the following files:
```

/usr/lib/libva.so.0.29.0
/usr/lib/pkgconfig/libva.pc
/usr/lib/libva.la
/usr/include/va_dri.h
/usr/include/va.h
/usr/include/va_backend.h
/usr/include/va_x11.h
/usr/X11R6/lib/modules/dri/dummy_drv_video.so
/usr/X11R6/lib/modules/dri/dummy_drv_video.la

```

and see if they've got the additional fields in them.

---

### Post by kdubya on 2009-01-25
> **brteag00 said:**
> Out of curiosity, where did you get your libva1 and libva-dev packages?
I am using the libva1 that Dell ships.  I cannot find an up to date libva-dev package, so I just got the header files off the the git repo and dumped them in /usr/include.  I have no idea if this is valid, but it seemed like a reasonable thing to try.


> **brteag00 said:**
> First, the configure script is looking for headers and packages files in different places than are installed on my system.
The developer is using Debian, so it looks like the package he is using must have dumped the headers to a slightly different path.

---

### Post by planeoldjim on 2009-01-25
> **marduk667 said:**
> I can REALLY not recommend to use the DELL image, as it is very unstable!
If you really want it contact me via PM.

It is not very hard to install the UNR-image and do the changes you need, and i think everybody here will help you if you are stuck...

I am very willing to try, just a little lost. I am attempting to install onto my mini from usb stick, it gets to a certain point and stops with a command prompt of ubuntu@ubuntu:~ or somthing close to that. Where or how do I edit the items discused in the previous links, from the command prompt? from a working version on another computer? Again thanks for the help and patience!  -Jim

---

### Post by kylecronan on 2009-01-25
Are you attempting to install UNR, or Intrepid, or something else?

---

### Post by planeoldjim on 2009-01-25
intrepid i think 8.10 latest edition

---

### Post by brteag00 on 2009-01-25
> **planeoldjim said:**
> intrepid i think 8.10 latest edition

See my post a page back.  For this hardware, I strongly recommend the UNR (Ubuntu Netbook Remix) image:  [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

---

### Post by kylecronan on 2009-01-26
Another question: are you trying to install Ubuntu on a second partition, or are you willing to get rid of Windows completely?  From what I saw when I downloaded UNR, its installer assumes that you want to wipe the whole disk.

---

### Post by marduk667 on 2009-01-26
You can get libva here:

[https://launchpad.net/~repro-moblin-image/+archive](https://launchpad.net/~repro-moblin-image/+archive)

---

### Post by brteag00 on 2009-01-26
> **marduk667 said:**
> You can get libva here:

[https://launchpad.net/~repro-moblin-image/+archive](https://launchpad.net/~repro-moblin-image/+archive)

Yeah, that's where I got mine.  As I mentioned above, they're substantially different than the ones the mplayer patch was coded against.

Still looking for someone's /usr/X11R6/lib/modules/dri/psb_drv_video.so ...

---

### Post by marduk667 on 2009-01-26
Hey i have not extracted the image yet, but as far as i did it (maybe tomorrow) i will upload the files.

What did you change to compile mplayer?

---

### Post by kdubya on 2009-01-26
That libva1 is the same one that ships with the Dell installation.  

I will tar up my psb_drv_video.so with those other files when I get home.

---

### Post by kdubya on 2009-01-27
Here is my psb_drv_video.so and psb_drv_video.la

---

### Post by marduk667 on 2009-01-27
Ah thanks...i just wanted to extract my image...

---

### Post by CrazyDesi on 2009-01-27
I'm a little confused on the UNR.  Is it based on 8.04 or 8.10?

Also is the UNR beneficial?  The original Dell image is really slow.  Is battery the same?

---

### Post by kdubya on 2009-01-27
> **CrazyDesi said:**
> I'm a little confused on the UNR.  Is it based on 8.04 or 8.10?

Also is the UNR beneficial?  The original Dell image is really slow.  Is battery the same?

UNR is just some extra packages for Ubuntu.  You can get it for 8.04 or 8.10. However there are no 3d drivers for the x server in 8.10, so people are using 8.04.

And the Dell image is not slow, the machine is slow.  It weighs nothing and costs nothing, something has to give.  If you are using the Dell image then you need to run it in standard full desktop mode not whatever weird mode it ships with.  That desktop launcher is hideous, slow and completely useless.

---

### Post by CrazyDesi on 2009-01-27
> **kdubya said:**
> UNR is just some extra packages for Ubuntu.  You can get it for 8.04 or 8.10. However there are no 3d drivers for the x server in 8.10, so people are using 8.04.

And the Dell image is not slow, the machine is slow.  It weighs nothing and costs nothing, something has to give.  If you are using the Dell image then you need to run it in standard full desktop mode not whatever weird mode it ships with.  That desktop launcher is hideous, slow and completely useless.

What is post 94 referring to then?

---

### Post by brteag00 on 2009-01-27
> **kdubya said:**
> UNR is just some extra packages for Ubuntu.  You can get it for 8.04 or 8.10. However there are no 3d drivers for the x server in 8.10, so people are using 8.04.


This is incorrect on several levels.

First, the UNR is based on Ubuntu 8.04 (Hardy), and it does indeed have several extra packages (ume-launcher, maximus, etc.) - but it also uses a different architecture, lpia ("low-powered intel architecture.")  Packages built for the lpia architecture have different compiler optimizations enabled that (supposedly) make them run faster on the Atom (with its small cache, for example.)  Most i386-architecture .debs should run fine on the lpia architecture, but many of them won't install because the person who built the package didn't anticipate lpia being binary-compatible with i386.  (If you're just going to stick with software from the Ubuntu repositories, it's not a problem.)

The other thing that you get with a new architecture are architecture-specific kernel parameters.  In this case, the UNR includes two kernel modules that are not available in the stock-standard Hardy install: psb.ko and drm_psb.ko modules.  These modules are required to run the xserver-xorg-video-psb Xorg driver, which you need if you want full screen resolution on the display.  If you use a stock Ubuntu installation, either 8.04 or 8.10, then you're stuck using the VESA drivers which max out at 1024x768, which your screen will then scale to 1280x800.  Not the optimal solution.  

Yes, you also need the UNR drivers for 3D and hardware-accelerated video - but those are just icing, and not required for day-to-day use.  (Compiz doesn't work anyway.)  If you want to get the most out of this hardware under Linux, you need to either use the Dell image (which might not be your best bet - see below), or follow the first two steps from post #94 on this thread to use the UNR image.

> **kdubya said:**
> 
And the Dell image is not slow, the machine is slow.


I havn't seen any benchmarks, but there are several people on this thread who have reported that the UNR installation as per post #94 is faster and more stable than the Dell-supplied image.  YMMV.

> **kdubya said:**
> 
It weighs nothing and costs nothing, something has to give.  If you are using the Dell image then you need to run it in standard full desktop mode not whatever weird mode it ships with.  That desktop launcher is hideous, slow and completely useless.

Agreed on all points.  This machine is meant for consumption and light productivity, not for serious work.  On the other hand, it weighs ~2 lbs and gets 5.5 hrs of battery life on the 6-cell battery.  I'm not sure what launcher Dell is using, but if it's based on ume-launcher, get rid of it - pull up a terminal, type 'gnome-session-properties', and de-select 'ume-launcher' and 'maximus' from the list of startup programs.  That will get you back to the standard GNOME desktop, which is plenty-usable with this much screen real-estate.

---

### Post by brteag00 on 2009-01-28
> **brteag00 said:**
> If you want to get the most out of this hardware under Linux, you need to either use the Dell image (which might not be your best bet - see below), or follow the first two steps from post #94 on this thread to use the UNR image.

Oh yeah, one other thing.

The folks at Canonical seem to have some source code from Intel that's not publicly available - this is what ends up in the psb kernel and Xorg drivers.  These are substantially different than drivers at [http://moblin.org](http://moblin.org), whose repositories havn't been touched in over 6 months.  So, unless you want to try cross-porting the stuff from Ubuntu over to Fedora (or Gentoo or SuSE...etc), your best bet is to stay with Ubuntu in general, and the UNR in particular.  It makes me sad, too, because Fedora is my preferred distro (/me ducks).

Hopefully this will get sorted out soon.  Till then, this is what you're stuck with.

---

### Post by kdubya on 2009-01-28
Is there no lpia for 8.10?  I was under the impression that UNR was just some extra packages for lpia, and you could get an install image that had them installed by default.

---

### Post by brteag00 on 2009-01-28
> **kdubya said:**
> Here is my psb_drv_video.so and psb_drv_video.la

Sweet, thank you.  Here's an updated build script and a patch for mplayer-vaapi - the next post has detailed instructions for installing and using it.

---

### Post by brteag00 on 2009-01-28
> **kdubya said:**
> Is there no lpia for 8.10?  I was under the impression that UNR was just some extra packages for lpia, and you could get an install image that had them installed by default.

The UNR image is Hardy + a few extra packages + the custom kernel with the psb modules (and maybe some other stuff, I'm not sure.)  There is no stock 8.04 lpia image, just the UNR image.  You can get an "MID" image for 8.10 that is lpia architecture as well, but it comes with a 2.6.27 kernel, and the psb kernel modules are only available for 2.6.24 (in 8.04).

---

### Post by brteag00 on 2009-01-28
> **brteag00 said:**
> The next post has detailed instructions for installing and using it.

As promised, instructions for hardware-accelerated video decoding on the Mini 12, plus a few test results.  These instructions assume you're using a UNR-based install like I described in post #94, but the instructions should also work for you if you're using the Dell-provided image.

[LIST=1]
[*] Add the following two lines to your /etc/apt/sources.list
```

deb http://ppa.launchpad.net/repro-moblin-image/ubuntu hardy main
deb-src http://ppa.launchpad.net/repro-moblin-image/ubuntu hardy main

```
[*] Install libva1 and libva-dev from the PPA you just added.  Dell image users will already have libva1 installed.
```

brian@pol:~$ sudo apt-get install libva1 libva-dev

```
[*] If you don't have them already, download the drivers from kdubya's post #214.  Un-tar the two files and put them in /usr/X11R6/lib/modules/dri.  There should already be dummy_drv_video.so and dummy_drv_video.la in that directory.
[*] Download the mplayer patch from [http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/) -- I'm using mplayer-vaapi-20090123.tar.bz, the latest as of this writing.  Un-tar it in your home directory.
[*] Download the script and patch attached to post #222, and put them *in the directory that you just uncompressed from mplayer-vaapi-20090123.tar.bz*.  Afterwards, the directory should have the following files in it:
```

brian@pol:~/src/mplayer-vaapi-20090123$ ls
checkout-patch-build.sh      mplayer-vaapi.patch       README.txt
checkout-patch-build-unr.sh  mplayer-vaapi-unr.patch
mplayer-vaapi                mplayer-vaapi-unr.tar.gz

```
[*] Run checkout-patch-build-unr.sh.  It should download an SVN copy of the mplayer sources, apply both mplayer-vaapi.patch and mplayer-vaapi-unr.patch, and then configure and build mplayer.  Go get a cup of coffee - on my 1.6 Ghz Atom, it took ~30 minutes.
[*] Run your newly created mplayer binary as per the instructions at [http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/)
[/LIST]

A few test results.
[LIST]
[*] Several MPEG-2 clips, pulled off my MythTV box, played perfectly.  I tried a 720p clip and two 1080i clips - the interlacing is really noticable at 30 Hz (NBC affiliate broadcast), and the hardware acceleration prevents you from using a deinterlacer.  The FOX affiliate broadcasts 60 Hz, though, which looks spectacular.
[*] An MPEG-4 clip, 1080p, part of Big Buck Bunny from [http://www.bigbuckbunny.org](http://www.bigbuckbunny.org) .  This clip failed to play - mplayer threw an error.  It's not clear if this is a bug in the mplayer VA-API implementation, or the video decode library, or what.
[*] An H.264 clip, 1080p, also from Big Buck Bunny.  This clip played, but was full of annoying visual artifacts: parts of the screen would jitter up and down as the camera panned around.  It's not clear whether this is due to the H.264 stuff I had to rip out to get compatibility with the publicly available libva API, or whether it's the bug that the mplayer-vaapi author mentions.
[*] I don't have any WMV3 or VC-1 clips on hand, and am not particularly motivated to go looking for them.  Sorry, not interested in supporting Microsoft on this one.
[/LIST]

At the end of the day, hardware-assisted video decoding with mplayer and vaapi is still obviously a work-in-progress.  Not only did bugs interfere with 2 of the 3 codecs I tried, but you have to know how your video is encoded up front: the vaapi video output routine doesn't select the right video format for you, which is a pain.  That said, the hardware decodes 1080i@60Hz using only 20% of the processor, which is pretty stellar.  This would make an excellent set-top box if the software situation were to improve.  Note to self - check out MythTV's VA-API implementation...

---

### Post by CrazyDesi on 2009-01-28
K I just finished removing Dells image and replacing it with UNR according to post 94.  There is a considerable question; however, I still have some questions.

1.  I have followed brteag00's post on getting mplayer to work.  I haven't finished compiling it but it seems to be a standalone.  Is there a way to make it the default media player.

2.  Has any one been able to get Compiz working?

3.  Anybody have a technique to get longer battery life?  I am getting about 2 and a half with a 3-cell and I need around 3 hours :(.

4.  Whenever I hit "/" a series of the character keeps getting printed.

---

### Post by kdubya on 2009-01-28
brteag00, you are awesome.  I am going to give this a try when I get home.

And I am pretty sure Myth doesnt have vaapi support, only vdpau.  vdpau works great in myth.

---

### Post by brteag00 on 2009-01-28
> **CrazyDesi said:**
> 
1.  I have followed brteag00's post on getting mplayer to work.  I haven't finished compiling it but it seems to be a standalone.  Is there a way to make it the default media player.

This won't work as the default media player, because it can't auto-detect the stream type, and it won't fall back to un-accelerated decoding for unsupported streams.  Until this is better supported, it's just a toy and a tech demo.

> **CrazyDesi said:**
> 
2.  Has any one been able to get Compiz working?

Please read the rest of this thread.  The short answer is "no, the driver doesn't support it."

> **CrazyDesi said:**
> 
3.  Anybody have a technique to get longer battery life?  I am getting about 2 and a half with a 3-cell and I need around 3 hours :(.

That sounds about right for a 3-cell battery.  You can find other tricks for using less power at [http://www.lesswatts.org/](http://www.lesswatts.org/) - in particular, try out PowerTop.

> **CrazyDesi said:**
> 
4.  Whenever I hit "/" a series of the character keeps getting printed.

That's nothing I've ever seen.  Did you select an odd keyboard layout when you installed?  In the main GNOME menu, select System > Preferences > Keyboard and make sure that none of the settings are screwy (ie, accessibility is off, your layout is appropriate for your region, etc.)

---

### Post by kdubya on 2009-01-28
> **CrazyDesi said:**
> 
4.  Whenever I hit "/" a series of the character keeps getting printed.

This reminds me, WHAT THE HELL AM I PRESSING TO PASTE.  Somehow when I am typing I bump something that is doing a middle click, and pasting the last thing I highlighted.  I know there is no way I am hitting both mouse buttons at the same time, it is something else.  Does anyone else have this problem?  It is annoying as all hell.

---

### Post by CrazyDesi on 2009-01-28
Do you get stutter with youtube?  I keep getting a great deal of stutter.  Should I change my flash player to something other than adobe flash?

---

### Post by marduk667 on 2009-01-28
This could also be a pulseaudio problem. close the firefox and do a killall pulseaudio in a terminal, then restart firefox

---

### Post by kdubya on 2009-01-28
slow processor + horrible linux code in flash

choppy youtube

---

### Post by CrazyDesi on 2009-01-28
Has anyone tried flash on other netbooks?

---

### Post by CrazyDesi on 2009-01-28
I installed the UNR version and got 3d working, etc.  It was fast at first, but now X just closes on its own.  Firefox closes after around 3 minutes of use.  I have reverted back to the original Dell image for now.  Any one else having this problem?  The original Dell version did not crash for me.

---

### Post by kdubya on 2009-01-28
Of course, the day after we go through all of this trouble getting mplayer compiled with the right libva, the developer posts libva and libva-dev debs on his website.

[http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/](http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/)

---

### Post by CrazyDesi on 2009-01-28
Well I reinstalled the UNR version without the 3d accelaration and video acceleration.  It works pretty well now.  I got youtube going at full speed and firefox, openoffice, etc. open up extremely quick.  I don't know why the 3d acceleration stuff made it work so slow.  Hopefully, Dell will provide drivers to work with it.

---

### Post by mandel on 2009-01-28
Apologies for backing up a bit..

For those of you using the PSB driver with 2.6.27+ (and I assume I am reading this thread correctly and that there are a few of you doing so) are you successfully able to use it with resolutions higher than 640x480?

---

### Post by marduk667 on 2009-01-29
@mandel, i used it but now i have also installed UNR (8.04.2), and yes, it worked with 1280x800 but you had to patch the kernel modules and build the psb.ko module for that kernel...

@crazydesi: i am pretty sure that you have installed the wrong psb driver from the ppa, they have uploaded a new one and with this the X-Server is very unstable if you are using 3D. Somewhere in this thread (~page 20) i have posted the correct psb-driver deb.

---

### Post by CrazyDesi on 2009-01-29
Ok I will try it later on tonight when I get home.  Unfortunately, my Dell has had a problem and must be returned.  The "/?" key is messed up :(.  It might be a motherboard problem.  Hopefully, it will be just a keyboard problem.

---

### Post by kylecronan on 2009-01-29
Hey everyone, I got my laptop back ok from Dell support.  I won't be trying a bios update again anytime soon!

Have we all somehow missed the existence of an lpia version of Intrepid?:

[http://cdimage.ubuntu.com/ports/releases/8.10/release/ubuntu-8.10-alternate-lpia.iso](http://cdimage.ubuntu.com/ports/releases/8.10/release/ubuntu-8.10-alternate-lpia.iso)

It will require the manual patching of DRM sources as before, but maybe this image is worth a try as one possible starting point.  I think I'll give it a try.  Although I don't see where the package files for this would even be hosted on any of canonical's servers- there are no lpia debs on the usual archive.ubuntu.com servers.

---

### Post by teatimest on 2009-01-29
This thread is going long and long, so someone might have already answered this question.... but,

Can I set UNR dual-boot with XP on mini 12, or will UNR uses entire disk?

Thanks.

---

### Post by CrazyDesi on 2009-01-29
I installed the 3d drivers and they work now that I am using Marduks improved image.  Anyone noticing a large increase in CPU usage from this?

---

### Post by mandel on 2009-01-29
@marduk667

Cool thanks.  I did in fact get everything patched up and working and did finally get full resolution working.  Any particular you reason you went back to the older kernel?

---

### Post by kylecronan on 2009-01-29
> **teatimest said:**
> This thread is going long and long, so someone might have already answered this question.... but,

Can I set UNR dual-boot with XP on mini 12, or will UNR uses entire disk?

Thanks.

If you want to install UNR on a partition that takes up only part of your drive you have two options:

1) install UNR first, then resize your partition with parted or similar, in order to make room for Windows.  Install XP with a USB cdrom or something.

2) leave Dell windows installed (after stripping out all the Dell crud of course: ), but shrink the volume to make space for linux.  You won't be able to use UNR's installer, so here's what you do:  Boot from a livecd to a root shell and do your fdisk and mkfs.ext3 for the linux partition.  Mount the install image on a loop device (pass "-o loop" to mount) and when you look inside it you will see a rootfs.img and a bootfs.img.  These can also be mounted with -o loop: copy the contents of the former to / and the latter to /boot in your new linux filesystem.  Do a 'mount -o bind /dev /mnt/dev' to make your device files available and then chroot into your new linux system.  You should now be able to run grub and install the boot loader onto your drive with the setup command (if you are missing some stageN files in /boot/grub then copy them over from another install- the setup command will now work).

--

Can anyone explain to me why I have Xpsb and psb_dri and the firmware file in my filesystem already, with this manual install I did of the UNR image from oem-images?  Did they sneak these in or something?  I don't get it.  This is before pulling down any updates from netbook-remix.archive.canonical.com.

---

### Post by CrazyDesi on 2009-01-29
So found I have found that installing the UNR 1.01 image with the pbs drivers from the repository has worked the most stable, provided the most battery life, and been the fastest.  Yet, this will not provide you with 3d or video acceleration.  I don't really need that though.  I find that this allows me most of the "netbook" tasks with good battery life.

---

### Post by kylecronan on 2009-01-29
> **CrazyDesi said:**
> So found I have found that installing the UNR 1.01 image with the pbs drivers from the repository has worked the most stable, provided the most battery life, and been the fastest.  Yet, this will not provide you with 3d or video acceleration.  I don't really need that though.  I find that this allows me most of the "netbook" tasks with good battery life.

Can you be more specific on the psb driver version that works well for you? (maybe do 'aptitude show xserver-xorg-video-psb')  I have 0.16.0+repack-0ubuntu1~804um5netbook1 without doing anything at all after install, and direct rendering is enabled (3D), though it seems kinda slow and jerky.

And at least somewhat more stable is 0ubuntu1~804um6, apparently?  (That's what I'm trying now.)

---

### Post by teatimest on 2009-01-30
Thank you for your detailed instruction!

I am a recent convert and the instruction #2 seems a little daunting...

So, I might go with UNR alone for this weekend and see if I am ready to make a switch.

> **kylecronan said:**
> If you want to install UNR on a partition that takes up only part of your drive you have two options:

1) install UNR first, then resize your partition with parted or similar, in order to make room for Windows.  Install XP with a USB cdrom or something.

2) leave Dell windows installed (after stripping out all the Dell crud of course: ), but shrink the volume to make space for linux.  You won't be able to use UNR's installer, so here's what you do:  Boot from a livecd to a root shell and do your fdisk and mkfs.ext3 for the linux partition.  Mount the install image on a loop device (pass "-o loop" to mount) and when you look inside it you will see a rootfs.img and a bootfs.img.  These can also be mounted with -o loop: copy the contents of the former to / and the latter to /boot in your new linux filesystem.  Do a 'mount -o bind /dev /mnt/dev' to make your device files available and then chroot into your new linux system.  You should now be able to run grub and install the boot loader onto your drive with the setup command (if you are missing some stageN files in /boot/grub then copy them over from another install- the setup command will now work).

--

Can anyone explain to me why I have Xpsb and psb_dri and the firmware file in my filesystem already, with this manual install I did of the UNR image from oem-images?  Did they sneak these in or something?  I don't get it.  This is before pulling down any updates from netbook-remix.archive.canonical.com.

---

### Post by CrazyDesi on 2009-01-30
For anyone that cares, I found a good repository for lpia based vlc.

deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main

It might help in getting the latest vlc player to play videos a tad bit faster.

---

### Post by jabronioh on 2009-01-30
My UNR install is running strong, no crashes and at least twice as fast as the factory Dell install.

I tried to install brteag00's mplayer-vaapi but withoug success. My output is as follows:

ken@ken:~/mplayer$ sudo ./checkout-patch-build.sh 
ERROR: you need VA API headers for this project

Not sure how to correct this, but according to brteag00's findings, maybe I am not missing so much.

As far as the battery is concerned, the 3 cell Li ion on this machine gives a lot of battery life, IMO. I originally had the Vista laptop with a 6 cell battery and it lasted forever! I am sure we can upgrade the battery from Dell relatively easily.

Finally, I just wanna say I am very happy now with my build and will probably wait and see if Jaunty has all our needs when it debuts.

---

### Post by kdubya on 2009-01-30
> **jabronioh said:**
> I tried to install brteag00's mplayer-vaapi but withoug success. My output is as follows:

brteag00's instructions and patches are no longer valid.  The mplayer-vaapi developer posted the correct libva and libva-dev debs for lpia on his website: [http://www.splitted-desktop.com/~gbeauchesne/libva/](http://www.splitted-desktop.com/~gbeauchesne/libva/)

Just install those and grab the mplayer build-deps.  The devloper's checkout-patch-build script works fine then.  Of course, there are still artifacts with h.264 that make it unusable.  It works great for mpeg2 though.

---

### Post by kylecronan on 2009-01-30
I just want to summarize the available info on psb driver versions: The 0.15 versions and 0.16 versions 0ubuntu1~804um5netbook1 and below are slow and unstable, even with UNR.  0.16.0+repack-0ubuntu1~804um6 is fine, and pretty stable even with direct rendering enabled (just the one crash report from Dennis so far).  However, it is only stable when used with UNR (perhaps this would also be true of other lpia compiled installs, like the jaunty mid image?).  Version 0.20 is no good, because the corresponding binary blobs are unavailable.

Now that they've pushed out 0.20, the _only_ place to get the working driver version is Dennis' post #198.

edit: After 25 pages I think I finally get what's going on.  You can install um6 on Belmont and everything is just great.  There was never any big issue with the Dell image, really.  It's not like they added some broken code to mess things up, they just only had um5netbook1 from Intel when that image was created.  The problem has been Intel's all along.  With um6 they found some way to kick the can down the road (actually i think they kicked it accidentally while trying to fix Mahjongg), but stability issues are still there and the driver seems pretty picky about configurations it likes.

---

### Post by CrazyDesi on 2009-01-30
> **kylecronan said:**
> I just want to summarize the available info on psb driver versions: The 0.15 versions and 0.16 versions 0ubuntu1~804um5netbook1 and below are slow and unstable, even with UNR.  0.16.0+repack-0ubuntu1~804um6 is fine, and pretty stable even with direct rendering enabled (just the one crash report from Dennis so far).  However, it is only stable when used with UNR (perhaps this would also be true of other lpia compiled installs, like the jaunty mid image?).  Version 0.20 is no good, because the corresponding binary blobs are unavailable.

Now that they've pushed out 0.20, the _only_ place to get the working driver version is Dennis' post #198.

edit: After 25 pages I think I finally get what's going on.  You can install um6 on Belmont and everything is just great.  There was never any big issue with the Dell image, really.  It's not like they added some 
broken code to mess things up, they just only had um5netbook1 from Intel when that image was created.  The problem has been Intel's all along.  With um6 they found some way to kick the can down the road (actually i think they kicked it accidentally while trying to fix Mahjongg), but stability issues are still there and the driver seems pretty picky about configurations it likes.
I'v actually found the latest drivers to be extremely fast and stable for 2d and every day work.  I can stream videos from my server and everything.  Have you tried them without the 3d acceleration?

---

### Post by kylecronan on 2009-01-30
I tried 0.20 and I see that it still works great with the valib stuff from Belmont (playing 1080p h264 with 17% cpu usage is pretty nice; ).  But I prefer to have direct rendering working, so I've pinned my video-psb package to um6.  Haven't noticed any difference in speed.

A really nice install is Belmont + dell updates, then add netbook-remix.archive to your sources.list and get the UNR updates, then add ubuntu-mobile PPA and get those updates!  Download the ~804um6 deb and install manually to restore working 3D.  System | Preferences | Switch Desktop Mode will give you back the normal gnome layout, then just remove the dell-launcher package (remove 'yahoo-toolbar-extension' while you're at it) and the nautilus desktop will come back to life.  totem and other gstreamer stuff can use libva, as in normal Belmont.  The lpia build of mplayer that's available doesn't do libva, but there must be some way to build that.

---

### Post by CrazyDesi on 2009-01-30
> **kylecronan said:**
> I tried 0.20 and I see that it still works great with the valib stuff from Belmont (playing 1080p h264 with 17% cpu usage is pretty nice; ).  But I prefer to have direct rendering working, so I've pinned my video-psb package to um6.  Haven't noticed any difference in speed.

A really nice install is Belmont + dell updates, then add netbook-remix.archive to your sources.list and get the UNR updates, then add ubuntu-mobile PPA and get those updates!  Download the ~804um6 deb and install manually to restore working 3D.  System | Preferences | Switch Desktop Mode will give you back the normal gnome layout, then just remove the dell-launcher package (remove 'yahoo-toolbar-extension' while you're at it) and the nautilus desktop will come back to life.  totem and other gstreamer stuff can use libva, as in normal Belmont.  The lpia build of mplayer that's available doesn't do libva, but there must be some way to build that.

What exactly does Direct Rendering provide?

---

### Post by kylecronan on 2009-01-30
It is for applications that use OpenGL.  Direct rendering means that the rendering of OpenGL visuals is handled by the video card instead of emulated in software (which is unusably slow).  It's one of the things needed for compiz to work- unfortunately compiz doesn't support this hardware anyway, at least not right now.  But hey, you don't want to be able to run quake? ;)

---

### Post by kylecronan on 2009-01-30
For those who have messed around with compiling mplayer- does anyone know what library is supposed to provide these ff_vaapi_* symbols?  I tried the mplayer-vaapi-20090128 build script, but it failed when it got to linking the binaries.  The ff_vaapi_ symbols aren't in the libva1 package shipped with Belmont, and I don't think they're in that 0.29-2ubuntu1 version either.  Maybe I have the wrong ffmpeg?

---

### Post by kdubya on 2009-01-30
> **kylecronan said:**
> For those who have messed around with compiling mplayer- does anyone know what library is supposed to provide these ff_vaapi_* symbols?  I tried the mplayer-vaapi-20090128 build script, but it failed when it got to linking the binaries.  The ff_vaapi_ symbols aren't in the libva1 package shipped with Belmont, and I don't think they're in that 0.29-2ubuntu1 version either.  Maybe I have the wrong ffmpeg?

You need to use the libva and libva-dev debs on the same website:

[http://www.splitted-desktop.com/~gbeauchesne/libva/](http://www.splitted-desktop.com/~gbeauchesne/libva/)

If you install those then it compiles and links fine.  Do NOT use the ones in Belmont.

---

### Post by kylecronan on 2009-01-31
I installed that version (thankfully it didn't seem to break anything, because with not all Belmont .deb's available there is no easy way to go back), but I still get the error:

```

libavcodec/libavcodec.a(h263dec.o): In function `decode_slice':
h263dec.c:(.text+0x437): undefined reference to `ff_vaapi_mpeg4_decode_slice_init'
h263dec.c:(.text+0x43f): undefined reference to `ff_vaapi_mpeg4_decode_slice'
libavcodec/libavcodec.a(h263dec.o): In function `ff_h263_decode_frame':
h263dec.c:(.text+0x15b6): undefined reference to `ff_vaapi_mpeg4_decode_slice_done'
h263dec.c:(.text+0x1736): undefined reference to `ff_vaapi_mpeg4_frame_end'
h263dec.c:(.text+0x1743): undefined reference to `ff_vaapi_mpeg4_frame_start'
h263dec.c:(.text+0x177f): undefined reference to `ff_vaapi_mpeg4_decode_slice_done'
libavcodec/libavcodec.a(h264.o): In function `decode_slice_header':
h264.c:(.text+0xf436): undefined reference to `ff_vaapi_h264_frame_start'
libavcodec/libavcodec.a(h264.o): In function `decode_nal_units':
h264.c:(.text+0x37505): undefined reference to `ff_vaapi_h264_decode_slice'
libavcodec/libavcodec.a(h264.o): In function `decode_frame':
h264.c:(.text+0x37f32): undefined reference to `ff_vaapi_h264_frame_end'
libavcodec/libavcodec.a(mpeg12.o): In function `decode_chunks':
mpeg12.c:(.text+0x60d0): undefined reference to `ff_vaapi_mpeg2_decode_slice'
mpeg12.c:(.text+0x6111): undefined reference to `ff_vaapi_mpeg2_field_end'
mpeg12.c:(.text+0x629e): undefined reference to `ff_vaapi_mpeg2_field_start'
mpeg12.c:(.text+0x62cf): undefined reference to `ff_vaapi_init_slice_data'
libavcodec/libavcodec.a(vc1.o): In function `vc1_decode_frame':
vc1.c:(.text+0x13177): undefined reference to `ff_vaapi_vc1_decode_picture'
collect2: ld returned 1 exit status
make: *** [mencoder] Error 1

```

This is when its trying to link mencoder.

---

### Post by marduk667 on 2009-01-31
Hey Kyle can you play 1080p Matroska Containers on the Mini12?
Is this possible with the UNR image?

---

### Post by kylecronan on 2009-01-31
I don't know: I couldn't find any test clips in that format.  If you get me a file I'll try it.

I'm sure all of this libva stuff can be got to work in UNR just as well as it does in the latest Belmont, but if you have access to Dell's image then why bother?  You can start with Belmont and, if you want, switch your sources.list over entirely.  You now have a machine that's tracking UNR, but with all the extra Belmont packages already installed (even the ones with no debs available).

---

### Post by brteag00 on 2009-01-31
> **kylecronan said:**
> I installed that version (thankfully it didn't seem to break anything, because with not all Belmont .deb's available there is no easy way to go back), but I still get the error:

```

libavcodec/libavcodec.a(h263dec.o): In function `decode_slice':
h263dec.c:(.text+0x437): undefined reference to `ff_vaapi_mpeg4_decode_slice_init'
...

```


This means 'configure' couldn't find libva or the header files and bailed.  Leave the libva1 and libva-dev .debs installed, but delete your mplayer build directory and try again.

---

### Post by brteag00 on 2009-01-31
> **kdubya said:**
> This reminds me, WHAT THE HELL AM I PRESSING TO PASTE.  

I was wandering around the synaptic driver's manpage and found the answer to your question.  Tapping the upper-right corner of the touchpad is the same as a middle-click, which is pasting the clipboard's contents.

---

### Post by Belveder on 2009-01-31
FYI:

This is what I just found minutes ago:

[http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/]("http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/")

[http://www.phoronix.com/scan.php?page=news_item&px=NzAyOQ]("http://www.phoronix.com/scan.php?page=news_item&px=NzAyOQ")

Greetings..

---

### Post by kylecronan on 2009-01-31
Great stuff- I've been wanting to write a rant like that for a while now!  Personally, I blame Intel for outsourcing the driver development to another company.  Obviously once that contract is over nobody is going to give a crap about maintaining the code.  Especially if the code is a mess.

---

### Post by kylecronan on 2009-01-31
> **brteag00 said:**
> This means 'configure' couldn't find libva or the header files and bailed.  Leave the libva1 and libva-dev .debs installed, but delete your mplayer build directory and try again.

Yeah I did delete the build directory.  I tried it again to make sure: same error.  The configure script isn't bailing- everything gets compiled but then it fails to link.

Google returns no hits for "ff_vaapi".  I'm not sure how to proceed: my whole procedure for debugging this kind of thing pretty much just calls exit() in that situation!  I wish the symbols hadn't been stripped from those shared objects.

---

### Post by CrazyDesi on 2009-01-31
> **kylecronan said:**
> I don't know: I couldn't find any test clips in that format.  If you get me a file I'll try it.

I'm sure all of this libva stuff can be got to work in UNR just as well as it does in the latest Belmont, but if you have access to Dell's image then why bother?  You can start with Belmont and, if you want, switch your sources.list over entirely.  You now have a machine that's tracking UNR, but with all the extra Belmont packages already installed (even the ones with no debs available).

Damn, I did it the other way and broke my system.  After I install Belmont, should I remove all the Dell sources?  What should the sources.list look like in the end?

---

### Post by kylecronan on 2009-01-31
I decided to leave the Dell sources in, so I guess I'll be tracking both Belmont and UNR going forward... not sure if it would be any safer to just pick UNR.  Here's my current sources.list, although I haven't confirmed that it also works if you try to do all the updates at once.  In my case, I did the updates and added sources in stages, as described a page or two back.

```

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted

deb http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main

```

With the um6 driver I've had two crashes over the course of 2 days of pretty heavy usage.  That's much better than before, but still highly annoying (on the other hand the need to find something to do with 3D has led me to discover armagetronad- omg so addictive!).  The only other issue I've noticed is firefox occasionally saying there is not enough memory to download a file (huh?).

---

### Post by kylecronan on 2009-01-31
[http://tech.slashdot.org/article.pl?sid=09/01/31/1859200](http://tech.slashdot.org/article.pl?sid=09/01/31/1859200)

Our plight is getting attention!  This is very good news!

---

### Post by CrazyDesi on 2009-01-31
> **kylecronan said:**
> I decided to leave the Dell sources in, so I guess I'll be tracking both Belmont and UNR going forward... not sure if it would be any safer to just pick UNR.  Here's my current sources.list, although I haven't confirmed that it also works if you try to do all the updates at once.  In my case, I did the updates and added sources in stages, as described a page or two back.

```

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted

deb http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main

```

With the um6 driver I've had two crashes over the course of 2 days of pretty heavy usage.  That's much better than before, but still highly annoying (on the other hand the need to find something to do with 3D has led me to discover armagetronad- omg so addictive!).  The only other issue I've noticed is firefox occasionally saying there is not enough memory to download a file (huh?).

Do you find it more stable than simply using the UNR?

---

### Post by kylecronan on 2009-02-01
My UNR install was all screwed up somehow, so I can't say for sure.  I suspect that what makes the difference is the xorg packages you're using, and in that case they are the same for both.  You can always move Xpsb.so out of the way and it's solid then.

---

### Post by CrazyDesi on 2009-02-01
I'll try it when I get mine back.  I got it sent back because the "?/" was sticky to the point that it made twenty characters per press.  In Linux, it was almost impossible to change directories.

---

### Post by teatimest on 2009-02-02
Hi kylecronan,

I hear the clicking noise coming from the hard drive, too.
And that is driving me crazy.
So, in order to change the APM value, what exactly should I do?

This is what I did...

sudo nano /etc/default/acpi-support

I see 
# Spindown time on battery
SPINDOWN_TIME=12

I should change this value to...?

Sorry for a really noob question.


> **kylecronan said:**
> Yeah, brteag suggested that workaround earlier.  Thanks for the link though, the comments contain a few nuggets that could be useful to us:

[INDENT]Default value for APM is 128 after a clean install of Gutsy Gibbon. A value of 192 or bigger, set with "hdparm -B", seems to be the range of values with no load cycles.[/INDENT]

[INDENT]Keep in mind that you can change the acpi spindown time in /etc/defaults/acpi-support. restarting the acpi-support service should enable the new times.[/INDENT]

Looks like changing the spin-down time might be preferable to turning off power management on the drive entirely.

---

### Post by kylecronan on 2009-02-02
I assumed this value was in seconds, but you were right to wonder about it.  This is from the hdparm man page:

[INDENT]The encoding of the timeout value is somewhat peculiar.  A  value  of  zero means  "timeouts are disabled": the device will not automatically enter standby  mode.   Values from  1  to 240 specify multiples of 5 seconds, yielding timeouts from 5 seconds to 20 minutes. Values  from  241  to  251 specify from 1 to 11 units of 30 minutes, yielding timeouts from  30 minutes to 5.5 hours.  A value of 252 signifies a timeout of 21 minutes. A value of 253 sets a vendor-defined  timeout period between 8 and 12 hours, and the value 254 is reserved. 255 is interpreted  as  21  minutes  plus  15 seconds. Note that some older drives may have very  different interpretations of these values.[/INDENT]

Maybe try something in the low 200s.

---

### Post by teatimest on 2009-02-03
So the default value 12 was 1 minute. I set it to 120 =10 minutes.
I still hear the subtle click sound, but not those clashing sound I uesd to hear. Additional benefit is that now it can come back from sleep.

Thanks a lot, kylecronan.

> **kylecronan said:**
> I assumed this value was in seconds, but you were right to wonder about it.  This is from the hdparm man page:

[INDENT]The encoding of the timeout value is somewhat peculiar.  A  value  of  zero means  "timeouts are disabled": the device will not automatically enter standby  mode.   Values from  1  to 240 specify multiples of 5 seconds, yielding timeouts from 5 seconds to 20 minutes. Values  from  241  to  251 specify from 1 to 11 units of 30 minutes, yielding timeouts from  30 minutes to 5.5 hours.  A value of 252 signifies a timeout of 21 minutes. A value of 253 sets a vendor-defined  timeout period between 8 and 12 hours, and the value 254 is reserved. 255 is interpreted  as  21  minutes  plus  15 seconds. Note that some older drives may have very  different interpretations of these values.[/INDENT]

Maybe try something in the low 200s.

---

### Post by ronewolf on 2009-02-05
I've had my Mini 12 for 3 days. Pretty good experience. I went down the path of loading UNR updates over the Dell install with the ~804um6 - per post #252. I have swap space setup (2GB) as confirmed by free -m and swapon -s. Appropriate entry in /etc/fstab.

I'm having two sorts of hibernate problems.

Trying the hibernate command (should work, right?) I get an error on the resulting text screen regarding the video card (I'll try to read out the details if needed). Waiting a while, the system came back to X. Shortly after tho, I had my first hang (I've had the system for 3 days now).

Second problem, I was able to get the hibernate button to show up in the gnome power menu by checking can_hibernate in the gnome-power-manager general conf. But after trying to hibernate one time, the button is no longer present (even tho the option is still checked). WTH?

Is it reasonable to expect hibernate to work on Ubuntu? On this netbook?

I've cross posted to the a new thread in Absolute Beginners. Is cross-posting OK on ubuntuformus?

---

### Post by ronewolf on 2009-02-05
> **kylecronan said:**
> 

A really nice install is Belmont + dell updates, then add netbook-remix.archive to your sources.list and get the UNR updates, then add ubuntu-mobile PPA and get those updates!  Download the ~804um6 deb and install manually to restore working 3D.  

Thanks for the summary install path. I was able to pretty much do this; of course, after reading reading reading thru this very helpful discussion.

So, I might go back to a fresh start (post #94). But since the system is working well, thought to maybe see if I can get fully functional from here. I posted my issue with hibernate in the previous message - just mention it here in case the hibernate issue is also screen driver related.

OK, running glxinfo returns the following:
```

name of display: 0.0
libGL error: open DRM failed (operation not permitted)
libGL error: reverting to (slow) indirect rendering
display: :0 screen: 0
direct rendering: No ....

```

Why do I care? Only for the ability to use a large external monitor. Actually, the high resolution selects fine for the external monitor (~1900x1200 - yay!). But there is still a minor problem that the Dell's screen view overlaps that of the external monitor instead of being an independent view. Know what I mean? Yes, I've used the Gnome(?) Screen Resolution Applet to move the two screens 'apart' - doesn't seem to have any effect. Any help/advice will be appreciated.

BTW, same result with the .20 xserver pkg.

---

### Post by kylecronan on 2009-02-05
My guess on the direct rendering is that you are missing a "Mode 0666" in "DRI" section of xorg.conf.  I'm not sure enabling that will fix the problem you described, though- try it and see.

---

### Post by ronewolf on 2009-02-06
> **kylecronan said:**
> My guess on the direct rendering is that you are missing a "Mode 0666" in "DRI" section of xorg.conf.  I'm not sure enabling that will fix the problem you described, though- try it and see.

Great catch! direct rendering: Yes :p

Unfortunately, tho, your intuition is correct and it doesn't seem to make a difference to anything that I'm doing or to the problem that with the use of multiple screens that I describe in my previous enabling direct rendering post

Thought to document exactly what I did in this final step:

1) used gedit to insert a DRI section into /etc/X11xorg.conf.

Section "DRI"
	Mode		0666
EndSection

2) restart X (cntl-alt-backspace)
3) run glxinfo with following result

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
etc

---

### Post by sdslayer on 2009-02-07
My mini 12 (ubuntu) is en route via fedex and I am trying to piece together the pros/cons of all the install options (posts 201, 219).  Please forgive my mistakes and help me understand what all this means.


Option 1 - Dell's 8.04 image "Belmont"
Pros
* I don't have to read these forums or mess with the OS :)
* DVD player & Fluendo codecs - What does this really buy me?
* working 3d & vid accel

Cons
* misc annoyances that can be removed (Y! toolbar, ume-launcher maximus)
* anecdotal evidence of instability/slowness (I didn't find quantifiable evidence)
* VESA drivers, no 1280x800 desktop (or is this only for the non-UNR hardy install?


Option 2 - Dell's 8.04 image "Belmont" + UNR + ? (post 252)
Pros
* more stable?

Cons
* no 3d & vi accel, unless psb um6 driver is installed


Option 3 - UNR 8.04 image  (post 94)
Pros
* can get 3D & vid accel working
* poulsbo drivers
* mplayer works if correct libva

Cons
* no Fluendo or DVD - how bad is this?


Option 4 - UNR 8.10 image  
Pros
* whatever misc improvements over 8.04

Cons
* 3d/vid accel unstable
* no Fluendo or DVD - how bad is this?

thanks in advance..

---

### Post by kylecronan on 2009-02-08
Option 4 does not really exist, I think you were reading about the Intrepid install hacked with Hardy's xorg.  However, there seems to be an lpia install of Intrepid that I don't think anyone here has tried.

3d and video acceleration can be made to work on all the UNR/Belmont flavors you mention (ymmv with regard to stability with the 3d components enabled).  And none of them will force you to use VESA since the 2d parts of the Poulsbo driver are open and work with any Hardy-based xorg.  Currently, none of these configurations comes by default with the um6 driver version that seems to work the best.  So it mostly just comes down to the libva packages for video playback, which Belmont gives you already working (but see brteag00's posts- it can be installed on regular UNR).  The fluendo codecs are some US-legal codecs for mpg, wmv, etc. that Belmont includes.

---

### Post by mkarnicki on 2009-02-08
Seems like this thread has calmed down. I admit I jumped from 8 to 26 page, since it's quite a long conversation, but I need a hint guys.

Do these:

[B]graphics (1280x800)
wi-fi[/B]

.. work? Or are there still problems? I need a possibly fast reply, as I'm taking my leave and I would like to order tomorrow mini 12 for my aunt to her shop (she needs a small and good looking laptop, specs are not important, but I'd prefer installing her ubuntu (hardy i386 ?), since I'm writing an application for her).

Huge thanks!

---

### Post by ronewolf on 2009-02-08
> **mkarnicki said:**
> Seems like this thread has calmed down. I admit I jumped from 8 to 26 page, since it's quite a long conversation, but I need a hint guys.

Do these:

[B]graphics (120x800)
wi-fi[/B]

.. work? Or are there still problems? I need a possibly fast reply, as I'm taking my leave and I would like to order tomorrow mini 12 for my aunt to her shop (she needs a small and good looking laptop, specs are not important, but I'd prefer installing her ubuntu (hardy i386 ?), since I'm writing an application for her).

Huge thanks!

i assume you mean [1280x800]... yes that works fine as does 802.11g. i'm using both right now. and both seemed to work fine right out of the box.

my experience overall has been quite positive.

---

### Post by mkarnicki on 2009-02-08
Sure ^ ^ a typo, meant 1280x800. I am happy to hear that! Thank you for your fast reply, Ron! :KS

---

### Post by erlguta on 2009-02-08
Wow!, 29 pages about  workarounds of how install one Ubuntu Intrepid in one Dell mini 12. I can not belive it.

Dell, i came here looking for information with the serious idea of buying this laptop, but watching this scenario I quickly changed my mind. With this kind of support and with such a pathetic way of doing things so badly, I think I'm going to forget it.

It is unacceptable, that in a laptop that is supposed to work with Ubuntu is so difficult to install it.
We are tired of see the same problems always (3D, wifi, etc).
Dell, why not stop doing your own versions of ubuntu and you do it completely compatible with an official ubuntu?.
I am not going to buy a dell computer until you can install an official Ubuntu without having to make a single damn workaround.

---

### Post by pistoncito on 2009-02-08
> **sdslayer said:**
> My mini 12 (ubuntu) is en route via fedex and I am trying to piece together the pros/cons of all the install options (posts 201, 219).  Please forgive my mistakes and help me understand what all this means.



Option 2 - Dell's 8.04 image "Belmont" + UNR + ? (post 252)
Pros
* more stable?

Cons
* no 3d & vi accel, unless psb um6 driver is installed




I bought the Mini 12 with ubuntu pre installed. I decided to make this mix, and it works better than only Blemont. At least I don't have problems with random X reboot now. Sometimes, the system freeze when tries to connect to Internet through wifi. Just freeze when start to try to connect. When i finnaly have connection, there's no more problem.

---

### Post by CrazyDesi on 2009-02-10
> **mkarnicki said:**
> Seems like this thread has calmed down. I admit I jumped from 8 to 26 page, since it's quite a long conversation, but I need a hint guys.

Do these:

[B]graphics (1280x800)
wi-fi[/B]

.. work? Or are there still problems? I need a possibly fast reply, as I'm taking my leave and I would like to order tomorrow mini 12 for my aunt to her shop (she needs a small and good looking laptop, specs are not important, but I'd prefer installing her ubuntu (hardy i386 ?), since I'm writing an application for her).

Huge thanks!

I can confirm they work on the UNR image.

---

### Post by ronewolf on 2009-02-10
> **brteag00 said:**
>  ... pull up a terminal, type 'gnome-session-properties', and de-select 'ume-launcher' and 'maximus' from the list of startup programs.  That will get you back to the standard GNOME desktop, which is plenty-usable with this much screen real-estate.

Not sure why my interfaces don't match this? Neither Maximus nor ume-launcher appear in my list of startup programs in the gnome-session-properties GUI. So instead, I tried using the Synaptic Package Manager to deinstall Maximus. However, that gets an error (and maybe wasn't a good idea?) as the ume-config-belmont seems to depend on Maximus. I went ahead and tried to uninstall them both. However, ume-config-belmont gets an uninstall error. Am I going down a rat hole here? Anyway, here is what shows up in dpkg.log when I try removing completely

```

2009-02-10 11:08:26 startup packages remove
2009-02-10 11:08:26 status half-installed ume-config-belmont 0.101.4
2009-02-10 11:08:26 remove ume-config-belmont 0.101.4 0.101.4
2009-02-10 11:08:26 status half-installed ume-config-belmont 0.101.4

```

---

### Post by floquet on 2009-02-10
Ubuntu has just released a Hardy update with a change in linux-ubuntu-modules to improve the support of Poulsbo chipset 

Bug #316780:SRU: Poulsbo DRM driver update from Intel; version 2.3.0.32L.0029

ANybody knows if this mean that Hady will now support Poulsbo from default installation without any other modifications?

Manel

---

### Post by pistoncito on 2009-02-10
> **ronewolf said:**
> Not sure why my interfaces don't match this? Neither Maximus nor ume-launcher appear in my list of startup programs in the gnome-session-properties GUI. So instead, I tried using the Synaptic Package Manager to deinstall Maximus. However, that gets an error (and maybe wasn't a good idea?) as the ume-config-belmont seems to depend on Maximus. I went ahead and tried to uninstall them both. However, ume-config-belmont gets an uninstall error. Am I going down a rat hole here? Anyway, here is what shows up in dpkg.log when I try removing completely

```

2009-02-10 11:08:26 startup packages remove
2009-02-10 11:08:26 status half-installed ume-config-belmont 0.101.4
2009-02-10 11:08:26 remove ume-config-belmont 0.101.4 0.101.4
2009-02-10 11:08:26 status half-installed ume-config-belmont 0.101.4

```

I had the same problem, and with that error network-manager doesn;t work. I had to re install both packages. To quit maximus from being load every session, I had to move the maximus-autostart.desktop from /etc/xdg/autostart/ to other directory.

---

### Post by zero4281 on 2009-02-11
> **floquet said:**
> Ubuntu has just released a Hardy update with a change in linux-ubuntu-modules to improve the support of Poulsbo chipset 

Bug #316780:SRU: Poulsbo DRM driver update from Intel; version 2.3.0.32L.0029

ANybody knows if this mean that Hady will now support Poulsbo from default installation without any other modifications?

Manel

Here's a link: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/316780](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/316780)

Looks like it's in linux-ubuntu-modules-2.6.24 - 2.6.24-23.37 which sits in hardy-proposed at the moment.

---

### Post by CrazyDesi on 2009-02-11
Can someone run this command to see what power save mode Dell is using vs the UNR remix on default:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

---

### Post by floquet on 2009-02-11
> **zero4281 said:**
> Here's a link: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/316780](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/316780)

Looks like it's in linux-ubuntu-modules-2.6.24 - 2.6.24-23.37 which sits in hardy-proposed at the moment.

The bug is fix released and is available from Hardy repositories. It will update from package linux-ubuntu-modules-2.6.24-23-generic Version 2.6.24-23-37. Description of the update is 
Versió 2.6.24-23.37: 
  * LPIA: Poulsbo driver 2.3.0.32L.0029 update
    - LP: #316780

In the bug 316780 description is:
"Intel has released an updated version of its Poulsbo (SCH) DRM driver (2.3.0.32L.0029); this contains numerous stability and performance related changes and is needed for lpia kernels and Ubuntu MID.". 
Inside there there are also some interesting comments:
"Tested successfully from hardy-proposed. I tested 2D and 3D and the updated libdrm and xf86-video-psb from the ubuntu-mobile hardy ppa."

---

### Post by marduk667 on 2009-02-11
CrazyDesi: ondemand on my UNR

i found in the diff of the kernel-patch:

add support for Linux kernel 2.6.27 & 2.6.21

sounds good :) did intel finally wake up?

---

### Post by sdslayer on 2009-02-11
Ok, I installed the dell updates, then UNR.  I didn't restart in between the updates (dont know if necessary).  The ubuntu-mobile PPA gave me an error about a public key not being avail, so I never installed that one.

But, after the updates, my HD clicks every 20-30 secs no matter what.  In a few more hours, I will go insane. Or, my mini may be flying off my balcony.

I set SPINDOWN_TIME=200  (assuming a reboot takes this into effect)

but, do I also have to do everything under hardy here:

[https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement)

---

### Post by CrazyDesi on 2009-02-11
> **marduk667 said:**
> CrazyDesi: ondemand on my UNR

i found in the diff of the kernel-patch:

add support for Linux kernel 2.6.27 & 2.6.21

sounds good :) did intel finally wake up?

Thank you :).  I guess thats not it.  I noticed some weird cpu usages in my belmont image that I downloaded, but that wasn't it I guess.

Anyway does this mean we can install a vanilla 8.04?

---

### Post by CrazyDesi on 2009-02-11
Is any one else having problems with their CPU acting up after closing Open Office?

---

### Post by zero4281 on 2009-02-12
> **zero4281 said:**
> Here's a link: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/316780](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/316780)

Looks like it's in linux-ubuntu-modules-2.6.24 - 2.6.24-23.37 which sits in hardy-proposed at the moment.

It looks like it's in the normal hardy release.  How do I help get this into the Netbook Remix?

---

### Post by kylecronan on 2009-02-12
> **zero4281 said:**
> It looks like it's in the normal hardy release.  How do I help get this into the Netbook Remix?

Well, hang on, have you tried installing it manually in UNR?  There could be other components that have to be upgraded at the same time- we don't know if it will work yet.  I would try it myself, but...

I'm trying Intrepid one more time (I just love the fact that aptitude can take some big set of packages like xorg from a different distribution, and just figure out everything it needs to do to hack it into place- yum would never be able to do this).  Anyway, I started with the lpia alternate installer this time (very broken- but possible!).

I can confirm that the source for this version of the DRM modules (2.3.0.32L.0029) compiles fine under Intrepid with 2.6.27.  I am now trying to get the latest 0.20 version of video-psb to work with xorg 1.5 (it looks like 0.20 has some changes that bring it somewhat closer to compatibility).  I tried lpia Intrepid + xorg 1.4 from UNR + drm 2.3.0 + psb 0.20 and it did not work (xorg starts up but the visual display is distorted).

NB: If you are happy with your install, please ignore these crazy machinations I'm describing.

@sdslayer, the error regarding unavailable public keys can be safely ignored (well, unless you're paranoid, I guess).

---

### Post by kylecronan on 2009-02-12
Good news: the attached patch will allow xserver-xorg-video-psb to compile for xorg 1.5.2.  This makes 2D accel possible in Intrepid without having to hack the xorg version. (and if you use lpia packages for your initial install, the speed is just as good as UNR)

As for the binary blobs, the firmware file and Xpsb.so load okay, so you do get xv.  But the psb_dri.so library fails with "AIGLX error: psb exports no extensions (/usr/lib/dri/psb_dri.so: undefined symbol: __driDriverExtensions)".  I suspect this means psb_dri.so is incompatible with the newer xorg, but it could also be the kernel module or xorg driver, both of which have a different version than the configuration in which 3D is known to work.

This setup is currently a huge pain to get working, but if anyone wants to try it I'll help.

---

### Post by kylecronan on 2009-02-12
ok, regarding the stability fixes:  What happens now is that the keyboard and mouse lockups still occur, but X recovers instead of crashing.  This takes 15 seconds or so.  If it doesn't happen very often, not a big deal.  But I wouldn't exactly call it "fixed".  As I recall, 0.20.0 on UNR crashed in the usual way, so the improvement must be a result of these new DRM modules.

It may be that the actual source of the problem is in evdev or somewhere else in the input systems.  I suspect this because a) this driver in particular forces you to use evdev, which is otherwise rarely used, and b) the lockups always seem to occur when using the touchpad.  Has anyone else noticed this?

I sent the Dell Mini project a request for a new psb_dri.so.  I believe that (along with a more proper version of my patch for video-psb) is now the last thing that is needed before all these drivers are up to date with released Ubuntu.  At least, in theory- in practice, the code will of course need to be packaged properly as well.

[https://answers.launchpad.net/dell-mini/+question/60733](https://answers.launchpad.net/dell-mini/+question/60733)

one last update: I had a second lockup, except this time X did not recover.  It didn't stop running either- I had to do a hard reboot.  Major bummer.

---

### Post by marduk667 on 2009-02-12
> Has anyone else noticed this?

Yes, but i only use the touchpad, i do not use a normal mouse with the Mini.

---

### Post by marduk667 on 2009-02-12
fyi

> 

netbook-remix.archive.canonical.com archive was updated in January
with security updates. We plan to update it again sometime in March to
coincide with the next major UNR update. An updated l-u-m will be part of that
update and has an even newer version of the Pouslbo driver than
referenced here, version 2.3.0.32L.0201.

We hope to push many of the UNR updates first to a proposed repo so folks can try it out before it is released. Don't know the exact date yet, but you can add the following to your sources.list to be sure to get the proposed updates when they become available:
deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix-proposed main universe multiverse restricted


---

### Post by zero4281 on 2009-02-12
> deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix-proposed main universe multiverse restricted

Awesome.  Where did you find this?

---

### Post by marduk667 on 2009-02-13
In the bug-report ([https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/316780](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/316780))

---

### Post by teatimest on 2009-02-13
> **marduk667 said:**
> In the bug-report ([https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/316780](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/316780))


Since it's in regular Hardy repo, does it mean I can install regular Hardy now?

If not, I will stick with UNR without 3D for now.

---

### Post by kylecronan on 2009-02-13
It certainly will not work out of the box yet.  I'd say you are better off with UNR.  Hardy still has a version of xserver-xorg-video-psb that is a year and a half old.

But you should try downloading the new linux-ubuntu-modules .deb and installing it manually with dpkg or the GUI package manager or whatever (will need a reboot after).  See if you notice any difference:  I suspect you'll see the same thing I saw with Intrepid, ie, no real improvement in stability with Xpsb.so enabled.

---

### Post by CrazyDesi on 2009-02-13
Any one else getting an upgrade to Intrepid?  I got the Dell Mini 12 drivers, plus UNR, plus mobile.

---

### Post by CrazyDesi on 2009-02-14
Anyone?

---

### Post by zero4281 on 2009-02-14
> **CrazyDesi said:**
> Any one else getting an upgrade to Intrepid?  I got the Dell Mini 12 drivers, plus UNR, plus mobile.

It's telling you to upgrade to Intrepid?  I wouldn't upgrade to Intrepid at this point.  What does /etc/apt/sources.list look like?

---

### Post by CrazyDesi on 2009-02-15
> **zero4281 said:**
> It's telling you to upgrade to Intrepid?  I wouldn't upgrade to Intrepid at this point.  What does /etc/apt/sources.list look like?

```

deb http://dell-mini.archive.canonical.com/ubuntu/ intrepid main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ intrepid main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ intrepid-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ intrepid-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ intrepid-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ intrepid-security main universe multiverse restricted

# deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
# deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

# deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
# deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ intrepid main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ intrepid main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ intrepid-updates main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ intrepid-updates main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ intrepid-security main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ intrepid-security main universe multiverse restricted

# deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
# deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

# deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted
# deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted

# deb http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main
# deb-src http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main

# deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
# deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix-proposed main universe multiverse restricted 

```

---

### Post by zero4281 on 2009-02-15
It looks like you have a bunch of repositories for Intrepid.

Here's my sources.list, granted i dont have dell-mini in my install.

```
deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted

deb http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix-proposed main universe multiverse restricted
```

---

### Post by zero4281 on 2009-02-15
You could try this and see what happens.  No, I didn't test it.  Buyer Beware!

```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ intrepid main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ intrepid-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ intrepid-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted

# deb http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main
# deb-src http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main

# deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
# deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix-proposed main universe multiverse restricted
```

---

### Post by CrazyDesi on 2009-02-18
Anyone still working on the Mini 12?

---

### Post by brteag00 on 2009-02-18
My feeling is that we've pushed things about as far as they'll go without some additional vendor (Ubuntu, Dell, Intel) engagement.

---

### Post by marduk667 on 2009-02-18
Yes thats my opinion too, i think we have to wait what intel will do with the drivers (and i hope they continue devlop it now) and if the Ubuntu Team gets Support built in Jaunty (what would be really great)

---

### Post by jabronioh on 2009-02-18
That is what I am waiting and hoping for. I need Jaunty to work out of the box!

Otherwise, I am still pretty happy with the UNR install so it isn't like I am lacking...

---

### Post by tombott on 2009-02-18
Not sure if this will help you:

[Dell 8.10 System Restore DVD]("http://linux.dell.com/wiki/index.php/Ubuntu_8.10#Dell_OS_Factory_Recovery_8.10_DVD_ISO")

---

### Post by CrazyDesi on 2009-02-18
> **tombott said:**
> Not sure if this will help you:

[Dell 8.10 System Restore DVD]("http://linux.dell.com/wiki/index.php/Ubuntu_8.10#Dell_OS_Factory_Recovery_8.10_DVD_ISO")

Hmm...Has anyone tried it?

---

### Post by kylecronan on 2009-02-18
Hmm, I guess theoretically that could work.  It was just put up on that site yesterday.

edit: no, it doesn't have the drivers

---

### Post by naidu01 on 2009-02-19
Actually only Dell's version of Ubuntu 8.04.1 has the dell mini 12 video drivers (v8.10 does not).  Check this out:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04")

on the installation screen it has:
1. Install with Intel Video Driver
2. Install with AMD Video Driver
3. Install with Nvidia Video Driver

But some folks don't like the Dell version of ubuntu, check it out:

[http://bits.quintanasegui.com/arxius/2008/12/30/dell-sells-ubuntu-boxes-that-cannot-run-ubuntu/]("http://bits.quintanasegui.com/arxius/2008/12/30/dell-sells-ubuntu-boxes-that-cannot-run-ubuntu/")

Can someone please test and reply with the results? My mini 12 does not have an external dvd drive so before I invest in one I need to know if this works. [-o<

---

### Post by kylecronan on 2009-02-19
The version of Hardy on that Dell website was put up months ago, so it's not going to work with a Mini 12.  You should check roughly pages 9-14 of this thread to get something that works.

Also, despite what is said in that article, it is entirely possible to run 8.10 at the correct screen resolution, and if you use an lpia version of Intrepid it is decent.  However, the X stability issues that remain in the psb driver are worse with this setup and with everything but UNR or Belmont running um6 psb drivers.

(although I totally agree with the point that Canonical needs to protect its brand from what Dell will do to it with its non-redistributable customized distros)

---

### Post by Tiler on 2009-02-19
> **CrazyDesi said:**
> Anyone still working on the Mini 12?

Yep.  CrazyDesi,  You and I howdied at the dellmini forum, I think.  Mine was shipped with the Dell ubuntu and I tried installing the UNR img with ImageWriter.  It also seems to be looking for all the lpia packages.

Everyone seems to be having better luck with UNR when they convert from regular Hardy.  I've tried several different approaches to installing vanilla Hardy but the Live CD can't see the Hard Drive (not SSD).  This issue is well documented and I've basically given up this approach.  

Now, I've got UNR installed but have access to a limited list of items in Add/Remove.  This particular mini-12 is a gift and I'm hesitant to give it because I'm not sure if the end-user is going to have access to the full list of third-party apps.  Wine, for example shows up in the list but disallows the install. 

I've tried to sort through sources.list in other installs to pick and choose which ones to add but it still seems to end up wrong.

I opened a ticket with the UNR team to get the Software Sources changed in the UNR img but it hasn't been open long.

---

### Post by zero4281 on 2009-02-20
> **Tiler said:**
> Wine, for example shows up in the list but disallows the install.

I'm able to install and run wine in the hardy install of UNR.  My system is up to date.  Here's my sources.list:

```
deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted

deb http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix-proposed main universe multiverse restricted
```

---

### Post by Belveder on 2009-02-20
Hi, 

I don't know if anybody of you already had access to IEGD 9.1.1. I did not have and it was not available for download from Intel as fas as I know. However, this is what I found just minutes ago

[http://forum.eeeuser.com/viewtopic.php?pid=511213]("http://forum.eeeuser.com/viewtopic.php?pid=511213")

Anyone interested in trying this? Unfortunately I do not have our Panasonic Toughbook CF-U1 at hand right now, but I will have a look at the Linux and the XP drivers as well.

Regards
Clemens

---

### Post by pistoncito on 2009-02-20
I used to have crashes of the X system when I am compiling software. Someone else with this problem? I had the original Ubuntu and UNR updates. 

By the way, which is the best configuration for the HDD click?

---

### Post by kylecronan on 2009-02-24
X crashes are normal at this point, until Intel fixes the driver for real.  The clicking can be fixed in the way described in earlier posts- doesn't matter which configuration you're using.

---

### Post by Chris B on 2009-02-27
I've had my Mini 12 for about a week now.  The first set of brteag00's instructions (in post #94) worked perfectly for getting 2D set up (thanks!)

I decided to start trying to get 3D working but without success, and I'm not sure where I'm going wrong.  I don't pretend to know much about how everything works, but I'm reasonably good at following directions.

So far 
(1) The firmware is in the right place (checked using dmesg)
(2) My Xorg.0.log file shows "Loading /usr/lib/xorg/modules//Xpsb.so" and "Xpsb extension for 3D engine acceleration enabled."

but glxinfo says (among many other messages):

ERROR!  sizeof(PsbDRIRec) does not match passed size from device driver
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
direct rendering: No

As I said, I don't really know what to look for or how to fix this.  Any hints?  I don't think I missed a step anywhere...

---

### Post by microman777 on 2009-02-27
Man, I just ordered the Dell Mini 12 with Ubuntu pre-installed, and now after reading this thread, I'm worried about using it. 

I can't comprehend how Dell would release a new laptop with an OS all full of glitches.

---

### Post by Chris B on 2009-02-27
Okay, I'm a glutton for punishment.  Just for fun I thought I'd see if I could get a dual-boot Windows setup going.  Everything went fine until I tried to configure GRUB: the Live CD won't recognize the Mini 12's hard drive!  I tried several different versions I have lying around, including a Mythbuntu 8.10 CD I used to set up my DIY DVR.  None of them can see the internal hard drive.  

Now I can't even boot back into Ubuntu :(.  Any advice on how to configure GRUB?

---

### Post by kylecronan on 2009-02-28
Chris, I can't say for sure.  Please provide more information on _exactly_ what you're trying to do.  Which LiveCD you were installing from when it failed to set up grub, for example.

If you have everything installed, but grub is messed up, then here's what you do: boot an installer cd/usb, mount your linux partition, chroot into that mountpoint, run grub, issue the setup command.  Obviously, that's the abbreviated version. ;)

---

### Post by Chris B on 2009-02-28
Kyle, thanks a lot for the reply.  Let me explain what I've done:

(1) Started with a blank HDD and tried several LiveCD's to install Ubuntu (8.04.1, 8.04.2, 8.10).  None of them recognized my internal HDD.
(2) Installed successfully from UNR CD, made recommended modifications; worked great.
(3) Used a Gparted Live CD to repartition HDD, making a 10GB partition for Windows (sits before UNR-installed partition).  Saved a copy of my menu.lst file on a USB stick. 
(4) Installed WinXP on the new partition, losing ability to boot into Ubuntu.
(5) Booted to a live CD (used 8.04.2) ran GRUB, when I try the command "root (hd*,*)" I just get "Error 21: Selected disk does not exist."

I'm guessing my problem is that I don't know how to get my linux filesystem mounted.  Sorry for such a basic question in a rather specific thread.

Edit: I figured out how to mount the HDD when booting from the Gparted Live CD.  I ran GRUB from that and then messed things up.  I think my linux partition switched from hd0,0 to hd0,1 after the windows partition was formatted.  So I changed the menu.lst settings for the ubuntu filesystem to hd0,1; it was originally hd0,0.  Then in GRUB I did "root (hd0,1)" followed by "setup (hd0)."  Now it boots to the ubuntu splashscreen but then just hangs.  I'm going to experiment with a few different iterations of the menu.lst file...

Edit2: Now it's booting into Windows XP again, but no GRUB menu appearing.  Here's what the relevant lines from my menu.lst file looks like (I'm assuming this is where the bootloader looks?):

Edit3: Finally have dual-boot working perfectly.  I had to change a line in my fstab because after installing on the previously-unused partition my linux partition became /dev/sda2 (had been sda1).  Also changed the root location in my menu.lst to /dev/sda2.

---

### Post by teatimest on 2009-03-01
My UNR machine has a problem with boot up.
It boots up.... but sometime it boots up flawlessly.
Most of the time, it stalled at the ubuntu logo and takes almost one minutes before I see any orange in the progress bar.

I enabled verbose bootup. Now I see it stops after
"mounting root file system" for a minutes.
Then the other line comes and HDD starks to kick in.

Sometime this does not happen at all.
In this case, the orange in the progress bar appear quickly and
I would not get stalled at all.

Does anybody here have similar symptom?
Do you have any suggestion for this problem?

Thank!

---

### Post by floquet on 2009-03-01
Hi Teatimest

I have exactly the same problem you describe. I've been looking around for solutions for weeks now, but nothing seems to work.:confused:

---

### Post by teatimest on 2009-03-02
Hi Floquet,

Isn't it annoying? You don't know when you have to wait. And it is kind of embarrassing to have a computer starting up that slow when I do my presentation.... I know Ubuntu can do much better than this!

One thing I remember is that I turned off the HDD's acoustic mode using feature tool from Hitachi. It did not help the speed much, so I put the acoustic mode back. Did you do this, Floquet? If so, this might be plausible cause. If not, I have no idea...

---

### Post by microman777 on 2009-03-02
Well I just tried Ubuntu 8.10 on my home pc to see how much I'd like it, before my Mini 12 arrives with Ubuntu. 

Compared to Windows 7, Ubuntu's look looks like Windows 95 in comparison. The only thing better on Ubuntu than Windows 7 IMO is the nice graphic effects when you open a new window and so forth. But as for visual eye candy over all, IMO Windows 7 kills Ubuntu!!!!

I'll try out Ubuntu on my Dell Mini 12 for a bit when it arrives, but I'll probably upgrade to Windows 7 later unless there a better alternative!!!!!!!!!!!

---

### Post by kylecronan on 2009-03-03
Chris, oops, sorry that I was away for a while, but I am glad to see that you got your dual-boot setup working great!  The way you had to do it is tricky.  I recommend to anyone the order where you start with windows, resize and then install linux- whenever possible that is.

Teatimest and floquet, I've never seen that, but I'm wondering- do you get consistently okay bootups if you add all_generic_ide to your kernel arguments at boot?  It seems your issue has something to do with the hard disk, and Marduk and I had to do this before with a non-lpia kernel, so it's worth a shot.

---

### Post by teatimest on 2009-03-04
Thanks kylecronan,

I tried your solution once... and unfortunately, it did not work. Ummmm....

Did I get bad hard drive? Is it dying?

My fstab reads like this:

/dev/sda1           /               ext3 defaults       0 0
proc                    /proc                   proc    defaults        0 0

And my menu.lst reads like this:

root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-lpia ro boot=disk splash
initrd          /boot/initrd.img-2.6.24-19-lpia

title           Ubuntu 8.04.1, kernel 2.6.24-19-lpia (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-lpia ro boot=disk single
initrd          /boot/initrd.img-2.6.24-19-lpia

title           Ubuntu 8.04.1, kernel 2.6.24-19-lpia (fix)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-lpia ro boot=disk all_generic_ide
initrd          /boot/initrd.img-2.6.24-19-lpia

Do you see anything wrong with my settings?

---

### Post by kylecronan on 2009-03-04
Somehow I don't think it is a hardware problem, because we've got two of you here with the same symptoms- it would have to be a widespread failure in that case.  But then, I can't think of anything that could explain it either!  Maybe you should do an fsck?

---

### Post by floquet on 2009-03-05
Hi

Same results than Teatimest. Adding the "all_generic_ide" option to the menu.lst did not changed the boot up time. The interesting thing is that this lock up only happens 50% of the times. Some times either booting or rebooting the system does not freeze at "waiting for root filesystem":o:confused:

---

### Post by teatimest on 2009-03-05
The integrity of the filesystem was determined by fsck. No error was identified...

Yes, but mine is like 80% congestion and 20% fast lane.

---

### Post by anoopalias01 on 2009-03-06
Hey..i found the cause for the delay at boot

we have to edit the grub kernel line from
kernel /boot/vmlinuz-2.6.24-19-lpia ro boot=disk single
to
kernel /boot/vmlinuz-2.6.24-19-lpia ro root=/dev/sda1

and i got quite big fonts using XFCE as the desktop 

But i have a very weired problem now! - ubuntu says the laptop is on battery power even when i have ac power on and connected..sometimes it recognizes the ac power ..sometimes in the middle of nowhere it just goes into battery mode (ac is still on )

Has anyone experianced similar problem .It worked fine on XP..so i wonder if the OS can really stop the ac flow! and start the battery to discharge

Any help is appreciated

Thanks

---

### Post by teatimest on 2009-03-06
Hi anoopalias01,

Adding "root=/dev/sda1" to the grub menu.lst solved the problem. Thanks sooooo much!

You can use Xfce as a desktop manager? Does it perform faster than Gnome? If so, I would like to try that, too.

teatimest

---

### Post by pistoncito on 2009-03-06
I installed xfce 4.6 (i had to compile everything in Terminal, without X system because X hangs up randomly when i was compiling). I have the same issue with the big fonts. I can't tell if run a lot faster than gnome, but works fine. I will try to use the composite part of xfce later.

---

### Post by anoopalias01 on 2009-03-08
Hey there is no need to compile

just do apt-cache search xfce

and install the xfce packages using sudo apt-get install

I think the main package you will need is xfce4..just go on and install all you think will be needed.

Once done at the GDM (at login ) options will have xfce as  aalternate desktop. try out once and if everything is fine make xfce permanent choice

XFCE , Epiphany (uncheck the option "let site choose its own font ) + deluge (for torrent) +pidgin will make your dell mini the true netbook


Anyone got the mic working...i got it working once in skype..but messed it up and now its not working....but theres some problem with the alsa for alc269 i guess. I tried model=basic as suggested by someone in a forum ..but no use :(

other than that my dell mini works perfect in 8.04 lpea now :).hats off to ubuntu

---

### Post by teatimest on 2009-03-09
> **anoopalias01 said:**
> Hey there is no need to compile

just do apt-cache search xfce

and install the xfce packages using sudo apt-get install

I think the main package you will need is xfce4..just go on and install all you think will be needed.

Once done at the GDM (at login ) options will have xfce as  aalternate desktop. try out once and if everything is fine make xfce permanent choice

XFCE , Epiphany (uncheck the option "let site choose its own font ) + deluge (for torrent) +pidgin will make your dell mini the true netbook


Anyone got the mic working...i got it working once in skype..but messed it up and now its not working....but theres some problem with the alsa for alc269 i guess. I tried model=basic as suggested by someone in a forum ..but no use :(

other than that my dell mini works perfect in 8.04 lpea now :).hats off to ubuntu

I am trying Xfce now. The clutter interface came back and did not know how I can disable. So I just uninsalled clutter. 

It seems that Xfce runs much more efficient in terms of memory usage. It feels a little snappier than Gnome. But the panel is annoying. When I maximize any window, the bottom of it goes under the panel. Is there any way I can change the behavior of the panel to task bar which is found in Gnome?

I also uploaded [timed bootup vide]("http://www.youtube.com/watch?v=cwxwthe72nU")o on youtube. Thanks annopalisus01!

---

### Post by pistoncito on 2009-03-11
> **anoopalias01 said:**
> Hey there is no need to compile

just do apt-cache search xfce

and install the xfce packages using sudo apt-get install

I think the main package you will need is xfce4..just go on and install all you think will be needed.

Once done at the GDM (at login ) options will have xfce as  aalternate desktop. try out once and if everything is fine make xfce permanent choice

XFCE , Epiphany (uncheck the option "let site choose its own font ) + deluge (for torrent) +pidgin will make your dell mini the true netbook


Anyone got the mic working...i got it working once in skype..but messed it up and now its not working....but theres some problem with the alsa for alc269 i guess. I tried model=basic as suggested by someone in a forum ..but no use :(

other than that my dell mini works perfect in 8.04 lpea now :).hats off to ubuntu

I had to compile because i wished to try the new xfce version (4.6). I had 4.4 at the repositories.

---

### Post by JinnJin on 2009-03-14
Hi All, maybe someone can help me that the problem drives me crazy.

The internel HDD can't be recognized when I was installing ubuntu 8.04 and 8.10. This issue has been mentioned by many people who also mentioned UNR can recognize the HDD. So I tried to install UNR via usb memory stick but installing process stoped after found Generic multi card. But Chris said that he was able to install successfully via UNR CD.

> **Chris B said:**
> (2) Installed successfully from UNR CD, made recommended modifications; worked great.

Is that UNR can only be installed via CD?

---

### Post by anoopalias01 on 2009-03-15
for some one else who happen to be here in the hope of running GNU/Linux on the Dell Inspirion Mini 12 ( Inspirion 1210 ). well i must say it works..it works better than the Windows XP i had preinstalled on my Dell Mini 12( the most annoying thing in XP was that there is a display driver bug which caused the cursor not to detect the background color in a Putty window .so thecursor goes invisible in putty )

Heres a summary of what works for me right now:

Display - works - i havent activated 3D mostly because i dont want it!.If you just want to watch movies and play 2D games . display works 100 percent

Sound - works out of the box

Front Mic - works ( jut have to play around with the volume control and enable every controls)

Mic - works ( go on tampering the input source in volume control)

Webcam - works out of the box

USB and card reader - works

Bluetooth - not tested


Perfomance - decent ( make use of some light weight desktop like xfce) - I can say the ATOM perfomance is below the celeron one of same GHz probably because of the low processor cache ). And it has a much slower hdd . But if you want more portability and less heat generating laptop with a decent screen size- Mini 12 is the answer

As for installation Ubuntu Netbook remix 8.04 install works fine from a USB stick. It wipes out anything existing on your hard drive though. But who needs the crappy windows XP!

That reminds me : the dell mini 12 is not available with Ubuntu preinstalled for me in India (at least for now ). So i had to pay around 80 USD for the XP license.Which i will never use again!. So if ever Bill Gates come over this thread - consider that 80 USD as alms given by a sympathetic user on behalf of the entire GNU/Linux community and stop layoffs of innocent workers from MS

---

### Post by JinnJin on 2009-03-16
Just installed by the steps on page 6, soooooo Coool

---

### Post by JinnJin on 2009-03-16
Just installed UNR Jaunty Daily Image which seems released yesterday.

everything seems fine.

The main menu need putting on top bar to instead of the desktop panel which is wired, nothing can be clicked and top part is covered by top bar.

Web page jumps when scrolling in FF, maybe the display driver is not correct.

---

### Post by pacyang on 2009-03-19
> **JinnJin said:**
> Just installed UNR Jaunty Daily Image which seems released yesterday.

everything seems fine.

The main menu need putting on top bar to instead of the desktop panel which is wired, nothing can be clicked and top part is covered by top bar.

Web page jumps when scrolling in FF, maybe the display driver is not correct.
Hi.
Thanks for share.

Really attractive. Can you give more details please ?
All seems work ? Wifi, Bluetooth, Sound,.. ?

Is the default X Server work well ? or do you have modified it ?
Because on ubuntu 8.10, the default xorg doesn't work and the "vesa" driver work very bad.

It will be awesome if this ubuntu version work well with the default installation, without do anything.


excuse my poor english.
pacyang from France.

---

### Post by marduk667 on 2009-03-20
Yeah i am also very interested in the jaunty thing. Have you checked for the poulsbo drivers? are they included?

---

### Post by benguin on 2009-03-21
I have been watching this thread for a while, as my initial enthusiasm about a Linux pre-installed Dell laptop quickly faded away. I was deeply disappointed by the quality of the Hardy install, in particular with the display driver. I guess its been stated many times that the Poulsbo drivers are not really anywhere near as good as the other true open-source drivers Intel produces, and it shows. Ever since I bought it in December, it has been exhibiting random X restarts, sometimes hard freezes, and sometime, on a smaller scale, firefox crashes. Has anyone here seen these happening to their 1210? Even scrolling the page faster is causing firefox to crash, and sometimes it takes down entire X with it. As you can imagine, this is not really usable by any definition. I don't know if I can return it, but if I could, I would. 

I sincerely pray Ubuntu/Dell/Intel comes up with a solution in Jaunty, particularly with the display drivers. If anyone has any experience with  the Jaunty UNR and the above-mentioned annoyances, please feel free to share. I'm desperate for some help/positive news. 

Thanks and I hope you forgive the rant.

-J

---

### Post by microman777 on 2009-03-23
I'm getting my Mini 12 Blue Ice finally delivered on Tuesday after a month and a half of waiting!!!!

---

### Post by kylecronan on 2009-03-23
Some work has been done on the kernel side at least:

[http://www.phoronix.com/scan.php?page=news_item&px=NzE1Mw](http://www.phoronix.com/scan.php?page=news_item&px=NzE1Mw)

"We know this sucks, we're working on it but thats all I can really say."  Gee, thanks a lot, Intel.

If I have some time I might try out those rejected patches to see if the xorg crashes are still there.

---

### Post by 2oh1 on 2009-03-23
I bought a refurbished mini 12 that came with XP.  I desperately want to get ubuntu working on it, even if it's just Dell's funky version.

How do I do this?!?

The instructions I've seen in this thread are over my head since I've never used Ubuntu before, aside from checking it out with a Live CD on my Mac.

NOTE!  I need the ability to chose a different screen resolution.  I'll be happiest with 800x600.  Everything on 1200x800 is just too small for my vision.  800 X 600 would be best, but 1024 X 768 might work.  I realize changing screen resolutions is no big deal, but I also have read that there are video issues with Ubuntu and Paulsbo?  I'm not entirely clear as to what that means, in practice, for a netbook.  Really, I just want to be able to do basic stuff with my Mini 12.  Surf the web, take notes, email.  That sort of thing.

Like I said, my experience with Ubuntu is limited, and I have no experience with XP.  I point this out because, even though I'm technically savvy, I'm clueless here and will need to be talked through it step by step :)

---

### Post by fitzkarraldo on 2009-03-23
> **JinnJin said:**
> Just installed UNR Jaunty Daily Image which seems released yesterday.

everything seems fine.




JinnJin,
more details please? :-)

---

### Post by kylecronan on 2009-03-23
@2oh1, post #94 is still the best way to go.  The files referenced in that post are available as attachments, which you can find in the preceding pages.  Try to follow brteag's instructions and post here if you run into any problems.  The one caveat is that the UNR installer will wipe your whole disk.  If you want to keep Windows and dual boot, the process is more complicated.

@fitzkarraldo, I'm fairly certain that the difference with Jaunty is that they have fixed the install process so that you don't have to do anything special to get a working system.  If you install Jaunty you will not have the correct screen resolution, and accelerated video will not be possible (well, it is possible to get the Poulsbo drivers working with more recent kernels and newer versions of xorg, but trust me, it's not worth the trouble).

---

### Post by 2oh1 on 2009-03-23
> post #94 is still the best way to go. The files referenced in that post are available as attachments, which you can find in the preceding pages. Try to follow brteag's instructions and post here if you run into any problems. The one caveat is that the UNR installer will wipe your whole disk. If you want to keep Windows and dual boot, the process is more complicated.

Three questions:

#1 - I'm ok with wiping out my HD and starting from scratch so long as there is a way for me to revert back to XP if I need to.  My mini 12 came with restoration CDs.  Will I be able to turn those CDs into usable disk images on my Mac so I can then use them on my mini 12 via usb flash cards?  I'm assuming XP would have to be bootable.  I really don't want to buy a USB CD/DVD drive if I don't have to.

#2 - What is Compiz?  Post #94 doesn't mention it, but following posts say that Compiz doesn't work.

#3 - Is there anything else that doesn't work, after doing an ubuntu install by following the post #94?  I'd hate to do all of that work only to find out that I can't change the screen resolution, or the touchpad doesn't work...  something like that.

Thanks for your help & info!

---

### Post by kylecronan on 2009-03-24
#1 - I've had some luck converting CD images to USB flash, but it can be rather complicated.  But you could always buy a USB cdrom at your local store and take it back later.  Just say it didn't work. ;)

#2 - Compiz is the window manager that gives you all the fancy visual effects that so many people love to show off in cafes.  Not a big deal.

#3 - You will be able to change the screen resolution to 800x600 at least.  Although this is the wrong aspect ratio (just by a little bit).  The only thing I can think of that you will be missing is the hardware-accelerated video playback that comes installed with Dell's version of Ubuntu called Belmont.  That means that you might get jerky playback with really large or highly compressed video files.

---

### Post by 2oh1 on 2009-03-24
Am I better off trying to find Dell's "Belmont" version?

---

### Post by kylecronan on 2009-03-24
In my opinion, Belmont is the best option (once you remove the cruft they put in there like the yahoo toolbar and dell launcher).  However, it contains some nonfree codec packages, so it's not publicly available.

---

### Post by 2oh1 on 2009-03-24
Let's say I have a belmont .img file.  Is there a way for me to turn it into a bootable flash drive?  Can I somehow do this on my Mac?  In other words, can I use my Mac to turn the img file into a bootable usb flash drive that I could then use on my Mini 12?

If that won't work, I guess I'd have to buy an external optical drive.  How would I turn the img file into a bootable DVD (preferably, using my Mac, but if not, then using XP on the mini 12)?

---

### Post by kylecronan on 2009-03-24
There are some instructions on converting CD images to USB here:

[https://help.ubuntu.com/community/Installation/FromUSBStick#Manual%20Approach](https://help.ubuntu.com/community/Installation/FromUSBStick#Manual%20Approach)

If you have an optical drive you can just burn the image onto a DVD in the usual way.  If the file really does have a .img extension it may need to be renamed to .iso.

Although, the fact that you say it is .img makes me think you may have the filesystem image contained within the CD, not the installer CD itself.  If that's the case, you would have to do a completely manual install, which is way too many steps for me to go into here.

---

### Post by battlebotscott on 2009-03-25
I am pretty new to ubuntu and i just installed unr and i am trying to get these psb drivers to work.  I followed post 94 and when i went into software sources i got the "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 99D6B21CC6598A30" error that another user previously noted.  It is not clear for me (and of course my limited experience) how to bypass this.  A few pages later user kdubya posted the drivers and i have downloaded them but i do not know what to do with them.  Can someone tell me in some detail how to install them and what should i do after i install them?  Thanks!

---

### Post by kylecronan on 2009-03-25
It's just a warning.  You can ignore that message.

---

### Post by teatimest on 2009-03-26
Hi kylecronan,

Are we supposed to get major UNR update that includs new graphic driver during March? It's almost April....

---

### Post by kylecronan on 2009-03-26
teatimest, I sure hope so.  Now might be a good time to ask for an update by posting a question to the netbook-remix project at answers.launchpad.net.

---

### Post by rami on 2009-03-29
Boy this is a lenghty thread for something one would have thought to work out of the box!

I read most of this thread, but a lot of things I admit flew straight over my head. But I settled with the post 94 option.

I installed UNR 8.04 and did the tweaks to get 3d working, but something seems to be wrong.  glxinfo | grep direct gives me the following

```

ERROR!  sizeof(PsbDRIRec) does not match passed size from device driver
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```What should I do?

cat /var/log/Xorg.0.log | grep Xpsb gives me this, so am assuming it worked but its falling back to indirect rendering
```

(II) PSB(0): Debug: psbPreinitXpsb
(II) Loading sub module "Xpsb"
(II) LoadModule: "Xpsb"
(II) Loading /usr/lib/xorg/modules//Xpsb.so
(II) Module Xpsb: vendor="Tungsten Graphics Inc."
Xpsb - 2.2.0.32L.0020
(II) PSB(0): [Xpsb] Started kernel request thread.
(II) PSB(0): Xpsb extension for 3D engine acceleration enabled.

```

Also the mic does not seem to work??

---

### Post by 2oh1 on 2009-03-29
I'm also trying to follow the instructions on post #94 (I couldn't figure out how to install the belmont image, whereas the UNR 8.0.4 image installed easily).

So...  I'm following post #94, but I'm stuck here:
> Unfortunately, the UNR doesn't come with an up-to-date Xorg driver. For that, I added the ubuntu-mobile PPA to my /etc/apt/sources.list:

```
deb http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main
```

I'm assuming that means to open the file in a text editor and add the code to the end.  I did that, but couldn't save the file because it says I lack the proper permissions.  That's odd, since I installed the OS and I'm the only user.

Now what?

---

### Post by rami on 2009-03-29
@2oh1

```
sudo gedit /etc/apt/sources.list
```

It will ask for your password type it in and hit enter :)

---

### Post by 2oh1 on 2009-03-29
OK.  Now I'm stuck on step 3 (from post #94)

> Drop the firmware file, msvdx_fw.bin, into /lib/firmware/2.6.24-19-lpia/ (or the directory corresponding to your running kernel). Restart the system to reload the psb.ko kernel module; it doesn't want to reload on a running system. Run 'dmesg' (or check your system logs): you will see a line that says 

```
[drm:psb_do_init] *ERROR* Debug is 0x00000000
```

Drop the firmware file...?  Where do I find the firmware file, and then how do I figure out the proper directory for the kernel I'm running?

I'm guessing I'll need codes to move the file from my desktop to the proper folder...  no drag and drop, right?

---

### Post by rami on 2009-03-29
Nevermind guys, I had to downgrade my xserver-xorg-video-psb. Posts on page 20 explained everything. marduk667 and brteag00 hit it on the head :)

However the more I play around with my system the more I find glitches :(

As I said earlier, the mic isn't working at all. Sound works just fine, however if I suspend and come back, sound works on videos but not on Skype? I removed Pulseaudio and working on ALSA...

Also there is no hibernate option to be seen...am on UNR.

Finally after all this tweaking, is there a way to save all this into an image so I can use it later on if I screw up the system??

@2oh1 well I believe you can have a GUI drag and drop if you do a "sudo nautilus"

But most people just prefer doing it from the command line

sudo mv /path/of/file /path/of/destination
Here are the files:

[http://e.imagehost.org/download/0337/psb_dri](http://e.imagehost.org/download/0337/psb_dri)
[http://e.imagehost.org/download/0532/Xpsb](http://e.imagehost.org/download/0532/Xpsb)
[http://e.imagehost.org/download/0820/msvdx_fw](http://e.imagehost.org/download/0820/msvdx_fw)

---

### Post by 2oh1 on 2009-03-29
Got it - done.  I've completed everything from post #94 and confirmed it works.

Now a question:  I'm noticing a "chk chk" sound every now and then.  Is it the HD?  Is it something I need to worry about?  I doubt it has anything to do with the updating I just completed, but I thought I'd ask here anyway - just in case.

---

### Post by kylecronan on 2009-03-29
Yes, the clicking sound is from the hard drive.  The power management on this drive works very poorly, causing the drive head to park itself over and over again (it does the same thing in Windows).  Search this thread for "hdparm" and you will find information on some workarounds.  I emailed Samsung about this a while back, but they didn't respond.

Rami, sorry but I'm not sure what could be causing the glitches with sound.  Anyone currently running UNR who can confirm the microphone should work?  I'm still running a hacked-up version of Intrepid.

I believe Realtek actually provides binary drivers for Linux.  They might be worth a try.

As for saving a disk image, the simplest thing to do is to use 'dd' after booting from a CD or flash drive.  Try googling "dd disk image".

---

### Post by 2oh1 on 2009-03-30
Just out of curiosity - does the Dell version of Hardy have the HD power management clicking issues?

Also - thanks to all of you for the info in this thread!  Good god, there are some brilliant people in here.

---

### Post by rami on 2009-03-30
Oh stupid me! Apparently the mics were muted in alsamixer so I cranked it up.

But for some reason it didn't save all setting. So I did a "sudo alsactl store 0"

But still PCM isn't saving, it goes back to 40% :( I thought of doing a script, but then again its a sudo command so I would need to put my password everytime. Any thoughts?

Also resuming after standby, I get weird behaviour from the sound. Skype completely dies, Firefox sound on youtube (flash)  sometimes work, sometimes it doesn't. Couldn't really find a pattern

However mplayer always works, but I get two different errors everytime I open a video:

```
[AO_ALSA] alsa-lib: pcm_hw.c:573:(snd_pcm_hw_resume) SNDRV_PCM_IOCTL_RESUME failed:Function not implemented
```
OR
```
AO [pulse] Failed to connect to server: Connection refused
```

I am assuming the first is related to the problem.

NOTE: I completely removed pulseaudio and installed esound

ideas?

---

### Post by rami on 2009-03-30
> **kylecronan said:**
> 

As for saving a disk image, the simplest thing to do is to use 'dd' after booting from a CD or flash drive.  Try googling "dd disk image".

hmm maybe not an image, but rather make this modified UNR as a UNR itself. I mean just plug in the usb thumb into the mini and it self installs tthis not the original UNR

---

### Post by kylecronan on 2009-03-30
You could probably do a straight 'dd' disk image (without any compression as suggested by some tutorials) and then replace the image file contained within the UNR bootable CD.  A while back I looked at the UNR installer script and as I recall it uses dd itself.

---

### Post by TexasTele on 2009-03-31
Folks I am a total novice Ubuntu user but have been in IT for 20 years. I am trying to install Ubuntu on Dell Mini 12 that shipped with XP in order to show my clients they can use Ubuntu with Citrix on netbooks and eliminate MSFT desktop licenses. I have read through these threads as well as the novice threads. At this point in the game it is beyond me to engineer or understand all of this. Is there a FAQ anywhere that can walk someone like myself through? I can handle it and start from square one if necessary but want to ask first. Thank You.

---

### Post by rami on 2009-03-31
Well there are different options for this netbook. But I would highly recommend Ubuntu Notebook Remix (UNR) 8.04. 

Follow the instructions here [https://wiki.ubuntu.com/UNR#UNR%20Hardy%20Image%20Installation](https://wiki.ubuntu.com/UNR#UNR%20Hardy%20Image%20Installation) 

I would go for the .img option, due to the fact that netbooks don't have optical drives and you want to employ this in a business environment. Lugging an external CD-Drive around the office to install Ubuntu doesn't really paint a nice image :P

Anyways, once that is done. You should read up on post "94" on this thread. It has detailed explanation on how to get 3D rendering to work. The instructions refer to 3 files I linked to them in this [post]("http://ubuntuforums.org/showpost.php?p=6979724&postcount=372")

This netbook, sadly, is riddled with glitches. So you might want to consider other netbooks. Or at least read through this whole thread. I understand that a lot of stuff might fly over your head at the beginning, but after reading 38 pages stuff will "jell"

Of course if you have any questions just ask :)

An extra step I did after post "94" was get on a XFCE desktop. I highly recommend it to everybody reading this thread. GNOME is just a bit too heavy for this puny processor. I did a 

```
sudo apt-get install xubuntu-desktop
```

Worked like a charm!

---

### Post by sdslayer on 2009-04-03
I'm using the Belmont hardy with the suggestions on this forum.  My 3D isn't working, but everything else works ok.  I probably get a crash every 10-30 hrs or so, but that's not my big complaint.

My system is **very** slow.  Just web browsing is way slower than the 6 yr old mid tier laptop this replaced.  Am I being too picky? 

I've spent hours fixing the HDD click and have scripts on my desktop to enable/disable BT.  At this point, I just want to find a Win7 beta and install that.

---

### Post by TexasTele on 2009-04-03
Rami thank you very much I will start there and see what I get. Sounds like I would be better off ordering a Mini9 or Mini10 instead due to chipset? Business being business, we are somewhat of a "Dell Shop" to our clients, who like Dell nonetheleast of which because they are a Texas company. It is sometimes counterproductive but I can be seen carrying a Mac, I can be seen carrying a Dell, I can't necessarily be seen carrying an Acer.

---

### Post by matthiasak on 2009-04-05
Mini 10's also have the same chipset as the Mini 12. You may be best off going with a Samsung NC-20 (Via chipset) or any other netbook with an Intel 945GSE.

---

### Post by pastorUsuk on 2009-04-07
They should make a "Dell Mini 12" section, just like they have for the Acer Aspire One.

Hopefully when 9.04 stable rolls around, it will work without glitches...

I can't even get "startx" to work :(

---

### Post by BXL on 2009-04-07
Please correct me if I am wrong... reading the different threads regarding the Dell Mini 12 it seems like Ubuntu doesn't work out of the box, it's not possible to upgrade RAM and it has a slow HD due to PATA.

---

### Post by jackwcole on 2009-04-07
Your assumptions are not correct. The Mini 12 with Ubuntu works fine out of the box. The posts here are for those that originally had other O/S's or wanted to see if they could hack another version of Ubuntu. Yes, the PATA HD is slow and the CPU is not very fast with the current Poulsbo drivers.

---

### Post by 2oh1 on 2009-04-08
> **jackwcole said:**
> Your assumptions are not correct. The Mini 12 with Ubuntu works fine out of the box.

The mini 12 with Ubuntu works fine "out of the box"?  That's simply not true - unless you bought a Mini 12 that came with Ubuntu originally.  Even then, some people have had problems with it (freezes, etc).


> **jackwcole said:**
> The posts here are for those that originally had other O/S's or wanted to see if they could **hack** another version of Ubuntu.

Hack?

The version of Ubuntu Dell ships mini 12s with is, in fact, hacked.  Try getting 8.10 to run on your mini 12.  Let us know how it goes (and let us know what hacks you had to employ to make it work).

QUESTION:  Why isn't the Dell version of Ubuntu for the Mini 12 freely available?  The answer to that question is also the answer as to why your post is wrong.  Dell's version is hacked with proprietary code.


[QUOTE=BXL]

Please correct me if I am wrong... reading the different threads regarding the Dell Mini 12 it seems like Ubuntu doesn't work out of the box, it's not possible to upgrade RAM and it has a slow HD due to PATA.[/QUOTE]

Others here are faaaaaaaaaaaaaaar more qualified to speak on this subject than myself, but here's what I've learned:  Ubuntu Netbook Remix 8.04 works on the Mini 12 (minus 3D graphics), but you probably need to turn off the UNR desktop and use the standard Ubuntu desktop.  That's been my experience.  With the help of post #94 in this thread, you can get 3D graphics working properly.  I did.

Sadly, you can't upgrade RAM on the mini 12.  That's a shame, but then again, it's just a netbook.  If you need a real laptop, you're probably better off buying a real laptop.

The mini 12 does have a slow HD.  That's a shame too, but then again, it's just a netbook.

The thing is, we're still in the early days of netbooks.  I suspect that in a few years, there will be some really amazing options, but right now it seems like many of the companies involved are fighting this rather than supporting it.  Microsoft, especially, but Intel too.  They all want to sell higher end machines with higher profit margins.  I think the whole netbook thing caught these corporate types by surprise.  Initially, I'm guessing, they thought it was just a fad, but the reality is that many of us enjoy having a laptop for basic functions such as surfing the net on the go.  Thus, the netbook.

I bought a refurbished Mini 12 with a 6 cell battery and Windows XP from Dell.  I followed the superb advice from post #94 in this thread (and had some other help too - thanks so much to all!!!!).  With that help, I got UNR 8.04 running quite well.

I'm really happy with it.

---

### Post by BXL on 2009-04-08
@ 2oh1

Thanks for your answer. It's a pity that the Mini 12 is only available with 1 GB Ram. I don't care to much about the CPU since I mainly use Office. 

I assume that during the next months the gap between cheap Netbooks and expensive Subnotebooks will be filled with better-value Subnotebooks. 

Actually I am looking in replacing my Inspiron 510m and since it served me well during the last 5 years I thought that I stick with Dell. But 15" is just to large, the Latitude overpowered and overpriced. The Mini 12 just seemed to be what I am looking for... 

@ jackwcole

Sorry, since when is installing Ubuntu "hacking"? I don't care if Dells Ubuntu runs on the Mini 12, I wanted to know if the Ubuntu ISOs run out of the box or if I have to "hack" since installing Ubuntu etc. doesn't work out of the box ;-)

And the Ubuntu Mini 12 is, at least at the moment in Germany, not such a good deal. Choosing the same equipment it's around &#8364; 80,- more expensive than the Windows Mini 12.

---

### Post by kylecronan on 2009-04-11
I just found this:

[http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini-proposed/main/binary-lpia/](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini-proposed/main/binary-lpia/)

The psb driver is up to 0.27 now.  Anyone want to see if xv (and maybe even DRI) is now possible without xorg crashes?  I may not get to it for a while (sadly, I got used to using Vista + Cygwin for daily use months ago).

---

### Post by Largest on 2009-04-12
Hi,

I have a Dell Mini 12 and wanted to run ubuntu, thought it would be a piece of cake.
From what I've read here, looks like I'm stuck with XP if I want the full functionality of this fine piece of technology, is this correct?

---

### Post by rami on 2009-04-12
> **kylecronan said:**
> I just found this:

[http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini-proposed/main/binary-lpia/](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini-proposed/main/binary-lpia/)

The psb driver is up to 0.27 now.  Anyone want to see if xv (and maybe even DRI) is now possible without xorg crashes?  I may not get to it for a while (sadly, I got used to using Vista + Cygwin for daily use months ago).

I broke my direct rendering after getting it to work via #94. I stripped out GNOME installed XFCE and then Fluxbox, installed GNOME again, tons of tweaks to get it right. Settled with Fluxbox, its great for the Dell, much faster and lighter than GNOME and XFCE. Wish I gave Fluxbox more than 5 minutes before :)

But now I lost direct rendering somewhere along the road, so am willing to try this Kyle. But honestly I don't quite understand this direct rendering thing. I mean I don't play games, don't really need compiz (won't work on Fluxbox). Would I really benefit from direct rendering? What do I have to gain? Speedier window switching? Better scrolling?

Anyways am assuming this is the right package:

[http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini-proposed/main/binary-lpia/xserver-xorg-video-psb_0.27.0+repack-0netbook2_lpia.deb](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini-proposed/main/binary-lpia/xserver-xorg-video-psb_0.27.0+repack-0netbook2_lpia.deb)

what about the rest?

---

### Post by kylecronan on 2009-04-12
The only thing that comes to mind is that Flash uses OpenGL to do accelerated full screen display.  It doesn't really matter though, because the code that feeds into that is so slow as to makes full screen flash video unusable on this hardware anyway.

My main concern is the X crashes.  Brteag00's UNR config seems to do the best job of minimizing them, much better than Dell's version in fact, but I still won't use a machine for regular daily tasks if it could crash on me at any time.  And in order to make the crashes go away, you have to give up xv, so no accelerated video at all (and I've yet to see a CPU fast enough to play 30 fps without video acceleration, certainly not the Atom).  DRI is something I use very occasionally, but I need video playback just about every day.

The other relevant packages are libdrm*, libgl*, linux-image*, and linux-ubuntu-modules*.

---

### Post by teatimest on 2009-04-12
Hi Kylecronan,

I would like to try them. How can I add the proposed repo? Or should I do it manually?

> **kylecronan said:**
> The only thing that comes to mind is that Flash uses OpenGL to do accelerated full screen display.  It doesn't really matter though, because the code that feeds into that is so slow as to makes full screen flash video unusable on this hardware anyway.

My main concern is the X crashes.  Brteag00's UNR config seems to do the best job of minimizing them, much better than Dell's version in fact, but I still won't use a machine for regular daily tasks if it could crash on me at any time.  And in order to make the crashes go away, you have to give up xv, so no accelerated video at all (and I've yet to see a CPU fast enough to play 30 fps without video acceleration, certainly not the Atom).  DRI is something I use very occasionally, but I need video playback just about every day.

The other relevant packages are libdrm*, libgl*, linux-image*, and linux-ubuntu-modules*.

---

### Post by kylecronan on 2009-04-12
Try adding this to /etc/apt/sources.list.  I'm not sure if all the dependencies and everything will work out though.

```

deb http://netbook-remix.archive.canonical.com/ubuntu hardy-dell-mini-proposed main

```

---

### Post by teatimest on 2009-04-14
Thank you kylecronan.
I added the repo and did the update all. It included update on kernel. In the new one, wifi did not work, so I am using old kernel. I don't see much difference. Nothing broken but nothing improved.

> **kylecronan said:**
> Try adding this to /etc/apt/sources.list.  I'm not sure if all the dependencies and everything will work out though.

```

deb http://netbook-remix.archive.canonical.com/ubuntu hardy-dell-mini-proposed main

```

---

### Post by fitzkarraldo on 2009-04-14
> **kylecronan said:**
> I just found this:

[http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini-proposed/main/binary-lpia/](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini-proposed/main/binary-lpia/)

The psb driver is up to 0.27 now.  Anyone want to see if xv (and maybe even DRI) is now possible without xorg crashes?  I may not get to it for a while (sadly, I got used to using Vista + Cygwin for daily use months ago).

Hi kyle,
I was able to install the same upgrades provided at that url without adding any source in my apt config. I was actually using the configuration that you suggested at post #252.

the upgrade provided me several new packages including the new kernel 2.6.24-22-lpia, I just rebooted the netbook and everything seems to work fine (wifi included). I'll inform you about performances and crashed.

PS: with the previous install I was experiencing slow scrolling in firefox and slow performances in window change (i.e. alt+tab sequence on the keyboard). is it normal? if so, is it dued to the processor or the bad video driver?

---

### Post by kylecronan on 2009-04-14
Fitzkarraldo, what do you mean by "with the previous install"?  It just started doing it with this latest update?  Or it just stopped?

I'm not sure why the scrolling would be slow, but I did notice that a lot of the times I got the xorg crash it was when I was scrolling.  So maybe you're on to something there.

Yeah, let us know if you get the X crash or the thing where it just stops responding for a while but then comes back to life later.

Kyle

PS.  Now that this new psb_dri.so is available I'm pretty sure it would now be possible to get Intrepid or Jaunty working properly.

---

### Post by fitzkarraldo on 2009-04-15
> **kylecronan said:**
> Fitzkarraldo, what do you mean by "with the previous install"?  It just started doing it with this latest update?  Or it just stopped?

I'm not sure why the scrolling would be slow, but I did notice that a lot of the times I got the xorg crash it was when I was scrolling.  So maybe you're on to something there.

Yeah, let us know if you get the X crash or the thing where it just stops responding for a while but then comes back to life later.

Kyle

PS.  Now that this new psb_dri.so is available I'm pretty sure it would now be possible to get Intrepid or Jaunty working properly.

The previous install was the configuration that I had with post #252 before the update I made yesterday (new kernel and psb). 
I just would like to know if it's a general problem and, if so, why it is/was happening (bad hardware or bad video driver?) I don't know if the update of yesterday improved the situation, I'm at work now and I'll check it tonight.

---

### Post by fitzkarraldo on 2009-04-15
> **kylecronan said:**
> 

PS.  Now that this new psb_dri.so is available I'm pretty sure it would now be possible to get Intrepid or Jaunty working properly.

This might be very very very interesting....

---

### Post by fitzkarraldo on 2009-04-15
> **kylecronan said:**
> 

Yeah, let us know if you get the X crash or the thing where it just stops responding for a while but then comes back to life later.



Everything seems ok, moreover my video performances seems much better (scrolling for example).

I looked at the xserver-xorg-video-psb changelog and something is wonderful (I remember you that with the upgrade of yesterday I moved xserver-xorg-video-psb from 0.16.0+repack-0ubuntu1-804um6 to 0.27.0+repack-0netbook2):


```
xserver-xorg-video-psb (0.27.0+repack-0netbook2) netbook-common; urgency=low

  * **Rebuild against libdrm2 2.3.0.23+repack-0netbook4. No code changes.**

 -- Steve Magoun <steve.magoun@canonical.com>  Thu, 26 Mar 2009 14:29:40 -0400

xserver-xorg-video-psb (0.27.0+repack-0netbook1) netbook-common; urgency=low

  * **New upstream release (Build 0038)**
  * Repacked upstream tarball:
    - Removed debian directory
  * Changelog from upstream:
    - **enable HDMI hotplug**

 -- Alberto Milone <alberto.milone@canonical.com>  Fri, 20 Mar 2009 10:17:25 +0100

xserver-xorg-video-psb (0.23.0+repack-0netbook1) netbook-common; urgency=low

  * **New upstream release (Build 0033)**
  * Repacked upstream tarball:
    - Removed debian directory
  * Changelog from upstream:
    - pass the HDMI certification

 -- Debbie Beliveau <debbie.beliveau@canonical.com>  Tue, 17 Feb 2009 21:27:34 +0000

xserver-xorg-video-psb (0.22.0+repack-0netbook1) netbook-common; urgency=low

  * **New upstream release (Build 0032)**
  * Repackged upstream tarball:
    - Removed debian directory
  * Changelog from upstream:
    - **fix the xserver hang issue**
  * Also reportedly fixes HDMI output problems

 -- Steve Magoun <steve.magoun@canonical.com>  Wed, 11 Feb 2009 18:00:09 -0500

xserver-xorg-video-psb (0.21.0+repack~0netbook3-0netbook1) hardy; urgency=low

  * New upstream release

 -- Michael Frey <michael.frey@canonical.com>  Fri, 06 Feb 2009 16:18:48 +0000

xserver-xorg-video-psb (0.21.0+repack~0netbook2-0netbook1) hardy; urgency=low

  * **New interim upstream release from Intel (Build 0031) fixes video tearing**
  * Repackaged upstream tarball:
    - Removed debian directory
    - Removed .git directory
  * Wacky version number required because we are expecting a final 0.21.0
    release someday, and we expect it will need repacking too.

 -- Steve Magoun <steve.magoun@canonical.com>  Tue, 03 Feb 2009 17:31:37 -0500

xserver-xorg-video-psb (0.21.0+repack~0netbook1) hardy; urgency=low

  * **New upstream release from Intel.  Fix for video tearing and crash.**

 -- Michael Frey <michael.frey@canonical.com>  Thu, 22 Jan 2009 12:00:40 -0500

xserver-xorg-video-psb (0.20.0+repack~0netbook2) hardy; urgency=low

  * Rebuild against new libdrm-dev headers for correct psb version

 -- Michael Frey <michael.frey@canonical.com>  Wed, 07 Jan 2009 17:04:29 -0500

xserver-xorg-video-psb (0.20.0+repack~0netbook1) hardy; urgency=low

  * New upstream release

 -- Michael Frey <michael.frey@canonical.com>  Wed, 07 Jan 2009 13:56:32 -0500

xserver-xorg-video-psb (0.16.0+repack-0ubuntu1~804um5netbook2) hardy; urgency=low

  * Upstream patch to fix Video Tearing issue (LP: #308760)

 -- Michael Frey <michael.frey@canonical.com>  Tue, 16 Dec 2008 17:37:18 -0500


```

---

### Post by kylecronan on 2009-04-15
> **fitzkarraldo said:**
> 
```

  * Changelog from upstream:
    - **fix the xserver hang issue**

```

Yay, after 400 posts we finally have a proper video driver!

I'm installing the latest jaunty lpia daily to see if this driver is compatible with xorg 1.6.

---

### Post by danboid on 2009-04-16
Hi fellow poulsbo Linux victims! ;)

What a mess eh?

I bought a Dell Inspiron Mini 10 (with XP Home (yuk!) preloaded unfortunately- I'm sending the XP disks back today, hopefully they'll give me my refund) a couple of days ago and I've barely used it yet as I've just been trying all sorts of different distros, configs and switches trying to get the video to work properly- no luck yet. The best I've had so far was installing a recent jaunty i386 desktop daily build- all the hardware worked but the video was stuck at 800x576 with VESA driver.

Reading through this thread (which I did in full yesterday) I couldn't see anyone else who was trying to get Ubuntu running on a Mini 10- is the Mini 10 a UK only model? Of course the Mini 12 has a bigger, higher-res screen but I'm presuming that apart from the screen specs that the hardware (esp. the video chipset) in the Mini 12 will be pretty much identical to the mini 10 so I SHOULD be able to follow the instructions in this thread as long as I change my xorg.conf to reflect that I can't do more than "1024x576" right? What resolutions can I achieve on the mini 10? I'm presuming it can do 1024x576, 800x576 and probably 640x480? I've had a damn good search but I've failed to find ANY guides or info for anyone wanting to install Linux on the mini 10 - nothing :(

I've got my fingers crossed that kyle will be successful getting this latest driver working under Jaunty as I would appreciate an up-to-date kernel and system but I could live with Hardy for a while if I meant I could get accelerated 2D AND DRI/OGL accel. I'm not a gamer but I DO need DRI working as one of the main reasons I bought this was to run pianobooster on it which requires opengl for smooth playback scrolling so its certainly a less demanding DRI app.

I can only find jaunty lpia as an alternate install iso and so far I have not had any luck with using unetbootin with any ubuntu alternate installers as it always complains about not being able to find the install medium (CD). Would I have to get a USB CD/DVD drive or is there a working method to install an alternate iso off USB? Only the desktop iso's boot and install via unetbootin for me.

Post #94 and the rest of this thread seems to agree that that my best bet for getting 3D accel working would be to install UNR 1.0.1 and tweak from there but UNR 1.0.1 doesn't seem to like the mini 10. I've tried installing it three times now and its done the same thing every time- it starts booting, Ubuntu logo/ bar gets to top, I see the login prompt then the screen starts flickering before I get the error:

----------------

ERROR: The OEM installer failed. Your system may not be usable yet. Please report this bug to your vendor.

To create a new user so you can use your new system normally, type:

adduser USERNAME

... replacing USERNAME with the username you would like to use (your first name in lower case is normally a reasonable choice), and follow the prompts.

If this succeeds, type 'exit' to reboot the system.

bash: no job control in this shell
-------------------------

I can get to the root prompt and TRY adding a user as it says but its near impossible as the keyboard doesn't respond to my input properly- I know thats not a hardware fault as the keyboard works fine under jaunty. I have to push keys multiple times for them to register on the terminal- you think you've typed the right command (according to the display) but then you push enter and bash/dash whatever rejects it has a different idea of what you typed in.

So what now? I'd certainly like some advice but I think the next thing I'll try will be to install Ubuntu 8.04.02 i386 desktop then try applying the instructions in post #94, combine that with the Dell xorg.conf (that I'll adjust for the mini 10 display) that somebody posted somewhere in this thread and hope for the best? Or might I be better doing that with intrepid desktop install instead?

I think it goes without saying that I'm very disappointed with Dell and Intel. One of the main reasons I picked this device was precisely because it had intel graphics and, up until poulsbo at least, intel had always provided up-to-date, fully open source drivers which would allow you get fully accelerated X w/ DRI running under and Linux OS straight out of the box. Seems I can no longer recommend intel graphics to (potential) Linux users.

FINALLY (sorry about this mammoth post, had a lot to get off my chest) is there nothing that can be done to consolidate and clear up this ridiculously long thread? If the OP is still with us then it would be fantastic if he could edit post #1 so that it links to post #94, that post with Dells xorg.conf (what post # was that?), the extra files required to get things working as well as any other important info or links that made their way into this thread. Even better would be a Ubuntu on Dell Mini 10/12 wiki page

Thanks for your help!

Dan

---

### Post by dimeified on 2009-04-16
i am downloading the newest lpia beta release, i will try to install it tonight on my mini 12.

---

### Post by kylecronan on 2009-04-16
Here's how to get the alternate installers to work with USB:

* Use UNetbootin to copy the installer to USB flash
* Boot the installer
* Before you try to install, switch to the F2 console and mount your USB drive (/dev/sdb1) on /cdrom
* I don't remember if this is really necessary, but just in case: cd to /cdrom/dists and delete the empty file "stable" and replace it with a copy of the jaunty directory: cp -a jaunty stable
* Go through the installer steps (including partitioning) until it fails somewhere so you can get to the main installer menu
* Choose "load installer components from CD" and select "iso-scan"
* It will start installing the base system and so forth

I'll let you know how things work out with the new drivers.  First I need to get the wireless working.

Danboid, very much agreed that we need to make this thread more accessible- it has become a monster!  I don't think the OP is around anymore but I could edit post #2.

---

### Post by danboid on 2009-04-16
Hi Kyle!

I referred to my netbook as the Mini 10 but actually its called the 'Inspiron 1010' although I'm 99% sure its two names for the same product- it certainly seems to have the same spec as the Mini 10 I saw on their site.

I tried booting Hardy 8.04.02 i386 desktop but it only got as far as running the local scripts (rc.local) then the boot stops at that point.

I've just tried your instructions for installing jaunty lpia alternate with no luck. I can switch to the 2nd VT and mount /dev/sdb1 under /cdrom fine (I do this as soon as the first blue installer screen appears right?) but it doesn't find any install medium. I tried to delete the stable dir as you suggested but I'm told that the drive is read only- its not as I've set it to be write enabled. I also tried mounting with this command

mount -t vfat /dev/sdb1 /cdrom -o rw

but I still had the same problem- read only. Strange.

If I choose 'load installer components from cd' it just says 'Failed to copy file from CD-ROM. Retry? <Yes/No> - no sign of any "iso-scan" option in any of the menus far as I can see.

As for wifi- that worked out of the box for me under jaunty i386 on my 1010- has the mini 12 not got the same broadcom wifi chipset as mine?

Yes, I think it'd be good if you edit post #2. Apart from a link to post #94 is should have a link to the post with the Dell xorg.conf, links to the extra files required, a link to the post on how to compile (was it mplayer?) with libva support, the 'best' hdparm settings to stop the drive click, a link to Dells official 'Ubuntu on Mini' forum (note they don't have such a thing for the Mini 10/ Inspiron 1010) and any other gems that have surfaced in this epic- I'm sure there's some I've missed off that list.

I've never ran lpia before - does it not have all the packages in the repo that are available to i386 users? I'm sure that was mentioned in this thread. If thats the case I think I'd rather run the i386 version but will the new driver only run under jaunty lpia, if it runs at all? If thats the case then where do I get the latest code for the psb driver to compile it myself- if it is publically available?

---

### Post by kylecronan on 2009-04-16
Hmm, I don't remember the exact procedure I used.  Maybe wait until you get the first failure before mounting the USB on /cdrom?  Sorry I can't be more specific: I had to fiddle with it a lot before I stumbled onto something that worked.  Oh, and make sure you're using the daily and not the beta.

For the wireless, you just have to install linux-restricted-modules and reboot.  I guess the lpia version doesn't come with this installed by default, whereas i386 does.  As to your question about the difference, there really does seem to be a significant speedup when all the system software is compiled for lpia.  You might occasionally need a piece of software that hasn't been compiled for that architecture, but you can just manually download the i386 deb and force install it with dpkg.

Now, the results of my experiments with Jaunty are in.  I got everything installed, but X wouldn't start.  The psb DRM module loads like it did before, but I don't see any /dev/dri/card0.  I think it is probably related to this:

[http://lkml.org/lkml/2009/3/1/58](http://lkml.org/lkml/2009/3/1/58)

Intrepid uses 2.6.27 and would not have this issue, so I may go back to that.  I really like the fast bootup in Jaunty though!

I'll add some links to post 2 sometime in the next few days.

---

### Post by matthiasak on 2009-04-16
I have a belmont .img file now and I've succeeded in putting it on my USB drive, however now I have a problem booting it on my Dell Mini 10... It is loading the file ubnkern (20KB)and then tries to load ubninit (1.35 GB) and can't because i dont have that much memory. Is there some special option should add in the boot option to allow it to page a temporary area of sorts...

I'm so close to just having Ubuntu on my system finally #-o Just need it to boot finally!

---

### Post by kylecronan on 2009-04-17
Here's the status with the latest drivers: psb_dri.so still only works with Xorg 1.4, so if you want DRI you're stuck with Hardy.  However, the Xpsb module works with Xorg 1.5, so you can have xv video acceleration in Intrepid.  Jaunty is not an option as far as I can tell, because the psb DRM module didn't work for me with both the Ubuntu 2.6.28 and mainline 2.6.29.1.

If you can live without DRI/OpenGL and want to upgrade to Intrepid, here are my notes on the process.  It is not easy though!

```

use UNetbootin to install ubuntu-8.10-alternate-lpia.iso onto USB flash
boot installer
detect ethernet interface, use mirror http://ports.ubuntu.com directory: /
install will fail to get kernel; continue
install will fail to install grub
boot installer USB into rescue mode, setup network and mount root partition
spawn a shell in your root partition
wget http://ports.ubuntu.com/pool/main/l/linux-lpia/linux-image-2.6.27-4-lpia_2.6.27-4.9_lpia.deb
dpkg -i linux-image-2.6.27-4-lpia_2.6.27-4.9_lpia.deb
manually edit /boot/grub/menu.1st; after "End Default Options" add:
title           Ubuntu 8.10
kernel          /boot/vmlinuz-2.6.27-4-lpia root=/dev/sda5 ro quiet splash
initrd          /boot/initrd.img-2.6.27-4-lpia

boot your system and login on the console
aptitude install ubuntu-desktop

wireless:
download and install linux-restricted-modules-2.6.27-4-lpia_2.6.27-4.4_lpia.deb

sudo /bin/bash
aptitude install dpkg-dev linux-image-lpia
cd
echo "deb-src http://netbook-remix.archive.canonical.com/ubuntu hardy-dell-mini-proposed main restricted universe" >> /etc/apt/sources.list
apt-get update (ignore the warning)
apt-get source linux-ubuntu-modules-2.6.24
cd linux-ubuntu-modules-2.6.24-2.6.24/ubuntu/media/drm-poulsbo/
sed -i '/EXPORT_SYMBOL(idr_/d' drm_compat.c
make -C /lib/modules/2.6.27-4-lpia/build M=`pwd` clean
make -C /lib/modules/2.6.27-4-lpia/build M=`pwd`
cp drm_psb.ko psb.ko /lib/modules/2.6.27-4-lpia/kernel/drivers/gpu/drm/
mv /lib/modules/2.6.27-4-lpia/kernel/drivers/gpu/drm/drm.ko /lib/modules/2.6.27-4-lpia/kernel/drivers/gpu/drm/drm.ko.disabled
depmod -a
mkdir /usr/include/drm ; cp psb_drm.h psb_reg.h /usr/include/drm/
cd
apt-get source libdrm=2.3.0.23+repack-0netbook4
apt-get build-dep libdrm=2.3.0.23+repack-0netbook4
apt-get build-dep xserver-xorg-video-psb
cd libdrm-2.3.0.23+repack
./configure --prefix=/usr --exec-prefix=/
make
make install
cd
apt-get source xserver-xorg-video-psb
cd xserver-xorg-video-psb-0.27.0+repack
./configure --prefix=/usr
make (ignore the failure in exa/)
cp src/.libs/psb_drv.so /usr/lib/xorg/modules/drivers
cd
wget http://netbook-remix.archive.canonical.com/dists/hardy-dell-mini/restricted/binary-lpia/libva1_0.29-9_lpia.deb
dpkg -i libva1_0.29-9_lpia.deb
wget http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini-proposed/universe/binary-lpia/psb-video_0.28+0038-0netbook1_lpia.deb
dpkg -i psb-video_0.28+0038-0netbook1_lpia.deb
wget http://netbook-remix.archive.canonical.com/dists/hardy-dell-mini-proposed/universe/binary-lpia/xorg-modules-xpsb_0.16+0038-0netbook1_lpia.deb
dpkg -i xorg-modules-xpsb_0.16+0038-0netbook1_lpia.deb
wget http://netbook-remix.archive.canonical.com/dists/hardy-dell-mini-proposed/main/binary-lpia/libgl1-mesa-dri-psb_0.24+repack+0038.1-0netbook1_lpia.deb
dpkg -i libgl1-mesa-dri-psb_0.24+repack+0038.1-0netbook1_lpia.deb
cat <<EOF >/etc/X11/xorg.conf
Section "Device"
    Identifier "poulsbo"
    Driver "psb"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "poulsbo"
EndSection
EOF
reboot

```

---

### Post by madman_sp on 2009-04-18
Hello everybody!

I have following this forum for many months (I bought my mini 12 on january) and first I want to say ... THANKS!!

My default ubuntu installation was crashing every time and thanks to this forum I was able to install a functional hardy UNR (post #94) but only with 2D acceleration (full res and working video. I don`t know why DRI didn`t work). For the moment enought for me. But I tried to install the new kernel and psb-driver you provide recently (psb 0.27), the result:
kernel problem:
    No wifi (detect the device but no run it).
psb-driver problem:
    X crashes when I run a video or the totem plays a mp3 (the sound video effects of totem I think is crashing because amarok plays well). It crash and start again in logon screen like when you press ctrl+alt+backspace.

With grub I run the last functional kernel and wifi comes back but I am not able to do work correctly the psb-driver.

Well, my question is ... exist a solution for the psb-driver 0.27 or I will have to downgrade the driver. I have UNR hardy with Xorg 1.4.1.

If you want to know something please, tell me what and how I get the info (commands or something). I am a noob in linux ;P.

Thanks again and sorry my bad English.

---

### Post by snowpine on 2009-04-18
> **kylecronan said:**
> Here's how to get the alternate installers to work with USB:

* Use UNetbootin to copy the installer to USB flash
* Boot the installer
* Before you try to install, switch to the F2 console and mount your USB drive (/dev/sdb1) on /cdrom
* I don't remember if this is really necessary, but just in case: cd to /cdrom/dists and delete the empty file "stable" and replace it with a copy of the jaunty directory: cp -a jaunty stable
* Go through the installer steps (including partitioning) until it fails somewhere so you can get to the main installer menu
* Choose "load installer components from CD" and select "iso-scan"
* It will start installing the base system and so forth



Good news, there is a new daily build of lpia that fixes the installer bug. None of these steps are necessary any more (except for steps 1-2 obviously). This is tested on my Mini 9; unless there are big hardware differences, it should work on the Mini 12 as well.

[http://cdimage.ubuntu.com/ports/daily/current/](http://cdimage.ubuntu.com/ports/daily/current/)

---

### Post by dimeified on 2009-04-18
I am downloading the iso now to install on my mini12. Luckily i have an external cd drive so i should be able to just boot from the cd. What screen resolutions did you get working?

update: installed flawlessly from usb cdrom.
video, glxinfo reported i am using direct rendering.
however, screen resolution is set to 1024x768.

---

### Post by dimeified on 2009-04-18
Well, its now 2:10 and im up and online on the mini. I am using my mobile broadband verizon usb dongle to connect to the internet though. My internal wireless card doesnt work at the moment, but it seems that the broadcom st proprietary driver is loaded for it. Network manager even shows SSID's of networks around me. It might be a human error, i'll double check my settings.
glxinfo reports as follows

dimeified@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.4
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shading_language_120, GL_ARB_shadow, 
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_program_debug, GL_MESA_resize_buffers, 
    GL_MESA_texture_array, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_fragment_program, GL_NV_light_max_exponent, 
    GL_NV_point_sprite, GL_NV_texture_rectangle, GL_NV_texgen_reflection, 
    GL_NV_vertex_program, GL_NV_vertex_program1_1, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGI_texture_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

64 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xbc 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xbd 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xbe 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xbf 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xc0 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xc1 24 tc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xc2 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xc3 24 tc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xc4 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xc5 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xc6 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xc7 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xc8 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xc9 24 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xca 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xcb 24 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xcc 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xcd 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xce 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xcf 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xd0 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xd1 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xd2 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xd3 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xd4 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xd5 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xd6 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xd7 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xd8 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xd9 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xda 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xdb 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xdc 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0xdd 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xde 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xdf 24 dc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xe0 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xe1 24 dc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xe2 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xe3 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xe4 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xe5 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xe6 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xe7 24 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xe8 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xe9 24 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xea 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xeb 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xec 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xed 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xee 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xef 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xf0 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xf1 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xf2 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xf3 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xf4 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xf5 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xf6 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xf7 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xf8 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xf9 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x3b 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

128 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x3c  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x3d  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x3e  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x3f  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x40  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x41  0 tc  0  8  0 r  .  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x42  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x43  0 tc  0  8  0 r  y  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x44  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x45  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x46  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x47  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x48  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x49  0 tc  0  8  0 r  .  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x4a  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x4b  0 tc  0  8  0 r  y  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x4c  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x4d  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x4e  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x4f  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x50  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x51  0 tc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x52  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x53  0 tc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x54  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x55  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x56  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x57  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x58  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x59  0 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x5a  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x5b  0 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x5c  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x5d  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x5e  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x5f  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x60  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0x61  0 tc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0x62  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0x63  0 tc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0x64  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x65  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x66  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0x67  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0x68  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x69  0 tc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x6a  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0x6b  0 tc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0x6c  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6d  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x6e  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x6f  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x70  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x71  0 tc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x72  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0x73  0 tc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0x74  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x75  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x76  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x77  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x78  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x79  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7a  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x7b  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7c  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x7d  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x7e  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  0  0  0  0  0  0 0 None
0x7f  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  0 16 16 16  0  0 0 Slow
0x80  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x81  0 dc  0  8  0 r  .  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x82  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  8  0  0  0  0  0 0 None
0x83  0 dc  0  8  0 r  y  .  3  3  2  0  0  0  8 16 16 16  0  0 0 Slow
0x84  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x85  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x86  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  0  0  0  0  0  0 0 None
0x87  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  0 16 16 16  0  0 0 Slow
0x88  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x89  0 dc  0  8  0 r  .  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x8a  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  8  0  0  0  0  0 0 None
0x8b  0 dc  0  8  0 r  y  .  3  3  2  0  0  8  8 16 16 16  0  0 0 Slow
0x8c  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x8d  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x8e  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0  0  0  0  0  0 0 None
0x8f  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  0 16 16 16  0  0 0 Slow
0x90  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x91  0 dc  0 16  0 r  .  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x92  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  8  0  0  0  0  0 0 None
0x93  0 dc  0 16  0 r  y  .  5  6  5  0  0  0  8 16 16 16  0  0 0 Slow
0x94  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x95  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x96  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x97  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x98  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x99  0 dc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x9a  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 None
0x9b  0 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x9c  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x9d  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0x9e  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0  0  0  0  0  0 0 None
0x9f  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  0 16 16 16  0  0 0 Slow
0xa0  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xa1  0 dc  0 24  0 r  .  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xa2  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  8  0  0  0  0  0 0 None
0xa3  0 dc  0 24  0 r  y  .  8  8  8  0  0  0  8 16 16 16  0  0 0 Slow
0xa4  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xa5  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xa6  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0  0  0  0  0  0 0 None
0xa7  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  0 16 16 16  0  0 0 Slow
0xa8  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xa9  0 dc  0 24  0 r  .  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xaa  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8  0  0  0  0  0 0 None
0xab  0 dc  0 24  0 r  y  .  8  8  8  0  0 24  8 16 16 16  0  0 0 Slow
0xac  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xad  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xae  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0xaf  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0xb0  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xb1  0 dc  0 32  0 r  .  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xb2  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8  0  0  0  0  0 0 None
0xb3  0 dc  0 32  0 r  y  .  8  8  8  8  0  0  8 16 16 16 16  0 0 Slow
0xb4  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xb5  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xb6  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0xb7  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0xb8  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xb9  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0xba  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0xbb  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

---

### Post by kylecronan on 2009-04-18
snowpine, yes, there are huge hardware differences between the Mini 9 and Mini 12.  However, there is an easier way: I have found that Ubuntu's usb-creator program works much better than UNetbootin.  But it requires that you have access to a linux system already.

dimeified, you've got the software rasterizer, not hardware-based rendering.  Real DRI (as in (AI)GLX support for OpenGL) is not possible with the vesa driver.

madman_sp, are you still getting the Xorg crash with the kernel update you mentioned?  Did you install all updates available from that proposed repo or did you manually install just some of them?  Post a /var/log/Xorg.0.log with your crash in it (note that sometimes it ends up in /var/log/Xorg.0.log.old).

A few quick notes:

The psb driver is not compatible with Xorg 1.6, even with a compatible kernel such as 2.6.27.  It is source compatible but when you try to run it the X server gets all the way through its initialization and then segfaults.

Jaunty can be made to work with psb if you downgrade the kernel to the lpia kernel from Intrepid and downgrade Xorg to Intrepid's 1.5.2.  As with Intrepid, GLX is not possible.

---

### Post by madman_sp on 2009-04-19
HI!

what I did:
I put the repo "deb [http://netbook-remix.archive.canonical.com/ubuntu](http://netbook-remix.archive.canonical.com/ubuntu) hardy-dell-mini-proposed main" on source.list and installed the packages "libgl1-mesa-dri-psb" (v0.24), "xserver-xorg-video-psb" (v0.27) and the kernel 2.6.24-22, the old kernel was 2.6.24-19.

ok, then I rebooted and ran the new kernel. First Wifi didn`t work and ... incredible ... I HAD DRI!!!! :) Flash on firefox worked good but when I tried to run a video with VLC or Totem the X crashed.

Here is the "Xorg.O.log.old". I don`t know what look for, sorry.

```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux chobo 2.6.24-19-lpia #1 SMP Mon Nov 3 15:25:26 UTC 2008 i686
Build Date: 15 April 2008  05:24:02PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 20 00:12:31 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81cea60
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,8100 card 1028,02b1 rev 06 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,8108 card 1028,02b1 rev 06 class 03,00,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,811b card 1028,02b1 rev 06 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,8110 card 0000,0000 rev 06 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,8112 card 0000,0000 rev 06 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,8114 card 1028,02b1 rev 06 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,8115 card 1028,02b1 rev 06 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,8116 card 1028,02b1 rev 06 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,8117 card 1028,02b1 rev 06 class 0c,03,20 hdr 00
(II) PCI: 00:1f:0: chip 8086,8119 card 1028,02b1 rev 06 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,811a card 1028,02b1 rev 06 class 01,01,80 hdr 00
(II) PCI: 02:00:0: chip 10ec,8136 card 1028,02b1 rev 02 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 14e4,4315 card 14e4,04b5 rev 01 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd8400000 - 0xd84fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xd80fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation unknown chipset (0x8108) rev 6, Mem @ 0xd8100000/19, 0xd0000000/27, 0xd8380000/17, I/O @ 0x1800/3
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[1] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[2] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[3] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[4] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[5] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[10] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[11] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[12] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[13] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[1] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[2] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[3] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[4] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[5] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[7] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[10] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[11] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[12] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[13] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[5] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[6] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[7] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[8] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[9] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[16] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[17] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[18] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[19] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "psb"
(II) Loading /usr/lib/xorg/modules/drivers//psb_drv.so
(II) Module psb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.27.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) Debug: psbSetup
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) PSB: driver for Intel GMA500 chipsets: Intel GMA500
(II) Primary Device is: PCI 00:02:0
(II) Debug: psbProbe
(--) Assigning device section with no busID to primary device
(--) Chipset Intel GMA500 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[5] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[6] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[7] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[8] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[9] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[16] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[17] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[18] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[19] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) PSB(0): Debug: Allocating new device
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[5] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[6] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[7] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[8] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[9] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[18] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[19] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[20] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[21] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[22] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) PSB(0): Debug: psbPreInit
(II) PSB(0): psb_drv - 2.3.2.32L.0038
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) PSB(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) PSB(0): Depth 24, (==) framebuffer bpp 32
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(--) PSB(0): Linear framebuffer at 0x0
(==) PSB(0): RGB weight 888
(==) PSB(0): Default visual is TrueColor
(==) PSB(0): Use hardware cursor.
(==) PSB(0): Using ACPI for LVDS detection.
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so
(II) PSB(0): Debug: psbPreinitXpsb
(II) Loading sub module "Xpsb"
(II) LoadModule: "Xpsb"
(II) Loading /usr/lib/xorg/modules//Xpsb.so
(II) Module Xpsb: vendor="Tungsten Graphics Inc."
	compiled for 1.4.0.90, module version = 0.1.0
(II) PSB(0): Debug: psbDeviceScreenInit
(II) PSB(0): Debug: Initializing device
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) PSB(0): Debug: MMIO virtual address is 0xb7aac000
(--) PSB(0): Mapped PCI MMIO at physical address 0xd8100000
	with size 512 kiB
(--) PSB(0): Detected 8060 kiB of "stolen" memory set aside as video RAM.
(EE) PSB(0): screnIndex is:0;fbPhys is:0x3f800000; fbsize is:0x007df000
(--) PSB(0): Mapped graphics aperture at physical address 0x3f800000
	with size 7 MiB
(II) PSB(0): Debug: DRM device init
(II) PSB(0): Poulsbo MemClock 533, CoreClock 200
(II) PSB(0): Poulsbo Latencies 324 744 210 450
(II) PSB(0): sku_value is 0x00800000, sku_bSDVOEnable is 1, sku_bMaxResEnableInt is 0
(II) PSB(0): Debug: psbInitOutputs
(II) PSB(0): Debug: psbLVDSInit
(II) PSB(0): Output LVDS0 using monitor section Configured Monitor
(II) Debug: i830_psbOutputInit
(II) PSB(0): I2C bus "LVDSBLC_B" initialized.
(II) PSB(0): I2C bus "LVDSDDC_C" initialized.
(II) PSB(0): I2C device "LVDSBLC_B:BLC Control" registered at address 0x58.
(II) PSB(0): Debug: i830_psbDDCGetModes
(II) PSB(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) PSB(0): initializing int10
(WW) PSB(0): Bad V_BIOS checksum
(II) PSB(0): Primary V_BIOS segment is: 0xc000
(II) PSB(0): VESA BIOS detected
(II) PSB(0): VESA VBE Version 3.0
(II) PSB(0): VESA VBE Total Mem: 8000 kB
(II) PSB(0): VESA VBE OEM: Intel(r)Poulsbo Graphics Chip Accelerated VGA BIOS
(II) PSB(0): VESA VBE OEM Software Rev: 1.0
(II) PSB(0): VESA VBE OEM Vendor: Intel Corporation
(II) PSB(0): VESA VBE OEM Product: Intel(r)Poulsbo Graphics Controller
(II) PSB(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) PSB(0): Found panel mode in BIOS VBT tables:
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 (50.1 kHz)
(II) PSB(0): BLC Data in BIOS VBT tables: datasize=0 paneltype=13                      type=0x00 pol=0x01 freq=0x00c8 minlevel=0x00                         i2caddr=0x58 cmd=0xaa 
(WW) PSB(0): BIOS panel mode data doesn't match probed data, continuing with probed.
(II) PSB(0): BIOS mode:
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 (50.1 kHz)
(II) PSB(0): probed mode:
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Lid state timer is enabled!
(II) Debug: i830_psbPtrAddToList
(II) PSB(0): Debug: i830_psbSDVOInit
(II) PSB(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) PSB(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) PSB(0): I2C bus "SDVOB DDC Bus" initialized.
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: sdvo_get_capabilities, caps.output_flags=3e
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Output SDVO-1 has no monitor section
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 10 00                      (i830_SDVO_CMD_SET_TARGET_INPUT)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 1D                         (i830_SDVO_CMD_GET_INPUT_PIXEL_CLOCK_RANGE)
(II) PSB(0): SDVO: R: C4 09 74 40             (Success)
(II) PSB(0): SDVO device VID/DID: 02:42.02, clock range 25.0MHz - 165.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
(II) Debug: i830_psbPtrAddToList
(II) Debug: i830_psbOutputCompat
(II) PSB(0): Debug: i830_psbOutputTypesToIndex
(II) PSB(0): Debug: Output crtc mask is 0x00000002, compat mask is 0x00000001
(II) PSB(0): Debug: i830_psbOutputTypesToIndex
(II) PSB(0): Debug: Output crtc mask is 0x00000001, compat mask is 0x00000002
(II) PSB(0): Debug: xxi830_psbInitCrtcs
(II) PSB(0): Debug: xxi830_psbCrtcInit
(II) PSB(0): Debug: xxi830_psbCrtcInit
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 0 as available for all screens.
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 1 as available for all screens.
(II) PSB(0): Debug: psbDeviceFinishInit
(II) Debug: Really running psbDeviceFinishInit
(++) PSB(0): i830_psbSaveHWState
(II) PSB(0): Debug: xxi830_psbOutputSave
(II) PSB(0): Debug: psbLVDSSave
(II) PSB(0): Debug: xxi830_sdvo_save
(II) PSB(0): Debug: SDVO: W: 20                         (i830_SDVO_CMD_GET_CLOCK_RATE_MULT)
(II) PSB(0): SDVO: R: 01                      (Success)
(II) PSB(0): Current clock rate multiplier: 1
(II) PSB(0): Debug: SDVO: W: 04                         (i830_SDVO_CMD_GET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug:  --save_active_outputs is 0
(II) PSB(0): Debug: SDVO: W: 10 00                      (i830_SDVO_CMD_SET_TARGET_INPUT)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 12                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 13                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART2)
(II) PSB(0): SDVO: R: 00 00 00 00 16 20 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 11 00 00                   (i830_SDVO_CMD_SET_TARGET_OUTPUT)
(II) PSB(0): SDVO: R:                         (Invalid arg)
(II) PSB(0): Debug: SDVO: W: 18                         (i830_SDVO_CMD_GET_OUTPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Target not specified)
(II) PSB(0): Debug: SDVO: W: 06 08 48 9E AE             (i830_SDVO_CMD_GET_IN_OUT_MAP)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 0.
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 1.
(==) PSB(0): Shadow framebuffer disabled
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) PSB(0): Acceleration enabled
(==) PSB(0): [EXA] Allocate 32768 kiB for EXA pixmap cache.
(==) PSB(0): [EXA] Allocate 4 kiB for scratch memory.
(II) Debug: i830_psbOutputAssignToScreen
(II) PSB(0): Output "SDVO-1" is assigned to this screen.
(II) Debug: i830_psbOutputAssignToScreen
(II) PSB(0): Output "LVDS0" is assigned to this screen.
(II) PSB(0): Searching for matching Poulsbo mode(s):
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Output LVDS0 connected
(II) PSB(0): Output SDVO-1 disconnected
(II) PSB(0): Output LVDS0 using initial mode 1280x800
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 0 as available for all screens.
(II) Debug: i830_psbOutputDisableCrtcForOtherScreens
(II) Debug: Grabbing crtc 1 for screen 0
(==) PSB(0): Using gamma correction (1.0, 1.0, 1.0)
(**) PSB(0): Display dimensions: (260, 160) mm
(**) PSB(0): DPI set to (125, 203)
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd8380000 - 0xd839ffff (0x20000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] 0	0	0xd8100000 - 0xd817ffff (0x80000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd8000000 - 0xd8003fff (0x4000) MX[B]
	[8] -1	0	0xd8400000 - 0xd840ffff (0x10000) MX[B]
	[9] -1	0	0xd8410000 - 0xd8410fff (0x1000) MX[B]
	[10] -1	0	0xd83a4000 - 0xd83a43ff (0x400) MX[B]
	[11] -1	0	0xd83a0000 - 0xd83a3fff (0x4000) MX[B]
	[12] -1	0	0xd8380000 - 0xd839ffff (0x20000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xd8100000 - 0xd817ffff (0x80000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] 0	0	0x00001800 - 0x00001807 (0x8) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[22] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[23] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[24] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[25] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) PSB(0): Debug: psbScreenInit
(II) PSB(0): Debug: psbDRIScreenInit
(II) PSB(0): Debug: SAREA size is 8192
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:0:2:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) PSB(0): [drm] Using the DRM lock SAREA also for drawables.
(II) PSB(0): [drm] framebuffer handle = 0x3f800000
(II) PSB(0): [drm] added 1 reserved context for kernel
(II) PSB(0): X context handle = 0x1
(II) PSB(0): [drm] Allocated device DRM context 2.
(II) [drm] Irq handler installed for IRQ 17.
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: Shadow
(II) PSB(0): Debug: Calling fbScreenInit.
(II) PSB(0): Debug: Fix up visuals.
(II) PSB(0): Debug: fbPictureInitInit
(II) EXA(0): Offscreen pixmap area of 33554432 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II) PSB(0): Debug: Backing store
(==) PSB(0): Backing store disabled
(==) PSB(0): Silken mouse enabled
(II) PSB(0): DPMS enabled
(WW) PSB(0): Option "UseFBDev" is not used
(II) PSB(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) PSB(0): Debug: psbLVDSCreateResources
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): Debug: psbLVDSSetProperty  panelfitting 0
(II) PSB(0): Debug: SDVO: W: 27                         (i830_SDVO_CMD_GET_SUPPORTED_TV_FORMATS)
(II) PSB(0): SDVO: R: FF FF FF FF FF 1F       (Success)
(II) PSB(0): Debug: SDVO: W: 84                         (II) PSB(0): SDVO: R: FA DF                   (Success)
(II) PSB(0): Debug: SDVO: W: 61                         (II) PSB(0): SDVO: R: 00 00 00 00             (Target not specified)
(II) PSB(0): Debug: SDVO: W: 67                         (II) PSB(0): SDVO: R: 00 00 00 00             (Target not specified)
(II) PSB(0): Debug: TVStandard is 1, TVStdBitmask is 1
(II) PSB(0): Debug: i830_sdvo_set_tvoutputs_formats, format is NTSC_M
(II) PSB(0): Debug: SDVO: W: 5A 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_hue, hue is 0
(II) PSB(0): Debug: SDVO: W: 5D 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_brightness, brightness is 0
(II) PSB(0): Debug: SDVO: W: 60 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_contrast, contrast is 0
(II) PSB(0): Debug: SDVO: W: 63 00 00                   (II) PSB(0): SDVO: R:                         (Target not specified)
(II) PSB(0): Debug: i830_sdvo_set_horzontal_overscan, x overscan is 0
(II) PSB(0): Debug: i830_sdvo_set_vertical_overscan, y overscan is 0, status is 16
(II) PSB(0): [DRI] installation complete
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: Buffer 0 rotation 0 handle 0xb9650604
Xpsb - 2.2.0.32L.0020
(II) PSB(0): [Xpsb] Started kernel request thread.
(II) PSB(0): Xpsb extension for 3D engine acceleration enabled.
(II) PSB(0): Set up textured video
(II) PSB(0): Xv video acceleration enabled.
(II) PSB(0): Initializing HW Cursor.
(II) PSB(0): Debug: psbEnterVT 1
(EE) PSB(0): has_fbdev is true
(++) PSB(0): i830_psbSaveHWState
(II) PSB(0): Debug: xxi830_psbOutputSave
(II) PSB(0): Debug: psbLVDSSave
(II) PSB(0): Debug: xxi830_sdvo_save
(II) PSB(0): Debug: SDVO: W: 20                         (i830_SDVO_CMD_GET_CLOCK_RATE_MULT)
(II) PSB(0): SDVO: R: 01                      (Success)
(II) PSB(0): Current clock rate multiplier: 1
(II) PSB(0): Debug: SDVO: W: 04                         (i830_SDVO_CMD_GET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug:  --save_active_outputs is 0
(II) PSB(0): Debug: SDVO: W: 10 00                      (i830_SDVO_CMD_SET_TARGET_INPUT)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 12                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 13                         (i830_SDVO_CMD_GET_INPUT_TIMINGS_PART2)
(II) PSB(0): SDVO: R: 00 00 00 00 16 20 00 00 (Success)
(II) PSB(0): Debug: SDVO: W: 11 00 00                   (i830_SDVO_CMD_SET_TARGET_OUTPUT)
(II) PSB(0): SDVO: R:                         (Invalid arg)
(II) PSB(0): Debug: SDVO: W: 18                         (i830_SDVO_CMD_GET_OUTPUT_TIMINGS_PART1)
(II) PSB(0): SDVO: R: 00 00 00 00 00 00 00 00 (Target not specified)
(II) PSB(0): Debug: SDVO: W: 06 08 C8 9E AE             (i830_SDVO_CMD_GET_IN_OUT_MAP)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 0.
(II) PSB(0): Debug: xxi830_psbCrtcSave pipe 1.
(II) PSB(0): Debug: psbSetVGAOff
(II) PSB(0): Debug: i830_psbCrtcSetupCursors
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 0 ARGB addresses 0x3fe40000, 0x00000000
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 1 ARGB addresses 0x3fe45000, 0x00000000
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0xc0000008
(II) Debug: Pipe B PLL 0xd8027200
(II) Debug: Pipe B Enabled 0x80000000
(II) PSB(0): Debug: BLCType=0 Backlightg level = 0
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 0
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): Debug: xxi830_psbCrtcLock
(II) PSB(0): Debug: psbLVDSModeFixup
(II) Debug: i830_psbOutputEnableCrtcForAllScreens
(II) Debug: Marking crtc 0 as available for all screens.
(II) Debug: i830_psbOutputDisableCrtcForOtherScreens
(II) Debug: Grabbing crtc 1 for screen 0
(II) PSB(0): Debug: xxi830_psbCrtcModeFixup, NULL
(II) PSB(0): Debug: i830_psbOutputPrepare, output->dpms,off
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0x08000001
(II) Debug: Pipe B PLL 0x58027200
(II) Debug: Pipe B Enabled 0x00000000
(II) PSB(0): Debug: BLCType=0 Backlightg level = 0
(II) PSB(0): Debug: xxi830_psbCrtcPrepare
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): Debug: xxi830_psbCrtcModeSet
(II) PSB(0): Debug: i830_psbCrtcModeSet
(II) PSB(0): Debug: chosen: dotclock 71314 vco 1996800 ((m 104, m1 17, m2 7), n 3, (p 28, p1 2, p2 14))
(II) PSB(0): Debug: clock regs: 0xd8027200, 0x00031107
(II) PSB(0): Debug: psbPipeSetBase
(II) PSB(0): Debug: psbLVDSModeSet
(II) PSB(0): Debug: xxi830_psbCrtcCommit, crtc->dpms
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS On / Sb /SS 
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210f30 
(II) PSB(0): Debug: i830_psbOutputCommi, output->dpms, ont
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0x48000001
(II) Debug: Pipe B PLL 0xd8027200
(II) Debug: Pipe B Enabled 0x80000000
(II) Debug: psbLVDSSetPanelPower: lidState= 0
(II) PSB(0): Debug: BLCType=0 Backlightg level = 100
(II) PSB(0): Debug: xxi830_psbCrtcUnlock
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 0
(II) PSB(0): Debug: Crtc DPMS Off
(II) PSB(0): xxi830_Output configuration:
(II) PSB(0):   Pipe A is off
(II) PSB(0):   Display plane A is now disabled and connected to pipe A.
(II) PSB(0):   Pipe B is on
(II) PSB(0):   Display plane B is now enabled and connected to pipe B.
(II) PSB(0):   Output LVDS0 is connected to pipe B
(II) PSB(0):   Output SDVO-1 is connected to pipe none
(II) PSB(0): Debug: psbAdjustFrame
(II) PSB(0): Debug: psbPipeSetBase
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:0:2:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/psb_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) PSB(0): Setting screen physical size to 261 x 163
(II) PSB(0): Debug: psbXf86CrtcResize 1280 800
(II) PSB(0): Debug: i830_psbCrtcSaveCursors
(II) PSB(0): Debug: i830_psbCrtcHWCursorSave
(II) PSB(0): Debug: i830_psbCrtcHWCursorSave
(II) Debug: psbScanoutDestroy
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: PsbDRIUpdateScanouts
(II) PSB(0): Debug: Buffer 0 rotation 0 handle 0x885ee004
(II) PSB(0): Debug: i830_psbCrtcSetupCursors
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 0 ARGB addresses 0x3fbe8000, 0x00000000
(II) PSB(0): Debug: i830_psbCrtcHWCursorAlloc
(II) PSB(0): Debug: Cursor 1 ARGB addresses 0x3fbed000, 0x00000000
(II) PSB(0): Debug: psbAdjustFrame
(II) PSB(0): Debug: psbPipeSetBase
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "es"
(**) Generic Keyboard: XkbLayout: "es"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(--) Synaptics Touchpad touchpad found
(II) PSB(0): Debug: psbSaveScreen
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS On / Sb /SS 
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210f30 
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0xc0000008
(II) Debug: Pipe B PLL 0xd8027200
(II) Debug: Pipe B Enabled 0x80000000
(II) Debug: psbLVDSSetPanelPower: lidState= 0
(II) PSB(0): Debug: BLCType=0 Backlightg level = 100
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbLVDSDetect 1
(II) PSB(0): Debug: psbGetLidStatus lidState= 0
(II) PSB(0): Debug: psbLVDSGetModes
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Printing DDC gathered Modelines:
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Modeline "1280x800"x0.0   70.98  1280 1328 1360 1416  800 803 809 835 +hsync -vsync (50.1 kHz)
(II) PSB(0): Debug: psbLVDSSetProperty
(II) PSB(0): EDID vendor "SEC", prod id 12631
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: psbLVDSModeValid
(II) PSB(0): Debug: xxi830_sdvo_detect 1
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): SDVO: R: 00 00                   (Not supported)
(II) PSB(0): Debug: SDVO: W: 0D 01 00                   (i830_SDVO_CMD_SET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: SDVO: W: 0E                         (i830_SDVO_CMD_GET_ACTIVE_HOT_PLUG)
(II) PSB(0): Debug: xxi830_sdvo_dpms 0, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 03                         (i830_SDVO_CMD_GET_TRAINED_INPUTS)
(II) PSB(0): SDVO: R: 00                      (Success)
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: SDVO: W: 02                         (i830_SDVO_CMD_GET_DEVICE_CAPS)
(II) PSB(0): SDVO: R: 02 42 02 01 01 3D 3E 00 (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: SDVO: W: 0B                         (i830_SDVO_CMD_GET_ATTACHED_DISPLAYS)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Pending)
(II) PSB(0): SDVO: R: 00 00                   (Success)
(II) PSB(0): Debug: xxi830_sdvo_dpms 3, active_outputs=0
(II) PSB(0): Debug: SDVO: W: 05 00 00                   (i830_SDVO_CMD_SET_ACTIVE_OUTPUTS)
(II) PSB(0): SDVO: R:                         (Success)
(II) PSB(0): Debug: psbDisplayPowerManagementSet
(II) PSB(0): Debug: xxi830_psbCrtcDpms pipe 1
(II) PSB(0): Debug: Crtc DPMS On / Sb /SS 
(II) PSB(0): Debug: xxi830_psbCrtcLoadLut 0x8210f30 
(II) PSB(0): Debug: psbLVDSDPMS
(II) Debug: PanelPower Status = 0xc0000008
(II) Debug: Pipe B PLL 0xd8027200
(II) Debug: Pipe B Enabled 0x80000000
(II) Debug: psbLVDSSetPanelPower: lidState= 0
(II) PSB(0): Debug: BLCType=0 Backlightg level = 100
```

If you need something more, please tell me. Thanks again!

---

### Post by kylecronan on 2009-04-19
I think this is what you need to do: in your sources.list, for the hardy-dell-mini-proposed repo you should have "main restricted universe" instead of just "main".  Then make sure you also have the updates to the libdrm2, libva1, psb-video and xorg-modules-xpsb packages.

---

### Post by theozzlives on 2009-04-19
> **matthiasak said:**
> I have a belmont .img file now and I've succeeded in putting it on my USB drive, however now I have a problem booting it on my Dell Mini 10... It is loading the file ubnkern (20KB)and then tries to load ubninit (1.35 GB) and can't because i dont have that much memory. Is there some special option should add in the boot option to allow it to page a temporary area of sorts...

I'm so close to just having Ubuntu on my system finally #-o Just need it to boot finally!

I wouldn't call it close if you're not bootin?:P

---

### Post by matthiasak on 2009-04-19
Well, in the string of attempts to boot something it was 'close' haha, getting somethign with working drivers and everything and then knowing I couldn't load the RAMDisk file.

It turns out I could mount the ubninit ramdisk file as a loopback device and extract the files again to my SD card.

Now installed with the Dell Belmont Hardy. Sadly I could never get desktop effects running right off or when I installed the updates from the Dell repos in the original sources.list, but everything else works amazingly well :)

---

### Post by dimeified on 2009-04-20
I have removed the lpia install in favor of the i386 daily jaunty build. Wireless works out of the box. Actually, everything does except the display is still 1024x768. I dont mind the vesa frame buffer, its fine for what i do until the accelerated graphics driver is developed.

NetBSD guys seem to have luck running on the mini 12 with a program called 855resolution that adds 1280x800 to the vesa frame buffer table at boot and allows that resolution to be utilized by x. Is there a similar utility for ubuntu?

see [http://mydellmini.com/forum/xorg-conf-for-mini-12-solved--t5664.html](http://mydellmini.com/forum/xorg-conf-for-mini-12-solved--t5664.html)

actually this might answer it [http://ubuntuforums.org/showthread.php?t=114067](http://ubuntuforums.org/showthread.php?t=114067)

---

### Post by teatimest on 2009-04-20
Hi madman_sp,

I have same problem with wifi with newer kernel. Did you make it work eventually?

teatimest

>ok, then I rebooted and ran the new kernel. First Wifi didn`t work and ... incredible ... I HAD DRI!!!! :) Flash on firefox worked good but when I tried to run a video with VLC or Totem the X crashed.> [QUOTE][/QUOTE]

---

### Post by matthiasak on 2009-04-20
> **dimeified said:**
> I have removed the lpia install in favor of the i386 daily jaunty build. Wireless works out of the box. Actually, everything does except the display is still 1024x768. I dont mind the vesa frame buffer, its fine for what i do until the accelerated graphics driver is developed.

NetBSD guys seem to have luck running on the mini 12 with a program called 855resolution that adds 1280x800 to the vesa frame buffer table at boot and allows that resolution to be utilized by x. Is there a similar utility for ubuntu?

see [http://mydellmini.com/forum/xorg-conf-for-mini-12-solved--t5664.html](http://mydellmini.com/forum/xorg-conf-for-mini-12-solved--t5664.html)

actually this might answer it [http://ubuntuforums.org/showthread.php?t=114067](http://ubuntuforums.org/showthread.php?t=114067)
As far as 855resolution ... you could instead just add the mode to xrandr

```

matthiasak@matthiasak:~$ cvt 1280 800 60
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
matthiasak@matthiasak:~$ xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
matthiasak@matthiasak:~$ xrandr --addmode LVDS "1280x800_60.00"

```

Then you can go to the Screen Resolution dialog and change it to 1280x800

---

### Post by jorjoso on 2009-04-20
hii i have a dell mini 12 with ubuntu

I found these repositories

#HP MINI  REPOS-------------------
#deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy main universe multiverse restricted

#deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy main universe multiverse #restricted



#deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-updates main universe multiverse #restricted

#deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-updates main universe #multiverse restricted



#deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-security main universe multiverse #restricted

#deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-security main universe #multiverse restricted



#deb [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-hpmini main universe multiverse #restricted

#deb-src [http://hpmini.archive.canonical.com/mie/](http://hpmini.archive.canonical.com/mie/) hardy-hpmini main universe #multiverse restricted

#-----------------------------------

have the most current version of lpia kernel gnome and firefox

but not if I should update????

be sure to update?
I have commented these lines for now

---

### Post by fitzkarraldo on 2009-04-21
> **jorjoso said:**
> hii i have a dell mini 12 with ubuntu

have the most current version of lpia kernel gnome and firefox

but not if I should update????

be sure to update?
I have commented these lines for now

Hi jorjoso,
I used that repositories for a while and I verified that their software is quite more updated than the software available in dell-canonical repositories but, according to me, nothing so important.
Moreover, I think that those repositories broke me some gnome settings...

---

### Post by HarryKane on 2009-04-21
Hi,

I have installed the Jaunty Daily live-image like it was said on [https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR), but I have some problems with the graphics (very slow). I found in the [mydellmini-forum]("http://mydellmini.com/forum/getting-ubuntu-8-0-4-to-work-on-the-mini-12-t2606.html") a how to and a [link (Post #94)]("http://ubuntuforums.org/showpost.php?p=6512181&postcount=94") to solve the problem. Unfortunatly this was for the 8.04 version.

Can someone explain to me how I get this to work with the 9.04? 

Thanks,
HarryKane

---

### Post by dimeified on 2009-04-21
The kernel and xorg in jaunty is not compatible with the driver in hardy unr. This is why i will be downgrading back to hardy unr.

---

### Post by HarryKane on 2009-04-21
Can you/someone explain, how to downgrade to hardy? 

I tried the installation of hardy unr some month ago and my whole system was deleted. However I need a dual boot system with WinXP.

---

### Post by kylecronan on 2009-04-21
> **HarryKane said:**
> Can you/someone explain, how to downgrade to hardy? 

I tried the installation of hardy unr some month ago and my whole system was deleted. However I need a dual boot system with WinXP.

Post #243.

---

### Post by kylecronan on 2009-04-21
Hey everyone, I've created a Wiki and added a message back at the beginning of this thread.  Feel free to add to the wiki.

[http://gma500.wiki-site.com](http://gma500.wiki-site.com)

---

### Post by marduk667 on 2009-04-22
i just updated the psb driver and now i get on glxinfo:

> ERROR!  sizeof(PsbDRIRec) does not match passed size from device driver
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

any idea?

Edit: i had to install the other psb packages from the dell repository, now it works :)

---

### Post by marduk667 on 2009-04-22
omg with the new driver my mini12 locks up when i use the webcam, anyone else with this problem? it happens in cheese and skype...

also i have some graphic errors while browsing with firefox

---

### Post by matthiasak on 2009-04-22
None here... are you using 0.27? I'm pretty sure I have the latest, and I have both the dell and ubuntu nbr repos in my sources.list

anyone gotten compiz working?

```

matthiasak@matthiasak:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) GMA500 20081031 - 2.3.2.32L.0038 x86/MMX/SSE2
OpenGL version string: 2.0 Mesa 7.0.3
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_framebuffer_object, GL_EXT_fog_coord, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_separate_stencil, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x55 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

I have OpenGL Acceleration but yet I get a message about no glx accel:

```

matthiasak@matthiasak:~$ compiz
Checking for Xgl: not present. 
FATAL: Module battery not found.
Detected PCI ID for VGA: 00:02.0 0300: 8086:8108 (rev 07) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x576) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
/home/matthiasak/.themes/Dust/gtk-2.0/gtkrc:698: error: unexpected identifier `highlight_shade', expected character `}'

```

---

### Post by bethenco on 2009-04-22
> **marduk667 said:**
> 
Edit: i had to install the other psb packages from the dell repository, now it works :)

Hey marduk667, I get the same error from glxinfo.

Can I get some more specific info about how you solved it? What do you have in /etc/apt/sources.list? Which other psb packages did you install?

Here's some info on my situation:

[LIST]
[*] Got a Dell Mini 12 with ubuntu preinstalled.
[/LIST]
  
[LIST]
[*] Followed the instructions in post 94: [http://ubuntuforums.org/showpost.php?p=6512181]("http://ubuntuforums.org/showpost.php?p=6512181&postcount=94")
[/LIST]

[LIST]
[*]Everything in those instructions seemed to work: the firmware shows up appropriately in output of dmesg and my Xorg.0.log has the line ```
(II) PSB(0): Xpsb extension for 3D engine acceleration enabled.
```
[/LIST]
But when I run glxinfo, I get ```
ERROR!  sizeof(PsbDRIRec) does not match passed size from device driver
```This seems to be the exact same situation described by Chris B in this post: [http://ubuntuforums.org/showpost.php?p=6810886](http://ubuntuforums.org/showpost.php?p=6810886)

Anyone have any ideas?

---

### Post by marduk667 on 2009-04-22
please check in synaptics if you have all psb drivers installed, there are several:

> libgl1-mesa-dri-psb - MESA 3D DRi driver for Poulsbo
xserver-xorg-video-psb - 2D graphics driver for Poulsbo
psb-video - Video decode driver for Poulsbo
xorg-modules-xpsb - 3D graphics daemon for Poulsbo


still the problem with my webcam, but i have a unr installed, not the belmont image...

My sources.list:

> deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix main universe multiverse restricted
deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix main universe multiverse restricted

deb [http://ppa.launchpad.net/ubuntu-mobile/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ubuntu) hardy main

deb [http://ppa.launchpad.net/network-manager/ppa/ubuntu](http://ppa.launchpad.net/network-manager/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/network-manager/ppa/ubuntu](http://ppa.launchpad.net/network-manager/ppa/ubuntu) hardy main

deb [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/blueman/ppa/ubuntu](http://ppa.launchpad.net/blueman/ppa/ubuntu) hardy main

deb [http://ppa.launchpad.net/repro-moblin-image/ubuntu](http://ppa.launchpad.net/repro-moblin-image/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/repro-moblin-image/ubuntu](http://ppa.launchpad.net/repro-moblin-image/ubuntu) hardy main

#deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-proposed restricted main universe multiverse

deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix-proposed main universe multiverse restricted

deb [http://netbook-remix.archive.canonical.com/ubuntu](http://netbook-remix.archive.canonical.com/ubuntu) hardy-dell-mini-proposed main restricted universe


---

### Post by matthiasak on 2009-04-22
why are you using the hardy repos? do you think that might be the point of contention?

---

### Post by bethenco on 2009-04-22
> **marduk667 said:**
> please check in synaptics if you have all psb drivers installed, there are several:

Awesome, thanks! That fixed it for me.

Just to be clear, I don't have the belmont image installed either. I overwrote it using the Hardy UNR installer as explained in post 94.

I used cheese to try the webcam, but I couldn't reproduce any lockups. I'm guessing this is due to my version of xserver-xorg-video-psb or one of the other packages for which I'm using an older version (see bottom of this post).

Here a few more details on what I did for anyone else who needs them:

First I followed all the directions in post 94.

Next, I added the line 
```
deb [http://netbook-remix.archive.canonical.com/ubuntu](http://netbook-remix.archive.canonical.com/ubuntu) hardy-dell-mini-proposed main restricted universe
```to my /etc/apt/sources.list, which now looks like
```

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted
deb-src http://netbook-remix.archive.canonical.com/ubuntu/ hardy-netbook-remix main universe multiverse restricted

deb http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ubuntu hardy main

deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-dell-mini-proposed main restricted universe

```Next I used synaptic to install libgl1-mesa-dri-psb, psb-video, and xorg-modules-xpsb. These packages are only made available by the "hardy-dell-mini-proposed" line, so I hadn't installed them previously.

I have NOT, as yet, upgraded any other packages to the latest version available in hardy-dell-mini-proposed. In particular, I'm using xserver-xorg-video-psb version "0.20.0+repack-0ubuntu1~804um1~dooz1", rather than "0.27.0+repack-0netbook2". The packages libdrm2, linux-image-lpia, linux-lpia, linux-restricted-modules-common, and linux-restricted-modules-lpia also had new versions that I didn't install.

---

### Post by kylecronan on 2009-04-22
I just wanted to mention that since I posted that link to the hardy-dell-mini-proposed repo I have realized that the same packages are also in regular old hardy-dell-mini on that server.

Also, dell-mini.archive.canonical.com and netbook-remix.archive.canonical.com are the same server.

---

### Post by pistoncito on 2009-04-23
> **marduk667 said:**
> please check in synaptics if you have all psb drivers installed, there are several:



still the problem with my webcam, but i have a unr installed, not the belmont image...

My sources.list:

I don't have problems with the webcam. This are my psb packages installed:

ii  libgl1-mesa-dri-psb                        0.24+repack+0038.1-0netbook1                         MESA 3D DRi driver for Poulsbo
ii  psb-video                                  0.28+0038-0netbook1                                  Video decode driver for Poulsbo
ii  xorg-modules-xpsb                          0.16+0038-0netbook1                                  3D graphics daemon for Poulsbo
ii  xserver-xorg-video-psb                     0.27.0+repack-0netbook2                              2D graphics driver for Poulsbo

My Mini 12 was originally with Belmont, but i use this forum to modified it to UNR.

---

### Post by krowland44 on 2009-04-24
I just purchased a Mini 12 w/XP Home.  Since I had a mini 9 that worked well w/8.04, I decided to put it on my mini 12, however I cannot get it to load either from within Windows or from booting off the 8.04 and/or8.10 CD/DVD.

Can anyone help, please???

Does anyone know if the Mini 12 supports Linux??

I am pretty new at Linux, so go easy on me.

---

### Post by tyroeternal on 2009-04-24
The mini 12 will run linux and is sold preloaded with Ubuntu, just like the mini 9.  This is not to say that it will be easy to put it on your system.  At this point I honestly think that as a new linux user it would be unwise to attempt to install it as there are massive headaches with the mini 12 still.

If you would really like to try it you should read through this whole thread and see how others have done it.  Here is a post in this thread that can may you started: [http://ubuntuforums.org/showthread.php?p=6642302](http://ubuntuforums.org/showthread.php?p=6642302)

---

### Post by krowland44 on 2009-04-24
Thank you.

---

### Post by HarryKane on 2009-04-24
Can someone explain in more detail what a dumb linux noob, like me, has to do to install 8.04 beside XP? I tried to follow what was written in #243 but after mounting the boot and root images I couldn't make this 'mount -o bind /dev /mnt/dev' and I don't know what I have to do with chroot ... 
Probably I already made some mistakes while mounting unr-1.0.1.img, so please begin from scratch.

Thanks for any advice!
Greetings,
HarryKane

PS: I already have installed XP and some days ago I tried 9.04 (still installed). I used the live-System from the USB-thumb.

---

### Post by kylecronan on 2009-04-24
For the chroot: chroot /mnt /bin/bash (this makes /mnt your new / and runs a bash shell within the new root)

Did you do all the steps up to the bind mount for /dev?  Were you able to mount rootfs.img and bootfs.img somewhere?  When you copy the files from these be sure to use the "-a" argument to cp, so that file attributes are preserved.  For example, if rootfs.img is at /mnt2 and your new root filesystem is at /mnt: "cp -a /mnt2/* /mnt"  Did you get any error messages in the steps you did so far?

I'll try to help you figure this out.  But if you can't get this way to work you might have to reinstall Windows.  Ie, run the regular UNR installer, use gparted to resize your filesystem and make room for Windows, then do your XP install.

---

### Post by teatimest on 2009-04-24
Jaunty UNR is out, right? Does it work?

---

### Post by danboid on 2009-04-26
Finally got round to experimenting with the HDMI out on the Mini 10 a bit more but I've not managed any better than 720x576 @ 50Hz with no audio

[http://mydellmini.com/forum/hdmi-output-on-mini-10-t6961.html](http://mydellmini.com/forum/hdmi-output-on-mini-10-t6961.html)

If anyone knows any better, please let me know. What about under Windows? Can XP output higher than 720x576?

---

### Post by matthiasak on 2009-04-26
XP can, I have used it extensively on the Mini 10. I was outputting HDMI at 1080p. ;)

---

### Post by kylecronan on 2009-04-26
Make sure you have the latest version of the various video driver packages.  The changelog mentioned something about updates to the HDMI support.

---

### Post by tentwelveeight on 2009-04-26
> **teatimest said:**
> Jaunty UNR is out, right? Does it work?

Installed jaunty unr last night for my wife. She says it is snappier than hardy unr. The new notification system is nice.

Everything seems to work out of the box except the GMA 500 display driver (of course). This limits the res to 1024 by 768 and renders the unr desktop unusable. A simple switch to the standard GNOME desktop speeds things up considerably though.

Volume, brightness, suspend, battery, page up/down, and printscreen Fn keys work. Wireless on/off Fn key does not. Couldn't check the VGA-out Fn key but assuming it doesn't work sans the correct GMA 500 driver.

Hibernates and suspends fine. Suspends on lid closing fine. Takes nearly 60 sec coming out of either to reconnect to wireless tho.

Only problem I had was this annoying message popping up after autologin: > The application 'NetworkManager Applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked. 

I detailed the fix for this problem on this post tho:
[http://ubuntuforums.org/showthread.php?t=1138099](http://ubuntuforums.org/showthread.php?t=1138099)

(Basically just go into wireless settings and tic the "available to all users" box)

Cheers -joe

---

### Post by ziocecco83 on 2009-04-27
I have installed UNR hardy on my Dell Mini 12 follow your guide.
3D,wifi, flash videos and audio playing(with amarok and vlc) work well, the only problem I have is when I try to play video files with any player or try to use video with cheese or skype that causes chrash and need to reboot manually the system.
Anyone could help me?

---

### Post by teatimest on 2009-04-27
Thanks for your reply, tentwelveeight!

I see. If that is the case, I should stick with Hardy for now.

> **tentwelveeight said:**
> Installed jaunty unr last night for my wife. She says it is snappier than hardy unr. The new notification system is nice.

Everything seems to work out of the box except the GMA 500 display driver (of course). This limits the res to 1024 by 768 and renders the unr desktop unusable. A simple switch to the standard GNOME desktop speeds things up considerably though.

Volume, brightness, suspend, battery, page up/down, and printscreen Fn keys work. Wireless on/off Fn key does not. Couldn't check the VGA-out Fn key but assuming it doesn't work sans the correct GMA 500 driver.

Hibernates and suspends fine. Suspends on lid closing fine. Takes nearly 60 sec coming out of either to reconnect to wireless tho.

Only problem I had was this annoying message popping up after autologin:  

I detailed the fix for this problem on this post tho:
[http://ubuntuforums.org/showthread.php?t=1138099](http://ubuntuforums.org/showthread.php?t=1138099)

(Basically just go into wireless settings and tic the "available to all users" box)

Cheers -joe

---

### Post by danboid on 2009-04-28
Matt/ Kyle:

So obviously this is a flaw with the linux drivers. My install is 100% up to date and it was when I last tried HD out. I've just checked now and there have been no updates since I last tried this. I'm using the same sources.list as mattiasak atm.

Kyle:

Good to see your wiki, that is very helpful but I was secretly hoping you were going to create a wiki for Mini 12/10 with general tips for people running Ubuntu on a poulsbo machine- not just setting up the display.

Everybody!:

2 things I've so far failed to sort out are:

How do I get my normal GNOME desktop back permanently? I've uninstalled the dell-launcher and removed it from the session, but after I reboot I still can't see my desktop and have to use the Dell desktop toggle. I want rid so bad, so long!

Is hibernate supported under belmont? I removed the Dell restore partition and replaced it with a swap partition, 'formatted' it as swap (mkswap) ran swapon, added a resume=/dev/sda3 or whatever to my kernel loader and added it to my fstab. I then enabled hibernate support in gconf-editor but I still don't get 'Hibernate' option!?

Thank Yooooo!

---

### Post by stupidfish on 2009-04-28
Hi all,

I have attempted to read through this entire post - but it is sooo long. I have just recently Installed UNR Jaunty onto my girlfriend's dell mini 12. After a bit of fiddling, I have got it working decently. Changed it to the standard desktop so that it was workable. Only issue I can see is with the graphics driver. Can only get it to run at 1024.

Is there anything I can do to make the graphics driver run at it's best, keeping in mind the GMA 500 driver is still not supported. Or is straight out of the box the best bet?

Also, are there any ideas as to when this might be supported? Are previous versions of UNR or alternative distros any better? Is it just a wait and see?

Thanks in advance.

---

### Post by kylecronan on 2009-04-28
Post #420 has a way to get correct resolution with the vesa driver.

---

### Post by danboid on 2009-04-28
Hibernate just magically started to work in that the icon wasn't in my log out options before but now it is. I thought I'd met all the requirements but I haven't figured out why the hibernate option wasn't appearing after making those adjustments and now it is. :confused:

I've also got my GNOME desktop to survive reboot- what I didn't do before was select 'Automatically Remember Running Applications when logging out' under the options tab of gnome-session-properties after having uninstalled the dell apps, removed Dell Launcher from the startup apps and having switched to normal desktop mode.

Its 2 steps forwards and one back though as just after having tested hibernation I discover wifi has decided to to stop working. I reboot normally- still no wifi. Neither ifconfig, iwconfig, network-manager or wicd are showing my wlan card now :(

---

### Post by kylecronan on 2009-04-29
Hmm, is the "wl" module loaded (check lsmod)?  Maybe try this: apt-get --reinstall install linux-restricted-modules

---

### Post by danboid on 2009-04-29
Thanks Kyle!

Yes, wl was the module name that was missing from my /etc/modules - after loading that my wlan is available under wicd as eth1, which I'm using with the wext WPA. I then just had to use rcconf to get wicd to autostart on boot.

I'm very happy to report that the wifi does work (under wicd at least) after resuming from hibernate so I feel I've got a proper Linux netbook now thats just waiting for fully working HDMI output support. Maybe its my TV or even my cable that the driver doesn't like? More likely the driver is unfinished or buggy IMO.

EDIT

Note that if anyone else wants to dump network-manager for wicd you need to compile it from source and install/use rcconf to auto-run wicd as I couldn't get wicd to install under belmont from the wicd hardy repo- obviously they don't support lpia too.

---

### Post by marduk667 on 2009-04-29
Hi,

today i made a reinstallation with the dell image, after that i activated the dell proposed and launchpad network-manager repos.

Now i have a weird problem with the network-manager: It gets an adress as i can see in the syslog but network manager doesnt recognize it so it stops after 45 seconds and says that it cant activate it...

Any idea?

---

### Post by matthiasak on 2009-04-29
> **marduk667 said:**
> Hi,

today i made a reinstallation with the dell image, after that i activated the dell proposed and launchpad network-manager repos.

Now i have a weird problem with the network-manager: It gets an adress as i can see in the syslog but network manager doesnt recognize it so it stops after 45 seconds and says that it cant activate it...

Any idea?

Maybe just dont use the launchpad network manager updates, just use the dell mini repos and the hardy UNR repos? Frist try just restarting and disabling networking and then re-enabling it. 

Is it just your wireless or other APs too? We do have a different kernel with the Belmont image, so maybe the network-manager version you installed doesn't like the modules for the lpia kernel?

---

### Post by marduk667 on 2009-04-29
i need the new nm for 3g internet but today the guys from #nm helped me to fix it, i had to disable cdc_ether module by putting it into the blacklist.
now everything seems to work fine :)

---

### Post by AmyRose on 2009-04-30
I just got one of these secondhand. The previous owner didn't like it. I did at first, but the previous owner screwed some things up so I had to reinstall. But she did not provide me with the DVD that came with the computer, so I'm trying to install from the Hardy UNR image (1.0.1), as described in post #94: > **brteag00 said:**
> Et voila, Hardy has working 3D.  Woot!

Here's an explicit rundown of what I did.

Upon booting it, I get this error:

```
checking device /dev/sda for installation source...
checking device /dev/sdb for installation source...
checking device /dev/sdc for installation source...
checking device /dev/sdd for installation source...
Sleeping for 5 seconds
```

This happens repeatedly and gets stuck here. I've verified the MD5sum of the image, so I know it probably downloaded OK. Any idea what's up?

---

### Post by marduk667 on 2009-04-30
Hey, i found the belmont image on Rapidshare, so if anyone needs the link i can share them via PM, don't want to publish them here as i think that this is against forum rules.

---

### Post by jackblow33 on 2009-04-30
Just finished installing with the belmont.img. Have tried to transfer the .img to my usb thumb drive with dd but wasnt able to boot the install but have work with image-writer.
Have update the os and still ok.
Thanks

---

### Post by noravanq on 2009-04-30
Hi there.

Short version of my question: Want XP and Ubuntu dual-boot. Which Ubuntu, 8.04 or 9.04? What goes first, XP or Ubuntu?

Long version:

My sister got a my mini 12 as a gift, and it came with vista installed. But vista is too slow, so we want to replace it and want to have both XP and Ubuntu. Both of us have absolutely no prior experience with Ubuntu, so will need some help.

Reading this thread I understand that I should follow post #94 and install a UNR version of Ubuntu. Which one should I go with, 8.04 or 9.04? We tried various Live USB-s (8.04,8.10,9.04) and 9.04 seemed to work the best since the only issue was the screen. In the others either the GUI didn't load at all (we just got a terminal), or wi-fi didn't work. 

The second question is which way should we do? XP then Ubuntu or Ubuntu then XP?

If I understand correctly, under normal circumstances it's better to do XP then Ubuntu, but reading this thread I understood that UNR versions of Ubuntu want to wipe everything before installing. 

If I do Ubuntu first, then XP will break the boot sector of Ubuntu, and I will have to restore it by doing what's suggested here [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by snowpine on 2009-04-30
Hi noravanq, I recommend installing Windows first, then Ubuntu NBR 9.04 second.

---

### Post by kylecronan on 2009-04-30
noravanq, search the thread for dual boot.  Yes, the UNR installer will wipe your whole disk.  I think it is easier to deal with the XP install overwriting grub than it is to manually install UNR.

If you watch video, you need to use 8.04.  Follow post #94 (actually, that post should be updated to reflect the fact that there is now a better way to get the binary blobs).

---

### Post by greggh on 2009-04-30
> **kylecronan said:**
> (actually, that post should be updated to reflect the fact that there is now a better way to get the binary blobs).

What's the better way to get the binary blobs now?

---

### Post by kylecronan on 2009-04-30
dell-mini.archive.ubuntu.com, hardy-dell-mini repo, libgl1-mesa-dri-psb, psb-video and xorg-modules-xpsb packages.  See also [http://gma500.wiki-site.com](http://gma500.wiki-site.com)

---

### Post by greggh on 2009-04-30
> **kylecronan said:**
> dell-mini.archive.ubuntu.com, hardy-dell-mini repo, libgl1-mesa-dri-psb, psb-video and xorg-modules-xpsb packages.  See also [http://gma500.wiki-site.com](http://gma500.wiki-site.com)

Thanks, but I don't understand how to use this.

For instance from [http://gma500.wiki-site.com/index.php/Main_Page](http://gma500.wiki-site.com/index.php/Main_Page)...

> Kernel DRM module (psb.ko)
Unlike most drivers, this kernel module must be available for the psb Xorg driver to function at all.  The latest version is in the main repo, as part of the linux-ubuntu-modules package (debian/media/drm-poulsbo in the source package).

I can't find that package debian/media/drm-poulsbo listed in [http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/)

Also, do I add this as a repo? Do I somehow load each of these packages/modules separately? This is all too confusing. Starting to regret buying this netbook. But thanks for trying to help anyway.

---

### Post by Xernie on 2009-05-01
> **matthiasak said:**
> As far as 855resolution ... you could instead just add the mode to xrandr

```

matthiasak@matthiasak:~$ cvt 1280 800 60
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
matthiasak@matthiasak:~$ xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
matthiasak@matthiasak:~$ xrandr --addmode LVDS "1280x800_60.00"

```

Then you can go to the Screen Resolution dialog and change it to 1280x800
I tried this and I got a "cannot find output LVDS" error after the addmode command. Do you know what this means?

Also, I'm not sure if I am using the vesa driver. That is, I might still be using intel. I tried dpkg-reconfigure'ing xserver-xorg but it didn't ask me about drivers. I also put the line
```

Driver     "vesa"

```
in the device section of my xorg.conf, but I don't think it worked. How do I know which driver I am using?

---

### Post by stupidfish on 2009-05-02
> **kylecronan said:**
> Post #420 has a way to get correct resolution with the vesa driver.

Just tried that and got the following errors:

 
tiffany@tiffany-laptop:~$ cvt 1280 800 60
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
tiffany@tiffany-laptop:~$ xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
tiffany@tiffany-laptop:~$ xrandr --addmode LVDS "1280x800_60.00"
xrandr: cannot find output "LVDS"

so i tried again and got this:

tiffany@tiffany-laptop:~$ cvt 1280 800 60
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
tiffany@tiffany-laptop:~$ xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 ()
  Serial number of failed request:  18
  Current serial number in output stream:  18
tiffany@tiffany-laptop:~$ xrandr --addmode LVDS "1280x800_60.00"xrandr: cannot find output "LVDS"

I am a linux newbie, so please go easy. Thanks in advance.

---

### Post by pahautane on 2009-05-02
Xernie and stupidfish, if you run:
```
xrandr -q --verbose
```

You should get output that looks something like this:
```
toro@paparoa:~$ xrandr -q --verbose
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 (0x102) normal (normal) 0mm x 0mm
Identifier: 0x101
Timestamp:  795899
Subpixel:   horizontal rgb
Clones:    
CRTC:       0
CRTCs:      0
Panning:    0x0+0+0
Tracking:   0x0+0+0
Border:     0/0/0/0
Transform:  1.000000 0.000000 0.000000
0.000000 1.000000 0.000000
0.000000 0.000000 1.000000
filter: 
1024x768 (0x102)   48.0MHz *current
h: width  1024 start    0 end    0 total 1024 skew    0 clock   46.8KHz
v: height  768 start    0 end    0 total  768           clock   61.0Hz
800x600 (0x103)   29.3MHz
h: width   800 start    0 end    0 total  800 skew    0 clock   36.6KHz
v: height  600 start    0 end    0 total  600           clock   61.0Hzv
```

If you use the value from the Identifier line in place of LVDS then the addmode command should work, eg:
```
xrandr --addmode 0x101 "1280x800_60.00"
```

After you have done that you will find that a 1280x800 option appears in the Display Preferences dialogue. Unfortunately, when I select this option I just get the error "could not set the configuration for CRTC 256", so no 1280x800 for me yet. It also possible to select a resolution from the command line using
```
xrandr --output 0x101 --mode 1280x800_60.00
```
(using your identifier of course), unfortunately this doesn't work for me either, I just get the error "xrandr: Configure crtc 0 failed". 

Let me know if you guys have any more success than me.

Also, stupidfish, the reason you got the error the second time your tried to create the newmode is because the mode already exists (no need to add it again). If you run "xrandr -q" you should see the mode you have added. If you want to you can remove a mode from the list with:
```
xrandr --rmmode "1280x800_60.00"
```
Or if you have already added the mode (with xrandr --addmode) then run
```
xrandr --delmode 0x101 "1280x800_60.00"
```
first before you run rmmode.

Hope that make sense and that you get further than I did.

---

### Post by kylecronan on 2009-05-02
> **greggh said:**
> I can't find that package debian/media/drm-poulsbo listed in [http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/](http://netbook-remix.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/)

Also, do I add this as a repo? Do I somehow load each of these packages/modules separately? This is all too confusing. Starting to regret buying this netbook. But thanks for trying to help anyway.

Yeah, I think we all regret it. :)  That note about drm-poulsbo was just for people who want to compile the driver from source.  You should be able to just add this repo to your sources.list (do these commands as root):

```
echo "deb http://netbook-remix.archive.canonical.com/ubuntu/ hardy-dell-mini main restricted universe" >> /etc/apt/sources.list
```

And then do some updates:

```
aptitude full-upgrade
aptitude install xserver-xorg-video-psb

```

---

### Post by tyroeternal on 2009-05-02
I have a quick question for those running jaunty.  My wireless is not working out of the box for jaunty unr or the lpia-alternate install.  Is there a step that I am missing?  The sta driver is on and lsmod shows wl is there...

---

### Post by Xernie on 2009-05-02
> **pahautane said:**
> Xernie and stupidfish, if you run:
```
xrandr -q --verbose
```

You should get output that looks something like this:
```
toro@paparoa:~$ xrandr -q --verbose
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 (0x102) normal (normal) 0mm x 0mm
Identifier: 0x101
Timestamp:  795899
Subpixel:   horizontal rgb
Clones:    
CRTC:       0
CRTCs:      0
Panning:    0x0+0+0
Tracking:   0x0+0+0
Border:     0/0/0/0
Transform:  1.000000 0.000000 0.000000
0.000000 1.000000 0.000000
0.000000 0.000000 1.000000
filter: 
1024x768 (0x102)   48.0MHz *current
h: width  1024 start    0 end    0 total 1024 skew    0 clock   46.8KHz
v: height  768 start    0 end    0 total  768           clock   61.0Hz
800x600 (0x103)   29.3MHz
h: width   800 start    0 end    0 total  800 skew    0 clock   36.6KHz
v: height  600 start    0 end    0 total  600           clock   61.0Hzv
```

If you use the value from the Identifier line in place of LVDS then the addmode command should work, eg:
```
xrandr --addmode 0x101 "1280x800_60.00"
```

After you have done that you will find that a 1280x800 option appears in the Display Preferences dialogue. Unfortunately, when I select this option I just get the error "could not set the configuration for CRTC 256", so no 1280x800 for me yet. It also possible to select a resolution from the command line using
```
xrandr --output 0x101 --mode 1280x800_60.00
```
(using your identifier of course), unfortunately this doesn't work for me either, I just get the error "xrandr: Configure crtc 0 failed". 


I just tried this and got the CRTC error you got. In other words, I was able to add the mode using your advice and the resolution did show up in the Display Preferences, but when I select it I get the same CRTC error you got.

Has anybody been able to get 1280x800 using the method in post 420?

---

### Post by pistoncito on 2009-05-02
> **Xernie said:**
> I just tried this and got the CRTC error you got. In other words, I was able to add the mode using your advice and the resolution did show up in the Display Preferences, but when I select it I get the same CRTC error you got.

Has anybody been able to get 1280x800 using the method in post 420?

same error here. It's a pitty, since jaunty seems to run faster than hardy.

---

### Post by catslaugh on 2009-05-02
I&#8217;m running Jaunty.  I downloaded 855resolution_0.4-1ubuntu1_i386.deb (had to go Googling to find it), installed it, and put these settings in /etc/default/855resolution:
MODE=5c
XRESO=1280
YRESO=800
That, along with the post 420 instructions, got me to 1280×800 resolution using the vesa driver.

---

### Post by tyroeternal on 2009-05-02
As I have noticed a few people around the web using the Dell Mini 9 and the Mini 12 having the same issue with wireless not working in jaunty after reinstall, here is the fix:  I had turned off bluetooth and wireless with the aircraft manager before installing Jaunty without realizing it.  After the new OS was installed wireless and bluetooth showed as existing but could not be turned on due to lack of working function keys.

To fix the problem I was able to re-enable both wireless and bluetooth after installing the aircraft-manager program as linked to and detailed in these articles: for [jaunty](http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html) & for [hardy/intrepid](http://www.ubuntumini.com/2008/12/aircraft-manager-save-battery-by.html).

Sorry to have jumped into the ongoing resolution fix talk.  Also, a big 'Thank You' to everyone that has put effort in to solving the many issues this laptop brings forward.

---

### Post by stupidfish on 2009-05-02
> **catslaugh said:**
> I’m running Jaunty.  I downloaded 855resolution_0.4-1ubuntu1_i386.deb (had to go Googling to find it), installed it, and put these settings in /etc/default/855resolution:
MODE=5c
XRESO=1280
YRESO=800
That, along with the post 420 instructions, got me to 1280×800 resolution using the vesa driver.

Pardon my ignorance, but how exactly does one go about doing this?

---

### Post by catslaugh on 2009-05-02
As I recall, I did as post 420 suggested:
```
holocron% cvt 1280 800 60
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
holocron% xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
```
and then the next line didn’t work:
```
holocron% xrandr --addmode LVDS "1280x800_60.00"
```
So I looked at subsequent messages about the 855resolution program.  I tracked it down at [http://old-releases.ubuntu.com/ubuntu/pool/universe/8/855resolution/](http://old-releases.ubuntu.com/ubuntu/pool/universe/8/855resolution/) , found that it would still install (with the usual [FONT="Courier New"]dpkg -i[/FONT]), and then ran [FONT="Courier New"]sudo 855resolution -l[/FONT] to find a VESA mode I didn’t need, ran [FONT="Courier New"]sudo 855resolution 5c 1280 800[/FONT], logged out, and when gdm came up again it was in 1280×800 mode.  I had to edit [FONT="Courier New"]/etc/defaults/855resolution[/FONT] to tell it about the parameters; 855resolution installs in [FONT="Courier New"]/etc/rc5.d[/FONT] at S13, before gdm starts, so by the time the X server starts, the BIOS has already been tweaked.

---

### Post by pahautane on 2009-05-02
I can confirm that the steps from catslaugh work for me:

```
wget http://old-releases.ubuntu.com/ubuntu/pool/universe/8/855resolution/855resolution_0.4-1ubuntu1_i386.deb
sudo dpkg -i 855resolution_0.4-1ubuntu1_i386.deb 
sudo 855resolution -l
sudo 855resolution 5c 1280 800
```

Then edit /etc/default/855resolution as suggested and finally logout. When gdm restarted 1280x800 was selected automatically, yay. Nice work, thank you.

---

### Post by greggh on 2009-05-02
> **pahautane said:**
> I can confirm that the steps from catslaugh work for me:

```
wget http://old-releases.ubuntu.com/ubuntu/pool/universe/8/855resolution/855resolution_0.4-1ubuntu1_i386.deb
sudo dpkg -i 855resolution_0.4-1ubuntu1_i386.deb 
sudo 855resolution -l
sudo 855resolution 5c 1280 800
```

Then edit /etc/default/855resolution as suggested and finally logout. When gdm restarted 1280x800 was selected automatically, yay. Nice work, thank you.


What's the performance like with the VESA driver at 1280X800? Do YouTube videos play ok?

---

### Post by Xernie on 2009-05-02
> **pahautane said:**
> I can confirm that the steps from catslaugh work for me:

```
wget http://old-releases.ubuntu.com/ubuntu/pool/universe/8/855resolution/855resolution_0.4-1ubuntu1_i386.deb
sudo dpkg -i 855resolution_0.4-1ubuntu1_i386.deb 
sudo 855resolution -l
sudo 855resolution 5c 1280 800
```

Then edit /etc/default/855resolution as suggested and finally logout. When gdm restarted 1280x800 was selected automatically, yay. Nice work, thank you.

This didn't work for me, but I think it might be because of the VESA driver. I mean, how do I know if I am using that and not the Intel driver? Put another way, did you guys do something to enable the VESA driver?

---

### Post by tyroeternal on 2009-05-02
For those that use the alternate-lpia version of jaunty, the i386 deb must be repackaged for lpia before it can be installed, here is how to do that:

[LIST=1]
[*]extract the contents of the i386 deb file
[*]rename the folder "855resolution_0.4-1ubuntu1_lpia" and open it
[*]remove the binary file and extract both compressed files within, then delete the original compressed files
[*]move the etc and usr folders out of the data folder and delete the data folder
[*]rename the control folder "DEBIAN" and open it
[*]open the control file and set the architecture as "lpia" rather than "i386"
[*]now, open a terminal and navigate to where the main folder is at and build the package: "dpkg --build 855resolution_0.4-1ubuntu1_lpia"
[*]the package then can be installed with: "sudo dpkg -i 855resolution_0.4-1ubuntu1_lpia.deb"
[/LIST]

I hope this helps :)

---

### Post by Abke on 2009-05-03
i also confirm that post 474 (855resolution) is working for me (in combination with post 420).

When i completed the instructions as in post 420, the last command didn't work for me. After that i executed the commands from post 472 (addmode, delmode etcetera) and the resolution somehow changed, but not usable at all. Vertical stripes and parts of the screen were overlapping. I had to use a tool at startup to fix this (and went back to the old settings). After that i executed the commands as in post 474. Works perfect! (of course only the resolution, the display is still slow and even scrolling trough a page isn't working nice and smooth).

---

### Post by danboid on 2009-05-03
Hi

One of the main apps that I wanted to use on my mini 10 is having problems with the psb video driver - I'm getting frequent crashes and freezes and gdb is pointing at my psb dri driver segfaulting so I wanted to check with you guys that I have the latest drivers installed.

Heres what dpkg says I have installed, psb wise:

----------------------------

dan@dan:~$ dpkg --list '*psb*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  libgl1-mesa-dri-psb       0.24+repack+0038.1-0netbo MESA 3D DRi driver for Poulsbo
un  psb-kmd                   <none>                    (no description available)
ii  psb-video                 0.28+0038-0netbook1       Video decode driver for Poulsbo
ii  xorg-modules-xpsb         0.16+0038-0netbook1       3D graphics daemon for Poulsbo
un  xserver-xorg-driver-psb   <none>                    (no description available)
ii  xserver-xorg-video-psb    0.27.0+repack-0netbook2   2D graphics driver for Poulsbo

-----------------------------------

This page hints at a version '5.0.0.0040':

[https://lists.ubuntu.com/archives/kernel-team/2009-April/005339.html](https://lists.ubuntu.com/archives/kernel-team/2009-April/005339.html)

Has that not made it into the hardy lpia repos yet? Update manager says I'm up to date and I'm pretty sure I've got all the best repositories enabled that are mentioned in this thread.

EDIT

Kyle- could you please add the latest driver versions and/or their ubuntu package names to the gma500 wiki please?

---

### Post by catslaugh on 2009-05-04
The VESA driver doesn’t do flash so well.  YouTube gets pretty choppy when it has to handle fast-moving video, and you start seeing flashes of the background behind the video.  Not as bad as it was under 1024×768, but I’m definitely looking forward to real Poulsbo support.

---

### Post by dimeified on 2009-05-04
FYI for anyone trying to run compiz for window effects, or AWN for your taskbar. Im running netbook remix on my mini 12, the hardy 8.04 version with all the instructions to use the psb driver. I took advice of one of the posts and installed XFCE. I have enabled the compositing effects under xfce and now i can run awn, and im sure docky would work too. Everything seems solid, and i dont really miss compiz/gnome at all. I get true transparency on my terminal windows now too!

---

### Post by AdamWill on 2009-05-04
Did anyone notice that, on April 30th, a bunch of new packages landed in the ubuntu-mobile repositories that appear to be psb for Ubuntu 8.10?

[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xserver-xorg-video-psb/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xserver-xorg-video-psb/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xpsb-glx/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xpsb-glx/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/libd/libdrm-poulsbo/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/libd/libdrm-poulsbo/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-kernel-source/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-kernel-source/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-firmware/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-firmware/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-meta/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-meta/)

are the bits of it that I can find. Intel....why. Just...why.

---

### Post by fitzkarraldo on 2009-05-04
> **AdamWill said:**
> Did anyone notice that, on April 30th, a bunch of new packages landed in the ubuntu-mobile repositories that appear to be psb for Ubuntu 8.10?

[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xserver-xorg-video-psb/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xserver-xorg-video-psb/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xpsb-glx/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xpsb-glx/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/libd/libdrm-poulsbo/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/libd/libdrm-poulsbo/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-kernel-source/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-kernel-source/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-firmware/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-firmware/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-meta/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-meta/)

are the bits of it that I can find. Intel....why. Just...why.

you're right, look [here]("https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any") 

every package has the following changelog
```
Initial package for Intrepid.
```

So, seems that they're working on...

---

### Post by papatrpt89 on 2009-05-04
> **AdamWill said:**
> Did anyone notice that, on April 30th, a bunch of new packages landed in the ubuntu-mobile repositories that appear to be psb for Ubuntu 8.10?

[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xserver-xorg-video-psb/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xserver-xorg-video-psb/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xpsb-glx/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/x/xpsb-glx/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/libd/libdrm-poulsbo/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/libd/libdrm-poulsbo/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-kernel-source/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-kernel-source/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-firmware/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-firmware/)
[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-meta/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-meta/)

are the bits of it that I can find. Intel....why. Just...why.

What exactly does this mean from an end-user standpoint?  That Intel is working on a driver, but only for 8.10?

A friend of mine recently bought a lower-end Mini 12 (Inspiron 1210) with Ubuntu 8.04 preloaded.  The preloaded OS requested to install ~140 updates or so when first hooked up to the net.  After this, network manager broke without explanation, and neither wired nor wireless connections would work.  Also, standard USB drives wouldn't mount, without explanation.

So, I opted to install 9.04 NBR on it.  Everything seemed to be working wonderfully (USB, wired and wireless network, etc.) save the graphics driver.  I started looking around for one of these, only to realize that one isn't available without a good deal of futzing and hacking.

Adam, your article proved remarkably helpful in figuring things out.  I hope as much as you do that a native, open driver finds its way into the repos sooner rather than later.  I have a few specific questions that either Adam or someone else knowledgeable may be able to answer:
1) If and when a native driver is released, would it automatically find its way to a Jaunty NBR install with default repos?  If not, what steps would need to be taken to pull the new driver from the repos?
2) Does anyone have a guess as to how long it might take for a native driver to become available in a repo?
3) Are future versions of Ubuntu likely to integrate support for the GMA 500 chipset?

I successfully applied the screen resolution fix suggested in this thread, but window movements, web page scrolls, etc. were still jerky, proving to me that the resolution fix wasn't actually a driver, rather a hack (besides the fact that the package was under 10kb in size, if I remember right).

At this point, I'm going to put a dual boot between XP and Ubuntu (XP has native chipset drivers, and video plays back smoothly on it, a function my friend uses quite a bit) and hope that an Ubuntu driver becomes available.  My friend does like to use Linux, and recognizes that it is a good deal speedier on a lower-end netbook such as his.

Thanks to everyone in this thread for helping put things together, and I do hope that this driver fiasco gets figured out pretty soon.

---

### Post by AdamWill on 2009-05-04
papa: it indicates that the bit of Intel which makes packages for Ubuntu at the request of Dell is working on a driver for Ubuntu 8.10 technology, likely for a future Dell-tweaked, 8.10-based UNR, just like their current tweaked 8.04-based UNR. I guess.

1: I can't answer this.
2: Very hard to answer that, either. No-one is entirely clear on how much of Intel is working on an actual decent native driver that is not a hacky special-sauce mess hidden away in the UNR development process. Greg Kroah-Hartman is working independently on such a driver, but it's hard to know how long that'd take him. Could be weeks, could be years. Once one emerges from either Intel or Greg, it would likely show up in the repositories for all major distributions quite rapidly.
3: I would imagine that, if a proper generic native driver becomes available, they would.

---

### Post by papatrpt89 on 2009-05-04
Adam,

Thanks for your response.  One more quick question that you may be able to answer: in your post about this topic on happyassassin, you mentioned that using a certain kernel and putting some proprietary globs in place, it might be possible to put a working setup together.  Did you ever get anywhere with this?  If I get the time, I may try putting the latest kernel supported by the driver together with the proprietary bits over a Jaunty NBR base.

If this is infeasible, I'll just cross my fingers and hope for the best.  Thanks again for your help and information with this process.

---

### Post by AdamWill on 2009-05-05
no, I never got anywhere. That doesn't mean it's impossible, just that it requires more chops than I possess. :) Someone with decent coding skills and a vague working knowledge of the X.org and kernel interfaces could probably do it. (And that someone is Greg Kroah-Hartman, who's trying, when he has the spare time.)

---

### Post by papatrpt89 on 2009-05-05
Very cool, thanks for the info!

---

### Post by Xernie on 2009-05-06
> **dimeified said:**
> Im running netbook remix on my mini 12, the hardy 8.04 version with all the instructions to use the psb driver.

To which instructions are you referring?

---

### Post by dimeified on 2009-05-06
Post 94 and everything after that which walks you through using the psb driver. I havnt gotten to be able to get movie player to not crash (i haven't tried yet), but i can use the 3d screen savers, the glxinfo shows direct rendering enabled, i can watch flash videos (rock solid), and use the awn dock, and i have true transparency, im running 1280x800. The compositing is smooth and efficient too.

The only thing i wish i could figure out, how the hell to get the volume controls FnF4, FnF5, and FnF6 to work for mute up and down. Oh and FnF7 for print screen.

Aside from those two complaints i am completely satified using this all the time as a stable netbook platform so far...

oh almost forgot, cheese crashes my login session too (so no camera), but it did that before i even switched to xfce.

---

### Post by Xernie on 2009-05-06
> **dimeified said:**
> Post 94 and everything after that which walks you through using the psb driver. I havnt gotten to be able to get movie player to not crash (i haven't tried yet), but i can use the 3d screen savers, the glxinfo shows direct rendering enabled, i can watch flash videos (rock solid), and use the awn dock, and i have true transparency, im running 1280x800. The compositing is smooth and efficient too.

The only thing i wish i could figure out, how the hell to get the volume controls FnF4, FnF5, and FnF6 to work for mute up and down. Oh and FnF7 for print screen.

Aside from those two complaints i am completely satified using this all the time as a stable netbook platform so far...

oh almost forgot, cheese crashes my login session too (so no camera), but it did that before i even switched to xfce.

Thanks! (And thanks to brteag00 as well.)

One question: does anybody know if there is any reason why this exact procedure wouldn't work using Jaunty UNR rather than Hardy?

---

### Post by greggh on 2009-05-06
> **Xernie said:**
> Thanks! (And thanks to brteag00 as well.)

One question: does anybody know if there is any reason why this exact procedure wouldn't work using Jaunty UNR rather than Hardy?

I believe it won't work because those proprietary bits don't work with kernels newer than the one in Hardy.

---

### Post by brteag00 on 2009-05-07
Hey y'all -

I just wanted to note that a few more packages have dropped in the ubuntu-mobile PPA in the last week, and the driver is now fully functional in Intrepid.  That means working 3D and video decode as well as full-resolution 2D.  The archive is [_here._]("https://launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=intrepid")

There is some evidence that things are still somewhat hacked together, as these packages depend on libdrm v1 instead of v2.  This necessitates a rebuilt Mesa and Xorg stack.  However, it's super easy once you add the PPA to your /etc/apt/sources.list (following the instructions on page linked above) - just install the poulsbo-driver-2d and poulsbo-driver-3d meta-packages.  These pull in the rest - Xorg driver, DRI library, libva, firmware, Xpsb, Mesa, the works.

I have installed the above on a stock Intrepid (lpia) install, and it works fine.  There were two hiccups - first, the DRI device is created in the "video" group, so you have to be a member of that group to use 3D or video accel.  Second, a couple files in the above packages conflicted with a Mesa package (mesa-common-devel, I think) that I already had installed - if you get errors, remove the appropriate Mesa packages before pulling in the PPA's.

Also of note - if you add "psb" to its driver whitelist, Compiz works with these drivers.  (If you recall, it didn't work in Hardy.)  I think it's unusably slow, but I know there were a bunch of folks here who wanted it.

The gripe, of course, is that we're still a release behind the rest of the Ubuntu world - ie, no Jaunty packages yet.  But it sure is nice to have all the bits available from an official source instead of ripping them out of the Dell image.

---

### Post by greggh on 2009-05-07
> **brteag00 said:**
> just install the poulsbo-driver-2d and poulsbo-driver-3d meta-packages.  These pull in the rest - Xorg driver, DRI library, libva, firmware, Xpsb, Mesa, the works.

Could I just install poulsbo-driver-2d and skip poulsbo-driver-3d. I don't want 3d. I just want good 2D and video acceleration. I read earlier in this thread that in Hardy some people got better 2D performance if they didn't also have the 3D bits installed.

> I have installed the above on a stock Intrepid (lpia) install, and it works fine.

How do you do a stock Intrepid (lpia) install? From what I read earlier in this thread I thought that in order to get a proper lpia architecture installed you couldn't do a stock install, but rather you needed to install Ubuntu Netbook Remix.

> There were two hiccups - first, the DRI device is created in the "video" group, so you have to be a member of that group to use 3D or video accel.

I'm confused about that. How do you make it so that you're a member of that group?

Thanks for the info. Much appreciated.

---

### Post by kylecronan on 2009-05-07
Seems like the hardest part is getting the lpia alternate iso for Intrepid to install.  It will fail to install the kernel and also doesn't complete the install itself due to some xorg package conflict.  I had to leave my system in a partially installed state and then go in with the rescue mode and manually install linux-image-lpia and linux-restricted-modules-lpia, run update-grub, and install ubuntu-desktop.

I wonder if there is any work that remains to be done for compatibility with xorg 1.6, or if the issue with Jaunty is just the incompatibility with 2.6.28 at this point.

edit: greggh, as far as 2d vs 3d, I think you're remembering when people disabled 3d because of the old stability issue (which is mostly resolved now).  That's very different than saying that 2d performance is affected by having AIGLX enabled.  Also, you're probably going to want the "3d" parts of the driver so that you can use xv to watch video.

Here is the link for "stock" (ie, not UNR) Intrepid for lpia:

[http://cdimages.ubuntu.com/ports/releases/intrepid/release/ubuntu-8.10-alternate-lpia.iso](http://cdimages.ubuntu.com/ports/releases/intrepid/release/ubuntu-8.10-alternate-lpia.iso)

The best way to get this on a USB stick is with Ubuntu's usb-creator program.  It still won't install right (see above).

I didn't have to add myself to the 'video' group.  I just emptied out my xorg.conf after installing the poulsbo driver packages and everything worked immediately.

---

### Post by greggh on 2009-05-07
kylecronan, thanks for the info. Just 2 quick questions.

1. That link to the Intrepid lpia iso. Is that the one you had trouble installing and had to go into rescue mode?

2. When you say you just had to empty out your xorg.conf after installing the poulsbo driver. How exactly is emptying your xorg.conf done?

Thanks again. Sorry if some of these questions are dumb. I'm still really bad when it comes to the command line.

---

### Post by kylecronan on 2009-05-07
1. That's the one.  If you're not that familiar with the command line, it will not be an easy one to install.  In addition to the problems I mentioned before, X won't start in VESA mode without the HorizSync/VertRefresh fix documented early in this thread.  Also, I had to add cdrom-detect/try-usb=true to the boot options for the rescue mode.  But give it a try.  You will learn a lot, and I'd be happy to help you if you get stuck.

2. You could use a text editor.  Or, my favorite: cp /dev/null /etc/X11/xorg.conf (although I take it back: I did have to add myself to the 'video' group for stuff that uses DRI)

---

### Post by greggh on 2009-05-07
kylecronan, thanks very much for the offer of help. I may take you up on it in the near future if I get totally stuck. But I'm optimistic that I'll be able to install it.

---

### Post by greggh on 2009-05-07
> **kylecronan said:**
> (although I take it back: I did have to add myself to the 'video' group for stuff that uses DRI)

How do you add yourself to the 'video' group?

---

### Post by kylecronan on 2009-05-07
The simplest way is to use the "Users and Groups" control panel under "Administration" (or sudo vigr).

---

### Post by brteag00 on 2009-05-07
With regards to getting the lpia image to install - I ended up doing a network install using a PXE boot with appropriately configured DHCP and TFTP servers.  That process is beyond the scope of this discussion - I'm sure a standard USB-stick install would work fine.

You can actually get the kernel to install from the installer with just one command-line trick - the installer will complain that it can't find a kernel.  Tell it to continue with the installation.  Then, when you get to the next screen (selecting packages, as I recall), go over to another virtual terminal (Alt+F2, I think) and, at the prompt, type "apt-get install linux-lpia".  This will install the kernel, and then you can continue with the rest of the OS installation as usual.  NOTE - you want the 'desktop' packages but NOT the 'mobile' packages, they conflict with eachother!

Sheesh.  For all the polish that the rest of Ubuntu receives, the release engineering for this particular piece really stinks.

---

### Post by kylecronan on 2009-05-07
Yeah if you do a net install you don't have the issue with conflicting packages causing the install to fail (just the missing kernel).  They must have fixed the lpia packages after the release was done.

Have you been able to get mplayer-vaapi working with this driver?  I got it compiled, and when I play a file it opens up the psb_drv_video stuff just fine, but then I get this error:

```
VDec: vo config request - 368 x 480 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.

```

Any idea why it would do that?

---

### Post by brteag00 on 2009-05-07
> **kylecronan said:**
> 
```
VDec: vo config request - 368 x 480 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.

```

Any idea why it would do that?

No, I don't.  I havn't compiled a new version; I'm using the one I built a few months back (20090123).  Are you using the version of libva that comes with Intrepid, or the one on the mplayer-vaapi website?

---

### Post by kylecronan on 2009-05-07
> **brteag00 said:**
> No, I don't.  I havn't compiled a new version; I'm using the one I built a few months back (20090123).  Are you using the version of libva that comes with Intrepid, or the one on the mplayer-vaapi website?

I installed the libva debs from the mplayer-vaapi website.  I had to use --force-depends to get the libva-dev package to install, but I figure that's probably okay if it compiled.

---

### Post by brteag00 on 2009-05-07
> **kylecronan said:**
> I had to use --force-depends to get the libva-dev package to install, but I figure that's probably okay if it compiled.

Yeah, I did too.

I just built the newest mplayer-vaapi, and it seems to work fine as well.

From my (admittedly limited) experience with video decoding, your "could not find matching color space" error sounds like a problem with Xv or XvMC.  Are you sure you've got all your permissions, etc. correct?  Ie, hardware-accelerated 3D works?  Also check your /var/log/Xorg.0.log for errors.  Beyond that, I'm not sure what to suggest...

---

### Post by marduk667 on 2009-05-08
Wow this went really fast now, maybe they can do this for Jaunty, too? Do you know who is reponsible for the PPA?

---

### Post by fitzkarraldo on 2009-05-08
> **marduk667 said:**
> Wow this went really fast now, maybe they can do this for Jaunty, too? Do you know who is reponsible for the PPA?

anybody tried to upgrade from hardy? I have a working Hardy install, according to post #252, and I suppose that the upgrade process should work as actually the only problem with Jaunty seems to be the install process (I should downgrade some psb packages too, I suppose). Any suggest?

@those who tried Intrepid on this netbook: what about performances?

---

### Post by matthiasak on 2009-05-08
I have successfully installed the i386 version of intrepid :P  wasn't hard, use unetbootin or usb-creator to make the install USB and then boot. Everything went quickly.

simply do:
1) install intrepid desktop .iso
2) run any and all updates available (without changing software sources, etc)
3) add these two lines to /etc/apt/sources.list

```

deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu intrepid main

```

and then install the packages 'poulsbo-driver-2d' and 'poulsbo-driver-3d'

and voila! working compiz and everything! boots fast, works amazingly well, plus there's the option to upgrade to jaunty and such when the dirvers become available.

PLEASE NOTE: do NOT add sources for backports or proposed updates, they will f!*# the install and stability up and then it will crash and will force X into low-graphics mode. If you do this, press escape at the boot menu and choose the last kernel before the bad update. It will be fine to then boot into that kernel normally. remove the two incompatible kernel entries in /boot/grub/menu.lst to get it to automatically choose the "good" kernel.

---

### Post by greggh on 2009-05-08
matthiasak, thanks for the info. Going the intrepid i386 route does sound very simple compared to installing the intrepid alternate lpia iso.

Is there a very substantial and noticeable performance hit going with i386 instead of lpia?

---

### Post by greggh on 2009-05-08
> **matthiasak said:**
> PLEASE NOTE: do NOT add sources for backports or proposed updates, they will f!*# the install and stability up and then it will crash and will force X into low-graphics mode.

Are you saying that you can never run an update, or the system will break? Or  are you saying that you just can't run any updates if you have the backports repo enabled?

---

### Post by matthiasak on 2009-05-08
There is no performance hit that I can presumably feel in the system other than less developed video drivers, which are obviously still being developed. 

I just meant that you do not want to install updates from intrepid-proposed, I actually have not tried backports, but proposed installed a newer, and incompatible, kernel.

---

### Post by greggh on 2009-05-08
> **matthiasak said:**
> There is no performance hit that I can presumably feel in the system other than less developed video drivers, which are obviously still being developed. 

Yeah, I know that the video drivers are still a work in progress for GMA 500. I was just wondering if there is a meaningful performance difference between running Intrepid lpia over Intrepid i386. So I gather that you think there isn't.

> I just meant that you do not want to install updates from intrepid-proposed, I actually have not tried backports, but proposed installed a newer, and incompatible, kernel.

Now I understand. Thanks for sharing your experience.

---

### Post by Flonak on 2009-05-09
Hello guys,

First message in this forum that I read very often.

Just wanted to be the one that makes you happy to know that there is a first Jaunty package on the ubuntu-mobile PPA.

It's only a source-package but I really think the end of this mess is near.

Nice week-end to all of you.

---

### Post by Flonak on 2009-05-09
> **matthiasak said:**
> I have successfully installed the i386 version of intrepid :P  wasn't hard, use unetbootin or usb-creator to make the install USB and then boot. Everything went quickly.

simply do:
1) install intrepid desktop .iso
2) run any and all updates available (without changing software sources, etc)
3) add these two lines to /etc/apt/sources.list

```

deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu intrepid main

```and then install the packages 'poulsbo-driver-2d' and 'poulsbo-driver-3d'

and voila! working compiz and everything! boots fast, works amazingly well, plus there's the option to upgrade to jaunty and such when the dirvers become available.

PLEASE NOTE: do NOT add sources for backports or proposed updates, they will f!*# the install and stability up and then it will crash and will force X into low-graphics mode. If you do this, press escape at the boot menu and choose the last kernel before the bad update. It will be fine to then boot into that kernel normally. remove the two incompatible kernel entries in /boot/grub/menu.lst to get it to automatically choose the "good" kernel.


This blocks at step 1.

I used the "Create a usb startup disk" wizard and the ubuntu desktop iso and at boot, I only got a prompt. (no gnome).

What iso image did you use to get this working ?

---

### Post by marduk667 on 2009-05-09
Hey you can use the standard iso, but you have to change the xorg.conf after boot, then restart gdm.

> Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 30.0 - 80.0
VertRefresh 50.0 - 70.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x800" "1024x640"
EndSubSection
EndSection


After this all the steps work!
I today have reinstalled my Mini12 with intrepid and it really works great, even better than the Dell-Image! I also can use the great functions of intrepid now (added the blueman from ppa so i can use networkmanager to connect to 3G via bluetooth)
Also the firefox seems to be faster and more stable, the X-Server also seems more stable for what i have seen for now. Suspend/Wakeup works perfect. Compiz is a bit slow so i switched it off for now, but it really works :)
It seems i now can work with the Mini12 as i wanted nearly half a year after buying it...

---

### Post by decahedron on 2009-05-09
I have just ordered a Dell Mini 12 (with XP because it was free).  I plan to upgrade to Ubuntu ASAP.  There has been some discussion about installing Ubuntu on the Mini 12 due to the GMA 500 graphics driver.  

I have been told in the Dell forum that the desktop i386 9.04 (jaunty) will install no problem.  However, I believe the users in this thread of much greater technical competence (I mean no disrespect to the users in the Dell forums, just stating a fact).  Has anyone in this thread tried jaunty.  Are there potential pit falls anyone here can see?

I have also heard about a Ubuntu Netbook Remix, a modified ubuntu for Netbooks.  Ubuntu 9.04 UNR be a good option to try?

Thanks for all the hard work the users of this thread have put into this.  I do not have the technical competence myself to have figured out how to install Ubuntu on the Mini 12.  Thanks to this thread I feel that I will at least be able to follow the instructions.

---

### Post by marduk667 on 2009-05-09
Jaunty will work but no 3D/2D Acceleration.

I would recommend to install intrepid and use the ubuntu-mobile ppa as described above, this will bring you 2D/3D and everything else works best!

---

### Post by decahedron on 2009-05-09
Thanks

---

### Post by teatimest on 2009-05-09
I have Hardy UNR and was thinking of upgrading to Intrepid via update manager. During the process, I get error saying that...

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/main/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/main/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/universe/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/universe/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/multiverse/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/multiverse/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/restricted/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/restricted/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/main/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/main/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/universe/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/universe/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/multiverse/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/restricted/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/restricted/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/main/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/main/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/universe/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/universe/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/multiverse/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/multiverse/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/restricted/binary-lpia/Packages.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/restricted/binary-lpia/Packages.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found
, W:Failed to fetch [http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://netbook-remix.archive.canonical.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Does this mean I can't upgrade from Hardy UNR to Intrepid UNR? Anybody tried or succeeded?

---

### Post by dimeified on 2009-05-09
i had the same issue so im doing the i386 iso, i tried the normal desktop iso but as predicted x wouldnt start, i edited xorg.conf added in the lines and was able to start x with startx. i double clicked the installer and went through the motions but at one point the installer juts exited about half way through copying the files for the new isntallation. im downloading the alternate installer now to try a text base install.

---

### Post by matthiasak on 2009-05-10
> **dimeified said:**
> i had the same issue so im doing the i386 iso, i tried the normal desktop iso but as predicted x wouldnt start, i edited xorg.conf added in the lines and was able to start x with startx. i double clicked the installer and went through the motions but at one point the installer juts exited about half way through copying the files for the new isntallation. im downloading the alternate installer now to try a text base install.


Strange, I am using the mini 10, not the 12, in case that may mean something else... but which tool did you use to create the USB? Unetbootin or usb-creator?  I had tried Unetbootin and it messed up before and then used usb-creator and it worked... I was able to boot to the live desktop, which ran at 800x600 automatically, and was able to run that installer and then add the repos and it automatically configured my screen's size to 1024x576.

---

### Post by decahedron on 2009-05-10
This morning I posted a link to this thread in the Dell forums and tonight I see that the post was deleted.  Dell is not posting drivers, .ISO files or answering any posts with regards to this issue.  In addition, posts that direct people to this information are deleted.  Hrm

---

### Post by floquet on 2009-05-10
I'm trying to follow the installation for the 8.10-lpia posted by kylecronan several posts ago. I've sorted many problems but there is one I can not sort. When trying to install the lpis kernel in the rescue mode (see post #501) the system just keep on asking for the Ubuntu installation cdrom after the "apt-get install linux-lpia". It seems not able to find the files, but odd enough it just read the Releases files:(.

Any help will be appreciated

---

### Post by greggh on 2009-05-10
> **floquet said:**
> I'm trying to follow the installation for the 8.10-lpia posted by kylecronan several posts ago. I've sorted many problems but there is one I can not sort. When trying to install the lpis kernel in the rescue mode (see post #501) the system just keep on asking for the Ubuntu installation cdrom after the "apt-get install linux-lpia". It seems not able to find the files, but odd enough it just read the Releases files:(.

Any help will be appreciated

Did you remember to do the following?

> Also, I had to add cdrom-detect/try-usb=true to the boot options for the rescue mode.

From your problem it sounds like you may have skipped that.

---

### Post by danboid on 2009-05-10
Progress! :D

Thanks to mattiasak's post #512 (the 'new' #94 IMO ;) ) in this thread I now have Intrepid installed and running very nicely ('cept for a few GFX probs which I cover later) on my mini 10! Thank you Matt! I followed his instructions in #512 and I used marduk's xorg.conf in post number #519 only I changed the line:

Modes "1280x800" "1024x640"

to

Modes "800x576"

That let me 'startx' and run the intrepid desktop (X GUI) installer np!

One big plus about having upgraded to intrepid is its fixed my touchpad- under belmont I found impossible to use scrollbars using the touchpad but I can do that fine under Intrepid so I no longer need to always have my USB mouse plugged in to use X now.

After I installed the pouslbo 2D and 3D drivers and rebooted, X changed to the correct video mode (1024x576) despite me still using marduks xorg.conf which currently only specifies 800x576 and doesn't even mention psb. DRI wasn't enabled/accessable until I created a 'video' group and added my user to that group, now glxinfo tells me I do have DRI enabled but I still can't activate compiz as it just says 'Desktop Effects could not be enabled'. lsmod tells me I've got the psb and drm modules loaded?

Seeing as I can't get compiz working I can be pretty certain that I've not got my GFX card configured properly hence I shouldn't be surprised that I can't even get a picture of any res out of the HDMI port yet. The good news to emerge out of all my GFX probs is that xrandr does see my HDTV and it lists an additional, higher res - 1280x720 - as being available that wasn't available in belmont, but I've so far failed to get any of the 3 available HDMI res' to work under Intrepid (the others being 640x480 and 800x600) but I'll have to try again after someones explained how to get compiz working- I'll prob. need a properly configured xorg.conf.

Kyle - Your gma wiki page could well do with being updated to reflect the new support by intrepid. I would really like to see your page include full instructions on how to get X/compiz fully functional and include complete xorg.conf files for both the Mini 12 and the Mini 10.

After we've done that we should then update:

[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

Which is now totally outdated and wrong wrt Linux support and it should link to Kyles page, once we've updated and fleshed it out a bit with xorg.conf's and recommended/latest package repository addresses and version numbers for reference. This thread is beyond a joke now but we could kill it when we complete the gma500 Linux wiki with the necessary info and guides.

I'm much happier now that I'm running normal, i386 Ubuntu instead of a LPIA version. Why? Because the main reason I use Ubuntu and Debian are the repositories which allow me to avoid having to mess around compiling some big nasty programs. All non-official, 3rd party repos support i386 but hardly any provide LPIA packages too and personally I haven't noticed LPIA builds to be any faster than i386. Running 'normal' ubuntu is just a lot easier.

Thanks for your help guys!

---

### Post by dimeified on 2009-05-10
i used an external cd drive to install... also glxinfo reports there is no direct rendering for me even though i installed both the 2d and 3d drivers.

---

### Post by floquet on 2009-05-10
Yes. I did try with cdrom-detect/try-usb=true. Without this option the installation will not even start. I had the installation half way thru, as described by kyle, the kernel installation failed. When moved to the recovery mode to install the kernel, I got this failure. As recommended by Kyle, when doing the apt-get install linux-lpia, apt will be able to read the packages definition (also in the usb thumb drive) but not the installation files themselves.

Nevertheless, I moved to the installation of the 8.10 386 as described in post #512 by Matthiasak. I had to activate the old trick of adding the "all_generic_ide" option to the grub line.

One note, the installation of the psb-driver-2D and psb-driver-3D has to be done after updating the system to the current versions. Initial versions of the 8.10, and certainly the one in the ISO file will not start the X.

I have the impression that this 8.10 386 is a little bit slower than the 8.04 lpia (installed following Marduk's #94 post). If I get to solve this problem and install 8.10 lpia I should be able to compare both 8.10

Thanks to everyone in this thread for this wonderful source of information

Floquet

---

### Post by huso113 on 2009-05-10
Hi all,
My question is not related to graphic staff, but to the thermal management.
I try to get CPU temperature in standart way and get zero:
```
cat /proc/acpi/thermal_zone/TZ00/temperature
temperature 0 C
```

Can someone report him temperature to get sure it`s not hardware problem?

---

### Post by kylecronan on 2009-05-10
> **floquet said:**
> Yes. I did try with cdrom-detect/try-usb=true. Without this option the installation will not even start. I had the installation half way thru, as described by kyle, the kernel installation failed. When moved to the recovery mode to install the kernel, I got this failure. As recommended by Kyle, when doing the apt-get install linux-lpia, apt will be able to read the packages definition (also in the usb thumb drive) but not the installation files themselves.

I had to plug in an ethernet cable and put [http://ports.ubuntu.com/](http://ports.ubuntu.com/) in my sources.list.  apt-get update and then you can get the kernel to install.

---

### Post by dimeified on 2009-05-10
For anyone attempting the intrepid install, make sure you don't get too anxious and install the 2d/3d drivers with the new source repos without FIRST running apt-get update and upgrade! If you get too anxious like i did and install the 2 drivers first, you will end up overwriting the xorg.conf generated by them when you run apt-get update/upgrade and 3d will not be enabled. I had to add the dri section after the fact to get it all working hehe...

---

### Post by danboid on 2009-05-10
dimeified:

Mattiasak did specify in #512 that you should do a full update/ upgrade before installing the pouslbo drivers anyway- did you miss it?

Could somebody who has compiz working on a mini 10 or mini12 please share their xorg.conf? Dunno about you dimefield but I had to use the xorg from marduk post #519 to get the Intrepid desktop installer to start and the installer just retained my xorg.conf. I did a full update before installing the psb drivers and I've tried re-installing them a few times but doing so hasn't changed my xorg.conf.

Kyle- Do you not agree that all Mini 10/12 Ubuntu users would benefit by having a reference xorg.conf easily available on your gma500 wiki? At least we can start by working towards it by posting one that will work as best we can manage given the current conditions.

Whats the checklist for fully working psb (3D and compiz working) drivers? ie what modules need to be loaded and how?

EDIT

After a fair bit of messing around trying to get compiz working or trying to install libqt4-dev I can't even get the 3D driver to install now! Hopefully I can fix this without re-installing from scratch. Is it just that Mini 10 isn't supported by this latest driver yet? Despite not having the 3D driver installed DRI is apparently still available. 

root@atombox:~# apt-get install poulsbo-driver-3d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libglu1-xorg-dev: Depends: libglu1-mesa-dev but it is not going to be installed
  libqt4-opengl-dev: Depends: libgl1-mesa-dev or
                              libgl-dev
                     Depends: libglu1-mesa-dev but it is not going to be installed or
                              libglu-dev
  xlibmesa-gl-dev: Depends: libgl1-mesa-dev
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@atombox:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic libgl1-mesa-dri-psb
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgl1-mesa-dev libglu1-mesa-dev mesa-common-dev
The following NEW packages will be installed:
  libgl1-mesa-dev libglu1-mesa-dev mesa-common-dev
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/435kB of archives.
After this operation, 1909kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  mesa-common-dev libgl1-mesa-dev libglu1-mesa-dev
Install these packages without verification [y/N]? y
(Reading database ... 177267 files and directories currently installed.)
Unpacking mesa-common-dev (from .../mesa-common-dev_7.2-1ubuntu3~810um1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/mesa-common-dev_7.2-1ubuntu3~810um1_all.deb (--unpack):
 trying to overwrite `/usr/include/GL/glext.h', which is also in package libgl1-mesa-dri-psb
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_7.2-1ubuntu3~810um1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-dev_7.2-1ubuntu3~810um1_all.deb (--unpack):
 trying to overwrite `/usr/lib/pkgconfig/gl.pc', which is also in package libgl1-mesa-dri-psb
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_7.2-1ubuntu3~810um1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libglu1-mesa-dev_7.2-1ubuntu3~810um1_i386.deb (--unpack):
 trying to overwrite `/usr/include/GL/glu_mangle.h', which is also in package libgl1-mesa-dri-psb
Errors were encountered while processing:
 /var/cache/apt/archives/mesa-common-dev_7.2-1ubuntu3~810um1_all.deb
 /var/cache/apt/archives/libgl1-mesa-dev_7.2-1ubuntu3~810um1_all.deb
 /var/cache/apt/archives/libglu1-mesa-dev_7.2-1ubuntu3~810um1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dimeified on 2009-05-10
I read what he wrote about that, but i was too anxious to wait. Also, i do have compiz working, make sure you add WHITELIST="psb" to compiz and it will start with compiz --replace. Also, i did the alternate installer which is text based, so you dont have to worry about editing xorgs until AFTER you have a completely installed system.

---

### Post by matthiasak on 2009-05-10
> **dimeified said:**
> I read what he wrote about that, but i was too anxious to wait. Also, i do have compiz working, make sure you add WHITELIST="psb" to compiz and it will start with compiz --replace. Also, i did the alternate installer which is text based, so you dont have to worry about editing xorgs until AFTER you have a completely installed system.


Awwww... sorry I DID add psb to whitelist, forgot to add that part in there.

I had everything working without having to screw with xorg or any config file by doing these now updated steps:

1) install i386
2) install updates (dont add backports or proposed sources)
3) restart
3) use the repos available at ([https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any](https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any)) to install poulsbo-driver-2d and poulsbo-driver-3d
4) edit /usr/bin/compiz "whitelisted drivers line", add 'psb' to the list
5) restart
6) turn on/off any effects you see fit with CCSM or System > Appearance > Effects

It runs well for me... updateability and application compatibility is a BIG PLUS... as well as no Yahoo toolbar stuff and a newer pre-installed Firefox. 

Now as far as video playback, I am not sure whether because I have compiz enabled or I don't have Fluendo codecs working. newer drivers will help fix a lot of problems, but I jsut can't play 720p and run Skype video chat at the same time as easily... granted right now I am on skype, running songbird, evolution, 10 tabs in Firefox, and compiz with several virtual desktops holding each application. I'm only at 50% memory usage of 1024 MB with an empty pagefile too, so I'm sitting pretty. As soon as we have working packages for Jaunty, however, I think i will take the plunge. Maybe the libva and the video accel api's will be better supported.

I also have removed pulse-audio, just running ALSA.

update: I accidently had poulsbo-driverS-2d/3d rather than poulsbo-driver-2d/3d

also, here is my xorg for those curious:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by greggh on 2009-05-10
> **matthiasak said:**
> Now as far as video playback, I am not sure whether because I have compiz enabled or I don't have Fluendo codecs working. newer drivers will help fix a lot of problems, but I jsut can't play 720p and run Skype video chat at the same time as easily... granted right now I am on skype, running songbird, evolution, 10 tabs in Firefox, and compiz with several virtual desktops holding each application. I'm only at 50% memory usage of 1024 MB with an empty pagefile too, so I'm sitting pretty.

Does your Mini 10 have a Z520, or a Z530?

---

### Post by matthiasak on 2009-05-10
> **greggh said:**
> Does your Mini 10 have a Z520, or a Z530?

Z530... why?

---

### Post by greggh on 2009-05-10
> **matthiasak said:**
> Z530... why?

Because my Mini 12 has a Z520, and I was wondering if I will get the same level of performance as you experienced. Now I know I can expect a bit less.

---

### Post by matthiasak on 2009-05-11
I wouldn't bank on it being far below, however this is a processor with HT, so the clock rate will pull more strings in terms of basic performance.

The main thing with the apps I have running is that most are handled by something other than the processor. When FF and evolution arent active, the threads are sleeping. Skype is handled by poulsbo video decoder, and the processor is used by this and little bit by songbird. So the system sees little drag.

Also, it does help to remove pulseaudio... it tends to eat up more cpu cycles. That and other things to help the system, like stop indexing and tracker, stop any extra services you don't need, and editing the swappiness of the virtual memory.

As far as this goes, however, I'm feeling like we finally have a solid footing to work with when installing ubuntu onto not just a Dell Mini but any other new Poulsbo system coming out.

Tis' a good feelin' :)

---

### Post by danboid on 2009-05-11
Thanks for pointing out the compiz whitelist line! Now compiz is working great on my Mini 10 - I don't know what everyone is complaining about as it seems to run just as well as on the pouslbo as under any intel gfx I've seen really. Its certainly not choppy or jerky w/ normal windows and SD video ie youtube etc.

So, the latest procedure roughly goes:

1) install i386 intrepid via Ubuntu USB creator
1.5 ) Copy xorg.conf if booting desktop CD
2) install updates (dont add backports or proposed sources)
2.5) restart
3) use the repos available at ([https://edge.launchpad.net/~ubuntu-m...ies_filter=any](https://edge.launchpad.net/~ubuntu-m...ies_filter=any)) to install poulsbo-driver-2d and poulsbo-driver-3d
4) edit /usr/bin/compiz "whitelisted drivers line", add 'psb' to the list
5) Use System -> Admin -> Users and Groups to create a group called 'video' if it doesn't exist  already and add your user to that group to enable DRI.
6) restart
7) turn on/off any effects you see fit with CCSM or System > Appearance > Effects

Working compiz is normally a pretty good sign you've got your X drivers setup OK, maybe if not entirely correctly. However, I still don't automatically get any picture out of HDMI like I did under belmont. Matts xorg.conf is just unconfigured so looks like I'm going to have to experiment more with xrandr to try and get a picture.

---

### Post by dimeified on 2009-05-11
fyi, rather than create a video group or add an xorg dri subsection, under privelages there is an option to "enable tv capture and 3d acceleration".

---

### Post by drb116 on 2009-05-11
I have a Dell mini 12 shipped with Ubuntu 8.04.  I tried to upgrade to 8.10 via the upgrade manager and it said it was upgrading to 8.10, but after 30 minutes and no errors, I did a reboot and found I was still on 8.04.
 
Is it possible to upgrade the version that was originally shipped to 8.10, then to 9.04?

---

### Post by dimeified on 2009-05-11
unfortunately you can not upgrade that way. You have the Dell Belmont ubuntu image, and dell hasn't released an 8.10 version of it yet. They have their own graphics drivers that only work with 8.04. Your better off just downloading the intrepid alternate installer cd, install the system, and then follow the steps in the last 2 pages to get the system up and running. It's pretty sad honestly to see Dell *holding back* their customers to 8.04, yet the open source community has us up to 8.10 already. What really sucks about it is if you do upgrade to intrepid as described, you will loose fluendo codecs for video playback since it is dell proprietary software.

---

### Post by matthiasak on 2009-05-11
> **dimeified said:**
> unfortunately you can not upgrade that way. You have the Dell Belmont ubuntu image, and dell hasn't released an 8.10 version of it yet. They have their own graphics drivers that only work with 8.04. Your better off just downloading the intrepid alternate installer cd, install the system, and then follow the steps in the last 2 pages to get the system up and running. It's pretty sad honestly to see Dell *holding back* their customers to 8.04, yet the open source community has us up to 8.10 already. What really sucks about it is if you do upgrade to intrepid as described, you will loose fluendo codecs for video playback since it is dell proprietary software.

I wonder if we could extract the fluendo codecs from Belmont :)

---

### Post by decahedron on 2009-05-11
Is there any advantage to installing the lpia image, since this is for low power intel architectures?  Would I be trading battery life for other essentials?

Thanks

---

### Post by dimeified on 2009-05-11
> **matthiasak said:**
> I wonder if we could extract the fluendo codecs from Belmont :)

im not sure how proprietary the video driver / codecs are, but it would be illegal to do even if it were possible, and because of that it would never make it into a distro or package archive, so it wouldnt really have much support, especially for integrating it into intrepid considering it was written for hardy.

---

### Post by dimeified on 2009-05-11
> **decahedron said:**
> Is there any advantage to installing the lpia image, since this is for low power intel architectures?  Would I be trading battery life for other essentials?

Thanks

I ran hardy lpia then switched to intrepid i386. I havn't noticed any real difference in battery life. What i have noticed is that i dont have to deal with repackaging i386 debs for lpia now, so that has me sold to i386 already.

---

### Post by decahedron on 2009-05-11
> **dimeified said:**
> im not sure how proprietary the video driver / codecs are, but it would be illegal to do even if it were possible, and because of that it would never make it into a distro or package archive, so it wouldnt really have much support, especially for integrating it into intrepid considering it was written for hardy.

All the codecs needed are already available in the repositories.  So, Fluendo is not really required.  However, It would be much easier for Dell to just write the drivers and provide them into the standard distribution.  They may end up spending some money to develop the drivers that they would prefer to keep proprietary BUT what is the cost of maintaining a completely separate version of Ubuntu independently?

---

### Post by greggh on 2009-05-11
Looks like Dell is moving away from the Atom Z platform for its netbooks.

[http://www.engadget.com/2009/05/11/dells-299-mini-10v-now-officially-on-sale/](http://www.engadget.com/2009/05/11/dells-299-mini-10v-now-officially-on-sale/)

> Looks like Dell's Stateside online store has put the new $299 Atom N270-powered Mini 10v (née Inspiron 1101) up for order after it went on sale in Denmark late last night. Preliminary ship date is listed as June 1, but we're guessing it'll arrive a little sooner, as the original date was "mid-May."

I get the feeling we won't be seeing that many more devices sporting the gma 500.

[IMG]http://www.blogcdn.com/www.engadget.com/media/2009/05/5-11-09insp10v.jpg[/IMG]

---

### Post by zim2dive on 2009-05-12
> **greggh said:**
> Looks like Dell is moving away from the Atom Z platform for its netbooks.

[http://www.engadget.com/2009/05/11/dells-299-mini-10v-now-officially-on-sale/](http://www.engadget.com/2009/05/11/dells-299-mini-10v-now-officially-on-sale/)



I get the feeling we won't be seeing that many more devices sporting the gma 500.

Ditto from Engadget: [http://www.engadget.com/2009/05/12/intel-reveals-notebook-and-netbook-plans-for-the-rest-of-the-yea/](http://www.engadget.com/2009/05/12/intel-reveals-notebook-and-netbook-plans-for-the-rest-of-the-yea/)

---

### Post by woodhouse on 2009-05-12
what about "psb-modules" in ppa jaunty packages?
please, I prefer to use jaunty.. all mini-10 devices are recognised!

thank you..
guy

---

### Post by dimeified on 2009-05-12
> **woodhouse said:**
> what about "psb-modules" in ppa jaunty packages?
please, I prefer to use jaunty.. all mini-10 devices are recognised!

thank you..
guy

what?

---

### Post by matthiasak on 2009-05-13
xserver-xorg-video-psb - 0.31.0-0ubuntu1~904um1 

at [https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any](https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any)

new xserver 2D drivers just went live! We're almost there! now we need the opengl (3D) and DRI support, and we'll be up to date with ... well... wow.... hard to believe our struggle is almost over...

who wants to toss the ring in the lava :)

I think I'm going to plunge-in, run the update from Intrepid to Jaunty and I will let you guys know how it works in ~24 hours. 

Until tomorrow, ciao

---

### Post by woodhouse on 2009-05-13
> **matthiasak said:**
> xserver-xorg-video-psb - 0.31.0-0ubuntu1~904um1 

at [https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any](https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any)

new xserver 2D drivers just went live! We're almost there! now we need the opengl (3D) and DRI support, and we'll be up to date with ... well... wow.... hard to believe our struggle is almost over...

who wants to toss the ring in the lava :)

I think I'm going to plunge-in, run the update from Intrepid to Jaunty and I will let you guys know how it works in ~24 hours. 

Until tomorrow, ciao
simply fantastic!
it works perfect...

only one little trouble: it seems that isn't possible to expand my desktop to a second display; I can only duplicate it.

---

### Post by bcleveng on 2009-05-13
Hi, I'm hoping someone can give me a little bit of help.

I'm trying to get Ubuntu up and running on my mini 12. I've read through most of the thread, and followed these steps:

> **danboid said:**
> So, the latest procedure roughly goes:

1) install i386 intrepid via Ubuntu USB creator
1.5 ) Copy xorg.conf if booting desktop CD
2) install updates (dont add backports or proposed sources)
2.5) restart
3) use the repos available at ([https://edge.launchpad.net/~ubuntu-m...ies_filter=any]("https://edge.launchpad.net/%7Eubuntu-m...ies_filter=any")) to install poulsbo-driver-2d and poulsbo-driver-3d
4) edit /usr/bin/compiz "whitelisted drivers line", add 'psb' to the list
5) Use System -> Admin -> Users and Groups to create a group called 'video' if it doesn't exist  already and add your user to that group to enable DRI.
6) restart
7) turn on/off any effects you see fit with CCSM or System > Appearance > Effects


Everything's going as expected until I hit step 6. After fully installing, when I reboot it hangs during the boot stage. The last thing I get is a section of boot messages that look like:
> Starting periodic command scheduler crond         [ OK ]
Enabling additional executable binary formats binfmt-support     [ OK ]
Checking batery state...
/dev/sda:
Setting Advanced Power Management level to 0xfe (254)
And then a blinking cursor. If I drop it into console mode through a ctrl + alt + f1, it will let me log in. If I then try to run startx, I get a bunch of error messages that look like:
> (WW) PSB: No matching Device section for instance (BusID PCI:0@0:28:0) found
(WW) PSB: No matching Device section for instance (BusID PCI:0@0:28:1) found
(WW) PSB: No matching Device section for instance (BusID PCI:0@0:29:0) found
...
(EE) PSB(0): the stolenBase is:0x3f800000
(EE) PSB(0): screnIndx is:0;fbPhys is:0x3f800000; fbsize is:0x007df000
(EE) PSB(0): First SDV0 output reported failure to sync or input is not trainded!!!
FATAL: Module psb not found.
(EE) [drm] drmOpen failed.
(EE) PSB(0): [dri] DRIScreenInit failed. Disabling DRI.
(EE) [drm] Could not uninstall irq handler.
(EE) PSB(0): This driver currently needs DRM to operate.
Could someone give me some pointers here? I'm guessing I'm doing something really silly that's holding me back, but I can't figure out what. The install of poulsbo-driver-*D both complete without an error, and I made sure to add psb to the whitelist, and to add the video privledges. 

My only real goal is to have Ubuntu running (any version) with full hardware support. I'd really appreicate any help!

Thanks!

---

### Post by dimeified on 2009-05-13
Coincidentally yesterday a new kernel wanted to install on my intrepid, so i went for it, and x wouldn't start. I had to revert back. When i get home i will boot the newer kernel again and match my errors against yours.

---

### Post by tyroeternal on 2009-05-13
@ bcleveng: I am having the same issues.  There was another kernel update that seemed to knock the legs out from under my install yesterday.  Maybe it is time to move back to Jaunty if 2d is actually usable.

@ matthiasak & woodhouse: so you guys can confirm that 2d is working with jaunty now?

---

### Post by jackblow33 on 2009-05-13
2d working with Jaunty, just finish installing it. Install Jaunty desktop.iso, Update (41mb), grab the 2d driver from mobile PPA and you have Ubuntu 9.04 working.
Update: 
720p tested and working good with the clip I have tested(playback is like what I have with belmont), a problem I have is with the wireless network interface, online bandwidth test= 200 kb/s dl with the wireless and with the wired interface got around 1.6 mb/s.
As far as I know that's the only problem I have with Jaunty.
Youtube sd is good, Hd is unwatchable. 

Have restore my system with belmont finally. I have no real problem with this one, but Jaunty is close.

---

### Post by dimeified on 2009-05-13
hell yea jack, thanks for the info! When i get home from work i will try to upgrade my intrepid to jaunty via update manager then add the jaunty ppa repo's for the video.

---

### Post by javel404 on 2009-05-13
HI ,
i've just upgraded intrepid to jaunty , it boots faster blabla But it freezes 10 minutes after , it's not a full desktop install , a customize xfce install (not xubuntu) .
i notice i've lost one hour switching hardy/lpia to i386/intrepid with the 3-cell battery , can someone can post his lpia intrepid sources.list , i tried with netbook-remix intrepid repository ,it fails , it doesn't exist i think ?

---

### Post by dimeified on 2009-05-13
My intrepid install would freeze like that. If i pressed the power button for a second it would unfreeze and i would get the "logout restart shutdown" screen, and i would hit cancel and be back in business.

also during the initial install, sometimes it seemed like the progress bar would sit there, and i would  hit enter and then it would blast to 100% and finish what it was doing.

also, a couple times on boot i had that happen where the splash screen would sit, and the progress bar wouldn't move unless i hit escape.

Try to press the power button when it freezes and let me know what happens, because if your expiriencing the same problem then it isnt necessarily a jaunty issue.

---

### Post by tyroeternal on 2009-05-13
I've seen the same issues in intrepid.  Pressing the power button to unfreeze the system was getting extremely annoying.  I've also noticed the same issues with the system hanging during the system install or at boot.  Pressing any buttom seemed to get things moving again.

If you want to use lpia for jaunty you should install the lpia-alternate version from this page:  [http://cdimage.ubuntu.com/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/ports/releases/jaunty/release/)

---

### Post by chr15m on 2009-05-13
After working away at it all evening, the packages from jaunty ppa finally seem to be running ok on my Mini 12.

Had to install most things from here:
[https://launchpad.net/~ubuntu-mobile/+archive/ppa?field.series_filter=jaunty](https://launchpad.net/~ubuntu-mobile/+archive/ppa?field.series_filter=jaunty)

Use the libdrm-poulsbo1 and xserver-xorg-video-psb instead of libdrm2 (might see some errors from apt when you do the switch)

Had to make sure modules "drm" and "psb" were being loaded on startup - I used modconf to do that.

Finally I had to make a symlink as follows:
sudo ln -s /usr/lib/xorg/modules/libexa.so.xserver-xorg-video-psb /usr/lib/xorg/modules/libexa.so
as otherwise the exa module wasn't loading, causing X to fail miserably.

Doesn't seem super stable (pygame segfaulted which never happens), but it's sure nicer than the slow old intel driver was before. 3D works but I haven't run anything intensive.

---

### Post by matthiasak on 2009-05-14
Well I uninstalled all the poulsbo stuff adn then did the jaunty update. Everything completed fine.

I rebooted, made sure those updates were available, then installed the xserver-xorg-video-psb package. 

Jaunty runs flawlessly for me, no changing filenames, etc... boots and loads programs faster...

I really like the enw notification system. Fullscreen flash runs well, and video under VLC is muy bueno. 

Hope this helps!

btw, 3d support not available yet, as the AIGLX / DRI support and OpenGL packages have yet to be released, so no compiz or tuxkart yet :P

---

### Post by greggh on 2009-05-14
matthiasak, good to hear it. All that's important to me is good 2d and video. Glad to hear it works well.

---

### Post by AdamWill on 2009-05-14
I got the Ubuntu stuff rebuilt and working on Fedora, finally:

[http://www.happyassassin.net/2009/05/13/native-poulsbo-gma-500-graphics-driver-for-fedora-10/](http://www.happyassassin.net/2009/05/13/native-poulsbo-gma-500-graphics-driver-for-fedora-10/)

I don't have 3D acceleration up yet, but I'm hoping to get it going tomorrow for Fedora 10. Probably won't be possible for Fedora 11 until the Xpsb and Mesa stuff is available for Ubuntu 9.04.

---

### Post by tentwelveeight on 2009-05-14
I got it working too. Here's what I did:

Installed jaunty UNR from ubuntu.com using .img file (.iso didn't work for some reason)
Installed all updates with Update Manager
Added repos from matthiasak's post 
> [https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any](https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any)
There's a nice youtube tutorial on how to do this here:
> [http://www.youtube.com/watch?v=UUZOQsNo_ws](http://www.youtube.com/watch?v=UUZOQsNo_ws)
Then I just followed the guy in the youtube tutorial's advice and opened synaptic, clicked on the "origin" button, selected the new repo and marked the xserver-xorg-video-psb package for installation just like matthiasak said. It uninstalled a few packages and installed a few others. Then I restarted and had a full size desktop on reboot!

A few notes:
youtube indeed works fine under all scenarios except full screen HD
the ubuntu netbook launcher is still unusable, but I prefer the classic desktop anyways
scrolling in websites is faster, but there's still a bit of delay
I have 3 uninstalled packages waiting in the update manager. I'll install them after this post and report any problems.

My wife says she doesn't care and just wants the laptop back (but I think she's going to be very happy) Thanks y'all

---

### Post by tyroeternal on 2009-05-14
Does anyone have any idea about how lpia differs from i386 in practice?  Is it worth jumping on the lpia arch when there are fewer packages available?  Would using i386 and possibly building my own kernel be as good, or are there actual battery life/system speed differences that compel the use of lpia?

Big thanks to everyone spearheading the work on figuring out how to get our systems in working order.

---

### Post by fitzkarraldo on 2009-05-14
Does definitely Jaunty work well? Except 3D of course..
Any freeze like that reported in post #562 or any problem installing with the desktop or alternate .img?

---

### Post by optimistique1 on 2009-05-14
> **matthiasak said:**
> I have successfully installed the i386 version of intrepid :P  wasn't hard, use unetbootin or usb-creator to make the install USB and then boot. Everything went quickly.

simply do:
1) install intrepid desktop .iso
2) run any and all updates available (without changing software sources, etc)
3) add these two lines to /etc/apt/sources.list

```

deb http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu intrepid main

```

and then install the packages 'poulsbo-driver-2d' and 'poulsbo-driver-3d'

and voila! working compiz and everything! boots fast, works amazingly well, plus there's the option to upgrade to jaunty and such when the dirvers become available.

PLEASE NOTE: do NOT add sources for backports or proposed updates, they will f!*# the install and stability up and then it will crash and will force X into low-graphics mode. If you do this, press escape at the boot menu and choose the last kernel before the bad update. It will be fine to then boot into that kernel normally. remove the two incompatible kernel entries in /boot/grub/menu.lst to get it to automatically choose the "good" kernel.

Hi I would love to try this options as it sounds the most simply way.  However, when I try and install from the Intrepid live CD I get as far as the splash screen and cannot load 'X', so how did you get to the point where you got to the desktop to install the updates?
Thanks
Garry

---

### Post by optimistique1 on 2009-05-14
> **marduk667 said:**
> Hey you can use the standard iso, but you have to change the xorg.conf after boot, then restart gdm.



After this all the steps work!
I today have reinstalled my Mini12 with intrepid and it really works great, even better than the Dell-Image! I also can use the great functions of intrepid now (added the blueman from ppa so i can use networkmanager to connect to 3G via bluetooth)
Also the firefox seems to be faster and more stable, the X-Server also seems more stable for what i have seen for now. Suspend/Wakeup works perfect. Compiz is a bit slow so i switched it off for now, but it really works :)
It seems i now can work with the Mini12 as i wanted nearly half a year after buying it...


How do I get to the point where I can  change the xorg.conf and  restart gdm.  I get as far as the progress bar when I boot 8.10 Live CD then I get the balck screen with text on...

Please I hope someone cal help :-(

---

### Post by zim2dive on 2009-05-14
I thought I'd followed the thread, but maybe I missed something...

I downloaded the 9.04 UNR img and used win32diskmanager to copy to a USB stick...

I changed my boot to USB and get to the menu where I can choose langauge.. but then I drop into a busybox prompt when I try to boot from the liveCD(usb).. I wanted to try before installing...

Any hints?

thanks,
Mike

---

### Post by dimeified on 2009-05-14
> **zim2dive said:**
> I thought I'd followed the thread, but maybe I missed something...

I downloaded the 9.04 UNR img and used win32diskmanager to copy to a USB stick...

I changed my boot to USB and get to the menu where I can choose langauge.. but then I drop into a busybox prompt when I try to boot from the liveCD(usb).. I wanted to try before installing...

Any hints?

thanks,
Mike

afiak the success of jaunty installs has been with the i386 desktop installer. With this you do not need to edit xorg to install the system, the vesa mode worked for the installer on my mini12. unr is lpia based.

---

### Post by tyroeternal on 2009-05-15
> **optimistique1 said:**
> How do I get to the point where I can  change the xorg.conf and  restart gdm.  I get as far as the progress bar when I boot 8.10 Live CD then I get the balck screen with text on...

Please I hope someone cal help :-(

At this point I am not sure if installing Intrepid is a good idea.  There was an update that seemed to break the drivers for my system.  If you are intent on using Intrepid, since the video drivers do not work well, it would probably be better to use an alternate install rather than a live installer.


> **dimeified said:**
> afiak the success of jaunty installs has been with the i386 desktop installer. With this you do not need to edit xorg to install the system, the vesa mode worked for the installer on my mini12. unr is lpia based.

I believe the UNR is not lpia based, only the lpia-alternate.

---

### Post by zim2dive on 2009-05-15
Ah.. that did it... here's a blow-by-blow upgrade account...

ok, so I downloaded the *desktop* install, and used unetbootin on my Windows(work) laptop ([http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)) to put the ISO on a USB stick and booted to the "liveCD" version (after booting with F2 to change boot priority to USB)... 

things look good, so I run the installer... pick my language, keyboard, time zone, and tell it to use the full disk (I've got no love for keeping 8.04 around).. enter name/pwd info... and its off to the races... well, a pretty slow race really... maybe 15 minutes to install.  

Install finished.  Reboot.. connect to wireless (new dialog make much more sense than it did before).. go to System/Update manager and click on "Check"... get a list of a bunch of updates.... click on Install.... 15 minutes later that is done...added repos> deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main listed in post 569.. 

now to do the #@%#@% key thing (3 steps backward in user-friendly).. so I did watch the YouTube in 569.. copied and pasted the key into a file and imported via the Authentication tab...

As noted, click on the Origin button the left (very handy idea) and select the xserver-xorg-video-psb package and then installed and restarted.

System->Display is reporting 1200x800.

thanks to tentwelveeight and matthiasak (and everyone else that has contributed) !!

---

### Post by zim2dive on 2009-05-15
doing a little testing with my new Jaunty install...

The Daily Show is not really watchable even in a small window.

On Youtube, it seems ok at small window.. choppy at full screen.

I launched a terminal window and cranked up "top" to see how far YouTube was pushing...

I ordered the 1.3G single core model... what the heck does 115% cpu usage mean?!?! (this is Youtube normal size)

---

### Post by kdubya on 2009-05-15
> **zim2dive said:**
> 
On Youtube, it seems ok at small window.. choppy at full screen.

I launched a terminal window and cranked up "top" to see how far YouTube was pushing...

I ordered the 1.3G single core model... what the heck does 115% cpu usage mean?!?! (this is Youtube normal size)

Flash performance is so piss poor that the 1.3ghz atom can barely play youtube.  The same chip can play h.264 at 720p, fullscreen in mplayer.  I have no idea why adobe is not dedicating all of their flash resources to adding real hardware acceleration.

You are seeing 115% because of hyperthreading.  The OS sees the atom at two cores even though it is only one.

---

### Post by zim2dive on 2009-05-15
Jaunty update...

I tried hibernating... when I woke it up it crashes saying no 3D driver...

not critical for me.. just documenting.

---

### Post by KristinaK on 2009-05-16
I want to buy replacement to my year old Dell Mini Inspiron 12. What you suggest? I need 12 inch screen and ubuntu 9.04. Why I can only select XP and not Ubuntu? Why its not possible to customize it to 2GB of ram?

---

### Post by zim2dive on 2009-05-16
> **KristinaK said:**
> I want to buy replacement to my year old Dell Mini Inspiron 12. What you suggest? I need 12 inch screen and ubuntu 9.04. Why I can only select XP and not Ubuntu? Why its not possible to customize it to 2GB of ram?

Mini10 with the hi-res screen?

---

### Post by coleridge on 2009-05-16
A simple question: does anybody know, when the GMA500-driver-support-whatsoever will be implemented in a way, so that a simple installation of jaunty will directly lead to a fully functioning dell mini 12? 
Without actually having to follow any of the (very helpful) ways to make it function described here?

---

### Post by optimistique1 on 2009-05-16
> **zim2dive said:**
> Ah.. that did it... here's a blow-by-blow upgrade account...

ok, so I downloaded the *desktop* install, and used unetbootin on my Windows(work) laptop ([http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)) to put the ISO on a USB stick and booted to the "liveCD" version (after booting with F2 to change boot priority to USB)... 

things look good, so I run the installer... pick my language, keyboard, time zone, and tell it to use the full disk (I've got no love for keeping 8.04 around).. enter name/pwd info... and its off to the races... well, a pretty slow race really... maybe 15 minutes to install.  

Install finished.  Reboot.. connect to wireless (new dialog make much more sense than it did before).. go to System/Update manager and click on "Check"... get a list of a bunch of updates.... click on Install.... 15 minutes later that is done...added repos listed in post 569.. 

now to do the #@%#@% key thing (3 steps backward in user-friendly).. so I did watch the YouTube in 569.. copied and pasted the key into a file and imported via the Authentication tab...

As noted, click on the Origin button the left (very handy idea) and select the xserver-xorg-video-psb package and then installed and restarted.

System->Display is reporting 1200x800.

thanks to tentwelveeight and matthiasak (and everyone else that has contributed) !!


Hey buddy you're amazing, got the same results and now it all looks great - 9.04 in full swing.

Did you manage to get 3D drivers and if so how?

---

### Post by zim2dive on 2009-05-16
> **optimistique1 said:**
> Hey buddy you're amazing, got the same results and now it all looks great - 9.04 in full swing.

Did you manage to get 3D drivers and if so how?

Let me requote myself :) > thanks to tentwelveeight and matthiasak (and everyone else that has contributed) !!  I just followed their steps and kept a step by step log... 

I don't have 3D drivers, and don't see any in the repo's.

Unscientifically I think my boot time is slower with 9.04 desktop.  Also can't stand the keyring for my wireless password.. off to research how to disable that....

---

### Post by tentwelveeight on 2009-05-16
> **zim2dive said:**
> Also can't stand the keyring for my wireless password.. off to research how to disable that....

I posted a fix for this issue a little while ago. It's quite easy. Here you go:

[http://ubuntuforums.org/showthread.php?t=1138099]("http://ubuntuforums.org/showthread.php?t=1138099")

Good Luck! -joe

---

### Post by sadata on 2009-05-16
> **coleridge said:**
> A simple question: does anybody know, when the GMA500-driver-support-whatsoever will be implemented in a way, so that a simple installation of jaunty will directly lead to a fully functioning dell mini 12? 
Without actually having to follow any of the (very helpful) ways to make it function described here?

This looks very promising!

[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-kernel-source/]("http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-kernel-source/")

---

### Post by TomaszC on 2009-05-17
> **sadata said:**
> This looks very promising!

[http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-kernel-source/](http://ppa.launchpad.net/ubuntu-mobile/ubuntu/pool/main/p/psb-kernel-source/)

So, to sum up this longish thread - is there an easy way to have Ubuntu 9.04 running on mini 12 using the native resolution (1280x800)?

Could someone competent summarize needed steps?

---

### Post by zim2dive on 2009-05-17
Any battery and/or speed tips for Jaunty?  ie.  still trying to figure out how to turn off bluetooth (but not wifi).. I'm not using it. no sense in wasting the power... what is the "Dell Hardware Switch" checkbox under the BT prefs?

Fn+F2 doesn't seem to do anything? (the other Fn keys seem to work)

EDIT: my own contribution... for Firefox.. install the Greasemonkey add-on.. then install this script; [http://userscripts.org/scripts/show/38994](http://userscripts.org/scripts/show/38994) to force all Flash on web pages to default to low quality... save some CPU cycles that way...

EDIT2: credit to tyroeternal.. see [http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html](http://www.ubuntumini.com/2009/04/aircraft-manager-for-ubuntu-904.html) for a jaunty compatible aircraft manager to turn the radios on/off

EDIT3: found this tutorial to speed up and increase screen real estate for Firefox: [http://www.ubuntumini.com/2008/11/customizing-firefox-for-netbooks.html](http://www.ubuntumini.com/2008/11/customizing-firefox-for-netbooks.html)

---

### Post by dimeified on 2009-05-17
> **TomaszC said:**
> So, to sum up this longish thread - is there an easy way to have Ubuntu 9.04 running on mini 12 using the native resolution (1280x800)?

Could someone competent summarize needed steps?

it can't really get any easier than install the desktop iso, update, then add the repos and apt-get install drivers.

---

### Post by danboid on 2009-05-17
Just when I thought we almost had this mess sorted out...

Anyone who has read this thread will know that I have been successful in getting compiz running nicely under Intrepid (desktop) i386 on my Dell Mini 10- which of course requires both the pouslbo 2D and 3D drivers to be installed and working- and hence I know this to be possible. I know that the kernel I was using when I had compiz and DRI working was the 2.6.27-7-generic but sadly I didn't take note of the pouslbo/psb driver and module version numbers, which I'm now regretting as I am currently unable to get the current poulsbo drivers to work at all so I'm wondering if they got updated since I last installed and broke mini 10 support? SOMETHING has been updated and stopped psb graphics working under Mini 10 Intrepid i386.

I ended up doing a re-install trying to work my way round a dependency conflict that the poulsbo 3D driver has with libgl1-mesa-dev. When I first installed Intrepid on my mini 10 I installed the 3D gfx driver before I tried compiling any QT4 or KDE4 apps, both of which require you have libqt4-dev installed, which in turn depends on libgl1-mesa-dev. However, you will find that apt doesn't let you install libqt4-dev or I should imagine any other package which might require libgl1-mesa-dev as this conflicts with libgl1-mesa-dri-psb which is a dependency of poulsbo-driver-3d. So, I decided to re-install but this time I installed all the QT/KDE and GNOME/GTK dev stuff I'd need first and then discovered that apt wouldn't let me install poulsbo-driver-3d because it depends on libgl1-mesa-dri-psb which conflicts with libgl1-mesa-dev which is a dependency of libqt4-dev! Barggh!!

I can still install poulsbo-driver-2d (xserver-xorg-video-psb 0.18, xpsb-glx 0.11, psb-firmware 0.24 atm) from

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) intrepid main

under the latest intrepid i386 without any errors but X doesn't even begin to start with that installed. I can use X unaccelerated at 800x576 but with this latest combination of packages, poulsbo-driver-2d installed and with both 2.6.27-14-generic and 2.6.27-7-generic kernels booting only ever gets as far as saying something like:

setting Advanced Power Management level to 0xxx (xxx) [ OK ]

Then you have no option other than rebooting and removing poulsbo-driver-2d via recovery mode root shell.

So, has anyone else got compiz working on intrepid i386 right now- pref. on a mini 10? If so, could you please share the output of

dpkg --list '*psb*'

and 

uname -a

and tell me of any video voodoo you may have had to perform too please!

---

### Post by TomaszC on 2009-05-17
> **dimeified said:**
> it can't really get any easier than install the desktop iso, update, then add the repos and apt-get install drivers.

Which repos exactly?

So, if I want to run Ubuntu 9.04 on mini 12, I should:

1) install Ubuntu 9.04 from a CD/DVD or tftp

2) add this repository:

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

3) install all packages listed here (or not all? which ones?):

[https://launchpad.net/~ubuntu-mobile/+archive/ppa?field.series_filter=jaunty](https://launchpad.net/~ubuntu-mobile/+archive/ppa?field.series_filter=jaunty)

4) do I have to do any changes to xorg.conf?

5) anything else?

---

### Post by pistoncito on 2009-05-17
@TomaszC

The only item you don't have to forget is make an update of every package before 2nd point of your list.

Install Ubuntu 9.04 and with small and ugly resolution make an update. Then you could add the mobile repository and install libdrm1-poulsbo and xserver-xorg-video-psb 

It need to unistall drm2 or something like that. Then you just need to reboot. I don't have to change anything at xorg.conf. I used UNR image, but when i make the final install i will use desktop image (now i installed it in another partition).

Only a doubt, do you make a swap partition? I made it, but i don't know if it's good or bad.

---

### Post by TomaszC on 2009-05-18
> **pistoncito said:**
> @TomaszC

The only item you don't have to forget is make an update of every package before 2nd point of your list.

Install Ubuntu 9.04 and with small and ugly resolution make an update. Then you could add the mobile repository and install libdrm1-poulsbo and xserver-xorg-video-psb 


I made an installation using PXE/tftp (where I chose "netbook remix" option), which I think takes care of installing everything fresh.

But the resolution was never small and ugly for me - every distro I tried, including Ubuntu, displayed with 1024x768 )unless that's what you're referring to as ugly; although I saw post in this thread mentioning resoultion of 800x576 or something like that).


> **pistoncito said:**
> 
It need to unistall drm2 or something like that. Then you just need to reboot. I don't have to change anything at xorg.conf. I used UNR image, but when i make the final install i will use desktop image (now i installed it in another partition).

Only a doubt, do you make a swap partition? I made it, but i don't know if it's good or bad.

Yes, I made a 1.2 GB swap image. I'm not sure if it's not needed for suspend to disk?

---

### Post by pistoncito on 2009-05-18
After using Jaunty for some days, all works fine, but i still feel that the original belmont with UNR packages has more speed. I was writing something in geany (a text editor) and it's speedest with 8.04 than this 9.04. I don't know if 3D has importance or it's difference between lpia and 386. But it's nice to see Jaunty working at Mini 12.

---

### Post by tyroeternal on 2009-05-18
Does anyone know if the poulsbo 2d bits would work with a custom built 2.6.30 kernel that is slightly trimmed down and made for our processor?  Even if it only works for the current kernel in Jaunty, it would be nice to have a slightly smaller kernel built for our system.  Are there any of the more skilled users that could hand out a trimmed down kernel .deb, or is this going to have to be something everyone has to do for themselves?

I do not know a ton about how well this could be done, but maybe someone could put up a ppa with trimmed down kernels for the Mini 10/12.

---

### Post by Flonak on 2009-05-19
Here are my tutorial for Jaunty on Mini 12 : [http://www.tipsandthoughts.com/?p=4](http://www.tipsandthoughts.com/?p=4)

Thanks to all of you guys

---

### Post by johncallen on 2009-05-19
Great tutorial.  Works very well on my mini 10.

As you said 3D performance is horrible.  

A few graphics performance test
Hulu takes about 50-75% CPU usage when playing video.
glxgears reports 80-100 FPS while using 50-60%CPU.
glxinfo reports that the software raster is in use.

My 2 cents...Intel dropped the ball on this.  I find the Intel / Imagine technologies link strange since Intel is such a advocate for open source and Imagine is clearly not.

Anyone know who is actually maintaining the Poulsbo kernel drivers?

---

### Post by zim2dive on 2009-05-19
> **johncallen said:**
> Great tutorial.  Works very well on my mini 10.

As you said 3D performance is horrible.  

A few graphics performance test
Hulu takes about 50-75% CPU usage when playing video.
glxgears reports 80-100 FPS while using 50-60%CPU.
glxinfo reports that the software raster is in use.

I didn't think Hulu would be watchable.. Usually its worse than video from thedailyshow.com and that drops to 1-2fps framerate (audio is ok... video is not).. and until Flash gets GPU offload, I don't think it will improve... and I don't expect to see GPU offload (ala VDPAU) for Intel.. so I think Flash video on Atom is always going to blow :(

---

### Post by johncallen on 2009-05-19
So after installing and getting 9.04 to work on the mini 10 (minus reasonable 3D performance), I thought I would dual boot and add a 8.10 install.  I follow all the instructions I found in this thread.  the result is that same as a few others.  I get the error reporting that "this driver currently needs DRM to operate".  I tried to add a module entry in xorg.conf to load drm, but got same failure.  

So it looks like GMA500 support is broken in 8.10.

Guess I'll hope that 3D support in 9.04 arrives soon.

---

### Post by zim2dive on 2009-05-19
> **johncallen said:**
> So after installing and getting 9.04 to work on the mini 10 (minus reasonable 3D performance), I thought I would dual boot and add a 8.10 install.  I follow all the instructions I found in this thread.  the result is that same as a few others.  I get the error reporting that "this driver currently needs DRM to operate".  I tried to add a module entry in xorg.conf to load drm, but got same failure.  

So it looks like GMA500 support is broken in 8.10.

Guess I'll hope that 3D support in 9.04 arrives soon.

(do we get red/blue glasses??  just kidding)...Might be a thread tangent.. but as someone who is still learning.. what is 3D? 

I only know I need/want 3D b/c Hibernate seems to want it (which makes no sense to me, except some developer must have decided they wanted fancy graphics for what is otherwise seems a non-graphical function)

---

### Post by dothedog on 2009-05-20
Hi all, I have been following this thread for a while now and have used a bunch of the recommendations. I actually have a Kohjinsha SC3 but it has mostly the same hardware as the Mini 12. In any event, I have gotten Jaunty on with 2D support but here is my question: has anyone gotten mplayer-vaapi working in Jaunty? I keep getting no video with the latest version (mplayer-vaapi-20090423.tar.bz2). I did have it working with a February build and Hardy...

---

### Post by TomaszC on 2009-05-22
And by the way, has anyone been able to get bluetooth to work with Jaunty / 9.04 on mini 12?

---

### Post by trgreerca on 2009-05-23
The information here is great.  Thanks to everyone who has contributed.  I've kicked off the upgrade process...

I can do without the 3D drivers for a while. But it will sure be nice when they are available.

What is the latest forecast on their arrival?

---

### Post by SQuark on 2009-05-23
Can someone explain to me, if we've only got 2D support, how come the Metacity compositor *does* work on my Mini 10 running Jaunty?

---

### Post by dimeified on 2009-05-23
Do you mean compiz? Metacity is just a window decorator.

---

### Post by michael37 on 2009-05-23
I got my Mini 12 about a week ago and I noticed that a lot of information in this thread is outdated.

I am wondering what's the best version for Mini 12 as of late May 2009 -- please vote [thread=1167915]in the poll here[/thread].

---

### Post by matthiasak on 2009-05-23
> **michael37 said:**
> I got my Mini 12 about a week ago and I noticed that a lot of information in this thread is outdated.

I am wondering what's the best version for Mini 12 as of late May 2009 -- please vote [thread=1167915]in the poll here[/thread].


Well if people would read through the whole forum, you will find a multitude of information here that is in relative terms not outdated. 

Until the packages are released here ([https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any]("https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa?field.name_filter=psb&field.status_filter=published&field.series_filter=any")) denoting Jaunty GLX and 3D support, Jaunty is stuck with 2D and video acceleration. Intrepid actually has fully supported 2D and 3D (meaning Compiz works, too). You can use these steps to install Intrepid:

Note these are for the mini 10. You are welcome to try this on the Mini 12, too. I think it should work for all computers/netbooks with Poulsbo if you follow the directions exactly. Skipping a step and going straight to installing the 3d and 2d drivers will not work for everyone.

1) install the desktop i386 .iso OR the lpia, it's your own choice, you won't really notice nay difference in performance between either (lpia is a modified i386 package with compiler tags that are supposed to be optimized for Atom, but I found i386 ran great...)
2) install updates FIRST (do NOT add backports or proposed sources)
3) restart
3) use the repos available at ([https://edge.launchpad.net/~ubuntu-m...ies_filter=any](https://edge.launchpad.net/~ubuntu-m...ies_filter=any)) to install these metapackages: 'poulsbo-driver-2d' and 'poulsbo-driver-3d'
4) Use Gedit to edit the file '/usr/bin/compiz' : in the "whitelisted drivers line", add 'psb' to the list
5) save and restart
6) turn on/off any effects you see fit with CCSM or System > Appearance > Effects


Compiz and Desktop Compositing should work fine for you now, no matter what netbook with GMA 500 you have. The driver packages will automatically configure your screen size, so don't bother changing the resolution in xorg before you install the packages.

---

### Post by SQuark on 2009-05-24
> **dimeified said:**
> Do you mean compiz? Metacity is just a window decorator.

No, I did mean Metacity.

Some Googling around has taught me that Metacity's compositor works on the CPU instead of the graphics card. So if you want compositing in Jaunty on your Mini, try it! It works for me. :)

Here's the command to turn it on:
```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```
and off again:
```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```

---

### Post by danboid on 2009-05-24
I haven't used my mini 10 in a couple of weeks now - I'd take it back if I could but I bought it with XP pre-installed so saying that it "doesn't work well with Linux" sadly isn't a good enough reason to return it :(

There have been precisely zero replies to my question/problem with trying to install libqt4-dev alongside the poulsbo-3D driver under 8.10 - am I really the only person here who needs to be able to compile QT4 and KDE4 apps on my mini AND have 3D accel, no matter how weedy it may be? Weedy it may be but it is good enough for what I need it for.

I said in my last big post to this thread (#591) that I was pretty sure it was the 2.6.27-7 I was running when I had compiz working but I since realised (after looking at the menu.lst on my other 8.10 machine) that it could've also been 2.6.27-11 that I was running. I can't be bothered re-installing Intrepid again just to find find out that yes, compiz is truly borked under kernel/ config version x.

Has anyone got compiz working on a mini 10 with a fully up-to-date Intrepid install (2.6.27-14 kernel etc.)??

---

### Post by R_U_Q_R_U on 2009-05-25
See this:

[http://ubuntuforums.org/showthread.php?t=1156353&page=2&highlight=Dell+Mini+10](http://ubuntuforums.org/showthread.php?t=1156353&page=2&highlight=Dell+Mini+10)

Great news! The Dell Mini 10 now runs on Ubuntu 9.04 at full nominal resolution of 1024  x  576!
 

What has happened is that the [Ubuntu Mobile Team]("https://edge.launchpad.net/%7Eubuntu-mobile") has compiled and packaged kernel modules, X.org drivers, libraries to interface to kernel DRM services, etc. etc. for the Poulsbo chipset and made them available on their PPA.

---

### Post by danboid on 2009-05-26
3D?

HDMI?

Otherwise, good news, thanks!

---

### Post by woodhouse on 2009-05-26
In my case,
- No 3D (!!!)
- Yes HDMI

---

### Post by danboid on 2009-05-26
I've just installed jaunty alternate i386 onto my mini 10 without a hitch, although the psb driver still needs a lot of work.

There will be people on here who have very minimal video requirements who will basically only require that they can get the full res out of their screen- well for those jaunty has arrived as all is working fine 'cept advanced graphics features in that atm there is no Xv (Video accel.- full screen youtube etc. is too jerky to be watchable), glxinfo does say Direct Rendering is available but there is no 3D working 3D accel yet as far as I can see as compiz doesn't work, even after adding psb to the Whitelist and enabling 3D accel privs for your user and some simple 3D games (foobillard, gunroar) that I've tested have verified that there is no 3D accel at present.

The good news, as has already been hinted at, is that HDMI is now working better than ever before on the mini 10 in that I get a 1280x720 image on my TV as soon as X starts (I need to log out if already logged in for the HDMI picture to come up). Unfortunately, this still has problems:

* No sound! I've checked both alsamixer and paman but both only see an analogue HDA intel alsa device. I can get sound coming out of my mini 10 but not via HDMI cable through the TV.

* Picture doesn't fit. I've not tried experimenting with the various config options xrandr offers to resize and reposition the HDMI display yet but I cannot see the full desktop on my TV, I'd guess that about 10-20 pixels round the edge of the screen are being obscured. I was hoping my TV would offer an 'auto-zoom/ position' function but it doesn't sadly. Can you see your full desktop on your HDMI screen without any manual adjustment woodhouse, anyone else? 

There are basically no configuration options available for adjusting displays available under GNOMEs screen config tool. I know suse have a good graphical display config tool as part of YasT that does what I require but is there not a better xrandr GUI available to Ubuntu/Debian/GNOME users?

Playing with external displays under Jaunty/GNOME has only highlighted to me that GNOME still doesn't handle the whole deal too well as it normally results in your GNOME panel icons getting moved about and their order messed up. I hope GNOME 3 will solve this problem.

---

### Post by subslug on 2009-05-26
> **danboid said:**
> I haven't used my mini 10 in a couple of weeks now - I'd take it back if I could but I bought it with XP pre-installed so saying that it "doesn't work well with Linux" sadly isn't a good enough reason to return it :(


We ordered ours from Dell With XP and got sent a model with Vista, I would be dancing if I could get XP to install happily on this thing for her. Vista is just too damn slow. I can get Xp all done except for the video drivers, something is terribly wrong with the drivers for this device under XP.

I had the same experience you had with installing the poulsbo drivers on Intrepid. It hangs at the same screen mentioned in your earlier post. So, I was able to fix Intrepid with the partition editor, amazing what that tool can fix.  [-o<
NOW..I'm going to follow the steps and give Jaunty a try, I really hope this is the fix because I've spent far too much time trying to make joy out of this Dell crap.

For anyone interested, at the same time she bought this Mini 12 I bought the Asus 1000HE and I've not jumped through any hoops installing Linux on that system. It's so easy it's funny. Not to mention it runs as if Linux was meant to be on it. Installs easy, sound works, graphics work, wireless works, Nic works, resume/suspend works.
It even gets a lot more battery life, sure the screen is a little smaller but I would return this Dell for another ASUS in a second if could.

---

### Post by danboid on 2009-05-26
HDMI audio works!!

For those few programs that actually care about what setting you've chosen under System -> Preferences -> Sound then you've got to choose

HDA Intel MID INTEL HDMI (ALSA)

For all your sound settings, that will then make at least Totem/'Movie Player' use your HDMI screen to output the sound.

Totem, like Flash, gets really jerky when you try playing any videos full screen with the current jaunty psb driver, so instead I'm using smplayer to play video files on my hdmi screen as smplayer lets you select the alsa hdmi audio output, which firefox and vlc can't see. To get hmdi audio output working under smplayer, push CTRL+P for the prefs., click on the 'Audio' tab and then choose 

alsa ( 0.3 - HDA Intel MID )

For the 'Output driver' option then choose Apply / OK

So I have actually seen every bit of hardware (at least almost fully) working under Linux on my Mini 10 now, just not all at once and under the same version. I have seen 3D and accelerated video working under belmont/Hardy, compiz working under intrepid and now I've seen a nigh on 100% working HDMI under Jaunty- someone just needs to pull the right strings now and we cold have a fully working driver under Jaunty soon, I'd hope!

Can anyone tell me how I might be able to get the sound output by flash under FF to be redirected to the alsa HDMI output and if there is a better tool for Ubuntu users wanting to calibrate their displays via gui than the one that comes with GNOME?

---

### Post by subslug on 2009-05-26
I pretty much got everything working on Jaunty on the Dell Mini 12, with the one exception of Youtube videos but, honestly...life was probably better before Youtube anyway.  ;)

I was a little surprised that suspend even works. Usually that's like a unicorn on anything Dell makes, there's rumors but no-one's ever really seen it.

Note to anyone reading through this epic thread....skip the Intrepid install and just go straight to Jaunty. It runs much better anyway.

---

### Post by danboid on 2009-05-27
I've just been testing a few SD ie DVD res MP4 files under smplayer with the current jaunty psb driver and I was surprised to see it played them very smoothly, despite xvinfo insisting there is no video accel to speak of yet. Not tried playing any HD clips yet but us Mini 10 owners are limited to 1280x720 anyway- I'll have to track down some footage encoded at that res and see how it handles playback of that.

OK, so I still can't see all of my screen atm the mo and theres no 3D accel yet but my Mini 10 has now vastly improved its worth as a Linux media playback device as most of the vids I have are only SD res or below anyway.

I've tried using the intrepid xpsb-glx with jaunty- X still works and it doesn't seem to choke on the x 1.5 compiled xpsb module. It does have the positive effect of getting rid of the 'xpsb module missing' or whatever error message you get every time you hibernate if you install and xvinfo does then report that xv accel is working but trying flash would suggest otherwise and 3D accel certainly doesn't work using the intrepid xpsb.so. 

So the question is when are we going to see an X 1.6.x friendly Xpsb blob arrive as I hear Dell are sticking with Hardy for a while yet, maybe until the next LTS release of buntu?

---

### Post by tyroeternal on 2009-05-27
Dell sticking with LTS releases would not be surprising.  Their focus seems to be on providing a simple, stable system for the preinstalls.  Given the wait and test nature of even security updates to Hardy they seem to indicate that they are more focused on simplicity than new features.  Obviously, upgrading seems to be an "at your own risk" kind of endeavor around here.

---

### Post by tyroeternal on 2009-05-29
Is there anyone using Jaunty + Ubuntu-Mobile PPA with the proposed packages turned on?  I recently re-installed my system with lpia and tried using the proposed packages, but x would not start properly.  Anyone else have that issue?

---

### Post by floquet on 2009-05-29
Yesterday I installed Jaunty (386) and PPA for Ubuntu mobile. My Dell mini 12 seems to work fine except for the 3d

---

### Post by tyroeternal on 2009-05-29
> **floquet said:**
> Yesterday I installed Jaunty (386) and PPA for Ubuntu mobile. My Dell mini 12 seems to work fine except for the 3d
What I am curious about is if there is an update in the proposed repository that breaks the system.

---

### Post by floquet on 2009-05-31
> **tyroeternal said:**
> What I am curious about is if there is an update in the proposed repository that breaks the system.

As per a previous recommendation for Intrepid I have the proposed and backports repositories disabled.

---

### Post by johncallen on 2009-06-01
[tyroeternal]("http://ubuntuforums.org/member.php?u=302181"), I added proposed and updated as well.  I got the same result as you.  Fortunately it left the previous kernel installed.  When I boot from that, I am back to the working 2D state.

---

### Post by teatimest on 2009-06-07
Since one of the bottlenecks on this laptop is the slow hard drive, does anyone tried to use ext4 to improve the performance?

---

### Post by tyroeternal on 2009-06-08
I'm using ext4 at the moment, but I'm not aware of any particular performance improvements, though I've read that there are some.  I just chose it for the new car smell.

---

### Post by teatimest on 2009-06-09
> **tyroeternal said:**
> I'm using ext4 at the moment, but I'm not aware of any particular performance improvements, though I've read that there are some.  I just chose it for the new car smell.

Thanks!

I tried to convert ext3 to ext4 anyway. You are right. I don't feel significant improvement. Boot time got a little shorter, though.

---

### Post by woodhouse on 2009-06-12
I'm using PSB module (2D) but the system is very slow, compared with Windows.

This depends from the missing 3D module? The 3D module was already present on previous Ubuntu versions? It's so complicated to pack the 3D version of PSB?

I don't understand... Someone can help me?

---

### Post by tyroeternal on 2009-06-12
Unfortunately the old video driver stuff does not work for the newer kernels.  There is work (or rumor of work) being done to get the system to work properly and add 3D support, but it is more than likely a long ways off still.

---

### Post by woodhouse on 2009-06-16
So if I use the "new" Jaunty Ubuntu-release, but I install the previous Intrepid linux-kernel (2.6.27), I can use the previous PSB drivers, including 3D?

I'll try!

---

### Post by woodhouse on 2009-06-16
Yes, I confirm you, folks! To use DELL Mini 10/12, you should

1) install (K)UBUNTU 9.04 (Jaunty);
2) add INTREPID repositories for PSB on PPP, and install its;
3) add INTREPID ubuntu repositories to downgrade the following:
3a) the kernel 2.6.27.xxx;
3b) X.org server 1.5.2.xxx;

My conclusion is:
- DELL very very bad (chosing Poulsbo)!
- Debian Pacakage System is great!

---

### Post by wmd_172 on 2009-06-16
so to confirm Woodhouse,

you now have Jaunty runnning on your mini 12 with 3d (!!!!!!!!!) ?

---

### Post by teatimest on 2009-06-16
Do you see any difference in video acceleration? Would this allows me to watch shows on Hulu? If so, I would like to try this.

> **wmd_172 said:**
> so to confirm Woodhouse,

you now have Jaunty runnning on your mini 12 with 3d (!!!!!!!!!) ?

---

### Post by wmd_172 on 2009-06-17
Sorry, I was asking it works...

Id like to upgrade.

I can watch Hulu perfectly in Hardy...

Do we have 3d drivers for Jaunty yet?

---

### Post by woodhouse on 2009-06-17
Yes, I confirm.. Even if the process is quite complicated, you can use 3D drivers inside Jaunty (9.04), by using old X.org 1.5.2 (that one on Intrepid repositories)...

The general graphic performances improve!

---

### Post by wmd_172 on 2009-06-17
Do you see a performance increase using Jaunty vs Hardy?

---

### Post by teatimest on 2009-06-18
So, I followed the instruction and installed 2d and 3d poulsbo driver from Intrepid Moble PPA.

Do I need 2.6.27 kernel or is X.org 1.5.2 is sufficient for the 3D driver to work? Do you have the Intrepid repository for kernel and Xorg? I can't find it... And once I install older xorg, how can I use older one instead of new one?

Oh, one more question. Does having 3D driver working improve video acceleration? Or is it 2D driver?

Why installing graphic drivers has to be this hard....
I just want to have a working system.
I loved my Dreamcast, but oh my... 
Intel should buy Imagination Technology and make the drivers open!
**** you, Dell and Intel!!!

> **woodhouse said:**
> Yes, I confirm.. Even if the process is quite complicated, you can use 3D drivers inside Jaunty (9.04), by using old X.org 1.5.2 (that one on Intrepid repositories)...

The general graphic performances improve!

---

### Post by pachistano on 2009-06-18
> **woodhouse said:**
> Yes, I confirm you, folks! To use DELL Mini 10/12, you should

1) install (K)UBUNTU 9.04 (Jaunty);
2) add INTREPID repositories for PSB on PPP, and install its;
3) add INTREPID ubuntu repositories to downgrade the following:
3a) the kernel 2.6.27.xxx;
3b) X.org server 1.5.2.xxx;

My conclusion is:
- DELL very very bad (chosing Poulsbo)!
- Debian Pacakage System is great!



guys... i'm lost.
I really need help because i'm getting insane, please.
could anybody provide help on how to do points 2 and 3?
i cannot find repositories, cannot add old repo and i get lost in the net!
it's a week 24/7 I'm trying to fix my ubuntu dell jauntry... this post fix both audio HDMI and 3D? 
i already have 2D working and "normal audio" too but no compiz and 3d effects.
also, I add, when trying to start compiz I get
root@paranoia:/var/log/gdm# tail -f \:0.log 
(EE) PSB(0): screnIndex is:0;fbPhys is:0x3f800000; fbsize is:0x007df000
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(EE) PSB(0): has_fbdev is true
(EE) AIGLX error: dlopen of /usr/lib/dri/(null)_dri.so failed (/usr/lib/dri/(null)_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!

what a monster did dell create?!?

---

### Post by 2oh1 on 2009-06-18
I too would love to see someone post a detailed how-to for those of us who are new to Ubuntu.  I'd love to give it a shot, but I'm definitely an Ubuntu newbie (my main computer is a Mac).

---

### Post by teatimest on 2009-06-18
I think the step 2) is 
Add Intrepid PPA in source list

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) intrepid main 
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) intrepid main 

To add them in the list, go to System > Administration > Software Sources, then select Third Party Software Tab, then Add those two lines. Update the database in Synaptic and find poulsbo-driver-2d and poulsbo-driver-3d. I installed them. 

For step 3) I think I have to find Intrepid repository that contains older kernel and Xorg.

I converted ext3 to ext4. Do you think there might be problem using ext4 if I downgrade kernel and Xorg. 2.6.27 should be ok with ext4, right?

Ext4 Wiki says:
>   For people who are running Debian

In Debian Lenny (Testing), the following current packages provide ext4 support:

    * ext4dev module in the linux-image package (2.6.26-10)
    * e2fsprogs (1.41.3-1) 

It should be noted that the stock 2.6.26 ext4 has problems with delayed allocation and with filesystems with non-extent based files. So until Debian starts shipping a 2.6.27 based kernel or a 2.6.26 kernel with at least the 2.6.26-ext4-7 patchset, you should mount ext4dev filesystems using -o nodelalloc and only use freshly created filesystems using "mke2fs -t ext4dev". (Without these fixes, if you try to use an ext3 filesystem which was converted using "tune2fs -E test_fs -o extents /dev/DEV", you will probably hit a kernel BUG the moment you try to delete or truncate an old non-extent based file.) 

---

### Post by gtaluvit on 2009-06-18
OK, so adding the ubuntu-mobile PPA and intrepid lines to the sources is easy enough. What packages did you do a "Force Version" on in order to get everything right?

---

### Post by bluepenny65 on 2009-06-18
I have added all repositories I can from so many recommendations online but still can't get to view online videos or youtube properly. The thread is so long and I get lost in so many help offered in here...can someone help with simplest recommendations of repositories to download (I know it will still be slow anyway without the 3D).

---

### Post by gtaluvit on 2009-06-19
There are multiple approaches which is why it's so complicated. The general consensus is:

[LIST]
[*]Dell Hardy: Works out of the box with everthing
[*]Intrepid with Ubuntu Mobile PPA (Intrepid): SHOULD work out of the box with everything though I haven't tested it but others in this thread have.
[*]Jaunty with Ubuntu Mobile PPA (Jaunty): Gives proper resolution in 2D, supports cpu intensive software compositing. No 3D (This is how I run)
[*]Jaunty with Ubuntu Mobile PPA (Intrepid) and Intrepid main/restricted/security/updates/et al with forced versioning of a 2.6.27 kernel and 1.5.2 Xorg should give everything.
[/LIST]

All of this is even more complicated depending on if you're using i386 or lpia.

This new thing with the forced versions was JUST found and woodhouse seems to be the only one with it working so far. I'd like to know what he forced back because when I started trying it, it wanted to uninstall a whole lot. Anyways, if you want a netbook that works, you'll need to use Dell's Hardy until a solution to this Poulsbo (Bad Dell!!!) issue is solved.

---

### Post by woodhouse on 2009-06-20
> **gtaluvit said:**
> There are multiple approaches which is why it's so complicated. The general consensus is:

[LIST]
[*]Dell Hardy: Works out of the box with everthing
[*]Intrepid with Ubuntu Mobile PPA (Intrepid): SHOULD work out of the box with everything though I haven't tested it but others in this thread have.
[*]Jaunty with Ubuntu Mobile PPA (Jaunty): Gives proper resolution in 2D, supports cpu intensive software compositing. No 3D (This is how I run)
[*]Jaunty with Ubuntu Mobile PPA (Intrepid) and Intrepid main/restricted/security/updates/et al with forced versioning of a 2.6.27 kernel and 1.5.2 Xorg should give everything.
[/LIST]

All of this is even more complicated depending on if you're using i386 or lpia.

This new thing with the forced versions was JUST found and woodhouse seems to be the only one with it working so far. I'd like to know what he forced back because when I started trying it, it wanted to uninstall a whole lot. Anyways, if you want a netbook that works, you'll need to use Dell's Hardy until a solution to this Poulsbo (Bad Dell!!!) issue is solved.

Very good report!

Theorically you need only to 
1) add these repositories to JAUNTY:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) intrepid main
2) install psb modules;
3) downgrade xserver-xorg and linux-image.

But I should admit that the last step is quite complicated, especially if you use some DPKG frontend like 'aptitude'... For the kernel, there are no problems. But for XOrg, if you try to downgrade it, APT enforces you to uninstall many other packages (including KDE/GNOME..). So for me the solution was to downgrade first the "sub"-packages of xserver-xorg and finally xserver-xorg itself.
To downgrade a packages you need to launch the command:

apt-get install xserver-xorg/intrepid

---

### Post by gtaluvit on 2009-06-21
Well, I confirmed in lpia that woodhouse's method does work. I had to Pin most of the xserver packages and reboot with the 27 kernel and I had 3d working. Unfortunately, the cpu usage of X was pegged at 100% and although I could get 3d (tested by Diablo II actually working under Wine) it was terribly slow. Glxgears ran about 300 fps (as opposed to 30 in non-accelerated jaunty). Still, the need to pin all the packages and the HUGE headache in reverting back (learn to love dpkg-divert) I'm going to stick with Jaunty with UM Jaunty until they have 3d.

---

### Post by pachistano on 2009-06-21
> **gtaluvit said:**
> Well, I confirmed in lpia that woodhouse's method does work. I had to Pin most of the xserver packages and reboot with the 27 kernel and I had 3d working. Unfortunately, the cpu usage of X was pegged at 100% and although I could get 3d (tested by Diablo II actually working under Wine) it was terribly slow. Glxgears ran about 300 fps (as opposed to 30 in non-accelerated jaunty). Still, the need to pin all the packages and the HUGE headache in reverting back (learn to love dpkg-divert) I'm going to stick with Jaunty with UM Jaunty until they have 3d.


i tried to do the same (installed version is 9.04 as told before and dell mini 10), but synaptic mixed to apt is an hell in forcing packets version.
in my etc/apt/preferences i forced to 8.04 every packet 
then...
xorg: I had first to remove the packet 1.7  and then install 1.5.2, the *only* way for me to have a real switch of version 
about the kernel..
I found only the packet named "kernel-core"matching the version 1.2.27 mentioned and did the same as xorg
i also found the psb packet in .deb version 0.18 and rod about that using  woodhouse's configuration, psb packet version needed is <=0.20. installed it and than reboot but i got a prompt insted of X!
btw, i need my laptop as he needs me and also u notice me that cpu is 100%, so i give up and going to reinsall ubuntu dell 9.04 and use it without 3d. 

one question to everbody: is your wireless working allthetime?
mine sometimes loose the access point and i have to reconnect manually. mine is 802.11n and cpu settings are "performance"

---

### Post by spb37 on 2009-06-22
I have ub jaunty on my vaio-p at native resolution but screen redraws are too slow.  Anyone want to give me links or an idiots guide towards getting the ubuntu mobile ppa drivers installed.  Thx

---

### Post by pachistano on 2009-06-23
> **spb37 said:**
> I have ub jaunty on my vaio-p at native resolution but screen redraws are too slow.  Anyone want to give me links or an idiots guide towards getting the ubuntu mobile ppa drivers installed.  Thx

i don't have my laptop near me, sorry if i am generic. in case, post questions:

here is what I did 

1) install ubuntu dell image 9.04 (jauntry) - 2.1 GB is the correct size 
2) run a system update
apt-get update
apt-get upgrade
synaptic (or apt, whatever.. ) will remove the old version of Xorg and install a new one, and will do more things...say yes to everything, don't worry and drink a coffe, smoke a cigarette or play for a while with your girl or your pet :p
    suggestion: in case you are playing with your girl, do-not-stop playing once synaptic is ready! otherwise your girl will get angry with you! (my experience)

3) remove from /boot/grub/menu.lst the lines the system added after the update
this because with the new kernel, psb does not work!

  -> this rows are referred to the NEW kernel you installed. in facts, after the update you will have 2 different kernel versions inside your system and inside your menu.lst
so, remove the new one ( i remember the last kernel is the 2.6.2x.13) 

4) add to your /etc/apt/sources the repositories of psb drivers

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

- thanks to [http://www.tipsandthoughts.com/?p=4](http://www.tipsandthoughts.com/?p=4)

5) run a synaptic update one more time, or apt-get update

6)install xserver-xorg-video-psb it is supposed to be version 0.31.0
apt-get install xserver-xorg-video-psb

the system will install some addtional packages related to psb

7) reboot

8 )at this point, you are supposed to have a 9.04 running in 2D with the resolution you paid for 


it worked with my brand new dell mini 10 


questions? post here

bye,
fabio

---

### Post by spb37 on 2009-06-23
Just what I needed.  Thx so much

---

### Post by yzarc on 2009-06-24
Now I have the right resolution in my dell mini 10, but the wifi disappeared   :( 

what can I do to get it back?

---

### Post by tyroeternal on 2009-06-24
> **yzarc said:**
> Now I have the right resolution in my dell mini 10, but the wifi disappeared   :( 

what can I do to get it back?

When did it disappear, after you installed Jaunty?

---

### Post by yzarc on 2009-06-24
happend when I installed xserver-xorg-video-psb on jaunty.

---

### Post by gtaluvit on 2009-06-25
The module install seems to be missing a step. It messed me up too. Try this:

```
sudo /sbin/lrm-manager
sudo modprobe wl

```

That should regenerate the module magic for your kernel. You may need to reboot.

---

### Post by yzarc on 2009-06-25
thank you guys very much but in the middle time I reinstall everything from the begin, now it's working :)

---

### Post by majklus on 2009-06-25
Hello guys, at first thanks for this thread, its very helpful.

I have new Acer One 751h laptop with this measly GMA 500 chipset, Ubuntu Jaunty installed. I tried to follow *brteag´s* instructions (message **#94**) so I installed xserver-xorg-video-psb package from PPA repository and then coppied firmware, psb_dri.so and Xpsb.so to the system.

Now I´ve got proper resolution, 2D video acceleration works, no 3D of course. My problem is that my laptop totally freeze very often and I suspect video driver makes this issue. If this happened, I can drive the cursor via mouse, but that´s all. X server does not response and reset of whole computer is nessesary.

Anybody saw this behavior? It´s really annoying. Is there any other way to get a full resolution and video acceleration working? Thanks fo help and sorry about language...

---

### Post by woodhouse on 2009-06-26
Something happens to PPA Jaunty [repositories]("https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa/+index?field.name_filter=&field.status_filter=published&field.series_filter=jaunty")...
;-)

Maybe we can finally use the latest Jaunty with 2D/3D video... I can't believe yet.. I'll check as soon as possible!

Have you tested ?

---

### Post by majklus on 2009-06-26
I tried it. Resolution and video acceleration seems OK, glxinfo reports Direct rendering:Yes, glxgears gives me about 230 FPS (instead of 80 FPS before driver update). But compiz not work for me, I´m not able to allow desktop effects.
Now I hope it solves my problem with stability. For you compiz is working?

---

### Post by majklus on 2009-06-26
ufff, it freeze again... so new driver doesn´t help me...

---

### Post by ssombra on 2009-06-26
Hi,
I followed the instructions here and i was able to install Ubuntu 9.04 on mi mini, thank you all very much.
However, yesterday i turned my laptop on and the system asked for updates. I installed them and now i don't have wifi!!

I am new with ubuntu so any help would be great. 
Thanks
Sebastian

---

### Post by pitakill on 2009-06-26
Actually i prefer gentoo instead of ubuntu but the chipset Poulsbo is a PITA, anyway i bought dell mini 12" with ubuntu preloaded, and what.cd has the answer for a out-of-box installation of ubuntu.

There isn't a problem with the repositories of Dell, something like

[http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/)

If anyone has more info for gentoo on the dell mini 12"; X, and the webcam isn't properly working.

Thanks in advance.

---

### Post by spb37 on 2009-06-28
I tried the approach below with my vaio-P both with kubuntu lpia jaunty and ubuntu non lpia jaunty on my vaio-p.  Both times the xserver would keep trying to start (giving the vaio screen) but fall back to the text login mode.  Using the failsafe xorg.conf which relies on vesa works but is not the native driver / holy grail.  Everything else works better than expected, it even goes to sleep when I close the lid.  Ubuntu and kubuntu both boot faster than windows 7 and even my home desktop kubuntu.  So I am eager to get the poulsbo driver working.  The vaio-p linux wiki page is blank but if I poulsbo to work it would be a great post.  So close but yet so far.    

Appreciate any help / suggestions.    









> **pachistano said:**
> i don't have my laptop near me, sorry if i am generic. in case, post questions:

here is what I did 

1) install ubuntu dell image 9.04 (jauntry) - 2.1 GB is the correct size 
2) run a system update
apt-get update
apt-get upgrade
synaptic (or apt, whatever.. ) will remove the old version of Xorg and install a new one, and will do more things...say yes to everything, don't worry and drink a coffe, smoke a cigarette or play for a while with your girl or your pet :p
    suggestion: in case you are playing with your girl, do-not-stop playing once synaptic is ready! otherwise your girl will get angry with you! (my experience)

3) remove from /boot/grub/menu.lst the lines the system added after the update
this because with the new kernel, psb does not work!

  -> this rows are referred to the NEW kernel you installed. in facts, after the update you will have 2 different kernel versions inside your system and inside your menu.lst
so, remove the new one ( i remember the last kernel is the 2.6.2x.13) 

4) add to your /etc/apt/sources the repositories of psb drivers

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

- thanks to [http://www.tipsandthoughts.com/?p=4](http://www.tipsandthoughts.com/?p=4)

5) run a synaptic update one more time, or apt-get update

6)install xserver-xorg-video-psb it is supposed to be version 0.31.0
apt-get install xserver-xorg-video-psb

the system will install some addtional packages related to psb

7) reboot

8 )at this point, you are supposed to have a 9.04 running in 2D with the resolution you paid for 


it worked with my brand new dell mini 10 


questions? post here

bye,
fabio

---

### Post by gtaluvit on 2009-06-29
> **woodhouse said:**
> Something happens to PPA Jaunty [repositories]("https://edge.launchpad.net/~ubuntu-mobile/+archive/ppa/+index?field.name_filter=&field.status_filter=published&field.series_filter=jaunty")...
;-)

Maybe we can finally use the latest Jaunty with 2D/3D video... I can't believe yet.. I'll check as soon as possible!

Have you tested ?

I have tested the new 3D driver for Jaunty. glxgears does run significantly faster although I still don't have true 3d support in Wine and I've read elsewhere that compiz still doesn't function. I removed the 3d stuff though pretty shortly though because I was experiencing hard lockups. Currently with 2D I get freezes that I can break out of with plugging/unplugging of any USB device. The lockups with the 3D driver were hard locks that required a hard poweroff. Not cool.

---

### Post by tyroeternal on 2009-06-29
> **spb37 said:**
> I tried the approach below with my vaio-P both with kubuntu lpia jaunty and ubuntu non lpia jaunty on my vaio-p. Both times the xserver would keep trying to start (giving the vaio screen) but fall back to the text login mode.

The issue you are having sounds like it is because you are booting the system with the wrong kernel.  The kernel from the original jaunty install works with the psb driver, but the newer kernel does not.

I do not have the vaio p, but that is the way my mini 12 responds to booting with the wrong kernel.  You should select the older kernel at boot time, or if you accidentally removed the wrong one from your menu.lst file, it will need to be added back.

Hope that helps :D

---

### Post by pachistano on 2009-06-29
nice to hear that glx is working at more than (ridicolous) 80fps 

i'm going home to try this new release, and than back doing a report to you people.

i think post #1000 will win a developer from intel or dell for one day... :D

bye,
fabio

---

### Post by pachistano on 2009-06-29
> **pachistano said:**
> nice to hear that glx is working at more than (ridicolous) 80fps 

i'm going home to try this new release, and than back doing a report to you people.

i think post #1000 will win a developer from intel or dell for one day... :D

bye,
fabio

synaptic update + search for "psb" in your packages
install everything you see with the "psb"string in the name, except psb-modules (because my kernel package is locked to version 2.6.28.11 and psb-modules needs linux-generic AND linux generic needs new kernel .13)

reboot
and
bit@paranoia:~$ glxgears 
1361 frames in 5.0 seconds = 272.121 FPS
1371 frames in 5.0 seconds = 274.050 FPS

instad of 80/100
much better! :)

i confirm compiz still does not work, and i'm still experiencing a slow youtube.
any suggestion? do i need to remove "poulsbo-driver-2d"?? i can see a poulsbo-driver-3d installed in the system too.
how do i know the system is runnig poulsbo-driver-2d or poulsbo-driver-3d??

cheers,
fabio

---

### Post by dimeified on 2009-06-29
Dude your awesome, i did as described and have the same results. Also i have compiz, i added psb to the whitelist in the compiz bin file. Performance isn't superb, but acceptable. I am running avant window navigator, and have the bar size at 24. helps with screen realestate and performance.

glxgears
989 frames in 5.0 seconds = 197.709 FPS
1499 frames in 5.0 seconds = 299.539 FPS
1530 frames in 5.0 seconds = 305.926 FPS
1314 frames in 5.0 seconds = 262.684 FPS

---

### Post by valikor on 2009-06-29
What are the advantages and disadvantages to installing 9.04 on the mini 12? Is the Dell version of ubuntu better for any reason? In theory it's supposed to be better suited for the hardware, but mine is brand new out of the box and it's a little bit sluggish.

Suggestions?

---

### Post by woodhouse on 2009-06-30
So let's summarize the state of poulsbo:
I can use my Mini 10 (but also if you have a Mini 12),

[LIST]
[*]using **Windows** (noooo..please);
[*]installing Ubuntu **Intrepid** (8.10) and adding **related PPA repositories** at the end;
[*]([COLOR=Red]**new**[/COLOR]) installing Ubuntu **Jaunty** (9.04) and adding  **related PPA repositories** at the end;
[/LIST]
Since PPA Jaunty repositories have new packages (some day ago), I tried the last one.

But, I don't understand why KDE fails to start with the following backgrace inside log (**/var/log/kdm.log**):
[INDENT][FONT=Courier New]Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80bd3f5]
2: [0xb7f67400]
3: /usr/lib/xorg/modules/drivers//psb_drv.so [0xb78596a0]
4: /usr/lib/xorg/modules/extensions//libextmod.so [0xb78ff0c4]
5: /usr/bin/X [0x80d7fa3]
6: /usr/bin/X [0x814bb35]
7: /usr/bin/X [0x817cd5c]
8: /usr/bin/X [0x814589b]
9: /usr/lib/xorg/modules/extensions//libglx.so [0xb78d921a]
10: /usr/bin/X(main+0x44c) [0x807237c]
11: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b36775]
12: /usr/bin/X [0x80717a1]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11
[/FONT][/INDENT]
Further, if I try to use **glxgears**, I receive the following error:
[INDENT][FONT=Courier New]glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

[/FONT][/INDENT]Anybody can help me?
Thanks

---

### Post by valikor on 2009-06-30
Hmm nobody is directly answering my question, but it seems that since so many people are trying to install Jaunty on the Mini 12, there is a rough concensus that Jaunty is better than the preloaded Dell version of ubuntu?

What about xubuntu?

I'm just trying to make mine run a bit more smoothly... it's a bit sluggish out of the box.

---

### Post by tyroeternal on 2009-06-30
> **valikor said:**
> Hmm nobody is directly answering my question, but it seems that since so many people are trying to install Jaunty on the Mini 12, there is a rough concensus that Jaunty is better than the preloaded Dell version of ubuntu?

What about xubuntu?

I'm just trying to make mine run a bit more smoothly... it's a bit sluggish out of the box.

Sorry to not answer before.  I use jaunty because it has the latest versions of the programs that I use on a daily basis.  Dell's upgrade/update methods are now how I like my system to be managed.  It is okay if you want a simple "just works" system, but I like to shoot for a bit more.  In my opinion jaunty is a bit snappier because of the latest versions of everything, but that may also be me projecting.

Xubuntu is good, but I just like gnome.  Personally I do not see the need for a more minimal environment, but that is always a matter of taste.  Yay for choice!  Ultimately, the minis are netbooks... they will be sluggish.  It is just part of their give and take -> features vs price.

---

### Post by teatimest on 2009-06-30
After I messed up with Jaunty, I backed up all my data and installed Xubuntu 9.04. I have never used Belmont, but I used UNR 8.04, i386 Ubuntu 9.04 and i386 Xubuntu 9.04. Ubuntu Jaunty was snappier than UNR 8.04. You can feel the improvement. 

But I did not like Nautilus. I think it is too much for netbook. It was almost unusable when I tied to upload pictures. It took loooong time to display thumnails. Now I am happy with Thunar. The only problem was that I had to manually install Dropbox (so that I don't run Nautilus with it).

> **tyroeternal said:**
> Sorry to not answer before.  I use jaunty because it has the latest versions of the programs that I use on a daily basis.  Dell's upgrade/update methods are now how I like my system to be managed.  It is okay if you want a simple "just works" system, but I like to shoot for a bit more.  In my opinion jaunty is a bit snappier because of the latest versions of everything, but that may also be me projecting.

Xubuntu is good, but I just like gnome.  Personally I do not see the need for a more minimal environment, but that is always a matter of taste.  Yay for choice!  Ultimately, the minis are netbooks... they will be sluggish.  It is just part of their give and take -> features vs price.

---

### Post by Xernie on 2009-07-01
> **dimeified said:**
> Dude your awesome, i did as described and have the same results. Also i have compiz, i added psb to the whitelist in the compiz bin file. Performance isn't superb, but acceptable. I am running avant window navigator, and have the bar size at 24. helps with screen realestate and performance.

glxgears
989 frames in 5.0 seconds = 197.709 FPS
1499 frames in 5.0 seconds = 299.539 FPS
1530 frames in 5.0 seconds = 305.926 FPS
1314 frames in 5.0 seconds = 262.684 FPS

How do you add psb to the whitelist?

---

### Post by tyroeternal on 2009-07-01
> **Xernie said:**
> How do you add psb to the whitelist?

Edit the file /usr/bin/compiz and add "psb" to the whitelist section.

---

### Post by dimeified on 2009-07-01
Hey sorry i didn't clarify that. It's worth noting, animations really suck on this machine with compiz, all i use it for is true transparent term windows, and so i can run avant-window-navigator.
What services and such do you guys typically disable to free up memory? I don't think i'll need cups anytime soon, so i wanna disable that.

---

### Post by pachistano on 2009-07-01
> **woodhouse said:**
> So let's summarize the state of poulsbo:
I can use my Mini 10 (but also if you have a Mini 12),

[LIST]
[*]using **Windows** (noooo..please);
[*]installing Ubuntu **Intrepid** (8.10) and adding **related PPA repositories** at the end;
[*]([COLOR=Red]**new**[/COLOR]) installing Ubuntu **Jaunty** (9.04) and adding  **related PPA repositories** at the end;
[/LIST]
Since PPA Jaunty repositories have new packages (some day ago), I tried the last one.

[INDENT][FONT=Courier New]
[/FONT][/INDENT]Anybody can help me?
Thanks

woodhouse, what kernel are you using? maybe you forgot to choose the 2.6.28.11 kernel from grub

i'm experiencing disconnections from my wifis and also problems after a long suspend mode time, anybody else is experiencing the same?

i will post details in the future, i'm monitoring my syslog

fabio

---

### Post by gtaluvit on 2009-07-01
> **woodhouse said:**
> 
Further, if I try to use **glxgears**, I receive the following error:
[INDENT][FONT=Courier New]glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

[/FONT][/INDENT]Anybody can help me?
Thanks

I know exactly what your problem is: diversions. The problem with some of the packages are they divert the real packages to new ones but never change it back if you uninstall or revert. I had this problem when I tried to do the magic of using Jaunty with Intrepid pacakges and PPA enabled. When I reverted everything back to Jaunty, I was majorly borked. Use ```
dpkg-divert
``` to remove all the OpenGL related nonsense and you should be fine.

---

### Post by ssombra on 2009-07-02
Hi,
I installed ubuntu in my mini 10 following all your tips and instructions. Despite it has a very slow performance, i could install compiz.
I prepared an screencast so you can see the performance:

[http://www.screentoaster.com/watch/stUEhdQEJIR11ZRVxcU1tdUVFc/ubuntu_in_mini_10]("http://www.screentoaster.com/watch/stUEhdQEJIR11ZRVxcU1tdUVFc/ubuntu_in_mini_10")

Best

---

### Post by pachistano on 2009-07-02
> **pachistano said:**
> woodhouse, what kernel are you using? maybe you forgot to choose the 2.6.28.11 kernel from grub

i'm experiencing disconnections from my wifis and also problems after a long suspend mode time, anybody else is experiencing the same?

i will post details in the future, i'm monitoring my syslog

fabio

i'm back with my logs... 
the log starts with a sleeping mode (suspend)
after opening the laptop, he cames back to life but i can not see anything on the monitor, just a black screen!!
please helpppppppppp
here below the entire log, sorry it too verbose

Jul  1 22:27:30 paranoia NetworkManager: <debug> [1246480050.001371] periodic_update(): Roamed from BSSID 00:19:84:80:A5:FD (SuperKrusty) to (none) ((none)) 
Jul  1 22:27:31 paranoia NetworkManager: <info>  Sleeping... 
Jul  1 22:27:31 paranoia NetworkManager: <info>  (eth0): now unmanaged 
Jul  1 22:27:31 paranoia NetworkManager: <info>  (eth0): device state change: 2 -> 1 
Jul  1 22:27:31 paranoia NetworkManager: <info>  (eth0): cleaning up... 
Jul  1 22:27:31 paranoia NetworkManager: <info>  (eth0): taking down device. 
Jul  1 22:27:31 paranoia NetworkManager: <info>  (eth1): now unmanaged 
Jul  1 22:27:31 paranoia NetworkManager: <info>  (eth1): device state change: 8 -> 1 
Jul  1 22:27:31 paranoia NetworkManager: <info>  (eth1): deactivating device (reason: 37). 
Jul  1 22:27:31 paranoia NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Jul  1 22:27:31 paranoia NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess  
Jul  1 22:27:31 paranoia NetworkManager: <info>  (eth1): cleaning up... 
Jul  1 22:27:31 paranoia avahi-daemon[2643]: Withdrawing address record for 192.168.8.99 on eth1.
Jul  1 22:27:31 paranoia avahi-daemon[2643]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.8.99.
Jul  1 22:27:31 paranoia avahi-daemon[2643]: Interface eth1.IPv4 no longer relevant for mDNS.
Jul  1 22:27:31 paranoia NetworkManager: <info>  (eth1): taking down device. 
Jul  1 22:27:31 paranoia avahi-daemon[2643]: Withdrawing address record for fe80::224:2cff:fe09:aa6 on eth1.
Jul  1 22:27:33 paranoia kernel: [  728.962887] [drm] intel_lvds_prepare
Jul  1 22:27:33 paranoia kernel: [  728.962896] [drm] intel_lvds_set_power: 0
Jul  1 22:27:33 paranoia kernel: [  728.962901] [drm] intel_lvds_set_backlight: the level is 0
Jul  1 22:27:33 paranoia kernel: [  729.074053] [drm] LVDS: set mode 1024x576 c
Jul  1 22:27:33 paranoia kernel: [  729.074120] [drm] intel_lvds_commit
Jul  1 22:27:33 paranoia kernel: [  729.074125] [drm] intel_lvds_set_power: 1
Jul  1 22:27:33 paranoia kernel: [  729.491659] [drm] intel_lvds_set_backlight: the level is 100
Jul  1 22:27:33 paranoia kernel: [  729.491675] [drm] intel_lvds_dpms: the mode is 0
Jul  1 22:27:33 paranoia kernel: [  729.491680] [drm] intel_lvds_set_power: 1
Jul  1 22:27:33 paranoia kernel: [  729.491687] [drm] intel_lvds_set_backlight: the level is 100
Jul  1 22:27:33 paranoia kernel: [  729.555614] [drm] intel_lvds_prepare
Jul  1 22:27:33 paranoia kernel: [  729.555621] [drm] intel_lvds_set_power: 0
Jul  1 22:27:33 paranoia kernel: [  729.555626] [drm] intel_lvds_set_backlight: the level is 0
Jul  1 22:27:33 paranoia kernel: [  729.666834] [drm] LVDS: set mode 1024x576 c
Jul  1 22:27:33 paranoia kernel: [  729.666897] [drm] intel_lvds_commit
Jul  1 22:27:33 paranoia kernel: [  729.666902] [drm] intel_lvds_set_power: 1
Jul  1 22:27:33 paranoia kernel: [  730.093465] [drm] intel_lvds_set_backlight: the level is 100
Jul  2 13:22:53 paranoia acpid: client 2595[0:0] has disconnected 
Jul  2 13:22:53 paranoia kernel: [  731.672155] PM: Syncing filesystems ... done.
Jul  2 13:22:53 paranoia kernel: [  731.677791] PM: Preparing system for mem sleep
Jul  2 13:22:53 paranoia kernel: [  731.677802] Freezing user space processes ... (elapsed 0.00 seconds) done.

now it is sleeping


Jul  2 13:22:53 paranoia kernel: [  731.679792] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Jul  2 13:22:53 paranoia kernel: [  731.685132] PM: Entering mem sleep
Jul  2 13:22:53 paranoia kernel: [  731.685154] Suspending console(s) (use no_console_suspend to debug)
Jul  2 13:22:53 paranoia kernel: [  731.685375] drm_sysfs_suspend
Jul  2 13:22:53 paranoia kernel: [  731.686657] btusb_intr_complete: hci0 urb f62d5b80 failed to resubmit (1)
Jul  2 13:22:53 paranoia kernel: [  731.687787] btusb_bulk_complete: hci0 urb f62d5400 failed to resubmit (2)
Jul  2 13:22:53 paranoia kernel: [  731.687829] btusb_bulk_complete: hci0 urb f62d5180 failed to resubmit (1)
Jul  2 13:22:53 paranoia kernel: [  732.485611] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jul  2 13:22:53 paranoia kernel: [  732.485984] sd 0:0:0:0: [sda] Stopping disk
Jul  2 13:22:53 paranoia kernel: [  732.811097] ACPI handle has no context!
Jul  2 13:22:53 paranoia kernel: [  732.811207] wl 0000:03:00.0: PCI INT A disabled
Jul  2 13:22:53 paranoia kernel: [  732.824411] r8169 0000:02:00.0: PME# enabled
Jul  2 13:22:53 paranoia kernel: [  732.824605] r8169 0000:02:00.0: wake-up capability enabled by ACPI
Jul  2 13:22:53 paranoia kernel: [  732.840624] ehci_hcd 0000:00:1d.7: PCI INT D disabled
Jul  2 13:22:53 paranoia kernel: [  732.856338] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Jul  2 13:22:53 paranoia kernel: [  732.856388] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Jul  2 13:22:53 paranoia kernel: [  732.856430] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Jul  2 13:22:53 paranoia kernel: [  732.888310] HDA Intel 0000:00:1b.0: PCI INT A disabled
Jul  2 13:22:53 paranoia kernel: [  732.904380] psb 0000:00:02.0: PCI INT A disabled
Jul  2 13:22:53 paranoia kernel: [  732.920417] PM: suspend devices took 1.236 seconds
Jul  2 13:22:53 paranoia kernel: [  732.920518] ACPI: Preparing to enter system sleep state S3
Jul  2 13:22:53 paranoia kernel: [  732.922819] Disabling non-boot CPUs ...
Jul  2 13:22:53 paranoia kernel: [  732.925704] CPU 1 is now offline
Jul  2 13:22:53 paranoia kernel: [  732.925712] SMP alternatives: switching to UP code
Jul  2 13:22:53 paranoia kernel: [  733.228245] CPU0 attaching NULL sched-domain.
Jul  2 13:22:53 paranoia kernel: [  733.228253] CPU1 attaching NULL sched-domain.
Jul  2 13:22:53 paranoia kernel: [  733.228336] CPU0 attaching NULL sched-domain.
Jul  2 13:22:53 paranoia kernel: [  733.228754] CPU1 is down
Jul  2 13:22:53 paranoia kernel: [  733.228869] Extended CMOS year: 2000
Jul  2 13:22:53 paranoia kernel: [  733.228869] Back to C!
Jul  2 13:22:53 paranoia kernel: [  733.228869] Extended CMOS year: 2000
Jul  2 13:22:53 paranoia kernel: [  733.228869] Enabling non-boot CPUs ...
Jul  2 13:22:53 paranoia kernel: [  733.228869] SMP alternatives: switching to SMP code
Jul  2 13:22:53 paranoia kernel: [  733.529714] Booting processor 1 APIC 0x1 ip 0x6000
Jul  2 13:22:53 paranoia kernel: [  733.227872] Initializing CPU#1
Jul  2 13:22:53 paranoia kernel: [  733.227872] Calibrating delay using timer specific routine.. 3190.37 BogoMIPS (lpj=6380750)
Jul  2 13:22:53 paranoia kernel: [  733.227872] CPU: L1 I cache: 32K, L1 D cache: 24K
Jul  2 13:22:53 paranoia kernel: [  733.227872] CPU: L2 cache: 512K
Jul  2 13:22:53 paranoia kernel: [  733.227872] CPU: Physical Processor ID: 0
Jul  2 13:22:53 paranoia kernel: [  733.227872] CPU: Processor Core ID: 0
Jul  2 13:22:53 paranoia kernel: [  733.620249] CPU1: Intel(R) Atom(TM) CPU Z530   @ 1.60GHz stepping 02
Jul  2 13:22:53 paranoia kernel: [  733.621029] Switched to high resolution mode on CPU 1
Jul  2 13:22:53 paranoia kernel: [  733.621032] CPU0 attaching NULL sched-domain.
Jul  2 13:22:53 paranoia kernel: [  733.628107] CPU0 attaching sched-domain:
Jul  2 13:22:53 paranoia kernel: [  733.628116]  domain 0: span 0-1 level SIBLING
Jul  2 13:22:53 paranoia kernel: [  733.628124]   groups: 0 1
Jul  2 13:22:53 paranoia kernel: [  733.628141] CPU1 attaching sched-domain:
Jul  2 13:22:53 paranoia kernel: [  733.628148]  domain 0: span 0-1 level SIBLING
Jul  2 13:22:53 paranoia kernel: [  733.628155]   groups: 1 0
Jul  2 13:22:53 paranoia kernel: [  733.633030] CPU1 is up
Jul  2 13:22:53 paranoia kernel: [  733.633036] ACPI: Waking up from system sleep state S3
Jul  2 13:22:53 paranoia kernel: [  733.686935] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jul  2 13:22:53 paranoia bluetoothd[2555]: Stopping security manager 0
Jul  2 13:22:53 paranoia bluetoothd[2555]: HCI dev 0 down
Jul  2 13:22:53 paranoia bluetoothd[2555]: Adapter /org/bluez/2555/hci0 has been disabled
Jul  2 13:22:53 paranoia bluetoothd[2555]: HCI dev 0 unregistered
Jul  2 13:22:53 paranoia bluetoothd[2555]: Unregister path: /org/bluez/2555/hci0
Jul  2 13:22:53 paranoia bluetoothd[2555]: Unregistered interface org.bluez.NetworkPeer on path /org/bluez/2555/hci0
Jul  2 13:22:53 paranoia bluetoothd[2555]: Unregistered interface org.bluez.NetworkHub on path /org/bluez/2555/hci0
Jul  2 13:22:53 paranoia bluetoothd[2555]: Unregistered interface org.bluez.NetworkRouter on path /org/bluez/2555/hci0
Jul  2 13:22:53 paranoia bluetoothd[2555]: HCI dev 0 registered
Jul  2 13:22:53 paranoia kernel: [  733.832344] psb 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul  2 13:22:53 paranoia kernel: [  733.848288] [drm] intel_lvds_prepare
Jul  2 13:22:53 paranoia bluetoothd[2555]: HCI dev 0 up
Jul  2 13:22:53 paranoia bluetoothd[2555]: Starting security manager 0
Jul  2 13:22:53 paranoia kernel: [  733.848303] [drm] intel_lvds_set_power: 0
Jul  2 13:22:53 paranoia kernel: [  733.848311] [drm] intel_lvds_set_backlight: the level is 0
Jul  2 13:22:53 paranoia kernel: [  733.908951] [drm] LVDS: set mode 1024x576 c
Jul  2 13:22:53 paranoia kernel: [  733.909021] [drm] intel_lvds_commit
Jul  2 13:22:53 paranoia kernel: [  733.909026] [drm] intel_lvds_set_power: 1
Jul  2 13:22:53 paranoia kernel: [  733.909040] [drm] intel_lvds_set_backlight: the level is 100
Jul  2 13:22:53 paranoia kernel: [  733.924312] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xd83a0004)
Jul  2 13:22:53 paranoia kernel: [  733.924331] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jul  2 13:22:53 paranoia kernel: [  733.924348] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Jul  2 13:22:53 paranoia kernel: [  733.924392] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jul  2 13:22:53 paranoia kernel: [  733.924408] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jul  2 13:22:53 paranoia kernel: [  733.924511] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x0, writing 0xd840d840)
Jul  2 13:22:53 paranoia kernel: [  733.924522] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0x50005000)
Jul  2 13:22:53 paranoia kernel: [  733.924530] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0x20002020)
Jul  2 13:22:53 paranoia kernel: [  733.924541] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jul  2 13:22:53 paranoia kernel: [  733.924550] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Jul  2 13:22:53 paranoia kernel: [  733.924572] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Jul  2 13:22:53 paranoia kernel: [  733.924602] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x0, writing 0xfff0)
Jul  2 13:22:53 paranoia kernel: [  733.924610] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xd800d800)
Jul  2 13:22:53 paranoia kernel: [  733.924618] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0x200000f0)
Jul  2 13:22:53 paranoia bluetoothd[2555]: rfcomm_bind: Address already in use (98)
Jul  2 13:22:53 paranoia bluetoothd[2555]: audio-headset: Operation not permitted (1)
Jul  2 13:22:53 paranoia bluetoothd[2555]: l2cap_bind: Address already in use (98)
Jul  2 13:22:53 paranoia bluetoothd[2555]: audio-a2dp: Operation not permitted (1)
Jul  2 13:22:53 paranoia kernel: [  733.924629] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
Jul  2 13:22:53 paranoia kernel: [  733.924637] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Jul  2 13:22:53 paranoia kernel: [  733.924656] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Jul  2 13:22:53 paranoia kernel: [  733.924678] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jul  2 13:22:53 paranoia kernel: [  733.924684] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jul  2 13:22:53 paranoia kernel: [  733.924727] usb usb2: root hub lost power or was reset
Jul  2 13:22:53 paranoia kernel: [  733.924752] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jul  2 13:22:53 paranoia kernel: [  733.924758] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jul  2 13:22:53 paranoia kernel: [  733.924799] usb usb3: root hub lost power or was reset
Jul  2 13:22:53 paranoia kernel: [  733.924841] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jul  2 13:22:53 paranoia kernel: [  733.924848] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jul  2 13:22:53 paranoia kernel: [  733.924889] usb usb4: root hub lost power or was reset
Jul  2 13:22:53 paranoia kernel: [  733.940291] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 21 (level, low) -> IRQ 21
Jul  2 13:22:53 paranoia kernel: [  733.940312] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jul  2 13:22:53 paranoia kernel: [  733.940526] pata_sch 0000:00:1f.1: setting latency timer to 64
Jul  2 13:22:53 paranoia kernel: [  733.956308] r8169 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x107)
Jul  2 13:22:53 paranoia kernel: [  733.956341] r8169 0000:02:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xd840000c)
Jul  2 13:22:53 paranoia kernel: [  733.956359] r8169 0000:02:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xd841000c)
Jul  2 13:22:53 paranoia kernel: [  733.956376] r8169 0000:02:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x2001)
Jul  2 13:22:53 paranoia kernel: [  733.956391] r8169 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jul  2 13:22:53 paranoia kernel: [  733.956408] r8169 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jul  2 13:22:53 paranoia kernel: [  733.956505] r8169 0000:02:00.0: wake-up capability disabled by ACPI
Jul  2 13:22:53 paranoia kernel: [  733.956519] r8169 0000:02:00.0: PME# disabled
Jul  2 13:22:53 paranoia kernel: [  733.972322] wl 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jul  2 13:22:53 paranoia kernel: [  733.972363] wl 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd8000004)
Jul  2 13:22:53 paranoia kernel: [  733.972379] wl 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jul  2 13:22:53 paranoia kernel: [  733.972396] wl 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
Jul  2 13:22:53 paranoia kernel: [  733.972456] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jul  2 13:22:53 paranoia kernel: [  733.972471] wl 0000:03:00.0: setting latency timer to 64
Jul  2 13:22:53 paranoia kernel: [  733.987198] sd 0:0:0:0: [sda] Starting disk
Jul  2 13:22:53 paranoia kernel: [  735.392647] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Jul  2 13:22:53 paranoia kernel: [  735.392655] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
Jul  2 13:22:53 paranoia kernel: [  735.405579] ata1.00: configured for UDMA/100
Jul  2 13:22:53 paranoia kernel: [  735.417868] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Jul  2 13:22:53 paranoia kernel: [  735.418060] sd 0:0:0:0: [sda] Write Protect is off
Jul  2 13:22:53 paranoia kernel: [  735.418069] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul  2 13:22:53 paranoia kernel: [  735.418306] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  2 13:22:53 paranoia kernel: [  736.100326] usb 1-7: reset high speed USB device using ehci_hcd and address 4
Jul  2 13:22:53 paranoia kernel: [  736.352316] usb 3-1: reset full speed USB device using uhci_hcd and address 2
Jul  2 13:22:53 paranoia kernel: [  736.505527] PM: resume devices took 2.820 seconds
Jul  2 13:22:53 paranoia bluetoothd[2555]: Registered interface org.bluez.Service on path /org/bluez/2555/hci0
Jul  2 13:22:53 paranoia kernel: [  736.505643] PM: Finishing wakeup.
Jul  2 13:22:53 paranoia kernel: [  736.505648] Restarting tasks ... done.
Jul  2 13:22:53 paranoia bluetoothd[2555]: Registered interface org.bluez.NetworkPeer on path /org/bluez/2555/hci0
Jul  2 13:22:53 paranoia bluetoothd[2555]: Registered interface org.bluez.NetworkHub on path /org/bluez/2555/hci0
Jul  2 13:22:53 paranoia kernel: [  736.958318] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Jul  2 13:22:53 paranoia bluetoothd[2555]: Registered interface org.bluez.NetworkRouter on path /org/bluez/2555/hci0
Jul  2 13:22:53 paranoia bluetoothd[2555]: Registered interface org.bluez.SerialProxyManager on path /org/bluez/2555/hci0
Jul  2 13:22:53 paranoia bluetoothd[2555]: Adapter /org/bluez/2555/hci0 has been enabled
Jul  2 13:22:56 paranoia acpid: client connected from 2595[0:0] 
Jul  2 13:22:56 paranoia NetworkManager: <info>  Waking up... 
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth0): now managed 
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth0): bringing up device. 
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth0): preparing device. 
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Jul  2 13:22:56 paranoia NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jul  2 13:22:56 paranoia NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jul  2 13:22:56 paranoia kernel: [  737.493746] psmouse serio1: ID: 10 00 64<6>r8169: eth0: link down
Jul  2 13:22:56 paranoia kernel: [  739.863431] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth1): now managed 
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth1): device state change: 1 -> 2 
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth1): bringing up device. 
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth1): preparing device. 
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth1): deactivating device (reason: 2). 
Jul  2 13:22:56 paranoia NetworkManager: <WARN>  nm_device_wifi_disable_encryption(): error setting key for device eth1: Invalid argument 
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Jul  2 13:22:56 paranoia NetworkManager: <info>  (eth1): supplicant interface state:  starting -> ready 
Jul  2 13:22:57 paranoia avahi-daemon[2643]: Registering new address record for fe80::224:2cff:fe09:aa6 on eth1.*.
Jul  2 13:23:06 paranoia kernel: [  750.045012] eth1: no IPv6 routers present
Jul  2 13:23:22 paranoia NetworkManager: <info>  Activation (eth1) starting connection 'Auto SuperKrusty' 
Jul  2 13:23:22 paranoia NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Jul  2 13:23:22 paranoia NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jul  2 13:23:22 paranoia NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jul  2 13:23:22 paranoia NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jul  2 13:23:22 paranoia NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jul  2 13:23:22 paranoia NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jul  2 13:23:22 paranoia NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Jul  2 13:23:22 paranoia NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto SuperKrusty' has security, and secrets exist.  No new secrets needed. 
Jul  2 13:23:22 paranoia NetworkManager: <info>  Config: added 'ssid' value 'SuperKrusty' 
Jul  2 13:23:22 paranoia NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jul  2 13:23:22 paranoia NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jul  2 13:23:22 paranoia NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jul  2 13:23:22 paranoia NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul  2 13:23:22 paranoia NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jul  2 13:23:22 paranoia NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jul  2 13:23:22 paranoia NetworkManager: <info>  Config: set interface ap_scan to 1 
Jul  2 13:23:22 paranoia NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> disconnected 



why the display is black WHYYYYY???????????????????????????
only a reboot worked for me


i cut the reboot logs, if needed, please ask

Jul  2 13:23:58 paranoia syslogd 1.5.0#5ubuntu3: restart.
Jul  2 13:23:59 paranoia kernel: Inspecting /boot/System.map-2.6.28-11-generic
Jul  2 13:23:59 paranoia kernel: Cannot find map file.
Jul  2 13:23:59 paranoia kernel: Loaded 54095 symbols from 42 modules.
Jul  2 13:23:59 paranoia kernel: [    0.000000] BIOS EBDA/lowmem at: 00097000/00097000
Jul  2 13:23:59 paranoia kernel: [    0.000000] Initializing cgroup subsys cpuset

---cut---

please, please, help

---

### Post by woodhouse on 2009-07-02
> **pachistano said:**
> woodhouse, what kernel are you using? maybe you forgot to choose the 2.6.28.11 kernel from grub

i'm experiencing disconnections from my wifis and also problems after a long suspend mode time, anybody else is experiencing the same?

i will post details in the future, i'm monitoring my syslog

fabio

really really thanks!
now it works.

---

### Post by PatrickVogeli on 2009-07-02
if you need to stop kernel updates coming in, you can remove the packages linux linux-image-generic and linux-headers-generic. This way, no more new kernels will be installed, and I'd say that if -11 works fine for you, why upgrade?

Another solution would be to install newer kernels, so you can try them, but always keep -11 as first booting kernel. You can do that by copying the whole -11 kernel entry in /boot/grub/menu.lst above the line that says "### BEGIN AUTOMAGIC KERNELS LIST". That way, automatic grub updates won't change your first option, defaulting you to the good kernel but you'll always have the newest kernel installed and you'll be able to try them.

Hope that helps someone.

---

### Post by pachistano on 2009-07-02
woodhouse, you are welcome!
btw, i solved my issue in using suspend mode. i modified acpi parameters as follow, and my netbook does not freeze on resume.

/etc/default/acpi-support

SAVE_VIDEO_PCI_STATE=true

USE_DPMS=false

LOCK_SCREEN=false

one of these three parameters solveed my issue, i don't know which one is at the moment (running out of time at the moment: trying to move house and job to nederland... anybody could help????).

 i will post details in the future if i have.


fabio

---

### Post by fitzkarraldo on 2009-07-03
everybody here says that the right kernel is 2.6.28-11 but if I boot with that kernel I'm not able to start a full desktop session because "Ubuntu is running in low graphics mode" and several errors about DRM are showed to me.
actually, instead, if I start with my 2.6.28-13-generic kernel everything seems to work fine, except that my desktop randomly freezes and I have to power off it.

any suggest?

---

### Post by pachistano on 2009-07-03
> **fitzkarraldo said:**
> everybody here says that the right kernel is 2.6.28-11 but if I boot with that kernel I'm not able to start a full desktop session because "Ubuntu is running in low graphics mode" and several errors about DRM are showed to me.
actually, instead, if I start with my 2.6.28-13-generic kernel everything seems to work fine, except that my desktop randomly freezes and I have to power off it.

any suggest?

@fitzkarraldo,
good to hear that kernel .13 is working as well, but we need more infos about your configuration.
do you have the PPA third party repositories we suggested in previous posts?
are you running ubuntu jaunty, right?
is your system fully updated?
what does glxgears says?
is your 3d working? 

about your issue, try to change acpi parameters as suggest on my previous post, and let us know. it seems to fix (for me, at the moment!) all issues i had related suspending and freezing

people: what do you think if I do an image of my system's partition and share it? could this help?


bye,
fabio

---

### Post by fitzkarraldo on 2009-07-03
> **pachistano said:**
> @fitzkarraldo,
good to hear that kernel .13 is working as well, but we need more infos about your configuration.
do you have the PPA third party repositories we suggested in previous posts?
are you running ubuntu jaunty, right?
is your system fully updated?
what does glxgears says?
is your 3d working? 

about your issue, try to change acpi parameters as suggest on my previous post, and let us know. it seems to fix (for me, at the moment!) all issues i had related suspending and freezing

people: what do you think if I do an image of my system's partition and share it? could this help?


bye,
fabio

Hi fabio,
I'm running a full updated Jaunty with ubuntu-mobile repository 
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

in this moment I'm running 2.6.28-13-generic kernel and glxgears says
964 frames in 5.0 seconds = 192.689 FPS
1007 frames in 5.0 seconds = 201.341 FPS
925 frames in 5.0 seconds = 184.943 FPS
743 frames in 5.0 seconds = 148.594 FPS
1007 frames in 5.0 seconds = 201.166 FPS
1014 frames in 5.0 seconds = 202.799 FPS
859 frames in 5.0 seconds = 171.793 FPS
873 frames in 5.0 seconds = 174.571 FPS
1036 frames in 5.0 seconds = 207.112 FPS

(in some moments even better values)

Are you exeperiencing freeze problem with kernel 2.6.28-11 too?

---

### Post by sam_yan1314 on 2009-07-03
i support fedora Linux 9.
it is good to use !

---

### Post by pachistano on 2009-07-03
> **fitzkarraldo said:**
> Hi fabio,
I'm running a full updated Jaunty with ubuntu-mobile repository 
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

in this moment I'm running 2.6.28-13-generic kernel and glxgears says
964 frames in 5.0 seconds = 192.689 FPS
1007 frames in 5.0 seconds = 201.341 FPS
925 frames in 5.0 seconds = 184.943 FPS
743 frames in 5.0 seconds = 148.594 FPS
1007 frames in 5.0 seconds = 201.166 FPS
1014 frames in 5.0 seconds = 202.799 FPS
859 frames in 5.0 seconds = 171.793 FPS
873 frames in 5.0 seconds = 174.571 FPS
1036 frames in 5.0 seconds = 207.112 FPS

(in some moments even better values)

Are you exeperiencing freeze problem with kernel 2.6.28-11 too?


hello,

i have these repos in my sources:
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

same as yours.
mine glxgears is running at an avarage of 250 FPS, a bit better than yours (note: i'm running gnome with compiz, firefox, skype, pidgin, evolution at the same time)

i experienced freezes and also a problem after suspending (blank screen see mine previous posts for details) and i solved these problems modifing ACPI options and doing a reboot. (maybe an /etc/init.d/acpid restart    works too)
after these modifications (yesterday afternoon) i have had not these problems again.
it's soon to definitively say that this is the right solution, but using my dell for some hours, i had no problems.

what kind of dell do you have?
are you also experiencing disconnection problems from wifi card manager?
it seems to be my last headache issue to definitevely fix my dell.

fabio aka ba bei o

---

### Post by fitzkarraldo on 2009-07-03
> **pachistano said:**
> hello,

i have these repos in my sources:
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

same as yours.
mine glxgears is running at an avarage of 250 FPS, a bit better than yours (note: i'm running gnome with compiz, firefox, skype, pidgin, evolution at the same time)

i experienced freezes and also a problem after suspending (blank screen see mine previous posts for details) and i solved these problems modifing ACPI options and doing a reboot. (maybe an /etc/init.d/acpid restart    works too)
after these modifications (yesterday afternoon) i have had not these problems again.
it's soon to definitively say that this is the right solution, but using my dell for some hours, i had no problems.

what kind of dell do you have?
are you also experiencing disconnection problems from wifi card manager?
it seems to be my last headache issue to definitevely fix my dell.

fabio aka ba bei o

fabio, I have a dell mini 12.

actually I'm running same programs as yours, except evolution and compiz (I don't need it), yesterday when I tried glxgears I obtained an average value of 240fps. 
I'll try to apply the acpi settings to .13 kernel, just to see if I can solve the problem of freeze with this kernel too.
However, I have not had any disconnection from wifi at the moment.

I'm still unable to start a desktop session with .11 kernel, any idea?
here my psb packages situation:
i  psb-firmware                                                           p   psb-kernel-headers 
p   psb-kernel-source
i A psb-modules                                                   
i  xpsb-glx                                                               i   xserver-xorg-video-psb

---

### Post by pachistano on 2009-07-03
> **fitzkarraldo said:**
> fabio, I have a dell mini 12.

actually I'm running same programs as yours, except evolution and compiz (I don't need it), yesterday when I tried glxgears I obtained an average value of 240fps. 
I'll try to apply the acpi settings to .13 kernel, just to see if I can solve the problem of freeze with this kernel too.
However, I have not had any disconnection from wifi at the moment.

I'm still unable to start a desktop session with .11 kernel, any idea?
here my psb packages situation:
i  psb-firmware                                                           p   psb-kernel-headers 
p   psb-kernel-source
i A psb-modules                                                   
i  xpsb-glx                                                               i   xserver-xorg-video-psb


i don't have my dell near me, but i clearly remember that i insalled some psb packages named -something-psb-2d and 3d.
do a search for "psb" in synaptic. search using "name and description" option, and install these packages.
after this, you are supposed to run .11 kernel.

try it and than come back to let us know.
let also us know which version of the above packages are you running.

one more question: are you running 802.11b wireless card or 802.11n? mine is 802.11n...


bye,
fabio

---

### Post by fitzkarraldo on 2009-07-03
> **pachistano said:**
> i don't have my dell near me, but i clearly remember that i insalled some psb packages named -something-psb-2d and 3d.
do a search for "psb" in synaptic. search using "name and description" option, and install these packages.
after this, you are supposed to run .11 kernel.try it and than come back to let us know.
let also us know which version of the above packages are you running.


maybe you mean poulsbo-driver-2d and poulsbo-driver-3d packages, I installed them but no success in booting .11 kernel.
I also modified the acpi settings, now I'm going to check if they will solve the freeze problem.

> 
one more question: are you running 802.11b wireless card or 802.11n? mine is 802.11n...

bye,
fabio

I suppose 802.11b as in Italy I think this model was sold only with this wireless card...

---

### Post by pachistano on 2009-07-03
> **fitzkarraldo said:**
> maybe you mean poulsbo-driver-2d and poulsbo-driver-3d packages, I installed them but no success in booting .11 kernel.
I also modified the acpi settings, now I'm going to check if they will solve the freeze problem.



I suppose 802.11b as in Italy I think this model was sold only with this wireless card...

lol! are you italian? :p also me! 
i bought this dell in italy, but with "particular" configuration -do-not-ask-me-how I did.
us keyboard, 802.11n card and 6 cells battery.. 

of course i was meaning poulsbo-driver-2d and poulsbo-driver-3d
-> pls post here your psb packages version

also, let us know if my ACPI workaround works for you.

ciao,
fabio

---

### Post by fitzkarraldo on 2009-07-03
> **pachistano said:**
> lol! are you italian? :p also me! 
i bought this dell in italy, but with "particular" configuration -do-not-ask-me-how I did.
us keyboard, 802.11n card and 6 cells battery.. 

:-D

> 
of course i was meaning poulsbo-driver-2d and poulsbo-driver-3d
-> pls post here your psb packages version


psb-firmware 0.30-0ubuntu1~904um1
psb-modules 4.41.1-0ubuntu1~904um1
xpsb-glx 0.18-0ubuntu1~904um1
xserver-xorg-video-psb 0.31.0-0ubuntu1~904um1

> 
also, let us know if my ACPI workaround works for you.


no success, with .13 kernel and your ACPI settings the situations seemed worst, so I returned to standard settings but I still have crashes.

When I try to boot with .11 kernel I obtain several errors, among whose:
- DRM open failed
- could not initialize irq handler
- this driver currently needs DRM to operate

????

---

### Post by pachistano on 2009-07-03
> **fitzkarraldo said:**
> :-D



psb-firmware 0.30-0ubuntu1~904um1
psb-modules 4.41.1-0ubuntu1~904um1
xpsb-glx 0.18-0ubuntu1~904um1
xserver-xorg-video-psb 0.31.0-0ubuntu1~904um1



no success, with .13 kernel and your ACPI settings the situations seemed worst, so I returned to standard settings but I still have crashes.

When I try to boot with .11 kernel I obtain several errors, among whose:
- DRM open failed
- could not initialize irq handler
- this driver currently needs DRM to operate

????


sorry,
no idea.
anybody else could help? it's hard to help you, cause i do not have this system configuration. during the weekend i will try to reproduce your problem in case i have enough time to spend on it. 
btw, try to google for it, in my opinion is an ACPI issue, probably you need to play in this direction.

fabio

---

### Post by satbunny on 2009-07-03
I have exactly the same problem after an xpsb update on wednesday (that's when I installed it)

I am running Jaunty, kernel .11

My sources.list is as follows: this is quite conventional, but a few weeks ago it also included the backports and proposed repositories.

> # deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

deb [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/transmissionbt/ubuntu](http://ppa.launchpad.net/transmissionbt/ubuntu) jaunty main



---

### Post by pachistano on 2009-07-03
> **satbunny said:**
> I have exactly the same problem after an xpsb update on wednesday (that's when I installed it)

I am running Jaunty, kernel .11

My sources.list is as follows: this is quite conventional, but a few weeks ago it also included the backports and proposed repositories.


why don't you people post a syslog?
clear it, and wait when the issue happens.
than post it here, could provide some clues...
...

---

### Post by mikewhatever on 2009-07-03
> **satbunny said:**
> I have exactly the same problem after an xpsb update on wednesday (that's when I installed it)

I am running Jaunty, kernel .11

My sources.list is as follows: this is quite conventional, but a few weeks ago it also included the backports and proposed repositories.

The backports are there still, as for proposed, I don't think there is such a repository.

---

### Post by aliosa27 on 2009-07-03
For those that are getting the drm(etc etc) errors now, you need to do a apt-get install linux-generic

This should take you to 2.6.28.13 .

Vaio P users;

 add mem=1980MB to your kernel command line and you should be able to boot into X without the psb module bombing out .

---

### Post by tyroeternal on 2009-07-03
After the xpsb update my .11 kernel stopped letting X start,  but the .13 suddenly started working just fine... Fortunately I did not have to monkey around with anything, other than [FONT="Mono"]modprobe wl[/FONT] to get my wireless up and running again.

---

### Post by fitzkarraldo on 2009-07-04
> **tyroeternal said:**
> After the xpsb update my .11 kernel stopped letting X start,  but the .13 suddenly started working just fine... Fortunately I did not have to monkey around with anything, other than [FONT="Mono"]modprobe wl[/FONT] to get my wireless up and running again.

have you had any freeze of X?

---

### Post by pachistano on 2009-07-04
> **fitzkarraldo said:**
> have you had any freeze of X?


guys, 
bad news.... i'm also experiencing freezes of X, no way to resume....
my acpi workaround works only to resume from suspend mode without problems (blank screen)... :S

---

### Post by fitzkarraldo on 2009-07-04
> **pachistano said:**
> guys, 
bad news.... i'm also experiencing freezes of X, no way to resume....
my acpi workaround works only to resume from suspend mode without problems (blank screen)... :S

in conclusion, actual version of drivers is quite unusable.

---

### Post by sol1tude on 2009-07-04
for fixing freezing problem:
[http://anothersysadmin.wordpress.com/2009/05/05/ubuntu-904-and-uxa-acceleration-in-xorg/](http://anothersysadmin.wordpress.com/2009/05/05/ubuntu-904-and-uxa-acceleration-in-xorg/)
for me it works :)

---

### Post by tyroeternal on 2009-07-04
> **fitzkarraldo said:**
> have you had any freeze of X?

Yes, I'm having the issues as well.  I sent an email to the person adding poulsbo packages into the ubuntu-mobile ppa and asked him if he knew of the problems.

---

### Post by satbunny on 2009-07-05
> **pachistano said:**
> why don't you people post a syslog?
clear it, and wait when the issue happens.
than post it here, could provide some clues...
...

Sure. What is it, and where is it? Is it a log file? Is it a simple text file? Is it always generated or does something have to be enabled or run? Where is it?

BTW 'you people' is just such a lovely form of address.

---

### Post by fitzkarraldo on 2009-07-05
> **sol1tude said:**
> for fixing freezing problem:
[http://anothersysadmin.wordpress.com/2009/05/05/ubuntu-904-and-uxa-acceleration-in-xorg/](http://anothersysadmin.wordpress.com/2009/05/05/ubuntu-904-and-uxa-acceleration-in-xorg/)
for me it works :)

it doesn't work for me :(

---

### Post by fitzkarraldo on 2009-07-05
here we have a bug report on launchpad

[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/393290](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/393290)

---

### Post by majklus on 2009-07-05
For me seems that change xorg.conf helps, at least a have not any freezes for more then 5 hours of using my netbook, it's the best result I ever have. Thank's for posting, I will continue with testing. ;)

---

### Post by pachistano on 2009-07-06
> **satbunny said:**
> Sure. What is it, and where is it? Is it a log file? Is it a simple text file? Is it always generated or does something have to be enabled or run? Where is it?

BTW 'you people' is just such a lovely form of address.

hello satbunny,
almost every log file linux produces, is located in /var/log and subfolders
you have different log files, each for a different "thing" eg: system, X, boot, security... 
depending from your distribution and configuration, some files could change name. 
every log is a txt file and in case you delete it, the system provides to create it again.
the file i'm interested in is syslog.
you can clear the file using
> /var/log/syslog

also, you can see what the system is writing on the log file in realtime using 

tail -f logname
 
hope this helps

bye,

fabio


ps: is "you people" offensive? clarify me the situation, in order to avoid misunderstandings...tnx

---

### Post by pachistano on 2009-07-06
> **fitzkarraldo said:**
> here we have a bug report on launchpad

[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/393290](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/393290)


...waiting for a fix....

---

### Post by dimeified on 2009-07-06
i tried the uxa acceleration fix in xorg and it did not work. and it may be too early to confirm, but i removed the line out of xorg so it looks the way it originally did, and i havnt had a freeze yet. wtf?

---

### Post by tyroeternal on 2009-07-06
It seems to be a completely random thing... sometimes it freezes five minutes in, other times it never gets me and I shut it down properly.

---

### Post by dimeified on 2009-07-06
well before now i had 2 scenarios,

1 - computer freezes, have to pressed power button to bring up shutdown screen then hit cancel to resume working.

2 - computer freezes with mouse still movable, nothing works except holding the power button down to power off.

scenario 1 happened after 10 minutes after booting, and 10 minutes thereafter.

scenario 2 happened EVERY TIME i booted the computer after about a half hour of use.

Now after editing xorg, adding uxa, saving,rebooting, freezing, removing uxa, rebooting... suddenly everything is ok. the freezes definately were NOT random for me, and i should have had them happen by now, ive been using the pc for 3 hours now without freezing.

---

### Post by dimeified on 2009-07-06
looks like scenario 1 just happened, damn

---

### Post by puttux on 2009-07-06
I got a new dell mini 10, four days back..... and am having the same problem... I first had the 2.6.28-11 kernel when I installed 9.04 first. But the psb drivers didn't work, so had to upgrade to the 2.6.28-13 kernel. But that broke my wifi. And the psb drivers weren't very smooth either. While the totem movie player could play my videos ok... smplayer seemed jerky... (there were random crashes of course... usually when there were lots of applications open or when I was copying file in large numbers)... So I just switched back to the old kernel, removed the psb drivers and am watching videos using mplayer on the svga mode now... 
Just hoping for a stable psb driver at the earliest...

---

### Post by pachistano on 2009-07-07
> **dimeified said:**
> well before now i had 2 scenarios,

1 - computer freezes, have to pressed power button to bring up shutdown screen then hit cancel to resume working.

2 - computer freezes with mouse still movable, nothing works except holding the power button down to power off.

scenario 1 happened after 10 minutes after booting, and 10 minutes thereafter.

scenario 2 happened EVERY TIME i booted the computer after about a half hour of use.

Now after editing xorg, adding uxa, saving,rebooting, freezing, removing uxa, rebooting... suddenly everything is ok. the freezes definately were NOT random for me, and i should have had them happen by now, ive been using the pc for 3 hours now without freezing.


ok, i know dell ubuntu is really a bloody mess. confusion everywhere, fix this and break that, freeze, lock, 2d, 3d, poulsbo, different kernels and repos...

i think we need to clarify the situation.
everybody has a system *NOT* freezing, could please post the running configuration?
i would like to know:
kernel version
psb version and from which repo 
xorg version
additional packages
compiz yes or compiz no

what kind of modifications this system has.

thanks a lot, this could help a lot

fabio

---

### Post by Xernie on 2009-07-07
> **pachistano said:**
> ok, i know dell ubuntu is really a bloody mess. confusion everywhere, fix this and break that, freeze, lock, 2d, 3d, poulsbo, different kernels and repos...

i think we need to clarify the situation.
everybody has a system *NOT* freezing, could please post the running configuration?
i would like to know:
kernel version
psb version and from which repo 
xorg version
additional packages
compiz yes or compiz no

what kind of modifications this system has.

thanks a lot, this could help a lot

fabio

I second this excellent suggestion.

---

### Post by aliosa27 on 2009-07-07
I can tell you weather your running -11 -13 it looks like the way to get around the freezing problem is to simply remove the binary firmware blob ./lib/firmware/msvdx_fw.bin

However Then we are back to square 2(as 1 was no acceleration) to no 3d/xv acceleration

That takes care of the freezing....


So the hardware cursor still functions...
weird


this happens with compiz and without..

logs to follow..

---

### Post by pachistano on 2009-07-08
> **aliosa27 said:**
> I can tell you weather your running -11 -13 it looks like the way to get around the freezing problem is to simply remove the binary firmware blob ./lib/firmware/msvdx_fw.bin

However Then we are back to square 2(as 1 was no acceleration) to no 3d/xv acceleration

That takes care of the freezing....


So the hardware cursor still functions...
weird


this happens with compiz and without..

logs to follow..


I removed /lib/firmware/msvdx_fw.bin from the system but:

-3d still working
-freezing still happens

where did you get this advice?
is it working for you?

fabio

---

### Post by fitzkarraldo on 2009-07-08
_perhaps_ I've found some kind of solution...

before last week I had a jaunty install working without any problem, except 3d (no driver existed yet). I realized that maybe something got broken when I:
- updated my kernel to 2.6.28-13
- discovered and installed the 3d version of poulsbo driver.

Well, this morning I decided to remove the 3d driver, packages psb-firmware and xpsb-glx, and until now (more than 3 hours) I had no freeze. In last week, instead, with 3d driver installed, my notebook was freezing every hour more or less.

I'll keep you informed...

---

### Post by aliosa27 on 2009-07-08
Fabio,


   Your Right, it actually still does happen on -13 without the firmware blob..I think the firmware is compiled into the xpsb.so module now, looking at the xorg logs it does not show it attempting to find the firmware anymore on -13...However rolling back to -11, and removing the firmware blob does take care of the freezing.. 


sorry..

---

### Post by fitzkarraldo on 2009-07-08
> **fitzkarraldo said:**
> _perhaps_ I've found some kind of solution...

before last week I had a jaunty install working without any problem, except 3d (no driver existed yet). I realized that maybe something got broken when I:
- updated my kernel to 2.6.28-13
- discovered and installed the 3d version of poulsbo driver.

Well, this morning I decided to remove the 3d driver, packages psb-firmware and xpsb-glx, and until now (more than 3 hours) I had no freeze. In last week, instead, with 3d driver installed, my notebook was freezing every hour more or less.

I'll keep you informed...

still no crashes, definitely actual config is more stable.

---

### Post by tyroeternal on 2009-07-08
> **fitzkarraldo said:**
> still no crashes, definitely actual config is more stable.

Are you using the -13 kernel or the -11 kernel?  If you removed the new packages and are using the -11 kernel it should not be surprising that your system is working... you just reverted to the last working setup that we all had before.

---

### Post by fitzkarraldo on 2009-07-08
> **tyroeternal said:**
> Are you using the -13 kernel or the -11 kernel?  If you removed the new packages and are using the -11 kernel it should not be surprising that your system is working... you just reverted to the last working setup that we all had before.

I'm running the -13 kernel.

---

### Post by pachistano on 2009-07-08
> **fitzkarraldo said:**
> I'm running the -13 kernel.


i'm also running your config since 2 hours and no freezes :)
very very good

thank you very much

fabio

---

### Post by aliosa27 on 2009-07-08
So we are all back to our non-3d enabled state on -13.

---

### Post by pachistano on 2009-07-08
> **aliosa27 said:**
> So we are all back to our non-3d enabled state on -13.

bit@paranoia:~$ glxgears 
290 frames in 5.0 seconds = 57.736 FPS
344 frames in 5.0 seconds = 68.667 FPS
329 frames in 5.0 seconds = 65.702 FPS
368 frames in 5.0 seconds = 73.466 FPS

and we are at the starting point.

new kernel, old problems. btw, i will keep using this configuration, slow, no compiz, but who cares. just working well almost everything. 

good night,
fabio

---

### Post by gtaluvit on 2009-07-09
> **dimeified said:**
> 

1 - computer freezes, have to pressed power button to bring up shutdown screen then hit cancel to resume working.



I have this as well BUT I don't if I disable the synaptic touchpad and use an external mouse. I can get the freeze to happen in no time just scrolling in firefox but with an external mouse AND disabling synaptic, I'm fine.

---

### Post by Isofarro on 2009-07-09
Hi from a long time lurker. This forum has helped me sort out many issues running Ubuntu of different flavours over a number of different computers. The most recent being a Dell Mini 12 just a few minutes ago. Since this is a massive thread, and there isn't one single clear list of step-by-step instructions (although all the information is available in this thread), here's the process I went through from start to finish on the Dell Mini 12 - using a USB CD Rom to install Ubuntu 9.04 (Jaunty):


[LIST=1]
[*]Download [[COLOR=black]Ubuntu 9.04 (Jaunty) Desktop iso[/COLOR]]("http://www.ubuntu.com/getubuntu/download")
[*]Burn iso image to CD
[*]Connect USB CD-drive and network cable to the Mini 12.
[*]Start Mini 12 and when the Inspirion logo appears press F12 to enter boot mode. The boot mode link will turn from grey to white when it is activated successfully.
[*]Put the Ubuntu disk into the CD Drive
[*]Select CD/DVD from the boot menu to boot from the USB CD-drive
[*]On the language menulist press Enter to select English (the default selected language)
[*]Select Install Ubuntu, language English, Keyboard autodetects correctly as UK, and set timezone to London, and set up an account.
[*]Chose for Ubuntu to use the full disk (hasta la Vista)
[*]Unbuntu spends about 15 - 20 minutes installing before finally displaying a dialogue box to restart the computer.
[*]Restart. After what looks like a barf of error text Ubuntu asks you to remove the CD, close the tray, then press Enter.
[*]Remove CD from tray, close tray and press Enter. Ubuntu restarts to a normal looking bootup and login prompt.
[*]Login. Ubuntu starts up normally and shows a typical clean desktop. The initial resolution is set to 1024x768 - looks fairly decent.
[*]In the top menu go to System > Administration > Update Manger
[*]In the Update Manager application click Check. Enter your login password to perfom the administrative tasks. Ubuntu now gets a fresh list of updated packages and returns with a list of Important security updates/
[*]Click Install Updates to kick of installing 111.1Mb of updates (158 packages) as of 9 July 2009. Ubuntu downloads and installs all these packages. After installation a restart is required.
[*]Click Restart Now to restart Ubuntu. This reboots back into the login prompt. So login again and get back to the standard desktop.
[*]Drop into a terminal by clicking Applications > Accessories > Terminal. This opens a terminal and starts bash.
[*]Enter sudo nano /etc/apt/sources.list. This starts the nano text editor for us to add two new package repositories. Enter your login password if prompted.
[*]Add the following two lines to the end of the file: 
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
[*]Press Ctrl-O to save the file, and press Enter to accept the filename. Then press Ctrl-X to exit nano.
[*]Open the [Public Key Server url]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x99D6B21CC6598A30") in your browser
[*]Highlight the public key on this page (everything starting from "-----BEGIN PGP PUBLIC KEY BLOCK-----" through to "-----END PGP PUBLIC KEY BLOCK-----" inclusive), and copy it with Ctrl-C
[*]Open a text editor (from the top menu Applications > Accessories > Text Editor.
[*]Paste in your copied text by pressing Ctrl-V, and click Save. In the Save dialogue box enter the name as ppa.key and click Save.
[*]In the top menu click System > Administration > Software Sources, and enter your password when requested.
[*]In Software Sources switch to the Authentication tab and click Import Key File.... Select ppa.key from the Import key dialogue box and click OK.
[*]In the top navigation bar click System > Administration > Synaptic Package Manager. Enter your login password if prompted.
[*]In Synaptic Package Manager click Reload to reload the list of packages.
[*]Click the Origin button to get a list of repositories, and in that list select ppa.launchpad.net/main.
[*]Select the package xserver-xorg-video-psb and Mark it for installation. Click Mark in the popup dialogue box that follows.
[*]Still in Synaptic Package Manager click Apply, and in the Summary dialogue box click Apply to install the package. The new packages are downloaded and installed.
[*]When the changes have been applied close all the applications and restart Ubuntu.
[*]Log back in again after Ubuntu has restarted. The desktop now looks crisper as the resolution is now correctly configured to 1280x800.
[/LIST]

---

### Post by Xernie on 2009-07-10
> **Isofarro said:**
> Hi from a long time lurker. This forum has helped me sort out many issues running Ubuntu of different flavours over a number of different computers. The most recent being a Dell Mini 12 just a few minutes ago. Since this is a massive thread, and there isn't one single clear list of step-by-step instructions (although all the information is available in this thread), here's the process I went through from start to finish on the Dell Mini 12 - using a USB CD Rom to install Ubuntu 9.04 (Jaunty):


[LIST=1]
[*]Download [[COLOR=black]Ubuntu 9.04 (Jaunty) Desktop iso[/COLOR]]("http://www.ubuntu.com/getubuntu/download")
[*]Burn iso image to CD
[*]Connect USB CD-drive and network cable to the Mini 12.
[*]Start Mini 12 and when the Inspirion logo appears press F12 to enter boot mode. The boot mode link will turn from grey to white when it is activated successfully.
[*]Put the Ubuntu disk into the CD Drive
[*]Select CD/DVD from the boot menu to boot from the USB CD-drive
[*]On the language menulist press Enter to select English (the default selected language)
[*]Select Install Ubuntu, language English, Keyboard autodetects correctly as UK, and set timezone to London, and set up an account.
[*]Chose for Ubuntu to use the full disk (hasta la Vista)
[*]Unbuntu spends about 15 - 20 minutes installing before finally displaying a dialogue box to restart the computer.
[*]Restart. After what looks like a barf of error text Ubuntu asks you to remove the CD, close the tray, then press Enter.
[*]Remove CD from tray, close tray and press Enter. Ubuntu restarts to a normal looking bootup and login prompt.
[*]Login. Ubuntu starts up normally and shows a typical clean desktop. The initial resolution is set to 1024x768 - looks fairly decent.
[*]In the top menu go to System > Administration > Update Manger
[*]In the Update Manager application click Check. Enter your login password to perfom the administrative tasks. Ubuntu now gets a fresh list of updated packages and returns with a list of Important security updates/
[*]Click Install Updates to kick of installing 111.1Mb of updates (158 packages) as of 9 July 2009. Ubuntu downloads and installs all these packages. After installation a restart is required.
[*]Click Restart Now to restart Ubuntu. This reboots back into the login prompt. So login again and get back to the standard desktop.
[*]Drop into a terminal by clicking Applications > Accessories > Terminal. This opens a terminal and starts bash.
[*]Enter sudo nano /etc/apt/sources.list. This starts the nano text editor for us to add two new package repositories. Enter your login password if prompted.
[*]Add the following two lines to the end of the file: 
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
[*]Press Ctrl-O to save the file, and press Enter to accept the filename. Then press Ctrl-X to exit nano.
[*]Open the [Public Key Server url]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x99D6B21CC6598A30") in your browser
[*]Highlight the public key on this page (everything starting from "-----BEGIN PGP PUBLIC KEY BLOCK-----" through to "-----END PGP PUBLIC KEY BLOCK-----" inclusive), and copy it with Ctrl-C
[*]Open a text editor (from the top menu Applications > Accessories > Text Editor.
[*]Paste in your copied text by pressing Ctrl-V, and click Save. In the Save dialogue box enter the name as ppa.key and click Save.
[*]In the top menu click System > Administration > Software Sources, and enter your password when requested.
[*]In Software Sources switch to the Authentication tab and click Import Key File.... Select ppa.key from the Import key dialogue box and click OK.
[*]In the top navigation bar click System > Administration > Synaptic Package Manager. Enter your login password if prompted.
[*]In Synaptic Package Manager click Reload to reload the list of packages.
[*]Click the Origin button to get a list of repositories, and in that list select ppa.launchpad.net/main.
[*]Select the package xserver-xorg-video-psb and Mark it for installation. Click Mark in the popup dialogue box that follows.
[*]Still in Synaptic Package Manager click Apply, and in the Summary dialogue box click Apply to install the package. The new packages are downloaded and installed.
[*]When the changes have been applied close all the applications and restart Ubuntu.
[*]Log back in again after Ubuntu has restarted. The desktop now looks crisper as the resolution is now correctly configured to 1280x800.
[/LIST]

Nice summary.

Some of us don't have an external CD-ROM drive, though. In that case, one needs to create a USB startup disk using "USB Startup Disk Creator" (duh!) in the System menu. If you have another machine with Jaunty, it should be installed by default. If not, you need to install it.

From there, it is quite easy to create a USB startup disk from the Jaunty CD or the ISO image on a USB stick (1GB is more than enough).

---

### Post by benguin on 2009-07-14
Thanks a ton Isofarro. I was so looking for exactly that. A very happy Mini 12 owner (not something I can say a lot).

-J

> **Isofarro said:**
> Hi from a long time lurker. This forum has helped me sort out many issues running Ubuntu of different flavours over a number of different computers. The most recent being a Dell Mini 12 just a few minutes ago. Since this is a massive thread, and there isn't one single clear list of step-by-step instructions (although all the information is available in this thread), here's the process I went through from start to finish on the Dell Mini 12 - using a USB CD Rom to install Ubuntu 9.04 (Jaunty):


[LIST=1]
[*]Download [[COLOR=black]Ubuntu 9.04 (Jaunty) Desktop iso[/COLOR]]("http://www.ubuntu.com/getubuntu/download")
[*]Burn iso image to CD
[*]Connect USB CD-drive and network cable to the Mini 12.
[*]Start Mini 12 and when the Inspirion logo appears press F12 to enter boot mode. The boot mode link will turn from grey to white when it is activated successfully.
[*]Put the Ubuntu disk into the CD Drive
[*]Select CD/DVD from the boot menu to boot from the USB CD-drive
[*]On the language menulist press Enter to select English (the default selected language)
[*]Select Install Ubuntu, language English, Keyboard autodetects correctly as UK, and set timezone to London, and set up an account.
[*]Chose for Ubuntu to use the full disk (hasta la Vista)
[*]Unbuntu spends about 15 - 20 minutes installing before finally displaying a dialogue box to restart the computer.
[*]Restart. After what looks like a barf of error text Ubuntu asks you to remove the CD, close the tray, then press Enter.
[*]Remove CD from tray, close tray and press Enter. Ubuntu restarts to a normal looking bootup and login prompt.
[*]Login. Ubuntu starts up normally and shows a typical clean desktop. The initial resolution is set to 1024x768 - looks fairly decent.
[*]In the top menu go to System > Administration > Update Manger
[*]In the Update Manager application click Check. Enter your login password to perfom the administrative tasks. Ubuntu now gets a fresh list of updated packages and returns with a list of Important security updates/
[*]Click Install Updates to kick of installing 111.1Mb of updates (158 packages) as of 9 July 2009. Ubuntu downloads and installs all these packages. After installation a restart is required.
[*]Click Restart Now to restart Ubuntu. This reboots back into the login prompt. So login again and get back to the standard desktop.
[*]Drop into a terminal by clicking Applications > Accessories > Terminal. This opens a terminal and starts bash.
[*]Enter sudo nano /etc/apt/sources.list. This starts the nano text editor for us to add two new package repositories. Enter your login password if prompted.
[*]Add the following two lines to the end of the file: 
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
[*]Press Ctrl-O to save the file, and press Enter to accept the filename. Then press Ctrl-X to exit nano.
[*]Open the [Public Key Server url]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x99D6B21CC6598A30") in your browser
[*]Highlight the public key on this page (everything starting from "-----BEGIN PGP PUBLIC KEY BLOCK-----" through to "-----END PGP PUBLIC KEY BLOCK-----" inclusive), and copy it with Ctrl-C
[*]Open a text editor (from the top menu Applications > Accessories > Text Editor.
[*]Paste in your copied text by pressing Ctrl-V, and click Save. In the Save dialogue box enter the name as ppa.key and click Save.
[*]In the top menu click System > Administration > Software Sources, and enter your password when requested.
[*]In Software Sources switch to the Authentication tab and click Import Key File.... Select ppa.key from the Import key dialogue box and click OK.
[*]In the top navigation bar click System > Administration > Synaptic Package Manager. Enter your login password if prompted.
[*]In Synaptic Package Manager click Reload to reload the list of packages.
[*]Click the Origin button to get a list of repositories, and in that list select ppa.launchpad.net/main.
[*]Select the package xserver-xorg-video-psb and Mark it for installation. Click Mark in the popup dialogue box that follows.
[*]Still in Synaptic Package Manager click Apply, and in the Summary dialogue box click Apply to install the package. The new packages are downloaded and installed.
[*]When the changes have been applied close all the applications and restart Ubuntu.
[*]Log back in again after Ubuntu has restarted. The desktop now looks crisper as the resolution is now correctly configured to 1280x800.
[/LIST]

---

### Post by marconeuro on 2009-07-15
I have a dell mini 10. It's quite the same as the dell 12 inches, same hardware. I followed pretti much the guide here, plus something else, and posted on a blog:
[http://machicecaga.blogspot.com/2009/06/dell-mini-10-z520-gma-500-ubuntu-904.html](http://machicecaga.blogspot.com/2009/06/dell-mini-10-z520-gma-500-ubuntu-904.html)

My problem is that the computer freeze quite often, I don't know how to debug it and the only thing I can do is shut down pushing the power button. Sometimes I still can use the mouse, other times I had the grey monitor of the standby. Someone had the same problem and know the solution? or know how to debug the problem?

---

### Post by fitzkarraldo on 2009-07-15
> **marconeuro said:**
> I have a dell mini 10. It's quite the same as the dell 12 inches, same hardware. I followed pretti much the guide here, plus something else, and posted on a blog:
[http://machicecaga.blogspot.com/2009/06/dell-mini-10-z520-gma-500-ubuntu-904.html](http://machicecaga.blogspot.com/2009/06/dell-mini-10-z520-gma-500-ubuntu-904.html)

My problem is that the computer freeze quite often, I don't know how to debug it and the only thing I can do is shut down pushing the power button. Sometimes I still can use the mouse, other times I had the grey monitor of the standby. Someone had the same problem and know the solution? or know how to debug the problem?

It seems to be a problem of 3D driver, the only solution actually is remove it.

---

### Post by kultex on 2009-07-15
I want to buy a used Mini12 - I am using it for cutting audio and I am a bit worried about the speed of the harddisk - can anyone do:

sudo hdparm -tT /dev/sda1

and post the output

thx kultex

---

### Post by tentwelveeight on 2009-07-15
> **kultex said:**
> I want to buy a used Mini12 - I am using it for cutting audio and I am a bit worried about the speed of the harddisk - can anyone do:

sudo hdparm -tT /dev/sda1

and post the output

thx kultex

/dev/sda1:
 Timing cached reads:   774 MB in  2.00 seconds = 386.89 MB/sec
 Timing buffered disk reads:   84 MB in  3.04 seconds =  27.65 MB/sec

---

### Post by divan0 on 2009-07-17
> **marconeuro said:**
>  My problem is that the computer freeze quite often, I don't know how to debug it and the only thing I can do is shut down pushing the power button. Sometimes I still can use the mouse, other times I had the grey monitor of the standby. Someone had the same problem and know the solution? or know how to debug the problem?
Hi, can you check the CPU temp? Just install the Gnome/XFCE/KDE applet for it or using 'watch -n 1 sensors' command, and check if the freezes are connected to the temperature. Thanks!

---

### Post by johncallen on 2009-07-18
It looks like some work has been done on the 3D driver for the GMA500.  

installing the package poulsbo-driver-2d from the ppa repo will install all packages needed for 2D support.  And installing the package poulsbo-driver-3d will install the requirements for 3D support.  After installing the 3D support, glxgears reports 300-350 fps.

---

### Post by pachistano on 2009-07-19
> **johncallen said:**
> It looks like some work has been done on the 3D driver for the GMA500.  

installing the package poulsbo-driver-2d from the ppa repo will install all packages needed for 2D support.  And installing the package poulsbo-driver-3d will install the requirements for 3D support.  After installing the 3D support, glxgears reports 300-350 fps.

and what about freezes??

---

### Post by JohnnyS987 on 2009-07-20
Isofarro,

Thank you very much for this fantastic HOWTO. This worked perfectly on my Dell Mini 12, except I booted from a USB key rather than a CD. I am very happy that the system now comes out of standby reliably, which did not happen under XP. I haven't seen any freezing or other problems.

I would suggest to the forum admin that your post be set as "sticky" at the beginning of this thread to make it easier to find. There's over 70 pages on this thread so it took me a while to find it.

JS

> **Isofarro said:**
> Hi from a long time lurker. This forum has helped me sort out many issues running Ubuntu of different flavours over a number of different computers. The most recent being a Dell Mini 12 just a few minutes ago. Since this is a massive thread, and there isn't one single clear list of step-by-step instructions (although all the information is available in this thread), here's the process I went through from start to finish on the Dell Mini 12 - using a USB CD Rom to install Ubuntu 9.04 (Jaunty):


[LIST=1]
[*]Download [[COLOR=black]Ubuntu 9.04 (Jaunty) Desktop iso[/COLOR]]("http://www.ubuntu.com/getubuntu/download")
[*]Burn iso image to CD
[*]Connect USB CD-drive and network cable to the Mini 12.
[*]Start Mini 12 and when the Inspirion logo appears press F12 to enter boot mode. The boot mode link will turn from grey to white when it is activated successfully.
[*]Put the Ubuntu disk into the CD Drive
[*]Select CD/DVD from the boot menu to boot from the USB CD-drive
[*]On the language menulist press Enter to select English (the default selected language)
[*]Select Install Ubuntu, language English, Keyboard autodetects correctly as UK, and set timezone to London, and set up an account.
[*]Chose for Ubuntu to use the full disk (hasta la Vista)
[*]Unbuntu spends about 15 - 20 minutes installing before finally displaying a dialogue box to restart the computer.
[*]Restart. After what looks like a barf of error text Ubuntu asks you to remove the CD, close the tray, then press Enter.
[*]Remove CD from tray, close tray and press Enter. Ubuntu restarts to a normal looking bootup and login prompt.
[*]Login. Ubuntu starts up normally and shows a typical clean desktop. The initial resolution is set to 1024x768 - looks fairly decent.
[*]In the top menu go to System > Administration > Update Manger
[*]In the Update Manager application click Check. Enter your login password to perfom the administrative tasks. Ubuntu now gets a fresh list of updated packages and returns with a list of Important security updates/
[*]Click Install Updates to kick of installing 111.1Mb of updates (158 packages) as of 9 July 2009. Ubuntu downloads and installs all these packages. After installation a restart is required.
[*]Click Restart Now to restart Ubuntu. This reboots back into the login prompt. So login again and get back to the standard desktop.
[*]Drop into a terminal by clicking Applications > Accessories > Terminal. This opens a terminal and starts bash.
[*]Enter sudo nano /etc/apt/sources.list. This starts the nano text editor for us to add two new package repositories. Enter your login password if prompted.
[*]Add the following two lines to the end of the file: 
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
[*]Press Ctrl-O to save the file, and press Enter to accept the filename. Then press Ctrl-X to exit nano.
[*]Open the [Public Key Server url]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x99D6B21CC6598A30") in your browser
[*]Highlight the public key on this page (everything starting from "-----BEGIN PGP PUBLIC KEY BLOCK-----" through to "-----END PGP PUBLIC KEY BLOCK-----" inclusive), and copy it with Ctrl-C
[*]Open a text editor (from the top menu Applications > Accessories > Text Editor.
[*]Paste in your copied text by pressing Ctrl-V, and click Save. In the Save dialogue box enter the name as ppa.key and click Save.
[*]In the top menu click System > Administration > Software Sources, and enter your password when requested.
[*]In Software Sources switch to the Authentication tab and click Import Key File.... Select ppa.key from the Import key dialogue box and click OK.
[*]In the top navigation bar click System > Administration > Synaptic Package Manager. Enter your login password if prompted.
[*]In Synaptic Package Manager click Reload to reload the list of packages.
[*]Click the Origin button to get a list of repositories, and in that list select ppa.launchpad.net/main.
[*]Select the package xserver-xorg-video-psb and Mark it for installation. Click Mark in the popup dialogue box that follows.
[*]Still in Synaptic Package Manager click Apply, and in the Summary dialogue box click Apply to install the package. The new packages are downloaded and installed.
[*]When the changes have been applied close all the applications and restart Ubuntu.
[*]Log back in again after Ubuntu has restarted. The desktop now looks crisper as the resolution is now correctly configured to 1280x800.
[/LIST]

---

### Post by marconeuro on 2009-07-20
> **divan0 said:**
> Hi, can you check the CPU temp? Just install the Gnome/XFCE/KDE applet for it or using 'watch -n 1 sensors' command, and check if the freezes are connected to the temperature. Thanks!

Sorry I can't I don't have the pc for a couple of weeks, and hopefully will be fixed in two weeks!

glxgears reports 300-350 fps for me too

---

### Post by marduk667 on 2009-07-21
and no freezes? so compiz should run faster too now...please keep us up to date

---

### Post by graydj on 2009-07-23
Just to add my piece:

Acer Aspire One 751 (also utilises the same CMA500 chip as the Dell Mini 12) running the latest 2D/3D Poulsbo drivers gives me:

daniel@daniel-laptop:~/Desktop$ glxgears
1118 frames in 5.0 seconds = 223.494 FPS
1193 frames in 5.0 seconds = 238.435 FPS
1207 frames in 5.0 seconds = 241.277 FPS
1178 frames in 5.0 seconds = 235.515 FPS
1196 frames in 5.0 seconds = 239.063 FPS
1200 frames in 5.0 seconds = 239.876 FPS

...however I am experiencing regular freezes - sometimes with/sometimes without mouse movement - every two hours or so. I'm unable to replicate the freeze; it seems completely random.

I will uninstall the 3d accelerator and provide an update.

---

### Post by marduk667 on 2009-07-24
hey, maybe this is our problem with the freezes:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/305979](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/305979)

has anybody checked if those patches went in "our" libdrm?

---

### Post by commandant_gogo on 2009-07-25
Hi,

I did install ubuntu 9.04 on friend's Dell Mini 12. 
[LIST]
[*]I had no problem for installation
[*]I have a lot of freezes, even with 2D drivers only on Gnoma. Using XFCE seems to be way more stable.
[*]Sound volume is very low.
[*]Flash usage is awful. I download it from the official Adobe website; but i never managed to view a video with a decent fluidity. Processor (Atom) is at 100% immediately. The only solution i found is to use the fiefox plugin "downloadhelper"
[*]Had problems reading mp3 in rhythmbox, resolved by the following solution: [https://bugs.launchpad.net/rhythmbox/+bug/236201/comments/10]("https://bugs.launchpad.net/rhythmbox/+bug/236201/comments/10")
[/LIST]

hope it can help

---

### Post by commandant_gogo on 2009-07-29
Does anyone tries Moblin on it?

---

### Post by fitzkarraldo on 2009-07-29
> **commandant_gogo said:**
> Does anyone tries Moblin on it?

Actually, AFAIK Dell Mini 12 should still not be supported by Moblin.

---

### Post by danboid on 2009-07-29
3D accel + compiz under Jaunty!

Good to see progress, even if it is agonisingly sloooow. 

Like the others who've installed the poulsbo 3D driver for jaunty I get the occasional freeze and unfortunately HDMI output still isn't quite right (at least for us UK/PAL HDMI users) as the desktop is still a bit too big and goes off the edge of my TV :(

The last bit of hardware I want to get working now is the internal mic on my mini 10 but I've got a nasty feeling that the internal mic doesn't work under ALSA atm - hopefully someone can prove otherwise? I've been unable to record anything with it- yes I set capture to 'int mic' and I have the capture and mic sliders right up in alsamixer but no go. I've tried different hda configs too such as the eeepc settings as they also have the ALC269- nada.

---

### Post by ssombra on 2009-07-29
> **danboid said:**
> 3D accel + compiz under Jaunty!

Good to see progress, even if it is agonisingly sloooow. 

Like the others who've installed the poulsbo 3D driver for jaunty I get the occasional freeze and unfortunately HDMI output still isn't quite right (at least for us UK/PAL HDMI users) as the desktop is still a bit too big and goes off the edge of my TV :(

The last bit of hardware I want to get working now is the internal mic on my mini 10 but I've got a nasty feeling that the internal mic doesn't work under ALSA atm - hopefully someone can prove otherwise? I've been unable to record anything with it- yes I set capture to 'int mic' and I have the capture and mic sliders right up in alsamixer but no go. I've tried different hda configs too such as the eeepc settings as they also have the ALC269- nada.
I do have the internal mic working on my mini 10 and as far as i remember i didn't have to do some special configuration (i am just starting with ubuntu).
ssombra

---

### Post by danboid on 2009-07-29
Hey ssombra!

You're right- internal mic does work!

Don't know what it was that was preventing it working before as I've just reset the things I changed that I thought might've got it working but its still OK. Weird :confused:

I've uninstalled the 3D driver now - I'll be sure to try the next release.

Hopefully Karmic will fare better with poulsbo gfx support

---

### Post by PreviousN on 2009-07-30
> **danboid said:**
> 
Like the others who've installed the poulsbo 3D driver for jaunty I get the occasional freeze 

The occasional freeze is a dealbreaker for my scenario. I'm using a kohjinsha sc3, which also has GMA500/Pulsbo. Does anyone know if going back to hardy and installing drivers on that will stop the freezing? I prefer not to use vesa because this was meant to be a media-top. Just a little laptop that I could watch movies on...


> **danboid said:**
> Hey ssombra!
Hopefully Karmic will fare better with poulsbo gfx support

I doubt it. The driver issue is still a mess, and there hasn't been any movement. Check out this recap by someone in the community: 
[http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/](http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/)

I've searched for information like everyday and haven't found much. It seems that Intel has abandoned the linux community with GMA500/Pulsbo. What a shame since the Dell Mini 12, Sony Viao P, and Kohjinsha SC3 all have the same chipset. Millions of people are affected by this. Linux has likely lost a lot of users. This should be part of the 100 papercuts program, since according to the blog: 
[http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/](http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/)

It's like 99 percent there, just needs to be finished. 

From the blog:
> This is really silly, because the code is obviously 99% basically there and working. It just needs the people who actually know the code and the hardware to put it in the right places and not random obscure undocumented repositories, submit it upstream, and keep it up to date.

---

### Post by danboid on 2009-07-30
Previous N:

Yeah, maybe I was being overly optimistic in deciding to leave off "..but I somehow doubt it". I've not tried the Karmic alphas yet but I just know they won't have improved PSB support as its not supported by xorg yet.

Like many others here, I bought my Mini 10 esp,. to run Linux - the fact that it had Intel gfx to me always meant it would work great under Linux. For just about every other intel IGP that is indeed the case. Very sad.

I uninstalled the poulsbo 3D driver but buntu still freezes every hour or so. I'm presuming that when I did a apt-get upgrade recently that it also installed a newer poulsbo 2D driver as the one I have installed now refuses to work with the previous - 2.6.28-11 - kernel.

What version of the 2D driver was it that worked stable with 2.6.28-11 and is there an occult procedure to get it back OR has anyone figured out the cause of the instability with the latest poulsbo driver yet?

---

### Post by satbunny on 2009-07-30
I too have uninstalled the 3d drivers and still get xorg freezes.. sigh.

---

### Post by fitzkarraldo on 2009-07-30
> **danboid said:**
> 

I uninstalled the poulsbo 3D driver but buntu still freezes every hour or so. I'm presuming that when I did a apt-get upgrade recently that it also installed a newer poulsbo 2D driver as the one I have installed now refuses to work with the previous - 2.6.28-11 - kernel.



Have you removed both xpsb-glx and psb-firmware packages?

---

### Post by PreviousN on 2009-07-30
I've currently got poulsbo/GMA500 drivers installed in Jaunty. I was getting random freezes (and 3d didn't work well anyway), so I removed the 3d part of the driver. I am getting fewer freezes but its still unusable. 

So to recap: I've got Jaunty, latest kernel, and 2d drivers installed. I would give you more information but I'm so frustrated I don't even want to turn the damn thing on!

But here's my question. I'm willing to run an old version of ubuntu. I mean, I ran it the first time around on a different computer without problems. So, my question is: do you get random freezes when installing hardy LTS and then putting psb drivers in it? If so, there is no point. 

Another irritation: even when the damn thing isn't freezing, if I close the lid I can't get video back after the backlite shuts off. Frustrating!

---

### Post by satbunny on 2009-07-30
> **fitzkarraldo said:**
> Have you removed both xpsb-glx and psb-firmware packages?

Yup..

and I dual boot jaunty and hardy, and both freeze a little without the drivers, and freeze a lot with them..

---

### Post by fibrewire on 2009-07-30
hey in vista i noticed on a reinstall of the driver on my AO751h that there is some sort of PersistenceThread.exe that runs in task manager. i wonder if this is needed to restart the driver on crash, which has happened several times in vista

---

### Post by gtaluvit on 2009-07-30
For those of you with the 2D only freeze, this works for me:

Press the power button or insert/remove a USB device. For some reason that triggers it to "wake up" from its frozen state. I have to cancel the shutdown dialog but it's better than a hard restart. I've also noticed I get less freezes if I disable the touchpad and just use an external mouse.

---

### Post by satbunny on 2009-07-31
Thanks for the tip, although we're getting quite junkyard mechanics with the Mini 12, aren't we?

---

### Post by nobodyisme on 2009-07-31
I was searching for info on poulsbo and found [this]("https://launchpad.net/%7Ealbertomilone/+archive/poulsbo-graphics"). Maybe it can be useful, these packages where published on 2009-07-25. Can anybody say if these packages are of any help?

---

### Post by dragonmule on 2009-07-31
Hey guys, I have two dell mini 12 to check, 1.33 and 1.6. Some have said that the freezing is only with 1.6 which is incorrect as I've seen it happen with 1.33. I have noticed it more common with the 1.6ghz, but maybe that is just my bad luck.

In any case, I have found that my machine does not freeze if I set the cpu frequency applet to set to performance, power saving, etc. This also has an automatic setting which is the default behavior.

I have also noticed that with the most updated (Apr 9) dell-mini canonical upgrades for 8.04, the crashes are far less frequent, but not eliminated with the speedstep frequency set to auto. Still, with clock freq set on the CPU, I haven't seen one freeze (*crosses fingers*).

I haven't seen any update on the video driver in quite some time. 

I've checked with
cat /var/log/dpkg.log |grep psb

And these are all the Mar 1 version afaik.

I expect the updates to continue, but reading these threads it seems as if people are trying to do all sorts of things to install different packages and versions hoping some magic will unlock the full potential of the gma500 on linux. I don't think this is currently possible.

As for general progress with the VA API, there are people working on it.

[http://cgit.freedesktop.org/libva/](http://cgit.freedesktop.org/libva/)

People have been putting in work regularly on this. libva is supposed to be the next step in linux video... but the only video chips which natively support libva are the GMA500 and S3 Chrome from what I understand. This creates a bit of a problem as both of these are closed source.

Where are people seeing crashes btw? For me, it seems to only be when flash in firefox is running which is often. I thought it was networking at first as I wasn't reproducing a crash with the network off, but now I am thinking it is when the cpu frequency changes in the middle of a flash animation running.

I tried to upgrade my 1.6 machine to 9.04 almost immediately, but quickly went back to the restore disk and the updates when the video playback seemed to not work as well. I suppose I did something wrong. I am going to try to move to 9.10 in a couple of months and see how that goes.

If all of this has been said or if I am incorrect on some things, sorry.

---

### Post by dragonmule on 2009-07-31
> **nobodyisme said:**
> I was searching for info on poulsbo and found [this]("https://launchpad.net/%7Ealbertomilone/+archive/poulsbo-graphics"). Maybe it can be useful, these packages where published on 2009-07-25. Can anybody say if these packages are of any help?

This may work? But it is not current

libva (0.29-9-0ubuntu6netbook2)That is not latest version of libva at least. I think 0.30.4 is.

---

### Post by PreviousN on 2009-07-31
I am no longer getting freezes, following sammyboy405's advice from this thread: [http://ubuntuforums.org/showthread.php?t=1213416](http://ubuntuforums.org/showthread.php?t=1213416)
> 
Do this, Unless you Really want the 3D Features.

Keep the 3D Drivers..

Here is a Copy of my xorg.conf

Code:

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option "AccelMethod" "EXA"
        Option "DRI" "off"
        Option "MigrationHeuristic" "greedy"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection

```
I added the

Code:

```
Option "AccelMethod" "EXA"
Option "DRI" "off"
Option "MigrationHeuristic" "greedy"

```
And the freezes "So Far" have gone away and I still have the performance increase.

I ran glxgears for about 5 hours and no problems on my SC3 (which also has GMA500/Poulsbo). Then I surfed the net on it for a while and still no problems. 

I, however, am still not able to have the display "wake" after being closed. I always have to turn off the computer via the power button if I forget and close the lid.

---

### Post by tbrooks2828 on 2009-07-31
Thanks for your help provided in this thread.  I have the drivers installed and glxgears shows ~250 frames per second.  

I'd like to play some video to exercise the driver.  I have installed vlc and played some of the video from this site:

[http://www.h264info.com/clips.html](http://www.h264info.com/clips.html)

but it is choppy at best.

Any suggestions on a player to exercise the offloading features the driver enables?

Thanks...

---

### Post by csimpkin on 2009-07-31
I have been following this thread for a long time. I have a mini 12 and look forward to upgrading from the default hardy install that came from dell. I need to use this machine and so I can't have it down with freezes and the like. I have never had a freeze with the dell version of hardy. I was looking around and noticed that dell passes a few options to the psb driver. The options-belmont file has the lines...

```
options xc5000 init_fw=1
options psb disable_vsync=1 no_fb=1
```

I haven't seen it mentioned in the thread if anyone has tried it with jaunty and the 3d drivers to possibly address any freezing issues.

Chad

---

### Post by dragonmule on 2009-07-31
> **csimpkin said:**
> 
```
options xc5000 init_fw=1
options psb disable_vsync=1 no_fb=1
```

xc5000 is for the tv tuner dell sells, I think.

disable vsync would make sense. I have to set vsync to 0 to get boxee to work right.

no_fb sets FBDev to off, I'm not sure if this would cause freezing.

---

### Post by danboid on 2009-07-31
> **fitzkarraldo said:**
> Have you removed both xpsb-glx and psb-firmware packages?

Hi fitzk!

No, I'd forgot about them- thanks for the reminder/tip! Now that I've uninstalled them all seems well again- I've had my netbook on all day- just flipping the lid down when not using it- and it hasn't froze since I removed those two packages and poulsbo 3D. Note that I'm running fluxbox under Jaunty.

Got to try sammyboys' xorg.conf that PreviousN posted next, see if that gives me stable 3D- at least we seem to have a stable 2D config to fall back on now (for the mo at least - jinx? ;)

---

### Post by dragonmule on 2009-07-31
> **tbrooks2828 said:**
> :

[http://www.h264info.com/clips.html](http://www.h264info.com/clips.html)

but it is choppy at best.

Any suggestions on a player to exercise the offloading features the driver enables?

Thanks...

This is a codec issue. "Dellbuntu" hardy belmont for mini 12 comes with h.264 fluendo codec and these movies run flawlessly. Fluendo sells the codec in a comprehensive codec pack and there is always medibuntu.

---

### Post by danboid on 2009-08-01
PreviousN's xorg.conf does indeed seem to have resolved the stability issues with using the latest pouslbo 3D driver- for me on my mini10 at least- big thanks previousN (and sammyboy)! It might be as good idea for someone to inform the packagers of the driver so that they can maybe automate the setup of xorg.conf at install time?

I can shut the lid and re-open it- no issues with backlight not coming back on and both resume and hibernate work great too- all with 3D enabled. If anyone is having probs with power functions etc. then maybe its GNOME (and/or compiz) thats causing the prob? Any (moderately) experienced Linux users should be using a more lightweight window manager such as fluxbox or icewm anyway as ditching GNOME/KDE will gain you a fair wodge of extra memory and greatly improve performance for running resource intensive apps- I can't use the phasex synth on my netbook under GNOME but it runs fine under fluxbox, for example.

I highly recommend pcmanfm as a great lightweight alternative to Nautilus and Konq- the only thing I miss when using pcmanfm instead of Nautilus is video thumbnails. XFCE is slowly becoming as bloated as GNOME and I find lxde still to be buggy and missing a few essential features but I'll be sure to keep tabs on lxdes progress as it is a promising project.

---

### Post by dimeified on 2009-08-02
+1 on PreviousN's xorg, it solved my freezing on my mini 12 with jaunty

---

### Post by fitzkarraldo on 2009-08-03
> **PreviousN said:**
> I am no longer getting freezes, following sammyboy405's advice from this thread: [http://ubuntuforums.org/showthread.php?t=1213416](http://ubuntuforums.org/showthread.php?t=1213416)



This works for me too, thanks a lot!

---

### Post by pachistano on 2009-08-03
freezing problem seems to be solved also for me, thanks but:
i also have the probem after the suspend: black screen. :(

---

### Post by puttux on 2009-08-04
The solution works very well.... Though glxgears gives a lesser fps  (it used to give about 250 before, and now is about 120), my performance seems to have improved a great deal. Web page scrolling, general text editing seems a lot more smooth now. I also had issues with kate not refreshing the text display. Even that is solved now. No freezes too. Thanks a lot... :)

EDIT: I don't have the issues with suspending which others are facing. I can resume normally after a suspend or a hibernation.

---

### Post by tbrooks2828 on 2009-08-04
> **dragonmule said:**
> This is a codec issue. "Dellbuntu" hardy belmont for mini 12 comes with h.264 fluendo codec and these movies run flawlessly. Fluendo sells the codec in a comprehensive codec pack and there is always medibuntu.

Thanks for your response.  I downloaded and installed fluendo but the video playback is still kinda choppy.  

Do I need to enable the codecs?  Or does just installing them enabled them? 

In mplayer, under preferences->codec&demuxer, the video codec family is listed as "none".

Any ideas?

Thanks!

---

### Post by marduk667 on 2009-08-05
does compiz still work with the new xorg.conf?

---

### Post by fitzkarraldo on 2009-08-05
> **marduk667 said:**
> does compiz still work with the new xorg.conf?

markduk, it doesn't work for me (but I really don't need).

---

### Post by satbunny on 2009-08-05
> **tbrooks2828 said:**
> Thanks for your response.  I downloaded and installed fluendo but the video playback is still kinda choppy.  

Do I need to enable the codecs?  Or does just installing them enabled them? 

In mplayer, under preferences->codec&demuxer, the video codec family is listed as "none".

Any ideas?

Thanks!

Add the medibuntu repositories and then I'd install and try vlc, I find it much faster and smoother on my Mini12 than any other video player.

[http://www.medibuntu.org/]("http://www.medibuntu.org/")

---

### Post by tbrooks2828 on 2009-08-05
> **satbunny said:**
> Add the medibuntu repositories and then I'd install and try vlc, I find it much faster and smoother on my Mini12 than any other video player.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

can you play hd h264 encoded videos with vlc?

thanks..

---

### Post by satbunny on 2009-08-05
> **tbrooks2828 said:**
> can you play hd h264 encoded videos with vlc?

thanks..

yes. but we are really off topic here..

---

### Post by ssombra on 2009-08-05
> **marduk667 said:**
> does compiz still work with the new xorg.conf?

It does work for me but with a poor performance. However it is enough for me.

Sebastian

---

### Post by pjman on 2009-08-05
> **marduk667 said:**
> does compiz still work with the new xorg.conf?

Compiz works for me but I had to add the following to /usr/bin/compiz under "# Driver whitelist":

```
WHITELIST="psb"
```

---

### Post by marduk667 on 2009-08-05
yeah i made the changes and compiz still works! great, no freeze up to now!

> yes. but we are really off topic here.. 

i think if we can get hints of how to get best performance from the mini 12 it is on topic ;)

---

### Post by duskstriker on 2009-08-05
> **pjman said:**
> Compiz works for me but I had to add the following...

Awesomeness! Thanks for the tip pjman. Compiz is working great on my new mini. :P

---

### Post by marduk667 on 2009-08-06
Wow, compiz working, no freezes, more speed on browsing, this is the first time i am really happy with my Mini 12! Also 3G is running really great now.
(I also got my new HTC Magic last week, so i am reeeeally happy at the moment :) )

OT: I only need a good option to watch the NFL season in germany now ;) If anyone knows how to get NFL Gamepass running on Linux please send me a PM

---

### Post by satbunny on 2009-08-06
Yes! I tried the new xorg.conf and (fingers crossed) no freezes and my FPS under glxgears moved from 20fps to 60fps.

---

### Post by mukiex on 2009-08-07
To everyone working on video:

The Fluendo codecs are based on GStreamer. Both VLC and Mplayer are NOT GStreamer-based players. If you're on Ubuntu, Totem is GStreamer-based and SHOULD cover your video acceleration.

However, without a GMA 500 I can't verify this. Anyone stuck on vid accel, please try Totem after installing Fluendo (and make sure 3D is working) and post your results.

That is all ;)

---

### Post by jackwcole on 2009-08-07
Just checked the U.S. Dell site and the Mini 12 is no longer offered for sale. The only Mini's being offered are the Mini 10 and the Mini 10v (with the 950 chipset and at a lower price than the Mini 10), is it possible that Dell is moving away from the gma500 chipset? Does  anyone know if any open source support is being planned for the gma500 chipset? If not, we may be between a rock and a hard place for future improvements.
Jack

---

### Post by snowpine on 2009-08-07
> **jackwcole said:**
> Just checked the U.S. Dell site and the Mini 12 is no longer offered for sale. The only Mini's being offered are the Mini 10 and the Mini 10v (with the 950 chipset and at a lower price than the Mini 10), is it possible that Dell is moving away from the gma500 chipset? Does  anyone know if any open source support is being planned for the gma500 chipset? If not, we may be between a rock and a hard place for future improvements.
Jack

Mini 9 and Mini 12 have been discontinued. Dell is coming out with a new model, the Mini 11, soon. Not sure on the hardware specs yet...

---

### Post by mikewhatever on 2009-08-08
> **jackwcole said:**
> Just checked the U.S. Dell site and the Mini 12 is no longer offered for sale. The only Mini's being offered are the Mini 10 and the Mini 10v (with the 950 chipset and at a lower price than the Mini 10), is it possible that Dell is moving away from the gma500 chipset? Does  anyone know if any open source support is being planned for the gma500 chipset? If not, we may be between a rock and a hard place for future improvements.
Jack

It's unlikely any open source support is coming for gma500. Intel doesn't seem to be interested to supply official support for any Ubuntu release since Hardy, so you are right about the rock and the place.  Even Intel's own Mibling doesn't support gma500 yet, and it's unknown if it ever will. Oh yeah, if you were hoping to use Carmic this fall, read this: [http://www.phoronix.com/scan.php?page=news_item&px=NzQzMg](http://www.phoronix.com/scan.php?page=news_item&px=NzQzMg).

---

### Post by s-tobe on 2009-08-08
Hi there
Interesting to see progress in this thread
I have recently bought ASUS 1101HA . Great laptop bu unfort. with this #$@@ GMA500 video chip. Thanks to this thread I was able to get HD 1366:768 resolution with 2D and 3D poulsbo drivers installed on Ubuntu Jaunty 9.04. Still don't know the difference and the value of 2d and 3d but anyway, Maybe somebody can summarize the differences.

my ASUS 1101HA was suffering from incidental display freezes as well. I have just added the suggestions of PreviousN (xorg.conf changes) and I am waiting for my next freeze to happen (or not). I can confirm that since these little additions to xorg.conf it seems that page up /down in firefox during browsing is less choppy (more smooth, I don't know the exact word in English)

For reference and forum user benefit I insert my installed packages:
s-tobe@s-tobe-netbook:~$ sudo dpkg --list |grep poulsbo
ii  libdrm-poulsbo1                            2.3.0-0ubuntu1~904um1              Userspace interface to kernel DRM services -
ii  poulsbo-driver-2d                          1.1-0ubuntu1~904um1                Metapackage for the 2D Poulsbo (psb) X11 dri
ii  poulsbo-driver-3d                          1.1-0ubuntu1~904um1                Metapackage for the 3D Poulsbo (psb) X11 dri
s-tobe@s-tobe-netbook:~$ sudo dpkg --list |grep psb
ii  poulsbo-driver-2d                          1.1-0ubuntu1~904um1                Metapackage for the 2D Poulsbo (psb) X11 dri
ii  poulsbo-driver-3d                          1.1-0ubuntu1~904um1                Metapackage for the 3D Poulsbo (psb) X11 dri
ii  psb-firmware                               0.30-0ubuntu1~904um1               Binary firmware for the Poulsbo (psb) 3D X11
ii  psb-kernel-source                          4.41.1-0ubuntu1~904um1             Kernel module for the Poulsbo (psb) 2D X11 d
ii  psb-modules                                4.41.1-0ubuntu1~904um1             Kernel module built for -generic or -lpia ke
ii  xpsb-glx                                   0.18-0ubuntu1~904um1               X11 drivers for Poulsbo (psb) 3D acceleratio
ii  xserver-xorg-video-psb                     0.31.0-0ubuntu1~904um1             X.Org X server -- Intel Poulsbo (2D)
s-tobe@s-tobe-netbook:~$ 

my XORG.CONF now looks like:
Section "Device"
        Identifier      "Configured Video Device"
        Option "AccelMethod" "EXA"
        Option "DRI" "off"
        Option "MigrationHeuristic" "greedy"

EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

### Post by AdamWill on 2009-08-10
For anyone running (or interested in running) Fedora 11, I've cleaned up my Fedora 11 build of the UNR packages and updated to the latest ones I can find, and put them in a repository. 3D acceleration and compiz work, with this stuff.

See [my blog post](http://www.happyassassin.net/2009/08/10/intel-gma500-poulsbo-on-fedora-11-repository-with-working-3d-compiz-support/) for more details.

---

### Post by ssombra on 2009-08-10
Hi,
I was able to install Jaunty and thanks to all the instructions in this thread i had 3d and even compiz working. However, i deactivated the visual effects and now i can't activate them back :(
What could be wrong?
any ideas?

Thanks in advance

---

### Post by Xernie on 2009-08-11
I can confirm that changing xorg.conf as suggested stops the freezes; it also improves performance a bit for me.

However, ever since kernel 2.6.28-14 I haven't been able to run X. I know it's a problem with that kernel because it works fine with 2.6.28-13. Has anybody had this issue? The error it gives has something to do with DRI or something -- I'll post the exact thing when I get home.

Any ideas?

---

### Post by ssombra on 2009-08-11
> **Xernie said:**
> I can confirm that changing xorg.conf as suggested stops the freezes; it also improves performance a bit for me.

However, ever since kernel 2.6.28-14 I haven't been able to run X. I know it's a problem with that kernel because it works fine with 2.6.28-13. Has anybody had this issue? The error it gives has something to do with DRI or something -- I'll post the exact thing when I get home.

Any ideas?
I had the same problem and i found the solution in another thread (sorry, i don't remember the exact source). You have to rebuild the module from a command prompt:

sudo dpkg-reconfigure psb-kernel-source

Hope this help.

---

### Post by ssombra on 2009-08-11
> **ssombra said:**
> Hi,
I was able to install Jaunty and thanks to all the instructions in this thread i had 3d and even compiz working. However, i deactivated the visual effects and now i can't activate them back :(
What could be wrong?
any ideas?

Thanks in advance
I already find the problem. thanks

---

### Post by marduk667 on 2009-08-13
would you please add the solution for the problem here in this thread?

---

### Post by satbunny on 2009-08-13
Well Dell have cancelled the Mini 12.. 

[http://bit.ly/IOODA]("http://bit.ly/IOODA")

Now is it really due to the reasons stated or because it's such a dog with the hardware?

Truth be told they could fix the hardware by work or by switching the hardware.. so I guess they are really of the opinion that 12" is too big for a netbook.

Will the work to sort the poulsbo gma500 issues continue?

---

### Post by ssombra on 2009-08-13
It may sound stupid, but i installed the compiz tray icon and from there i selected compiz as window manager and emerald as window decorator (as i had it before) and everything worked again. I am starting with Linux and everything is very difficult for me.

---

### Post by tbrooks2828 on 2009-08-14
Guys.. 

Thanks for all your help so far in this thread. I am using a new hardware platform using the Intel Atom/Poulsbo solution. With your help, I've been able to install the drivers and play video correctly. It works well and looks great.

There is only one remaining issue. With the new driver, I cannot output to a DVI monitor. Output to a VGA and to LVDS monitors work great. And I see the bios and Ubuntu splash screen on the DVI monitor, but once Ubuntu comes all the way up, the DVI monitor turns off. Also note that before I installed the new driver, display to the DVI monitor worked fine.

The xrandr command returns:
Screen 0: minimum 320 x200, current 800 x 600, maximum 2080 x 1024
LVDS0 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0 mm 800x600      62.5*+
TMDS-1 disconnected (normal left inverted right x axis y axis)

I've also included my Xorg.0.log which includes a whole bunch of lines that say this:

(EE) PSB(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(EE) PSB(0): Unable to read from SDVOCTRL_E for SDVOB slave 0x70.

Any ideas?

---

### Post by JohnnyS987 on 2009-08-14
OK, here's a weird problem: After the kernel was upgraded from .13 to .14, the video won't work. It only tried to come up in a reduced-resolution mode, but fails. I can only get to a command prompt.

I reset the default kernel in grub to .13 and it boots and works, but I would rather run a current kernel.

Anyone know how to get the video to come up properly after a kernel upgrade?

> **JohnnyS987 said:**
> Isofarro,

Thank you very much for this fantastic HOWTO. This worked perfectly on my Dell Mini 12, except I booted from a USB key rather than a CD. I am very happy that the system now comes out of standby reliably, which did not happen under XP. I haven't seen any freezing or other problems.

I would suggest to the forum admin that your post be set as "sticky" at the beginning of this thread to make it easier to find. There's over 70 pages on this thread so it took me a while to find it.

JS

---

### Post by Xernie on 2009-08-14
> **ssombra said:**
> I had the same problem and i found the solution in another thread (sorry, i don't remember the exact source). You have to rebuild the module from a command prompt:

sudo dpkg-reconfigure psb-kernel-source

Hope this help.

Thanks! This worked. I actually didn't even have that package (psb-kernel-source); once I installed it I was able to boot in the new kernel. :)

> **JohnnyS987 said:**
> OK, here's a weird problem: After the kernel was upgraded from .13 to .14, the video won't work. It only tried to come up in a reduced-resolution mode, but fails. I can only get to a command prompt.

I reset the default kernel in grub to .13 and it boots and works, but I would rather run a current kernel.

Anyone know how to get the video to come up properly after a kernel upgrade?

Look at post #791 -- ssombra posted a solution to this.

---

### Post by JohnnyS987 on 2009-08-14
Thanks!

---

### Post by JohnnyS987 on 2009-08-14
Yup. That worked. Thanks!!!

---

### Post by AdamWill on 2009-08-25
some notes:

you don't need to disable DRI to prevent hangs and improve performance. The important parameter is the MigrationHeuristic one: Option "MigrationHeuristic" "greedy" . Just that parameter is enough to avoid the hangs and improve performance. Many systems also require Option "IgnoreACPI" "true" to boot at all.

The kernel module can be built on kernel 2.6.30 with a couple of trivial patches - you can get them from my Fedora .src.rpm, [http://adamwill.fedorapeople.org/poulsbo/src/psb-kmod-4.41.1-8.fc11.src.rpm](http://adamwill.fedorapeople.org/poulsbo/src/psb-kmod-4.41.1-8.fc11.src.rpm) .

---

### Post by jbernardo on 2009-08-30
Thanks Adam, thanks everyone who posted here. I have no more freezes since adding the 'Option "IgnoreACPI" "true"'. The other one (Option "MigrationHeuristic" "greedy") didn't fix the freezes.

@Adam - did you manage to enable 3D/Compositing in Fedora 11? That is what I am still missing here, as kwin effects won't work yet.

@Anyone: are you using [Alberto Milone's ppa]("https://launchpad.net/%7Ealbertomilone/+archive/poulsbo-graphics")? I wonder if it works better than the[ ubuntu-mobile]("https://launchpad.net/%7Eubuntu-mobile/+archive/ppa") one.

---

### Post by sol1tude on 2009-08-31
hi there,
i have a dell mini 12 + UNR 9.04 + poulsbo drivers from ubuntu-mobile repo. everethyng works as it should but powertop says that **psb@pci:0000:00:02.0 takes 40-60%** wakeups and my ubuntu laptop works with battery about 3hours (Windows works about 4hours). Does it normal or I can fix it?

---

### Post by AdamWill on 2009-08-31
jbernardo: yes, I have 3D acceleration working, Compiz enabled. So do others using my packages.

To whoever's running the Wiki - sorry, I seem to have screwed it up. I wanted to add links to my Fedora repo but it seems to be behaving oddly. Links you enter in Wiki format - [[http://blah.blah](http://blah.blah) foobar] - the first time show up in HTML format when you edit the page - <a href="http://blah.blah">foobar</a> - and when you save, the page starts showing the raw text of the HTML-style link. Very bizarre. Not sure what's wrong with it.

---

### Post by jbernardo on 2009-08-31
> **AdamWill said:**
> jbernardo: yes, I have 3D acceleration working, Compiz enabled. So do others using my packages.

AdamWill: I've found that compiz isn't a good indicator of working 3D acceleration, as it will work using CPU simulated compositing. The ubuntu packages allow the use of compiz, but kwin will still complain that compositing is disabled, and the effects won't work.

---

### Post by AdamWill on 2009-08-31
jbernardo: it was a compound, not a B proves A. :) I've also run a few other 3D accelerated things.

I think your experience is rather the reverse of what you think; kwin's effects not working isn't proof that 3D acceleration isn't working. Compositing isn't the same thing as 3D acceleration anyway, but the suggestion that compositing is disabled on psb seems wrong. What does 'grep -i composit /var/log/Xorg.0.log' show for you?

---

### Post by jbernardo on 2009-09-02
> **AdamWill said:**
> I think your experience is rather the reverse of what you think; kwin's effects not working isn't proof that 3D acceleration isn't working. Compositing isn't the same thing as 3D acceleration anyway, but the suggestion that compositing is disabled on psb seems wrong. What does 'grep -i composit /var/log/Xorg.0.log' show for you?

```
$ grep -i composit /var/log/Xorg.0.log
(II)         Composite (RENDER acceleration)
(II) Initializing built-in extension COMPOSITE
```

This implies that Composite should work. But, the same as for 3D, kwin doesn't like it. And for composite, kwin clearly states it is disabled. Also, using the glblur screensaver to evaluate 3D performance, I only get 16fps (even below the GMA950 on my AA1 in jaunty), which for me points to non existing hw acceleration.

---

### Post by yzarc on 2009-09-02
sorry guys,
i just installed the update of the kernel 2.6.28-15 , I already had this one installed and working. now I can't boot, after the splash, the screen just turn off. no images, no back light. 

I tried the dpkg-recomfigure on recovery mode but nothing changed. Any one had the same problem? any help?

---

### Post by jbernardo on 2009-09-02
I had that problem with 2.6.31, karmic, so I removed the mem= entry from grub and it booted again. Can you try it?

---

### Post by yzarc on 2009-09-02
the problem was with the kernel 2.6.28-15.51 so I removed it, turn down the proposed updates and reinstall the kernel. I had to reinstall also the linux-generic and psb-module.

get back to 2.6.28-15.49 solved my problem, thank you any way :)

---

### Post by jonah1980 on 2009-09-02
hey guys same problem here with the updates killing my computer. what's causing this and when will we be safe to update again?

---

### Post by jonah1980 on 2009-09-02
ps what is the command from the recovery terminal to go back to 2.6.28-15.49 kernel?

---

### Post by sirjeppe on 2009-09-03
This thread is kind of a mess unfortunately :P... It has helped me a bit but I haven't managed to get it to work when trying out all different tips and trix :(

I got as far as getting VESA drivers to work in 8.04 I think but I still couldn't watch movies in full screen which probably is expected though. But I don't want 8.04 and people seems to get 9.04 to work as well.

Do someone have clear (and structured) steps on how to get as much as possible to work in 9.04? I have just made a fresh install of Jaunty (i386) and I'm wondering what to do next.

There is talk about this Hardy lpia unr version which I haven't been able to find _anywhere_ :( The instructions in the wiki page in post no. 2 refers to this one so they don't help me I guess.

Please help me. I just had to reinstall Windows (dual boot) just to be able to watch movies and series with good quality (and in full screen). I would really appreciate any kind of help to get me rolling.

Thank you!

---

### Post by SQuark on 2009-09-03
Hey sirjeppe!

You may have better luck following the first post in this thread: [http://ubuntuforums.org/showthread.php?t=1213416](http://ubuntuforums.org/showthread.php?t=1213416)

It seems to be up to date.

To get Compiz to work, you'll have to whitelist psb. Have a look at this post for how to do that and some more optimalisations: [http://ubuntuforums.org/showpost.php?p=7775507&postcount=32](http://ubuntuforums.org/showpost.php?p=7775507&postcount=32)

But as stated above, it might not work with the latest kernel version. I haven't updated myself yet, so I can't help you there.

---

### Post by sirjeppe on 2009-09-03
Fantastic!!!

That was so easy when you have a guide ;) hehe... Thank you so much for pointing me in the right direction SQuark!

---

### Post by SQuark on 2009-09-04
Hey, my pleasure! :)

---

### Post by jonah1980 on 2009-09-04
hey any word on a fix after the update to -15.51, stuck in command prompt from recovery kernel and no idea how to go back to .49 or fix it??

---

### Post by AdamWill on 2009-09-05
it's normal for the GMA 500 to be slower than any other Intel chipset. Windows benchmarks I've seen show it at about 50% of the performance of the GMA 900.

---

### Post by mikewhatever on 2009-09-05
> **jonah1980 said:**
> hey any word on a fix after the update to -15.51, stuck in command prompt from recovery kernel and no idea how to go back to .49 or fix it??

Install the following package from command line: psb-kernel-source.
sudo apt-get install psb-kernel-source

If it is already installed, run this -> sudo dpkg-reconfigure psb-kernel-source.

---

### Post by jonah1980 on 2009-09-10
> **mikewhatever said:**
> Install the following package from command line: psb-kernel-source.
sudo apt-get install psb-kernel-source

If it is already installed, run this -> sudo dpkg-reconfigure psb-kernel-source.

that didn't work for me, just a black screen still. i ended up wget downloading the .49 kernel from backports and doing a dpkg -force-downgrade which got it working.

but today a new updated kernel came out .52, i risked installing this one and it works fine. so whatever the problem was with .51 they've now fixed it for .52 so i'm all up-to-date.

cheers for the help

---

### Post by nicolas.cadio on 2009-09-15
Hello,

I try to install the graphic acceleration with Ubuntu 9.04 on a system which has the same configuration (Intel Atom + Poulsbo).

I have installed the differents lib and bin :
    - Kernel DRM module (psb.ko)
    - GPU firmware (msvdx_fw.bin)
    - Xorg driver (psb_drv.so)
    - Xorg driver binary blob (Xpsb.so)
    - DRI interface (dri_psb.so)
    - Hardware video decode interface (psb_drv_video.so)
    - Valib aka vaapi (libva.so)
    - libDRM (libdrm.so)

This is the result of glxinfo :
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 0.1.0 psb (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tls/psb_dri.so
libGL: OpenDriver: trying /usr/lib/dri/psb_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: Searching for BusID PCI:0:2:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
libGL error:
Can't open configuration file /etc/drirc: No such file or directory.
libGL error:
Can't open configuration file /home/innes/.drirc: No such file or directory.
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
...
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
...
GLX version: 1.2
GLX extensions:
...
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) GMA500 20081116 - 5.0.1.0046 x86/MMX/SSE2
OpenGL version string: 2.0 Mesa 7.4
OpenGL shading language version string: 1.10

I think I have a problem with the function drmWaitVBlank.
If someone has the solution to repair this function, I want it.

Thanks, nicolas

---

### Post by pachistano on 2009-10-16
> **sirjeppe said:**
> This thread is kind of a mess unfortunately :P... It has helped me a bit but I haven't managed to get it to work when trying out all different tips and trix :(

I got as far as getting VESA drivers to work in 8.04 I think but I still couldn't watch movies in full screen which probably is expected though. But I don't want 8.04 and people seems to get 9.04 to work as well.

Do someone have clear (and structured) steps on how to get as much as possible to work in 9.04? I have just made a fresh install of Jaunty (i386) and I'm wondering what to do next.

There is talk about this Hardy lpia unr version which I haven't been able to find _anywhere_ :( The instructions in the wiki page in post no. 2 refers to this one so they don't help me I guess.

Please help me. I just had to reinstall Windows (dual boot) just to be able to watch movies and series with good quality (and in full screen). I would really appreciate any kind of help to get me rolling.

Thank you!

my ubuntu is working well, fullscreen and compiz and also suspend as well.
please take a look to my last posts at pages 76 more or less.
sorry for not having the time to explain again and cloosely look at to updates but my life is a little mess at the moment. just one thing: follow my instructions exactly as explained.

I wish you success.

---

### Post by ronewolf on 2009-10-16
> **pachistano said:**
> my ubuntu is working well, fullscreen and compiz and also suspend as well.
please take a look to my last posts at pages 76 more or less.

referring to pages isn't effective as the number of posts/page is settable. i think that you are referring to your post 648 and the followup 665. both much appreciated, tho i have tried it myself. 

8.04 hardy works pretty well for me, the occasional crash and problems with youTube being the only gotchas. i seem to be be stuck with this old firefox and surmise that that i need to update the OS to move to the more recent firefox. 

not a Dell Mini specific question, but is the recommended process to first install on an USB stick before migrating the upgraded OS to my (not partitioned) hard drive? if so, i'd appreciate a pointer as to how to do that.

also, is it possible to boot from sdcard? or is USB the only option (besides the hard drive, duh) for that? asking because i also should really get around to creating a recovery 'image' and i have lotsa sdcards but only a few USB sticks. is 2GB the right size for this?

---

### Post by greggh on 2009-11-01
Interesting piece about much improved GMA 500 performance under Moblin Linux.

[http://www.liliputing.com/2009/11/quake-iii-hd-video-demoed-on-netbooks-with-gma-500-graphics-moblin-linux.html](http://www.liliputing.com/2009/11/quake-iii-hd-video-demoed-on-netbooks-with-gma-500-graphics-moblin-linux.html)

> Most netbooks released over the past year have shipped with Intel Atom N270/N280 processors and GMA 950 graphics. But a handful use a different chipset designed to provide longer battery life and enhanced graphics performance. While the Intel Atom Z520/Z530 processors are noticeably more sluggish than their N2xx counterparts, the GMA 500 graphics chipset shows some promise, and some netbooks with this chipset even include HDMI ports to output HD video to an external display.

And things are starting to look even brighter for the GMA 500 chipset. This week at a Mobile Dev Camp event in Germany, Martin Mohring from the Linux Foundation demonstrated several mobile devices playing HD video and graphically intensive video games including Quake III. Probably the most impressive demo showed an MSI Wind U115 with an Atom Z530 processor and GMA 500 graphics running Quake III in HD resolutions on an external display at about 35 frames per second.

For the demo, the netbook was running Moblin Linux. As far as I know, the Windows drivers for this chipset won&#8217;t allow this kind of performance.

---

### Post by ronewolf on 2009-11-02
i've since answered a few of my own questions so thought to post the answers here.
> **ronewolf said:**
>  i seem to be be stuck with this old firefox and surmise that that i need to update the OS to move to the more recent firefox. 
despite posts elsewhere that FF should not be upgraded without a corresponding OS upgrade, the good folks at [Ubuntuzilla]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page") provide a well put together utility for both updating FF as well as keeping it updated.


> **ronewolf said:**
>  also, is it possible to boot from sdcard?
ah, sdcards appear as USB devices. is this always the case with netbooks? anyway, nice feature and i was successful in installing an image to an sdcard using unnetbootin. couldn't get the usb boot creator utility that came with 8.04 to work.


> **ronewolf said:**
>   is the recommended process to first install on an USB stick before migrating the upgraded OS to my (not partitioned) hard drive? if so, i'd appreciate a pointer as to how to do that.
so using unnetbootin i was able to get a working 9.04 on my sdcard. as i started with an .iso, this version has none of my customizations. so i'm left with two questions. 1) how to get the sdcard based OS to reflect the customizations (.conf file changes, installed/removed apps, etc). and then, once i have the system that i want and see that its working well, how do i copy that back to my hard drive?

---

### Post by 2oh1 on 2009-11-13
How can I install both Ubuntu and XP on my Mini 12?  It came with XP, but I installed Hardy on it using the instructions on post #94 in this thread.

Is it possible for me to have both XP and Jaunty?  How do I do this?  Please keep in mind that I am a total Ubuntu newbie who is equally clueless about windows.  I'm a Mac guy.

I have no problem wiping this HD out and starting from scratch here.

---

### Post by mikewhatever on 2009-11-15
> **2oh1 said:**
> How can I install both Ubuntu and XP on my Mini 12?  It came with XP, but I installed Hardy on it using the instructions on post #94 in this thread.

Is it possible for me to have both XP and Jaunty?  How do I do this?  Please keep in mind that I am a total Ubuntu newbie who is equally clueless about windows.  I'm a Mac guy.

I have no problem wiping this HD out and starting from scratch here.

Well, the basic procedure is the same for Mac, Windows and Linux. To install XP, you need to create an NTFS partition, and then install the way you would on any computer. I suggest reading up on the concept of dual booting just to get more familiar with it.
[http://www.google.com/search?btnG=1&pws=0&q=ubuntu+windows+dual+boot](http://www.google.com/search?btnG=1&pws=0&q=ubuntu+windows+dual+boot)

---

### Post by sol1tude on 2010-01-05
Hi guys. Im just discovered that the brightness can be set by FN keys.
all that you need to make FN+F9 and FN+F10 keys work on your mini 12 in Ubuntu Karmic Koala 9.10 is just edit your** /etc/default/grub** and make kernel line look like this:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_skip_timer_override"then you need 
> # update-gruband reboot your system.
nolapic allows to use dell smbios for changing backlight (brightness) in grub.
acpi_backlight=vendor allows to use your vendor's backlight system instead of default video.
I dont know why this settings are not default in Karmic. Hope you like your new FN-F9 & FN-F10 keys in 9.10 :)
acpi_skip_timer_override is dell acpi specific. this make small freezes disappear from usplash.

UPDATED

---

### Post by sol1tude on 2010-01-05
MOVED
for what is done look: [http://ubuntuforums.org/showpost.php?p=8869733&postcount=840](http://ubuntuforums.org/showpost.php?p=8869733&postcount=840)

---

### Post by modafokaxx on 2010-01-05
Ok, I'm sorry guys and girls, these is going to seem crass, but is there a simple guide/post/wiki article/whatever I can follow to update a Dell Mini 12 from stock Dell "Belmont" Ubuntu hardy 8.04 to karmic 9.10?
I'd like to update, and not reinstall, but that sounds complicated. (You're not supposed to update straight from 8.04 to 9.10, and I'm not sure I can incrementally update since the only 8.10 image I've seen is a UNR for MIDs).

I've been scouting around for quite some time now, and I'm starting to wonder if it's even worth the hassle to update, as it is my Mum's computer and she's not adamant about getting a more up to date version (though a new version of Network Manager and Firefox would be good).

I'm sure it's in this thread somewhere, but I don't have the courage to read through it all.

Anyone can point me to a clear set of instructions?
I'm not asking for something simple, just something clear. ;)

Thanks a lot everyone!

---

### Post by mocoloco on 2010-01-05
> **modafokaxx said:**
> ... Anyone can point me to a clear set of instructions?
I'm not asking for something simple, just something clear. ;)

Yes, here: [http://ubuntuforums.org/showthread.php?t=1294173]("http://ubuntuforums.org/showthread.php?t=1294173")

Easy to follow and works perfectly.  A few notes from me, I used the standard Ubuntu 9.10 (i386) disc rather than the lpia, and I didn't need to do the step to fix audio since mine already worked.  I may still go back and reinstall with lpia however since it's built for this architecture.  
The main piece I needed was step 5 for the Poulsbo graphics driver, and using the ppa method worked perfectly, (PPA says 9.04 but still works in 9.10).
Enabling compiz was neat but useless, since it freezes on resume with compiz enabled.
Use gconf-editor to set power-manager not to requre a password on resume from suspend, look in /apps/gnome-power-manager.
Last piece I was missing is brightness control, but a few replies above yours in this thread explains how to fix it.

That thread I linked to is now closed but there's a new one for feedback here [http://ubuntuforums.org/showthread.php?t=1310907]("http://ubuntuforums.org/showthread.php?t=1310907")

---

### Post by michael37 on 2010-01-06
> **modafokaxx said:**
> Ok, I'm sorry guys and girls, these is going to seem crass, but is there a simple guide/post/wiki article/whatever I can follow to update a Dell Mini 12 from stock Dell "Belmont" Ubuntu hardy 8.04 to karmic 9.10?
I'd like to update, and not reinstall, but that sounds complicated. (You're not supposed to update straight from 8.04 to 9.10, and I'm not sure I can incrementally update since the only 8.10 image I've seen is a UNR for MIDs).

I've been scouting around for quite some time now, and I'm starting to wonder if it's even worth the hassle to update, as it is my Mum's computer and she's not adamant about getting a more up to date version (though a new version of Network Manager and Firefox would be good).

I'm sure it's in this thread somewhere, but I don't have the courage to read through it all.

Anyone can point me to a clear set of instructions?
I'm not asking for something simple, just something clear. ;)

Thanks a lot everyone!

mocoloco replied with my clean install instructions, not an upgrade.  It is possible to upgrade Dellbuntu-8.04 to Dellbuntu-9.04, but not 9.10 and it's a very difficult and very creative procedure.  I would not recommend it.  Just clean-install 9.10.

---

### Post by mocoloco on 2010-01-06
I pointed out that in the guide I linked to it recommends the lpia release.  I used i386 and was thinking of reinstalling but not any more, for two reasons, based on the info in [this article]("http://www.workswithu.com/2010/01/05/benchmarking-ubuntus-lpia-build/").
[LIST=1]
[*]The benefits of the lpia build are minimal, for both speed and battery usage.
[*]Moving forward lpia will no longer be officially supported. It's possible the community will support it but combined with #1 there's no real reason to chance it and not be able to upgrade later.
[/LIST]

---

### Post by folkie on 2010-01-24
> **sol1tude said:**
> what is done (my own results) on Karmic:
- Brightness (can adjust (also with gnome applet) + dim when idle)
- Suspend \ Hibernate work very well
- WiFi / Bluetooth are working flawlessly
- Sound works good after fixing alsa-base.conf
- 2D Acceleration
- And other on-board devices working well

not working:
- 3D Acceleration (but it cat work if we broke up brightness) - system just freezes

not tested:
- Video
- HD Video
- Web camera
so I think this is same as Windows (where acceleration doesnt works too - 3fps (e.g. in Hedgewars) is NOT an acceleration). Soon I'll test videos.
if you have any questions Im ready to answer.

Could you please publish anywhere the instructions how to get all described features work well?
Because I still have problems with resuming from suspend mode and random sound dissapearing.

---

### Post by sol1tude on 2010-01-24
> **folkie said:**
> Could you please publish anywhere the instructions how to get all described features work well?
Because I still have problems with resuming from suspend mode and random sound dissapearing.
you can fix sound problems:
```

$ sudo gedit /etc/modprobe.d/alsa-base.conf

```and add to the end of file:
```
**options snd-hda-intel model=dell**
```to fix suspend\resume problems you must edit your grub configuration:
```
sudo gedit /etc/default/grub
```find line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and replace it with:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor **acpi_skip_timer_override**"                      
```and after replacing:
```
$ sudo update-grub
```and reboot your laptop.
I think all gma 500 users must just wait for [new]("http://www.phoronix.com/scan.php?page=news_item&px=NzY2MA") upcoming Intel driver :)

UPDATE 2: I've added some fix for boot and shutdown freezes**. Bold **settings is highly recommended.

---

### Post by sol1tude on 2010-02-21
Update: DO NOT USE nolapic KERNEL OPTION. It may cause 3D acceleration loss. Use only acpi_backlight=vendor to make your backlight keys working.

---

### Post by michael37 on 2010-02-21
> **sol1tude said:**
> Update: DO NOT USE nolapic KERNEL OPTION. It may cause 3D acceleration loss. Use only acpi_backlight=vendor to make your backlight keys working.

Yep yep, please click on "edit" on your previous post and correct it.

---

### Post by michael37 on 2010-02-21
*Summary of posts 828 and 836/837.*

I just discovered that the brightness can be set by FN keys.
all that you need to make FN+F9 and FN+F10 keys work on your mini 12 in Ubuntu Karmic Koala 9.10 is just edit your /etc/default/grub and make kernel line look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

```
then you need
```
$ sudo update-grub

```and reboot your system.
acpi_backlight=vendor allows to use your vendor's backlight system instead of default video.
I dont know why this settings are not default in Karmic. Hope you like your new FN-F9 & FN-F10 keys in 9.10

---

### Post by sol1tude on 2010-02-23
michael37, thank you.

Now who uses Ubuntu Karmic - please keep updated with new [settings]("http://ubuntuforums.org/showpost.php?p=8720143&postcount=835"). All they are improve stability of your laptop.

---

### Post by sol1tude on 2010-02-23
Latest achievements:

what is done (my own results) on Ubuntu Karmic 9.10 (**2.6.31-14-generic**):
- **Brightness** (can adjust (also with gnome applet) + dim when idle)
- **Suspend** \ **Hibernate**
- **WiFi** / **Bluetooth** are working flawlessly
- **Wireless** **Switcher** (out of the box from embedded software)
- **Sound** works very good after fixing alsa-base.conf
- **2D/3D** Acceleration (~280 FPS glxgeas & 29 sec gtkperf full test)
- **Video** & HD & FullHD Video
- **Web Camera** (out of the box. you can test it with cheese)
**- 3D after S3 RESUME**
- And other on-board devices working well


not working:
- 

not tested:
-

other recommendations:
- In the latest video driver installation script firefox 3.5 scrolls much smoother than before. But for perfect scroll I recommend use Chromium ([ppa]("https://launchpad.net/%7Echromium-daily/+archive/ppa")). But for best results I also recommend disable compiz. 
- Video (with totem or vlc) and compiz is not very good combination. Without compiz it works smoothly as it have to. HD Video works with mplayer only. The installation script below in this message installs mplayer & vaapi for HD video on Dell Mini 12. To watch this video you can use terminal: **mplayer -fs -vo vaapi -va vaapi HDtest.mpg**

interesting links:
- [Ubuntu Poulsbo support wiki page]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/")
- [Linux tipps]("http://linux-tipps.blogspot.com/2009/12/vaapi-accelerated-hd-video-on-msi-wind.html")

You set up video from this with [script]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/") and my previous posts.
if you have any questions Im ready to answer. Again.

---

### Post by Zagodem on 2010-03-02
I'm new to ubuntu and  the forum, just wanted to see if you all could help me with a problem..im trying to install ubuntu 8.10 on my mini 12 (it had xp before) but it only gets to the ''scanning disks'' part of the partitioner, then it simply freezes. Any ideas? thanks a bunch

---

### Post by michael37 on 2010-03-02
> **Zagodem said:**
> I'm new to ubuntu and  the forum, just wanted to see if you all could help me with a problem..im trying to install ubuntu 8.10 on my mini 12 (it had xp before) but it only gets to the ''scanning disks'' part of the partitioner, then it simply freezes. Any ideas? thanks a bunch

Simple idea: do not install 8.10.

---

### Post by tomfool on 2010-03-20
Hi to everyone!
I'm trying to run screenlet on my mini 12 using metacity wihtout compiz effects activeted,when i swicht-on metacity as compositing manager they run properly but if i try to play a video it's not fluent.Do you know why?
Another thing,when i resume from suspend the audio doesn't work.
Thanks
I'm italian so if my english is bad help me to improve it!;)

---

### Post by fitzkarraldo on 2010-03-20
> **tomfool said:**
> Hi to everyone!
I'm trying to run screenlet on my mini 12 using metacity wihtout compiz effects activeted,when i swicht-on metacity as compositing manager they run properly but if i try to play a video it's not fluent.Do you know why?
Another thing,when i resume from suspend the audio doesn't work.
Thanks
I'm italian so if my english is bad help me to improve it!;)

suspend works fine for me, on kernel 2.6.31-20, adding these options to boot
acpi_backlight=vendor acpi_skip_timer_override

---

### Post by sol1tude on 2010-03-21
> **tomfool said:**
> Hi to everyone!
I'm trying to run screenlet on my mini 12 using metacity wihtout compiz effects activeted,when i swicht-on metacity as compositing manager they run properly but if i try to play a video it's not fluent.Do you know why?
Another thing,when i resume from suspend the audio doesn't work.
Thanks
I'm italian so if my english is bad help me to improve it!;)
please, read this thread carefully and add kernel options suggested by [fitzkarraldo]("http://ubuntuforums.org/member.php?u=785749").
about sound: this is a 'hda-intel: spurious response' bug and nobody knows how to fix it [not fixed neither by ubuntu community nor by intel]
someone says that adding to /etc/modprobe.d/alsa-base.conf 'options snd-hda-intel model=acer' works but not for me. it works until I resume from suspend. but it is better than nothing: without this line you may lose your sound right in any moment.

---

### Post by fitzkarraldo on 2010-03-21
> **sol1tude said:**
> 
about sound: this is a 'hda-intel: spurious response' bug and nobody knows how to fix it [not fixed neither by ubuntu community nor by intel]
someone says that adding to /etc/modprobe.d/alsa-base.conf 'options snd-hda-intel model=acer' works but not for me. it works until I resume from suspend. but it is better than nothing: without this line you may lose your sound right in any moment.

sol1tude, 
sound problem was solved on my machine in this way:
* upgrade alsa to 1.0.22.1, you can compile it or upgrade through backports
* add this line to /etc/modprobe.d/alsa-base.conf 
options snd-hda-intel model=dell

after this changes sound works fine, even after suspend/hibernate.

hope it helps!

---

### Post by 2oh1 on 2010-04-29
10.4 on the mini 12?  Jolicloud works out of the box (it seems that everything works except for the ability to change screen resolutions).  I'm hoping that means the latest Ubuntu works too!  Does it?

---

### Post by jbernardo on 2010-04-29
Many users are trying... You can follow our efforts to port mandriva's patches on[ this thread.]("http://ubuntuforums.org/showthread.php?p=9195428#post9195428")

---

### Post by mikewhatever on 2010-04-30
> **2oh1 said:**
> 10.4 on the mini 12?  Jolicloud works out of the box (it seems that everything works except for the ability to change screen resolutions).  I'm hoping that means the latest Ubuntu works too!  Does it?

No, at least not yet. The only reason Jolicloud works is because its xserver is an older version, 1.6.4, same as in Karmic.

---

### Post by modafokaxx on 2010-05-31
Any news on Lucid on the Mini 12?

I'll check the GMA500 thread too, but I'm hoping to get a quick answer if anyone knows… :)

---

### Post by fitzkarraldo on 2010-06-01
> **modafokaxx said:**
> Any news on Lucid on the Mini 12?

I'll check the GMA500 thread too, but I'm hoping to get a quick answer if anyone knows… :)

Support is still not complete but I'm using Lucid on my Mini 12 since several weeks, look here for more info
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#lucid](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#lucid)

---

### Post by greggish on 2010-07-01
> **fitzkarraldo said:**
> Support is still not complete but I'm using Lucid on my Mini 12 since several weeks, look here for more info
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#lucid](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#lucid)

From the wiki instructions for Lucid:

> this command will add 'GMA500 PPA' repository and update database

sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config

Since 3d is still broken wouldn't it be better to skip the "poulsbo-driver-3d" part and just type:

sudo apt-get install poulsbo-driver-2d poulsbo-config ?

---

### Post by Flonak on 2010-07-02
Installing the 3D package doesn't break anything and allows you to get the 3D to work as soon as the functionnality is released by just apt-get upgrade your system.

---

### Post by pjman on 2010-08-05
> **fitzkarraldo said:**
> sol1tude, 
sound problem was solved on my machine in this way:
* upgrade alsa to 1.0.22.1, you can compile it or upgrade through backports
* add this line to /etc/modprobe.d/alsa-base.conf 
options snd-hda-intel model=dell

after this changes sound works fine, even after suspend/hibernate.

hope it helps!

I don't see an upgraded version of alsa (1.0.22.1) in backports for karmic. Is there a ppa  that you had to add first?

---

### Post by maddentim on 2010-08-06
@pjman, I didn't find a repo, but here is a decent guide to install from source: [http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/]("http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/")

---

### Post by yvesdm3000 on 2011-01-22
I'm going to upgrade my tablet from 10.04 to 10.10. What is the current status and is there anything that needs fixing to make it work (and that is not in the binary blob of course) ?

This thread is immensely long and I think I can spend my time better than reading pages and pages...

I remember there was an issue where Xorg crashed in our driver and has a workaround in the poulsbo-config, is that still pending ?

-Yves

---

### Post by pjman on 2011-01-22
Yves - the wiki probably has the most stable info.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

Also, there is another thread that seems to be updated quite often on progress: [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345)

Good luck!

---

### Post by JohnnyS987 on 2011-03-12
Just a note: I had a problem today when I updated my "pm-utils" package from 1.3.1 to 1.4.1 in "Update Manager". It broke suspend/resume and bluetooth.

So, I did a "reinstall" of the poulsbo stuff as follows:

sudo apt-get install psb-kernel-source --reinstall
sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config --reinstall

This seems to have fixed my suspend/resume problems and my bluetooth mouse now works.

Ubuntu version: 10.10
uname-a output: Linux wj-Mini-12 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 GNU/Linux

I hope this is useful to someone. :)

---

