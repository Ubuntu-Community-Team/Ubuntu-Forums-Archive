---
title: "HTPC - Running short on memory + occasional screen tear - new graphics card ???"
date: 2015-07-25
forum: Hardware
---

### Post by z7APXKm on 2015-07-25
Hi,

I have a HTPC in a low(ish) profile case.  It runs Myth backend and Kodi frontend.  It's also running Skype, Chromium, my security camera setup, Samba for filesharing, web and database stuff.  I have 4GB physical memory, but 1GB seems to be shared out onto the onboard video.

My system is almost at capacity memory-wise.  I could add more, but I'm wondering whether a better solution would be to install a dedicated graphics card, which might free up that extra 1GB and also combat the occasional screen tear (especially on DVD playback, and to a lesser extent on recorded TV).  I have already installed compton and it has improved the situation greatly, but I think I'm at the limit of what software-based fixes can give me.

I have a [350W BeQuiet BN104 psu]("http://www.bequiet.com/en/powersupply/45") and an [Asus P8H77-M PRO]("https://www.asus.com/uk/Motherboards/P8H77M_PRO/") motherboard running 12.04

Any recommendations from m'learned friends?

thanks

---

### Post by weatherman2 on 2015-07-25
If you have an Asus P8H77-M PRO now (?), you can upgrade the RAM to 32GB:

[https://www.asus.com/uk/Motherboards/P8H77M_PRO/specifications/](https://www.asus.com/uk/Motherboards/P8H77M_PRO/specifications/)

I'd probably upgrade the RAM to 8GB minimum before buying a graphics card (and a new power supply to handle to graphics card).  But, first I'd check your system while running everything to see how much RAM it is actually using - and how much you've swapped, if any.  If you aren't swapping now, more RAM may not help much.

I have been using an HTPC with integrated graphics and it works beautifully for me - no screen tearing to report though at best I'm doing 720p video not 1080p or anything.  I'm also not running all of that other stuff you have running.  4GB is more than adequate for what I need.  I also prefer the integrated graphics - less power, less heat, one lass fan running, etc.

---

### Post by Yellow Pasque on 2015-07-25
What kind of GPU does it have?
```
sudo update-pciids
lspci | grep -i VGA
```

---

### Post by z7APXKm on 2015-07-26
Thanks for the replies.


```
# lspci | grep -i VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
```

Swap info:

```
# swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       3875836 183856  -1

```

---

### Post by efflandt on 2015-07-26
The **free** command checks how much memory is being used and available (and swap). buffers/cache (which caches drive access) will automatically be freed up as needed for programs.

---

