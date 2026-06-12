---
title: "nm-applet slow detection of wireless"
date: 2009-05-07
forum: Hardware
---

### Post by jonathanmotes on 2009-05-07
Hi all,

When I boot, I have to wait a minute or so before nm-applet shows any wireless signals or shows that it is trying to connect to any. I'm running Jaunty and didn't have this issue with Intrepid. 

From *lspci*, my wireless card is an Intel Corporation PRO/Wireless 3945ABG.

I'm using a Dell Inspiron 1420 laptop.

Thanks for the help!

---

### Post by jonathanmotes on 2009-05-08
Has anyone had this issue? Thanks :)

---

### Post by NilsE on 2009-05-08
I noticed the same issue but it is very inconsistent.  Sometime it is slow to connect and sometimes it is fast but it always connects so I don't complain.

The delay is always between when the "no network connection" icon shows and when it starts connecting.

I should add that I think it has to do with the fact that I have 3 ways to connect: wired, Verizon air card, and wireless.  I think the delay is nm-applet trying to figure out which one is active.

---

### Post by jonathanmotes on 2009-05-09
Thanks for the reply NilsE! 

Actually, the behavior you describe is exactly like mine. It does connect properly from time to time, and like for you, "The delay is always between when the "no network connection" icon shows and when it starts connecting."

I only have Ethernet and the wireless, so I would think we are both experiencing the same issue.

---

### Post by misiu_mp on 2009-05-09
I have a similar problem with slightly different symptoms. 
Directly after boot, the nm starts connecting but it takes long time and fails in the end.
I have to disable wireless through the applet and enable it again. Only then I get a connection.
My card is also Intel PRO/Wireless 3945ABG in a hp Compaq 6510b. I connect to a WPA2 Personal network and there is no other connection or network hardware except for Ethernet.

Together with problems with GM965 graphics ([https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392)) this is a total failure. Intel really sucks this time. They put experimental drivers in a release kernel, those bastards! Ubuntu should act sooner and reverted to earlier versions. 
I have a Mint Elissa livecd (based on 8.04) and there all of these work perfectly.

---

### Post by jonathanmotes on 2009-05-09
> **misiu_mp said:**
> 
Together with problems with GM965 graphics ([https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392)) this is a total failure. .

I just wanted to point out that bug 359392 was actually fixed recently! This bug has been a major show stopper for me also, but I can now use Compiz without freezing (I had to manually un-blacklist the video card though). The driver still has some performance issues after running for a while however (a related, still unfixed bug). I got frustrated with it the other day and turned Compiz back off.....

---

### Post by dthuk on 2009-05-12
I can confirm that I also experience exactly the same problem as Jonathanmotes. nm-applet simply sits there showing no connection for a minute or so, then finally decides to connect. It never fails to connect once it gets around to trying so it's only a nuisance really.

I also have Intel 3945ABG wireless chipset. The machine is a Dell Inspiron 6400.

---

### Post by dthuk on 2009-05-12
I changed over to wicd and now the connection is immediate on startup!I guess this is a network manager problem then.

It doesn't explain the cause of the problem but does at least get me started quickly now. As it happens, wicd seems much nicer to use, so I'll think I'll be sticking with it.

---

### Post by jonathanmotes on 2009-05-14
> **dthuk said:**
> I changed over to wicd and now the connection is immediate on startup!I guess this is a network manager problem then.

It doesn't explain the cause of the problem but does at least get me started quickly now. As it happens, wicd seems much nicer to use, so I'll think I'll be sticking with it.

Thanks for the tip! I installed Wicd myself and it is working great :)

---

### Post by travtek on 2009-05-14
I have the same problem with jaunty on my lenovo z61m laptop.  It also uses the 3945abg wireless card.  I also have Debian installed on the laptop.  I recently upgraded Debian to unstable and the slow wireless detection happens in Debian with the 2.6.29-1 kernel.  If I boot Debian unstable using the Lenny kernel 2.6.26-2 it works fine.  So it may involve a problem with the kernel module.

---

