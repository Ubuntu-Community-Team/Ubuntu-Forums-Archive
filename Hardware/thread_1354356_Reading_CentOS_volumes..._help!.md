---
title: "Reading CentOS volumes... help!"
date: 2009-12-13
forum: Hardware
---

### Post by zoomiest on 2009-12-13
I had a CentOS home server, running Samba - which died after a local (but short) power outage. Unfortunately, I didn't run it on a UPS.

Now the CentOS box won't get on the network...

I elected to mount the hard drive in my Ubuntu desktop box, and copy off the contents... which brings me to my question.

This CentOS file system seems to be encrypted, or otherwise unreadable.

what is with the incompatibility? I can only ready the CentOS /boot partition (ext3).

How can I read this?

(I have already installed GDecrypt, but it just says "(mountpoint) isn't empty")

Help! (important stuff on the drive...)

Should I just overcome the reason the CentOS box won't access the network? Is that easier?

---

### Post by paulisdead on 2009-12-13
Are the other partitions set up as LVM partitions?  Try this to setup lvm support.
```
sudo apt-get install lvm2
sudo modprobe dm-mod
sudo vgscan

```
At this point, I don't know where in /dev it could show up.  You might want to run "dmesg" and see if it noticed any new devices.

---

### Post by zoomiest on 2009-12-14
Thanks for your help... I seem to be getting some errors...

1) when I start to install lvm2, it says its already up to the newest, but it doesn't know the modprobe dm... command. 

```
FATAL: Module dm_mod not found.
```

vgscan wasn't working either. I got the following:
```
  Reading all physical volumes.  This may take a while...
  Couldn't find device with uuid 'HTFX9Q-pAsr-JP8s-maLb-6sRm-0Ipw-49uygu'.
  Couldn't find all physical volumes for volume group VolGroup01.
  Couldn't find device with uuid 'HTFX9Q-pAsr-JP8s-maLb-6sRm-0Ipw-49uygu'.
  Couldn't find all physical volumes for volume group VolGroup01.
  Volume group "VolGroup01" not found
```

I am sure I have to get mod-probe working first...

Any suggestions?

---

### Post by paulisdead on 2009-12-14
Sorry, think I may have left out a step.  I'm a little new to LVM myself.  Try this after vgscan
```
sudo vgchange -ay
sudo lvdisplay
```
I did some poking around, and it appears that LVM maybe compiled directly into the kernel, and not as a module in the newer versions of ubuntu, so you wouldn't need to modprobe anything.  The only LVM box I've got around is my debian server, so it's a tad different.

---

