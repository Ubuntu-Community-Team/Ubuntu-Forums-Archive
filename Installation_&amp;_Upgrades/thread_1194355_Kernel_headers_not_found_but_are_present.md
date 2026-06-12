---
title: "Kernel headers not found but are present?"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by chrispy212 on 2009-06-22
Hey,
So I'm trying to install something that will allow me to use the extra buttons on my laptop, one of which is basically the on-switch for my wireless card, without which, I cannot connect wirelessly to our LAN. This package is called acerhk.

However, on either trying to use make on the source downloaded from their site, or using build from module-assistant tells me that I don't have the kernel headers, and to either get them from apt, or use the prepare option in m-a. However, I do have the correct headers. I did try both of their suggestions though, and they didn't help
In /usr/src, I have linux-headers-2.6.27-7-generic, linux-headers-2.6.28-13 and linux-headers-2.6.28-13-generic, with my kernel being 2.6.28-13-generic. I also have a link from /usr/src/linux to linux-headers-2.6.28-13-generic. 

What am I missing?!

Thanks

---

### Post by Shazaam on 2009-06-22
Quick experiment-
Try this in terminal and see if it wants to install anything...
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by chrispy212 on 2009-06-22
Nah, doesn't wanna install squat. 0 updated, 0 installed etc.
What does this mean?

---

### Post by master_kernel on 2009-06-22
Check that the symlinks are set correctly in /lib/modules/$(uname -r).

Scratch that. I forgot Ubuntu's kernels don't have symlinks there. Instead, try this:
```
cd /lib/modules/$(uname -r)
rm -f build source    # They technically shouldn't exist anyway
ln -s /usr/src/linux-headers-$(uname -r) build
ln -s /usr/src/linux-headers-$(uname -r) source
```

Note that none of those commands should return any errors if the headers are installed.

---

### Post by chrispy212 on 2009-06-22
Nope, no errors
Well, I got some permissions nonsense cos I overlooked using sudo at first, but I don't think that's what you meant! Adding with sudo, none of those lines caused an error.

Hasn't fixed the original build errors though... it's convinced the headers don't exist
Is it me or is this weird?

I should also probably add that this was a fresh install yesterday.

---

### Post by master_kernel on 2009-06-23
What does m-a prepare output?

---

### Post by chrispy212 on 2009-06-23
It gives me
```

chris@medion-laptop:~$ sudo m-a prepare
[sudo] password for chris: 
Getting source for kernel version: 2.6.28-13-generic
apt-get install linux-headers-2.6.28-13-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.28-13-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

Done!

```

---

### Post by chrispy212 on 2009-06-25
Has everyone given up? Linux isn't much good if I can't use make!
:confused:

---

### Post by master_kernel on 2009-07-01
> **chrispy212 said:**
> Has everyone given up? Linux isn't much good if I can't use make!
:confused:
Make sure your system is up to date. Then make sure you are root, and followed the directions exactly for setting up the module.

Especially ./configure, since you didn't mention that. I'm not sure if the package includes it, but if it does, make sure you run it.

If that fails, post back here if you haven't given up.

---

### Post by chrispy212 on 2009-07-02
The module does not contain a ./configure

I edited the makefile to directly point to my headers, but now I get

```

CFLAGS was changed in "/home/*****/Desktop/Downloads/acerhk-0.5.35/Makefile". Fix it to use EXTRA_CFLAGS. Stop.

```

So I fixed it to EXTRA_CFLAGS in the makefile. So then it build, but... 
```

WARNING: modpost: Found 2 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'

```

which has stumped me, again. Should I actually build my kernel like that, or is it telling me something will go wrong?

---

### Post by master_kernel on 2009-07-14
I'm stumped too. But then again I don't use manual source files that often.

---

