---
title: "GeForce and Biostar mobo problem - limited screen resolution"
date: 2009-05-12
forum: Hardware
---

### Post by dchenard on 2009-05-12
Good morning,

I have this baffling problem when installing 8.04 on a machine I'm refurbishing for a friend's daughter.

Hardware:

Biostar M7VIW mobo (circa 2003)
Athlon XP 1800
512 MB DDR RAM
80 GB IDE HD
Onboard sound and LAN
GeForce MX440 64 MB AGP 4X video card

My problem is that I can't get any higher than 800 x 600 resolution (17" CRT, that works fine with other machines). Before installing the nVidia restricted driver I can choose from 320 x240 up to 800 x 600 but no higher. After installing the driver I get 800 x 600 only, can't adjust a thing.

What baffles me is that I tried to run a TNT card and it worked fine. When I got the machine it had a VoodooII 3500TV in it, and I had the same problem. The machine has a dual-boot setup with Win2k (not my choice...) and everything works fine. 

I thought I might have some weird BIOS problem, so this morning I reset it. No change. Looking around on the Biostar site I found an recent application to flash the BIOS, but it runs under Windows (no separate BIOS available). I might try it tonight when I return home (what do I have to lose at this point...). No separate BIOS file available to flash manually.

Sorry for being verbose, but is this a known issue, and is there a fix for it? I looked at the xorg.conf, but the display parameters aren't in that file anymore. I have limited ability to look under the hood, if anyone can help me solve this issue I would appreciate a whole lot  ](*,)

BTW I tried to install OpenSuSe 11.1, same issue (and the sound didn't work either).

Thanks,

DC

---

### Post by coffeecat on 2009-05-12
I recently ran the 8.04 live CD on a machine with the same CPU but, more importantly, the same (or nearly the same) AGP graphics chipset. It was connected to a 24" 1920x1200 flat screen monitor and the resolution set itself up correctly in the live environment first go. Which makes me wonder if the monitor is not putting out accurate (or any) [EDID data]("http://en.wikipedia.org/wiki/EDID"). Being a CFT that's more than likely. The versions of xserver that come with Ubuntu since a year or more ago (and other distros) rely on EDID information.

Two suggestions:

Have you got a fairly recent flat screen monitor you could try this machine + Ubuntu 8.04 live CD out on? I know it doesn't solve the problem, but at least you'll be able to see whether that graphics card will indeed support a resolution greater than 800x600.

If that works, I guess you'd have to add some mode lines to xorg.conf manually. I haven't done this for some time, so I'll need to look something up and post back, but in the meantime please post the best resolution of that CFT monitor. Also the Horizontal and Vertical sync values if you can get hold of them. You have to be more careful with CFT monitors when editing xorg.conf.

---

### Post by dchenard on 2009-05-12
Thanks for the quick response, you might be on to something here.

Yet I'm not sure this is the solution (but I'm willing to run tests here until the problem is solved). I'm saying this because I have connected a number of machines to that monitor (through a KVM switch), and none other than that one has given me grief. My main machine is an Athlon X2 6000+ on an Asus MB and a GeForce 8800 GS, and my secondary machine is an Athlon XP 2700+ on another Asus MB and a GeForce 6800 Deluxe (NOT the 6800 from a couple years ago, but the model released before the GeForce2 cards ten years ago). Both these machines run OpenSuSe 11.1 (one 32 bit, the other one 64 bit), and they both run fine. And it's not an issue of Ubuntu vs. SuSe, I tried SuSe on my trouble machine and it didn't work either.

In order to eliminate the KVM as a potential problem source, I'm connecting the Ubuntu machine directly to the monitor. I noticed that the image is shifted to the right on the monitor (hiding half of the shutdown button on the Gnome desktop), so the EDID suggestion might be right (but why only that machine?:confused: )

One final oddity, as I received the machine the BIOS was set with PCI as the "output", even though the video card that came with it was AGP. I haven't tried reverting that item back (I did switch it to AGP when I started working on the machine), not sure this will change anything...

Thanks for all the help, greatly appreciated.

DC

---

### Post by dchenard on 2009-05-12
Forgot to mention, I also tried Jaunty, and it did not go through the install (either switched to character mode or froze)

DC

---

### Post by coffeecat on 2009-05-12
> **dchenard said:**
> but why only that machine?:confused: )

Perhaps an obscure bug with that particular graphics chipset and the 'nv' driver? On second thoughts, I'm not sure the machine I mentioned did have that exact graphics card, but I'm sure it was Nvidia MX4-something.

> **dchenard said:**
> Forgot to mention, I also tried Jaunty, and it did not go through the install (either switched to character mode or froze)

DC

I managed to get Jaunty installed, but by then we had put a newer graphics card in, which leads me to another suggestion....

Have you got a more recent nvidia AGP card you could at least try out in the machine that's giving you trouble? Perhaps one of the cards that gives you correct resolution with that monitor in another machine? That way you could see whether it is the card rather than the monitor that's the problem. And, if so, perhaps you could get a better/more recent card for the refurbishment.

---

### Post by dchenard on 2009-05-12
I did try another GeForce card before trying the MX (forgot to mention that...](*,)), a GeForce FX5200, same result.

The monitor itself is as old as the GeForce 6800 mentioned above (bought them at the same time), why it would work with all the other machines except that one is puzzling...


When I get home tonight I'll try swapping monitors (I have a LCD one still in the box), we'll see if that changes anything. If that doesn't work I'll try flashing the BIOS.

Maybe in the end I've been terribly unlucky and managed to use two defective GeForce cards...

Thanks again,

DC

---

### Post by dchenard on 2009-05-12
I'm writing this using an Acer AL1715 LCD monitor, and lo and behold, it works! Initial resolution was 1280 x 1024, too small for my declining eyesight, brought it down to 1024 x 768...

So it was the monitor that was the problem... Now, I'm not giving that LCD monitor away to my wife's friend's daughter, so I have to find a plan B... 

Thanks for all the help, =D>

DC

---

### Post by johnlvs2run on 2009-05-12
The Ubuntu resolution did not adjust with my Biostar motherboard and Nvidia.

I moved to Sabayon and the resolution is perfect.

[http://ubuntuforums.org/showthread.php?t=822315&page=5](http://ubuntuforums.org/showthread.php?t=822315&page=5)

---

