---
title: "Can't install Ubuntu 8.10, 8.04, or 7.10 on a 2002 Gateway"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by piroteknix on 2009-04-12
The other day, my friend brought his computer to me, asking me to "fix" it for him. I started it up, and it asked for a Windows XP CD. I assumed he deleted his operating system :rolleyes: . He couldn't find his Windows CD anywhere, and none of our friends had one, so I suggested Linux. At first we tried Damn Small Linux, which worked, albeit not the best, and it wasn't exactly what we were looking for anyway.

Next, I burned Ubuntu 8.10 to a CD and put it in. When I tried to install it, or tried "try Ubuntu without any change to your computer," the loading bar made it to the end, but the screen turned black after that, and then nothing else happened. When I tried running without changing the computer in Safe Graphics Mode, the desktop background image and cursor showed up, but nothing else. And when I tried installing in Safe Graphics Mode, the desktop background and cursor appeared, as well as a white window titled "Install." No text showed up *in* the window, but the cursor turned to the I-shape like text *should* be there.

After 8.10 didn't work out, I tried Ubuntu 8.04. I downloaded it, burned it to a CD, and tried it in the computer. But it did the same thing as 8.10. The farthest we could get was the desktop background image showing up in Safe Graphics Mode.

Then, a friend online suggested Ubuntu 7.10. It had similar results to the other two versions. When I tried simply starting or installing Ubuntu, the loading bar finished, but then the screen went black again, and nothing more.

What's going on? Am *I* doing something wrong? Or is it a problem with the computer? The computer is a 2002 Gateway Model No. MFATXNIN NMZ 300S.

This is my first experience with Linux, and at first I was really excited, but now I'm disappointed that it hasn't worked out (yet)!

---

### Post by tommcd on 2009-04-12
Is this your Gateway computer:
[http://www.recycledgoods.com/item/23870.aspx](http://www.recycledgoods.com/item/23870.aspx)
According to that page, it only has 256mb RAM. That may be why you are having problems with the live CD. It also likely explains why DSL installed ok.
Try the Ubuntu 8.10 32 bit alternate install CD. Or even the Xubuntu alternate install CD. This will likely work, since that Gateway is an Intel system. The alternate install CD is a text based installer; but it is pretty easy to follow.
If burning the CD from Windows, use Iso Recorder or Indra Recorder, and burn at the slowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
You friend should consider upgrading the RAM in that machine if they intent to use it for a while. 1GB RAM would be the sweet spot.

And welcome to the Ubuntu forums!

---

### Post by piroteknix on 2009-04-12
Thanks for the advice! I'll try out the 8.10 alternate installer and tell you how it works out.

---

### Post by piroteknix on 2009-04-16
Ok, the installer worked out great! ...but, you're right, the computer doesn't have enough RAM to actually do anything in Ubuntu. Thanks a lot for your help, I'll tell my friend to get more RAM :)

---

