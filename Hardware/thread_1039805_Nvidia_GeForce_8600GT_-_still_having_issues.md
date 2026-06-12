---
title: "Nvidia GeForce 8600GT - still having issues"
date: 2009-01-14
forum: Hardware
---

### Post by JawsThemeSwimming428 on 2009-01-14
I recently installed Ubuntu 8.10 on a Velocity Micro ProMagix that has a GeForce 8600GT graphics card. Didn't check to see if the graphics card had any issues and of course it did! I found a bunch of posts on the issues getting this card functioning but haven't found a solution that works for me. Drivers Manager pops up and says there are restricted drivers available. When I try to enable either of the two listed (177 or 173) it doesn't work and says another version of the driver is in use. However, I cannot enable desktop effects. If anyone can point me in the right direction I would be very grateful!

---

### Post by jespdj on 2009-01-15
Try this in a terminal:
```
sudo apt-get update
```
Then reboot and go to the Restricted Drivers Manager again to try to enable the driver.

I had to do that after first installing Ubuntu.

The nVidia 8600 should work fine; I have an nVidia 8600 GTS in my desktop and a 8600M GT in my laptop and both work fine with the restricted driver.

---

### Post by JawsThemeSwimming428 on 2009-01-18
> **jespdj said:**
> Try this in a terminal:
```
sudo apt-get update
```
Then reboot and go to the Restricted Drivers Manager again to try to enable the driver.

I had to do that after first installing Ubuntu.

The nVidia 8600 should work fine; I have an nVidia 8600 GTS in my desktop and a 8600M GT in my laptop and both work fine with the restricted driver.

Thanks for the reply. I had done all updates previous to trying to install the driver. I just re-installed Ubuntu on this machine and instead of trying the Restricted Drivers Manager, I tried manually installed the latest NVidia driver from the website (180.22). I followed the directions here [http://ubuntuforums.org/showthread.php?t=580779](http://ubuntuforums.org/showthread.php?t=580779). Everything said successful. When I tried to restart gdm I got a black screen with nothing on it. I waited 15 minutes and nothing came up. I manually rebooted the system and when it came back up I got the Ubuntu loading screen and then it went to the black screen again with nothing ever coming up to log in. I'm not sure what else to try here. Anyone willing to help me troubleshoot this I would be very grateful! I would really like to get Ubuntu on this machine as it is my main desktop. Thanks!

---

### Post by jespdj on 2009-01-18
Here are other instructions: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

You have to make sure that you do not have any of the Ubuntu nvidia packages installed, and add 'nv' to the disabled modules (see the instructions).

I'm now running the nVidia driver version 180.22 from the nVidia website, it works well on my laptop (8600M GT) as well as on my desktop (8600 GTS).

If you still get the black screen, try this:
- press Ctrl+Alt+F1 (this should get you to a text-based login screen)
- login
- type: dmesg | more
- see if you see any error messages there that might have to do with the nVidia driver (use 'q' to quit 'more')

Also have a look at logfiles in /var/log such as /var/log/Xorg.0.log

---

### Post by JawsThemeSwimming428 on 2009-01-18
> **jespdj said:**
> Here are other instructions: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

You have to make sure that you do not have any of the Ubuntu nvidia packages installed, and add 'nv' to the disabled modules (see the instructions).

I'm now running the nVidia driver version 180.22 from the nVidia website, it works well on my laptop (8600M GT) as well as on my desktop (8600 GTS).

If you still get the black screen, try this:
- press Ctrl+Alt+F1 (this should get you to a text-based login screen)
- login
- type: dmesg | more
- see if you see any error messages there that might have to do with the nVidia driver (use 'q' to quit 'more')

Also have a look at logfiles in /var/log such as /var/log/Xorg.0.log

I tried what you said and I am still not working. The only thing I didn't try because I wasn't sure of where/what to do is adding 'nv' to the disabled modules and getting rid of the nvidia packages...can you explain a little more, sorry.

I did check dmesg and showed a few segfault lines that ran similar to this:

Xorg[5130] segfault at 4 ip b7f425bf sp bfb53374 error 4 in ld-2.8.90.so

Not sure what that means, hopefully someone can help me out! 

From the link provided above I also added the following line to my xorg at the end of the screen section:

Option "UseDisplayDevice" "DFP"



Thanks.

---

### Post by Kossilar on 2009-01-18
Having the same issue on my R700 laptop. After fully updating the system I tried to use the restricted drivers manager to install the drivers and the system fails to load the X Server on startup. 

Apparently I have the NVIDIA-177 drivers installed already, which is odd since I never got them to work previously, however the system is not using them and I have no clue how to enable them.

---

### Post by JawsThemeSwimming428 on 2009-01-18
> **Kossilar said:**
> Having the same issue on my R700 laptop. After fully updating the system I tried to use the restricted drivers manager to install the drivers and the system fails to load the X Server on startup. 

Apparently I have the NVIDIA-177 drivers installed already, which is odd since I never got them to work previously, however the system is not using them and I have no clue how to enable them.


Sorry to hear you are having issues, but glad I am not the only one! Have you tried manually installing the drivers from the Nvidia website?

---

### Post by jskandhari on 2009-01-18
Goto system>Administration>Hardware Drivers  incase your nvidia 177 driver is installed just click on enable and then it will say to restart.. you can check it by logging out and re-login...

---

### Post by JawsThemeSwimming428 on 2009-01-18
In my case, the point is that doesn't work. I can install it but X does not start then.

---

### Post by Kossilar on 2009-01-18
I've tried manual installation of the nvidia 180 drivers as well as the 177 drivers. Neither work. The 180 drivers install correctly but fail to load on startup. The 177 drivers fail to install altogether.

The restricted driver manager does not work at all.

EDIT: Okay I just uninstalled and then reinstalled the nvidia-177* packages. The Hardware Manager is still failing.

---

### Post by JawsThemeSwimming428 on 2009-01-19
Still having this issue. Not sure what to do in order to get this graphics driver/card working. Any help would be appreciated. Thanks.

---

### Post by JawsThemeSwimming428 on 2009-01-29
I posted in the Nvidia forums ([http://www.nvnews.net/vbulletin/showthread.php?p=1910166#post1910166](http://www.nvnews.net/vbulletin/showthread.php?p=1910166#post1910166)) and no response either. I really could use a hand if someone would be willing to troubleshoot with me. I really would like to stay with Ubuntu.

---

### Post by probbins on 2009-01-30
This is a work-around that I found in another discussion,

Once you get to the black screen, use 

ctrl-alt f1

then 

ctrl-alt f7

This somehow resets the gdm and you should have a working screen.

I'm using a dual monitor setup and my main monitor goes black, these steps fix that.

This is on ubuntu 8.04, nvidia 180.22

There seems to be some problem between the latest kernel update and the nvidia 180 driver.

Strangly enough, the latest kernel update allowed me to install and have the 180.22 driver work (accept for the black screen), and have the Compiz desktop also work reliably.

One thing I haven't tried yet is to turn off the fancy desktop stuff and see if the problem persists. I'll be doing that later today.

---

### Post by Maheriano on 2009-01-30
I just got my 8600 GT working last night. I tried to turn on the Desktop Effects but they said they wouldn't enable. So I tried to turn them on to the medium setting and it said there was no suitable driver. Then I found a website with a program called something like Compiz Check and when I ran it, it told me I was using the NV driver instead of the proprietary driver and asked if I wanted to search for them. After I did so, it found them, downloaded them and installed. Then I was able to enable the Desktop Effects no problem.

---

### Post by jimv on 2009-01-30
Try this:

```
sudo apt-get remove --purge nvidia*
```

That will get rid of all of your current Nvidia drivers.

Then install the Nvidia driver from their website again, and make sure you say yes when it wants to update your xorg.conf file.

If you still get a black screen, press control+alt+f1 to drop to a terminal, log in, and type:

```
sudo /etc/init.d/gdm stop
```

Which will cancel the xserver, then type this to start it:

```
startx
```

This may give you an error that we can use to troubleshoot further.

---

### Post by Maheriano on 2009-01-30
[http://ubuntuforums.org/showthread.php?t=799070&highlight=desktop+effects+enabled](http://ubuntuforums.org/showthread.php?t=799070&highlight=desktop+effects+enabled)

---

### Post by dmalloch on 2009-01-30
> **jespdj said:**
> Try this in a terminal:
```
sudo apt-get update
```
Then reboot and go to the Restricted Drivers Manager again to try to enable the driver.

I had to do that after first installing Ubuntu.

The nVidia 8600 should work fine; I have an nVidia 8600 GTS in my desktop and a 8600M GT in my laptop and both work fine with the restricted driver.


=============================

I have just encountered the same problem with a desktop equipped with two geForce 8800's.  When I tried to activate the drivers I got the message "System error: E: Unable to correct problem, you have held broken packages".  The simple remedy suggested by jespdj worked perfectly and I was able to activate the driver without further problems.  Sometimes the simple solution works!

---

### Post by keroseneman on 2009-02-13
I got mine working after a few hrs of getting frustrated, I had both 173 and 177 installed by default;

I tried going to Nvidia.com and downloading new drivers but that failed, the site kept telling me I can't do that... 

I ran updates (there was a LOT) after install was complete I proceeded to reboot

After Reboot:

I tried activating 177 which downloaded and installed, requested reboot, after reboot nothing happened

I then tried installing 173 which downloaded and installed just like 177, requested reboot, after reboot my desktop was at 1440x900 by default

Everything works now, and I even have the Nvidia Server button under System.. thanks guys couldn't do it without reading about all the issues you have and getting annoyed that I might be screwed too! :lolflag:

---

### Post by JawsThemeSwimming428 on 2009-07-20
> **jimv said:**
> Try this:

```
sudo apt-get remove --purge nvidia*
```

That will get rid of all of your current Nvidia drivers.

Then install the Nvidia driver from their website again, and make sure you say yes when it wants to update your xorg.conf file.

If you still get a black screen, press control+alt+f1 to drop to a terminal, log in, and type:

```
sudo /etc/init.d/gdm stop
```

Which will cancel the xserver, then type this to start it:

```
startx
```

This may give you an error that we can use to troubleshoot further.

Following these instructions, and using the latest nvidia driver (185), I was able to get Ubuntu working with the driver on this machine. Nothing else posted had worked. Thanks!

---

