---
title: "Medion MD 96630"
date: 2009-05-17
forum: Hardware
---

### Post by moose2 on 2009-05-17
Hi,

I have a Medion MD 96630 Notebook with two problems:
[LIST]
[*]sound (line out) doesn't work
[*]boot behavior is strange
[/LIST]

Here is a [video of my notebook booting](http://www.youtube.com/watch?v=HqNmHgjNKjQ), [beeping]("http://www.youtube.com/watch?v=6ITW1wvAjkU") and a video of my notebook [displaying some strange lines by shutting down]("http://www.youtube.com/watch?v=1mIo1v1Xf9M").

It starts, stops, and starts after 3 seconds again to boot. 
Here are the Launchpad-Bugs I submitted:
[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312302](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312302)
[*][https://bugs.launchpad.net/fedora/+bug/313486](https://bugs.launchpad.net/fedora/+bug/313486)
[/LIST]

In [ubuntuusers.de](http://wiki.ubuntuusers.de/Medion_MD_96630) we tried to find a solution, but we could only get the internal speakter to work by adding
```
snd-hda-intel model=laptop-eapd probe_mask=1
```
to **/etc/modprobe.d/alsa-base**

It would be very nice if you could help me to fix those bugs.

Sincerely Yours,
Martin Thoma

---

