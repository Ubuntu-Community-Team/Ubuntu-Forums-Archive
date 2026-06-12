---
title: "Ubuntu Hardy Freezes on Ultrabay removal"
date: 2008-04-09
forum: Hardware
---

### Post by tenroc2o0o on 2008-04-09
I have a Thinkpad T43 (2668-91U)
Running Ubuntu Hardy 2.6.24-15
I have a 2nd Hard Disk adapter I freqently swap out with my UltraBay DVD-RW.

Even when the partition isn't mounted, when I attempt to remove the ultrabay Linux completely freezes including the mouse.

I found some articles on ThinkWiki about the UltraBay but they talk about specific drivers and list patches for older linux kernals.

Can someone help me figure out what is happening and how to fix it?

Thanks!
James

---

### Post by Tagallo on 2008-04-09
I have the same problem with Hardy on a R61. 
Should I try the Thinkwiki guides?

---

### Post by tenroc2o0o on 2008-04-15
Still having problem.. Anyone?

---

### Post by ss08 on 2008-04-16
Well the solution provided at the Thinkwiki worked for me. I have a X61 with an ultrabay.. What you need to do is find the offending hw that causes the problem (the CDROM for me) and the scsi host id for it. Scan the /sys/class/scsi_device/x:0:0:0/ folder and check out the vendor names. For me the CDROM id was 0.
So, to undock safely, I did 
echo 1 > /sys/class/scsi_device/<x>\:0\:0\:0/delete

To dock, I did
echo 0 0 0 > /sys/class/scsi_host/host<x>/scan

Make sure you get the "x" correct.
Hope it helps.

---

### Post by tenroc2o0o on 2008-04-16
Oops.

Well restarting Ubuntu. lol

I deleted 0:0:0:0 which apparently is my primary partition... *sigh*
I'll try 1:0:0:0 after it finishes scanning /dev/sda5 for errors on boot up.... Hope it boots ok.. lol

---

### Post by ss08 on 2008-04-16
Make sure that the host id is correct. As I mentioned in my earlier post, one way to do that would be to check the vendor in the /sys/class/scsi_devices/x:x:x:x/device directory. I don't think trial and error is a very good idea. One sure way to find out is by booting with and without the dock and diffing the /sys/class/scsi_devices directory.

---

### Post by tenroc2o0o on 2008-04-16
Ok I was able to eject and insert it a few times successfully while I was logged in as su in console. (sudo didn't seem to work a few times..?)
I finally figured out how to mark a script as executable (sudo chmod +x /scriptname..) so I used those two scripts from ThinkWiki they listed for insert and eject.
Except
I just ran the eject script and then popped out the eject tug bar (didn't actually pull out drive) and linux froze.

Rebooting..

Ok Inserted drive.. came up and mounted fine.
Unmounted drive.
Tried eject script - system beep. 
Tug bar popped out - still Ok this time...
-Begin to pull out drive - Lockup.
Errrr....

I'll reboot again and try it manually and see why script isn't working

---

### Post by ss08 on 2008-04-16
I didn't try the entire script. I was just happy that I was able to dock/undock without rebooting, even if I had to run a command prior to doing so. :)

For eject, did you try pressing the undock switch before pulling the undock lever? That switch triggers something, you'll see it in the dmesg log. Not sure how it works if you directly pull the undock lever, though,,,,

---

### Post by tenroc2o0o on 2008-04-16
Ok I just ran the eject script on ThinkWiki and my computer froze after a few seconds. Didn't TOUCH anything on drive.  Going to try manual deletion method again and try to figure out what's wrong with their script.
Oh, and I just noticed the very too last scripts (after the main ones here: )


**************Create /usr/local/sbin/ultrabay_insert with permissions 755:

```
#!/bin/bash
echo 12 > /proc/acpi/ibm/beep
sync
echo 0 0 0 > /sys/class/scsi_host/host1/scan
```

**************Create /usr/local/sbin/ultrabay_eject with permissions 755:

```
#!/bin/bash
ULTRABAY_SYSDIR='/sys/class/scsi_device/1:0:0:0/device'
shopt -s nullglob

# Umount the filesystem(s) backed by the given major:minor device(s)
unmount_rdev() { perl - "$@" <<'EOPERL'  # let's do it in Perl
	for $major_minor (@ARGV) {
		$major_minor =~ m/^(\d+):(\d+)$/ or die;
		push(@tgt_rdevs, ($1<<8)|$2);
	}
        # Sort by reverse length of mount point, to unmount sub-directories first
        open MOUNTS,"</proc/mounts" or die "$!";
        @mounts=sort { length($b->[1]) <=> length($a->[1]) } map { [ split ] } <MOUNTS>;
        close MOUNTS;
        foreach $m (@mounts) {
                ($dev,$dir)=@$m;
		next unless -b $dev;  $rdev=(stat($dev))[6];
		next unless grep($_==$rdev, @tgt_rdevs);
		system("umount","-v","$dir")==0  or  $bad=1;
	}
	exit 1 if $bad;
EOPERL
}

# Get the UltraBay's /dev/foo block device node
ultrabay_dev_node() {
	UDEV_PATH="`readlink -e "$ULTRABAY_SYSDIR/block:"*`" || return 1
	UDEV_NAME="`udevinfo -q name -p $UDEV_PATH`" || return 1
	echo /dev/$UDEV_NAME
}

if [ -d $ULTRABAY_SYSDIR ]; then
	sync
	# Unmount filesystems backed by this device
	unmount_rdev `cat $ULTRABAY_SYSDIR/block\:*/dev     \
	                  $ULTRABAY_SYSDIR/block\:*/*/dev`  \
	|| {
		echo 10 > /proc/acpi/ibm/beep;  # error tone
		exit 1;
	}
        sync
        # Nicely power off the device
	DEVNODE=`ultrabay_dev_node` && hdparm -Y $DEVNODE
        # Let HAL+KDE notice the unmount and let the disk spin down
	sleep 0.5
	# Unregister this SCSI device:
	sync
	echo 1 > $ULTRABAY_SYSDIR/delete
fi
sync
# Turn off power to the UltraBay:
if [ -d /sys/devices/platform/bay.0 ]; then
	echo 1 > /sys/devices/platform/bay.0/eject
else
	echo eject > /proc/acpi/ibm/bay
fi
# Tell the user we're OK
echo 12 > /proc/acpi/ibm/beep
```



************Create /etc/acpi/events/ultrabay-insert:

```
event=ibm/bay MSTR 00000001 00000000
action=/usr/local/sbin/ultrabay_insert
```

************Create /etc/acpi/events/ultrabay-eject:

```
event=ibm/bay MSTR 00000003 00000000
action=/usr/local/sbin/ultrabay_eject
```

====================================================

What do those two last scripts do?  Does that mean when I hit the switch to pop out the pull bar it'll automatically launch the script? Or are these required by the above eject script?

---

### Post by tenroc2o0o on 2008-04-16
Ok simply doing the following:
su
echo 1 > /sys/class/scsi_device/1:0:0:0/device/delete

works. The next line, echo eject > /proc/acpi/ibm/bay .. the bay object doesn't exist.

And i can reinsert with
su
echo 0 0 0 > /sys/class/scsi_host/1:0:0:0/scan


I'd love to use their script though because it looks like it automatically dismounts any paritions before ejecting and also powers down the hard disk - especially if it can be set to automatically run when you hit the eject switch.

---

### Post by ss08 on 2008-04-16
The last two scripts associate the the insert and eject scripts with an event, which I'm guessing is the release for eject. But as far as I can see in my laptop, it's just a mechanical lever. No idea how it can trigger an event in the kernel. Or maybe I'm stupid.
But, does the simple single command I suggested initially work? the fancy scripts in the thinkwiki page are all based on the assumption that those commands do work.

EDIT: I just saw your last post. So it does work. Atleast that's something.

---

### Post by tenroc2o0o on 2008-04-16
Yeah my last post...
I can unmount now with simply echo 1> /../delete
So i'm trying to figure out which part is locking it up...

Oh, and btrw: In Windows if I hit the switch and popped the tug bar out, Windows would automatically begin 'Safely Removing Hardware' and would say "It is now safe to remove this device..". I think it does send some type of signal.  I'd be interested in trying to figure out where that'd be logged away at..?

---

### Post by tenroc2o0o on 2008-04-16
Yeah thanks though... Probably wouldn't have kept trying had you not said it worked for you.

I commented out portion of script that unmounts existing file systems and it still froze linux after I ran it.

This is the only other line that actually does anything else:
```
# Nicely power off the device
	DEVNODE=`ultrabay_dev_node` && hdparm -Y $DEVNODE
```
Gonna try disabling that line..

EDIT: Yeah that didn't work either. I'm frustrated now. This can't be good for poor Ubuntu freezing 900 times.

---

### Post by tenroc2o0o on 2008-04-16
Now I'm pissed. I've litterally walked through the script and executed it by hand in the terminal command by command including the if statements -  worked like a champ.
When i execute it as a script it freezes linux.

---

### Post by MikeKnoop on 2008-04-28
Are you sure the script is even executing? The problem I've been having with docking/undocking is that the script is never called, meaning the event is not being triggered.

-Mike

---

### Post by MikeKnoop on 2008-06-03
Made a script to undock/redock the ultrabay. The script can be found in the following thread:

[http://ubuntuforums.org/showthread.php?t=816755](http://ubuntuforums.org/showthread.php?t=816755)

-Mike

---

### Post by ingo on 2008-06-24
So how comes this started in 8.04 while it worked perfectly in 7.10? Anybody any ideas? Has a bug been filed?

BTW - great the community has found a workaround - I for one would not have been able to...

---

### Post by MikeKnoop on 2008-06-24
I filed a bug this morning.

[https://bugs.launchpad.net/ubuntu/+bug/242638](https://bugs.launchpad.net/ubuntu/+bug/242638)

-Mike

---

### Post by ingo on 2008-06-24
Cheers, I added my 2cs

---

### Post by snowstar on 2008-07-14
I can take a stab at why --- the change between gutsy and hardy....

Has to do with the kernel in gutsy I was running kernel 2.6.22.x and upgrading to hardy running 2.6.24.x. I have read but not confirmed that the a couple of things have happened. Kernel module name has changed from ibm_acpi to thinkpad_acpi. But I have also read on the thinkwiki forum that libata is the culprit and it needs to be rebuilt.... At this point I'm not 100% sure what the ultimate fix is hopefully the the good folks quashing bugs for Ubuntu will figure out what the real problem is and fix it....

---

### Post by bomanizer on 2008-07-19
*crossing fingers for an easy fix to appear*

I also found myself hard-booting a couple of times before giving up. Gutsy handled bay events smoothly, but now with Hardy... ehh... I knew it! Should have stayed with 7.10 The upgrade frenzy always gets me...

---

### Post by bomanizer on 2008-08-12
*Bump*

Has anyone heard of updates on this issue?

---

### Post by bomanizer on 2008-08-25
> **ss08 said:**
> Well the solution provided at the Thinkwiki worked for me. I have a X61 with an ultrabay.. What you need to do is find the offending hw that causes the problem (the CDROM for me) and the scsi host id for it. Scan the /sys/class/scsi_device/x:0:0:0/ folder and check out the vendor names. For me the CDROM id was 0.
So, to undock safely, I did 
echo 1 > /sys/class/scsi_device/<x>\:0\:0\:0/delete

To dock, I did
echo 0 0 0 > /sys/class/scsi_host/host<x>/scan

Make sure you get the "x" correct.
Hope it helps.

This worked for me, though Thinkwiki is warning against this method. Does anyone know why? Are we in risk of trashing our drives with this method?

---

### Post by bismark on 2008-08-25
> **bomanizer said:**
> This worked for me, though Thinkwiki is warning against this method. Does anyone know why? Are we in risk of trashing our drives with this method?

I think the problem is that without doing the "echo eject > /proc/acpi/ibm/bay" or similar command you don't shutdown the power to the ultrabay.

My coworker on gentoo can run the exact commands specified by thinkwiki.org and the light next to his ultrabay turns off and then he can pull the device out. If I only run "echo 1 > /sys/class/scsi_device/$ID:0:0:0/device/delete" it removes the device from the system but I THINK (stress think) that the bay is still powered. Now is this going to instantly kill your device, I doubt it, but I don't think it's good to go swamp crazy and possibly fry your drive.

The problem as far as I can see is not with the actual removal of the SCSI device (cdrom or harddrive) but with the bay modules themselves (thinkpad_acpi.ko or bay.ko).  If either of them loads correctly there should be an entry in /proc/acpi/ibm/bay or /sys/devices/platform/bay.0/eject respectively.  Unfortunately neither of those entries show up or respond properly so you cannot properly power down the bay.

Just my $0.02.

---

### Post by bomanizer on 2008-09-17
Well, I found something... thinkwiki suggests adding a kernel boot option. Details [here.]("http://www.thinkwiki.org/wiki/Talk:Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61") Will try now, let's see how this turns out...

EDIT: bah, didn't do anything, still freezes. I think the reason is explained [here.]("http://www.mail-archive.com/ibm-acpi-devel@lists.sourceforge.net/msg01389.html")

---

### Post by bomanizer on 2008-10-04
I think this is solved in Intrepid. I just installed the current build and no issues so far :) It seems that when upgrading one should always skip one release ;)

---

