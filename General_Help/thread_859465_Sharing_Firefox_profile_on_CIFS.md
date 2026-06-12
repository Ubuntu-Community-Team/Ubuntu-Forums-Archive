---
title: "Sharing Firefox profile on CIFS"
date: 2008-07-14
forum: General Help
---

### Post by arp87 on 2008-07-14
Hi,

I am very new to Linux and have been tinkering with Ubuntu for about a month now, and I love it and it is now my primary OS. But I am having a problem trying to share a common Firefox profile between my different computers.

I am running Hardy in a dual-boot setup with XP, and I also have a CIFS mounted file server and a laptop (which I plan to dual boot as well). I would like to store a common Firefox profile on my file server.

I used Firefox Profile Manager (firefox -profilemanager) to try to create a new blank profile on the mounted device which I could then copy my settings into. However no files were created in the directory; and when Firefox tries to access that profile two files are created in the directory -- "lock" and ".parentlock". If I delete those files, copy my profile settings into the directory, and then try to use it as the default Firefox profile, the same two files are created and in this case Firefox breaks and gives me a "Firefox is already running" message, even if I reboot, and the only solution is to remove completely and reinstall.

I have created new profiles in other local directories and they work fine so I know this has something to do with the mounted device. It seems like maybe a permissions issue but the permissions seem OK as far as I can tell and the mounted device works fine with everything else. Does anyone have any suggestions ? And what are these "lock" and ".parentlock" files?

Thanks

---

### Post by arp87 on 2008-07-14
OK well I stopped being lazy and did some googling on the lock and .parentlock files and discovered they are created by Firefox when the profile is in use and that's the reason for the "Firefox is already running" message. 

However it still doesn't explain the problems with creating a new profile on my CIFS mounted device, or using an already existing profile on that same device.

After some more searching I found someone who had a similar program and for him apparently he fixed it by changing the mount options in /etc/fstab. Unfortunately I don't really understand the mount options so I don't know what is wrong with mine or what I should change them to.

He says that his original mount options were 
```
/dev/hda4 /shared vfat defaults 0 0
```
and he changed them to
```
/dev/hda4 /shared vfat rw,user,users,auto,umask=0000 0 0
```

in my case, my fstab line says
```
//NAS/media /mnt/NAS/media cifs guest,rw,iocharset=utf8 0 0
```

I really don't know what most of those options are so unless anyone has any suggestions based on these fstab options I am probably going to let it go... in the meantime I am going to check out the newly released Mozilla Weave and see if that can provide the desired functionality..

---

### Post by arp87 on 2008-07-14
Ok well apparently its related to a known bug with sqlite3 and cifs and is also related to a known firefox bug... its been suggested to add "nobrl" to the mount options but that didn't work for me.

For posterity's sake here are some bug reports..

[https://bugzilla.mozilla.org/show_bug.cgi?id=278860](https://bugzilla.mozilla.org/show_bug.cgi?id=278860)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483507](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483507)
[https://bugs.launchpad.net/debian/+source/samba/+bug/117730](https://bugs.launchpad.net/debian/+source/samba/+bug/117730)

---

