---
title: "ThinkPad W701ds experience"
date: 2011-02-13
forum: Hardware
---

### Post by tristano on 2011-02-13
I have a ThinkPad W701ds and can say it is close to fully-functional on Ubuntu 10.04 Lucid. I had a miserable time pulling together the information necessary to get to that point, but it's running like a champ now and I will try to provide some sort of documentation to that end.

The major issues encountered were graphics (NVIDIA), grub (fakeRAID), and suspend (USB3). Both 10.10 Maverick and 10.04 Lucid were attempted and in either case the problems start immediately.

The W701ds has a second screen built in and the Ubuntu installer apparently takes quite a liking to it. Once the initial "keyboard = human" logo does its thing, the boot process will move from the primary display to the secondary, even if the secondary display is closed. It also treats the secondary display as a horizontal screen rather than vertical (which is to be expected, I suppose), so text will begin scrolling sideways before it is replaced by a sideways graphical boot. The CD drive will make amusing noises for a few minutes and then stop. It appears at this point that the boot has frozen, but it is only the display. Moving the secondary display a little (go to open it if it is closed, close it a little if it is open) will cause the lights to come back on and the primary display will give you the option of a live boot or install, either of which will work fine at this point.

I chose to just install and manually partitioned the fakeRAID array (RAID0) with /boot, /, /home, and swap partitions. No issues were encountered until it came time for grub to be installed on the MBR. 10.10 pretended to install something onto the RAID MBR and 10.04 kept using /dev/sda regardless of the device selection. Neither worked upon reboot.

If a grub prompt appeared at all on boot, it was possible to fiddle with root, linux, and initrd commands in grub to boot the new installation, but the solution that seemed to work best was to go back to the live CD and "Try Ubuntu" rather than selecting install (minding the secondary display issue again). Once there, grub could be installed to the RAID array with something like the following in a terminal:

```

$ sudo mount /dev/mapper/isw_RAID02 /mnt/
$ sudo mount /dev/mapper/isw_RAID01 /mnt/boot/
$ sudo mount -o bind /dev /mnt/dev
$ sudo chroot /mnt/
$ sudo grub-install /dev/mapper/isw_RAID0

```

The "bind" option can be used on other system filesystems, if necessary (/dev/pts, /sys).

Another reboot and grub should load Ubuntu without any intervention, at least in 10.10. My experience in 10.04 was that the nomodeset option had to be added (this is for NVIDIA video cards) to the boot options at times. If the boot sticks at a black screen and will not continue (I still get a black screen on boot now, but it is temporary), reboot, hold Shift to enter the grub menu, press "e" to edit the kernel arguments, and type "nomodeset" without quotes right before or after "quiet splash" and then Ctrl+X to boot it. X/GDM should then load, allowing login to an account.

10.04 and 10.10 then diverge further. In 10.10, proprietary NVIDIA drivers were installed without a hitch. In 10.04, no driver from the repository would work, regardless of the kernel selected. The latest from nvidia.com had to be downloaded and installed. I did this after running "sudo apt-get purge nvidia-*" and adding blacklist entries for vga16fb and nouveau to /etc/modprobe.d/blacklist.conf, though I cannot confirm that those are necessary steps or if the NVIDIA install script would be all it takes. Note that the NVIDIA installer cannot run while X is active, so log out, log into the console at Ctrl+Alt+F1, and use "sudo service gdm stop" to turn off GDM and X prior to running the script. Be sure to opt to run nvidia-xconfig when installation completes so that the nvidia driver is used for X.

Now with a functioning nvidia driver, it became apparent that the secondary display should actually do something. I used nvidia-settings to configure the second display as a separate X screen. TwinView does not work as there is no way to rotate the secondary display while not rotating the primary. With separate X screens, the primary can stay as it is and the secondary can be rotated counter clockwise so that it makes sense to sane individuals. I added "RandRRotation" and "Rotate" options to /etc/X11/xorg.conf as follows:

```

Section "Device"
    Identifier     "Device1"
    ...
    Option         "NoLogo" "true"
    Option         "RandRRotation"
EndSection

...

Section "Screen"
    Identifier     "Screen1"
    ...
    Option         "Rotate" "CCW"
    ...
EndSection

```

Device1 and Screen1 should correspond to the secondary display. 

At this point, all features of the system should be working--audio, video, networking, stylus, camera--all except for suspend. It is a known issue that USB3 interferes with suspend, so the workaround is to unload the corresponding module. On 10.04, this is accomplished by adding this line to /etc/pm/config.d/unload_module :

```

SUSPEND_MODULES="xhci"

```

That should seal the deal for Lucid on the W701ds. The same workaround is required for Maverick (though with xhci_hcd instead of xhci), but it just exposes another bug that for some reason causes suspend to work only once per login session. A second suspend during a session will result in a resume to the login screen and the suspended session will be lost every time. Development X packages may fix this, but I opted for a downgrade to Lucid instead.

Everything is running great now, so I post this in the chance that someone who finds himself in my old shoes won't have to walk so far in them. The W701ds is a great system and I'd hate to run any other OS on it.

:cool:

---

### Post by rasa7777 on 2011-02-16
I have a w701ds, with Ubuntu 10.10, and have spent hours trying to get the external DVI ports to work, without luck. I could only get the VGA port to work, and only if I installed the nouveau drivers, then adding boot options to disable the DVI ports via

video=DVI-D-1:d video=DVI-D-2:d

I haven't tried the DisplayPort yet.

Has anyone had any luck driving an external monitor via DVI or DisplayPort?

FYI, everything works fine in Windows.

---

### Post by Zygmunt Krynicki on 2011-02-17
I've purchased this laptop a few days ago. It should be arriving shortly. I'll share my experience with you once I get my hands on it.

Thanks
ZK

---

### Post by tristano on 2011-02-17
> **rasa7777 said:**
> 
Has anyone had any luck driving an external monitor via DVI or DisplayPort?
I haven't messed around with external monitors because the built in dual screen fits what I need, but I seem to recall reading that the external ports are disabled if the internal accessory screen is enabled. In your testing, did you disable that screen or just the external DVI ports?

I know I used an external display a time or two during installation, with all of the trouble I had, and I know it worked at that point, but I just tried with the nvidia driver and had no luck. To be fair, I refused to disable the accessory display, since it would require a restart of X. Maybe I'll give it a shot later...

Zyg, cool, it would be great to learn more about what works and doesn't work on these things. I'm pretty stoked so far, hopefully it works out for you as well.

---

### Post by tristano on 2011-02-18
Ugh, DVI support seems to be quite horrid in 10.04 as well. The nvidia driver recognizes the monitor easily, but when I enable it, the primary display gets trashed and the external DVI display does nothing. I got the same result regardless of whether I disabled the internal accessory display or not. 

The W701 is "certified" compatible with 10.04, so that dual screen in the W701ds must really throw it off: [http://www.ubuntu.com/certification/hardware/201001-5133](http://www.ubuntu.com/certification/hardware/201001-5133)

Maybe disabling DFP-1 (that is the name of the accessory display in nvidia-settings, anyway) in grub would help, if that hasn't been tried. Of course then you'd need separate grub "profiles" for when you want to use the internal dual screen vs external.

---

### Post by tigerman123 on 2011-05-22
i am looking to buy w701ds but ebay is to expensive is there any where else can i find it. Please help or is there anybody selling one. thanks

---

