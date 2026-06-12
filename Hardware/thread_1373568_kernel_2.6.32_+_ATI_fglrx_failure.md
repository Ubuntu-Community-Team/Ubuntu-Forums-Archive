---
title: "kernel 2.6.32 + ATI fglrx failure"
date: 2010-01-05
forum: Hardware
---

### Post by clevertomato on 2010-01-05
The research I've done on the forums suggests that kernel 2.6.32 + the ATI fglrx drivers will fix brightness Fn keys and suspend / resume problems on my Dell Studio 1555. During the rebuild phase there are some failures. I am at a loss for what to do from here. (I have ATI Mobility Radeon HD 4570 based on the M92 chipset.)

Here's what I've done:
1. Fresh install of Karmic amd64 (using ext4).
2. Remove any ATI and Radeon open source drivers.
3. Reboot.
4.
```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx fglrx-amdcccle
```5. ```
sudo aticonfig --initial
```6. 
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/linux-headers-2.6.32-02063202-generic_2.6.32-02063202_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/linux-headers-2.6.32-02063202_2.6.32-02063202_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/linux-image-2.6.32-02063202-generic_2.6.32-02063202_amd64.deb
sudo dpkg -i ./linux*
```(I've tried it with kernel 2.6.32 AND 2.6.32.2 and get same results with both.)

Following are all of the results:
```
[sudo] password for shawnboy: 
Selecting previously deselected package linux-headers-2.6.32-02063202.
(Reading database ... 114194 files and directories currently installed.)
Unpacking linux-headers-2.6.32-02063202 (from .../linux-headers-2.6.32-[INDENT]02063202_2.6.32-02063202_all.deb) ...
Selecting previously deselected package linux-headers-2.6.32-02063202-generic.
Unpacking linux-headers-2.6.32-02063202-generic (from .../linux-headers-2.6.32-02063202-generic_2.6.32-02063202_amd64.deb) ...
Selecting previously deselected package linux-image-2.6.32-02063202-generic.
Unpacking linux-image-2.6.32-02063202-generic (from .../linux-image-2.6.32-02063202-generic_2.6.32-02063202_amd64.deb) ...
Done.
Setting up linux-headers-2.6.32-02063202 (2.6.32-02063202) ...
Setting up linux-headers-2.6.32-02063202-generic (2.6.32-02063202) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.32-02063202-generic                                                                                    
 *  fglrx (8.660)...                                                            fglrx (8.660): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-image-2.6.32-02063202-generic (2.6.32-02063202) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-02063202-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-02063202-generic
Found initrd image: /boot/initrd.img-2.6.32-02063202-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.32-02063202-generic                                                                                    
 *  fglrx (8.660)...                                                            fglrx (8.660): Installing module.
........(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

shawnboy@dell-ubuntu:/media/KK/shawn_docs/kernel_2.6.32.2$[/INDENT]
```If anyone has any suggestions, I'm all ears. I've tried doing the above in different order (i.e. switching kernel, THEN installing ATI fglrx driver, but get same results... failure)

Incidentally, after switching kernels I get "Warning: unable to find suitable fs in /proc/mounts" message during bootup, which I don't understand, but it seems not to cause any problems.

---

### Post by clevertomato on 2010-01-06
I gave up on trying the 2.6.32 kernel with fglrx drivers right now, so I never solved the original problem of this post per se, but I got everything working that I wanted to... finally.

On my Dell Studio 1555 with ATI Mobility Radeon HD 4570 the following is working:


[LIST]
[*]Brightness keys
[*]Suspend and resume
[*]Lid closing and opening behavior
[*]3D effects
[/LIST]
Here's what I did, for the record...

I reinstalled Karmic amd64 AGAIN. This time, out of desperation, I chose ext3 instead of ext4. I have no idea if that is related. In fact, I doubt it is. After fresh install, I installed ATI Catalyst 9.11 drivers from ATI's website (the ati*.run file). I chose automatic install with that and it completed fine. Then I applied all critical system updates, which gave me kernel 2.6.31-16, among other things. Brightness keys work, suspend / resume works, even closing the lid and reopening works. Compiz works. I'm afraid to breathe for fear that something is going to break again. I didn't have to add anything to my grub line or upgrade to a non-released kernel.

---

### Post by clevertomato on 2010-01-06
I spoke too soon, BUT, I have some very specific information that I hope someone will know how to use.

Everything was working perfectly, but today it all went to crap except manual suspend / resume still worked (from the upper right corner). Brightness keys did nothing and closing the lid did nothing. Difference? Last night I had the battery removed from my laptop. Today I have the battery back in. I removed the battery, plugged into AC cord, and it all worked perfectly again.

SO, without battery but with AC power, it all works. With battery, brightness keys and lid closure behavior stops working. I'm hoping this clue is enough for someone to come up with a solution to the problem.

**SOLVED: I added "noapic" to the appropriate line in my grub file and voila... all is right with the world again. Whew!**

---

### Post by myk02k on 2010-02-01
Hey guys.  I'm having a similar issue with my Toshiba A505 notebook (AMD, fglrx, compiz, karmic 64 install) and was wondering if this is related.  My brightness control (FN+F6 & FN+F7) work fine on restarting, but after suspending my computer and restoring the session, those function buttons no longer work.  Where are you finding info about this issue?

---

### Post by clevertomato on 2010-02-01
Sorry, but I can't help you beyond what I've detailed worked for me finally. Have you tried adding " noapic" to the end of the appropriate line in Grub?

---

### Post by myk02k on 2010-02-02
> **shawnboy said:**
> Sorry, but I can't help you beyond what I've detailed worked for me finally. Have you tried adding " noapic" to the end of the appropriate line in Grub?

I was initially confused because it sounded like I needed the newest kernel to fix the issue.  However, after adding the "noapic" option in Grub, my issue is now gone.  Was this some sort of work-around using the noapic option?

---

### Post by turingmachine on 2010-02-02
Computer is HP TX2500 with ATI HD3200 graphics (ATI Technologies Inc RS780M/RS780MN). Updated from 9.04 with fglrx+compiz to 9.10 and have been having the "flashing boot screen" problem for several days now.

When this happens I can only boot by waiting for grub menu, pressing "e", and adding "text" to the end of the kernel line. Then I can "rm /etc/X11/xorg.conf" and X will start correctly.

Tried the 2.6.33-020633rc6-generic PPA kernel and edgers repository (as above, from [https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)) and adding "noapic" to end of kernel boot line. DKMS still exiting with build failed (see [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/320986](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/320986)). Went to go to "/var/lib/dkms/fglrx/" and remove all old versions. Trying to manually build using "dkms build -k 2.6.33 --kernelsourcedir /usr/src/linux-headers-2.6.33-020633rc6-generic -m fglrx -v 8.69" and "linux-source-2.6.33" but still fails. 

Then tried Ubuntu's 2.6.31-14-generic kernel and DKMS was able to build fglrx successfully. However, when trying to start X I got "incompatible kernel module" and "failed to map FB memory" errors. Still no success.

SUCCESS! Now have compiz and acceleration working with 2.6.31-14-generic using ati-driver-installer-10-1-x86.x86_64.run (proprietary). It didn't work earlier, wasting alot of time, but reinstalling mysteriously did the trick.

---

### Post by clevertomato on 2010-02-02
myk02k: work-around... i suppose you can call it that. I don't understand the nuts and bolts enough to explain it to you. Search net for "APIC" and it may give you some insight. Apparently there are couple different ways of accomplishing things like brightness adjustment keys... APIC is one and I think usually the default. If your machine doesn't employ that method, however, then "noapic" will help you in some cases. That's best stab at it I can make.

turingmachine: Don't you love it when that happens. Not as good as actually knowing what was going on and what fixed it, but sometimes you reach a point where you just don't care as long as it works.

---

