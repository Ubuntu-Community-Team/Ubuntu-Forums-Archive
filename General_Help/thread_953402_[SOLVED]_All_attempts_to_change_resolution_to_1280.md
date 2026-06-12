---
title: "[SOLVED] All attempts to change resolution to 1280x900 failed"
date: 2008-10-20
forum: General Help
---

### Post by HungryMan on 2008-10-20
As of now I am tired and I turn to the forums now for help with my annoying predicament.

I installed updates last night (seemed like kernel updates, as the packages were "linux" and "linux-headers" or something like that.) turned off the computer and went to sleep. Next day, I found that my max screen resolution was 800x600 and Compiz didn't work.

I went to system>administration>hardware drivers and it said something that shocked me: "Your device does not use any proprietary drivers" Just less than 12 hours ago, I was using the proprietary nVidia drivers.

I tried editing xorg.conf countless times, but still, no effect.

I tried installing the nVidia driver from nVidia themselves, but only got a max resolution of 1024x768.

I tried tinkering with the settings at displayconfig-gtk (I think I changed the driver though ](*,)), and got a max resolution of 800x600 again

Then I edited xorg.conf countless times again, I got more choices for the screen resolution, but abysmally low values (640x480-320x240 wtf?!)

And now, I ask for help, either in changing my resolution back to 1280x900 and get compiz back or roll back the updates. PS. Compiz really isn't the main priority. MY EYES HURT SO BADLY with such a low resolution and would like to get back to 1280x900 right now. Thanks in advance!

BTW, my graphics card is nVidia GeForce FX 5000 (at least that's what it says when the BIOS boots up.), Ubuntu 8.04. Please ask if I'm missing something.

---

### Post by HungryMan on 2008-10-20
ok, now I'm just frigging annoyed. gedit won't even start *sigh*.
I guess im just going to do a clean install.:cry:
I give up.

---

### Post by RobOrr on 2008-10-20
the new kernel .21 has caused problems with many people's computers, with such wierd and wonderful effects as removing firefox's bookmark ability, killing your panels if you click on the quit button, and generally pissing about with nVidia cards. 

I had a couple of these problems, which went away when i removed the .21 kernel and reverted back to .19

to remove it, use

> sudo apt-get remove linux-restricted-modules-2.6.24-21-generic
and to remove it from grub,
> sudo gedit /boot/grub/menu.lst

and then scroll down a fair bit to reach the options (its probably worth giving the file a quick read, it controls your Grub bootup menu) where you can either delete or comment out (put hashes in front of) the .21 line, so that when you power on you never accidentally try to load a kernel that isn't installed.

---

### Post by bubbalouie on 2008-10-20
Perhaps the following may help:

   sudo apt-get install nvidia-settings

Then:

   sudo nvidia-settings

Pick a resolution, apply, if it works, save the setting to xorg.conf....

On the off chance you are not using the driver a all you may need to run:

   sudo nvidia-xconfig

Then restart X (ctrl+alt+backspace), make sure you close everything ebfore restarting X BTW.

I have not had to edit xorg.conf to change resolution in a few years by using this method on systems with nvidia cards.

Good luck.

Ryan

---

### Post by HungryMan on 2008-10-22
Thanks RobOrr, good thing I looked back here before reinstalling ubuntu! I'm going to do that when I'm not busy, so I can use Blender again.

I did get the desired 1280x960 (not 900 btw) after changing cards (an old one with no hardware acceleration) and being persistent with replacing my new settings with the older, perfect settings. Does anyone know why it suddenly worked the nth time I've been doing EXACTLY the same thing (replacing the new xorg.conf with the older xorg.conf)?

Here's what I did:
replace current xorg.conf with the old, working one, restart X, it says screen and monitor not detected correctly (sometimes, nothing happens), dpkg-reconfigure xserver-xorg, repeat.

Thanks again in advance!

---

