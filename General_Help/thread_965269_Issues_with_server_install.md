---
title: "Issues with server install"
date: 2008-10-31
forum: General Help
---

### Post by Phixion on 2008-10-31
I've been trying to install Ubuntu Server Edition on my server, it's a Celeron M 1.30GHz - after installing and rebooting it's giving an error message, something about the kernel not supporting my CPU, as my CPU doesn't have PAE enabled.

Obviously I need to use another kernel, but how do I go about this? I can't access a console as it won't boot.

I've tried the alternative install CD and it wouldn't install...

Cheers

---

### Post by bodhi.zazen on 2008-10-31
Try using the generic kernel.

To install this use chroot.

Boot the desktop CD (or any live CD really).

mount your ubuntu partition (I will assume it is /dev/sda1) at /mnt

```
sudo mount /dev/sda1 /mnt
```

Now chroot and install the generic kernel

```
sudo -i # To become root

chroot /mnt
```

Now 

```
apt-get install linux-generic
```

Reboot to hard drive, choose the linux kernel. If you wish you can then re-compile the server kernel without PAE support.

---

### Post by Wayne_V on 2008-10-31
Yes - it does seem the server kernel requires PAE.   The generic doesn't, I believe.  What was the error with the alternate CD?

---

### Post by Phixion on 2008-10-31
The issue I'm having with the alt-cd is that it gets to 6% on "Select and install software" and seems to get stuck.

I can hear the CD bay reading, but it isn't moving :/

---

### Post by bodhi.zazen on 2008-10-31
did you try chroot ?

---

### Post by Phixion on 2008-10-31
I'm going to give your way a go now.

---

### Post by Phixion on 2008-10-31
How do I go about getting the latest server kernel to recompile?

---

### Post by bodhi.zazen on 2008-10-31
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Phixion on 2008-10-31
Stuck already:

sudo apt-get build-dep linux

no such package - I've enabled all repositories in sources.list

Any ideas?

---

### Post by bodhi.zazen on 2008-10-31
Can you give us more information / an update ?

Are you running on the live CD or were you able to install the generic kernel ?

Look at your sources list , make sure you have the deb-src enabled

---

### Post by Phixion on 2008-10-31
I had all respositories enabled, after installing the generic kernel I logged in fine but can't find build-dep package.

Nevermind, it seems like too much fussing to compile a kernel, I guess I'll just make do with the generic.

---

