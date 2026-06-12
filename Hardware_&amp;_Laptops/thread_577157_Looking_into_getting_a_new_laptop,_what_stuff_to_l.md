---
title: "Looking into getting a new laptop, what stuff to look out for?"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by Amablue on 2007-10-15
I've been using my current laptop for about 2 years (and it was a year old when I got it) and it's age is starting to show. I'm looking into getting a new laptop. I have been for a while, but my urge to play Portal and the rest of the Orange Box has pushed me over the edge. 

I'll most likely be dual booting XP and (K)Ubuntu (I havn't decided which flavor *buntu to go with this time). I know from my experience with my Dell Inspiron to avoid Broadcom chips like the plauge. Is there anything else I should look out for? Which graphics cards are best for Linux? What other compatibility issues might there be?

Or, if you have any suggestions for specific Ubuntu freindly laptops I'm all ears too. I know that Dell has Ubuntu loaded laptops now, are those good for games? I'm aiming for around $500, so nothing too high-end. I just want to be able to run the Orange Box without problems. 

I glanced at the stickied topics, but they have too much info to wade through, if someone could point me in the right direction I'd appreciate it :)

---

### Post by bg1256 on 2007-10-15
Nvidia is much, much better than ATI, at least right now, when it comes to 3D acceleration.

I just bought a new gateway today from circuit city for 579.96, and you might want to check it out.

It has the broadcom chipset, but my last one had that as well. Ndiswrapper works fine, althought it does take some tinkering.

---

### Post by Amablue on 2007-10-15
I'll keep an eye out for NVidia then. Still, I'm sick of Broadcom stuff, I'd rather just avoid the hassle all together.

---

### Post by w5cgu on 2007-10-21
Watch out and read the manual if you can b4 u buy.

We just got a new Compaq and on the HP web site it states NOT to use Linux as it will not work.  Do not try for a dual boot as it will mess up Winbloz (it has that new useless new OS from Winbloz).

I am going to attach a USB drive and boot it for Linux.  Have not tried it yet but should work.

There big thing is that you will not be able to find drivers (video and sound) and again, it will mess up what ever that MS thing is.  I spent over a week just getting it to work with my wireless network in the house and I am retired from SUN Microsystems  as a HW engineer!

Good luck and read b4 you spend.

John

---

### Post by tempel on 2007-10-21
I had problems with getting the Broadcom wireless chipset running on my Dell laptop when i first installed Ubuntu, but it's all changed now.  Gutsy downloads and extracts firmware completely painlessly, as long as you can get a wired internet connection.

So sorry, i don't have much further advice for you, but the Broadcom shouldn't be so much of a problem any more.

---

### Post by steveneddy on 2007-10-22
Get one with nVidia graphics, or Intel onboard graphics and Intel wireless.

These are supported the best.

Have you looked at the fine offerings at system76?

There is almost one in every price range now.

I own a Serval Performance and I couldn't be happier with it.

It runs Gutsy 64 bit. Intel Core 2 Duo, 2 GIG RAM, 80 gig HD and USB, Firewire, DVD burner, awsome sound (if you have it plugged into speakers, onboard sound is a little weak) SD card reader, wireless, bluetooth.

All works. Even after the upgrade. 64 bit rocks.

:popcorn:

---

### Post by w5cgu on 2008-02-08
Using an external USB drive I have installed Linux on my C552us laptop and all works but the WAN interface.  I am still looking for a driver that will work with it.  If anyone has any thoughts please let me know as the system is not much good without the network interface working.

Thanks in advance,  John :(

---

### Post by avsa242 on 2008-04-30
> **w5cgu said:**
> Using an external USB drive I have installed Linux on my C552us laptop and all works but the WAN interface.  I am still looking for a driver that will work with it.  If anyone has any thoughts please let me know as the system is not much good without the network interface working.

Thanks in advance,  John :(


John,

Not sure if you're watching for replies to this anymore or if you've moved on or not, but I have installed Hardy on my mother's C552US and have gotten the WiFi (I'm assuming this is what you're referring to when you say WAN; sorry if you meant the wired NIC) to "work" with the b43 driver. I originally installed Feisty on it and, at the time, the bcm43xx driver was not nearly mature enough to be used. When Gutsy came out I tried it again, and it seemed as though it was fully functional, but the latency was for some reason atrocious. I just installed Hardy on it today which now uses the new b43 driver and it works *better* but it still after all this time has pretty bad latency. If I ping my router or repeater the latency is between 40 and 70ms where it should be about 1-2ms. It is an improvement but still can be difficult to deal with. Strangely, it seems to be affected by the Intel graphics and/or X.
Have you tried either b43 or ndiswrapper?

Cheers,
Jesse Burt

---

