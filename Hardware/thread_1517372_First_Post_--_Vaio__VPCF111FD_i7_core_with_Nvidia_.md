---
title: "First Post -- Vaio  VPCF111FD i7 core with Nvidia 310M -  No acceleration"
date: 2010-06-24
forum: Hardware
---

### Post by Aloon on 2010-06-24
Greetings:

This is my first post after reading a bazillion threads here. Thanks for all the helpful advice that has helped so much in the past. Long live open-source.

I recently bought a new laptop. I got an excellent deal on a Sony Vaio i7 core. The model number is VPCF111FD and it has the 310M Nvidia card.

Originally it had windows 7 and I at first dual-booted it with 10.4. I worked out some of the obvious problems like no sound , 64 bit flash etc so I decided to install Lynx only on the hard-drive and get away from windblows altogether (haven't used microsoft since the mid-nineties). 

Everything went fine and then I realized that the hardware driver that jockey recommends doesn't work for my 64 bit 310M setup. After a bunch of reading I tried all the recommendations about editing xorg.conf with the appropriate lines. When I reboot I got the split screen that many people mention.

I got rid of the split-screen by starting again. Somewhere between trying again and an update of xorg-server-core , when I boot now I get my 16:9 display , my monitor section says "laptop" instead of "unknown" and I get dozens of different resolution settings including 1600 X 900.

So i'm happy at least i've got everything except hardware acceleration on the video card ,  now I just need to focus in and solve that problem ...

Can anyone help me problem solve getting the Nvidia 310M accelerated on a Vaio FPCF111FD i7 core ?

I can dig up and link all the various methods I've tried. In some cases I reinstalled Ubuntu just to make sure that previous attempts didn't leave things broken.

Thanks very much in advance.

---

### Post by Aloon on 2010-06-25
Thought i'd mention:

Everything is running good except the Nvidia 310M hardware driver. I think one of the updates may have helped. That or uninstalling all the Nvidia instances and then trying the xorg.conf EDID additions.

Video tests show FGLX gears rotating , all the other video tests passed. I get my 16:9 at the nice resolution. Everything seems good except that driver.

I don't play video games or do anything that really requires much 3d acceleration so I'll be fine as is , but if it would tweak the appearance of the desktop or make videos run better than I'd like to get that 64 bit Nvidia driver going for the 310M.

Any help greatly appreciated.

Thanks

---

### Post by cegem on 2010-09-20
hi there,

 could you mention how you got the sound working, i have the same laptop and i couldnt find anything to get the sound working..

Thanks

---

