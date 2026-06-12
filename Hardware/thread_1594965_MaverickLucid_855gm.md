---
title: "Maverick/Lucid 855gm"
date: 2010-10-12
forum: Hardware
---

### Post by Tommaso on 2010-10-12
This is how I "solved" all my problem with intel drivers in Ubuntu Lucid/Maverick with 855gm chipset.

Only in Lucid you have to re-enable Kms according to: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u
```

Then for both Lucid/Maverick you have to update your intel driver:

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates && sudo apt-get update && sudo apt-get upgrade
```

Upgrade your kernel with a mainline kernel from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2010-10-09-maverick/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2010-10-09-maverick/")

Download:

```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2010-10-09-maverick/linux-headers-2.6.36-997-generic_2.6.36-997.201010090908_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2010-10-09-maverick/linux-headers-2.6.36-997_2.6.36-997.201010090908_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2010-10-09-maverick/linux-image-2.6.36-997-generic_2.6.36-997.201010090908_i386.deb
```

Install:

```
sudo dpkg -i linux-headers-2.6.36-997-generic_2.6.36-997.201010090908_i386.deb linux-headers-2.6.36-997_2.6.36-997.201010090908_all.deb linux-image-2.6.36-997-generic_2.6.36-997.201010090908_i386.deb
```

Enable Intel Driver by editing your xorg.conf:

```
sudo gedit /etc/X11/xorg.conf
```

...and paste:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
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

Reboot...

---

### Post by jdobry on 2010-10-16
Nice! It works for me, but except this I need /etc/X11/xorg.conf from: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

PS: I am cry, because this solution have problem with kernel actualications. Without manulal work it must still on downloaded version, because it not have pkg source for aptitude.

---

### Post by jdobry on 2010-10-16
With default DRI render it can have problems, try this:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "DRI" "off"
        Option          "HWCursor" "off"
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

---

### Post by Tommaso on 2010-10-17
You are right....forgot to say that you have to enable intel driver thought an xorg.conf.

With this kernel you don't have any automatic update...but for me is a good deal for having a nice graphic performance.

P.s:I don't see any problem with DRI enabled...What problem you still having?

---

### Post by draylor on 2010-10-22
Having followed the steps in this thread, (along with several other 'fixes') I am still experiencing lockups.

Is there any news of a fix for this yet? Running with no X is getting extremely frustrating.

Many thanks.

In hope....

---

### Post by serpetiello on 2010-11-05
I have an i855GM-based Fujitsu-Siemens Stylistic ST5022D.
 
8.04: Xv worked great, watched lots of full-screen movies without any hassle.
 
9.04: some problems, solved by "nomodeset" at grub boot. Then Xv worked great, I watched lots of full-screen movies experiencing some random freeze (rarely, and only during video output).
 
10.04: Xorg started in VESA mode, no Xv.
 
Tommaso's links are broken, so I tried to load the latest packages (currently dated 20100511). I also had to build manually the xorg.conf (using "Xorg -configure") and modify it as shown in this page.
 
Alas, there are other graphics problems (for example non-redrawn areas when randomly moving windows) and even a "2.6.36.997something" kernel bug (unable to handle NULL pointer in the USB section).
 
GLXgears still shows some 120fps (thus it is working in vesa framebuffer mode); Xorg.0.log says it is working with inteldrmfb and does not show any Xv thing.
 
The mplayer complains "VO_XV: it seems there is no Xvideo support for your video card available"; the "xvinfo" says "screen #0 no adaptors present".
 
It seems I'll have to downgrade to some older Ubuntu release... :(

---

### Post by serpetiello on 2010-11-12
I also tried the Glasen's way:
 
[FONT=Courier New]sudo add-apt-repository ppa:glasen/855gm-fix[/FONT]
[FONT=Courier New]sudo apt-get update[/FONT]
[FONT=Courier New]sudo apt-get upgrade[/FONT]
[FONT=Courier New]sudo apt-get install 855gm-fix-dkms[/FONT]
[FONT=Courier New]reboot[/FONT]
 
and it installed everything, but nothing changed (xvinfo still says "no adaptors present").
 
Yes, my dmesg says "[   18.667151] agpgart-intel 0000:00:00.0: Intel 855GM Chipset" and my Ubuntu 10.10 was in a clean state (I uninstalled the -x-swat packages mentioned above).

---

### Post by Tommaso on 2010-11-13
Ok...in Ubuntu Maverick I installed this kernel and all seems to work well! :) [http://people.canonical.com/~ogasawara/lp614176/i386/]("http://people.canonical.com/~ogasawara/lp614176/i386/")

---

### Post by serpetiello on 2011-02-17
I am trying Ubuntu Natty 11.04 alpha 2 on my Fujitsu-Siemens Stylistic ST5022D tablet.
 
X11 works, but "xvinfo" says "no adaptors present".
 
 
That is, Natty shows kernel 2.6.38.1 but in the dmesg i find that it uses the old 2008 driver:
 
[drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
 
Then xorg 1.9.99.901 says it could support xv but... xvinfo says "no adaptors present".

---

