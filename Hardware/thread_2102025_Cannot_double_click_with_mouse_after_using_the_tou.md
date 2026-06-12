---
title: "Cannot double click with mouse after using the touchscreen."
date: 2013-01-06
forum: Hardware
---

### Post by sbnwl on 2013-01-06
I have two ubuntu installations side by side on a sony VPCJ128FG on the same HDD, namely Ubuntu 11.10 and Ubuntu 12.10. 

This problem is specific only to Ubuntu 12.10, (I'm writing using 12.10, No problems with the 11.10 version). 

Everything works just fine after login into my user account in Ubuntu 12.10 if I do not use the touchscreen of this desktop. Mouse single and double clicks are okay and work as expected. The problem starts only after my touchscreen is invoked by a finger touch or even a fly touches my touchscreen ;). After that the mouse double click stops working. Nothing happens when I double click on folder icons in nautilus. Even right click on folders in nautilus with mouse is also does nothing. But I can still drag select the folders with left mouse click, which is the only thing I can do in nautilus then. Menu can be clicked though as expected. 

This problem existed on this machine in 12.04 also. So I did a fresh install of 12.10, and got the same disappointment again.  What is wrong with the touch drivers I can't figure out myself. Searched through threads could not find any working solution. 

This problem is persistent on Unity desktop, so I installed gnome shell but still persistent, installed then Cinnamon and still no help. So I believe that the problem is related to something else. 

One more thing I noted that (after invoking touch screen) when I hover the mouse (without any click) in the bluetooth or network settings windows, the text automatically gets selected. And there is perfectly no such problems while using Firefox or Google Chrome browsers. I can use mouse within the browsers still perfectly.

---

### Post by sbnwl on 2013-01-09
Any ideas?

---

### Post by sbnwl on 2013-01-09
I had put the problem on forum only after a thorough try for one month myself.

---

### Post by zoltanthegypsy on 2013-02-10
Same behavior on Lenovo Twist.  Log out and back in to fix - temporarily.

---

### Post by sbnwl on 2013-02-14
@zoltanthegypsy

At least you confirmed it!

You are right. The temporary solution is logout, then login back. But It is working perfectly in Ubuntu 11. 10 which I kept on the same machine only due to this reason.
I have updated Ubuntu 11.10 whenever updates are available. No problems.

The problem was with Ubuntu 12.04, and still is there with Ubuntu 12.10.

---

### Post by xanthemia on 2013-03-22
This is happening to me too. But it occurs even if I don't touch the screen. Maybe a draft instigates it. Logging in and out does fix it, but how annoying to have to restart everything.  Using a Dell Inspiron One 2305. My non-touchscreen laptops don't have this problem, so I figure it is related to being touchscreen.

Additionally, I don't know if it's related but when using web browsers (both chromium and firefox) mouse functionality ceases in a tab once I use the right click function one time. I am pretty sure this also started once I upgraded to 12.04.

---

### Post by clever on 2013-04-03
This is happening to me too.  I'm on Linux Mint 14 Nadia, and it also happens with Ubuntu on Live USB.  Once I touch the screen, I am no longer able to double-click anything on the desktop, either through double-tapping the screen, or using the touch pad or even my external mouse.

Laptop is Samsung Series 7 Chronos NP780Z5E-S01UB.

---

### Post by enricogalli on 2013-04-07
Same exact story here.
I am using Ubuntu 12.10 on a Gordon System All in One computer with 23" touch screen.

It happens exactly the same thing explained by **sbnwl**.
Did anybody fix this?

---

### Post by galkowskit on 2013-04-11
I have the very same issue here with my ASUS VivoBook X202E. I hope someone will figure it out, because it is SUPER annoying. Could someone at least tell me how to temporarily disable the touch screen?

@edit:
This bug has been submitted here: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1002788](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1002788). It looks as it is a bug within xorg/xserver. 
Probably a fix: [http://cgit.freedesktop.org/xorg/xserver/commit/?id=3e6358ee6c33979329b78fe2097a1fdf76fb69cd](http://cgit.freedesktop.org/xorg/xserver/commit/?id=3e6358ee6c33979329b78fe2097a1fdf76fb69cd) - maybe someone can use it somehow. I don't really know what to do with it. ;)

@edit2:

OK, I have found a fix at the first link and it worked for me (at least up until now). BUT BE WARNED: when adding this repository it says that it's risky and should only be done when desperate and at your own risk. Still, if you want to try: 

1. Type in the Terminal:

[I]```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
```[/I]

2. Open Update Centre/Update Manager (or whetever its called in English version, I use Polish) and use it to install updates. Reboot.

It worked for me.

---

### Post by sbnwl on 2013-04-27
As of now, I am closing this thread! The reason?? I wiped out the Ubuntu 12.10 Installation, and Installed the Ubuntu 13.04 released two days back, alongside my old Ubuntu 11.10 installation. Now I see no problems with the touchscreen. Problem SOLVED!

I can't say for sure, whether the upgrading from Ubuntu 12.10 to 13.04 will help or not. But fresh Ubuntu 13.04 installation works perfectly.

---

### Post by sbnwl on 2013-04-27
I forgot to add that the following problem is still unresolved:
> One more thing I noted that (after invoking touch screen) when I hover  the mouse (without any click) in the bluetooth or network settings  windows, the text automatically gets selected.
But that is of not much importance to me, It can be okay to live with.

---

### Post by slickware on 2013-05-05
I just bought a Vivobook X202E and put 13.04 on it. I can confirm that the touchscreen does not interfere with the touchpad operation as noted by the OP.

However, double-tapping the touchscreen seems to have no effect; it will not open files or dialogues where it should.

If I then switch back and tap the trackpad, I often find that it will suddenly jump the cursor - most likely to wherever the cursor left off prior to switching to the touchscreen.

---

