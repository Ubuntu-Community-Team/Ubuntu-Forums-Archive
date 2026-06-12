---
title: "ubuntu 8.04 on Dell D600"
date: 2008-06-01
forum: Hardware
---

### Post by divindavid on 2008-06-01
hello i am about to buy a Dell latitude D600 off a friend and i want to double boot which i have dont many times. but i have only ran ubuntu on old IBMs. so this is my first time doing a Dell.
will deck top effects for if it has 32mb of video ram. 512ram a 1.6 or a 1.86 Pentium 4 (M) processor. and does the built in wireless work or will i have to use wicd

---

### Post by hotweiss on 2008-06-01
> **divindavid said:**
> hello i am about to buy a Dell latitude D600 off a friend and i want to double boot which i have dont many times. but i have only ran ubuntu on old IBMs. so this is my first time doing a Dell.
will deck top effects for if it has 32mb of video ram. 512ram a 1.6 or a 1.86 Pentium 4 (M) processor. and does the built in wireless work or will i have to use wicd

Just burn Ubuntu onto a CD and run a live session to see how everything works.

---

### Post by nick_h on 2008-06-01
Try the Live CD.

There is an old report from the [Laptop Testing Team](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD600) which suggests that it will probably work.

---

### Post by divindavid on 2008-06-01
> **hotweiss said:**
> Just burn Ubuntu onto a CD and run a live session to see how everything works.

if you used your eyes to read it says that i dont have the laptop yet. and i sayed that i have used ubuntu a lot before so i kind of know what a live cd is

---

### Post by Brian96 on 2008-06-04
> **divindavid said:**
> hello i am about to buy a Dell latitude D600 off a friend and i want to double boot which i have dont many times. but i have only ran ubuntu on old IBMs. so this is my first time doing a Dell.
will deck top effects for if it has 32mb of video ram. 512ram a 1.6 or a 1.86 Pentium 4 (M) processor. and does the built in wireless work or will i have to use wicd

I have this laptop, and it worked great with Gutsy, but there has been some sort of regression with the wireless drivers so I haven't gotten the wireless to work yet. (In Gutsy I only had to enable the restricted drivers in the restricted manager.) Also, the video does not seem to support desktop effects (although I didn't try too hard to get that working).

> **divindavid said:**
> if you used your eyes to read it says that i dont have the laptop yet. and i sayed that i have used ubuntu a lot before so i kind of know what a live cd is

Sheesh, they were just trying to help. If we are going to be all picky, one could ask WTH "deck top effects" are. :)

---

### Post by Brian96 on 2008-06-04
I may have posted too soon. I now have wireless working in HH with little ado. I think a few weeks ago I may have manually installed the bcm fw package. In any event, the device showed up in my restricted manager today when I checked (it was not there after a fresh install) and now I have it working without any work-around required.

---

### Post by vineas on 2008-06-04
I'm posting this now on a Dell D600 - works great.  The only issue I'm having is with the wireless configuration - it will work, but doesn't seem to save my WPA password between boots, so I need to open the network config and reset it in order for the network to work correctly.  I was coming to the forums to see if I can't track this down actually ...

---

### Post by IcOpRo on 2008-06-12
Hey i have that same Exact Laptop right now i`ve been using it since ubuntu 7 and now im running 8.04 on it and its been working with no problems. The only thing is that now on 8.04 the ATI drivers are restrictec, and desktop effects dont work.

The latptop works great is small and lightweight, so in my opinion go for it bro. It works with no problems.

Oh and also there is a workaround the restricted drivers to get desktop effects working.. wich im looking for info on the forums to do it, thats how i came upon this thread heheheh...

---

### Post by Rocket2DMn on 2008-06-14
To my knowledge, this model laptop uses the ATI Radeon Mobility 9000 card which does not take the restricted drivers, it uses the open source "ati" drivers.  Have a look at this thread to enable compiz - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
You can remove the restricted drivers that may have been installed from within Ubuntu by running
```
sudo apt-get remove --purge xorg-driver-fglrx
```
If you used EnvyNG to install restricted drivers, you can uninstall them from there.

---

