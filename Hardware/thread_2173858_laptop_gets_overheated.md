---
title: "laptop gets overheated"
date: 2013-09-11
forum: Hardware
---

### Post by jovan2 on 2013-09-11
Hello,

I've a problem when I am on my Ubuntu linux. Temperature goes up more then 85% and after that screen bloks and similar things. When I am on Windows, nothing similar happens. I've seen some tutorials how to fix it, but I want opinnion from here also. Does anyone has some idea?

---

### Post by QIII on 2013-09-11
Hello and welcome to the Forums.

Could you give us some information about the machine -- CPU, graphics card, etc?

---

### Post by jovan2 on 2013-09-11
Thank you so much!

Yes, sure, this is my machine: Nvidia GeForce GT 520M , 4096 MB DDR3-RAM (1333 MHz), Intel Core i5 2410M, HDD WDC Scorpio Blue WD6400BPVT-80HXZT1 640 GB 5400 rpm 5400rpm

---

### Post by tgalati4 on 2013-09-11
Open a terminal:

```
sudo apt-get install htop
htop
```

Watch *htop* and see what jobs are running while the system is getting hot.  Perhaps you have some stuck processes that are causing your CPU to go to 100% for long periods of time.

---

### Post by Yellow Pasque on 2013-09-11
It will help to disable the nvidia card when not in use (unfortunately, Linux is not at the point where this happens automatically):
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Linuxisfast on 2013-09-12
Install latest Ubuntu 12.04.3 and nvidia-optimus driver will be installed automatically and your laptop will run cooler. My ASUS K55VM i7 laptop with nvidia GT630M runs same temps as it does on Windows8.

---

### Post by tmcgravey-linux on 2013-09-12
I recently installed Ubuntu on a friend's laptop. When booted in Windows, the fan worked fine. When booted in Ubuntu, the
fan was not working. I updated the BIOS and then the fan worked properly with Ubuntu.

---

### Post by jovan2 on 2013-09-14
Do you know maybe how i can install nvidia-optimus driver manually? With out installing new ubuntu?
That happens few days ago, I've Ubuntu 2 months I think, not sure what happend.

---

### Post by buzzingrobot on 2013-09-14
Jovan, what version of Ubuntu are you currently running?

Also, what is happening with the screen when the unit gets hot? 

It appears your laptop has an Intel video chip embedded in the CPU plus the Nvidia card.  Many, many laptops do also. Identifying which video card the laptop is now using would be useful.    Some laptops allow you to choose which video you want to use via the BIOS setup. If your BIOS offers this option, you will likely see an option to enable the "discrete" video.  That's the Nvidia. The other option will be "integrated", which is the Intel video. (When one video card is disabled in BIOS, it is invisible; the machine will not see it. This means that if the Nvidia card is disabled and the machine still gets hot, something else is going on.)  The BIOS setup may offer a third option, the "Optimus" option.  Choose that if you install Bumbleee.

If you have none of these options in your BIOS setup, then Bumblebee will act to control the Nvidia card. You should read the wiki page at the link posted above, but, basically, BumbleBee works by activating the Nvidia only when there are intensive graphic calculations to be made.  The results of those calculations are then displayed on screen by the Intel video. I believe this is also what happens in Windows machines running Nvidia cards.

---

### Post by jovan2 on 2013-09-14
I am using Ubuntu 12.04 LTS.
Screen freezes, and i can't do anything

Now I've installed Bumbleee and everything seems fine, temperature doesen't go up more then 60C.

---

### Post by ajd-nanthakumar on 2013-11-02
I have been using 12.04.3 but optimus was not working full. Later I switched to 13.10 and now optimus is working full and can control the discrete nvidia card. So nvidia is activated only on high graphic apps or on users instructions. Better switch overto 13.10. And hey, I suppose Ubuntu has started getting Optimus support but practically from 13.10 through bumblebee

---

