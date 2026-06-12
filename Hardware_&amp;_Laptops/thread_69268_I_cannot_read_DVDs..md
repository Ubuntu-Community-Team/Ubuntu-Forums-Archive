---
title: "I cannot read DVDs."
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by Geek on 2005-09-26
Hey everyone!
I am a noob to Ubuntu and I need a few pointers:
Whenever I try to read this DVD which was burned for me (It has VERY important files on it and I need to be able to read them ASAP) it comes up with this message:
Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I do not know whether this is a hardware issue or a driver issue or both or something else,I would be most greatful if somebody could please help me ASAP.

Thanks for everybody's time,
Geek

---

### Post by Zelut on 2005-09-26
First thing I would suggest is checking to see whether you've done the DVD playback update from [www.ubuntuguide.org](www.ubuntuguide.org) ([http://www.ubuntuguide.org/#dvdplayback)](http://www.ubuntuguide.org/#dvdplayback)).  That may not be related but I know sometimes you need a small update for the DVD to work correctly.  There are a few other DVD related tips there I believe, might want to check those out as well..

---

### Post by mlomker on 2005-09-26
Add this line to your /etc/fstab file or replace the one that you've got for /dev/hdc.

```

/dev/hdc        /media/hdc      auto     defaults,users,noauto   0       2

```

---

