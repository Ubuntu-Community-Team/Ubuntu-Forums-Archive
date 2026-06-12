---
title: "builtin sdhc reader on r3000 not recognized"
date: 2009-01-27
forum: Hardware
---

### Post by ubuntumaybe on 2009-01-27
Hi,

I have a Compaq Presario R3000 with a builtin SDHC card reader. My 16gig card can be seen by windows but not ubuntu. When I try the usual commands, lspcmcia, lspci the card slots are reported as Texas instruments. When I insert the card then check the output using dmesg there is no message returned. I have read other posts and tried loading the tifm modules but nothing works. I was wondering if anyone knows of a windows app that I can run in wine that might force the card to be recognized. THanks.

---

### Post by Dakiraun on 2009-04-16
Surprised no one answered this.  The card reader in the R3000 was briefly supported in earlier Ubuntu's, but a kernel change broke it again.  I have one of those laptops myself. :/  Problem is that the card reader isn't a very good one to begin with, and half the time the Windows drivers don't work right for it either.  The reader on mine does nothing but Blue-screen Windows if I try to use it now anyway.  Since it doesn't support most of the newer card types, and isn't as fast as the USB 2.0 trasnfers you can do off most of the devices, I wouldn't worry too much about it.  The biggest barrier that I've had in getting Ubuntu on the R3000 has been video drivers - mine has a nVidia 440 GO GPU, and media playback like DVDs is horrible.

---

### Post by ubuntumaybe on 2009-04-16
Hi Dakiraun,

Thanks for responding. I eventually bought a usb 2.0 sdhc reader real cheap on ebay and it works great. Since you have the r3000 do you have the problem with the loose power adapter. If so how did you fix it. I have tried many forums including tomshardware but the only suggestion coming from people is to buy the xc100 cable - expensive. Thanks.

joe

---

### Post by Dakiraun on 2009-04-22
> **ubuntumaybe said:**
> Hi Dakiraun,

Thanks for responding. I eventually bought a usb 2.0 sdhc reader real cheap on ebay and it works great. Since you have the r3000 do you have the problem with the loose power adapter. If so how did you fix it. I have tried many forums including tomshardware but the only suggestion coming from people is to buy the xc100 cable - expensive. Thanks.

joe

Yes - a card reader was the better solution for me as well, heh.

Interesting you mention the power issue: I just fixed that 2 weeks ago, though mine was more a problem of the laptop going into battery mode constantly even though the cord was plugged in.  

I've seen two different plug issues with this model, and often people refer to them as a loose plug.  If the plug itself really is loose (as in, it wiggles around in the socket and won't stay in), you need to get a replacement socket housing for it, which you can get on E-bay for very cheap.

If you have a problem like I did where it keeps going to battery, but the plug seems to be securely in the socket, then you have a fractured solder on the socket housing to the motherboard.

In BOTH cases, you will need to disassemble the laptop nearly entirely to be able to get the motherboard out and fix the problem.  There are guilds available on how to do it from HP's site, and it just takes a little time and patience.  If you have the problem I did, you just need to use a soldering gun (and perhaps a tiny bit of extra solder) to re-solder the three contacts the power socket housing has on the motherboard.  The centre one is usually the one that causes that particular problem.  

If you have the other issue, then you have to use a soldering gun to melt/remove the solder from the old socket, remove it from the motherboard, then solder in the replacement socket.

Like I said, takes a little time and patience (and I strongly suggest a magnetic dish near by so you don't lose the insane number of screws that need to come out) but it's not that hard to do.  Drop me an e-mail to dakiraun [at] yahoo.com if you need any other help with that (I check that multiple times a day, vs. only checking this forum from time to time).  Good luck.

---

