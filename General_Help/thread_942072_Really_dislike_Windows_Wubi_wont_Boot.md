---
title: "Really dislike Windows Wubi wont Boot"
date: 2008-10-08
forum: General Help
---

### Post by jmambr on 2008-10-08
I would like to migrate from XP on a 700m Dell laptop. Have tried 8.04 live CD..... hangs during boot. Have tried 8.10 beta... live CD. This boots OK. Like it very much. But Wubi install under Windows:

1- Creates the Ubuntu folder.
2- Creates the CD image.

But boots into something called busybox which has the look of a DOS window. What do I do at this point?

---

### Post by ago on 2008-10-09
> **jmambr said:**
> I would like to migrate from XP on a 700m Dell laptop. Have tried 8.04 live CD..... hangs during boot. Have tried 8.10 beta... live CD. This boots OK. Like it very much. But Wubi install under Windows:

1- Creates the Ubuntu folder.
2- Creates the CD image.

But boots into something called busybox which has the look of a DOS window. What do I do at this point?


Press ESC at boot after "Ubuntu" and try the other boot option, in verbose mode note any error message.

---

### Post by jmambr on 2008-10-09
I booted in the verbose mode. The last message was?????

[5.128224]Clocksource tsc unstable (delta = -206404041 ns

What does this mean and how is it fixed?

---

### Post by ago on 2008-10-09
> **jmambr said:**
> I booted in the verbose mode. The last message was?????

[5.128224]Clocksource tsc unstable (delta = -206404041 ns

What does this mean and how is it fixed?

That should not be the relevant error. Do you have a complete system freeze or can you type commands in a terminal?

---

### Post by jmambr on 2008-10-09
I do not get a complete system freeze, I am able to type commands into busybox.

I rebooted a few more times and find that it now dies after the following:

[9.581665] ieee 1394: Host added: Id: Bus[0-00:1023] GUID[811f0f005799af00]

As before, I do not get a complete system freeze, I am able to type commands into busybox.

---

### Post by ago on 2008-10-10
Then post the output of the following

cat /proc/cmdline
cat /proc/partitions
cat /proc/mounts
grep err /casper.log
grep mount /caseper.log

---

### Post by jmambr on 2008-10-10
The results from cat /proc/cmdline

debian - installer/custom-installer = ubuntu/install/custom-installation iso-scan/filename=/ubuntu/mstall/installation.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/Local=en_us.utf-8 console-setup/layoutcode=us console-setup/variantcode = - -

The results from cat /proc/partitions

	major		minor		# blocks	name
	8		0		97685784	sda
	8		1		48169		sda1
	8		2		93988282	sda2
	8		3		3646755	sda3

The results from cat /proc/mounts

	rootfs 	/	rootfs rw 0 0
	none	/sys sysfs rw,nosuid,nodev,noexec, 0 0
	none	/proc proc rw,nosuid,nodev,noexec, 0 0
	udev 	/dev tempfs rw,mode=755 0 0
	fusectl	/sys/fs/fuse/connections fusectl rw 0 0

I received no observable output for grep err/casper.log  or  grep mount/casper.log

Is there a way to route the above to a textfile? If so, do I have to create a textfile beforehand? If so where?

---

### Post by ago on 2008-10-13
> **jmambr said:**
> 
Is there a way to route the above to a textfile? If so, do I have to create a textfile beforehand? If so where?

mkdir -p /mnt
mount /dev/sda2 /mnt
cp /casper.log /mnt

---

### Post by jmambr on 2008-10-13
Thanks for showing me how to copy the output to the file.

Do you have any further thought on how I can get wubi to work? 

What do you think of this approach.... I have another notebook that Wubi does run. Suppose I were to copy the Ubuntu directory (with the disk image) to the computer that does not run. Would this work?

---

### Post by ago on 2008-10-15
I'd like to see the logs, so I can be more precise. You can read it yourself using the more command and only posting error lines, particularly ones involving mountpoints. Screenshots will do too.

---

### Post by jmambr on 2008-10-15
Yesterday I noticed that one of the Norton utilities (GoBack) is initiated at the boot level. In order to see if this program was the source of the problem, I:

- Uninstalled the utility, which took a couple hours.
- uninstalled Ubuntu
- reinstalled Ubuntu and tried to boot.

This time Ubuntu IPL'd to the password screen and completely froze up. At this point, I am going to put Linux on the back burner (maybe trying 8.10 when it is released) until some time in the future.

Thanks very much for your time and effort that was spent on the problem.

---

### Post by ago on 2008-10-16
> **jmambr said:**
> 
This time Ubuntu IPL'd to the password screen and completely froze up.

There are 2 password screens, one in windows (wizard) and one in linux after second reboot (login).

In the second case it is probably a problem related to the video driver/configuration which can usually be fixed by pressing ESC at boot after "Ubuntu" and selecting rescue mode.

---

