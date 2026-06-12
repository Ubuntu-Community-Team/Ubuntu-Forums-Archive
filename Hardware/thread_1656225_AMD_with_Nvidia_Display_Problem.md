---
title: "AMD with Nvidia Display Problem"
date: 2010-12-30
forum: Hardware
---

### Post by renno on 2010-12-30
Hi there,

I bought this used machine (AMD processor with Nvidia video card) for general home use, and just finished installing Ubuntu 10.10. I am having a couple of display problem:

1. The desktop is larger than the monitor. I tried to follow some threads but was surprised that I did not have a xorg.conf file to start with.

2. The desktop twitches (on a periodic basis, maybe every 2-3 minutes).

3. This problem might be closely related to number 1: the mouse has some vertical offset, so if I want to have the cursor at a certain point, I need to aim a bit higher.

I hope you can help me with this,

Cheers,

---

### Post by pi/roman on 2010-12-30
Use this to create a new configuration file in your personal folder:
```
sudo X :1 -configure
```You will need to figure out what the maximum resolution of your display is and create modelines for it.  Insert them in your configuration and save it as xorg.conf in /etc/X11.

---

### Post by renno on 2010-12-30
Thanks for the reply,

When I used this command, the file was not created and I got the following output:

```
haboosh@haboosh-desktop:~$ sudo X :1 -configure

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux haboosh-desktop 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=28126fd3-d05c-4059-8417-55daff8048b0 ro quiet splash
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.18.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri Dec 31 03:55:17 2010
List of video drivers:
	tseng
	s3virge
	s3
	neomagic
	ati
	i128
	vmware
	i740
	mga
	ark
	ztv
	radeon
	tdfx
	voodoo
	sisusb
	trident
	nouveau
	mach64
	apm
	savage
	geode
	cirrus
	openchrome
	nv
	sis
	vmwlegacy
	chips
	r128
	rendition
	intel
	siliconmotion
	fbdev
	vesa
(EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
(++) Using config file: "/home/haboosh/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) [drm] No DRICreatePCIBusID symbol
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log
haboosh@haboosh-desktop:~$ sudo X:1 -configure
sudo: X:1: command not found
haboosh@haboosh-desktop:~$ sudo X :1 -configure

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux haboosh-desktop 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=28126fd3-d05c-4059-8417-55daff8048b0 ro quiet splash
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.18.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri Dec 31 03:55:52 2010
List of video drivers:
	tseng
	s3virge
	s3
	neomagic
	ati
	i128
	vmware
	i740
	mga
	ark
	ztv
	radeon
	tdfx
	voodoo
	sisusb
	trident
	nouveau
	mach64
	apm
	savage
	geode
	cirrus
	openchrome
	nv
	sis
	vmwlegacy
	chips
	r128
	rendition
	intel
	siliconmotion
	fbdev
	vesa
(EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
(++) Using config file: "/home/haboosh/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) [drm] No DRICreatePCIBusID symbol
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log

haboosh@haboosh-desktop:~$ sudo X :1 -configure

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux haboosh-desktop 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=28126fd3-d05c-4059-8417-55daff8048b0 ro quiet splash
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.18.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri Dec 31 03:56:09 2010
List of video drivers:
	tseng
	s3virge
	s3
	neomagic
	ati
	i128
	vmware
	i740
	mga
	ark
	ztv
	radeon
	tdfx
	voodoo
	sisusb
	trident
	nouveau
	mach64
	apm
	savage
	geode
	cirrus
	openchrome
	nv
	sis
	vmwlegacy
	chips
	r128
	rendition
	intel
	siliconmotion
	fbdev
	vesa
(EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
(++) Using config file: "/home/haboosh/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) [drm] No DRICreatePCIBusID symbol
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log 

```

It seems that the configuration failed, and I have no idea how to continue from here.

Thanks for your help,

---

### Post by renno on 2010-12-31
Hi there,

Thanks for your help. I created the xorg.conf.new file and then edited file by correcting the HorizantalSync and VertRefresh values. Then I restarted, but now I get the command line only. I am asked for the login and password, but upon entering I cannot get the gnome desktop afterwards.

Where do I go from here?

Cheers,

---

### Post by renno on 2010-12-31
Hi there,

I got the correct specs for the monitor and used the "cvt" utility to obtain the model line of the monitor. Then, I restarted so the resolution improved.

However, the desktop is still not displayed exactly on the physical space of the screen.

Can you please help with this?

Cheers,

---

### Post by pi/roman on 2011-01-02
Make sure the current nvidia driver is installed.
```
gksudo synaptic
```

In synaptic click reload first then search for "nvidia-current". See if "nvidia-current" is installed and if not then mark it for installation and click apply. If you had to install it then open a terminal and run "nvidia-xconfig". Hope that will fix the problem.

---

