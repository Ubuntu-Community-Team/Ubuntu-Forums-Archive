---
title: "Resolution Problem: XUbuntu 1024x768 in anything but desktop"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by TwiceOver on 2006-11-03
I have installed XUbuntu on an older laptop and it runs great.  The one problem is that I can't get 1024x768 resolution working.  The screen is always in 800x600 with a thick black border around it.  The strange part is that the install was in 1024 and the loading screen (The one that says XUbuntu and has a progress bar) is also in 1024.  As soon as I get to the logon it drops down to 800x600.

Xubuntu correctly finds the graphics driver Silicon Motion SM810, and I have been through the XServer reconfigure many times.  The only thing that I can possibly think is that it is sharing only 1mb of memory from the system for video and I can't change it.  That seems to be enough for Windows, maybe not for Linux?

Any ideas out there?

---

### Post by dermotti on 2006-11-03
If you select "vesa" as your video driver, do you get the same results?

---

### Post by TwiceOver on 2006-11-03
> **dermotti said:**
> If you select "vesa" as your video driver, do you get the same results?

Yes.

---

### Post by TwiceOver on 2006-11-03
Figured it out finally.

Had to define the amount of video memory: 1024k, Frame Buffer: no, Color Depth: 16.

Thats the only combination that has worked so far.  This is an older HP Omnibook XE-DA.

---

### Post by dannyboy79 on 2006-11-03
> **TwiceOver said:**
> Figured it out finally.

Had to define the amount of video memory: 1024k, Frame Buffer: no, Color Depth: 16.

Thats the only combination that has worked so far.  This is an older HP Omnibook XE-DA.
can you please be more specific how you defined the amount of video ram, etc, etc, maybe you could just post your xorg.conf?

I am having this same problem with an old hitachi laptop, here is some of my xorg.conf and lspci -v for reference. can anyone help me get 1024x768?

0000:00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01) (prog-if 00 [VGA])
Flags: bus master, medium devsel, latency 128, IRQ 9
Memory at fd000000 (32-bit, prefetchable) [size=16M]
Memory at fea00000 (32-bit, non-prefetchable) [size=2M]
Memory at fed00000 (32-bit, non-prefetchable) [size=1M]

and I am just using the 

Section "Device"
Identifier "NeoMagic Corporation NM2160 [MagicGraph 128XD]"
Driver "neomagic"
BusID "PCI:0:2:0"
Option "XaaNoScanlineImageWriteRect"
Option "XaaNoScanlineCPUToScreenColorExpandFill"

i have posted this question many times but no one has been able to help me, someone said that they got theres to work by adding the 2 options you see but still no go! oh yeah, also, my default depth is 16 just like the previous persons.

---

### Post by TwiceOver on 2006-11-03
I configured mine through the config utility

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dannyboy79 on 2006-11-03
> **TwiceOver said:**
> I configured mine through the config utility

```
sudo dpkg-reconfigure xserver-xorg
```
ok, well I may have done that once but I don't ever remember being asked what I wanted to define the amount of video memory to? or the default depth for that matter, can you please explain more or the easiest would be to just post your xorg.conf. thank you

---

### Post by TwiceOver on 2006-11-03
I'll be at work for the rest of the day so I don't have the laptop with me.  Also that laptop doesn't have internet (for now)or a cd burner.

During the xserver configure the memory question is probably fourth or fifth.  The text states something like "some cards that don't have memory or share memory... may have to specify..." The depth question is the very last question.

---

### Post by dannyboy79 on 2006-11-03
> **TwiceOver said:**
> I'll be at work for the rest of the day so I don't have the laptop with me.  Also that laptop doesn't have internet (for now)or a cd burner.

During the xserver configure the memory question is probably fourth or fifth.  The text states something like "some cards that don't have memory or share memory... may have to specify..." The depth question is the very last question.

alright, i take you aren't going to attempt to post your xorg.conf for me later? Well, one last question then, when it asks you for the amount of video ram, did you specify it in the k, so I actually put 1024, or did you specify it in mb, which then i think I would actually enter a number around 1? Also, what does your bios say if anything about sharing video ram? thank you so very much!

---

### Post by TwiceOver on 2006-11-03
> **dannyboy79 said:**
> alright, i take you aren't going to attempt to post your xorg.conf for me later? Well, one last question then, when it asks you for the amount of video ram, did you specify it in the k, so I actually put 1024, or did you specify it in mb, which then i think I would actually enter a number around 1? Also, what does your bios say if anything about sharing video ram? thank you so very much!

I wish I could, but short of retyping it I have no way to get it off the laptop right now.  The configuration asks you to specify in kb so on the line I put "1024" without the quotes.  My bios is so old it doesn't show any information about the shared ram, however I know there is 128mb in the laptop and it currently reports as 127mb.  So 1mb must be going to the video.

---

