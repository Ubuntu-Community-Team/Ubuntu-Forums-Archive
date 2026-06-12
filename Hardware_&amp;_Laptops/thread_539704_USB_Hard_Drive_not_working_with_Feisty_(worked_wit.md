---
title: "USB Hard Drive not working with Feisty (worked with previous versions of Xubuntu)"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by KaylNaris on 2007-08-31
Hello,

for this is my first post in this forums, I would like to say 'Hello' to everybody :-)

I have the following problem: 
Since I upgrade to Xubuntu my external hard drive is no longer working. 

The following happens, when I plug the hard drive into the USB-Port:
You can hear the hard drive spin up and it blinks a few times, but after a few seconds the hard drive ist shut down (no more spinning sounds, no more blinking). Afterward, it's not being mounted automatically and cannot be mountet manually. However, a file /dev/sdb is created. 

After removing the USB-plug and putting it back in, nothing happens (the hard drive doesn't spin up). The USB port itselt doesn't work until I reboot the computer. 

I've added the following attachments: 
 - output from /var/log/message while plugging in the hard drive
 - output from /var/log/kern

The following line from /var/log/kern caught my interest: 
```
Aug 22 20:34:09 kayl-laptop kernel: [ 2185.288000] Oops: 0000 [#1]
```
Does this mean, the kernel crashes when plugging in the hard drive? 

My system is a Toshiba Satellite 2410 Laptop. The USB-Hard-Drive is connected via a USB-2.0-PC-Card, because the Laptop doesn't have its own USB-2.0-Ports. 

The hard drive worked finde in previous versions ob Xubuntu, the problem occures since I upgrade to Feisty. Under Windows XP (installed on the same machine as dual boot) the hard drive also works fine. 

uname -a:
```
Linux kayl-laptop 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686 GNU/Linux
```

Does anybody have a solution for this problem? Any help would be greatly appreciated :-)
I can provide more data for the problem, if needed. Just give me a message. 

Thanks in advance and greetings from the Lake of Constance,

Achim

P.S.: Sorry for my bad English, it's been a while since the last time I actively used this language :-)

---

### Post by jnorthr on 2007-08-31
Welcome aboard !:popcorn:

Hope we can help you with your problem. 

If you have ANY usb ports on your system you can just directly attach the usb drive to that port, even if one device is usb 2.0 and the other device is usb1.1 or usb1.0. They will operate together aber mer langsam. If you avoid using the usb-pc adapter it may help to get it working. This is the plan i followed on mein machine und now de usb external drive verks. 8-)

Feisty versions of ubuntu may not have tested this combination of hardware together before. It's impossible to test all the possible combinations so by removing some piecs of hardware you may still get it working again. Also remember that kubuntu and ubuntu are NOT the same thing, they have the same core but they may have differents versions of components within them. Can you go back to try kubuntu again to confirm it works ?

---

### Post by vpjr on 2007-09-01
hi kaylnarris and everyone too.

i'm experiencing a problem with my usb flash drive with the same symptoms.  i've tried inserting the flashdrive to all available ports but the same thing happens - the LED of the flashdrive turns ON for a moment and then goes out.  The flashdrive and ports were working fine before the latest upgrade of the linux kernel.  i'm using ubuntu 6.10 btw.

Below is the part of the output of dmesg and i've colored-RED what i believe is the error messages directly related with the usb flashdrive.

kaylnarris, please post your dmesg too.

> [17179569.184000] Linux version 2.6.17-12-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Wed Aug 29 20:08:20 UTC 2007 (Ubuntu 2.6.17-12.40-generic)

> 
[COLOR="Red"][17179579.056000] usb 4-8: new high speed USB device using ehci_hcd and address 3
[17179579.168000] usb 4-8: device descriptor read/64, error -32
[17179579.384000] usb 4-8: device descriptor read/64, error -32
[17179579.600000] usb 4-8: new high speed USB device using ehci_hcd and address 4
[17179579.712000] usb 4-8: device descriptor read/64, error -32
[17179579.928000] usb 4-8: device descriptor read/64, error -32
[17179580.144000] usb 4-8: new high speed USB device using ehci_hcd and address 5
[17179580.552000] usb 4-8: device not accepting address 5, error -32
[17179580.664000] usb 4-8: new high speed USB device using ehci_hcd and address 6
[17179581.072000] usb 4-8: device not accepting address 6, error -32
[17179581.072000] ohci_hcd 0000:00:03.0: wakeup
[17179581.456000] usb 1-1: new full speed USB device using ohci_hcd and address 3
[17179581.680000] usb 1-1: configuration #1 chosen from 1 choice
[/COLOR]


thanks.

ven

---

### Post by vpjr on 2007-09-02
hi,

just a progress report on my particular problem: 

1. chkdsk (in Windows XP) the usb drive: didn't solve the problem.

2. went back to kernel version 2.6.17-10-generic: didn't solve the problem

3. tried the usb in a friend's kubuntu setup: the usb drive worked.

[COLOR="Red"]4. went to my BIOS settings and disabled the USB 2.0 setting and just used the USB legacy: the usb flashdrive finally worked.[/COLOR]

the following is the dmesg | grep usb output:

> [17179579.288000] usbcore: registered new driver usbfs
[17179579.288000] usbcore: registered new driver hub
[17179579.392000] usb usb1: configuration #1 chosen from 1 choice
[17179579.580000] usb usb2: configuration #1 chosen from 1 choice
[17179579.768000] usb usb3: configuration #1 chosen from 1 choice
[17179579.808000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[17179579.872000] usb usb4: configuration #1 chosen from 1 choice
[17179580.556000] usb 1-1: new full speed USB device using ohci_hcd and address 3
[17179580.780000] usb 1-1: configuration #1 chosen from 1 choice
[17179629.484000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5511
[17179629.484000] usbcore: registered new driver usblp
[17179629.484000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179701.684000] usb 4-8: new high speed USB device using ehci_hcd and address 3
[17179701.796000] usb 4-8: device descriptor read/64, error -32
[17179702.012000] usb 4-8: device descriptor read/64, error -32
[17179702.228000] usb 4-8: new high speed USB device using ehci_hcd and address 4
[17179702.340000] usb 4-8: device descriptor read/64, error -32
[17179702.556000] usb 4-8: device descriptor read/64, error -32
[17179702.772000] usb 4-8: new high speed USB device using ehci_hcd and address 5
[17179703.180000] usb 4-8: device not accepting address 5, error -32
[17179703.292000] usb 4-8: new high speed USB device using ehci_hcd and address 6
[17179703.700000] usb 4-8: device not accepting address 6, error -32
[17180591.608000] usblp 1-1:1.1: no suspend for driver usblp?
[17187508.180000] usb usb4: root hub lost power or was reset
[17187509.096000] Restarting tasks...<6>usb 1-1: USB disconnect, address 3
[17187509.096000] drivers/usb/class/usblp.c: usblp0: removed
[17187509.272000] usb 1-1: new full speed USB device using ohci_hcd and address 4
[17187509.496000] usb 1-1: configuration #1 chosen from 1 choice
[17187509.504000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x5511
[17187509.680000] usb 2-3: new full speed USB device using ohci_hcd and address 2
[17187509.880000] usb 2-3: not running at top speed; connect to a high speed hub
[17187509.896000] usb 2-3: configuration #1 chosen from 1 choice
[17187513.296000] usbcore: registered new driver libusual
[17187513.856000] usb-storage: device found at 2
[17187513.856000] usb-storage: waiting for device to settle before scanning
[17187513.856000] usbcore: registered new driver usb-storage
[17187518.856000] usb-storage: device scan complete

does anybody have an idea why this work?

regards,

ven

---

### Post by KaylNaris on 2007-09-02
Hello and thanks for your reply!

> **jnorthr said:**
> If you have ANY usb ports on your system you can just directly attach the usb drive to that port, even if one device is usb 2.0 and the other device is usb1.1 or usb1.0. They will operate together aber mer langsam. If you avoid using the usb-pc adapter it may help to get it working. This is the plan i followed on mein machine und now de usb external drive verks. 8-) 

Plugging the hard drive into one of the laptop's own USB-ports unfortunatelly doesn't solve the problem, the same symptoms as described in my first post occur, too. 

> **jnorthr said:**
> Feisty versions of ubuntu may not have tested this combination of hardware together before. It's impossible to test all the possible combinations so by removing some piecs of hardware you may still get it working again. Also remember that kubuntu and ubuntu are NOT the same thing, they have the same core but they may have differents versions of components within them. Can you go back to try kubuntu again to confirm it works ?

I already tried LiveCDs of Ubuntu and Xubuntu, the problem occured on both systems. At the moment I'm downloading an ISO image of Kubuntu. Later this evening I'm going to report if it worked. 

Greetings,

Achim

---

### Post by KaylNaris on 2007-09-02
Hello again,

now I've tried booting from the Kubuntu live CD. The same problem occurs, the hard drive spins up and stops after a few seconds. 

After I switched back to my installed Xubuntu system, I've noticed that, when a terminal is open, something that appears to be a stack trace is printed to stderr a few seconds after the usb hard drive is plugged in (see attachment 'syserr'). 

I've also attached the content of /var/log/dmesg. I booted the system without the hard drive plugged in, then called 
```
tail -F /var/log/dmesg
```
Then I plugged the USB hard drive to my laptop, but there was nothing added to dmesg. 

What else can I do to fix this problem? Any help is greatly appreciated :-)

Greetings and thanks in advance,

Achim

---

### Post by rickyrockrat on 2007-09-04
I happen to be developing some USB drivers, and those errors you are seeing are either the device (not likely, since it works elsewhere), your cable (since it works at low speed), or the USB port on the computer you are using has issues.  Hi-speed USB is 480 M/bits per second and it doesn't take much to mess it up.

Error -110 is a timeout error, if I remember correctly, and it means the device did not respond to a comman from the host (i.e. the PC).

It looks like you disconnected the cable, THEN had the kernel oops.  I've had this happen when I had a bad entry in my hotplug scripts...

1) Try  a different cable.
2) is the one you are using kinked?  
3) Does it say 2.0 or hi-speed on it? 
4) Try this: remove all USB devices from your PC. Do a fresh boot (complete powerof). Then plug the HDD in and post the output of dmesg.

5) If you can boot to different versions of the kernel to see if perhaps it IS a linux driver issue.

Your last dmesg output looks like it was truncated.

---

### Post by rickyrockrat on 2007-09-04
Just to clarify, you have a dual-boot machine, and when you boot into Windows, it works, but when you boot into Ubuntu (without touching anything) it doesn't?  Is the drive  formatted NTFS if so do you have ntfs drivers installed?  I'm getting confused as to who did what. Sorry 'bout that.

---

### Post by KaylNaris on 2007-09-05
Hello,

Thanks for your messages! I'll try to answer what I can: 

> Just to clarify, you have a dual-boot machine, and when you boot into Windows, it works, but when you boot into Ubuntu (without touching anything) it doesn't? 

Exactly as You described. It also worked fine in Dapper and Edgy and still works when I boot from a Edgy livecd. 

> Is the drive formatted NTFS if so do you have ntfs drivers installed? I'm getting confused as to who did what. Sorry 'bout that.

The drive ist formatted FAT32 because it seemed to be the simplest way to share files between Linux and Windows XP. 

> It looks like you disconnected the cable, THEN had the kernel oops. I've had this happen when I had a bad entry in my hotplug scripts...

The drive was still plugged in when the kernel oops happened. I did the following:
[LIST]
[*]Boot the machine
[*]Logged in and started Xfce
[*]Opened a terminal-window in Xfce
[*]Plugged in the usb drive
[*]The USB hard drive spins up (its LED flashes, makes sounds)
[*]A few seconds later the USB hard drive stops making sounds and the LED stops flashing, it just shuts down. 
[*]Kernel Oops is printed to the terminal window
[/LIST]


> 1) Try a different cable.

Okay, no problem: I've got two more USB cables, which i tried: the one connected to my scanner and the one connected to my printer. Both cables made no difference, everytime I plugged the drive in, a kernel oops was printed to the console. 

> 2) is the one you are using kinked? 

Sorry, I don't know what 'kinked' means. There is a thick cylinder-box which separates the cable into two parts, if that is what you mean. 

> 3) Does it say 2.0 or hi-speed on it? 

There is just the USB-Logo ([http://de.wikipedia.org/wiki/Bild:Usb-svg.svg](http://de.wikipedia.org/wiki/Bild:Usb-svg.svg)) printed on one plug of the cable, but no additional text. 

> 4) Try this: remove all USB devices from your PC. Do a fresh boot (complete powerof). Then plug the HDD in and post the output of dmesg.

Okay, I've done that and attached the output from dmesg to this post. 

> 5) If you can boot to different versions of the kernel to see if perhaps it IS a linux driver issue.

The following kernel versions are installed on my machine:
[LIST]
[*]2.6.20-15
[*]2.6.20-16
[/LIST]
The drive doesn't work with both kernels. 

> Your last dmesg output looks like it was truncated.

That's strange, I didn't edit the file, I just uploaded a copy of /var/log/dmesg. I hope it worked this time. 

I hope some of this information is useful :-) Thanks a lot for taking your time :-)

Greetings,
Achim

---

### Post by TheWebMachine on 2007-09-06
I am having the same problem with USB Harddrives and USB Flash devices.  My dmesg and errors are virtually identical (I will finish gathering them and then post as it's own post.) and this is happening on my IBM Thinkpad T40 while using both a Maxtor One-Touch 200GB USB external and PNY 1GB USB Flash Drive.  It keeps giving a port and/or hub reset error or it will say that the port is not responding.  Mind you, I am seriously doubting a hardware problem as this laptop runs Windoze just fine and reads all devices without error (same cables and drives work on my desktop Windoze PC. The BIOS is even the latest revision and underwent no upgrade recently. I would like to also note that I didn't begin experiencing my problem until after my second or third batch of updates from the default live CD (Fiesty 7.04 Standard Live CD - 32bit x86).  The original Live CD appears to work just fine with the USB devices.  It appears that an upgraded driver somewhere is the likely culprit.  It is the only thing that has changed on this system since it worked.  My RNDIS USB device works fine (HTC S620 - T-Mobile Dash running WM6) but the drives no longer work.

I'm at a loss at this point...no other forum on the net have proven fruitful in this matter.  Every log I've read shows the same messages (mine are no different)...pointing to an "apparent" hardware problem.  The only way the Kernel would know that a device wasn't working is if a driver (or module) told it so.  

Perhaps someone should begin tracing every driver that has been released as an upgrade since the Live CD release and pick out the ones that could be to blame.  

I'm no programmer, but I am a CTO and know enough to get the most out of my build.  This has simply escaped me for far too long.

I hope someone can track this down and I hope I have helped in some way.  This is just crazy. :confused: lol

---

### Post by TheWebMachine on 2007-09-06
Here is the dmesg output...broken down into 3 parts to allow upload.  Everything is in there.

Thanks in advance for everyone's help.

---

### Post by KaylNaris on 2007-09-06
Hello again,

I did a little testing, this is the result:

The problem also seems to occur on Xubuntu Gutsy Tribe 5, at least when booting from the live cd.  

Additionally, I experimented a little with some BIOS options, I activated "USB Legacy mode". This doesn't change anything when the USB drive ist connected via the USB2.0-pccard. 
But when I connect the drive to the built-in usb-1.0-port of my laptop, it behaves differently: 

When the drive is plugged in after the system booted up and after logging in to Xfce, the same error as described in my first post occurs. 

But when the drive is plugged in before the power switch is turned on, the drive spins up ob boot and keeps running. When I then log in to Xfce, an error message appears, stating that an internal error has occured (see attachment, "Interer Fehler" is German for "internal error", "Schließen" means "close"). I've also attached the according dmesg-output. 
Manually mounting the drive now works: 

```
kayl@kayl-laptop:~$ sudo mount /dev/sdb1 /media/CLASSIC\ HD/
kayl@kayl-laptop:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-386/volatile type tmpfs (rw)
(rw,noexec,nosuid,nodev,utf8,uid=1000,gid=1000)
/dev/mapper/sda1 on /mnt/windows_c type ntfs (ro,noexec,nosuid,nodev,nls=utf8,uid=1000,gid=1000)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/CLASSIC HD type vfat (rw)

```
(the last entry belongs to the usb disk, "CLASSIC HD")

so at least I now can access the drive. :)
The disadvantage is: I have to manually mount all other drives like CDs, because automounting doesn't work any more. :(

But at least it's a little progress. 

I hope I could provide some useful data! Is there anything else I can try to get the drive working without sacrificing automounting?

Achim

---

### Post by TheWebMachine on 2007-09-07
I think I may have discovered the problem, or the major aspect of it, at least.

Last night I was playing around with various modules and decided to temporarily remove the ehci_hcd module:

> sudo rmmod ehci_hcd

To my surprise, my USB hard drive mounted with no problem.  I then tested my other USB HDD and my USB Flash Drive.  All are working without issue and everything else seems to be working fine as well.  Granted, I don't use the Hibernate or Suspend features due to an issue regarding my sound driver after being in such states, so I can't say if either of those two functions have been affected.  I will continue testing those items tonight and post my findings.  I understand that by removing ehci_hcd that uhci_hcd will only provide me with USB1.2 compatibility, but at this point, I need to use my external drives moreso than I need USB2.0.

From what I can tell, it appears that ehci_hcd was repeatedly suspending/resuming the power to the USB bus. uhci_hcd works without issue.

Perhaps ehci_hcd is reading a false suspend signal when a device is initialized and get's tricked into thinking that ACPI is requesting a suspend?  I've been trying to dig through change logs but I'm no programmer so I haven't come up with an answer to the question, "Which was changed first, the Chicken (ehci_hcd) or the Egg (ACPI)?"  (Pardon the poor American humor.)

Oh, I forgot to "introduce" myself:

Linux mrebar-laptop 2.6.20-16-generic #2 SMP SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

---

### Post by jnorthr on 2007-09-08
Interesting link on this problem : [http://lists.debian.org/debian-amd64/2004/12/msg00139.html](http://lists.debian.org/debian-amd64/2004/12/msg00139.html)
or [http://lists.debian.org/debian-amd64/2004/12/msg00138.html](http://lists.debian.org/debian-amd64/2004/12/msg00138.html)

---

### Post by KaylNaris on 2007-09-26
Hello,

sorry for the delay! I've been quite busy for the last few weeks ... :-(

> Interesting link on this problem : [http://lists.debian.org/debian-amd64.../msg00139.html](http://lists.debian.org/debian-amd64.../msg00139.html)
or [http://lists.debian.org/debian-amd64.../msg00138.html](http://lists.debian.org/debian-amd64.../msg00138.html)

Thanks for these links, they're quite interesting. But unfortunately, the solutions provided there don't work for me: 
Switching to a different cable doens't work. The hard drive also works fine on the same machine in Windows XP (dual-boot), so I think a hardware defect can be excluded. 
I also tried to remove ehci_hcd, but it didn't work. The same problem as described in my first post occurs. 

In the meantime, I tried the following boot options:
 - irqpoll 
 - acpi=noirq

I also tried reinstalling the following packages: 
```
sudo aptitude reinstall hal hal-device-manager gnome-volume-manager 
```

Neither of these worked, the symptoms were the same as always. 

I've found two Bugs on Launchpad which seem to refer to similar problems:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/97510]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/97510")
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/83984]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/83984")

Is there anything else I can try? Thanks again for your time, I hope we can solve this problem :-)

Greetings,

Achim

---

