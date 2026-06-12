---
title: "Graphics card recommendation for 10.04 LTS 64bit"
date: 2012-07-24
forum: Hardware
---

### Post by galapogos on 2012-07-24
Hi,

I'm getting a graphics card for my Core i7-3700 system because the Intel HD 4000 graphics isn't supported on 10.04 LTS 64bit, and I have to use this version.

What graphics card can I buy today that is well supported in 10.04? I need it to support a dual monitor setup of a 1280x1024 LCD connected to VGA and a 1920x1080 LCD connected to DVI. I don't need any advanced graphics features for 3D gaming and what not, as this is a development PC, so basic graphics is sufficient.

Any recommendations?

---

### Post by Bucky Ball on 2012-07-24
You could probably save some money. That card does seem to work in 10.04 but with a newer kernel probably than what you are using. Issue these two commands in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

This will not upgrade the release, just packages and apps. Then this:

```
uname -r
```

What is the output from that last command? That shows the kernel you are running.

I have 10.04 but my wireless card will not run with the stock 10.04 kernel. It is not possible. So I use the 11.04 kernel in 10.04. It's really easy to do (as easy as installing the newer kernel with a one click deb file) and maybe we could go there if the above doesn't work. 

I think buying a new card is heading in the wrong direction at this point. You might save some money by digging a bit deeper (why waste what might be a perfectly good card???). ;)

PS: What is locking you to 10.04 LTS? Maybe create a spare partition and chuck Ubuntu (or *buntu) 12.04 on there and start diddling around with it as you'll have no choice come next April. That way you'll have the stable, production 10.04 and a 12.04 plaything until that's solid and 10.04 reaches EOL. ;)

---

### Post by galapogos on 2012-07-24
Hi,

Thanks for the reply. I've previously already tried to get it working following the same instructions for the HD 3000 graphics support, which are:

sudo add-apt-repository ppa:glasen/intel-driver
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty

So I already have 2.6.38. uname shows  2.6.58-15-generic. I've emailed stefan directly and he indicates that  Ivy Bridge-support was added to the Intel graphic-drivers in version 2.17 (his PPA only contains 2.15 for Ubuntu 10.04), and that I also need a very recent kernel version for a good Ivy
Bridge-support (At least 3.0, better is 3.2 or even 3.5) as well as Mesa 7.11 or better 8.0.

While installing the new drivers and kernel is relatively easy, Mesa apparently needs LLVM 2.8 whereas Ubuntu 10.04 only delivers version 2.7. He also wasn't sure if the xserver-version 1.7.6 from Lucid will run flawlessly with the updated driver-stack.

Sounds quite daunting to me as I'm quite an ubuntu noob.

---

### Post by Bucky Ball on 2012-07-24
Well, you're doing pretty good so far. My mistake, I was looking at the ATI Radeon HD 4000. Yours is the Intel, of course. ;)

---

### Post by galapogos on 2012-07-24
Thanks. I decided to take a leap of faith and updated to the oneiric backported kernel, and voila, it actually worked. Managed to get native resolution on both monitor as well as an extended desktop. :)

The only thing is that my smaller monitor isn't being recognized, probably coz it's too old.

I'll continue using this setup and see if everything's working...

---

### Post by Bucky Ball on 2012-07-24
Cool. Enjoy and hope it hangs together. 12.04 LTS should be up to 12.04.1 by now so it's getting there. ;)

I've installed on a couple of other machines (not mine) and seems to be fine there. Will kill the 11.04 partition on my laptop and try it shortly.

---

