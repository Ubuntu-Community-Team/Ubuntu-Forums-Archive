---
title: "Sound dead after update (no alsamixer either)"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by royrules22 on 2007-05-08
So I'm running Edgy (not Feisty) and my sound (Intel HDA) was working fine. And then a few weeks ago we had a kernel update. Ever since then I have no sound. When I click on the sound icon I get this error: 

"No volume control GStreamer plugins and/or devices found."

Typing in alsamixer at the command line gives me:
"alsamixer: function snd_ctl_open failed for default: No such device"

I did lshw and under multimedia it says this:
```

*-multimedia UNCLAIMED
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:febfc000-febfffff irq:7

```

I really need the sound for a presentation. Any help?

---

### Post by royrules22 on 2007-05-08
err... bump?

---

### Post by royrules22 on 2007-05-08
umm yea

---

### Post by royrules22 on 2007-05-08
Come on people. It's in the second page already and no replies? :(

---

### Post by royrules22 on 2007-05-09
bump...

---

### Post by syxbit on 2007-05-09
you don't need to bump 4 times in the same day
just go to the alsa website, and get alsadriver, alsalib and alsautils
compile and make and sudo make install on all three in that order

---

### Post by royrules22 on 2007-05-09
Hmm first three bumps after topic fell to second page. I need to get the sound working in 45 minutes for presentation. So it's URGENT for me. Second page with no replies equals bump time in my book. 

I just did the alsadriver, alsalib, & alsautils update. No dice :(


I'm so screwed. Let's see if I can migrate files to Windows... Oh god I'm so ****ed

---

### Post by royrules22 on 2007-05-16
Well it's been 6 days. Hope that's enough waiting. 

I had to go ahead with Windows for my presentation. But I would still love to get this working..

---

### Post by zanjabeel5 on 2007-05-16
look here:
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)

instead of bumping you should have searched the forum, many people have had this problem (including myself)
here is another post: and there are many too

[http://ubuntuforums.org/showthread.php?p=2664492#post2664492](http://ubuntuforums.org/showthread.php?p=2664492#post2664492)

---

### Post by royrules22 on 2007-05-16
> **royrules22 said:**
> I just did the alsadriver, alsalib, & alsautils update. No dice :(
I tried again as per the instructions in your first link. No luck there either.

I have a Asus W3J+ btw.

 I'm going to install Feisty over this thing now since none of the data is super-important anymore and see if anything works.

---

