---
title: "Compiz Fusion Randomly Turning Off effects"
date: 2008-11-24
forum: General Help
---

### Post by davydog187 on 2008-11-24
Hello,

I've been using Ubuntu for about a month and a half or so. Love it. I'm using Intrepid Ibex and I've had no problems, until Saturday. 

Heres the problem. I'm using compiz fusion. Works(ed) great. On Saturday I was using my laptop, just browsing the internet when all of a sudden the screen flickered, and all of my fusion effects were gone.

Now, they come back if I restart, change the settings in the compiz configurer, and enable effects....however the screen flickers again in a few minutes and I am left fustrated.

I tried reinstalling all the compiz packages in Synaptic, but that did not work...I have really no clue what to do. 


I have an ATI graphics card.

Help?

-Dave

---

### Post by eternalnewbee on 2008-11-24
Hi davydog187.
No ideas really. Just this: Go to your terminal and enter: ```
sudo apt-get update
```
You never know...

---

### Post by Keyper7 on 2008-11-24
Okay, davydog187, let's go.

First of all, let me be sure. Is compiz active? What exactly is not working, specific plugins or compiz itself?

Ps: it might take an entire day to check your reply to this, but I will

---

### Post by davydog187 on 2008-11-24
Compiz effects stop working(in general), so the screen will flicker and then all fusion effects go away until I log out and back in.

UPDATE***I tried sudo apt-get upgrade and it is working so far...but I'm not sure it will last, I'll again if it compiz crashes again

---

### Post by davydog187 on 2008-11-24
Compiz has stopped working again. sudo apt-get update did not fix it :/

Further suggestions?

---

### Post by eternalnewbee on 2008-11-25
Go to: Main Menu > System > Administration > Hardware Drivers, and check what the options are. If reinstalling compiz didn't solve it, then my guess is it's a problem with Hardware configuration.

---

### Post by Keyper7 on 2008-11-25
So apparently it's failing to start. I guess the first step is to check the error messages. Open a terminal and start compiz manually:

compiz --replace

and then post the output here.

---

### Post by accesshater on 2008-11-25
I can confirm this problem. I am using 8.10 (installed it when released).

I had no problem but now if i do something with the effects it switches off randomly.

I noticed some compiz updates a couple of days ago... could it be that that is the source of the problem?

---

### Post by former_warper on 2008-11-25
I have the same problem.  It came following the last update on compiz last weekend.  Perhaps it needs to be reported.
5 year old Gateway 7405GX ati Mobility Radeon 9600. Ubuntu 8.10 x86_64

---

### Post by davydog187 on 2008-11-25
```
david@david-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

That was what it said when I did compiz --replace. Keep in mind it was working when I did that

---

### Post by stormtrooprdave on 2008-11-25
I am having the same problem. Nothing has changed on my pc except the compiz updates that have come recently.  It seems at random points I lose my cube, wobbly windows, emerald theme, etc.  Is there a launchpad bug for this?

---

### Post by loomsen on 2008-11-25
Probably (and most likely) a problem with your xorg. 

You don't have xgl is what the terminal tells you. Make sure you get the right driver, and let fusion-icon run in a terminal

It will tell you what to do, or why sth crashed.

Maybe that permissions issue applies to other cards as well, you can try... Check the howto in my sig.

And use google before filing any bug.

*edit*

Thats what my synaptics shows if i search for mesa:
[[img]http://www.ubuntu-pics.de/thumb/6353/screenshot_01_S8AJ5r.png[/img]](http://www.ubuntu-pics.de/bild/6353/screenshot_01_S8AJ5r.png)

Texture from pixmaps...:
[[img]http://www.ubuntu-pics.de/thumb/6354/screenshot_02_1TZ6KL.png[/img]](http://www.ubuntu-pics.de/bild/6354/screenshot_02_1TZ6KL.png)

---

### Post by davydog187 on 2008-11-25
keep in mind that compiz fusion has been working for me perfectly for over a month. I think it may be directly related to the new compiz update. Is there a way to roll back to the previous files?

---

### Post by Keyper7 on 2008-11-26
> **davydog187 said:**
> That was what it said when I did compiz --replace. Keep in mind it was working when I did that

I'd recommend that you start compiz this way, through the terminal, and keep using it until it crashes. When it crashes, something useful might appear in the output.

In the meantime, are you using compizconfig-settings-manager? Sometimes it might happen that a compiz update conflitcs with previous setted options. In this case, you can try resetting all your settings to default.

---

### Post by accesshater on 2008-11-26
> **Keyper7 said:**
> I'd recommend that you start compiz this way, through the terminal, and keep using it until it crashes. When it crashes, something useful might appear in the output.

In the meantime, are you using compizconfig-settings-manager? Sometimes it might happen that a compiz update conflitcs with previous setted options. In this case, **you can try resetting all your settings to default.**

Done that, but it doesnt work.

@loomsen: i doubt it has something to do with xorg configuration files. Because compiz worked perfect before the compiz updates =/

---

### Post by Sloma on 2008-11-26
I have similar problem and also think this is caused by latest update. Is there a way to roll back?

---

### Post by Billbrasky82 on 2008-11-26
I am having the exact same problem and everything I have read to try and fix it does nothing. I am at my wits end with this, Compiz worked fine when I had the system installed under windows and I was so happy because not having Compiz was the one thing keeping me from installing Ubuntu for good. And now that I took the plunge this morning and lost everything I had due to a faulty external... I find this isnt even working. 

Anybody have any other ideas other than uninstalling and reinstalling?

---

