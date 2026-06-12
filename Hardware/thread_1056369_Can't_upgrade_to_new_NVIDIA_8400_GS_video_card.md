---
title: "Can't upgrade to new NVIDIA 8400 GS video card"
date: 2009-01-31
forum: Hardware
---

### Post by telcomguy on 2009-01-31
I've done a lot of research but still can't seem to solve my problem.  I have an HP desktop with on-board video and I'm trying to install a new PNY GeForce 8400 GS video card (standard PCI slot).  My BIOS automatically recognizes the card and disables the on-board video.  If I simply let 8.10 boot up, things go normally until I get to what would normally be the login screen.  At that point I have a garbled display and my keyboard is locked out.  I went into recovery mode and tried to run sudo dpkg-reconfigure xserver-xorg, but got a "read-only file system" message.  So, I rebooted, went into to recovery and did a "mount -n -o remount, rw /" then the dpkg-reconfigure statement.  That seemed to work, though I was only prompted to change my keyboard configuration -- no questions about video.  When I try to reboot, the system hangs with either segmentation faults or messages like "rc-default main process (4287) killed by SEGV signal".  If I remove the card and return to the on-board video, everything works fine.  Am I out of luck because of a hardware incompatibility or is there a work around?

---

### Post by compabeto on 2009-02-05
Hey telcomguy,

I am in a very similar situation as you, and so is this guy:

[http://ubuntuforums.org/showthread.php?t=1026257]("http://ubuntuforums.org/showthread.php?t=1026257")

We have the same card with similar computers, HP with onboard graphics. I also have issues like yours. I can not boot into Ubuntu with the card. There are success stories with this card on these forums, but they all require that you can boot into Ubuntu. This leads me to believe it might be an incompatibility with the HP hardware.

For now I am going to try other distros, maybe they will work. I will see if I can contact some developers about this problem.

---

### Post by telcomguy on 2009-02-15
compabeto,

Thanks for the reply.  I guess I'm glad it's just not me.  I was thinking about trying other distros as well, but haven't had the chance.  Please post if you have any luck.

---

### Post by compabeto on 2009-02-16
I tried Debian but didn't work, which I guess makes sense, it being the predecessor to Ubuntu. I also tried Fedora 10, which I am (sometimes) able to boot through the LiveCD. I installed it a couple of times, and most everything works, but I can never successfully shutdown the system, it just comes up with segmentation faults and hangs during the shutdown procedure. You might have better luck. I feel like the more stuff I try, my computer gets worse and worse, and I tried going back to my onboard video, but I think it's failing. 

I'm going to try and update my BIOS just for the hell of it, even though I am lead to believe my hardware is just dieing.

:(

---

### Post by kdardio2415 on 2009-03-29
I'm in the exact same boat as the OP (HP desktop, 8400 GS etc).  If anyone has any ideas other that hardware incompatibility, please interject.  I was hoping to get some dual screen action eventually, and I'd hate to have wasted money on a new card.

---

