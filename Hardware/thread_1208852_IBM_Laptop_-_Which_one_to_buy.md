---
title: "IBM Laptop - Which one to buy ?"
date: 2009-07-09
forum: Hardware
---

### Post by huzefa_from_kuwait on 2009-07-09
Hello people,

I have had a few battery and display related issue's with the HP laptop I am currently using (DV 1000), now I wish to buy the latest IBM think-pad laptop (with VGA and everything).

Can anyone suggest me which one should I go for. I am looking for the one that would give me no hardware related issue's with Ubuntu 9.04 specially battery and display.

Thanks,

---

### Post by rainwalker on 2009-07-09
I just got a brand new W700 (the beastly one) and everything works flawlessly! I have it set up to dual-boot Vista and Ubuntu, one OS on each hard drive. Ubuntu reads the files on the Vista hard drive perfectly, but I don't think there's any way (yet) to get Vista to read newer Linux filesystems yet.
Anyway, here's the breakdown running Ubuntu, let me know if I missed anything:

Display: The Nvidia drivers listed in the Restricted Device Drivers window worked, but I went ahead and compiled the v185 ones according to [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978), either way you get the full 1900x1200 resolution. Compiz performs wonderfully with the 1GB of graphics memory. Screen brightness control works perfectly, too.
Battery: Obviously battery life on such a machine isn't going to be great, but it seems to be about the same in Vista and Ubuntu (around 2 hours). However, power settings in vista seem to take effect at the hardware level up until you log in, such as dimming the display during boot up and at the log-in screen. Not a huge deal, but beware of conflicts (I don't think there would really be any).
Sound: Works great (including PulseAudio), but again, settings in Vista seem to take priority in that if you mute the sound in Vista, it will be muted if you boot Ubuntu (I think, I've been a bit wary of testing it because it works the way it is now).
Wireless: I purposefully chose the Intel wireless card, because I verified that it would work in Ubuntu. Signal and connectivity is great, but the only thing I have to compare to is the old Dell Inspiron 8600 (4 or 5 years old), so obviously I'm going to be satisfied.
Bluetooth: Works perfectly as well, though for some reason it's turned on by default. I solved this by installing the Blueman bluetooth program, which in my opinion is leaps and bounds better than the default Ubuntu one anyways. I enjoy using bluetooth more in Ubuntu than Vista, too, because you can actually browse the contents of bluetooth devices.
Fingerprint scanner: I haven't figured out how to get it to work, but I don't know of any application that uses it, either. Logging in is really the only time I ever use it, and it's really not even that necessary. I'm sure there's a way to get it to work, though.
Other hardware: You can program the ThinkVantage button to do whatever you want (obviously there's none of the ThinkVantage software in Ubuntu). All of the keys work like they're supposed to, including the Function key (which for some reason is always switched with the Control key compared to ever other keyboard layout). The middle button for using the touchpad is treated like the middle mouse button on a laptop, rather than the scrolling thing in Vista, which is nice (you can't middle-click on things by default, it has to be enabled in Vista). All of the Function combinations work, including the ThinkLight. The universal connectivity switch that turns the wireless and bluetooth on or off also works. The webcam works without anything additional programs or drivers. There might be a way to make the color calibrator work, but I doubt it. Suspend/resume and hibernate work. Last but not least, the integrated Wacom digitizer (tablet) almost works; you can use it to control the mouse movement (though it is incredibly sensitive) but you can't click with it, and I haven't gotten around to messing with it because I don't use it that much.

---

### Post by huzefa_from_kuwait on 2009-07-11
Thank you rainwalker for you feedback, but W700 is far more costly than my budget, the maximum i can affort is T400 with 256 or 512mb vga.

Would there be any hardware related issue's with T400 ?

Thanks.

---

### Post by tgalati4 on 2009-07-30
I bought a used T43P for $250 US.  2 GB of RAM, everything runs well out of the box wiht Linux Mint 7 Gloria (based on 9.04).  Has an ATI graphics card, but since Linux doesn't have any intensive games (save Tux Racer and Tremulous), the open source ATI driver runs compiz effects.  Avoid the T41 and T42 as the graphics chips tend to warp.  The P model has some other higher end stuff over the standard T43.   Bluetooth, wireless, and sleep and resume work without any problems.

It only came with a 40 GB drive, but that was quickly remedied with a 320 GB PATA notebook drive.

Oh, it's ugly, but you can plaster it with Ubuntu stickers or large penguins.

---

