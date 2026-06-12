---
title: "Updrading to 9.04 boots in tty, not kde?"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by capitales7 on 2009-05-11
Hello all. I'm a relative novice linux user, but this is first time I've done an upgrade... and I'm slightly confused as to why kubuntu 9.04 boots up into a tty instead of loading KDE.
I upgraded my work pc to 9.04 just fine, but now my home machine this happens.

I have a feeling that the answer is so "DUH", but I'm still learning... please help! :)

Thanks.

---

### Post by capitales7 on 2009-05-18
someone help :(!

---

### Post by SuperSonic4 on 2009-05-18
It's likely to be a graphics card issue. Do the two systems contain the same graphics card?

---

### Post by capitales7 on 2009-05-18
> **SuperSonic4 said:**
> It's likely to be a graphics card issue. Do the two systems contain the same graphics card?

It's a virtual machine running off my vista (yuck :p) host OS. So yes, same gfx. It worked fine with 8.10, but 9.04 does this.

I attached 2 screenshots. One shows it booting up as expected, then the next is all I can see, and the error when i do "startx".

---

### Post by taurus on 2009-05-18
Did you install a driver for your graphic card when you were still running 8.10?  

Otherwise, log in with your username and password.  Then reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by capitales7 on 2009-05-18
> **taurus said:**
> Did you install a driver for your graphic card when you were still running 8.10?  

Otherwise, log in with your username and password.  Then reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

I never installed a driver. I tried installing one now, but it's proving difficult.
Sadly, reconfiguring didn't help! :(
I also tried downloading and installing the driver from the nvidia site, but it didn't seem to detect that I have an nvidia card, perhaps because its a vm box?

---

### Post by raynevandunem on 2009-05-20
I would like to bump this with a similar issue. I upgraded to Jaunty (its a Wubi dual-boot) a few days ago, and when I restarted, it went into tty1 login and I have also tried startx and other procedures mentioned on here. ALT+F7 and CTRL+ALT+F7 don't work, neither do going into recovery mode for xfix or removing "quiet splash" (which reappears no matter how many times I remove it before resuming the boot). Basically, I'm SOL until I can find a solution, and I haven't messed with any drivers at any point throughout this process; even Intrepid wasn't as difficult when I upgraded to it from Hardy.

---

### Post by capitales7 on 2009-05-20
> **raynevandunem said:**
> I would like to bump this with a similar issue. I upgraded to Jaunty (its a Wubi dual-boot) a few days ago, and when I restarted, it went into tty1 login and I have also tried startx and other procedures mentioned on here. ALT+F7 and CTRL+ALT+F7 don't work, neither do going into recovery mode for xfix or removing "quiet splash" (which reappears no matter how many times I remove it before resuming the boot). Basically, I'm SOL until I can find a solution, and I haven't messed with any drivers at any point throughout this process; even Intrepid wasn't as difficult when I upgraded to it from Hardy.

Best thing about my VM setup is that I can easily revert to previous snapshots! :D
I kinda gave up on it as I can't install the nvidia drivers since the VM doesn't recognize the host gfx card as an nvidia one... 8.10 will do fine for now :)

---

