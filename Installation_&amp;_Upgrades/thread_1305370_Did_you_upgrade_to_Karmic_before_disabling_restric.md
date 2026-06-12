---
title: "Did you upgrade to Karmic before disabling restricted or 3rd party drivers?"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by bswilson on 2009-10-29
Well friends, if you (like me) went ahead and upgraded to Karmic but failed to disable any restricted or 3rd party drivers, you may encounter problems.

I have a home-built PC that has an nvidia GeForce 5500 AGP video card, and I use the restricted nvidia drivers.  I forgot to disable them before I upgraded.  I had downloaded the Alternate Installation ISO via bittorrent, so I was all prepared to skip the network install headaches.

The install went fine, but when I rebooted, my screen was flashing so violently that I could not even log in.  The GUI logon screen wasn't even presented.  Things were so whacky, my system wasn't even fully booting, so I couldn't SSH to it from another machine!

**How I fixed this**

Luckily, I had a bootable Knoppix CD.  I was able to boot into Knoppix, mount my Karmic system's HDD as read/write, and go into **etc/X11/xorg.conf** and change the driver from **nvidia** to **nv** (the one that comes with Ubuntu).  Once I did that, I was able to boot into Karmic with no problems.

---

### Post by layingback on 2009-10-30
Thanks for posting this!  I needed it, when I too wasn't psychic enough to know to disable restricted drivers!

---

### Post by ghicksrn on 2009-10-30
I upgraded netbook remix on my Dell Mini 9 with the 3rd party Broadcom driver in use. I had no option since it was being used for my connection. It posed no problem for me. But as I said, I had no choice.

---

### Post by nzo on 2009-10-30
I did a clean install and when I activated restricted Nvidia driver and rebooted, I had same shaking screen w/no login. Unfortunately, I could not restart as it seems to have killed my mobo. Asus m2n32-sli deluxe with 7600gt cards in sli. Probably should have stuck w/9.04 for a while.:(

---

### Post by joplass on 2009-10-30
Upgrade should automatically disable 3rd party software.  It did on mine.  I will report back if there is trouble.

---

### Post by wsxaz on 2009-10-31
Is there a possibility to open /etc/x11/xorg.conf in the recovery mode? (text only)

EDIT: yes there is. Never mind.

---

### Post by ratcheer on 2009-10-31
Ok, I am booted to an old Ubuntu 6.06 LiveCD. It also operates only in text mode. How do I find and mount the hard disk rw so I can edit the config? I have tried "sudo mount -nrw /dev/sda4" but it responds that /dev/sda4 cannot be found in /etc/fstab.

Or, alternatively, how do I boot to "recovery mode"? I assume that would be booting to the hard disk.

Thanks, Tim

---

### Post by lapdog on 2009-10-31
> **joplass said:**
> Upgrade should automatically disable 3rd party software.  It did on mine.  I will report back if there is trouble.

This seems reasonable.  It should also notify the user that it is doing so.

---

### Post by ratcheer on 2009-10-31
Ok, I have my PC booted into GUI mode after booting in recovery mode and editing /etc/X11/xorg.conf, as described in the first post of this thread.

However, it is still not using the nVidia driver. How do I properly install the nVidia driver for 9.10 without getting it all fouled up, again. I seem to have the understanding that, with 9.10, I am no longer supposed to download the proprietart driver from nVidia's website and install it myself. What am I supposed to do, instead?

Thanks,
Tim

---

### Post by ratcheer on 2009-10-31
Ok, I have the video driver all fixed. I downloaded 190.42 from nVidia and installed it in the usual manner.

Tim

---

### Post by werdnaelliott on 2012-07-25
This is an old thread...but still helpful!

I am running 10.04 on a machine that has a NVIDIA video card.  I tried installing the NVIDIA drivers but it didn't improve any visuals so I uninstalled minutes after.  Apparently the file '/etc/X11/xorg.conf' was still step up to use the NVIDIA drivers, because upon reboot I got a flickering terminal login screen.  

I saw what you said about the xorg.conf file and booted into recovery (hold left shift during boot to bring up the GRUB menu, and select recovery), started a root terminal and edited the 'xorg.conf' file changing "nvidia" to "nv", then rebooted.

Upon reboot Ubuntu complained about bad video driver config and I selected the "reset to default" options and rebooted again, success.  No more flickering terminal login screen, just the normal GUI login.

Thanks for the post.

---

