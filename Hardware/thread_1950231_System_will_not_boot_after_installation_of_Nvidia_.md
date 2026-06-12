---
title: "System will not boot after installation of Nvidia 173 driver"
date: 2012-03-31
forum: Hardware
---

### Post by skunkarific on 2012-03-31
I've been getting some weird video artifacts (such as parts of menus staying on the screen unless I reboot) after I added my Nvidia 430 card. I have had problems with the nvidia-current package, so I loaded the nvidia-173. When I restarted the computer, I got only a command line. I logged in, tried startx, got a message that my card wouldn't work with the 173 driver. Then I typed in sudo apt-get remove nvidia-173, rebooted, no GUI again, so no generic x driver replaced the 173. I typed sudo apt-get install nvidia-current, downloaded and installed the driver, rebooted, and still no gui, startx, still no gui. I tried sudo nvidia-xconfig, I get:

WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into
/etc modprobe.d/.
FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA: system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Thoughts? I'm running an HP 21", nothing weird there...

More information:
nvidia-settings is already the newest version
unable to locate package nvidia-xconfig
nvidia-settings is already the newest version

Would anyone be so kind as to let me know how to get back to a gui? I'm running 10.10

---

### Post by gordintoronto on 2012-03-31
What is an HP 21"? What video did you have before adding the Nvidia 430? Have you tried removing the Nvidia card?

I have an Nvidia card and use "current" in 10.10, and the results are perfect.

---

### Post by skunkarific on 2012-04-01
An HP 21" is a monitor, in other words, not a weird model or resolution.  

I'm glad "current" is working for you, I have a dual monitor setup, and was getting weird artifacts, e.g. parts of menus sticking on the screen.  If I restarted X, they went away.  On other computes, using the 173 driver worked better.

All I want to know is there some way to get a generic driver back so I can see my screen.

---

### Post by skunkarific on 2012-04-04
I tried reinstalling nvidia drivers and got this:

Just so you guys know, I'm typing this from a photo I took of the screen, so no copy and paste here...I'm really putting forth the effort!

skunk@CHUX-OFFICE apt install --reinstall nvidia-current
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
Need to get 0B/58.6MB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 193732 files and directories currently installed.)
Preparing to Preparing to replace nvidia-current 295.33 -0ubuntu~1maverick~xup1 (using ...nvi
dia-current 295.33-0ubuntu~1~xup1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia current ...
Processing triggers for man-db ...
Setting up nvidia-current-295.33 DKMS files...
Building only for 2.6.35-22-generic
Building for architecture x86_64
building initial module for 2.6.35-22-generic
Done.

nvidia-current.ko:
Running module version sanity check.
- Original module
- No original module exists within this kernel
- Installation
- Installing to /lib/modules/2.6.35-22-generic/kernel/drivers/char/d

epmod....

DKMS: install Completed.
Processing triggers for python-gmenu ...
REbuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update initramfs: Generating /boot.initrd.img-2.6.35-22-generic
Warning: No support for locale: en_US.utf8
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
Processing triggers for python-support ...
skunk@CHUX-OFFICE-$ _


I know to restart the system after a video driver install so....

skunk@CHUX-OFFICE sudo reboot now

When the system rebooted, a disk check was forced, which had some interesting output:

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
udevd[468]: can not read '/etc/udev/rules.d/z80_user.rules'

/dev/sda1: clean, 219369/987360 files, 1651767/3941941 blocks
/dev/sda3 has been mounted 32 times without being checked, check forced.
Your disk drives are being checked for errors, this may take some time
Press C to cancel all checks currently in progress

[ 562.414349] /build/buildd/linux-2.6.35/drivers/hid-core.c: can't r
eset device, 0000:00:12.2-1-4/input0, status -71
[ 562.424471] /build/buildd/linux-2.6.35/drivers/hid-core.c: can't r
eset device, 0000:00:12.2-1-4/input0, status -71
[ 562.595463] /build/buildd/linux-2.6.35/drivers/hid-core.c: can't r
eset device, 0000:00:12.2-1-4/input0, status -100
[ 562.595471] /build/buildd/linux-2.6.35/drivers/hid-core.c: can't r
eset device, 0000:00:12.2-1-4/input0, status -100

I unplugged the usb bus which has my keyboard and mouse plugged in, there are no other usb devices on the system, got to prompt

skunk@CHUX-OFFICE!$ startx
markers: (--) probed, (**) from config file, (==) default setting
(**) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log"' Time: Tue Apr 3 18:26:16 2012
(==) Using config file: "/etc/Z11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
WARNING: Deprecated configfile/etc/modprobe.conf, all config files belong into
/etc/modprobe.d/.
FATAL Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA: system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
for help.
Please also check the log file at "var/log/Xorg.0.log" for additional informati
on,

ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno3): Server error.
skunk@CHUX-OFFICE~$_

---

### Post by |{urse on 2012-04-04
you can try having jockey reinstall it from command line

> jockey-text --help
jockey-text -l
jockey-text -e xorg:nvidia_current


You also have a few odd bugs. Like 

> udevd[468]: can not read '/etc/udev/rules.d/z80_user.rules'

You can safely delete that file or do this --> [http://ubuntuforums.org/showpost.php?p=9302412&postcount=5](http://ubuntuforums.org/showpost.php?p=9302412&postcount=5)

And I've never seen "/etc/Z11/xorg.conf" usually its /etc/X11/xorg.conf. Is that intentional or a typo?

---

### Post by skunkarific on 2012-04-09
No trabaja :(
This is the output (Yes the Z11 was a typo btw):


jockey-text  /usr/lib/pymodules/python2.6/gtk/__init__.py:57: Gtkwarning:  could not open display
   warnings.warn(str(e), _gtk.Warning)

Searching for applicable drivers...
skunk@CHUX-OFFICE~$_

---

### Post by skunkarific on 2012-04-10
I gave up.  I was rebooting the computer to reimage it, and missed the "Boot from CDROM" prompt.  Suddenly, it took me to a graphical logon!

---

