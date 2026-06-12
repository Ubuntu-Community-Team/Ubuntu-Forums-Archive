---
title: "HP Pavilion dv5220ca with ATI Radeon X200M"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by lunaticchannel on 2006-12-13
Hey, I was just wondering if anyone else out there was running this HP Pavilion laptop (dv5220ca) or the dv5000 series. It came with an ATI Radeon Xpress 200 ***[-( *** series graphics card built on the motherboard. I've been trying to weeks now to get the 3d acceleration to work properly. Just recently I found out I had to change the BIOS to share an additional 128Mb of memory with the video card, just to not get a black screen when booting up Ubuntu. I'm running Ubuntu 6.10 (Edgy), and I've got Beryl running at startup and supposedly working, but the 3d desktop doesn't work. I can't even see the Beryl splash screen at startup. ](*,) 

Anyway, I haven't been able to figure it out for awhile and if anyone could give me some advice that would be awesome.;) 

Thanks

---

### Post by TusharG on 2006-12-14
ATI Radeon XPRESS 200M cards as of now doesnt work with Edgy but it will work properly with Ubuntu/ Dapper. You can follow my post [http://tusharg.blogspot.com](http://tusharg.blogspot.com) for details. I'm also waiting for ATI to release the drivers that will work with xorg 7.1 with 200M cards on Ubuntu Edgy. 
 Today I saw ATI has released 8.32.5 drivers but they have not yet posted a release nots, so not sure if they are covering 200M cards this time or not. The only drivers that worked well with our cards was 8.24

---

### Post by lnxusr on 2006-12-14
The recently released 8.32.5 drivers should work well with that card, I was able to get it working on Kubuntu dapper and am about to test it on edgy. My laptop is an HP Pavilion DV5212us with the notorious ATI Xpress 200M and sideport memory. In addition to actually working, the new driver should also work fine with pure sideport memory, I've got full 3D accel and full system access to my gig of ram. I put together some scripts that should streamline the install of the new drivers:

Dapper:
[http://lnxusr.phpnet.us/ati-8.32.5-builder.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder.sh)
Edgy [see below]:
[http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh](http://lnxusr.phpnet.us/ati-8.32.5-builder-edgy.sh)

The scripts will automatically download, build, install, and configure the 8.32.5 drivers. You may need to chmod +x ati-8.32.5-builder.sh or ati-8.32.5-builder-edgy.sh before running it. To run it, just enter sudo ./ati-8.32.5-builder-edgy.sh or ati-8.32.5-builder.sh. 
Also you may need to unlock certain repositories in /etc/apt/sources.list.

In order to get 3D acceleration working in edgy, add the following lines to your xorg.conf file:
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection
```

XGL/Beryl is working great! Now if only they'd add AIGLX support I'll stop wanting to strangle some ATI execs.
The scripts are based in the information found at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
Hope this helps.

---

### Post by Adler on 2007-01-04
lnxusr,

Thanks for your post. It does indeed work with the POS ATI Radeon XPress 200M card.

I keep trashing my system -- [Linux Mint]("http://lt.k1011.nutime.de/about.html") -- trying to get all the newest bleeding edge Ubuntu Feisty stuff, and always come back to your script when I re-build. 

Cool! And, thanks.

Adler

---

