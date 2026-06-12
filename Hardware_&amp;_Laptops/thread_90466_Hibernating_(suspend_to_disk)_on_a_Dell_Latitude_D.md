---
title: "Hibernating (suspend to disk) on a Dell Latitude D610"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by ispiked on 2005-11-15
So, tonight I figured I'd try to get hibernate working. Here I am 5 hours later and still not hibernating. 

I have setup everything that I am supposed to (I think). Added the resume=<swap partition> line to /boot/grub/menu.lst and all. So I choose hibernate from the Logout options menu and all goes well. I turn it back on and it seems to be working OK, then it ends with the following message:
```

resume= option should be used to set suspend device
swsusp: Need to copy 13477 pages

```
After that nothing happens; I turn it off and on and it loads up normally. A couple of things... swap is one of the last things mounted in fstab (don't know if this would make a difference or not). The function that prints out that error message ([http://www.kernelhq.com/browse-view.py?fv_nr=232276](http://www.kernelhq.com/browse-view.py?fv_nr=232276) line 175) is commented saying "/* This is called before saving image */", so I don't know why this would appear when *resuming* from suspend. Also, I am using an SATA harddrive, so it might be related to that.

---

### Post by computerbs on 2005-11-23
I am experiencing exactly the same errors as you.  Have you made any progress?

Thanks!

---

### Post by ranf on 2005-11-23
[QUOTE=ispiked]So, tonight I figured I'd try to get hibarnate working. Here I am 5 hours later and still not hibernating. 

I have setup everything that I am supposed to (I think). Added the resume=<swap partition> line to /boot/grub/menu.lst and all. [/QUOTE]
Please post your whole menu.lst and the output of `sudo fdisk -l'.

---

### Post by computerbs on 2005-11-23
Here is the fdisk output:


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6996    56195338+  83  Linux
/dev/sda2            6997        7296     2409750    5  Extended
/dev/sda5            6997        7296     2409718+  82  Linux swap / Solaris

And here is the menu.lst:

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by ranf on 2005-11-23
[QUOTE=computerbs]Here is the fdisk output:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6996    56195338+  83  Linux
/dev/sda2            6997        7296     2409750    5  Extended
/dev/sda5            6997        7296     2409718+  82  Linux swap / Solaris

And here is the menu.lst:

<snipped>
# kopt=root=/dev/sda1 ro
[/QUOTE]

This kopt line should look like this for your setup:
```
# kopt=root=/dev/sda1 ro resume=/dev/sda5
```

It is a good idea to then run this (I am not sure if it is necessary. But it won't hurt anyway):
```
sudo update-grub
```

---

### Post by computerbs on 2005-11-23
[QUOTE=ranf]This kopt line should look like this for your setup:
```
# kopt=root=/dev/sda1 ro resume=/dev/sda5
```

It is a good idea to then run this (I am not sure if it is necessary. But it won't hurt anyway):
```
sudo update-grub
```[/QUOTE]


I tried this.  Alas, to no avail :-(  Do you have a Dell Latitude D610?

---

### Post by ranf on 2005-11-23
[QUOTE=computerbs]I tried this.  Alas, to no avail :-(  Do you have a Dell Latitude D610?[/QUOTE]
Please be more specific. What messages do you see on screen?

No I don't have a Dell. Did you search the wiki for "D610" or "Latitude"?

---

### Post by computerbs on 2005-11-23
[QUOTE=ranf]Please be more specific. What messages do you see on screen?

No I don't have a Dell. Did you search the wiki for "D610" or "Latitude"?[/QUOTE]


I have the same error message as the original poster.  When I hibernate, it seems to suspend to disk OK.  I get the error message when it tries to resume.

From the wiki pages, it appears that hibernate either "just works" or it "doesn't."  No real fixes are discussed.  

Very frustrating...

---

### Post by ranf on 2005-11-23
[QUOTE=computerbs]
From the wiki pages, it appears that hibernate either "just works" or it "doesn't."  No real fixes are discussed.  

Very frustrating...[/QUOTE]
Yes I understand that.
Let's look at what the kernel says about ACPI support:
```
dmesg | grep "ACPI: ("
```

---

### Post by computerbs on 2005-11-23
[QUOTE=ranf]Yes I understand that.
Let's look at what the kernel says about ACPI support:
```
dmesg | grep "ACPI: ("
```[/QUOTE]

First of all, thanks for taking the time to look at this!


I didn't get any results with that grep, but if I do a more general grep, I get:

```

cedelis@ubuntu:~$ dmesg | grep -i "ACPI: ("
cedelis@ubuntu:~$ dmesg | grep -i acpi
[4294673.081000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[4294673.168000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
[4294673.227000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294675.503000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[4294675.503000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294675.506000] ACPI: Thermal Zone [THM] (53 C)
[4294690.292000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294690.292000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294690.629000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
[4294692.092000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294692.413000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294701.488000] ACPI: AC Adapter [AC] (on-line)
[4294701.803000] ACPI: Battery Slot [BAT0] (battery present)
[4294701.803000] ACPI: Battery Slot [BAT1] (battery absent)
[4294701.817000] ACPI: Lid Switch [LID]
[4294701.817000] ACPI: Power Button (CM) [PBTN]
[4294701.817000] ACPI: Sleep Button (CM) [SBTN]
[4294701.893000] ibm_acpi: ec object not found
[4294701.979000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294701.979000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294701.979000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[4294706.366000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[4299535.575000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[4299535.640000] ACPI: PCI interrupt for device 0000:03:03.0 disabled
[4299535.758000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[4299535.864000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[4299535.964000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[4299536.051000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[4299536.117000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[4299537.478000] ACPI: PCI interrupt for device 0000:03:01.0 disabled
[4299537.478000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[4299537.489000] ACPI: PCI interrupt for device 0000:00:1e.2 disabled
[4300715.505000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[4300715.506000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[4300715.508000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
[4300716.727000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[4300716.728000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[4300719.267000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4300719.321000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[4300719.908000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[4300719.983000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[4300720.052000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4300720.121000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[4300720.253000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
[4300720.419000] ACPI: AC Adapter [AC] (off-line)
[4300720.742000] ACPI: Battery Slot [BAT0] (battery present)
[4300720.742000] ACPI: Battery Slot [BAT1] (battery absent)
[4300722.289000] ACPI: Lid Switch [LID]
[4300722.289000] ACPI: Power Button (CM) [PBTN]
[4300722.289000] ACPI: Sleep Button (CM) [SBTN]
[4300722.355000] ACPI: Thermal Zone [THM] (37 C)

```

---

### Post by ranf on 2005-11-23
[QUOTE=computerbs]
I didn't get any results with that grep,
[/QUOTE]
Interesting.
I get a line saying:
```
[4294669.571000] ACPI: (supports S0 S3 S4 S5)
```
The different S thingies tell if sleep (suspend to RAM) and hibernate are supported.

I admit I'm running out if ideas.

---

### Post by computerbs on 2005-11-23
[QUOTE=ranf]Interesting.
I get a line saying:
```
[4294669.571000] ACPI: (supports S0 S3 S4 S5)
```
The different S thingies tell if sleep (suspend to RAM) and hibernate are supported.

I admit I'm running out if ideas.[/QUOTE]


I think dmesg chopped off the important stuff.  When I grep'd /var/log/messages, I found this:

```
Nov 23 11:18:16 localhost kernel: [4294668.926000] ACPI: (supports S0 S3 S4 S4bios S5)
```

The only difference is that mine says S4**bios**

---

### Post by ispiked on 2005-11-23
I did a little more research into this after I posted, and what I think (and am told) is happening is that it's freezing when it tries to throw the image back off the disk and back into the memory. The reason you (and me) are seeing the message about "swsusp: Need to copy 13477 pages" is because it's restoring what just happened before it hibernated. 
> 
[2005-11-15 20:02:50]<ispiked> you ever seen that error before?
[2005-11-15 20:03:00]<ispiked> "resume= option should be used to set suspend device"
[2005-11-15 20:03:05]<ispiked> like I pointed out, it makes no sense.
[2005-11-15 20:03:16]<vlad> well, it does
[2005-11-15 20:03:22]<ispiked> I'm resuming, though.
[2005-11-15 20:03:27]<vlad> that's jsut telling you that the resume= kernel option should point to whatever the device is being suspended to
[2005-11-15 20:03:30]<vlad> yes
[2005-11-15 20:03:37]<vlad> that message was printed before the suspend took place
[2005-11-15 20:03:43]<vlad> now that the resume took place, you see the same message again
[2005-11-15 20:03:46]<vlad> because the memory image was restored
[2005-11-15 20:03:47]<ispiked> but this is after it appears to "resume".
[2005-11-15 20:03:53]<vlad> 20:03 <@vlad> because the memory image was restored
[2005-11-15 20:04:08]<vlad> the *entire image of memory* was restored
[2005-11-15 20:04:12]<vlad> including everything that was in the console
[2005-11-15 20:04:15]<vlad> and everything that was in the framebuffers
[2005-11-15 20:04:17]<ispiked> vlad: ah!
[2005-11-15 20:04:24]<vlad> including messages that were printed before

I'm guessing we both have an SATA hard drive (I know I do), and right now, SATA suspend resume in the default kernel doesn't exist. There is a patch for it right now (which Ubuntu does include in their kernel), but it only seems to work for some people. So keep an eye out for new patches for it, and also keep an eye out on vlad's [blog post](http://blog.vlad1.com/archives/2005/11/01/75/) since he's got a bounty out for whoever gets suspend working on his laptop.

I went ahead and attached menu.lst and the output of `fdisk -l ' just incase I was overlooking something. I have the same line in my dmesg as computerbs does.

---

### Post by computerbs on 2005-11-23
[QUOTE=ispiked]I did a little more research into this after I posted, and what I think (and am told) is happening is that it's freezing when it tries to throw the image back off the disk and back into the memory. The reason you (and me) are seeing the message about "swsusp: Need to copy 13477 pages" is because it's restoring what just happened before it hibernated. 


I'm guessing we both have an SATA hard drive (I know I do), and right now, SATA suspend resume in the default kernel doesn't exist. There is a patch for it right now (which Ubuntu does include in their kernel), but it only seems to work for some people. So keep an eye out for new patches for it, and also keep an eye out on vlad's [blog post](http://blog.vlad1.com/archives/2005/11/01/75/) since he's got a bounty out for whoever gets suspend working on his laptop.

I went ahead and attached menu.lst and the output of `fdisk -l ' just incase I was overlooking something. I have the same line in my dmesg as computerbs does.[/QUOTE]



My eyes are peeled!  Can't wait for this to get fixed some day... got my fingers crossed...

---

### Post by ispiked on 2005-11-23
At the advice of mjg59, I removed "splash" from the kernel flags line in menu.lst and now hibernate seems to work flawlessly. :D

---

### Post by computerbs on 2005-11-24
[QUOTE=ispiked]At the advice of mjg59, I removed "splash" from the kernel flags line in menu.lst and now hibernate seems to work flawlessly. :D[/QUOTE]


Congrats!  Good news.  Unfortunately, it didn't work for me :(  I just get a blank screen now, which seems to be progress, but not success.  I can switch consoles and such, but my X windows session is just black.  Which kernel are you using?  Can you think of anything else I might try?  (grasping at straws)

---

### Post by computerbs on 2005-11-24
[QUOTE=computerbs]Congrats!  Good news.  Unfortunately, it didn't work for me :(  I just get a blank screen now, which seems to be progress, but not success.  I can switch consoles and such, but my X windows session is just black.  Which kernel are you using?  Can you think of anything else I might try?  (grasping at straws)[/QUOTE]

sorry for the dumb question.  Your menu.lst shows me what kernel version you are using.  I'm using the 2.6.12-10-686.  I wonder if that could be it...

---

### Post by computerbs on 2005-11-24
I'm getting CLOSER to a solution.

I commented out my 915resolution init.d script and hibernation now works!  I wonder if I need to tell ACPI subsystem about 915resolution somehow so that hibernation will work *with* it.  1400x1050 rez is *so* much better-looking that 1280x1024 (this is fuzzy).  Any idears?

---

### Post by computerbs on 2005-11-24
[QUOTE=computerbs]I'm getting CLOSER to a solution.

I commented out my 915resolution init.d script and hibernation now works!  I wonder if I need to tell ACPI subsystem about 915resolution somehow so that hibernation will work *with* it.  1400x1050 rez is *so* much better-looking that 1280x1024 (this is fuzzy).  Any idears?[/QUOTE]


To answer my own question:

I needed to call my 915resolution script upon resuming.  I noticed the older 815resolution script in /etc/acpi/resume.d:

Filename: 49-855-resolution-set.sh
```

#!/bin/bash

if [ -x /usr/sbin/855resolution ]; then
    . /etc/default/855resolution
    if [ "$MODE" != "" ] && [ "$XRESO" != "" ] && [ "$YRESO" != "" ]; then
        /etc/init.d/855resolution start;
    fi
fi

```

All I had to do was rename 855resolution to 915resolution.  It. now. WORKS!

Thanks for all of your help, guys!  Happy Thanksgiving!!!

---

### Post by ranf on 2005-11-24
Nice to see that you both got it working.

---

### Post by lanceh on 2005-12-07
> **computerbs]To answer my own question:

I needed to call my 915resolution script upon resuming.  I noticed the older 815resolution script in /etc/acpi/resume.d:

Filename: 49-855-resolution-set.sh
```

#!/bin/bash

if [ -x /usr/sbin/855resolution ] said:**
>  && [ "$XRESO" != "" ] && [ "$YRESO" != "" ]; then
        /etc/init.d/855resolution start;
    fi
fi

```

All I had to do was rename 855resolution to 915resolution.  It. now. WORKS!

Thanks for all of your help, guys!  Happy Thanksgiving!!!

i also have the 915resolution fix applied and tried using the above fix for hibernation. hibernation does now work but when my laptop comes back from hibernation it is in 1280x1024. so the 915resolution fix is not being applied.

what i've noticed is that i don't have /etc/default/915resolution or /etc/init.d/915resolution even though i have applied the fix and when i perform a full boot my screen is displaying at 1400x1050.

i used this post to apply the 915resolution fix. [http://www.ubuntuforums.org/showthread.php?t=79953](http://www.ubuntuforums.org/showthread.php?t=79953)

any thoughts? i'm very new to linux and this forum has been amazing. if it were not for the people here i probably would have given up on linux by now.

---

### Post by computerbs on 2005-12-12
[QUOTE=lanceh]i also have the 915resolution fix applied and tried using the above fix for hibernation. hibernation does now work but when my laptop comes back from hibernation it is in 1280x1024. so the 915resolution fix is not being applied.

what i've noticed is that i don't have /etc/default/915resolution or /etc/init.d/915resolution even though i have applied the fix and when i perform a full boot my screen is displaying at 1400x1050.

i used this post to apply the 915resolution fix. [http://www.ubuntuforums.org/showthread.php?t=79953](http://www.ubuntuforums.org/showthread.php?t=79953)

any thoughts? i'm very new to linux and this forum has been amazing. if it were not for the people here i probably would have given up on linux by now.[/QUOTE]


All I can think of, is that maybe the 915resolution script is being called too late?  I have my script run before gdm, e.g.:

/etc/rc3.d/S12_915resolution  /etc/rc3.d/S13gdm

("S12" comes before "S13").

Just a thought...

---

### Post by tifay on 2006-02-26
I find this site by google:
[http://rdo.homelinux.org/ubuntu-linux-on-a-dell-latitude-d610/](http://rdo.homelinux.org/ubuntu-linux-on-a-dell-latitude-d610/)

There is only one thing to do for 'suspend to ram'. I tried it & now works both: hibernate & suspend.

My settings & changes:
**1. vi /etc/default/acpi-support**
	add '915reslolution' to STOP_SERVICES
**2. vi /etc/acpi/resume.d/49-855-resolution-set.sh**
	change all '855resolution' to '915resolution'
**3. 915 script is on 12. place in rc2.d by:**
        update-rc.d 915resolution defaults 12
**4. no changes in grub/menu.lst**

---

### Post by tsr on 2006-03-12
Edit: Nope, works sometimes, but mostly not!

I'll second the above aproach somewhat, with the following changes:

- I'm using the 855resolution thingy
- I'm not using a Dell, but at least an Intel chipset
- I did keep the kopt=/dev/hda1 ro resume=/dev/hda5 line in the menu.lst file (mostly because I don't feel like trying without it :)

This definetly is making my ubuntu experience better!

---

