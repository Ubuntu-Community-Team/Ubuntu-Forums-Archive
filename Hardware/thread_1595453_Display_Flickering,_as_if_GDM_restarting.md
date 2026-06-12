---
title: "Display Flickering, as if GDM restarting"
date: 2010-10-13
forum: Hardware
---

### Post by spodesabode on 2010-10-13
Hi,

I've had this problem on my HP/Compaq machine since 10.04. It's fine with Windows 7, so not a hardware issue. It used to be fine with 9.x.

I've made a YouTube video of the issue here:

[http://www.youtube.com/tuliptree47#p/a/u/0/19YmkOVdh28](http://www.youtube.com/tuliptree47#p/a/u/0/19YmkOVdh28)

It visually looks like GDM restarting itself, IMO. It does this for quite some time, and I can't seem to find a trigger as to why or how, and sometimes it stops. It's made the machine completely unusable.

I've got a clean install of Maverick 32-Bit on there at the moment. According to lspci - I have the Intel 965GME integrated graphics. 

In dmesg, I see "skipping edid probe due to cached edid" - one entry for every flash of the screen.

Inside gdm/:0.log I see a few interesting entries, but one that makes senses as being linked is "I830PMEvent: Capability change".

Any ideas where to start? I'm sure I can't be the only person with this problem...

---

### Post by rklauco on 2010-10-13
You are not the only - as a matter of fact there is a launchpad entry with no resolution, yet:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/595773](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/595773)

---

### Post by spodesabode on 2011-05-03
Still getting this problem in Natty...

---

### Post by LittleLebowski on 2011-05-03
This is happening to me after upgrading to Natty.

---

