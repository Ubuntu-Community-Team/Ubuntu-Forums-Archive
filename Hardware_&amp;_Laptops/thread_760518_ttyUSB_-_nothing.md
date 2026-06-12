---
title: "ttyUSB - nothing"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by amiga_os on 2008-04-20
Hi,

I'm trying to use an Arduino Diecimila board with Ubuntu Hardy Heron.

I'd also like to sync my Palm Life Drive with Ubuntu too.

The problem is that there is no ttyUSB* modules.  One isn't created by the Life Drive when I press the sync button, and there isn't one there ready for the Arduino.  The Arduino just blinks at me repeatedly.

If this is a udev problem, then I don't understand udev... how do I turn it off?

---

### Post by amiga_os on 2008-05-01
I've not had a response to this, but I've made some progress sorting it out.

When I find threads where people have had problems that I'm having, and they don't reply to the thread with the progress they're making it doesn't help.  So I'm going to post my findings here in case anybody out there is struggling with the same issue.

I have two particular problems with USB in Ubuntu Hardy:
My Arduino board is totally unusable, it just blinks at me.
My LifeDrive is completely undetected (not just sync problems... it's actually an undetected USB device)... this is even when using Drive Mode, so I can't even copy my files over.

Evidence - when both devices are plugged in, then typing

```
sudo blkid
```

doesn't register anything

I discovered with my LifeDrive in Drive Mode that the device was being instantly disconnected from the computer, and trying to reconnect iself again.  Use this command to see what your USB messages are doing:

```
sudo dmesg
```

All of the workarounds for problems with these devices are about automounting, etc... but since Ubuntu is automatically disconnecting my devices, they're not assigned **anything** in the /dev directory... so udev rules aren't going to solve the problem, as the problem is before udev get's involved.

Depressing...

However!  I have hunted these problems down to the ehcpi_hcp module.  Removing the module makes it possible for the device to connect (as you can see using dmesg), and therefore is detected by hal (as you can see using blkid).  Remove the module by using the following command:

```
sudo modprobe -r ehcpi_hcp
```

Using blkid, you can then mount the device that the LifeDrive is at (replace /dev/sdb1 with whatever dev the LifeDrive is mounted to, the volume will be labelled LIFEDRIVE):

```

sudo mkdir /media/LifeDrive
sudo mount -t vfat /dev/sdb1 /media/LifeDrive

```

I imagine you will be able to even sync the Palm once you've got this far (obviously not when it's in Drive Mode).  I'm yet to see if this sorts out the Arduino problem.

I will report a bug in ehcpi_hcp on Launchpad.  If this is at all helpful to anybody else, then I can put some howto's together to sync the LifeDrive, and use it in DriveMode under Hardy.

---

### Post by amiga_os on 2008-05-01
Ok,

This bug has been reported, and has been triaged as high priority by the kernel team: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746")

Let's hope it get's sorted soon!

---

### Post by optique on 2008-06-05
Did you do this?

1. Using synaptic mgr, installed sun-java6-jre, gcc-avr, avr-libc.
2. Downloaded the arduino environment (arduino-0011-linux-tgz)
3. Attempted to sudo update-alternatives --config java, but the msg stated it was not necessary since only one Java was found.
4. Double clicked the Arduino file in the Arduino app folder.
5. Application runs, I select an example sketch and compile it. Arduino Tools->Serial port shows /dev/usbtty0 selected as expected.

---

