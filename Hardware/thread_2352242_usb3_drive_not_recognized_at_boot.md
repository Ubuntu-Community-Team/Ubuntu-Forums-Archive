---
title: "usb3 drive not recognized at boot??"
date: 2017-02-10
forum: Hardware
---

### Post by mux23 on 2017-02-10
heya,

long-time Linux user, running into an odd new problem. got a little 12v Fit-PC3 computer here, with an 8tb "Seagate Backup Plus Hub" attached to a USB3 port.

when I cold-boot the computer with the drive attached, the BIOS splash screen shows the USB drive as having been detected (calls it out by name, even)... but Ubuntu cannot see it. I've tried inserting the usb_storage module manually, no change. I cannot get the computer to recognize the drive no matter what I do. 'lsusb' does not show the device. 'dmesg' does not mention it being detected. 

when I cold-boot the computer *without* the drive attached, then attach the drive later after the machine is booted, the drive works just fine - shows up as /dev/sdb, gets mounted, etc.

how could this be?! nothing in dmesg, no errors in the logs that I can find. most of my Linux experience is big servers, I don't deal with USB hardly ever. :) 

```
root@tiefighter:~# uname -a
Linux tiefighter 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
root@tiefighter:~# cat /etc/debian_version 
stretch/sid
root@tiefighter:~#
```

---

### Post by mux23 on 2017-02-12
so, back at this again... I found an error in the logs after all!
```

syslog.1:Feb 11 10:24:35 tiefighter kernel: [    3.346826] xhci_hcd 0000:04:00.0: xHCI Host Controller
syslog.1:Feb 11 10:24:35 tiefighter kernel: [    3.346903] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 8
syslog.1:Feb 11 10:24:35 tiefighter kernel: [    3.387098] xhci_hcd 0000:04:00.0: Host not halted after 16000 microseconds.
syslog.1:Feb 11 10:24:35 tiefighter kernel: [    3.387160] xhci_hcd 0000:04:00.0: can't setup: -110
syslog.1:Feb 11 10:24:35 tiefighter kernel: [    3.387353] xhci_hcd 0000:04:00.0: USB bus 8 deregistered
syslog.1:Feb 11 10:24:35 tiefighter kernel: [    3.387546] xhci_hcd 0000:04:00.0: init 0000:04:00.0 fail, -110
syslog.1:Feb 11 10:24:35 tiefighter kernel: [    3.387681] xhci_hcd: probe of 0000:04:00.0 failed with error -110
```

any ideas what's going on here?

---

### Post by oldfred on 2017-02-12
Is that a case the Ubuntu boots before drive has come up to speed?
It is a large drive.

Also does drive have its own power supply? It may not have just enough power to work well?
Or have you turned on drive so you know it is running and still have issue?

---

### Post by mux23 on 2017-02-15
thanks for your reply - it definitely has come up to speed before Ubuntu boots; I turned off a "fast boot" option in the BIOS and the boot splash screen (the BIOS boot splash, not Ubuntu or grub) lists the drive by name.

the drive does have an external power supply, and I am using that also.

I'm stuck - it seems like maybe it's an older USB3 chipset on my pc, but it also seems like there should be some way to force Ubuntu to use the appropriate module at boot, or force a retry/reset of the xhci module from /etc/rc.local, or something along those lines... but currently the only way I can get the drive to be recognized by Ubuntu is to physically unplug and replug the USB cable from the drive.

(I know, I know, it sounds like that's just really not a big deal at all... but here's the thing: the Fit-PC3 is a 12v computer mounted deep in the wall of my off-the-grid cruising sailboat, and I'm currently working on her electrical system in Mexico... every time I lose power, which this month is pretty regularly, I have to crawl around in the guts of the boat to unplug/replug a USB cable so that I can see my storage drive again. it's really annoying!! :D )

---

### Post by oldfred on 2017-02-15
I assume for low voltage systems there are backup power supplies. It sounds like you really need one.
I just moved modem, router, phone switch and Ethernet switch to basement and added a backup power supply as any power flicker often required me to reset each of them in order.

Do not know about resetting, but found this:
[http://www.ubuntubuzz.com/2016/06/reset-usb-20-ehci-usb-30-xhci-without-reboot-linux.html](http://www.ubuntubuzz.com/2016/06/reset-usb-20-ehci-usb-30-xhci-without-reboot-linux.html)

lsusb shows my flash drive as this:
Bus 002 Device 002: ID 13fe:5500 Kingston Technology Company Inc.

But it is shown as a drive:
sudo lshw -C Disk -short
/0/100/14/0/2/0.0.0    /dev/sdc   disk           61GB SCSI Disk

---

### Post by mux23 on 2017-02-17
I don't believe power is part of the problem here; the drive is on a separate power supply from the computer. furthermore, the entire system *is* a backup power supply; it's a solar/wind system powered by four golf cart batteries. :) I monitor the system *very* closely for any fluctuations; I'm a ham radio guy, and the slightest hiccup in the power system shows up as massive distortion in my radio signals. :)

again, if I plug in the drive and then boot the computer, the BIOS sees the drive and calls it out by name in the BIOS devices list (Seagate Backup Hub)... but then Ubuntu does not see it. in fact, as far as I can tell (from the log snippet I posted above), Ubuntu doesn't even configure the USB3 interface at all!

however, if I boot the computer *without* the drive attached, and then attach the drive after Ubuntu is booted, the drive appears just fine.

I suspect this has to do with the order of the kernel modules being inserted, maybe some kind of race condition? alternately, maybe the BIOS having recognized the drive at boot means that it is presenting the drive to Ubuntu in a different way somehow?

---

### Post by vidtek on 2017-02-17
Mux23-

I have the same issue with USB3 ports on an older mobo, I just use a simple script to reset the USB bus after everything is loaded in the autostart bit of KDE.

```
#!/bin/sh

SYSXHCI=/sys/bus/pci/drivers/xhci_hcd

if [ "$(id -u)" != 0 ] ; then
 echo This must be run as root!
 exit 1
fi

if ! cd $SYSXHCI ; then
 echo Weird error. Failed to change directory to $SYSXHCI
 exit 1
fi

for dev_id in ????:??:??.? ; do
 printf "${dev_id}" > unbind
 printf "${dev_id}" > bind
done
```

I just call it reset_usb.sh, but it has to be run as root.

I have a rig in my loft with all the fans and drives spinning noisily aloft with a big conduit running all the cables to my living room, the WAF is not to be taken lightly.

I found I had to keep getting the slingsby ladder down and pressing the on/off button, so hard-wired into the power switch and reset switch of the case down to the end of the conduit with a couple of momentary micro-switches.  I haven't been aloft for a week now!

Cheers, Tony.

---

