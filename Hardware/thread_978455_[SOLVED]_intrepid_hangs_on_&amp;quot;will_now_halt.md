---
title: "[SOLVED] intrepid hangs on &amp;quot;will now halt&amp;quot;"
date: 2008-11-11
forum: Hardware
---

### Post by xchronox on 2008-11-11
I updated a little while ago and have been experiencing this ever since.
I'm using a Acer Aspire 4520 and I updated from Hardy the day after Intrepid was released.
The shutdown goes fine up until it reaches the final "will now halt".
Now I know it's ok to use the power button to just shut it down from there, but I'm sure you can imagine doing that at the end of a class can be kind of a pain. 
Anyway if anyone has information on how to fix this little bug I'd greatly appreciate it.

---

### Post by iponeverything on 2008-11-11
sound like apm is not working.

boot without splash and quite to get an idea of what might be going on.

---

### Post by xchronox on 2008-11-11
Hi thanks for the quick response. I did what ya said and it turned up an error saying:
halt&#65306;unable to iterate IDE devices:no such files or directory
I'm searching around, but still not coming up with a solution. Any more ideas?

---

### Post by iponeverything on 2008-11-11
found these is launchpad:

[https://bugs.launchpad.net/ubuntu/+bug/193125](https://bugs.launchpad.net/ubuntu/+bug/193125)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/138691](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/138691)

looks like it might be the a similar issues.

---

### Post by xchronox on 2008-11-11
> **iponeverything said:**
> found these is launchpad:

[https://bugs.launchpad.net/ubuntu/+bug/193125](https://bugs.launchpad.net/ubuntu/+bug/193125)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/138691](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/138691)

looks like it might be the a similar issues.
well, I tried every possible fix in the comments of both sites... not much luck, though the IDE devices message does not appear anymore, it still won't power down completely once it reaches 'will halt now'. It seems so odd to me that the restart command powers everything down and is able to boot it up again, yet shut down cannot just do half of that...
If i can't find a fix by this weekend I'll be reformatting and installing a fresh 8.10, but for the sake of understanding more about the inner workings of linux I would like to be able to solve this.

---

### Post by iponeverything on 2008-11-17
> **xchronox said:**
> well, I tried every possible fix in the comments of both sites... not much luck, though the IDE devices message does not appear anymore, it still won't power down completely once it reaches 'will halt now'. It seems so odd to me that the restart command powers everything down and is able to boot it up again, yet shut down cannot just do half of that...
If i can't find a fix by this weekend I'll be reformatting and installing a fresh 8.10, but for the sake of understanding more about the inner workings of linux I would like to be able to solve this.

I found this, it well be what is affecting you -- I just starting seeing this on my laptop after the last update.

[http://ubuntuforums.org/showthread.php?t=965935](http://ubuntuforums.org/showthread.php?t=965935)

---

### Post by xchronox on 2008-11-17
no such luck on either solution offered in that thread... that alsa bit didnt work, neither did adding the network shutdown addition...
As much as I'm getting used to just manually shutting it down... it's still really annoying. I'm going to reformate later this week. I'll let ya know if that final solution works out.

---

### Post by icanfly0307 on 2008-11-17
Please post your /boot/grub/menu.lst. Sometimes, there are unwanted paremeters to your kernel which don't use APM and ACPI affectively.

---

### Post by xchronox on 2008-11-17
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bee98fe3-9dc3-4d68-b7c1-594b2cb68883 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=792 rootflags=data=writeback quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single rootflags=data=writeback

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bee98fe3-9dc3-4d68-b7c1-594b2cb68883 ro splash vga=792 rootflags=data=writeback quiet 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=bee98fe3-9dc3-4d68-b7c1-594b2cb68883 ro  single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Hope this helps, I'm on the verge of reformatting.

---

### Post by icanfly0307 on 2008-11-17
Hmmmmmmmmmm... I couldn't find any bad parameters in your /boot/grub/menu.lst. My suggestion is that you try a full system update. This will fix any bugs and may solve your problem. If that doesn't work, I would recommend that you DOWNGRADE from Intrepid to Hardy. Why? Simple. Hardy has a longer support term AND most important of all, IT'S MORE STABLE. I could bet you anything that your problem will be solved in Hardy. So, let me know what happens once you're done. Good Luck! :)

---

### Post by xchronox on 2008-11-17
What are you referring to when you say "full system update"
As far as I can tell, besides experimental updates as of yet unsupported, everything is up to date.

---

### Post by icanfly0307 on 2008-11-17
> **xchronox said:**
> What are you referring to when you say "full system update"
As far as I can tell, besides experimental updates as of yet unsupported, everything is up to date.

By system updates, I mean the updates that are posted by Ubuntu (kernel upgrades, bug fixes, security updates, etc.). You should have an update icon in your notification area.

PS. I reread your previous posts. The "Unable to iterate HDA..." or whatever comes up during shutdown is normal. It always happens to me and my system shuts down normally. So that's definitely not the problem. :)

---

### Post by xchronox on 2008-11-17
Cool, good to narrow it down. Well everything is up to date, no broken packages, nothing to indicate a package in limbo...
I'm getting ready to reformat, so hopefully that solves it.

---

### Post by icanfly0307 on 2008-11-18
> **xchronox said:**
> Cool, good to narrow it down. Well everything is up to date, no broken packages, nothing to indicate a package in limbo...
I'm getting ready to reformat, so hopefully that solves it.

Good Luck! By the way, are you choosing Hardy or Intrepid, again?

---

### Post by xchronox on 2008-11-18
It's gonna be Intrepid. There are a few features and updated programs I prefer from their Hardy counterparts.
I've noticed there's always some sort of bug after an dist-upgrade, I'm in the process of creating a storage utility for program files so when upgrades come around I can simply reformate and have it up and running the way I like it within 30-60 minutes.
The idea came to me because I'm currently running Ubuntu on 3 separate machines, and I wanted the desktop and documents to sync up between all of them, but I digress. 
Could be just me, but reformatting seems to be less of a hassle for my machines at this point in Ubuntu's history.

---

### Post by icanfly0307 on 2008-11-18
Yeah, I know what you mean. Ubuntu is a lot easier for me to setup, too. Well, good luck!

---

### Post by carlosap on 2008-11-27
Hi, sorry

was this solved somehow?
i have the same problem, and i did a fresh install (except for my home files) but i still cant get it shut down.

---

### Post by xchronox on 2008-11-27
Well I haven't solved it on my system, though I had an idea about downgraded the kernel... Haven't acted on that yet, but i figure it has a 70% chance of fixing the issue, but at the same time a 95% chance of creating new issues.

---

### Post by carlosap on 2008-11-27
Hey, i finally got it working now
This guy found a solution

http://74.125.77.132/search?q=cache:2JoqBIDtx70J:tomechat.cl/linux/%3Fp%3D152%26pdf_version%3D1+"Unable+to+iterate+IDE+devices"&hl=es&ct=clnk&cd=7&gl=es&client=firefox-a

---

### Post by xchronox on 2008-11-27
That didn't 100% work for me... it doesn't power down itself unless i hit a combination of any randomly selected two buttons. Which actually is an improvement as that used to restart the computer.
So gettin closer for me, but not quite solved yet.

---

### Post by xchronox on 2008-11-28
Ok, As of 10:45pm mountain time, this is solved for my Asus 4520 with Ubuntu 8.10, Kernel version: 2.6.27-9.

I followed the directions given in [this post.]("http://74.125.77.132/search?q=cache:2JoqBIDtx70J:tomechat.cl/linux/%3Fp%3D152%26pdf_version%3D1+"Unable+to+iterate+ID E+devices"&hl=es&ct=clnk&cd=7&gl=es&client=firefox-a")
To summarize that for anyone that comes upon this thread

Open /etc/init.d/halt
```
sudo gedit /etc/init.d/halt
```

look for:
```
if [ “$INIT_HALT” = “POWEROFF” ] [COLOR="Red"]&&[/COLOR] [ -x /etc/init.d/ups-monitor ]
then
/etc/init.d/ups-monitor poweroff
fi
```

Replace [COLOR="Red"]&&[/COLOR] with [COLOR="Red"]-a[/COLOR] so it looks like this:

```
if [ “$INIT_HALT” = “POWEROFF” ] [COLOR="Red"]-a[/COLOR] [ -x /etc/init.d/ups-monitor ]
then
/etc/init.d/ups-monitor poweroff
fi
```

Save/quit
Open menu.lst
```
sudo gedit /boot/grub/menu.lst
```

find the line I've highlighted in red:
```
title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid 70a563a5-46dd-4bed-92c8-598c40777ac2
[COLOR="Red"]kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=70a563a5-46dd-4bed-92c8-598c40777ac2 ro quiet splash[/COLOR]
initrd /boot/initrd.img-2.6.27-7-generic
quiet
```

Add this to the end of that line:
```
acpi=noirq pci=assign-busses reboot=cold
```

Save/quit

Now the first time I did this it didn't work, I found that in my BIOS settings I had to specify my SATA mode as [COLOR="Red"]ACPI[/COLOR] before it would shut down by itself.

Thank you to everyone in this thread and al the others who provided resources that eventually came to solve this problem.

---

### Post by prashant32 on 2008-11-28
that was a nice post. I enjoyed reading it. 
thanks

---

### Post by steelmachine on 2009-08-24
> 
Open menu.lst
```
sudo gedit /boot/grub/menu.lst
```

find the line I've highlighted in red:
```
title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid 70a563a5-46dd-4bed-92c8-598c40777ac2
[COLOR="Red"]kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=70a563a5-46dd-4bed-92c8-598c40777ac2 ro quiet splash[/COLOR]
initrd /boot/initrd.img-2.6.27-7-generic
quiet
```

Add this to the end of that line:
```
acpi=noirq pci=assign-busses reboot=cold
```

Save/quit



In Ubuntu 9.04 there are two similar lines, but i changed the first one and my Acer 4520 now shuts down (some flicker on the screen like before, but after some seconds it shuts down).

---

