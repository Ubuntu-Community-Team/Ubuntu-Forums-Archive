---
title: "Having trouble using ntfs-3g and ntfs-config packages..."
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by newagelink on 2007-05-13
My Windows partition ("drive C") is, by default, located at "/media/disk". (Why do I have to type my password just to view it? Also, should I or can I mount it someplace else -- like at "/windows" -- instead? Or is it best to leave the defaults alone? I have to type my password into that stupid keyring every time as well, but that's another issue -- the PAM-keyring thing I tried installing also had no effect.)

[quote="https://help.ubuntu.com/community/MountingWindowsPartitions#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971"]Enable the universe repository and install the ntfs-config package.[/quote]I assumed the universe repository was already enabled by default, because I opened Synaptic Package Manager and found ntfs-3g and ntfs-config already sitting there.

So I marked ntfs-config for installation, which automatically marked ntfs-3g as well. So far so good, right?

Applications > System Tools > NTFS Configuration Tool. The only partition it listed was at "/dev/sda1", I think. (Going from memory; I only took a glance at it and assumed it was referring to /media/disk, because I thought "sda1" referred to the first partition detected ...) As the directions said, "The upcoming tool will detect NTFS partitions on your system." so I assumed that it had.

"if you wish to, click the mount directory to change it. When finished, click Apply." I didn't want to mess with anything, because I thought the default was correct, so I just clicked apply and went on.

"On the next screen Enable write support for internal device will be selected by default. Click OK."

No. That selection was disabled, and the only option I had to check or uncheck was "Enable write support for **external** device". I checked it, and it had no effect on /media/disk. It's still read-only. 

Realizing I messed up, I tried reinstalling the package, thinking that would take me back to the first screen to try again. No. Applications > System Tools > NTFS Configuration Tool took me directly to the second window again.

I completely remove ntfs-3g and ntfs-config and then reinstall them. It still takes me directly to the second screen, the only option being to enable write support for external device.

What do I need to do to fix this? :( Thanks for reading...

---

### Post by newagelink on 2007-05-14
A conversation this morning:
[quote="#ubuntu-offtopic channel"] ethereality checks to see if his thread has any new responses.
<ethereality> :( nobody loves me. [http://ubuntuforums.org/showthread.php?t=442779](http://ubuntuforums.org/showthread.php?t=442779)
<mc44> because it makes little to no sense? :P
<ethereality> What doesn't make sense about it?
 I thought I had explained the situation and what I'd done very thoroughly.
<mc44> :)
Ok, firstly you shouldnt be asked for a password to mount a local patition...
 that is just weird
<mc44> ethereality: pastebin your /etc/fstab file?
<ethereality> [http://paste.ubuntu-nl.org/20802/](http://paste.ubuntu-nl.org/20802/)
<mc44> oh ntfs-config removes the drive from there? hmm
<ethereality> oh
 um, by the way
 it's not at /media/disk by default, either
 i have to go to computer:///
 and then double click on
 37.3 GB Volume
 then it says
 "Access to this internal disk has been restricted by the administrator due to security reasons", i think, and it asks me for my password.
<mc44> ah, thats probably your problem :)
<ethereality> _then_ it mounts it at /media/disk and tells me i can stop the operation by pressing something.
<mc44> this is an internal drive right?
<ethereality> yeah, it's inside my computer, if that's what that means.
<mc44> and your windows partition is sda1?
<ethereality> well, i thought it was. i thought that's what it was when i was using, what was it, 5.10?
 all i know is that my windows partition is mounted at /media/disk
 after i double click on it from the computer:/// thing
<mc44> ethereality: type mount at a terminal
<mc44> should say /dev/sda1 on /media/disc
...
<ethereality> /dev/sda1 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8) is there.
<mc44> right
<ethereality> (see [http://paste.ubuntu-nl.org/20805/](http://paste.ubuntu-nl.org/20805/) )
<ethereality> [...] so i was right, then, sda1 is that partition?
<mc44> ethereality: could you pastebin /etc/fstab.pre-ntfs-config
<ethereality> [http://paste.ubuntu-nl.org/20806/](http://paste.ubuntu-nl.org/20806/)
<mc44> ethereality: hmm your ntfs isnt in there so thats why it isnt mounted automatically. Remove ntfs-3g, follow the instruction below then it should auto mount. When that works try ntfs3g again
<mc44> !ntfs
<ubotu> To view your Windows/Mac partitions see [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) . For write access see !ntfs-3g or !fuse
<ethereality> thanks ... i'll try that ...
<ethereality> i had thought that it already mounted them because it had shown them as being there at computer:///[/quote]So, I'll go try that.

---

