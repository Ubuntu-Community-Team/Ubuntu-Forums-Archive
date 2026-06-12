---
title: "No sound on Toshiba laptop."
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by wellsy1 on 2007-10-30
I have no sound on my Toshiba Satellite. I have a Realtek high definition soundcard and Ubuntu 7.1. New to Linux and need some help.

---

### Post by hoges on 2007-10-31
I have the same issue with my Toshiba m100. I remember when I installed feisty there was a lot of stuffing around to get it working. Stupid me, I assumed that the next version would fixed it, so I lost the site bookmarks...

Anyway, from what little I remember, I think it had something to do with changing the settings for alsa. I also remember having to set the driver as being generic - it gave the choice of a few different manufacturers.

I know mine uses the snd-hda-intel module, but I just don't know how to get it working. I'll post back if I find something.

Cheers
Hoges

---

### Post by hoges on 2007-10-31
Alright, I've got it working!!!

I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=473425").

For the record, I have a Toshiba Satellite M100 using Intel HDA Audio with a realtek chip. Headphones work as well.

---

