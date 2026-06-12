---
title: "can't mount external drive using fstab"
date: 2008-08-12
forum: Hardware
---

### Post by angelicapple on 2008-08-12
Hi,

I'm trying to mount my external ntfs hard drive using fstab.
Currently I'm using the following line:

```
UUID=D0F0C760F0C74B82 /media/noot auto utf8,user,exec,noauto,uid=1000,gid=100,umask=000 0       1
```

The folder /media/noot is chown'ed by me (my user name) and chmodded 770

However with this line, when I turn on the drive it gives me a 'cannot mount volume' error.

Any ideas? Thanks in advance.

---

### Post by coffeecat on 2008-08-12
A NTFS-formatted external USB drive always automounts for me when I plug it into my Ubuntu machine. I'm assuming you mean a USB (or firewire) drive when you say 'external'. So why are you trying to create a fstab line for it? Were you having problems with automounting?

**Edit:** of course, that's with Hardy. Earlier versions of Ubuntu (pre-Gutsy?) didn't have NTFS read-write and I can't remember what they did with external NTFS drives. What version of Ubuntu are you using?

---

### Post by angelicapple on 2008-08-13
Thanks for your help. I should indeed have mentioned my version: I am using Hardy, and as you say, normally it automounts (without a problem). 

However I would like to mount using fstab so I have additional options available, and I do believe that should be possible. (To be more specific, I want to give myself the option to use a trash folder on the drive, which I have successfully done on an internal ntfs drive using fstab)

Unless it's easier to change the GNOME volume manager options that hardy uses to automount usb drives? However I wouldn't have the slightest clue how to do that, and I couldn't find any info about on the internet.

---

### Post by coffeecat on 2008-08-13
I see what you mean now. The only thing I can suggest is to use 'ntfs-3g' instead of 'auto' in the third field of your fstab line. I have had some situations where 'auto' simply wouldn't work for me (can't remember what they were now).

> **angelicapple said:**
> Unless it's easier to change the GNOME volume manager options that hardy uses to automount usb drives? However I wouldn't have the slightest clue how to do that, and I couldn't find any info about on the internet.

I think you would need to look at udev rules. I have no experience of this except for one brief and unsuccessful attempt to make some of my own. :(

---

