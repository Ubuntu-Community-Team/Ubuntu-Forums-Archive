---
title: "How to mount a HDD on the same mount point for two different states"
date: 2014-03-22
forum: Hardware
---

### Post by gavdari on 2014-03-22
Hi Guys,
I've got an external hard drive usually connected to another computer over the network and mounted at /media/external on my Linux Mint 16 machine. However, sometimes I need to connect it to my linux laptop directly without losing the paths, so I was wondering if I can modify fstab in a way that uses the same mount point for the same drive, no matter how it is connected. I did a quick search, and I have added these two line in fstab:
```
//192.168.0.100/media/Siavash /media/external cifs guest,rw,uid=1000,gid=1000,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
UUID=F474B7AA74B76DCC /media/external ntfs users,default 0 0
```
Now when the hard drive is connected to the laptop, mount -a results in the following error:
```
fuse: failed to access mountpoint /media/external: Permission denied
```
What am I doing wrong?

---

### Post by TheFu on 2014-03-23
I would try using the LABEL to control the mount (don't know if this will work over ),
Or use autofs,
Or write a script that mounts it manually, checking both places.

It might be possible to get this working from the /etc/fstab too - I just don't know how.

---

### Post by gavdari on 2014-03-23
> **TheFu said:**
> I would try using the LABEL to control the mount (don't know if this will work over ),
Or use autofs,
Or write a script that mounts it manually, checking both places.

It might be possible to get this working from the /etc/fstab too - I just don't know how.

I forgot to mention that the drive is formatted as NTFS, and I don't think LABEL works on NTFS file system.
I tried to make it work with autofs, but it got way confusing for me :P. I tries a few tutorials and did everything they said to use autofs on a samba share, but none of them worked. It's as if I've unmounted the static mount, but no dynamic mount is there. I had to roll back to fstab static mount.
Anyways, I hope there is a way to make it work with fstab. Thanks for the tips.

---

### Post by gavdari on 2014-03-23
Just for future reference, this is how it can be done:
First I removed the physical connection entry in fstab and let it mount automatically at /media/$USER/external. Then I used --bind to create an alternative position:
```
[COLOR=#2E8B57][FONT=Monaco]sudo mount --bind /media/$USER/HDD /media/external[/FONT][/COLOR]
```

---

