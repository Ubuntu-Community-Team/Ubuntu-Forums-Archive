---
title: "ati-driver-installer-9-3-x86.x86_64"
date: 2010-04-22
forum: Hardware
---

### Post by yeehi on 2010-04-22
[This]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.6&lang=English") ati driver is for the mobility radeon x700.

There is no longer support for this hardware. They have stopped getting it to work with more recent versions of Ubuntu. The latest that is supported is Jaunty. Source is also listed when I run this:

>  sudo sh ati-driver-installer-9-3-x86.x86_64.run --listpkg

> Package Maintainer(s): Mario Limonciello <superm1@gmail.com>
                      Aric Cyr <aric.cyr@gmail.com>
Status: *UNVERIFIED*
Ubuntu Packages:
	Ubuntu/7.10
	Ubuntu/8.04
	Ubuntu/8.10
	Ubuntu/9.04
	Ubuntu/gutsy
	Ubuntu/hardy
	Ubuntu/intrepid
	Ubuntu/jaunty
	Ubuntu/source

For example, to build a Debian Etch package, run the following:
% ./ati-driver-installer-<version>-<architecture>.run --buildpkg Debian/etch



Should I try and install this onto a Lucid system, using source or jaunty as a parameter?

Thank you for your help!

---

### Post by Mark Phelps on 2010-04-23
> **yeehi said:**
> Should I try and install this onto a Lucid system, using source or jaunty as a parameter?


Basically -- NO.

Shortly after ATI dropped Linux support for your card, the version of the X-Server in Ubuntu changed.  The result is that no ATI drivers will work with Ubuntu versions with the default X-Server version newer than Ubuntu 8.10.

Your only working drivers now are the open source drivers -- which are installed by default.

If you try to force the installation of any ATI drivers, you will trash your display and only end up having to remove them, and replace them with the default open source drivers.

---

### Post by Ayuthia on 2010-04-23
I agree with Mark Phelps about not trying.  9.3 is old enough that it would not be compatible with 2.6.32 without patches.  Once that is patched up, you would then need to figure out how to patch it to work with xorg-server-1.7.

From what I understand right now, 10.4 is most likely the only fglrx driver that will work in Lucid because of the X.org server changes.

---

### Post by Allrab on 2010-04-27
Hello!

Has someone found a workaround for this, or is it simply not possible?
If there is a workaround is there a tutorial I could follow?
Should I downgrade to a previous version of Ubuntu?
What would you recommend?

**Allrab** Ubuntu 9.10 user

---

### Post by Mark Phelps on 2010-04-27
> **Allrab said:**
> Hello!

Has someone found a workaround for this, or is it simply not possible?
If there is a workaround is there a tutorial I could follow?
Should I downgrade to a previous version of Ubuntu?
What would you recommend?

**Allrab** Ubuntu 9.10 user
What I would recommend is either of the following:
1) Live with the limitations of the open-source drivers -- they're getting better all the time
2) Buy a newer card that DOES have ATI Linux support.

The latest Ubuntu version that works with the ATI Linux drivers for this card is 8.10. Since you can't actually "downgrade" versions, you would have to do a reinstall using that version.

---

### Post by Allrab on 2010-04-27
> **Mark Phelps said:**
> What I would recommend is either of the following:
1) Live with the limitations of the open-source drivers -- they're getting better all the time
2) Buy a newer card that DOES have ATI Linux support.

The latest Ubuntu version that works with the ATI Linux drivers for this card is 8.10. Since you can't actually "downgrade" versions, you would have to do a reinstall using that version.

Thank you, Buying a new GFX card is not an option, since I'm poor :) Also I have a Samsung R50 laptop, so even if I could afford a new GFX card, I can not install it in to the Laptop. I guess that is the problem with old things.
This leaves me with the only option to uninstall 9.10 and go with 8.10. Thank you for the quick response!

**Allrab**

---

### Post by Braik on 2010-05-02
I have an ATI Radeon X1300 and I have just installed Lucid, but 3D acceleration is not enabled.

There is any solution to this?

Thanks

---

### Post by WarezCoxtrong on 2011-12-06
OK. I have a Dell Vostro 1000 with the Xpress 1150, and I installed Oneiric through wubi, and I was able to get my gfx card working just fine with the ati-driver-installer-9-3-x86.x86_64.run.  I was playing Quake 3 via WINE, also was playing Nexuiz and other 3d apps just fine.  Then I transferred the Wubi install to its own dedicated ext4 partition and it worked fine.  Until I tweaked Compiz a little too much, and totally screwed Unity up, so I figured it'd be easier to just reinstall Ubuntu and go from there.

Anyway, I popped in the Ubuntu CD, reformatted the partition after a backup, and installed, now I can't get the driver working.  I screwed up the display trying to get it to work (Quake III was at a crawl, couldn't even really run Nexuiz, and Quake 4 was giving me all kinds of GL errors and wouldn't run.)  fglrxinfo (after i installed fglrx, because the ati-driver-installer package wouldn't work) mentioned something about mesa, so I knew the driver wasn't being used for my Radeon. (confirmed with a lsmod, it was using the radeon driver instead).

So my question is, how come it worked just fine with the first install (which was originally installed from wubi) but with a full on CD install, it isn't working?  The driver can obviously be made to work with 11.10, but I don't know what I did different, if anything, the first time I installed it.  There has got to be a way to get it working with full 3d acceleration if I've already done it once.  Hell, when it was working on that first install, it was running Quake 3 (under WINE, and yes, I know it can be installed natively even faster, I just wanted to test WINE and see how far it has come since the last time I tried it a few years back.) better than Windows, and now I can't really do anything because the driver won't install.

---

### Post by Mark Phelps on 2011-12-06
This is weird ... because there have been other recent similar reports of folks doing version to version to version in-place upgrades and having things like this work, and then, replacing that with a clean install and NOT having things like this work.

Those ATI drivers are NOT supposed to be able to work with any Ubuntu newer than 8.10, so if you discovered a workaround that DID get them working, then you lucked out.  Maybe has something to do with stuff left over from previous versions that STILL works, but does not get installed with the newer versions.

Sorry, but there's no supported way to get those drivers working with current Ubuntu releases other than seriously backporting older X-server versions.

---

### Post by WarezCoxtrong on 2011-12-06
This system had never had any Linux installed on it until just a few days ago, when I installed through wubi.  I don't remember exactly what I did that first time, but I was able to run 3d games on it just fine.  And apparently I'd downloaded the 9-3 driver, because it was on the backup disc that I burned right before I reformatted.  Prior to the wubi install, the only OS this laptop had ever had on it was Windows XP.  I'm getting to the point where I'm tempted to tear the f*** thing apart and try ripping the Geforce integrated chip from my HP laptop with a busted screen.. although I'm positive that'll just fry both machines.. But seriously.. there's nothing more f'ing annoying than having something work, then having to reinstall the SAME OS, and it not work.  I tried ./ati-driver-installer-9-3-x86.x86_64 --buildpkg Ubuntu/8.10 or whatever, and did the same for 9/04, and with --buildandinstallpkg as well. Best case scenario, I get thrown into Unity 2d on startup. Worst case, as soon as I get past the BIOS, it looks like the screen is melting, and I have to ctrl+alt+f1 into the console, manually remove all the packages from the fglrx driver with dpkg, and then sudo pkill X or reboot the computer.  I had it working once, I'd just like to get it working again.

Side note. I am able to build the source from --buildpkg Ubuntu/source, but I can't get it to do anything with ./configure or make.  Any ideas here?  If I could just get it compiled from source, I should be able to get around all this garbage I would think.  Anyway, on a side note, I think this is the last time I'll ever make the mistake of buying or recommending anything with an ATI product. I used to recommend them to many of my customers, who are generally Windows users, regardless, I think I'll be pushing NVIDIA and Intel from now on.

---

