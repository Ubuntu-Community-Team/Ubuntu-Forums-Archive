---
title: "HP dv2600 Install"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by starcannon on 2007-10-02
```
 
As of Ubuntu 8.04 Hardy Heron the only thing you must do is install your video drivers,
everything else just works, the annoying boot error has disappeared. 

The WebCam still will not go for more than 10~30 seconds at a time though, hope the 
uvcvideo guys can fill us in on how they got theirs working, as they list it fully 
functional.

```

```

******************************************
*** UPDATE:*******************************
****---------------------------------****
****With the Release of Gutsy************
****Use of the Desktop Live CD**********
****is possible.************************
*****************************************
*****************************************

```

**How to do a base install of Ubuntu Linux Feisty 7.04 Onto an HP Pavilion Entertainment PC (notebook) model dv2600**
*Things You Will need*: Computer with Internet Access, Thumb-drive, Internet Connection with ether-net access, and of course an HP dv2600. 
1. Download Alternate Install CD (live CD will not work as of the time of this posting)
2. **Choose** Option 1 from Alternate install CD boot menu, ignore memory error.
3. Install following along with the wizard.
     a) **If** you would like to keep the OEM Restore Partition be sure to choose Manual Partitioning.
     b) While Partitioning take the time to create a separate /home partition (this is a lifesaver)
            **Manual Partitioning quick guide** 
            i) Being Sure not to Delete the OEM Restore Partition(about 9.5gb on my machine). Do delete the larger system partition.
           ii) Create a Primary Partition ext2 about 128mb in size, set it as /boot, and set it as bootable.
          iii) Create another Primary Partition, size should be the same or double your RAM, so if you have 1gb of ram make a 2gb partion, set it as /swap
          iv) Create a Logical (or is it Extended?) Partition, 20-40gb is sufficient (some would say thats overkill) ext3 is fine, set it as /root.
           v) Create another Logical (or is it Extended?) Partition using up the remaining drive space, ext3 is fine, set it as /home
     c) Continue along with the install wizard until finished.
4. **While** install is doing its thing, get on another computer (you do have one right?) and download the latest 8 series drivers from [http://www.nvidia.com](http://www.nvidia.com), put these on a thumbdrive.
5. Reboot, making sure to remove install media.
6. **X server** is going to crash, don't worry about it, do make sure you have a network cable plugged in at this point though (i tried it once by carrying files on the thumb drive, that was a pita). Just select "No" to the X server crash screens, there'll be 2 of them I believe.
7. Login with your username and password.
8. **First** lets get the necessary stuff on there.
     a) At the command prompt enter: sudo modprobe ide-generic
     b) At the command prompt enter: sudo apt-get install build-essential
9) **Okay** now that you have the required build tools lets install the Nvidia Driver.
     a) Mount your usb drive, at the command prompt enter: sudo mkdir /media/thumb
     b) Next, at the command prompt enter: sudo mount -t vfat /dev/sdb1 /media/thumb
     c) Next, at the command prompt enter: cp /media/thumb/NVIDIA*.run /home/username
     d) Now, at the command prompt enter: sudo ./NVIDIA*.run
          i) Answer affirmatively to all of the screen prompts.
10) **Hang in there,** almost done, now to make sure that optical drive works everytime.
     a) At the command prompt enter: sudo nano /etc/modules
          i) append the document with "ide-generic" *no quotes*.
         ii) CTRL-X
        iii) Y
11) **Woohoo,** your about to see the desktop on your shiny new HP dv2600
     a) At the command prompt enter: sudo /etc/init.d/gdm restart
     b) Alternately you can just tyep: sudo reboot
12) Login
13) **Run updates,** orange icon upper right corner of screen.
14) Reboot
15) **RUH ROH!!!** The X server crashed didn't it, no worries, its just because you have a new kernel from the update.
     a) Tell the crash logs no, yes, whatever, just get through both of them.
     b) Login with username and password.
     c) At the command prompt enter: sudo ./NVIDIA*.run
          i) Answer all questions affirmatively except the last one that asks if you'd like to configure the xorg.conf file, tell it no (that way you don't lose any changes you may have made)
16) **Okay** back to the Desktop
     a) At command prompt enter: sudo /etc/init.d/gdm restart
     b) Or alternately you can enter: sudo reboot
17) Thats it, your done, you now have a base install of Ubuntu Linux Feisty 7.04 running on your shiny new HP dv2600, with wireless networking and the latest Nvidia drivers, notice the scroll bar works on the touch pad *outta the box* nice huh?
18 ) **ENJOY!!!** 8)

If I left something out please post it below.
**HELP** Does anyone know whats causing that memory error at boot up? or does anyone know how to make that memory error go away?

~Rob aka starcannon

---

### Post by unix.paul on 2008-02-01
Hi, 
what about CPU scaling? I have an HP dv2690, Ubuntu 7.10 regularly installed but with an error while loading Kernel in /sys/devices/system/cpu/cpu0/cpufreq/ NO DEVICE....

tnks:confused:

---

### Post by starcannon on 2008-04-18
CPU Frequency Scaling How To:

[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

---

### Post by unix.paul on 2008-06-09
> **starcannon said:**
> CPU Frequency Scaling How To:

[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

I've tried, but nothing, the error says There is no control of CPU ..

cat cpufreq says no device :(:confused:

---

### Post by starcannon on 2008-06-09
on the dv2600 I followed that guide and it "just worked"

on my Dell Inspiron | 5100 i had to add some of this stuff to, depending on your CPU etc... what you modprobe may vary.

GL

---

### Post by jethai on 2008-06-13
> **starcannon said:**
> on the dv2600 I followed that guide and it "just worked"

on my Dell Inspiron | 5100 i had to add some of this stuff to, depending on your CPU etc... what you modprobe may vary.

GL

What bios do you have, por favor? Or anyone with a working install  for that matter...
I've just installed and almost everything is working with exception to CPU Frequency Scaling (Unsupported). In turn, my fan is running at full blast and I'd like to have it working.

I believe I have F.25 and don't see any option in the bios for enabling cpu-fs. In this bog: [http://aldeby.org/blog/index.php/hp-pavilion-bios-changelogs-and-download-links.html](http://aldeby.org/blog/index.php/hp-pavilion-bios-changelogs-and-download-links.html), I noticed some other bios versions specifically address the issue, but I might have a newer bios tuned for Vista.

Thanks!

---

