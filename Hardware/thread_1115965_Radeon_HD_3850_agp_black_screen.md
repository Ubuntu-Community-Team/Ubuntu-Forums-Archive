---
title: "Radeon HD 3850 agp black screen"
date: 2009-04-04
forum: Hardware
---

### Post by erick713006 on 2009-04-04
hey everyone... im new to ubuntu. Im having a problem enabling ati acceleration. Every time i enable it and restart my computer, I get a black screen. Nothing happens it just stays black... i dont know what to do. Im using ubuntu 8.04. My graphics card is a Radeon HD 3850 AGP.

---

### Post by erick713006 on 2009-04-04
dump....

---

### Post by erick713006 on 2009-04-04
help plz....

---

### Post by Dakiraun on 2009-05-28
Yikes - I can't believe no one responded to this yet.  The problem is that the Radeon HD3850 AGP was a bit of a oddball card in that it was never meant to exist.  ATI/AMD had no plans to continue support for AGP cards up into that family, but because they outsource their production to other companies, many of those companies decided to continue with AGP, with the 3850 being the last (most powerful) card made for the AGP bus.

There's a wee problem though - normal drivers don't work with the card.  To make it work in Windows, you have to use "hotfix" drivers, which are usually provided on the CD with the card, or downloadable from the card's maker.  Unofficially (and you really have to hunt for them) you can also get ones from AMD/ATI.

Bigger problem: there are no drivers or support that I know of for any other OS.  In fact, I found this post while looking (as I do ever so many weeks) to see if anyone has figured out how to make this card work in Linux yet. :/  I would have never got it for my main PC had I known it was going to cause this kind of grief. :(

---

### Post by Kris_D on 2009-06-05
Anyone tried to install these drivers ([SIZE=2]ATI Catalyst™ Display Driver[/SIZE] v9.5):
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&#9001;=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English")

I want to upgrade my PC for AGP 3D card but I search a card supported by Ubuntu/Linux.

---

### Post by Dakiraun on 2009-07-11
I doubt that would work - they look to be the normal Linux drivers, rather than a hotfix driver - that's the same problem you face with Windows.  If you download the regular Catalyst driver, it doesn't work witht he AGP version of the card.

---

### Post by KingBongo on 2009-07-28
My brother is having the same problems with the Radeon 3850 chip set. Black screen with acceleration enabled. 

The card is a Sapphire HD3850 AGP, [http://www.datormagazin.se/tester/article249136.ece](http://www.datormagazin.se/tester/article249136.ece)

The computer is an old Compaq EVO D310, Celeron 1.7 GHz (Pentium 4), 1.2 GB DDR Ram. Yeah, I know the graphics card really is overkill, but it was cheap and possibly one of the best AGP cards ever made. It should work regardless. 

Does anybody know how to make the combo work on Ubuntu (now running 8.04, going to upgrade to 9.04 or 9.10)? I even tried to disable VGA in BIOS with no success. Did anybody try this new driver from AMD (Catalyst 9.7), [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.4&lang=English&rev=9.4&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.4&lang=English&rev=9.4&ostype=Linux%20x86)

What will work for sure? I really want to make this combo work. I am not a completely noob, but to much hacking won't work for me. Help would be appreciated.

---

### Post by KingBongo on 2009-08-01
Ok. I think I partly fixed this problem (Ubuntu 8.04) using a tip found in another thread,

apt-get remove fglrx*
apt-get install xorg-driver-fglrx
aticonfig --initial -f

which I believe loads and installs an open-source driver.

After that we can at least see what we are doing, :) But there are still issues. For example, it is not possible to change the screen resolution (now 1280x1024, 60Hz). If we try that the desktop background (and some of the upper bar) distorts and becomes greenish. Questions:

1. Why isn't it possible to change the resolution without issues?
2. How to find out if 3D acceleration is enabled or not?

Thanks.

---

### Post by ZxEfR on 2009-08-01
Dakiraun thank you!

Your post just saved me some money and a lot of crying LOL. I was just about to buy the AGP 3850.

My X800 just went out and I need a replacement/upgrade. I desperately wish to Play UT2004 in Linux with my P4 3.4ghz, 2gb ram, 8x AGP Alienware rig from 2004. My X800 actually worked to play UT2004 but not near good enough. Linux support for it was not good and now it's been dropped completely. Don't know if I'll ever be able to play UT2004 on this particular machine in Linux but would love to be able to. Any ideas for me on what card I should get? I haven't kept up with hardware for the past two or three years and it's hard to find info about my situation. Most have upgraded their whole systems so...........any info would be great. If I'm hijacking then no worries on an answer.

Update: I've decided on a GeForce 7950GT....got to the point where I got tired of researching and just decided to jump in.....LOL

---

