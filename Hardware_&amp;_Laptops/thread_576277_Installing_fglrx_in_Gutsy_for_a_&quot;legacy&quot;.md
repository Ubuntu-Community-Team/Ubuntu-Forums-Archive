---
title: "Installing fglrx in Gutsy for a &quot;legacy&quot; ati card (radeon 9000)"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by vemon on 2007-10-15
Hi!

I have a radeon 9000 card and I'd like to get it's tv-out working (with overscan) in Ubuntu Gutsy. It seems the only way to accomplish this is to install the ATI Proprietary driver (fglrx). I first tried to install the fglrx driver from ubuntu repositories but it's too new to support my "Legacy" ati card. The correct version of the driver would be 8.28.8 (at least according to the ati driver release notes).

Is there an older version of the driver available in the ubuntu repositories? Or has someone managed to install older versions of fglrx to Gutsy by using the ati installer? It seems that the 8.28.8 version of fglrx only supports xorg up to the version 7.1 but Gutsy has version 7.2.

Any help would be greatly appreciated!

- Jaakko

---

### Post by dodgydavec on 2007-10-15
I'm having a very similar problem to this. Everyone ends up saying install xorg-driver-ati or get a new graphics card. I can't get a new graphics card right now, and I can't find xorg-driver-ati. Dead end for me. Hope you have more luck.

---

### Post by vemon on 2007-10-15
I think the "xorg-driver-ati" you are referring to is the "ati" driver for xorg and is installed by default. If you can settle for 2d without tv-out then you can use either that or "radeon" driver (which is also installed by default) depending on the model of your ati card.

---

### Post by vemon on 2007-10-15
I finally got radeon 9000 + fglrx + tv-out with overscan working! The solution was a script made by the Kanotix distribution author (Kano). The solution is described in this thread: [http://www.phoronix.com/forums/showthread.php?t=4400](http://www.phoronix.com/forums/showthread.php?t=4400)

Direct download link to the fglrx installation script: [http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)

The script automagically detects the correct driver version for your card. I ran it with the -y option and it patched the driver to work with xorg 7,2. In addition to this script the xorg.conf should probably be edited using aticonfig (I had already done it prior to running the script)

NOTE: Seems like there is no 3d support with this approach!

---

### Post by beuk on 2007-10-19
I have a Thinkpad T40P also with the FireGL 9000. The only laptop without a "superkey" :S

I searched and searched for a solution, but can't find anything working.

I just installed compiz, and it works great! But when I install the xorg-driver-fglrx compiz doesn't start anymore.. I think it has something to do with 3d functionality missing ?

What I want:
- Use 3D (Compiz as window manager) 
- watch movies/dvd's on my tv via the TV-out connector.

What driver do I need to use ? I read about official ATI driver, an Xorg driver or another opensource ati driver? I'm really confused now. Does someone knows how to get it working?

---

### Post by Dr.Suave on 2007-11-11
> I finally got radeon 9000 + fglrx + tv-out with overscan working! The solution was a script made by the Kanotix distribution author (Kano). The solution is described in this thread: [http://www.phoronix.com/forums/showthread.php?t=4400](http://www.phoronix.com/forums/showthread.php?t=4400)

Direct download link to the fglrx installation script: [http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)

I'm trying to update my Radeon 9000 mobility driver.

I'm completely new to this, so I'm probably did something wrong - but when I tried to run the "install-fglrx-debian.sh" script I got this:

```
wilf@ubuntu-laptop:~/Downloads$ chmod +x install-fglrx-debian.sh
wilf@ubuntu-laptop:~/Downloads$ sh install-fglrx-debian.sh
Error: No KANOTIX found. Do not ask for support!
Error: No ATI RADEON/FIREGL adapter found.
```

I thought I'd break the rules and ask for help anyway - where am I going wrong?

Thanks a lot
Wilf

---

