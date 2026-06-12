---
title: "Almost fully functional Toshiba P205-S6237"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by rivera151 on 2007-11-24
Just to share, I'm posting what I did to get my Toshiba laptop working.  It was functional when I had it running Feisty, but hibernate and suspend where nowhere close.  I did the upgrade to Gutsy through the package manager, mostly because I knew that the Gutsy kernel allows me to bypass that horrid noise the hard drive made when shutting down, but so far, Gutsy's come along nicely.

This is for those of you newbies (like myself) who are new in the Linux world but love it once they get it all to work.  Post your success (or failure) story so I can shape this post up.

With Feisty I didn't have sound issues, nor issues with the Atheros WLAN; they worked out of the box, and the Gutsy upgrade didn't mess it up.  So I will not discuss sound or WLAN.

The first noticeable thing is getting the resolution working (1440x900).  Although there are many tutorials covering 915resolution, I'll post here the short and sweet.

[LIST=1]
[*]Download 915resolution --> "sudo apt-get install 915resolution"
[*]Use it to list your video modes --> "sudo 915resolution -l"
[*]Find an unused mode in the list (I chose mode 38, since I don't use an 8 bit per pixel resolution)
[*]Add the 1440x900 video mode to the /etc/X11/xorg.conf file **under 24 bpp mode**
[*]Find a way to run 915resolution in single user mode, before starting X
[/LIST]

The last item was the most challenging for me to find out.  I believe the easy way of doing that is editing the file /etc/default/915resolution ("sudo gedit /etc/default/915resolution") and adding the relevant information.  In my case, the file reads:
```

MODE=38
XRESO=1440
YRESO=900
BIT=32

```

If that doesn't work, the hard way goes like this:
[LIST=1]
[*]Create the file /etc/rcS.d/S51run-915resolution --> "sudo gedit /etc/rcS.d/S51run-915resolution"
[*]Add the line "915resolution 38 1440 900 32" to the file and save it
[*]Make the file executable --> "sudo chmod +x /etc/rcS.d/S51run-915resolution"
[/LIST]

Important: if you have to recur to the second method, make sure the parameters fed to 915resolution match the ones in /etc/default/915resolution; this will be important when we get hibernate working.

If you followed the instructions, your display should be working allright now.

Now let's get hibernate working.

I found out that the two biggest culprits on resuming from hibernate are:
[LIST=1]
[*]The LAN and WLAN hardware
[*]915resolution
[/LIST]

Fortunately, they are easily handled.  If you open /etc/hibernate/common.conf ("sudo gedit /etc/hibernate/common.conf") and find the section "Hardware tweaks" you will see that the line "Runi915resolution yes" is commented with a hash (#).  Uncomment it (remove the hash) to enable this line in the script.  The default parameters you supplied to /etc/default/915resolution will take care of everything.

For the LAN and WLAN interfaces, they need to brought down before suspending/hibernating and brought back up on resume.  Additionally, the kernel module for the Atheros WLAN must be removed on suspend/hibernate and reinserted on resume.  The /etc/hibernate/common.conf file provides for this also.  In the "network" section you can uncomment the two lines.  I made it look like this
```

### network
DownInterfaces eth0 ath0
UpInterfaces auto

```

That brings down both my ethernet and wireless interfaces.  "UpIntefaces auto" simply brings back only the interfaces brought down on powering down. 

To remove the ath_pci kernel module scroll to the modules section and make it look like this:
```

### modules
# UnloadModules snd_via82cxxx usb-ohcisuspend2 hibernate text
# UnloadAllModules yes
UnloadBlacklistedModules yes
LoadModules auto
# LoadModulesFromFile /etc/modules

```

Note that the "UnloadBlacklistedModules yes" line is uncommented.  The ath_pci driver is blacklisted by default.  See for yourself in the /etc/hibernate/blacklisted-modules file.  Do not unblacklist it, it is like this for a reason.

If when you resume hibernation you find that the computer is slow, but picks up speed much later after resuming (e.g. programs don't open as fast), you might need to specify your swap partition.  To do so, open the file /etc/hibernate/suspend2.conf and uncomment the line:
```

## useful for initrd usage:
SuspendDevice swap:/dev/sda2

```

Of course, you should replace /dev/sda2 with whatever your swap partition is.  Run the command "cat /etc/fstab" if you don't remember your swap partition.

If you hibernate and close the lid, an ACPI event is triggered that makes the computer go into a low power state, thus aborting the hibernate procedure.  To bypass this, open the file /etc/acpi/events/lidbtn ("sudo gedit /etc/acpi/events/lidbtn") and comment out the two functional lines.  My file now looks like this:
```

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

#event=button[ /]lid
#action=/etc/acpi/lid.sh

```
You can still set up a lid event through the Gnome Power Manager, so this will not hurt.

The the kernel has a quirk regarding the SATA HDD; on shutdown, the disk cache is not flushed and this causes a grinding noise on shutdown.  To fix this, do the following:
[LIST=1]
[*]Create the file /etc/rc0.d/S00shutdown-workaround --> sudo gedit /etc/rc0.d/S00shutdown-workaround
[*]Enter the following text in the file
[/LIST]
```

#! /bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown

```
[LIST=3]
[*]Save the file
[*]Make it executable --> sudo chmod +x /etc/rc0.d/S00shutdown-workaround
[/LIST]

This will get rid of the grinding sound on shutdown.  However, I have noticed that upon restart, the noise is there again, so I'm not sure if this is a permanent fix, but I will edit this if I get more info.

Go Ubuntu!

PS: To get the Chicony camera working, download "Cheese" from the repositories.

[EDIT 11/26/07 12:45 AST] Removed the USB section, since they no longer cause me any problems.  Added the section on SATA HDD cache flush "fix".
[EDIT 11/27/07 17:05 AST] Added swap partition configuration info.  Also, added info on disabling acpi lid event.

---

