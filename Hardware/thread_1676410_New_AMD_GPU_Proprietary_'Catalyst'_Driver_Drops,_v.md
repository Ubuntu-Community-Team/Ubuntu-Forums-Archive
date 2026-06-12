---
title: "New AMD GPU Proprietary 'Catalyst' Driver Drops, v11.1"
date: 2011-01-27
forum: Hardware
---

### Post by tehowe on 2011-01-27
Looks like the new driver for the Radeon I've been [fighting with]("http://ubuntuforums.org/showthread.php?t=1669327") went up [a bit earlier today]("http://forums.amd.com/game/messageview.cfm?catid=279&threadid=145818"). Hopefully it addresses most of the problems and little bugs people have been experiencing with Radeon cards. This driver update also includes support for the 6xxx version.

[AMD Catalyst 64-bit driver v11.1]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

That driver covers both 32 and 64 bit systems.

There's a wiki page for the release, but it hasn't been edited yet as of this posting: [http://wiki.cchtml.com/index.php/11.1](http://wiki.cchtml.com/index.php/11.1)

"It better work this time." How have your install experiences been with this new driver? Post them here...

---

### Post by BrokeMahPC on 2011-01-27
Has this been ported through to:

Ubuntu - Adimistration - Hardware Drivers

yet? I have a HD 6xxx card HD6850 and I am not sure if I should download from AMD or activate the driver in ubuntu.

There were many updates in 10.10 over the last few days including xorg and a new kernel update so it would be nice to know whats going on.

I prefer doing it the Ubuntu way as it's less hassle in the long run. Hope things are finally sorted out as I have been sitting with MESA drivers and the wrong screen resolution since October - praying for an official solution!

(I know there was a way to force it to use 10.12 - I have had bad experiences with those methods in the past. So prefrred to wait.)

---

### Post by tehowe on 2011-01-27
> **BrokeMahPC said:**
> Has this been ported through to:

Ubuntu - Adimistration - Hardware Drivers

yet? I have a HD 6xxx card HD6850 and I am not sure if I should download from AMD or activate the driver in ubuntu. (...)

The thing about that is, I think the Catalyst versions in Jockey (the proprietary driver installer) are only updated with each Ubuntu release, and because Canonical does subject these things to some testing I gather, the versions lag. But, yes, I'm sure it's safer.

I read that the Radeon proprietary driver version in Maverick is something equivalent to Catalyst 10.10 - not Ubuntu 10.10, not Catalyst 10.12, the most recent version, but v10.10. I've yet to get Mplayer to work, so unless there's a lower version that's stable and rather than wait for 'Natty Narwhal' or 'Oily Octopus' I'll try this new one out. What's the worst that could happen? :)

---

### Post by BrokeMahPC on 2011-01-27
You have convinced me! I will download fglrx / Catalyst 1.11. Sounds like the best option.

Just read that Gallium 3D will start in Natty - all singing, all dancing, solves all problems lol.

---

### Post by tehowe on 2011-01-27
Planned steps for this upgrade... IMPORTANT: don't assume I know what I'm doing. This is all from the 'Unofficial' AMD Linux Community Wiki. Pretty good page, lots of info though...

1. Completely uninstall existing ATI/AMD proprietary FGLRX graphics driver using System/Administration/Additional Drivers from the desktop menu. It hooks into synaptic well enough to automate this part of the process. 

2. Restart

3. Use [these instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx") to run (edit: build) the new downloaded package (for Maverick) or [pick your OS version here]("http://wiki.cchtml.com/index.php/Ubuntu") if you're not using Ubuntu 10.10. Note: Building your own Deb? Not for the faint of heart, but this is a pretty comprehensive guide. (I thought there was a way to just 'run' the .run file that Catalyst  comes bundled as, maybe that only applied to a prior version.)

4. Install. Panic? (Note: Panic optional)

5. In case of issues please [break glass]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx"). Link is to an uninstall process.

Question, if I get it working am I allowed to post a link to the Ubuntu-flavoured .deb I compiled?

---

### Post by tehowe on 2011-01-27
Ok, so here I am uninstalling flgrx from the command line to ensure the system is cleaned up... this after using the 'Additional Drivers' uninstall.

```
tehowe@galt:~$ sudo sh /usr/share/ati/fglrx-uninstall.sh
[sudo] password for tehowe: 
sh: Can't open /usr/share/ati/fglrx-uninstall.sh
tehowe@galt:~$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx-modaliases' for regex 'fglrx_*'
Note, selecting 'fglrx' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx_*'
Note, selecting 'fglrx-driver' for regex 'fglrx_*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx_*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx_*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx_*'
Note, selecting 'fglrx-control' for regex 'fglrx_*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx_*'
Note, selecting 'fglrx-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx_*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx_*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx-amdcccle*'
Note, selecting 'fglrx-dev' for regex 'fglrx-dev*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx-dev*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx-dev*'
Virtual packages like 'xorg-driver-fglrx' can't be removed
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libxmltok1 dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  fglrx* fglrx-modaliases*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 69.6kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 246826 files and directories currently installed.)
Removing fglrx ...
Purging configuration files for fglrx ...
update-initramfs: deferring update (trigger activated)
dpkg: warning: while removing fglrx, directory '/usr/lib32/fglrx' not empty so not removed.
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx/etc/ati' not empty so not removed.
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx/etc' not empty so not removed.
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx' not empty so not removed.
Removing fglrx-modaliases ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Processing triggers for ureadahead ...

```And here are the commands as executed from the Wiki to install the new driver...

```
tehowe@galt:~$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0
[sudo] password for tehowe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
debconf is already the newest version.
debhelper is already the newest version.
fakeroot is already the newest version.
fakeroot set to manually installed.
libstdc++6 is already the newest version.
wget is already the newest version.
dkms is already the newest version.
dkms set to manually installed.
libqtgui4 is already the newest version.
The following package was automatically installed and is no longer required:
  libxmltok1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fdupes
The following NEW packages will be installed:
  cdbs dh-make execstack fdupes libelfg0
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,410kB of archives.
After this operation, 2,605kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ maverick/main fdupes amd64 1.50-PR2-3 [21.3kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ maverick/main cdbs all 0.4.83ubuntu2 [1,216kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ maverick/main dh-make all 0.55 [40.8kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ maverick/main libelfg0 amd64 0.8.13-1 [57.8kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ maverick/main execstack amd64 0.0.20090925-1 [73.6kB]
Fetched 1,410kB in 5s (265kB/s) 
Selecting previously deselected package fdupes.
(Reading database ... 246816 files and directories currently installed.)
Unpacking fdupes (from .../fdupes_1.50-PR2-3_amd64.deb) ...
Selecting previously deselected package cdbs.
Unpacking cdbs (from .../cdbs_0.4.83ubuntu2_all.deb) ...
Selecting previously deselected package dh-make.
Unpacking dh-make (from .../archives/dh-make_0.55_all.deb) ...
Selecting previously deselected package libelfg0.
Unpacking libelfg0 (from .../libelfg0_0.8.13-1_amd64.deb) ...
Selecting previously deselected package execstack.
Unpacking execstack (from .../execstack_0.0.20090925-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up fdupes (1.50-PR2-3) ...
Setting up cdbs (0.4.83ubuntu2) ...
Setting up dh-make (0.55) ...
Setting up libelfg0 (0.8.13-1) ...
Setting up execstack (0.0.20090925-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
tehowe@galt:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manually installed.
The following package was automatically installed and is no longer required:
  libxmltok1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tehowe@galt:~$ cd ~/; mkdir catalyst11.1; cd catalyst11.1/
tehowe@galt:~/catalyst11.1$ chmod +x ati-driver-installer-11-1-x86.x86_64.run
tehowe@galt:~/catalyst11.1$ l
ati-driver-installer-11-1-x86.x86_64.run
tehowe@galt:~/catalyst11.1$ sudo apt-get remove --purge xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libxmltok1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xserver-xorg-video-all* xserver-xorg-video-ati* xserver-xorg-video-radeon*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 1,495kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 246972 files and directories currently installed.)
Removing xserver-xorg-video-all ...
Removing xserver-xorg-video-ati ...
Removing xserver-xorg-video-radeon ...
Purging configuration files for xserver-xorg-video-radeon ...
Processing triggers for man-db ...
tehowe@galt:~/catalyst11.1$ sh ati-driver-installer-11-1-x86.x86_64.run --buildpkg Ubuntu/maverick
Created directory fglrx-install.CEafHU
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.812........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/maverick
Package /home/tehowe/catalyst11.1/fglrx_8.812-0ubuntu1_amd64.deb has been successfully generated
Package /home/tehowe/catalyst11.1/fglrx-dev_8.812-0ubuntu1_amd64.deb has been successfully generated
Package /home/tehowe/catalyst11.1/fglrx-amdcccle_8.812-0ubuntu1_amd64.deb has been successfully generated
Package /home/tehowe/catalyst11.1/fglrx-modaliases_8.812-0ubuntu1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install.CEafHU
tehowe@galt:~/catalyst11.1$ l
ati-driver-installer-11-1-x86.x86_64.run  fglrx-amdcccle_8.812-0ubuntu1_amd64.deb  fglrx-installer_8.812-0ubuntu1_amd64.changes
fglrx_8.812-0ubuntu1_amd64.deb            fglrx-dev_8.812-0ubuntu1_amd64.deb       fglrx-modaliases_8.812-0ubuntu1_amd64.deb
tehowe@galt:~/catalyst11.1$ sudo dpkg -i fglrx*.deb
Selecting previously deselected package fglrx.
(Reading database ... 246954 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.812-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.812-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.812-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-modaliases.
Unpacking fglrx-modaliases (from fglrx-modaliases_8.812-0ubuntu1_amd64.deb) ...
Setting up fglrx (2:8.812-0ubuntu1) ...
Loading new fglrx-8.812 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-24-generic
Building for architecture x86_64
Building initial module for 2.6.35-24-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-24-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Setting up fglrx-modaliases (2:8.812-0ubuntu1) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_CA.utf8.cache...
Setting up fglrx-amdcccle (2:8.812-0ubuntu1) ...
Setting up fglrx-dev (2:8.812-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
tehowe@galt:~/catalyst11.1$ 

```That all seems to be in order, but when I try to configure the driver...

(For two monitors)
sudo aticonfig --initial -f --set-pcs-str="DDX,EnableRandR12,FALSE"

I get "command not found". ArgH! Where's aticonfig?

Note: Do NOT restart your computer at this point, or you may brick your desktop, as I did. Well, okay, I can get into the shell at startup but clearly the display driver needs to be configured at this point... any pointers?

---

### Post by BrokeMahPC on 2011-01-27
I have asked this question elsewhere and people are telling me they are getting the unsupported watermark with Catalyst 1.11.

Infuriating but I am hoping it's just a watermark and that some of it is working.

edit-------------
just found this on the Wiki:
[B]Cards in this group are unsupported as of Catalyst 10-12. The Catalyst  driver may run on these cards, but it is not guaranteed (and you will be  stuck with an "Unsupported Hardware" watermark unless you hack the  control file). Full open source support is forthcoming in Linux kernel  2.6.38.
* CAICOS      Radeon HD 6350
* TURKS       Radeon HD 6670
* BARTS       Radeon HD 6850/6870
* CAYMAN      Radeon HD 6950/6970[/B]


When is 2.6.38 coming out?

---

### Post by tehowe on 2011-01-27
> **BrokeMahPC said:**
> I have asked this question elsewhere and people are telling me they are getting the unsupported watermark with Catalyst 1.11.

Infuriating but I am hoping it's just a watermark and that some of it is working.

edit-------------
just found this on the Wiki:
Cards in this group are unsupported as of Catalyst 10-12. The Catalyst  driver may run on these cards, but it is not guaranteed (and you will be  stuck with an "Unsupported Hardware" watermark unless you hack the  control file). Full open source support is forthcoming in Linux kernel  2.6.38.

When is 2.6.38 coming out?

I think I read somewhere 11.1 is just for 5xxx and 6xxx cards.

---

### Post by BrokeMahPC on 2011-01-27
Looks like 1.11 only has full support for 5xxx and limited support for 6xxx - you still have to manually edit  the xorg and hack the watermark.

---

### Post by tehowe on 2011-01-27
SUCCESS! Kind of. Read on, all ye who dare the highwire install..

Bottom line? After all this, my best guess would be to enter 

```
sudo sh ati-driver-installer-11-1-x86.x86_64.run
```at a prompt and let things proceed that way, since that's what  I ended  up doing from the shell anyways after erasing the messed-up install.

Everything below is about how I came to this conclusion. Best of luck to you...
__________________________________________________________________________________________________________________

INITIALLY: WTF... no boot for me and my home directory is locked out (see preceding messages for background). Trying to run ecryptfs to mount it says it's not set up for ecrypt. !!?

Guess I'll try to wget the installation file to the root user directory and just run it as a shell script from there, the deb building exercise hasn't turned out very well.

Anyone want to IM me as to how you remount your ~/ directory? Or just post some advice about how to proceed? Thanks

UPDATE1: Ran the Catalyst install from the mount shell (not the 'build a Ubuntu deb' option, but choise 1, to install the driver with recommended settings), was able to run ati-config - does this mean you only get it if you don't do the debian build? - and rebooted. My boot up screen looks the same now as it did under the stock Ubuntu Catalyst driver, which is a good sign, but my /media/sdc1 is still unmounted, and the system hangs on bootup while telling me so until I drop into a shell. :(

UPDATE2: I skipped mounting the offending drive(s) and the Ubuntu/Gnome background screen and login came up, with a host of errors about not being to access .ICE authority file, not being able to create /home/, Desktop, and nautilus folders. I was given the chance to scrawl down my passphrase, but no menu bar or anything has appeared. I guess I need to figure out how to mount the home directory now...

UPDATE3: One more hard reset and my desktop came up!  Could this process get any more annoying and mysterious? Catalyst control center now says driver version 8.812. Unigine Heaven demo works a treat I gather this means the drivers are working better now as Unigine would NOT work under stock Ubuntu 10.10 proprietary drivers - still can't play any 2D videos except through VLC though. I guess I need to more closely examine how VAAPI (isn't that what it's called? is set up on my system.

---

### Post by tehowe on 2011-01-27
If you're trying the full *deb compilation method* of installing AMD Catalyst 11.1 drivers and you come upon the missing ati-config command like I did, you may not actually have to rip out the driver from the command line in the same way.
 
I noticed that there is help on making ati-config work when doing a .deb-based install fails in the Unofficial AMD Linux Wiki:
 
[URL="http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot"]Aticonfig not found after installation & "module does not exist" after boot 
[/URL]
It sounds almost exactly like the problem I ran into... now I'm wondering if I should start over and if doing a deb-based install with this fix would be better...

---

### Post by BrokeMahPC on 2011-01-28
Just to check - what card do you have? 5xxx or 6xxx series?

---

### Post by tehowe on 2011-01-28
> **BrokeMahPC said:**
> Just to check - what card do you have? 5xxx or 6xxx series?
 
It's a 5850. Unigine Heaven works at 20 fps on 1092x1080 standard settings, so I suspect Catalyst proper works. No video in Mplayer or PiTiVi or Openshot yet though and I've been fiddling with vaapi/xvba tars and debs [for a couple of days now]("http://ubuntuforums.org/showthread.php?p=10405564#post10405564") with no luck. :(

---

### Post by BrokeMahPC on 2011-01-31
> **tehowe said:**
> If you're trying the full *deb compilation method* of installing AMD Catalyst 11.1 drivers and you come upon the missing ati-config command like I did, you may not actually have to rip out the driver from the command line in the same way.
 
I noticed that there is help on making ati-config work when doing a .deb-based install fails in the Unofficial AMD Linux Wiki:
 
[URL="http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot"]Aticonfig not found after installation & "module does not exist" after boot 
[/URL]
It sounds almost exactly like the problem I ran into... now I'm wondering if I should start over and if doing a deb-based install with this fix would be better...

Same thing happened to me - that advice on the wiki did not work.
Hope we get a detailed guide soon - the wiki install procedure is not working for me!

---

### Post by BrokeMahPC on 2011-01-31
No luck for me!
aticonfig --intitial
"aticonfig: No supported adapters detected"

I'm going back to Windows - I will buy 7 later this week. I have spent hours researching this problem, trying different install methods and I had to reinstall Ubuntu x2 to get rid of all the ATI junk that could not be uninstalled.

Had enough - all for a simple driver. I can't see me trying Ubuntu again because by the time it's caught up in 2 years time (It took that long for my HD4670 to work properly) I will no doubt have a new graphics card that will also not work.

---

### Post by tehowe on 2011-02-01
> **BrokeMahPC said:**
> No luck for me!
aticonfig --intitial
"aticonfig: No supported adapters detected"

I'm going back to Windows - I will buy 7 later this week. I have spent hours researching this problem, trying different install methods and I had to reinstall Ubuntu x2 to get rid of all the ATI junk that could not be uninstalled.

Had enough - all for a simple driver. I can't see me trying Ubuntu again because by the time it's caught up in 2 years time (It took that long for my HD4670 to work properly) I will no doubt have a new graphics card that will also not work.

Did you try just running ATI's *.run driver file at the command line? That's what seemed to work for me. Various 3D demos work fine now and flgrxinfo says things are fine, but 2D acceleration in eg; mplayer/totem and PiTiVi do not work - there is no video at all. I don't think that's the Catalyst driver's fault, however, because 2D depends on a thicket of competing standards and I haven't got the standard Gnome apps depend on (VA-API) installed correctly yet. But to your point, there's no simple user manual to get that part working, either. 

I bought my 5850 because it's a workhorse GPU, and it's an older product. Hopefully it will 'just work' in 11.04 - apparently they're (they being our most excellent volunteer coding corps) furiously developing this open-source Gallium driver. 

I've seen people posting about problems getting the NVIDIA equivalent, the GTX 470 or 480 working as well.  So there's no point in swapping the card - I just have to wait, and work on the problem. I think you hit the nail on the head - video hardware is developing rapidly so the lag to get drivers translated becomes a bigger deal than, say, drivers for set standards like USB 2.0 or Bluetooth.

---

### Post by br4mbi on 2011-02-06
```

brambi@brambi-ubuntu:/usr/lib/fglrx/bin$ ./aticonfig --initial -f
Unable to open /etc/ati/control, please reinstall the driver.
./aticonfig: No supported adapters detected

```

That's what i get when i'm following : [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by finndo on 2011-10-06
<sarcasm>
glad to see that this issue has been resolved
</sarcasm>

I am trying to get an AMD 6850 working and getting the same error "no supported adapters detected"

---

