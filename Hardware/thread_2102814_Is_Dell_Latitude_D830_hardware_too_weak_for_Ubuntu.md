---
title: "Is Dell Latitude D830 hardware too weak for Ubuntu 12.04"
date: 2013-01-08
forum: Hardware
---

### Post by KozaG on 2013-01-08
Hi,

I'm running Ubuntu 12.04 on my Dell D830 laptop. The laptop has 2gb RAM 1.8 ghz CPU and nvidia quadro nvs 140m. I feel that 12.04 is a bit slow and gets even slower after three or more programs is running. I have noticed that Win XP had better performance with Blender than Ubuntu 12.04. Although I was using 2.59 blender in xp and the latest version of blender in ubuntu. But can these two versions have such a big difference that the latest Blender is much more heavier. 

Is it normal to have not smooth performance of 12.04 with my laptop? Will the experience improve significally if I upgrade my RAM to 4 gb or even 8 gb? What is the max RAM amount in 12.04 32bit anyway?

Thanks!

---

### Post by sudodus on 2013-01-08
[Vanilla] Ubuntu 12.04 LTS is a good version of Ubuntu, but it needs a lot of horsepower, that is not available in aging computers.

But the computer would do well with 12.04 and a lighter desktop environment. I suggest that you download the iso files and test them from a CD or USB drive (boot a live session without installing it). And when you see how it works, decide what to install.

***Xubuntu*** with the light desktop environment XFCE
***Lubuntu*** with the ultra-light desktop environment LXDE

---

### Post by tlhIngan on 2013-01-08
I recommend Lubuntu, that's what I'm running on my 9-year-old and 7-year-old PC's.
I believe the 32-bit OS's are limited to 4 GB or RAM, although your specific hardware may have lower maximum limits.

---

### Post by GreenTaurus on 2013-01-08
The max memory in the D830 is 4GB.

---

### Post by KozaG on 2013-01-10
Thanks!

So would I be seeing major improvement with OS performance if I would upgrade to 4gb RAM? Or will my processor be the bottle's neck in this situation?

I need wacom setup interface which Xubuntu and Lubuntu don't have. That is why I don't like those two OS'.

On my D830 Kubuntu was running pretty smoothly btw.

---

### Post by sudodus on 2013-01-10
> **KozaG said:**
> Thanks!

So would I be seeing major improvement with OS performance if I would upgrade to 4gb RAM? Or will my processor be the bottle's neck in this situation?

I think you'll do well with 2 GB of RAM, at least with [LX]ubuntu.
> 
I need wacom setup interface which Xubuntu and Lubuntu don't have. That is why I don't like those two OS'.

I have a Wacom Bamboo device, and it works out of the box in my Lubuntu 12.04 with xubuntu-desktop (in an old IBM Thinkpad T41).
> 
On my D830 Kubuntu was running pretty smoothly btw.
Which version of Kubuntu (10.04 ...)?

---

### Post by KozaG on 2013-01-10
It was Kubuntu 12.04 32bit.

Xubuntu and Lubuntu don't have graphical interface to setup the key binding for my Intuos 4 tablet and the interface is something that I need. Also if you plug in some device to a computer and only 50% of it works as it should I wouldn't call it "working out of the box". I'm talking here about the LEDs and the middle button which when pressing changes the touch circle mode.

---

### Post by sudodus on 2013-01-10
> **KozaG said:**
> It was Kubuntu 12.04 32bit.

Xubuntu and Lubuntu don't have graphical interface to setup the key binding for my Intuos 4 tablet and the interface is something that I need. Also if you plug in some device to a computer and only 50% of it works as it should I wouldn't call it "working out of the box". I'm talking here about the LEDs and the middle button which when pressing changes the touch circle mode.
Well, I have another and cheaper Wacom device. I can understand that yours needs tweaking to make everything work properly.

If Kubuntu 12.04 works well, I think [vanilla] Ubuntu 12.04 will work well too, they need about the same horsepower and memory to work well.

So use a flavour that works with your hardware. If you want faster graphics, for example to show high definition video, you can install light-weight desktop environments into your present Kubuntu version and select desktop at the log in screen before logging in :-)

```
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop
```

or install only LXDE and/or XFCE.

---

### Post by sudodus on 2013-01-10
> **KozaG said:**
> I feel that 12.04 is a bit slow and gets even slower after three or more programs is running. I have noticed that Win XP had better performance with Blender than Ubuntu 12.04

Back to the original question!

I think that Ubuntu's default desktop Unity as well as Kubuntu's KDE need a lot of RAM, so if you run many or big tasks, it is a good idea to increase the RAM. You will notice the difference, if you double the RAM to 4 GB.

---

### Post by Yellow Pasque on 2013-01-10
I would look at the CPU temp when running a bunch of programs. If it's getting too hot, it will throttle the clock speed to prevent damage (and eventually it will shut the system down if temps continue to rise).
It's possible your laptop needs a good internal dusting.

---

### Post by KozaG on 2013-01-11
Okey guys thanks for the help and tips! :)

---

### Post by win2456 on 2013-01-28
I went through the same dilemma a while back (2 years ago exactly).  Upgraded to 4GB RAM and started with a fresh install of ubuntu.  I do video transcoding, run an XP VM, sometimes let picasa scan through thousands of pictures and also use my laptop as a media server... With all of this, the system takes a beating.  4GB RAM is somewhat worth it.  It will not give you increased speeds, but will help prevent your system from choking quicker.

Pet peeves:
-System load always high (despite of trying different nvidia drivers and trying other things)
-Connecting an extended monitor seems to drag the performance down even more for some reason
-Have to clean out the dust buildup inside the computer quite frequently (and yes, this does help reduce heat and keep system running smooth)

I'm about done with this laptop (bought in 2006).  I do like unity but am going to give l/xubuntu a try as suggested earlier in this post and give the laptop to my kids or something.

Good information in this thread!

System specs:
D830
Nvidia 140m
4gb Kingston RAM
WD 750GB 7200RPM HD

---

