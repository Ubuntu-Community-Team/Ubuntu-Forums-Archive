---
title: "ATi Radeon 2400 HD Pro Driver Issues"
date: 2008-04-24
forum: Hardware
---

### Post by gwoodard on 2008-04-24
Hello, I need to know what video drivers (besides vesa) would work w/ the video card as mentioned in the title (I want full 3d stuff, faster screensavers, and the themes I want to work properly)

other than that the default drivers let the resolution be up too 1280x1024 which I like...

---

### Post by Ub1476 on 2008-04-24
Have you enabled the drivers in System>Administration>Hardware Drivers?

---

### Post by gwoodard on 2008-04-24
It is a newer card...it said it didn't need to be activated

---

### Post by Milkymonsta on 2008-04-27
I'm also having issues with my ATI Radeon 2400 HD AGP PRO card too, I haven't been able to even use Ubuntu 8.04 because as the system boots the video card turns off no matter what I try.

I've posted about my woes alas I haven't been so fortunate for any advice.

[http://ubuntuforums.org/showthread.php?t=765183]("http://ubuntuforums.org/showthread.php?t=765183")

---

### Post by gwoodard on 2008-04-27
> **Milkymonsta said:**
> I'm also having issues with my ATI Radeon 2400 HD AGP PRO card too, I haven't been able to even use Ubuntu 8.04 because as the system boots the video card turns off no matter what I try.

I've posted about my woes alas I haven't been so fortunate for any advice.

[http://ubuntuforums.org/showthread.php?t=765183]("http://ubuntuforums.org/showthread.php?t=765183")

Thank you I tried to install 8.04 but the mouse cursor lagged and the video drivers (restricted) installed but went into low graphics...

---

### Post by Dai777 on 2008-04-27
I had no problem with heron finding my card hd 2400pro not sure if mine is agp though. You can always use envy to see if comes up with the driver for you. I had to use envy to get the driver in gutsy.

---

### Post by gwoodard on 2008-04-28
I'm sorry, but I have tried envy in the past, didn't work out that well

but thank you for you comment

---

### Post by Yellow Pasque on 2008-04-28
Milky,
Boot your system and when it gets hung up with no video, try Ctrl+Alt+F1 to get to the terminal. Once there, follow this procedure. [http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

Use sudo vim to edit your xorg.conf  Once you enter the program, press 'i' to enter normal text editing mode. When you're finished, press 'Esc' and type :x[Enter] to save changes.

---

### Post by gwoodard on 2008-04-30
the question i am asking for is 7.10 not 8.04...

sorry for any confusion

---

### Post by Yellow Pasque on 2008-05-01
You're SOL. AMD/ATI doesn't have AGP support in Catalyst 8.4 (See posts by AMD developer 'Bridgman' in the last page of this thread: [http://www.phoronix.com/forums/showthread.php?t=7350&page=4](http://www.phoronix.com/forums/showthread.php?t=7350&page=4) ).

For the time being, I'd suggest using the radeonhd driver for 2D support/acceleration (follow the link in my sig).

---

### Post by gwoodard on 2008-06-28
Well, I tried to do the 8.04+Restricted...no go for the vesa drivers got messed up, couldn't switch w/out going off w/ the black screen on doom, reinstalled ubuntu and tried ENVY NG...whoops! same thing happens...

---

