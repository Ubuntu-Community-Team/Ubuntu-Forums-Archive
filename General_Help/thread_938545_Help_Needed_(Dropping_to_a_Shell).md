---
title: "Help Needed (Dropping to a Shell)"
date: 2008-10-05
forum: General Help
---

### Post by McFuzzie on 2008-10-05
Hey,

I am new here and to this forum and I am having issues with the installation of Ubuntu. I get this message:

Starting up...
Loading, please wait...
usplash: Setting mode 1600x1200 failed
usplash: Using mode 1280x1024
Gave up waiting for root device.   Common problems:
      - Boot args (cat /proc/cmdline)
          - Check rootdelay= (did the system wait long enough?)
          - Check root= (did the system wait for the right device?)
      - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/7f374ef3-be4b-4535-81b4-755d55e9a98b does not exist. Dr
opping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

Can you please help me.

---

### Post by bodhi.zazen on 2008-10-05
> **McFuzzie said:**
> Hey,

I am new here and to this forum and I am having issues with the installation of Ubuntu. I get this message:

Starting up...
Loading, please wait...
usplash: Setting mode 1600x1200 failed
usplash: Using mode 1280x1024
Gave up waiting for root device.   Common problems:
      - Boot args (cat /proc/cmdline)
          - Check rootdelay= (did the system wait long enough?)
          - Check root= (did the system wait for the right device?)
      - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/7f374ef3-be4b-4535-81b4-755d55e9a98b does not exist. Dr
opping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

Can you please help me.

Can you tell us more about how you installed Ubuntu and your hardware ? 

That error message indicates Ubuntu did not find your hard drive as it was booting.

Also can you boot the live CD, open a terminal, and show us the output of :

```
sudo blkid
```

---

### Post by xenoputtss on 2008-10-08
I am having this exact same problem.  But what I also noticed is that if I wait wait about 1.5 mins and then type "exit" that it will continue booting.

I am using Ubuntu 8.10beta(64bit).  I have a A8N-SLI mobo with amd64 dual core.  

Once everything is booted, everything seems to work fine on the computer.  

Is there a way I can make the computer wait longer for device drivers to load?

---

### Post by xenoputtss on 2008-10-14
> **xenoputtss said:**
> I am having this exact same problem.  But what I also noticed is that if I wait wait about 1.5 mins and then type "exit" that it will continue booting.

I am using Ubuntu 8.10beta(64bit).  I have a A8N-SLI mobo with amd64 dual core.  

Once everything is booted, everything seems to work fine on the computer.  

Is there a way I can make the computer wait longer for device drivers to load?

Well I fixed my issue.  Surprisingly it was something "simple" per say.  One of my harddrives was setup as "master WITH slave" and it was the only drive on that cable.  I turned it to master only and it booted straight up with no problem....and fast too.

---

