---
title: "Major problem updating to 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Vishesh on 2009-10-30
Hi
I have both Ubuntu and Kubuntu installed. I predominately use KDE, but I keep switching. While upgrading to 9.10 via KDE, I got a ksudo error, during the installing part and then the update mananger just went blank. I left it alone for a couple of hours, but nothing happened. Firefox got uninstalled somehow. 
When I tried to start the update-manager-kde again. It just wouldn't start. So I like an IDIOT thought that maybe I should restart the comp, and so I did.
Untill I got an errror while booting -
Booting 'Ubuntu, Linux 2.6.31-14-generic'
error: unknown command 'linux'

I should mention that I had already installed grub 2 a week back or so, and it working flawlessly. I get an unknown command 'initrd' error for the other kernels(2.6.28-*). I tried following the instructions given over here [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) (Unknow Command 'initrd' section), but it doesn't seem to help.

Does anyone have any idea what I can do? I don't have the LiveCD lieing around, but if needed I could download it. I suppose.

---

### Post by Sealbhach on 2009-10-30
I would suggest trying to reinstall Grub2 with a Live CD using this procedure here:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

There are a few more commands than before, but it's not too difficult to follow.

.

---

### Post by Vishesh on 2009-10-30
> **Sealbhach said:**
> I would suggest trying to reinstall Grub2 with a Live CD using this procedure here:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

There are a few more commands than before, but it's not too difficult to follow.

.

Okay. I've put the Live CD for download (7 hours+ :-( ). But do you really think it's a grub2 problem? I had already installed grub2 a week back, so that I won't have any issues upgrading to 9.10. Oh well, lets see.
My main concern is that the entire upgrade didn't complete before the error came.

---

### Post by Sealbhach on 2009-10-30
> **Vishesh said:**
> Okay. I've put the Live CD for download (7 hours+ :-( ). But do you really think it's a grub2 problem? I had already installed grub2 a week back, so that I won't have any issues upgrading to 9.10. Oh well, lets see.
My main concern is that the entire upgrade didn't complete before the error came.

From what I can see, you've installed a new kernel
```

Booting 'Ubuntu, Linux 2.6.31-14-generic

```

but the boot manager doesn't know how to handle it. So the first thing to try is to reinstall Grub2. If you can't get into your system, you're going to need a Live CD to fix it, whatever the problem is.
.

---

### Post by Vishesh on 2009-10-31
I followed the instruction given on the link till the **update-grub** command. I get an error -
```
grep: proc/mounts/: No such file or directory
Cannot find list of partitions!
done
```Any idea as to what I should do? Should I try the next command - **grub-install /dev/sda **?

---

### Post by Vishesh on 2009-11-02
I finished following the instructions on the link provided, and then on trying to boot I get the following error -
```

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for UUID=49baf3f9-e920-459d-956602901b286f045
/temp: waiting for (null)
...
...

```

The /etc/fstab file seems totally fine to me. Does anyone have any idea as to what I can do? It's been a number of days since I had my system working, and I really wish I hadn't tried to upgrade.
Is there no solution but a complete re-installation of the entire OS? I don't want to do this, as there were loads of softwares which I downloaded and compiled on my own, and re-doing the entire thing would be a major pain in the ***!

---

### Post by Vishesh on 2009-11-02
bump!
I've been looking for answers for quite sometime now. Now I'm on the process of backing up over 500gb of my data. I hope someone has a solution ..

---

### Post by Vishesh on 2009-11-02
Solved. A simple **mount -o remount, rw / **and **sudo** **dpkg --configure -a** in the recovery console!

I'm kinda glad no-one pointed me to the answer, now I'll always remember, and I landed up learning up a lot. Not to mention backing up my entire hard drive :-)

---

### Post by nemoskipper on 2009-11-04
Cool Vishesh.

Thanks

---

