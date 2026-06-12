---
title: "Graphics fail on bootup"
date: 2009-05-18
forum: Hardware
---

### Post by andybusse on 2009-05-18
Hi,

Just installed 9.04 successfully (I know this because I managed to restart it and it worked fine), but one website advised the way to get around the fglrx (I think that's how it's spelt) problem was just to go to hardware drivers and enable the driver. 

I now realise this was a stupid error, but due to other posts on this forum saying that AMD (I am using a Radeon Xpress 200M, somehow classed in the X300 series) had released a working driver for Jaunty, I downloaded the one from their website, installed it in 8.10 (success), then done what I mentioned above.

The problem I get is that when I boot (either of the two versions of 9.04 that I am presented with in GRUB menu), the loading bar appears, fills in about 15 seconds, then it flickers a black screen with purple, green and white lines 3 or 4 times before settling on another similar screen. If you like, I can take photos of the fail, but I'm unsure of the rules regarding photos on this forum.

Thanks to anyone who can help me solve this problem.

(NB: I can use recovery mode and it can give me a command line, but I do not know which (if any) commands to give it)

---

### Post by skymera on 2009-05-18
Your graphics chip is not supported by AMD on Jaunty.

You will need to use the open-source driver or stick to an earlier version of Ubuntu.

EDIT: 2,500th post :D:D:D:D

---

### Post by andybusse on 2009-05-18
Thanks, but how do I either revert back to 8.10 (it doesn't appear in grub, and I don't really want to lose the stuff I've got on there, even though it's backed up), or find a way of deselecting this driver from recovery mode?

Also, is the open source driver included in Jaunty or will i have to fetch it from somewhere (if so, how?)

---

### Post by skymera on 2009-05-18
You need to reinstall Ubuntu 8.10, there is no down grade option.

I would show you how to change your Xorg.conf to enable the open-source driver, however i'm at college and on XP :(

---

### Post by andybusse on 2009-05-18
Tried this command for both versions of 9.04 in recovery mode root shell prompt (i think that's what it was called), as advised by skymera in a PM:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Now, I get a similar, but different screen of misery on bootup.
Any advice that lets me keep ubuntu pretty much as it is (i.e. that avoids a complete re-install) would be greatly appreciated.

(PS: First time I've used Vista in weeks - it feels so slow :( )

---

### Post by sir.johneleth on 2009-05-18
Bit of a noob about this but is there no way you could use the recovery mode and boot to terminal / root and remove the nvida driver so it uses the standard one? as mine worked until i tried to install drivers, and i need to solve this.

---

