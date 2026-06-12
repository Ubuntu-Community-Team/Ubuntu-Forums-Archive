---
title: "Issues with HP Compaq nx9110 Laptop &amp; Hoary 5.04"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by Spyd on 2005-04-21
Hi all. Before I whine about my troubles, I need to say, that Linux changed my computer world view, and the hard work that went into building my debian systems and solving compatibility issues in Fedora and the wonders of Knoppix, all made my discovery of Ubuntu a great experience, Not only did the os encompass all the features I loved about other linuxes but it came with an Ideology that I could live by. So with that said, To authors, tester, users and supporters, Thanks so much for Ubuntu, I Actually erased my windows permanently. 

Now, the sad parts.

My main box is now my nx9110 laptop, and its what I use daily for writing my university papers, watching my RSS TV etc etc. There are only a few unsolved issues with my laptop that I have not been able to solve myself, so here goes.

External RGB Port
Internal 802.11g wireless
sound 
Numlock.

So, my problem with External RGB port is this: I use this laptop as my tv, and project PDFs on the wall for study groups, at least I did in windows, SInce Ubuntu, I have been unable to use my projector, it seems that the FN-f4 which used to switch to my external monitor port no longer works. I tried using Xev and it appears as though this key does not actually work under ubuntu, others do but this one doesnt. I have tried installing binary drivers for my vid card (radeon 9000) but all I managed to do was configure myself in the corner when I chose a gl screensaver with a one minute wait that managed to lock the hardware solid when it ran, so uininstalled it and went back to default drivers. Again, my video is ATI radeon mobility 9000 IGP. Any advice on this would be great, the difference between 6foot screen dvd and 1 foot is well..... enuf said :)

Internal a/b/g wireless- upon install ubuntu detected a broadcom  wifi adapter but could never make it work, I tried the hard way with NDISWRAPPER and it too never worked, I even built NDISWRAPPER form source, still no go, any suggestions here would be welcome.

Sound- I finally have sound working but it was a chore and required that i disable the detection of the ATIIXP modem driver detected by alsa, it seems it was causing issues, so now alsa works, but if I run teamspeak, absolutely nothing can be using the sound or it wont work, and even when nothing is using it it will sometimes lock on connection. The sound seems to be well, in need of some redesign, I still havent figured our how ESD is supposed to make things work better. Regardless, I cant really use systems sounds so I dont, Mp3s and Movies play fine. Sound is currenly working via alsa using my ATI IXP AC97 drivers

Lastly, my numlock. Yeesh, I read in the unofficial howto a way to make the numlock key be ON when gnome fires and I did it but I still have to hit numlock everytime, I use an external wireless logitech mounse and keyboard (USB) and it seems to be detected ok by ubuntu, but I really hate having to turn on the numlock so any directions there would be welcome.

I have entered my system into the ubuntu hardware database using the tool provided, and I dont know what else I can do to assist the developers to suport my hardware, but if you want I will try just about anything (Since I have happily partimaged my partition onto a backup server :)

Regards to the Ubuntu community, thanks for such an Awsome OS!!!!
Spyd

---

### Post by eric222 on 2005-04-22
Spyd, I have an HP zv5034US laptop and I think I have similar hardware.  I was able to get my sound (ATIIXP) working using the instructions in these 2 threads:

[http://ubuntuforums.org/showthread.php?t=26567&highlight=sound+hoary](http://ubuntuforums.org/showthread.php?t=26567&highlight=sound+hoary)
[http://www.ubuntuforums.org/showthread.php?t=25548](http://www.ubuntuforums.org/showthread.php?t=25548)

I was able to get my Broadcom wireless working using these:

[http://www.ubuntuforums.org/showthread.php?t=9454&highlight=ndiswrapper+broadcom](http://www.ubuntuforums.org/showthread.php?t=9454&highlight=ndiswrapper+broadcom) 
[http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation)

I used the  bcmwl5a.inf and bcmwl5a.sys files from the Windows drivers for my wireless.

Enjoy!

---

### Post by Spyd on 2005-04-25
Thanks Man!! , I have tried these things with some success, My sound is behaving very nicely now, but i have no system sounds but i am really happy that its behaving, I can live without pops and clicks from the interface :) I will wait for breezy before I sort out the rest of the sound issues. 

 I also made some headway with the external RGB Port. I discovered a feature of the radeon driver that will clone the output of one port to the other,
so i reverted back to the radeon driver in xorg.conf and put the line:

```
Option "CloneDisplay" "1"
```

In the device section of my video card this has enabled the external RGB port, It is my understanding that this feature is for dual head Vid cards with a digital and an analog, and that on a laptop the laptop screen is treated as digital port and external is the analog and so usually this option is used to clone one to the other, regardless it seems to have worked, , however, it behaves oddly, if I boot the machine with the projector attached to the laptop, it will only display on my projector, and to get it back on the laptop screen i must restart the system (I could probably just restart X but my system does not like to switch to init 3 for some reason-havnt worked it out yet) 

SOooo, if I boot without the projector and plug it in and leave it, I can always turn on projector and see the output on both, but if I forget to unplug the projector before I restart, I loose the laptop screen. At any rate, Thanks eric222 for your advice! and if anyone has any more radeon tricks for my laptop, im all ears, meanwhile if I find any more Ill post here :) 

Have you hugged your Ubuntu today? 
SpyD (1 Month M$ Free)

---

### Post by shadow07 on 2005-09-24
Well, I have a HP Compaq nc8000, which has the Mobility Radeon 9600.  The ATI Linux drivers install  on my machine.  However, it is rather anoying to launch the ATI Control Center, adjust the clone display option, and have to restart X, or reboot the machine.

Things like this anoy me, and I wish there was an easy way to accomplish this.

I'm all ears too for suggestions.

---

