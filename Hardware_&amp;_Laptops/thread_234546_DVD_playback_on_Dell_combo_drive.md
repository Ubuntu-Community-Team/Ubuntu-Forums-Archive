---
title: "DVD playback on Dell combo drive"
date: 2006-08-11
forum: Hardware &amp; Laptops
---

### Post by hawkbane on 2006-08-11
I recently installed Ubuntu Dapper on a refurb Dell Inspiron E1405.  To get encrypted DVDs to play, I installed gstreamer.  Now when I insert any DVD, Totem autoplays it, but I have no control of the DVD.  It auto playes the first chaper of the DVD, but then will allow me no other controls over the DVD, (menus, next chapter, etc).  It almost is like it treats the disk as a CD, but it is reading the DVD.  Any ideas guys?

Thanx,
~Hawkbane

---

### Post by Jagot on 2006-08-11
Did you do this:

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by kostkon on 2006-08-11
Look you have two options:

Using Totem with the gstreamer framework you cannot have menus or subtitles in DVDs. If you want to keep Totem with the gstreamer, just install xine (sudo apt-get install gxine) to use it as your DVD player.

If you don't care about gstreamer, just install Totem-xine and it will make your Totem to use the xine framework, thus allowing you to play DVDs with Totem.

---

### Post by hawkbane on 2006-08-11
Removing gstreamer and installing totem-xine worked like a charm.  Thanx for the help!

Hawkbane

---

