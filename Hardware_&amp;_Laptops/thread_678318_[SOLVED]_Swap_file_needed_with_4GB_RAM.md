---
title: "[SOLVED] Swap file needed with 4GB RAM?"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by nowhere@cox.net on 2008-01-25
Hey all,

Got Gutsy 64 installed on my T61 and read in a post that a swap file isn't really needed with 4GB RAM. Since I was short on HD space I opted to fore go the swap. 

I was wondering if the problems with suspend and hibernate everyone is having could be related. Do I need swap space to hibernate? 

If I need to add a swap, I can resize the Vista partition down 4GB or however much is needed and use gparted to format it as swap but I need some advice how to "attach" it to my Gutsy system as swap. I vaguely remember seeing a command somewhere but I can seem to get my search right to find it.

What do you all think?

Thanks,
Eric

---

### Post by kidders on 2008-01-26
Hi there,

I can't say I would recommend running a system with *absolutely* no virtual memory, no matter how much RAM it's got, to be honest. If you want to be able to hibernate your PC, you'll need at least as much virtual memory as you have RAM; if not, then the quantity you go for is less critical, and depends only on what you do with your computer.

> **nowhere@cox.net said:**
> If I need to add a swap, I can resize the Vista partition down 4GBI would suggest trying to avoid resizing filesystems where at all possible (unless you've backed up your system, I suppose). An alternative approach would be to store your swap space inside another filesystem (much like Windows and OSX do it), although it isn't nearly as efficient.

Plugging swap space into Linux is a simple matter of...```
$ sudo swapon /dev/whatever
```Your system should begin using it immediately. Most people also add a line like...```
/dev/whatever none swap sw 0 0
```...to their /etc/fstab to make swap activation automatic during boot.

If you intend to hibernate your PC, I would suggest allocating a little more swap than you have RAM. You see, if for some reason your Linux happened to need a little virtual memory for something, there may not be enough of it left over to hibernate.

---

### Post by nowhere@cox.net on 2008-01-27
Thanks kidders,

Since I did the guided resize option to install Gutsy to begin with, I decided to go ahead and ignore your most likely very wise advice about resizing. However, there's nothing really to lose on either system since the T61 is brand new and I have only booted Vista a couple times to make sure stuff is working and Gutsy is a brand new install with only the tweaks required to get Gutsy working properly, Since Vista space was really low already I decided to boot from the live CD and use gparted to shrink my ext3 partition. I then ran  fsck to update the filesystem with the new size, formatted a 5GB partition as swap (I have 4GB ram) and reboot to linux. Absolutely flawless. 

I the used your command to mount the swap and as far as I can tell it's all working fine (system monitor reports 5GB of swap).  I havent yet rebooted with the fstab entry but I am sure it will be fine also,

Thanks for the very useful reply. It saved me a ton of reinstall and re-tweaking time of starting over.

BTW do you know if it poses a problem to have partitions not ending on a cylinder boundary? All of my partitions report that including the recovery partition from Lenovo which I did not touch in the installation of Gutsy.

Thanks!
Eric

---

### Post by kidders on 2008-01-28
Glad your swap worked out for you. :-)

> **nowhere@cox.net said:**
> BTW do you know if it poses a problem to have partitions not ending on a cylinder boundary?Partition misalignment can cause problems in certain special cases, with a small number of OSs (eg sparc or msdos systems) ... but with Vista + Linux, I don't think it makes the slightest difference.

---

### Post by nowhere@cox.net on 2008-01-28
Awesome thanks because I don't think there would be much i could do with it since the boundary between the recovery partition and the Vista partition as set from the factory were the same way and I don't really want to mess with the recovery partition.

Thanks for the help. Now I just need to find the tweaks to actually get hibernate to work ;)

Eric

---

### Post by kidders on 2008-01-28
No worries. :-)

---

