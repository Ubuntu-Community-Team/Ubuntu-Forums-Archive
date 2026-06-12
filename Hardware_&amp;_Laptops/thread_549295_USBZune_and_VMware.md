---
title: "USB/Zune and VMware"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by utahcon on 2007-09-12
I have Windows XP running in VMware, I want to have my Zune plug in and be recognized that way.

The problem I am having could be related but I am not sure.

When I plug my Zune in via USB Kubuntu finds it (as a camera), and then promptly it disappears. It repeats this process over and over. 

I think this is causing the VMware to not be able to capture/mount the device for use in Windows.

How can I stop this?

---

### Post by twistedneck on 2007-11-14
I had a similar problem. 

Fixed it by properly initializing the usb port before i started vmware.

sudo -S mount -t usbfs /dev/bus/usb /proc/bus/usb

type that in before starting vmplayer and boom, finds the zune.

Now my only problem is getting the wireless sync to work int he new zune 2.0 software.

---

### Post by raydar on 2007-11-17
I also had the vmware no USB drive problem, with my drive showing up in Ubuntu Gutsy but not in the XP guest and VM-->Removable Devices-->USB Devices showing "empty."  I put 

usbfs  /dev/bus/usb /proc/bus/usb  usbfs  auto  0  0

in /etc/fstab, powered off the vm, exited vmware, and started it all up again, and not only my USB drive but my MIDI adapter showed up in VM-->Removable Devices-->USB Devices (I checked just the USB drive's checkbox) and in the XP guest.

BUT, when I started the XP guest, just before the guest popped up a "found new hardware" balloon, Ubuntu gave me an "Unsafe device removal" warning balloon.  Inside the XP guest, I could successfully copy a file to & from the USB drive & the desktop.  Outside the XP guest, in Ubuntu, the USB drive was (predictably) gone. 

 Is there anything wrong with the line I put in /etc/fstab, or is there a way to route the traffic so that the drive can be mounted in both the XP guest and Ubuntu?

---

### Post by raydar on 2007-12-02
Apparently there was something wrong with what I put in /etc/fstab.  I tried omitting the first of the two path arguments; i.e., where I had both locations specified via

usbfs /dev/bus/usb /proc/bus/usb usbfs auto 0 0

I tried instead just

usbfs /proc/bus/usb usbfs auto 0 0

and my USB drive showed up in VM-->Removable Devices-->USB Devices and in "My Computer" on the XP guest.  

I can't access my USB drive from Linux, but maybe this is the lesser of two evils, 'cause I had been using a Linux-desktop shortcut to a vm-desktop folder in order to open the folder & copy files  to my USB drive to take to work; that's arguably less straightforward than copying to the USB drive "the normal way" inside the vm. 

It seems reasonable that only one file system could have the USB drive mounted at one time, vs. conflict issues, but is that (a) in fact or (b) necessarily the case, with a vm?

---

### Post by saltydog on 2007-12-16
I had this message:

```
mount point /proc/bus/usb does not exist
```

---

### Post by andhraandroid on 2008-04-28
I know this is an old thread but since i have pretty much the same problem i thought that instead of creating a new thread id just post in this one.
Anyway I have a Zune 1.0 as in the old zune and i recently shifted back to ubuntu after a long hiatus. I've never been a serious user but this time i intend to commit, i've even deleted my normal xp install
I am using hardy heron and to get my zune synching i set up an xp virtual machine using virtualbox....not vmware....unfortunately i seem to have hit a roadblock.....zune is not mounting at all... xp.not even in ubuntu although i expected that because i've heard a lot about the lengths to which microsoft has gone to ensure zune only works to a 100% under xp. 
I enabled the usb ports on the virtual machine and my external harddrive seems to be recognized. 
I got my VM to recognize this by using the usb configuration tool that virtualbox has built in......unfortunately since my zune isnt mounting even on my ubuntu partition i am not able to configure it to work on my VM.
Any help would be greatly appreciated. I would normally boot into xp every time i had to sync but i rather hastily made the decision to get rid of my dual-boot setup and go only with ubuntu
Thanks

---

