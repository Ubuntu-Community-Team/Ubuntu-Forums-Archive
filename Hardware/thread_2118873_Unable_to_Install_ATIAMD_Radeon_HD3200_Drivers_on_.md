---
title: "Unable to Install ATI/AMD Radeon HD3200 Drivers on 12.04.2"
date: 2013-02-22
forum: Hardware
---

### Post by Spite.FU on 2013-02-22
After reinstalling Ubuntu 12.04.2 on an Acer Aspire 5535 with an ATI Radeon HD3200 I have been trying to install the AMD drivers for linux off their website using the method here [http://milodovic.wordpress.com/2013/02/11/things-to-do-after-installing-ubuntu-12-04-2-lts-part-i/]("http://milodovic.wordpress.com/2013/02/11/things-to-do-after-installing-ubuntu-12-04-2-lts-part-i/") among other similar ones.

I am getting errors during the installtion
```
DKMS part of installation failed.  Please refer to /usr/share/ati/fglrx-install.log for details
Removing temporary directory: fglrx-install.vx6g7D

```

The log file in /usr/share/ati/fglrx-install.log
says :-

 ```
Detected a previous installation, /usr/share/ati/amd-uninstall.sh
Installation with force option.
Check if system has the tools required for installation.
fglrx installation is being forced. Installation will proceed without the required tools on the system.
Uninstalling any previously installed drivers.
Forcing uninstall of AMD Catalyst(TM) Proprietary Driver.
No integrity verification is done.
restore of system environment completed
Errors during DKMS module removal
Uninstall fglrx driver complete.
For detailed log of uninstall, please see /etc/ati/fglrx-uninstall.log
System must be rebooted to avoid system instability and potential data loss.
/usr/share/ati/amd-uninstall.sh completed with 0

Creating symlink /var/lib/dkms/fglrx/8.98/source ->
                 /usr/src/fglrx-8.98

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.98/build; sh make.sh --nohints --uname_r=3.5.0-23-generic --norootcheck....(bad exit status: 1)
[Error] Kernel Module : Failed to build fglrx-8.98 with DKMS
[Error] Kernel Module : Removing fglrx-8.98 from DKMS

------------------------------
Deleting module version: 8.98
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfs
```

Now I am stumped.Help gratefully recieved.

---

### Post by QIII on 2013-02-22
Hello and welcome to the forums.

Please see the ATI wiki link in my signature and go to section 2.1. Installing via the command line.

Catalyst 12.4 is in the Precise repo and that is probably the easiest route.

Best of luck!

---

### Post by Spite.FU on 2013-02-22
Ok from the Terminal install it was looking promising and all the outputs looked fine, no errors.

On reboot however, I get the same problem - the display is in a low graphics resolution, stretched about the horizonal axis.

fglrxinfo yields-
```
$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

sudo aticonfig --initial
 gives-
```
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-0

```

so it appears something went correctly.

Incidently jockey just reports "No proprietary drivers are in use on this system" but does not give me an option to enable anything.

If I try to run Catalyst Control Centre I get an error window which says:-

"There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No AMD graphics driver is installed, or the AMD driver is not functioning properly.
Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig."

---

### Post by Spite.FU on 2013-02-22
The Card is a **Mobility** Radeon HD3200.
Kernel is 3.5.0-25-generic

---

### Post by 2F4U on 2013-02-22
Which version of the driver did you install? My understanding from this site

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

is that the kernel has to be below 3.5 and Xserver has to be below 1.13.

---

### Post by QIII on 2013-02-22
Ah.  I didn't see the point release was .2, which does indeed have a 3.5 kernel.  Your card will not work with that.

My apologies.

Let's get you back to the default open source Radeon driver.

Just to be sure we have cleared out the attempted install from the AMD website:

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

This may fail.  Don't worry about it if it does.

Remove what was installed from the repo:

```
sudo apt-get purge fglrx fglrx-amdcccle
```
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak2
```

Then:

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

```
sudo dpkg-reconfigure xserver-xorg
```

Reboot.  You should now be on the default open source Radeon driver.

---

### Post by m0dcm on 2013-03-16
I have found performance issues with both the ATI Proprietary Driver  & the Open Source one, mainly how they both do 3D and basic 2D.
I  have 2 Zotac Z-Box Mini AD01 with the Radeon 3200HD, and in Unity 3D  using the Proprietary driver in Ubuntu 12.04LTS the CPU usage is crazy,  and if you are running the 64bit version, well the memory leak is  hurrendous! In the Open Source one, Unity 3D works without any  performance hit, but video accelleration and lag on XBMC is a slight  issue.
So what I've done is drop to Unity 2D on both my Zotac Mini's  and running the Proprietary AMD/ATI Radeon Driver works great! As I use  my main PC mainly for my Hobby which is Amateur Radio & general day  to day browsing and emails etc, this works for me, but I do wish Unity  would work in 3D without the issues I've been having.

---

### Post by xaliqen on 2013-03-18
You probably want to have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2096845") for what other people did to get legacy catalyst working on older radeon cards with 12.04+.  Adding [this PPA]("https://launchpad.net/~makson96/+archive/fglrx") is one solution which works well on Quantal and Precise; it will help downgrade your X-Server and patch the kernel appropriately.

As for Raring, I'd stay away from it until someone finds a good solution for getting legacy fglrx working on 3.8+ kernels.  Of course, if you're okay with running non-fglrx drivers, then it's not an issue.

---

### Post by Rowan_ on 2013-05-26
> **xaliqen said:**
> this PPA[/URL] is one solution which works well on Quantal and Precise.

Using the repo's and directions located at the quoted [link]("https://launchpad.net/~makson96/+archive/fglrx") fixed my problems of HD4200 not working with Precise 12.04.  Among other benefits, I get no more tearing, and I can use apps such as XBMC too.
Thanks for the info.

---

