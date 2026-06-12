---
title: "HAL doesn't ignore root partition (xubuntu desktop icon)"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by vrajgh on 2007-08-28
I have had a minor problem ever since I upgraded my distribution to Feisty Fawn (or so I believe, I'm not sure how to double check which ubuntu version is running on a machine.) There has been an erroneous  icon on the XFCE desktop labelled "14G Volume."  I know for a fact that all my file systems are mounted correctly and they behave as expected. This extra icon is more of a curiosity than a problem as it hasn't got in the way of operating the machine or accessing files so I put it to one side as something to investigate once I had the time and the inclination.

That time is now.

I was intrigued that 14G is the size of my root partition and I spent some time investigating how XFCE and Thunar allocate these icons. I soon found out about the hardware abstraction layer (HAL.)  

Pertinant lines from lshal for the root partition follow:
```

volume.ignore = false  (bool)
linux.fstab.mountpoint = '/'  (string)
volume.is_mounted = false  (bool)
volume.mount_point = ''  (string)
```

Equivalent values from my home partition (which doesn't produce an erroneous desktop icon):
```

volume.ignore = true  (bool)
linux.fstab.mountpoint = '/home'  (string)
volume.is_mounted = false  (bool)
volume.mount_point = ''  (string)
```

My conclusion from this was that HAL was trying to manage the mounting of the root partition when it should be set to ignore it, as is the case for the home partition. Lo and behold, the following command causes this icon to disappear.

```
sudo hal-set-property  --udi $udi --key volume.ignore --bool true
```
(where $udi represents the appropriate udi string)

Now, this is a start of the diagnosis but not really a solution. I could add this line somewhere in the boot process but it is a real hack and HAL should know to ignore / as it knows to ignore /home.

Further research then pointed me in the direction of [this bug report on freedesktop.org]("https://bugs.freedesktop.org/show_bug.cgi?id=9836").   Although this bug report refers to an example of this problem on slackware, the discussion concludes that it is not a HAL bug but an issue with the distribution.

That thread suggests a "really simple" solution:
>  the fix is really simple - all that need to happens is that the initramfs (who
mounts rootfs) needs to create /dev/root and then after root is mounted it
should 'mount --move /dev/ /sysroot/dev' before transitioning into rootfs on
/sysroot.

Although I know in principle what initramfs is, I don't have the slightest idea how to go about altering its behaviour and think that if I do manage that for my system alone, I'll end up having to re-do the changes at future upgrades. (If I wanted to muck about with this sort of thing for fun then I'd still be running LFS.)

Alternatively, I considered applying a dirty cludge with "hal-set-property" after hal is loaded during boot but could not find a hal script in /etc/init.d. I don't therefore know what causes hal to be loaded at boot.

I suppose the reason for this post is to find out:
(1) is this really a wider problem with Xubuntu (I know of at least one other person who's had it, from   [this thread]("http://ubuntuforums.org/showthread.php?t=417665"), albeit hidden behind some other issues and misunderstandings)
(2) if someone with more knowledge than me of HAL can suggest a solution (elegant or otherwise)

Thank you very much for any help.

---

