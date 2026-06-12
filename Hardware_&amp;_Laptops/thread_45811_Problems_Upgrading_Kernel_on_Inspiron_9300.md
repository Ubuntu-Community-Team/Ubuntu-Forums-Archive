---
title: "Problems Upgrading Kernel on Inspiron 9300"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by sloan3d on 2005-07-01
I have Ubuntu Linux 5.04 running on my Inspiron 9300 laptop. I've been seeing  random lockups when the machine runs unattended, so I went to Google to look for answers. I think I found the solution on the [Linux on Laptops "Installing Kubuntu (Ubuntu) on Dell Inspiron 9300" page](http://www.rtr.ca/dell_i9300/) .

The page says that upgrading the Linux kernel to 2.6.11.11, with the provided patches, will fix the problem. I've tried that, but I can't get a working kernel. The new kernel seems to boot up normally, until X starts. The laptop locks up at that point, leaving either a black screen, or a black screen with a frozen Ubuntu startup wait cursor. Control-Alt-Backspace and Control-Alt-Delete have no effect after that, so I hold down the power button until the computer shuts down. I suspect that I missed something while trying to either compile or install the new kernel, because I pieced the instructions together from several different tutorials.

Here's what I did:

1.) Downloaded linux-2.6.11.11.tar.bz2, the kernel source archive at kernel.org
2.) Started the Ubuntu Root Terminal, and extracted the archive to /usr/src
3.) Downloaded the patch and config files (kernel.patches.gz and kernel.config.gz) from the Linux on Laptops page, and gunzipped them
4.) Copied kernel.patches to /usr/src/linux-2.6.11.11
5.) Copied kernel.config to /usr/src/linux-2.6.11.11/.config
6.) Went to /usr/src/, removed the old linux link, and typed "**ln -s /usr/src/linux-2.6.11.11 linux**" to create a new one
7.) Went to /usr/src/linux-2.6.11.11
8.) "**make oldconfig**"
9.) Applied the patch using the old-school technique, "**patch -p1 < kernel.patches**", because when I tried the "--added-patches" flag in make-kpkg earlier, it complained that the patch isn't a Debian kernel package
10.) Waited a while after typing "**make-kpkg --append-to-version=i9300 kernel_image binary**"
11.) When the build process finished, typed "**dpkg -i kernel-image-2.6.11.11-ml19300_10.00.Custom_i386.deb**"
12.) Built the initrd file using "**mkinitrd -o /boot/initrd.img-2.6.11.11-mli9300 2.6.11.11-mli9300**"
13.) Checked to make sure the vmlinuz and initrd files arrived in /boot okay
14.) Edited /boot/grub/menu.lst to add the initrd file name to the new kernel's standard and recovery mode definitions
15.) Rebooted, and saw the same old lock-up

What am I missing?

---

### Post by mlord on 2005-07-02
I build my i9300 kernels "the old fashioned way", rather than using the Unbuntu/Debian kernel build scripts.  It seems to work for me.

If the system is locking up on launch of X11, then perhaps the /etc/X11/xorg.conf file is the culprit?

If not, then  try again, this way:  I have updated my page (which you linked to) to now include the latest 2.6.12.2 kernel + patches + dot_config file for my i9300.

Grab linux-2.6.12.2 from here:
[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.12.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.12.tar.bz2)

Unpack it in /usr/src/ and then grab my add-on patches from here:
[http://rtr.ca/dell_i9300/2.6.12/](http://rtr.ca/dell_i9300/2.6.12/)

Apply each of the patch files in turn (alphabetical order works for me), and then copy my dot_config file over as .config and do a make oldconfig afterwards.  Follow that with a plain "make" and go for coffee.

On return, run a plain make again, and watch for error messages (easier than watching the first make run).  There should be no errors.

Wipe out any pre-existing modules directory of the same name from /lib/modules/, most likely by doing:  rm -rf /lib/modules/2.6.12.2/

Now do "make modules_install" and then "make install".

Finally, edit /boot/grub/menu.1st and add a new entry for this kernel:


title           Ubuntu, kernel 2.6.12.2
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.12.2 root=/dev/sda5 ro quiet splash resume=/dev/sda6
savedefault
boot


No initrd is needed, since the required fs/drivers are compiled-in to the main kernel, but you will need to edit the "root=/dev/sda5" entry to match your root directory partition, and also the "resume=/dev/sda6" to match your swap partition.

Cheers

---

### Post by mlord on 2005-07-02
One other idea is:

What video hardware does your i9300 have?  My kernel dot_config does NOT include the Nvidia AGP support, since mine uses the ATI X300 video card.  If your machine has Nvidia hardware, then you'll likely need to edit the dot_config (or use "make xconfig") to turn on CONFIG_AGP_NVIDIA and CONFIG_FB_NVIDIA.

If that turns out to be the issue, let me know, and I'll make it part of my standard dot_config for the future.

Cheers

---

### Post by sloan3d on 2005-07-05
I have the 128MB ATI X300 on my laptop. I tried checking my xorg.conf by temporarily changing its video driver from "ati" to "vga". The lockup still happened after I rebooted.

I'm just about to try the new kernel/patches you posted. I'll let you know how it works out.

Thanks.

---

### Post by sloan3d on 2005-07-05
I followed your instructions for building 2.6.12. I get the same result -- lockup right before X starts. So, that suggests the kernel isn't the problem.

Because of the work I do with this laptop, I've removed the two screws holding in the laptop hard drive, so I can swap between two drives of the same make and model. Both drives have Hoary Hedgehog installed. The drive with the problem was completely quarantined from any network access (for work reasons), as soon as I got Ubuntu up and running. The other hard drive is allowed to have network access, so it has about three weeks of Update Manager updates that the problem drive missed. Other than those few updates, which include one minor update to the 2.6.10-5 kernel, the two drives are identical, and running in the same laptop.

A few weeks ago, I used your page's instructions to build the 2.6.11 kernel on the drive with network access. Other than a few warning messages during bootup, the newer kernel works perfectly on that drive. When I tried copying that kernel to the isolated drive, the laptop showed the same lockup problems I described earlier. Since then, I've tried building several versions of the kernel directly on the isolated machine, and all of them lock up in the same way.

It's a very strange problem. The two drives should be identical, but one works fine with a newer kernel, and the other locks up.

I went to /var/log, to see if one of the files there might give me a clue. I checked Xorg.0.log and Xorg.0.log.old. They recorded the last time I started X from the working kernel (2.6.10-5), but not the attempt to start X in 2.6.12. /var/log/debug is similar -- it didn't record anything around the time when I tried booting into 2.6.12, but it has records of booting 2.6.10-5 before and after. In /var/log/kern.log, there are only three lines from around the time of the failed boot:

```
Jul  5 15:05:42 localhost kernel: apm: BIOS not found
Jul  5 15:05:47 localhost kernel: Kernel logging (proc) stopped.
Jul  5 15:05:47 localhost kernel: Kernel log daemon terminating.
```

In /var/log/messages, I found these lines from around that time:

```
Jul  5 15:05:39 localhost gconfd (ssloan-7721): Exiting
Jul  5 15:05:39 localhost shutdown[6421]: shutting down for system reboot
Jul  5 15:05:42 localhost kernel: apm: BIOS not found
Jul  5 15:05:47 localhost kernel: Kernel logging (proc) stopped.
Jul  5 15:05:47 localhost kernel: Kernel log daemon terminating.
Jul  5 15:05:47 localhost exiting on signal 15
```

Could the "BIOS not found" message be the real problem? What would keep the laptop from seeing the BIOS? Is it something to do with APM? As far as I can tell from your .config file, APM is completely disabled in the kernel I built.

---

### Post by mlord on 2005-07-08
The "apm: BIOS not found" message is normal for a modern laptop --> just means that we have no choice but to use ACPI for power management.  Ignore it.

For the 2.6.12.2 kernel not working, I suggest you (1) ensure that you have the kernel modules for it in /lib/modules/2.6.12.2/*, and that (2) the /boot/grub/menu.1st lines have correct paths for root= and resume= .. should match those from the other (working) kernels listed there.

If you would care to email me (mlord at pobox . com), then I might make a private copy of my pre-built kernel/modules available to you to try.  This would eliminate any potential build issues from the equation.

Cheers

---

### Post by sloan3d on 2005-07-08
I found an odd solution to my problem just this morning. I found out there was one other difference between the working laptop drive and the problem drive, that I hadn't thought of -- unlike the working drive, I'd disabled networking in the problem drive, and somehow, that kept it from booting 2.6.12.2.

Yesterday afternoon, I gave up on simply recompiling the kernel, since none of the kernels I tried to build ever worked on that drive. So, I backed up my data, then used Norton Ghost and a blank DVD to copy the entire working drive onto the problem drive. The overwritten problem drive booted fine after that... until I fiddled with the network settings.

After I disabled eth0 in the network-admin GUI, then tried to reboot, the laptop showed the same lockup symptoms that it did before. I copied the Ghosted DVD back over the drive, and that fixed it.

The next time I decided to change the network settings, I made a backup of /etc/network/interfaces, then edited the file by hand. Same lockup. But this time, I had a backup of my original interfaces file, so I booted into recovery mode, and copied the backup over the changed interfaces file. The laptop rebooted just fine.

I've given up on trying to disable the network card now, since it caused so many problems. So, I decided to find another solution, to keep that drive off the network. I've added a "pause" line to my grub menu.lst, that reminds me to unplug the network cable before booting.

Thank you so much for all the help!

---

### Post by mlord on 2005-07-08
The network setup has a longish timeout, so if you wait long enough .. minutes, not seconds .. it should eventually continue.

Cheers

---

