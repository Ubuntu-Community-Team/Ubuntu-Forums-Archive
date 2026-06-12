---
title: "Fakeraid with dmraid boot hangs at hid.core"
date: 2007-03-28
forum: Hardware &amp; Laptops
---

### Post by 1ino1eum on 2007-03-28
Hi

I've tried to install feisty and edgy on my fakeraid intel ich7  controler ... I've folowed the howto, everything when right, except that I can't boot because during the boot, it hangs in the initramfs at this line exactly :

drivers/usb/input/hid-core.c: v2.6:USB HID core driver

I've got a friend who has the same exact computer execpt the raid and he doent have this problem.

if I wait 3 minutes, I've got the busybox, and doing ls /dev/mapper shows me my raid drivers so dmraid is working but it seams the boot can't load something after drivers/usb/input/hid-core.c: v2.6:USB HID core driver...

help me tkx :)

---

### Post by 1ino1eum on 2007-03-29
ok I found the problem is that I ve got a lot of line during the boot :

attemp to access beyond end of device
sda: rw=0, want=582163478, limit=29304678

and again, again..
I dont know what is it at all :(

---

### Post by schlika on 2007-03-30
I had the exact same trouble using an nvidia-based raid0 fakeraid, and followed these istructions :bug/83231

[bug 83231]("https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/83231")

I simply created a script called : /usr/share/initramfs-tools/scripts/init-premount/udevSettle

containing :
------------------------------------------------------
#!/bin/sh -e
# initramfs premount script for udev

PREREQ="udev"

# Output pre-requisites
prereqs()
{
	echo "$PREREQ"
}

case "$1" in
    prereqs)
	prereqs
	exit 0
	;;
esac

/sbin/udevsettle --timeout=10
------------------------------------------------------

don't forget to chmod +x /usr/share/initramfs-tools/scripts/init-premount/udevSettle

and update your initramfs (update-initramfs -u) then reboot

Worked for me !!

---

### Post by 1ino1eum on 2007-03-30
tkx man but no, that didn't work as well : /

---

### Post by 1ino1eum on 2007-04-08
ok I tryed again today with no luck.
But I see that maybe it s not a dmraid problem but a SATA problem.
If I wait like 3 minutes, I've got those message before busybox:
check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev ALERT! does not exist.

The funny things is that there is NOTHING between ALERT! , and "does not exist" ... hum :)

---

### Post by PietroB on 2007-04-21
Did anyone resolve this? Thanks, P.

---

### Post by 1ino1eum on 2007-04-21
I gave up :(
I will retry with gusty gibbon.

---

### Post by pda1111 on 2007-05-05
A few comments on this one since I just messed around with it on feisty...

Schlika's script contains an error it seems:

The line "--timeout=10" should be "--timeout 10" withtout the equal sign

Furthermore instead of making a new script you can just add the line

/sbin/udevsettle --timeout 10

to the very end of /usr/share/initramfs-tools/scripts/init-premount/udev. 

I did this and it seems to work.

See [https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/83231](https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/83231) for more details.

BTW, to bypass the initial error and continue booting after falling back into busybox, you can just do

dmraid -ay
Ctrl-D

You can also add "break=mount" to the kernel line in grub to stop before mounting the file system. Do the above two commands there, and skip the several minute hang before exiting to busybox.

PS! I had to remove the splash stuff on the kernel line too.

---

