---
title: "Ubuntu 10.04, SIS 661/741/760..."
date: 2012-01-21
forum: Hardware
---

### Post by SIS_Laptop_User on 2012-01-21
Hi all,

I have recently transferred from 9.10 to 10.04. I have avoided doing this for a long time, because previous attempts have broken my graphics drivers. However, I am now out of options as I need to apt-get software for Geant4. Anyway, I tried transferring to 10.04 and the graphics are still broken. After searching for some time, I have found many other instances of this in the forums, and have tried all the solutions I found. I am currently running off a 9.10 live-cd in-order to access a browser.

Problem: Ubuntu reaches log-in screen. After trying to log in, the screen flickers black (I believe because it is trying several different resolutions), then returns to the log-in screen. This same behaviour is observed in low-graphics mode. The loading screen throws out weird colours and lines, but I never cared as this occasionally happened in 9.10.

I can reach the console of the installation, but only by temporarily changing 'quiet splash' to 'text' in grub. To me, this confirms that this is a graphics problem, as the text console runs fine. 

Attempted and failed solutions:
(1) Force vesa (both in xorg.conf and adding the 'xforcevesa' option after 'quiet splash' in grub.
(2) Change shared memory to 64 mb
(3) blacklist vga16fb
(4) Booting to earlier kernal ...31

Further details:

xserver-xorg-video-sis is installed.

ubuntu@ubuntu:~$ lshw -class display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:d0000000-d7ffffff(prefetchable) memory:dfee0000-dfefffff ioport:cc00(size=128)

xorg.conf - attached. This is identical to the version I used in 9.10.

/var/log/Xorg.0.log - too big to be attached, confirms my suspicions that many resolutions are being tried, with a selection of errors ranging from vrefresh, hsync and unknown for each resolution tried.

---

### Post by ajgreeny on 2012-01-21
Have you checked that the **xserver-xorg-video-sis** package is installed?  I think you should be using that instead of vesa, unless you know of a good reason to just use the vesa driver.

---

### Post by SIS_Laptop_User on 2012-01-21
Hi there,

Yes as I said at the bottom, I am sure that xserver-xorg-video-sis is installed. Sorry the attached file is the vesa one, the one I was using before changing to 10.04 is attached. I wouldn't even mind using the vesa one for now, I just want it to work.

---

### Post by ajgreeny on 2012-01-21
Wow!  That's quite an xorg.conf, even though most lines are commented out.

Unfortunately I do not have enough knowledge to help any further, other than saying that an old desktop machine I had about 10 years ago with a similar graphics card (sis 636?) had even worse graphic capability that yours does.

Sorry about that.

---

### Post by SIS_Laptop_User on 2012-01-21
Thanks ;) most of it was to allow a non-rectangular dual-monitor set-up with the best resolution on each monitor. Actually, I have now just clean installed 11.10 and given up on ubuntu's upgrade system as doomed to failure for sis cards. I've lost all my settings but at least it works now. I guess it will take me a day to get all the setting right, and I'd already lost a day to trying to repair the 10.04 version anyway...

---

