---
title: "ATI Radeon 9100 IGP: No S-Video"
date: 2008-05-07
forum: Hardware
---

### Post by core on 2008-05-07
Hi all

I've been using 8.04 Hardy the last few days and I tried something i've never used before: TV-Out using S-Video from my laptop's video card. In windows works great - just say to expand the desktop and there it goes - but on Hardy i'm not being much successful.

The thing is, i have no idea what should i do to activate S-Video. I don't even know if ATI drivers are installed, although compiz effects are on.

Command aticonfig is not avaliable, and EnvyNG does not work, with the message "your OS is not supported" (maybe not compatible with hardy heron yet?).

I read somewhere how to edit xorg.conf to configure s-video. but i didn't want to mess with it just yet, hoping there's some cleaner way to fix this... and faster.

While changing screen resolution, I notice the word "Cloned Output" on the screen. Does this mean S-Video should be working, yet with a mirror of my main output rather than expanding the desktop? Either way, I can't manage to see anything on my TV...

For now, I'm using dual-boot to use S-Video using windows... and that makes penguin sad :-(

Any help on this? Thanks

---

### Post by core on 2008-05-12
So, anyone? Maybe I'm missing the point on how to configure s-video on Ubuntu... but I can't find any info on this.

Thanks again.

---

### Post by herrison on 2008-05-25
Same problem here, older laptop. No idea how to make the s-video output work. The fn+f8 button does not appear to work. Dell Latitude D600. Radeon RV250. No documentation I can find.

---

### Post by Jimoto on 2008-09-28
Core,

Ubuntu has open source ati drivers installed by default so you should already have proper 2d and 3d acceleration, see this page on how to enable it.
_[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")_

Unfortunately the bad news is that S-video doesn't work for the 9100 IGP and I was told there is going to be no more support for this card (Somebody correct me if I am wrong), I also asked in the Intrepid channel but nobody responded. I have been trying for the last 3 days to get it working, since Xinerama doesn't work with ati and MergedFB has been replaced by xrandr. I managed to get the S-video output on, but it just displays jumble. Try it out for yourself, maybe somebody else can tweak it to work.

This forces xrandr to detect that S-video is connected, since the ati driver doesn't realise. Then apply default settings and enable the port.
```
xrandr --output S-video --set load_detection 1
xrandr --auto
```
Use this to turn it off
```
xrandr --output S-video --off
```

Sorry for the bad news, I really hope somebody comes up with a fix for this because it is the only reason I still need to use windows. If you read this and have found a way to get S-video working (with RS300M 9100 IGP) plese let us know.

---

### Post by Arless on 2008-11-05
jimoto did you try

 Option "ForceTVOut" "boolean"
               Enable this option to force TV Out  to  always  be  detected  as
               attached.  The default is off

in xorg.conf?

---

### Post by Jimoto on 2008-11-06
Arless,

Xorg was the first thing I tried, after fiddling around for ages without success I read that these ati drivers don't work with xinerama. I did however try the ForceTVOut at the time but it makes no difference.

Thanks for the idea though.

---

### Post by cr4z3d on 2008-11-20
Hey I've got this same card and attempting to get S-video working as well. I had used MythTV probably 2 years ago and got S-video working then. I have no idea what I modified or any of that but there has to be some way to get it working again? When I try the commands it just makes my TV blink but doesn't really do anything.

---

### Post by Jimoto on 2008-12-03
Same results here, you can tell something is being displayed on the screen because the picture changes when you drag windows around, but it's still unrecognisable in all the noise and fuzz. I thought there might be something wrong with the vertical and horizontal rates, but it all looked the same after trying various settings.

I might try Mythbuntu or LinuxMCE and see if they have better support, after all that's what these distros are made for.

---

### Post by ChuckMcB on 2008-12-06
> I might try Mythbuntu or LinuxMCE and see if they have better support, 
> after all that's what these distros are made for.
Let us know how you get on. I spent two weeks at the start of the year burning loads of CDs from dif. distros trying to get my D600's TV out working, all without any sucess. Had to drop XP back onto it to get it to work :(

---

### Post by aristides on 2008-12-10
Hello, and good news, i found a solution in a blog. Follow next link:

[http://wargle.blogspot.com/2007/05/solution-to-ati-9100-igp-tv-out-with.html](http://wargle.blogspot.com/2007/05/solution-to-ati-9100-igp-tv-out-with.html)


i try it, and the S-video works.

Thanks Wargle!!!

---

