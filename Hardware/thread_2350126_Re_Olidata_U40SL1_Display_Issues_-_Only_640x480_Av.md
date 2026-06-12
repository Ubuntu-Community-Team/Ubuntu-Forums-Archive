---
title: "Re: Olidata U40SL1 Display Issues - Only 640x480 Available"
date: 2017-01-21
forum: Hardware
---

### Post by lah-ca on 2017-01-21
[SIZE=5]**Edit:  See end of thread for summary**[/SIZE]

Hi,

I have been volunteering refurbing older computers for needy people.

I have received a donation of an Olidata U40SL1 notebook. The U40SL1 appears to have been made by ECS in China for sale under their own name, as well as for Olidata, an Italian company, and for Uniwill.  The model number occurs most commonly under these three badges.  It might also have been sold as an OEM whitebox item.  It is an extreme-ultra-low budget model with a Centrino Celeron proc and 1Gb of RAM.  Olidata seems to have sold a lot of them in South America, Chile in particular - the one I have in hand has a Spanish keyboard, and it came with Vista Starter 32 bit (Spanish) installed.  Some seem to have had XP.  

I believe the MOBO has a SIS chipset but I could be wrong.  

Tech support forums seem to have posts in Spanish from a lot of people looking, unsuccessfully, for Win 7 drivers.  Nobody seems to offer any support for this model.  Zip, Zilch, Nada!

The live disk of Ubuntu 16.04 64 bit boots, but there are warnings about video being rendered in software mode since there are no drivers.  There is also no wireless NIC support.  I booted to the xUbuntu 32 bit live disk and things seemed better.  The wireless NIC worked.  The screen res looked better. So I installed it.

Most everything seems to work adequately well, all considered, about as well as with xUbuntu on an underpowered netbook, but there is a problem with video display resolution, 640x480 only.  At this resolution, the system is unusable, except by terminal, since the buttons for pretty much everything in dialogue boxes are unreachable, off-screen.

Any ideas? Should I just send this one off for ethical recycling?

Using Google translate, I find that the Olidata U40SL1 has a Sis Mirage 3+ video chipset.  And therein, perhaps, lies the problem.

---

### Post by Autodave on 2017-01-21
Have you let the machine look for a driver itself?  Go to *Settings ->* Software & Updates -> Additional Drivers. Let it search to see if it finds one. If it does, use the recommended one.

---

### Post by lah-ca on 2017-01-21
> **Autodave said:**
> Have you let the machine look for a driver itself?  Go to *Settings ->* Software & Updates -> Additional Drivers. Let it search to see if it finds one. If it does, use the recommended one.

Hi.

Yes, I have checked for proprietary drivers.  But there was only the Intel Microcode for proc support available.

The big problem is the SIS Mirage 3+ video chipset.  It is just not supported, not even for Windows any more, I think.  Some people managed to get it working in older versions of Linux through a lot of command line work, but .... is it really worth the effort, even if it were possible with more recent distros?

The next problem is the Celeron M @ 1.7 GHz.  It is completely inadequate for the bloatware world we live in.

The donor has given his blessing for sending this off to FreeGeek for ethical recycling, which is probably what I will do unless someone has a magic wand to offer. 

Thanks for the reply.

---

### Post by wildmanne39 on 2017-01-21
I had to retire my old dell a long time ago that had SIS graphics like you said they have not been supported for a very long time.

---

### Post by mörgæs on 2017-01-22
Let's see the exact hardware before jumping to conclusions. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Yellow Pasque on 2017-01-22
Usually 640x480 means fbdev driver is being loaded. You should be able to get a better resolution with generic vesa driver. Make an /etc/X11/xorg.conf file with a text editor. Copy/paste the block of text below:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```


**If** it is SiS graphics, you will not get 3D acceleration. If you are not satisfied with the performance of the generic vesa driver (i.e. basic graphics operations such as moving windows are slow), you can try to get some 2D acceleration by building the SiS driver:
```
sudo apt-get install build-essential xorg-dev
cd ~/   #or whatever directory you want to use for this build
wget http://xorg.freedesktop.org/releases/individual/driver/xf86-video-sis-0.10.9.tar.bz2
tar xjf xf86-video-sis-0.10.9.tar.bz2
cd xf86-video-sis-0.10.9/
./configure --prefix=/usr/local
make
sudo make install
```

Then use the xorg.conf given above, except you will specify Driver "sis" instead of Driver "vesa"

---

### Post by lah-ca on 2017-01-22
> **mörgæs said:**
> Let's see the exact hardware before jumping to conclusions. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Hi.

Thanks for the reply.  The notebook has a SIS 771/671 video chipset, which means that the display might be improved by a workaround ( [http://askubuntu.com/questions/455888/low-resolution-on-lubuntu-14-04-sis](http://askubuntu.com/questions/455888/low-resolution-on-lubuntu-14-04-sis) ) or by trying to install the Xorg drivers ( [http://askubuntu.com/questions/362792/how-to-install-sis-771-671-video-drivers-on-13-10](http://askubuntu.com/questions/362792/how-to-install-sis-771-671-video-drivers-on-13-10) ).  Downloading and compiling SIS Linux drivers does not seem to be an option since only the 650/740 and 630/730 chipsets are support by SIS anymore.

Anyway ... the interesting bits from lshw:

```
computer
    description: Computer
    product: 671MX
    vendor: SiS
    width: 32 bits
    capabilities: smbios-2.5 smp-1.4 smp
    configuration: cpus=2
  *-core
       description: Motherboard
       physical id: 0
     *-cpu:0
          product: Genuine Intel(R) CPU           T1400  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.15.13
          serial: [REMOVED]
          size: 200MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: [REMOVED]
          size: 350MHz
          capabilities: ht
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-memory
          description: System memory
          physical id: 2
          size: 1019MiB

```

```

 *-display UNCLAIMED
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff memory:b0000000-b001ffff ioport:9000(size=128)

```

The notebook also has a 150 Gb hard drive, Toshiba, a Gigabit NIC, SIS, and a USB IEEE 802.11bg wireless NIC, probably SIS, but the hardware manufacturer is not listed - if it were important to know, I could look up the vendor ID with the first half of the MAC address, I guess.

BTW: very nice thread on *bringing old hardware back to life*!

> **Temüjin said:**
> Usually 640x480 means fbdev driver is being loaded. You should be able to get a better resolution with generic vesa driver. Make an /etc/X11/xorg.conf file with a text editor. 


> **Temüjin said:**
> **If** it is SiS graphics, you will not get 3D acceleration. If you are not satisfied with the performance of the generic vesa driver (i.e. basic graphics operations such as moving windows are slow), you can try to get some 2D acceleration by building the SiS driver:

Then use the xorg.conf given above, except you will specify Driver "sis" instead of Driver "vesa"

Thanks for the reply.  You posted this while I was responding to mörgæs, the helpful Icelandic penguin.

There is a blog here on the SIS support issue: [https://jrlinuxmint.wordpress.com](https://jrlinuxmint.wordpress.com)  It is now out of date for all current Ubuntu and Ubuntu-based distros, and it is based on the acknowledged work of a Brazillian, Hugo Bastos, in Portuguese.  I like the blogger's preamble:
The only reason for the creation of this blog is to help my fellow Linux friends out there with setting up a driver that works in Linux for the ill-famed SiS chipsets of the 671 / 672 / M672 / 771 / 772 & 717 family of video chipsets. These chips are notorious for not having decent drivers for Linux released by Silicon Integrated Systems (SiS), which is surprising, given the numbers of chips sold by SiS worldwide and the fact that anyone migrating to Linux and pestered by the absence of support to their chipsets will surely think twice before ever buying any kind of product with any kind of chip produced by SIS – it is the kind of attitude that really destroy the reputation of any company.

---

### Post by Yellow Pasque on 2017-01-22
^I'm not really sure what your point is with that post. It is not going to help you to google old rants about SiS' non-existent Linux support. They exited the x86 chipset business a long time ago anyway.

Try the "vesa" method I posted in my example xorg.conf or in the link you found. [http://askubuntu.com/a/462144](http://askubuntu.com/a/462144)
(They are two slightly different methods to accomplish the same thing.) Does it give you the same resolution as the Xubuntu Liveboot or not?

---

### Post by lah-ca on 2017-01-22
> **Temüjin said:**
> ^I'm not really sure what your point is with that post. 

To be honest, neither am I, actually.  But there is a point somewhere here, I guess, although, I freely acknowledge that this is not the place for an extended discussion of it.  PC sales, notebooks and desktops, keep plummeting, year after year, reaching ever new lows.  And as they do, it is the corporate world, gamers and Linux users who are the life-support system for the PC world.  Linux users become less and less marginal to the shrinking business of PC manufacturers. They need to take notice.

> **Temüjin said:**
> Try the "vesa" method I posted in my example xorg.conf or in the link you found. [http://askubuntu.com/a/462144](http://askubuntu.com/a/462144)
(They are two slightly different methods to accomplish the same thing.) Does it give you the same resolution as the Xubuntu Liveboot or not?

Thanks. I will.  And I will report back.

---

### Post by lah-ca on 2017-01-22
> **Temüjin said:**
> Try the "vesa" method I posted in my example xorg.conf or in the link you found. [http://askubuntu.com/a/462144](http://askubuntu.com/a/462144)
(They are two slightly different methods to accomplish the same thing.) Does it give you the same resolution as the Xubuntu Liveboot or not?

Hi.  

I used your suggestion, since it seemed the simpler and more direct option. 

Apart from me being an idiot and typing out the xorg.conf file (incorrectly), rather than using copy and paste, and thereby crashing the X server and then having to boot to the live disk to repair my ineptness, things seem to have gone quite well. 

***Initially*** during boot now, the system does not give the same resolution as  liveboot - it still looks quite low res.  But later in the boot process, things change, and by the time I get a desktop GUI to log into, I have 1024x768 resolution.  Thanks.  Cool.

I will update the system and test this fix.  I will probably experiment with the XORG SIS drivers, as well to see what the computer can do, if anything, with video, Flash, etc. 

More later.

Thanks, again.

---

### Post by lah-ca on 2017-01-23
Well... display performance with the vesa drivers is a 1000% better now, but it is still a bit marginal.  Standard recreational things such as Youtube clips and video clips on news sites mostly work if not maximized to full screen - there is only minor pixelation and only very occasional lagging or frame skipping.  At full screen, video breaks up badly and/or freezes and skips while sound continues on in real time.  DVD playback is only possible in a small window.  Moving, opening and closing windows and such works reasonably well.  

Interestingly, the sound card was not working.  I had failed to notice this earlier.  I had to force reload alsa to get it working.

The system as a whole is a bit marginal with XUbuntu.  It ***really struggles*** to load bloated web pages, for example.  It would work well enough for email and light word processing and such.  But most users, even desperately poor users, like to web surf, and for many people new to Canada, the Internet (social media) is a life line to friends and family.

I am reluctant to send this little beast for recycling just yet, because it is in like-new condition and because the battery is in really, really good shape.

So, I think I will reload it with LUbuntu and try the XOrg SIS drivers.  I will probably use the MVPS "there's no place like 127.0.0.1" modified hosts file to improve web performance (by referring URLs for ad and tracking sites to local host) and see how that works.  

More later.

---

### Post by mörgæs on 2017-01-23
The lshw output showed that there was only 1 GB of memory. Another GB will make a big difference.

---

### Post by lah-ca on 2017-01-23
> **mörgæs said:**
> The lshw output showed that there was only 1 GB of memory. Another GB will make a big difference.

Yes.  

Unfortunately, I have been getting rid of my personal stock of old stuff.  I no longer have any SODIMMs.  Anything useful, I donated to various places. 

I have not taken the laptop apart, yet, but from a superficial examination it looks like the RAM slots might be under the keyboard - not optimal if special tools are required.

I will examine further.

---

### Post by lah-ca on 2017-01-23
Well. ... the system is much peppier with LUbuntu 16.04.  I have not done a lot of testing, yet, though.

At present, I am using the vesa drivers because I cannot get the XORG SIS drivers compiled and installed.

The advice here: [http://askubuntu.com/questions/362792/how-to-install-sis-771-671-video-drivers-on-13-10](http://askubuntu.com/questions/362792/how-to-install-sis-771-671-video-drivers-on-13-10)

```
#to use
sudo apt-get install xserver-xorg-video-sis
#is obsolete.  And does not work in 16.04
```

The advice offered by Temüjin above is also out of date and my also not work in LUbuntu

```
sudo apt-get install build-essential xorg-dev 
#works just fine


cd ~/   #or whatever directory you want to use for this build 
#no problem


wget http://xorg.freedesktop.org/releases/individual/driver/xf86-video-sis-0.10.9.tar.bz2
#obsolete location.  manually downloaded from another x.org page.

tar xjf xf86-video-sis-0.10.9.tar.bz2
#would not run. many errors. used archive manager


cd xf86-video-sis-0.10.9
#no problem


./configure --prefix=/usr/local
#failed.  many errors.


make
#dependant upon success of above command so failed.


sudo make install
#dependant upon success of above command so failed.

```

Any further suggestions on trying the XORG SIS drivers?  Thanks.

---

### Post by lah-ca on 2017-01-23
OK.  I have to retract my statement about [http://xorg.freedesktop.org/archive/individual/driver/xf86-video-sis-0.10.7.tar.bz2](http://xorg.freedesktop.org/archive/individual/driver/xf86-video-sis-0.10.7.tar.bz2) being an obsolete URL.  It isn't.  And it works with wget on my 16.04 desktop.  Weird.

More information here: [http://www.linuxfromscratch.org/blfs/view/7.6/x/x7driver.html](http://www.linuxfromscratch.org/blfs/view/7.6/x/x7driver.html)

They say:

```
patch -Np1 -i ../xf86-video-sis-0.10.7-upstream_fixes-1.patch &&
./configure $XORG_CONFIG &&

make
```

Then as root:

```
make install
```

Thoughts?

---

### Post by lah-ca on 2017-01-23
OK.  Figured out where I went wrong with:

```
sudo apt-get install build-essential xorg-dev
cd ~/   #or whatever directory you want to use for this build
wget http://xorg.freedesktop.org/releases/individual/driver/xf86-video-sis-0.10.9.tar.bz2
tar xjf xf86-video-sis-0.10.9.tar.bz2
cd xf86-video-sis-0.10.9/
./configure --prefix=/usr/local
make
sudo make install

```

The issue was:

```
cd ~/   #or whatever directory you want to use for this build
```

Specifically: "or whatever directory you want to use for this build"

When I choose the home folder root, it all works.

But when I change the xorg.conf file from "vesa" to "sis" and reboot, we are back at 648 x 480 resolution.

So back to vesa for the moment.

---

### Post by lah-ca on 2017-01-23
> **mörgæs said:**
> The lshw output showed that there was only 1 GB of memory. Another GB will make a big difference.

I broke the Olidata warranty seal!  Oh no!  

There are two RAM slots, but only one is functional and accessible, meaning that the plastic block has two slots for RAM but the second slot does not appear to wired up nor are there any clips on that slot, not that you could get a SODIMM into it any as there is other hardware blocking the space.  Anyway 2 Gb DDR2 SODIMMs are alarmingly expensive new and extremely rare used - none locally on Craigslist.  I have checked all my usual sources for free stuff, as well.  I think the notebook is going to have live with just 1Gb unless something falls into my hands.

---

### Post by Yellow Pasque on 2017-01-23
> **lah-ca said:**
> But when I change the xorg.conf file from "vesa" to "sis" and reboot, we are back at 640 x 480 resolution.
Can we see an xorg log from when you try to use sis?

---

### Post by lah-ca on 2017-01-24
> **Temüjin said:**
> Can we see an xorg log from when you try to use sis?

But of course.  Here it is in is entirity.  The sis module appears not to exist.

```
    
Information    [    26.311] 
    Information    X.Org X Server 1.18.4
    Information    Release Date: 2016-07-19
    Information    [    26.311] X Protocol Version 11, Revision 0
    Information    [    26.311] Build Operating System: Linux 4.4.0-45-generic i686 Ubuntu
    Information    [    26.311] Current Operating System: Linux U40SI1 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:36:54 UTC 2017 i686
    Information    [    26.311] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-59-generic root=UUID=25c4ce11-d11a-47a0-8c1a-1fc39014f073 ro quiet splash vt.handoff=7
    Information    [    26.311] Build Date: 02 November 2016  10:05:16PM
    Information    [    26.311] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
    Information    [    26.311] Current version of pixman: 0.33.6
    Information    [    26.311]     Before reporting problems, check http://wiki.x.org
    Information        to make sure that you have the latest version.
    Information    [    26.311] Markers: (--) probed, (**) from config file, (==) default setting,
    Information        (++) from command line, (!!) notice, (II) informational,
    Information        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
    Information    [    26.311] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 24 08:26:30 2017
    Information    [    26.312] (==) Using config file: "/etc/X11/xorg.conf"
    Information    [    26.312] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
    Information    [    26.313] (==) No Layout section.  Using the first Screen section.
    Information    [    26.313] (**) |-->Screen "Default Screen" (0)
    Information    [    26.313] (**) |   |-->Monitor "Configured Monitor"
    Information    [    26.324] (**) |   |-->Device "Configured Video Device"
    Information    [    26.324] (==) Automatically adding devices
    Information    [    26.324] (==) Automatically enabling devices
    Information    [    26.324] (==) Automatically adding GPU devices
    Information    [    26.324] (==) Max clients allowed: 256, resource mask: 0x1fffff
    Information    [    26.324] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Information    [    26.324]     Entry deleted from font path.
    Information    [    26.324] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
    Information    [    26.324]     Entry deleted from font path.
    Information    [    26.324] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
    Information    [    26.324]     Entry deleted from font path.
    Information    [    26.324] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
    Information    [    26.324]     Entry deleted from font path.
    Information    [    26.324] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
    Information    [    26.324]     Entry deleted from font path.
    Information    [    26.324] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
    Information    [    26.324]     Entry deleted from font path.
    Information    [    26.324] (==) FontPath set to:
    Information        /usr/share/fonts/X11/misc,
    Information        built-ins
    Information    [    26.324] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
    Information    [    26.324] (II) The server relies on udev to provide the list of input devices.
    Information        If no devices become available, reconfigure udev or disable AutoAddDevices.
    Information    [    26.333] (II) Loader magic: 0x802df700
    Information    [    26.333] (II) Module ABI versions:
    Information    [    26.333]     X.Org ANSI C Emulation: 0.4
    Information    [    26.333]     X.Org Video Driver: 20.0
    Information    [    26.333]     X.Org XInput driver : 22.1
    Information    [    26.333]     X.Org Server Extension : 9.0
    Information    [    26.335] (++) using VT number 7
    Information    
    Information    [    26.335] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
    Information    [    26.336] (--) PCI:*(0:1:0:0) 1039:6351:1019:5050 rev 16, Mem @ 0xc0000000/268435456, 0xb0000000/131072, I/O @ 0x00009000/128
    Information    [    26.341] (II) LoadModule: "glx"
    Information    [    26.351] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
    Information    [    26.577] (II) Module glx: vendor="X.Org Foundation"
    Information    [    26.577]     compiled for 1.18.4, module version = 1.0.0
    Information    [    26.577]     ABI class: X.Org Server Extension, version 9.0
    Information    [    26.577] (==) AIGLX enabled
    Information    [    26.577] (II) LoadModule: "sis"
    Information    [    26.578] (WW) Warning, couldn't open module sis
    Information    [    26.578] (II) UnloadModule: "sis"
    Information    [    26.578] (II) Unloading sis
    Information    [    26.578] (EE) Failed to load module "sis" (module does not exist, 0)
    Information    [    26.578] (==) Matched sis as autoconfigured driver 0
    Information    [    26.578] (==) Matched modesetting as autoconfigured driver 1
    Information    [    26.578] (==) Matched fbdev as autoconfigured driver 2
    Information    [    26.578] (==) Matched vesa as autoconfigured driver 3
    Information    [    26.578] (==) Assigned the driver to the xf86ConfigLayout
    Information    [    26.578] (II) LoadModule: "sis"
    Information    [    26.578] (WW) Warning, couldn't open module sis
    Information    [    26.578] (II) UnloadModule: "sis"
    Information    [    26.579] (II) Unloading sis
    Information    [    26.579] (EE) Failed to load module "sis" (module does not exist, 0)
    Information    [    26.579] (II) LoadModule: "modesetting"
    Information    [    26.579] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
    Information    [    26.592] (II) Module modesetting: vendor="X.Org Foundation"
    Information    [    26.592]     compiled for 1.18.4, module version = 1.18.4
    Information    [    26.592]     Module class: X.Org Video Driver
    Information    [    26.592]     ABI class: X.Org Video Driver, version 20.0
    Information    [    26.592] (II) LoadModule: "fbdev"
    Information    [    26.592] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
    Information    [    26.600] (II) Module fbdev: vendor="X.Org Foundation"
    Information    [    26.600]     compiled for 1.18.1, module version = 0.4.4
    Information    [    26.600]     Module class: X.Org Video Driver
    Information    [    26.600]     ABI class: X.Org Video Driver, version 20.0
    Information    [    26.600] (II) LoadModule: "vesa"
    Information    [    26.600] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
    Information    [    26.600] (II) Module vesa: vendor="X.Org Foundation"
    Information    [    26.600]     compiled for 1.18.1, module version = 2.3.4
    Information    [    26.600]     Module class: X.Org Video Driver
    Information    [    26.600]     ABI class: X.Org Video Driver, version 20.0
    Information    [    26.600] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
    Information    [    26.600] (II) FBDEV: driver for framebuffer: fbdev
    Information    [    26.600] (II) VESA: driver for VESA chipsets: vesa
    Information    [    26.601] (EE) open /dev/dri/card0: No such file or directory
    Information    [    26.601] (WW) Falling back to old probe method for modesetting
    Information    [    26.601] (EE) open /dev/dri/card0: No such file or directory
    Information    [    26.601] (II) Loading sub module "fbdevhw"
    Information    [    26.601] (II) LoadModule: "fbdevhw"
    Information    [    26.601] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
    Information    [    26.614] (II) Module fbdevhw: vendor="X.Org Foundation"
    Information    [    26.614]     compiled for 1.18.4, module version = 0.0.2
    Information    [    26.614]     ABI class: X.Org Video Driver, version 20.0
    Information    [    26.614] (**) FBDEV(1): claimed PCI slot 1@0:0:0
    Information    [    26.614] (II) FBDEV(1): using default device
    Information    [    26.614] (WW) Falling back to old probe method for vesa
    Information    [    26.614] (EE) Screen 0 deleted because of no matching config section.
    Information    [    26.614] (II) UnloadModule: "modesetting"
    Information    [    26.614] (II) FBDEV(0): Creating default Display subsection in Screen section
    Information        "Default Screen" for depth/fbbpp 24/32
    Information    [    26.614] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
    Information    [    26.614] (==) FBDEV(0): RGB weight 888
    Information    [    26.614] (==) FBDEV(0): Default visual is TrueColor
    Information    [    26.614] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
    Information    [    26.614] (II) FBDEV(0): hardware: VESA VGA (video memory: 1216kB)
    Information    [    26.614] (II) FBDEV(0): checking modes against framebuffer device...
    Information    [    26.614] (II) FBDEV(0): checking modes against monitor...
    Information    [    26.614] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
    Information    [    26.614] (**) FBDEV(0):  Built-in mode "current": 30.7 MHz, 36.9 kHz, 73.3 Hz
    Information    [    26.614] (II) FBDEV(0): Modeline "current"x0.0   30.72  640 672 752 832  480 484 488 504 -hsync -vsync -csync (36.9 kHz b)
    Information    [    26.614] (==) FBDEV(0): DPI set to (96, 96)
    Information    [    26.614] (II) Loading sub module "fb"
    Information    [    26.614] (II) LoadModule: "fb"
    Information    [    26.615] (II) Loading /usr/lib/xorg/modules/libfb.so
    Information    [    26.629] (II) Module fb: vendor="X.Org Foundation"
    Information    [    26.629]     compiled for 1.18.4, module version = 1.0.0
    Information    [    26.629]     ABI class: X.Org ANSI C Emulation, version 0.4
    Information    [    26.629] (**) FBDEV(0): using shadow framebuffer
    Information    [    26.629] (II) Loading sub module "shadow"
    Information    [    26.629] (II) LoadModule: "shadow"
    Information    [    26.630] (II) Loading /usr/lib/xorg/modules/libshadow.so
    Information    [    26.630] (II) Module shadow: vendor="X.Org Foundation"
    Information    [    26.630]     compiled for 1.18.4, module version = 1.1.0
    Information    [    26.630]     ABI class: X.Org ANSI C Emulation, version 0.4
    Information    [    26.630] (II) UnloadModule: "vesa"
    Information    [    26.630] (II) Unloading vesa
    Information    [    26.630] (==) Depth 24 pixmap format is 32 bpp
    Information    [    26.630] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
    Information    [    26.656] (==) FBDEV(0): Backing store enabled
    Information    [    26.659] (==) FBDEV(0): DPMS enabled
    Information    [    26.659] (==) RandR enabled
    Information    [    26.676] (II) SELinux: Disabled on system
    Information    [    26.679] (II) AIGLX: Screen 0 is not DRI2 capable
    Information    [    26.679] (EE) AIGLX: reverting to software rendering
    Information    [    27.457] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
    Information    [    27.459] (II) AIGLX: Loaded and initialized swrast
    Information    [    27.459] (II) GLX: Initialized DRISWRAST GL provider for screen 0
    Information    [    27.582] (II) config/udev: Adding input device Power Button (/dev/input/event3)
    Information    [    27.582] (**) Power Button: Applying InputClass "evdev keyboard catchall"
    Information    [    27.582] (II) LoadModule: "evdev"
    Information    [    27.583] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
    Information    [    27.603] (II) Module evdev: vendor="X.Org Foundation"
    Information    [    27.603]     compiled for 1.18.1, module version = 2.10.1
    Information    [    27.603]     Module class: X.Org XInput Driver
    Information    [    27.603]     ABI class: X.Org XInput driver, version 22.1
    Information    [    27.603] (II) Using input driver 'evdev' for 'Power Button'
    Information    [    27.603] (**) Power Button: always reports core events
    Information    [    27.603] (**) evdev: Power Button: Device: "/dev/input/event3"
    Information    [    27.603] (--) evdev: Power Button: Vendor 0 Product 0x1
    Information    [    27.603] (--) evdev: Power Button: Found keys
    Information    [    27.603] (II) evdev: Power Button: Configuring as keyboard
    Information    [    27.603] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
    Information    [    27.603] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
    Information    [    27.603] (**) Option "xkb_rules" "evdev"
    Information    [    27.603] (**) Option "xkb_model" "pc105"
    Information    [    27.603] (**) Option "xkb_layout" "us"
    Information    [    27.605] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
    Information    [    27.605] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
    Information    [    27.605] (II) Using input driver 'evdev' for 'Video Bus'
    Information    [    27.605] (**) Video Bus: always reports core events
    Information    [    27.605] (**) evdev: Video Bus: Device: "/dev/input/event5"
    Information    [    27.605] (--) evdev: Video Bus: Vendor 0 Product 0x6
    Information    [    27.605] (--) evdev: Video Bus: Found keys
    Information    [    27.605] (II) evdev: Video Bus: Configuring as keyboard
    Information    [    27.605] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:0b/LNXVIDEO:00/input/input10/event5"
    Information    [    27.605] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
    Information    [    27.606] (**) Option "xkb_rules" "evdev"
    Information    [    27.606] (**) Option "xkb_model" "pc105"
    Information    [    27.606] (**) Option "xkb_layout" "us"
    Information    [    27.607] (II) config/udev: Adding input device Power Button (/dev/input/event0)
    Information    [    27.607] (**) Power Button: Applying InputClass "evdev keyboard catchall"
    Information    [    27.607] (II) Using input driver 'evdev' for 'Power Button'
    Information    [    27.607] (**) Power Button: always reports core events
    Information    [    27.607] (**) evdev: Power Button: Device: "/dev/input/event0"
    Information    [    27.607] (--) evdev: Power Button: Vendor 0 Product 0x1
    Information    [    27.607] (--) evdev: Power Button: Found keys
    Information    [    27.607] (II) evdev: Power Button: Configuring as keyboard
    Information    [    27.607] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
    Information    [    27.607] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
    Information    [    27.607] (**) Option "xkb_rules" "evdev"
    Information    [    27.607] (**) Option "xkb_model" "pc105"
    Information    [    27.607] (**) Option "xkb_layout" "us"
    Information    [    27.609] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
    Information    [    27.609] (II) No input driver specified, ignoring this device.
    Information    [    27.609] (II) This device may have been added with another device file.
    Information    [    27.610] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
    Information    [    27.610] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
    Information    [    27.610] (II) Using input driver 'evdev' for 'Sleep Button'
    Information    [    27.610] (**) Sleep Button: always reports core events
    Information    [    27.610] (**) evdev: Sleep Button: Device: "/dev/input/event1"
    Information    [    27.610] (--) evdev: Sleep Button: Vendor 0 Product 0x3
    Information    [    27.610] (--) evdev: Sleep Button: Found keys
    Information    [    27.610] (II) evdev: Sleep Button: Configuring as keyboard
    Information    [    27.610] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
    Information    [    27.610] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
    Information    [    27.610] (**) Option "xkb_rules" "evdev"
    Information    [    27.610] (**) Option "xkb_model" "pc105"
    Information    [    27.610] (**) Option "xkb_layout" "us"
    Information    [    27.612] (II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event9)
    Information    [    27.612] (**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
    Information    [    27.612] (II) Using input driver 'evdev' for 'USB 2.0 Camera'
    Information    [    27.612] (**) USB 2.0 Camera: always reports core events
    Information    [    27.612] (**) evdev: USB 2.0 Camera: Device: "/dev/input/event9"
    Information    [    27.612] (--) evdev: USB 2.0 Camera: Vendor 0xc45 Product 0x62c0
    Information    [    27.612] (--) evdev: USB 2.0 Camera: Found keys
    Information    [    27.612] (II) evdev: USB 2.0 Camera: Configuring as keyboard
    Information    [    27.612] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.3/usb1/1-7/1-7:1.0/input/input17/event9"
    Information    [    27.612] (II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD, id 10)
    Information    [    27.612] (**) Option "xkb_rules" "evdev"
    Information    [    27.612] (**) Option "xkb_model" "pc105"
    Information    [    27.612] (**) Option "xkb_layout" "us"
    Information    [    27.614] (II) config/udev: Adding input device HDA SIS966 Mic (/dev/input/event7)
    Information    [    27.614] (II) No input driver specified, ignoring this device.
    Information    [    27.614] (II) This device may have been added with another device file.
    Information    [    27.614] (II) config/udev: Adding input device HDA SIS966 Headphone (/dev/input/event8)
    Information    [    27.615] (II) No input driver specified, ignoring this device.
    Information    [    27.615] (II) This device may have been added with another device file.
    Information    [    27.615] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
    Information    [    27.616] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
    Information    [    27.616] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
    Information    [    27.616] (**) AT Translated Set 2 keyboard: always reports core events
    Information    [    27.616] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
    Information    [    27.616] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
    Information    [    27.616] (--) evdev: AT Translated Set 2 keyboard: Found keys
    Information    [    27.616] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
    Information    [    27.616] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input9/event4"
    Information    [    27.616] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
    Information    [    27.616] (**) Option "xkb_rules" "evdev"
    Information    [    27.616] (**) Option "xkb_model" "pc105"
    Information    [    27.616] (**) Option "xkb_layout" "us"
    Information    [    27.617] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
    Information    [    27.617] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
    Information    [    27.617] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
    Information    [    27.617] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
    Information    [    27.618] (II) LoadModule: "synaptics"
    Information    [    27.618] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
    Information    [    27.618] (II) Module synaptics: vendor="X.Org Foundation"
    Information    [    27.618]     compiled for 1.18.1, module version = 1.8.2
    Information    [    27.618]     Module class: X.Org XInput Driver
    Information    [    27.618]     ABI class: X.Org XInput driver, version 22.1
    Information    [    27.618] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
    Information    [    27.618] (**) SynPS/2 Synaptics TouchPad: always reports core events
    Information    [    27.618] (**) Option "Device" "/dev/input/event6"
    Information    [    27.680] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 57)
    Information    [    27.680] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 84)
    Information    [    27.680] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
    Information    [    27.680] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
    Information    [    27.680] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
    Information    [    27.680] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
    Information    [    27.680] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
    Information    [    27.680] (**) SynPS/2 Synaptics TouchPad: always reports core events
    Information    [    27.712] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input14/event6"
    Information    [    27.712] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
    Information    [    27.712] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
    Information    [    27.712] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
    Information    [    27.712] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
    Information    [    27.712] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
    Information    [    27.712] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
    Information    [    27.712] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
    Information    [    27.712] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
    Information    [    27.712] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
    Information    [    27.713] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
    Information    [    27.713] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"

```

---

### Post by lah-ca on 2017-01-24
I just ran through the process of downloading, compiling and installing the SIS drivers again, modified the xorg.conf file again, and the results are the same.  XORG cannot find the SIS module and so loads FBDEV drivers.

---

### Post by Yellow Pasque on 2017-01-24
Probably because I had you put it in /usr/local . Try again with
```
./configure --prefix=/usr
make
sudo make install
```

---

### Post by lah-ca on 2017-01-24
> **Temüjin said:**
> Probably because I had you put it in /usr/local . Try again with
```
./configure --prefix=/usr
make
sudo make install
```

Thanks, but still no go.  There was a warning message about remembering to run libtool --finish ....  after.  libtool was not installed.  I installed it; ran configure, make and make install again; and ran the libtool as suggested.  But no go.

Maybe I will try configure with /usr/local again and see if the libtool warning changes.

---

### Post by Yellow Pasque on 2017-01-24
Can you give the exact output from the make install portion? I tested it in my VM (also 16.04 32-bit) and I ended up with sis_drv.so in /usr/lib/xorg/modules/drivers, as expected.

---

### Post by lah-ca on 2017-01-24
> **Temüjin said:**
> Can you give the exact output from the make install portion?

Probably, although I do not presently know how to log the output to a text file.  But I will find out.  

[INDENT]make install > sis_make_install.txt ?[/INDENT]

 > **Temüjin said:**
> I tested it in my VM (also 16.04 32-bit) and I ended up with sis_drv.so in /usr/lib/xorg/modules/drivers, as expected.

I presently have two sis files in /usr/lib/xorg.modules/drivers - sis_drv.so and sis_drv.la  - so expectations are met, to this degree anyway.

---

### Post by lah-ca on 2017-01-24
I am wondering if it might not be better to reload LUbuntu and start again with a fresh installation.  There have been a number of missteps with the current installation, which may or may not affect the success of the SIS driver installation.

---

### Post by Yellow Pasque on 2017-01-25
If bloated web pages were causing issues and you find Lubuntu snappier, your main issue is probably the 1GB of RAM, as mörgæs suggested. You may not see a lot of benefit to getting the sis driver running, since the CPU is relatively powerful for a machine of this age/budget (and it's a dual core). If you find moving windows around to be fluid, the sis driver is probably not worth the time/effort. The only other advantage it would give you is support for more resolutions than vesa. You don't say what the native resolution of your system is though.

> I presently have two sis files in /usr/lib/xorg.modules/drivers - sis_drv.so and sis_drv.la - so expectations are met, to this degree anyway. 

Then I'm baffled why the Xorg log claims the sis driver is not found. It works in my VM, at least to the point where the Xorg log acknowledges the sis driver exists and prints a list of chipsets it supports.

> Probably, although I do not presently know how to log the output to a text file.

I just wanted you to run the command and copy/paste the output. Nevermind though, you answered my question that you had the file(s) in the right place.

---

### Post by lah-ca on 2017-01-25
Hi,

I have been away from working professionally in IT for too long, or not long enough, depending upon how you look at it (LOL), and have broken one of the most basic rules of diagnostics, one that I used to beat into the heads of my subordinates/trainees: "Never make assumptions.  Be ***tediously*** methodical, and base everything on evidence."  Intuition and imagination are necessary but must be supported and tested by tedious slog work.

Like a complete noob, and I am a relative Linux noob, I moronically assumed that the root cause was the same -- *XORG can't find the driver file --* when I changed the xorg.conf file to "sis", rebooted, and got the same results, 640x480 resolution.  But it is not the same cause!  ***Look at the logs, idiot ***(me). 

 :oops:

The problem now is that the SIS driver package does not support the 771/671 chipset; it is not in the supported devices list.  And so XORG resorts to the default of FBDEV drivers.

---

### Post by Yellow Pasque on 2017-01-25
> **lah-ca said:**
> The problem now is that the SIS driver package does not support the 771/671 chipset; it is not in the supported devices list.  And so XORG resorts to the default of FBDEV drivers.

Maybe this is one of those chipsets that needs sisimedia driver? I don't know. There seems to be a lot of overlap between the two driver packages.
[https://github.com/rasdark/xf86-video-sis671](https://github.com/rasdark/xf86-video-sis671)

---

### Post by Yellow Pasque on 2017-01-25
You probably want to clean up the cruft from your first attempt. So change to the xf86-video-sis-0.10.9 directory and run:
```
sudo make uninstall
```
You can then delete the directory and the tar.bz file you downloaded. Sorry for leading you down that road in the first place... :/

Here's something that looks more promising:
```
sudo apt-get install autoconf automake git  #you may already have some/all these packages
cd ~/   #or whatever dir you want to use
git clone https://github.com/rasdark/xf86-video-sis671.git
cd xf86-video-sis671/
git checkout for-xorg-1.18
autoreconf
automake
./configure --prefix=/usr --disable-static
make
sudo make install
```    

Then you change the line in xorg.conf to ' Driver "sis671" '

Here's what my Xorg log looked like when I did it in my VM:
```
[   997.179] (II) LoadModule: "sis671"
[   997.179] (II) Loading /usr/lib/xorg/modules/drivers/sis671_drv.so
[   997.179] (II) Module sis671: vendor="X.Org Foundation"
[   997.179]    compiled for 1.18.4, module version = 0.10.4
[   997.179]    Module class: X.Org Video Driver
[   997.179]    ABI class: X.Org Video Driver, version 20.0
[   997.179] (II) SIS671: driver for SiS chipsets: SIS5597/5598, SIS530/620,
        SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
        SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
        SIS[M]661[F|M]X/[M]741[GX]/[M]760[GX]/[M]761[GX]/662, SIS340,
        [M]670/[M]770[GX], [M]671/[M]771[GX]
```

This looks encouraging: **[M]671/[M]771[GX]**

---

### Post by lah-ca on 2017-01-25
> **Temüjin said:**
> You probably want to clean up the cruft from your first attempt. So change to the xf86-video-sis-0.10.9 directory and run:
```
sudo make uninstall
```
You can then delete the directory and the tar.bz file you downloaded. Sorry for leading you down that road in the first place... :/

......

This looks encouraging: **[M]671/[M]771[GX]**

Thanks.  I will try this later today.  I am heading off soon to try and pry a 2Gb DDR2 667 SODIMM out of someone's hands.  I might have to buy lunch so it might be just as cheap to buy new @ about $40 CDN, which is probably more than the notebook is worth - LOL.

I tried the basic instructions here for the bleeding-edge, 2-month-old "test-only" drivers: [https://github.com/rasdark/xf86-video-sis671/tree/master/ubuntu](https://github.com/rasdark/xf86-video-sis671/tree/master/ubuntu) - but the driver file, while located by XORG, could not be loaded.

Rather than trying to clean up, I think I will just reload - the ultimate clean-up.  Much has been done to this unfortunate LUbuntu installation and it grow less stable.  LUbuntu is a very quick installation.  Then we know we are starting with an entirely clean slate.

More later.

---

### Post by lah-ca on 2017-01-25
> **Temüjin said:**
> 
Sorry for leading you down that road in the first place... :/


Absolutely no apologies are necessary.  I appreciate your patience and persistence.

This problem, while a major PITA (pain in the ...), has been most educational.

Thanks.

---

### Post by lah-ca on 2017-01-25
> **Temüjin said:**
> Here's something that looks more promising:
```
sudo apt-get install autoconf automake git  #you may already have some/all these packages
cd ~/   #or whatever dir you want to use
git clone https://github.com/rasdark/xf86-video-sis671.git
cd xf86-video-sis671/
git checkout for-xorg-1.18
autoreconf
automake
./configure --prefix=/usr --disable-static
make
sudo make install
```    


Hi

There is some version/dependency issue:

```
user@U40SI1:~/xf86-video-sis671$ git checkout for-xorg-1.18
Note: checking out 'for-xorg-1.18'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 49d7f08... upd: fix for xorg-1.18
```

```
user@U40SI1:~/xf86-video-sis671$ autoreconf
configure.ac:38: error: must install xorg-macros 1.8 or later before running autoconf/autogen
configure.ac:38: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: error: echo failed with exit status: 1
autoreconf: aclocal failed with exit status: 1
```

Installed xutils-dev and ran commands again.  Better results.

---

### Post by lah-ca on 2017-01-25
Hooray!

The SIS drivers are loaded.  1280x800 res.  Better clarity.  Better colour.  Aspect ratio no longer slightly off.

Cool.  Thanks, Temüjin.

In the next while, I will summarize what was done to achieve this all.

---

### Post by Yellow Pasque on 2017-01-25
> **lah-ca said:**
> Absolutely no apologies are necessary.  I appreciate your patience and persistence.
This problem, while a major PITA (pain in the ...), has been most educational. Thanks.

You are welcome and the feeling is more than mutual.

---

### Post by Yellow Pasque on 2017-01-25
> Installed xutils-dev and ran commands again
Thank you for that.

---

### Post by lah-ca on 2017-01-26
[SIZE=5]**Summary**[/SIZE]

This post presents a solution for installing Linux SIS drivers on an Olidata U40SL1 notebook.  This notebook is apparently identical to ECS, Uniwill, and Olivetti units with the same model number, and the solution **_*should*_** work for them, as well.  The solution **_*should*_** also work for any device with a SIS 771/671 video chipset.

The solution is for ***LUbuntu 16.04 32 bit***, but it _***should***_ also work for various contemporary Ubuntu distros and forks.

[SIZE=2]**Acknowledgements **[/SIZE]

If you read this thread from beginning to end, you will see that pretty much all thanks are due to Temüjin.  Thanks!  But major thanks, also, to mörgæs, whom I shamefully forgot to acknowledge, earlier. 

[SIZE=2]**Expectations**[/SIZE]

The results will _***not***_ be perfect.  The SIS drivers provide only some level of 2D acceleration and no 3D.  There will be occasional display anomalies/corruption - restarting applications usually fixes this - in rare cases, rebooting or logging out/in is required. There will also be sporadic Ubuntu-has-experienced-an-internal-error messages, these  associated with XOrg, probably as a result of the SIS drivers - the problem beneath the error message seems to be non-disruptive, however.  In the end, 1280x800 resolution is achieved.  The vesa drivers, the next best alternative, provide only 1024x768 resolution, with some minor distortion of aspect ratio and with no acceleration, and full screen video playback, Youtube, DVDs, etc, is either not possible or is of unacceptable quality.  The SIS drivers provide higher resolution, better clarity, better colour, and better aspect ratio.  They also allow full screen video playback, including DVDs, at a moderately acceptable level.  I would also say that the notebook does not get as hot with SIS drivers as it does with the vesa ones, suggesting that the vesa drivers put more work on the proc.  Overall the performance of the notebook is better.  Web pages load faster, etc.

**Don't Work in 600 x 480 unless You Are a Masochist!**

The default fbdev drivers, those loaded, after installation, provide only 600x480 resolution.  It is difficult to work with this.  Create an xorg.conf file in /etc/X11/ in order to load the Linux-native vesa drivers which will provide 1024x768 resolution.  You will need this file later, anyway, to load the SIS drivers.

If you are new/newish to Linux, you can open a terminal and use sudo to launch a text editor so that you will have rights to save the file in the X11 folder.  For LUbuntu:

```
sudo leafpad
```

Copy/paste the following:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection


Section "Monitor"
        Identifier      "Configured Monitor"
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Save the file as ***xorg.conf*** in the X11 folder - /etc/X11

Reboot.  You should have 1024x768 resolution, which will make the rest of the work easier.

**Install a Log Reader**

This is not a necessity, but if something goes wrong, you will have easy access to the XORG logs for diagnostics.  For LUbuntu:

```
sudo apt-get install ksystemlog
```

[SIZE=2]**Prerequisites**[/SIZE]

Here I present the creation of the environment in which the compilation and installation of the drivers worked.  Not all steps may be necessary but this was the state in which things did work.

Run the following in a terminal.  Copy/paste is your friend.

```
sudo apt-get install build-essential xorg-dev
sudo apt-get install autoconf automake git
sudo apt-get install libtool-bin
# typo found here by Temüjin: sudo apt-get install ***xutils.dev***
# should read:
sudo apt-get install xutils-dev

```

**Downloading, Compiling and Installing Driver**

Run the following in a terminal.  Copy/paste is your friend.

```
cd ~/   #or whatever dir you want to use - note: the process works well in the root of the home folder.
git clone https://github.com/rasdark/xf86-video-sis671.git
cd xf86-video-sis671/
git checkout for-xorg-1.18
autoreconf
automake
./configure --prefix=/usr --disable-static
make
sudo make install
```

**Check for Driver Files**


Look in /usr/lib/xorg/modules/drivers - there should now be two SIS driver files: ***sis671_drv.la*** and ***sis671_drv.so***

**Loading Driver: Edit xorg.conf**

Open the xorg.conf file created above.  Remember to use sudo to open the text editor.

Change:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"

```

To:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "sis671"

```

Save and close the file.

**Reboot**

If you are new/newish to Linux and still have a terminal open:

```
shutdown -r now

```

This seems to work faster than GUI menu-driven reboot button.

**Enjoy!**

---

### Post by mörgæs on 2017-01-28
That's an impressive guide. Thanks to both of you.

Feel free to add to the old hardware thread so the advice is not buried and forgotten under new threads.

---

### Post by zibi83 on 2017-09-09
Hi, I have a problem:
after : 
./configure --prefix=/usr --disable-static

I see this in the end:

checking whether to build static libraries... no
./configure: line 18531: syntax error near unexpected token `XINERAMA,'
./configure: line 18531: `XORG_DRIVER_CHECK_EXT(XINERAMA, xineramaproto)'

can someone help me?:)

---

### Post by Yellow Pasque on 2017-09-09
^You have libxinerama-dev package installed?

---

### Post by zibi83 on 2017-09-23
Yes, when I type:sudo apt-get install libxinerama-dev libxinerama-dev is already the newest version (2:1.1.3-1).

---

