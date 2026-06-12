---
title: "FX5200 and a dell poweredge 830"
date: 2010-02-01
forum: Hardware
---

### Post by Beardfish on 2010-02-01
Hello

I've been battling recently with a retired dell poweredge 830. Tired of  the low resolution and 16Mb of video memory - I purchased a geforce  fx5200.

With no bios option to disable onboard video, I've been having some  trouble. With the card installed - I can use the display output just  fine to access command line / recovery stuff. But when booting normally,  I hit the splash screen - then just blank screen with everything going  on in the background just fine.

So I've been testing my googling tonight trying to find a solution for  my complete unfamiliarity with Ubuntu (completely new user, v9.10  karmic).

Sorting through solutions from previous versions / builds, I have only  been able to find ones dealing with editing xorg.conf

Other searches bring up resolution problems (I would be thrilled with  640x480 right now)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

This is the last thing I came across that seems to get me anywhere.

The output for -> lspci | grep -i nvidia 
...
06:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX  5200] (rev a1)
...
Trying to follow solutions using 'gksudo' results in an output of ->
...
(gksudo:1598): Gtk-WARNING **: cannot open display: :0
...

Please excuse my newness, this is a bit overwhelming at first.

Thanks for reading my ramble

---

### Post by lindsay7 on 2010-02-01
I think I can cut to the chase for you with that video card.  I had the same one in my desktop and it worked fine up until about Ubuntu kernel 2.6.31.16 or 2.6.31.15 I can not remember now, it has been a few weeks.  The problem is that these new kernel updates do not work with the 5200 card. All you will get is low res video. My desktop has an older motherboard and will only accomodate a pci card or a AGP card. So I bought an AGP card (Nvidia GeForce 6200) for about $25 from Newegg and that took care of the low res problem.  I too search all over the web for a solution to the problem with the 5200 card and there was none other than updating the graphics card.

So the best thing to do is get a newer vid card or go back to an older kernel or older Ubuntu or Mint that uses the older kernel.

---

### Post by Beardfish on 2010-02-01
Update, thought things over and went back to one of the original solutions found on these community forums. Using command line to install envy-ng, the text interface allowed me to install the Nvidia driver v173.14.20

Rebooted and now everything is working fine so it seems, 1024x768 (hey it's an old tv - and I was fine with 800x600 up until this point lol)

Thanks

---

### Post by lindsay7 on 2010-02-01
I am happy you got it working.  Just be advised that as time goes on and new kernels come out, you may keep seeing problems with this card. You might want to plan ahead and shop for a new vid card now while you have the time.  At some point that 5200 is going to hit the wall with your set up.

---

### Post by Beardfish on 2010-02-01
I understand. I just have to make considerations since the only available slot for a video card is a 64 bit pci slot (pcie x8 slot is too close to the south bridge for me to put a real card in)

I think the fan on this FX5200 will fail before it stops working in any other sense.

---

