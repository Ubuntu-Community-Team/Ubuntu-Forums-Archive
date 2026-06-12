---
title: "nvidia again!"
date: 2018-12-11
forum: Hardware
---

### Post by thomas_j_marshall2 on 2018-12-11
Had problems with a Nvidia 1030 graphics card in 18.04, low resolution and then went into a loop, couldn't get a graphical login.  I never got it resolved, reverted to xorg or Noveau, not sure.  So recently I did a fresh install of 18.10 and it worked perfectly, used the Nvidia driver.  Just the other day I logged in and the resolution is low, 1024×768 I think and can't change it.  I reverted to noveau and still the same.  Any ideas?

---

### Post by Autodave on 2018-12-11
What driver are you using?  It should be the 410.78.

---

### Post by thomas_j_marshall2 on 2018-12-11
390.  Running update that is what is installed.

---

### Post by CatKiller on 2018-12-11
That sounds exactly like it didn't pick up the EDID from your monitor. Since it worked before, check your cabling.

---

### Post by Autodave on 2018-12-11
The 390 driver is fine.  +1 with CatKiller: especially if it is a VGA cable.  If VGA and connections are good, try another cable.

---

### Post by thomas_j_marshall2 on 2018-12-13
Thanks.  I'll try another cable.

---

### Post by phototed on 2018-12-13
I've got the same problem.

I was running 18.10 with the drivers from ppa and one day the resolution dropped to 800x600.  I tried everything and could only get the full resolution by removing the ppa drivers.  The default drivers work, sorta but poorly so I'd like to get back to better drivers.

To be sure nothing else was going on I just did a fresh install, installed the ppa repo then the recommended driver.  Back to the unrecognized monitor and 8x6.  I didn't believe that cabling would suddenly change the behavior but for completeness I did try different cables.  Still not working.

It's possible the problem started after a SW refresh - My kernel is the latest: 4.18.0-12-generic.

Any ideas anyone?  Should I go through the hassle of installing and compiling the proprietary nVidia drivers?

---

### Post by CatKiller on 2018-12-13
**phototed** your symptoms are quite different from the OP's. They have low resolution regardless of driver version. You are only getting a low resolution with a particular driver version. I'd suggest you start a new thread to see if someone can help you. You should also include hardware details in that thread.

---

### Post by thomas_j_marshall2 on 2018-12-14
Haven't been able to try a replacement cable yet.  I dual-boot with windows 10 and no problems there.  Hoew likely is it that the cable is at fault?

---

### Post by CatKiller on 2018-12-14
> **thomas_j_marshall2 said:**
> Haven't been able to try a replacement cable yet.  I dual-boot with windows 10 and no problems there.  Hoew likely is it that the cable is at fault?

A dodgy or poorly-connected cable would cause those symptoms. There may be other things that would also cause those symptoms.

Windows doesn't rely on EDID in the same way as Linux does, so it's not an accurate troubleshooting test. Manufacturers will give Microsoft all the important details of the monitor as a "driver" (it isn't really a driver) that they won't do for us.

It *is* possible to set the resolution and timings for the monitor manually, but it's a bit of a pain to do so compared to simply unplugging and replugging a cable, or swapping one for another.

---

### Post by thomas_j_marshall2 on 2018-12-14
OK thanks, I'll get a cable.  Had it a few years!

---

### Post by Autodave on 2018-12-14
If you go into Settings -> Display, does it properly identify your monitor?  What is the largest screen that it lists?

---

### Post by thomas_j_marshall2 on 2018-12-20
New cable, same deal, low resolution.

---

### Post by thomas_j_marshall2 on 2018-12-20
> **Autodave said:**
> If you go into Settings -> Display, does it properly identify your monitor?  What is the largest screen that it lists?No, unknown monitor and 1024 x 768

---

### Post by CatKiller on 2018-12-20
> **thomas_j_marshall2 said:**
> New cable, same deal, low resolution.

> **thomas_j_marshall2 said:**
> No, unknown monitor and 1024 x 768

That means it's definitely been without EDID. The EDID would contain a name.

The Nvidia Settings has a re-detect displays button that you should try. You should also see if there's anything in ~/.monitors.xml that could be interfering. You should probably check /var/log/Xorg.0.log too. 

We can look at giving you a modeline after that.

---

### Post by thomas_j_marshall2 on 2018-12-20
Running nvidia settings gives a dialogue box that is blank, title bar is nvidia x-server... and help an quit buttons.

---

### Post by thomas_j_marshall2 on 2018-12-20
Command line gives:

login:~$ nvidia-settings

ERROR: NVIDIA driver is not loaded


ERROR: Unable to load info from any available system


(nvidia-settings:3731): GLib-GObject-CRITICAL **: 18:44:04.945: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

---

### Post by CatKiller on 2018-12-20
OK, so it looks like you aren't using the nvidia driver after all. You should look to get that installed, since the nouveau driver won't be able to clock your graphics card above the minimum.

---

### Post by thomas_j_marshall2 on 2018-12-22
Well got fed up fiddling about and reinstalled 18.10 so working now on nouveau.  I think the thing to do is stay away from the nvidia drivers.

---

### Post by CatKiller on 2018-12-22
> **thomas_j_marshall2 said:**
> Well got fed up fiddling about and reinstalled 18.10 so working now on nouveau.  I think the thing to do is stay away from the nvidia drivers.

That is exactly the opposite of what you should do, but it's your computer.

---

### Post by thomas_j_marshall2 on 2018-12-22
> **CatKiller said:**
> That is exactly the opposite of what you should do, but it's your computer.Not sure what more I could have done.  I have been trying for a week to no avail, nothing was working.

---

### Post by jerry47 on 2018-12-23
Ubuntu 18.04 or 18.10 does not play well with my Nvidia GPU either. Either the nouveau driver or Nvidia driver. My motherboard is a P8Z77-V Deluxe. Grub screen was not displaying the resolution detected in Grub configuration. The Plymouth screen lost its animation and was reduced size. I pulled the GPU out to check the onboard intel graphics and all went full size resolution. I then put it back and installed Manjaro Deepin and had no issues at boot. All full size. Both have stuttering audio issues that have not been resolved.  I tried one more new install for Ubuntu same issue with Nvidia GPU. Just before I formatted the SSD again Ubuntu got stuck at boot just looping and never got to the desktop. For now just went back to Win 7.

---

### Post by vidtek on 2018-12-23
Nvidia drivers are problematic on linux.  This is even more obvious since xorg.conf was deprecated.

I now have a tailor-made xorg.conf with all my video, keyboard and mouse settings fine-tuned the way I prefer them.  The same result is probably impossible without an xorg.conf file.
If you are presented with a black screen on login, go to a terminal and edit/create an xorg.conf file and where it gives the driver name as nvidia, replace it with vesa.  That will then give you a low-res working gui.  From there it is easier to troubleshoot.

---

### Post by Autodave on 2018-12-23
I have 4 machines here running Nvidia cards: 2 on 16.04 and 2 on 18.04.  Cards run from cheap to expensive. And not a single issue running the drivers from the repositories.

---

### Post by thomas_j_marshall2 on 2018-12-23
> **vidtek said:**
> Nvidia drivers are problematic on linux.  This is even more obvious since xorg.conf was deprecated.

I now have a tailor-made xorg.conf with all my video, keyboard and mouse settings fine-tuned the way I prefer them.  The same result is probably impossible without an xorg.conf file.
If you are presented with a black screen on login, go to a terminal and edit/create an xorg.conf file and where it gives the driver name as nvidia, replace it with vesa.  That will then give you a low-res working gui.  From there it is easier to troubleshoot.For me the trouble is I don't have the technical knowledge to tinker.  I can use the command line and follow instructions but that's it.  I've had problems on and off with most versions of ubuntu, both with nvidia and radeon.  I understand it's because the vendors don't share the code but it doesn't make it any less of a pain.

Picking up [**[COLOR=#000000]Autodave[/COLOR]**]("https://ubuntuforums.org/member.php?u=917298")'s point, I am running ubuntu on a laptop with no problems at all.

---

### Post by jerry47 on 2018-12-23
I'm running Ubuntu 18.10 on an Intel NUC7i7BNH with no issues at all. But there was some collaboration between Canonical and Intel on that generation with the version just before 18. Only problem I had was one time while it was just sitting there unattended, gnome crashed. With not being able to find a solution for the Asus Z77 sound stuttering problem. I'm starting to see my own posts now. Its been a couple of months trying to fix it using all the recommended solutions dating back a decade. So I'm not alone. Its a pulse audio Alsa issue. Manjaro is on the test SSD right now. No issues with Nvidia driver or booting with reduced resolution. So that's the one I'm going to concentrate on for now. If I can get it fixed on that Distro no doubt it will solve it for Ubuntu.

---

