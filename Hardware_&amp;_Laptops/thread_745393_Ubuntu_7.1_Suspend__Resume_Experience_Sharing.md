---
title: "Ubuntu 7.1 Suspend / Resume Experience Sharing"
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by milktea on 2008-04-04
[FONT="Arial"][SIZE="3"]Just a note to share my experience configuring suspend / resume in Ubuntu 7.10. It may not be the most optimize way, but that's what I did and make it work.

_1. The Suspend Process_

In Ubuntu 7.10, when you click suspend, here is what happen,

a. /etc/acpi/hibernate.sh is called
b. a bunch of ACPI and preparation script are run
c. /sbin/s2disk is run and suspension happen

With above basic, here is what I did.

_2. Installed uswsusp using following command._

sudo apt-get install uswsusp

This will give you s2disk in the /sbin directory.

_3. Configure uswsusp_

s2disk default configuration file is in /etc/uswsusp.conf

It is important to set the "resume device" to your linux swap, UUID doesn't work in my case, So I used the "/dev" notation. Below is my  uswsusp.conf file.

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/disk/by-uuid/6d77e24a-79d3-425c-bac6-f875a3f35855
splash = y
compress = y
early writeout = y
#image size = 2.26133e+09
RSA key file = /etc/uswsusp.key
shutdown method = platform

_4. Resume Process_

A lot of people talk about how to suspend, not that many talk about resume on the web. It took me quite I while to figure it out.

To resume, it is related to the boot process, so GRUB and initrd has to be properly configured.

a. GRUB, go to /etc/grub, edit menu.lst, make sure the resume option is there. Here is how my menu.lst look like.

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=25d8c849-34b1-4009-81e1-d313a20844d7 resume=UUID=6d77e24a-79d3-425c-bac6-f875a3f35855 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

b. initrd

i. Make sure the swap drive UUID is correct in this file /etc/initramfs-tools/conf.d/resume, Sometimes it is not updated. You can the UUID of swap drive using following command

/vol_id /dev/sda6 (or your swap drive id)

ii. After update above file, run 

sudo update-initramfs -u

This will update the initrd.img file in /boot directory. This will generate a new image that is aware of the swap drive location for resume purpose.

_5. Test with /sbin/s2disk_

With this in place, you can try 

sudo /sbin/s2disk

Chances are it will work, you see the screen go off and the harddisk is spinning when the hibernate image is created.

Then you are try to switch on your computer again. GRUB will show up, select the Ubutu option and the system should able to resume.

Now your /sbin/s2disk and resume function is probably configured

_5. Test with /etc/acpi/hibernate.sh_

The GNOME GUI will only call /etc/acpi/hibernate.sh, then the hibernate.sh will call /sbin/s2disk to suspend.

So it is important to tune /etc/hibernate.sh to make everything working. The /etc/hibernate.sh will call some acpi and prepare function, some of it will cause the resume fail. So I commented most of the /etc/hibernate.sh file. The only important line is /sbin/s2disk.

Below is how it look like.

#!/bin/bash

. /etc/default/acpi-support
# These 2 line cause my PC fail to resume, reason unknown, but just commented it to make it work
#. /usr/share/acpi-support/power-funcs
#. /usr/share/acpi-support/policy-funcs

if [ x$ACPI_HIBERNATE != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

# Unset video posting - it's not needed for suspend to disk
unset POST_VIDEO
unset USE_DPMS

. /etc/acpi/prepare.sh

#if [ x$LOCK_SCREEN = xtrue ]; then
#    for x in /tmp/.X11-unix/*; do
#	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
#	getXuser;
#	if [ x"$XAUTHORITY" != x"" ]; then
#	    export DISPLAY=":$displaynum"
#	    . /usr/share/acpi-support/screenblank
#	fi
#    done
#fi

echo -n $HIBERNATE_MODE >/sys/power/disk
# Below is commented as s2disk don't suppory -x / -y anymore, and s2disk is configured to use /etc/uswsusp.conf for the device

#if [ -x /sbin/s2disk ]; then
#    DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
#    if [ -f /etc/usplash.conf ]; then
#	. /etc/usplash.conf
#	/sbin/s2disk -x "$xres" -y "$yres" $DEVICE
#    else
#	/sbin/s2disk $DEVICE
#    fi

# s2disk will call /etc/uswsusp.conf for parameters
	/sbin/s2disk
#else
#    echo -n "disk" >/sys/power/state
#fi

$LAPTOP_MODE stop

. /etc/acpi/resume.sh

Now, once you tuned /etc/acpi/hibernate.sh file, instead of type /sbin/s2disk at shell, you can initiate hibernate through the GNOME GUI. However, it may take a few round to trial and error to adjust hibernate.sh script to make sure the acpi / prepare script don't impact the suspend / resume process.

Good luck, enjoy hibernate and hopefully save more power / CO2 for the world.[/SIZE][/FONT]

---

### Post by Hylian7 on 2008-04-12
Thank you for posting this. You deserve so much more credit. I have been tinkering around with this to fix my hibernate for a month, and this fixed it. Now to just get suspend (suspend to ram) working.

---

### Post by BkkBonanza on 2008-04-12
Yes. Thank you.
I have not been having success with this since installing Ubuntu.
I will give it a try. 

Why doesn't Ubuntu come configured to work with suspend properly? It has never once worked since I installed and I gave up a couple weks ago.

Chris :)

---

### Post by BkkBonanza on 2008-04-13
Well, tried as suggested above.
Suspended ok.
But doesn't resume at all. Maybe I'm doing it wrong?
After suspend the power is off - so I press the power button and what I get is a normal boot process same as if I just powered off normally. 
I did add the resume line to /boot/grub/menu.lst - apparently grub doesn't use it?

Any ideas?

Thanks,
Chris :)

---

### Post by milktea on 2008-04-18
BkkBonaza,

Apart from configuring GRUB. You also need to do following.

_b. initrd_

i. Make sure the swap drive UUID is correct in this file /etc/initramfs-tools/conf.d/resume, Sometimes it is not updated. You can the UUID of swap drive using following command

/vol_id /dev/sda6 (or your swap drive id)

_ii. After update above file, run_

sudo update-initramfs -u

This will update the initrd.img file in /boot directory. This will generate a new image that is aware of the swap drive location for resume purpose.

---

### Post by irumat on 2008-04-20
milktea,

Thank you!

I've been running Ubuntu on my Thinkpad X60 since 7.04. Suspend-to-ram never worked and hibernate only worked erratically. I upgraded to 7.10 as soon as it was released and neither suspend-to-ram or hibernate have worked at all since then.

This morning I read your post and so installed uswsusp and followed the instructions in your post. Suspend-to-ram AND hibernate work **every time**!

Great work.

---

### Post by davidgutu on 2008-04-20
Thanks yo!

---

