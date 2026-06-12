---
title: "accelerated video with Lucid on C840 laptop"
date: 2010-07-23
forum: Hardware
---

### Post by spipe on 2010-07-23
Just in case any others are tearing out their hair over this, here's how I got the accelerated nvidia driver working on a Dell Latitude C840 laptop, putting together a couple of tips from this forum.  It seemed to me it might be useful to lay it out step-by-step for anybody else struggling with the same model.

(The C840 is an older laptop model with exactly two virtues: you can buy it fairly cheaply, and it has a lovely 1600x1200 display.  Its main drawbacks are that it can't accommodate much memory by modern standards, its performance is sluggish especially with the open-source video driver, and it reports bogus EDID info that confuses the heck out of the current video drivers.)


1. Do a stock Lucid install.

2. On first boot afterward, hold down the Shift key to get the grub menu, and temporarily edit the kernel line, replacing "**quiet splash**" with "**nomodeset**".  Continue with boot and you should get to a workable desktop, though it might not be at the full resolution you want.  Don't worry about it.  If the grub menu slipped past you, the screen will probably come up black and you'll have to reboot and try again.

3. You'll be prompted shortly to run updates; decline or ignore that for now, to avoid a long wait.  You'll also be prompted to install the proprietary nvidia driver, version 96; say yes to that.

4. Once the driver is installed, reboot.  The video is going to fail again, but nothing in grub will help you this time.  Instead, wait for the boot activity to seem to be over, then press control+alt+F1 and log in at the text prompt.

5. The below command will give you an almost-workable xorg.conf file:
```
$ **sudo nvidia-xconfig**
```

6. Now edit that file:
```
$ **sudo nano /etc/X11/xorg.conf**
```

7. Insert a UseDisplayDevice line into the "Screen" section, as here:

```

...
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    **Option         "UseDisplayDevice" "DFP-0"**
    SubSection     "Display"
...
```

8. Reboot and all will be well.
```
$ **sudo reboot**
```


======================================================

Notes -

A. I'm not sure the last reboot is necessary - you might get away with,
```
sudo service gdm restart
```

B. I don't quite understand how the UseDisplayDevice option can work, given that "DFP-0" isn't defined anywhere else in the xorg.conf file.  I expected to have to download and install some kind of EDID file that would then be referenced as DFP-0, but it wasn't needed for some reason.

C. Obviously, use the terminal-based editor of your choice, be it vi or whatever.  I'm partial to zile, but that isn't installed by default.

---

### Post by Pete317 on 2010-08-09
Do you think that this will work with an upgrade from Hardy to Lucid rather than a fresh install?
Remembering all the problems I had getting the video to work properly when I upgraded to Hardy, has put me off upgrading since. However, there's quite a lot of software I want to use which won't work on Hardy.

---

### Post by zerin on 2010-08-19
Well, thanks for the easy and straightforward method of making the drivers work, i still have had this problem on my school laptop and never used the drivers for this very reason they didn't work. However, i followed your steps and still have the same problems i did before. Granted it's not a "fresh install" but the xorg.xonf was never modified before but after doing this, i still get the same error that forces me to run in low graphics mode, until i remove the Nvidia 96 drivers. I am using 9.10 if that makes a difference and would still like some help to eneable the drivers on this old machine of mine. the very same Dell c840 with the GeForce4 440 agp card.

---

### Post by spipe on 2010-09-04
Sorry for the late reply - I failed to subscribe to the thread.

This only worked for me on a fresh install.  I struggled with an upgrade for some time before deciding to wipe the machine and start fresh.

---

### Post by zerin on 2010-09-07
It's all right. I also did a fresh install and put Ubuntu 8.10 (don't ask why) and did the exact steps you mentioned. Worked like a charm, except for one little itty bitty thing. i get my screen with rainbow line on the right and a reflection of my top screen on the bottom. I can't explain it well, but i think that my GPU thinks i have a 1400X1050 instead of the 1600X1200 i do have. so i was wondering, what do i do to tell my xorg.conf that i have a different resolution monitor. i'm a keep trying different things, but for now, even though my desktop is weird. it is much faster. I won't give up!

edit: ok after searching the web, i found an old forum thread that solved this problem before, it involved doing as Snipe said, + adding this file[nvnew.raw]("http://cid-f20119059169b7cc.office.live.com/self.aspx/.Public/nvnew.raw") in your etc/X11 folder, next to your xorg.conf and your machine should display 1600x1200 instead of the 1400x1050 bug, that is if you have that screen size. 

I did not make this file, someone else did, i forgot who and where i got it from, but if you need it, here it is. but you only add this file if you have the same problem i did after making my default flat panel display the default. also, i'm think there are still problems with the external monitor stuff, but i'm not sure, must test. also, i did this on a 9.04 ubuntu machine, upgraded it, i don't think it makes a difference though.

---

### Post by Pete317 on 2010-09-11
Well, I eventually bit the bullet and upgraded from Hardy to Lucid.
After trying the fixes suggested here, I found that it would work approx. half the time, but at other times it would give me the "Ubuntu is running in low graphics mode" message on startup.
After disabling the Nvidia 96 driver, I don't get this any more, but I don't get accelerated graphics either.

---

### Post by zerin on 2010-09-23
OK this is a fix to one of my posts. it turns out that in order for the nvnew.raw file to work you have to put this ```
Option "CustomEDID" "DFP-0:/etc/X11/nvnew.raw"
``` in xorg.conf. right under the Option         "UseDisplayDevice" "DFP-0" and it will fix the resolution problem. 

PS. sorry about your misfortune Pete317, i tried so many ways to get it to work and the only times using the nvidia drivers ever works is a clean install. Also i notice that 10.04 runs slower than 9.10 on these laptops, huh? even with nvidia drivers working on mine.

---

### Post by Shaocaholica on 2010-09-24
Thanks for this.  I'll try it tonight with my Toshiba 5005 which has a GeForce4 440.

---

### Post by Pete317 on 2010-09-28
Well, it's been even worse over the last week or two, ever since one of the automatic updates. Now it runs in low graphics mode full-time, even if the nvidia driver is disabled.

Any pointers/tips on how to do a clean install without having to re-install all my apps and everything afterwards?

---

### Post by zerin on 2010-09-28
[LIST]
[*]you could try to completely get rid of the nvidia drivers and reinstalling it using the **envyNG **tool in the Repository. The Command Line Version is easy to use. after you completely clean it out and reinstall the 96 Nvidia driver using **envyNG** you can try to repeat the steps in the original post.
[/LIST]


[LIST]
[*]If even that doesn't work. you can always install the free nvidia drivers, which i think are enabled by a default installation, but if you keep being forced to go into low res mode, then you may not be using it. you can install the free Nvidia driver by adding this PPA:
[/LIST]
```
sudo add-apt-repository ppa:xorg-edgers/nouveau
```Then upgrade the packages and install xserver-xorg-video-nouveau

```
sudo apt-get update && sudo apt-get upgrade sudo apt-get install xserver-xorg-video-nouveau
```but these drivers have no 3d accel, only 2d, so it will be a bit faster that what you are  on now. That's most the help i got, if it was of any help at all.

---

### Post by Pete317 on 2010-10-01
Well, I don't quite know how, because I was just trying everything and anything, but I think I eventually got it up and running.
What I can remember doing is:

1) completely removing the nvidia drivers
2) completely removing noveau and adding it to the blacklist
3) re-installing the nvidia 96 driver via synaptic
4) I then got a black screen after reboot.
5) Restarted in recovery mode, selected failsafe video, then
6) Ran nvidia-xconfig and edited xorg.conf as described in the OP

After rebooting once more, everything just worked!

Thanks, guys, for your help.

Now all I have to do is get my wireless connection working again.

---

### Post by Shaocaholica on 2010-10-02
What about a brand new install in light of the recent developments?  Just add one more step to the original guide by blocking the noveau update?

How do you do that exactly?

---

