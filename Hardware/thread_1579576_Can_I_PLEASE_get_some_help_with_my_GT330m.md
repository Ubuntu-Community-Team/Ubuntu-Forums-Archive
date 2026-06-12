---
title: "Can I PLEASE get some help with my GT330m"
date: 2010-09-22
forum: Hardware
---

### Post by CrAiZ3 on 2010-09-22
p { margin-bottom: 0.08in; }a:link {  }  I am using Ubuntu 10.04LTS 64bit. My problem is that using the current driver (not sure what it is) the resolution is 2048x1536. My GT330m card uses 1900x1200 resolution. I can switch to 1900x1200 resolution using my current driver but the same thing happens. And by same thing I mean the screen is cut off from about the date on the right, and on the bottom I cant even open minimized programs. Other  people using the same model laptop (Sony Vaio VPCF115FM) are having the same problems. The problem was apparently resolved with the 330m using one of  three methods, all of which I have tried and have not been completely able to figure out. The first method is an older method, and requires a raw file be exported from windows. The info I used can be found here.
   
 [http://forum.notebookreview.com/5820189-post2517.html](http://forum.notebookreview.com/5820189-post2517.html)
 

 only problem is when I enable the restricted drivers I can barely see the screen at all. It is nearly impossible to navigate and I end up going back to the default configuration. Also, I get errors when opening xorg.conf.
 

 The second method uses the actual Nvidia driver from there website. The one i'm using is NVIDIA-Linux-x86_64-256.53.run   Using method 2, backlisting  is required. I get all the way up to step 6, but when I reboot I do not get an error. I have tried running the driver file using terminal and it comes up and tells me I cant do it while in X. I use the command:  sudo /ect/init.d/gdm stop    and it takes me to a black screen with:
(Process:527):GLib warning **:getpwuid_r(): failed due to unknown user id (0)
*Speech-dispatcher configured for user sessions
*starting common unit printing system: cupsd
*Pulse audio configured for pre-user sessions
*Enabling addional executable binary formats binfmt support
*Checking battery state...


And this is where im stuck



[http://forum.notebookreview.com/5820189-post2517.html](http://forum.notebookreview.com/5820189-post2517.html)


Someone had mentioned in chat today to try this:
[http://ubuntuforums.org/newthread.php?do=newthread&f=332](http://ubuntuforums.org/newthread.php?do=newthread&f=332)

Can someone point me in the right direction?

Thanks ahead of time,
CrAiZ3

---

### Post by CrAiZ3 on 2010-09-22
Bumping myself..

---

### Post by scrams on 2010-09-24
I had the same exact problem, same exact pc. Starting with the ubuntu restricted NVIDIA driver, I did exactly what is described in the link below 3 days ago with a fresh install of Ubuntu and it worked just fine. 

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

You shouldn't have to do the steps listed on your first method. NVIDIA has released an x64 driver for the GT330m. I believe those steps pre-date the linux driver release.

If your getting hung up on the exit to console, you may be able to boot in recovery mode or change your run level once you have booted to install it... I didn't have that problem. I think having the the ubuntu maintained NVIDIA driver installed is what caused mine to crash and gave me the option to exit to console. If all else fails, just install it and then follow the steps in the link.

Hope this helps.

---

### Post by xyexz on 2010-10-09
Hey I just put Ubuntu on my laptop which is the exact same model! :D

I see the previous post has a dead link that's why I'm putting this here incase you didn't get to instructions.

I can help you as I'm 100% setup and loving it, hopefully I can create decent instructions for you.

1st thing if you don't have a lot on your ubuntu installation I would start with a fresh installation, so we don't have any drivers half installed from whatever testing you did before.

This command will help you see how many drivers nvidia-wise you have installed currently.
[PHP]lsmod | grep 'nvidia'[/PHP]

If you can't do that you'll have to search around a little on backing up and removing kernel modules.

Once you've assured that you've got a clean slate (with just the basic nvidia driver that ubuntu installs at the beginning or just some trash driver that works for 640x480 display) you need to follow these steps:

1) Download the latest driver from here:
[http://us.download.nvidia.com/XFree86/Linux-x86_64/256.53/NVIDIA-Linux-x86_64-256.53.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/256.53/NVIDIA-Linux-x86_64-256.53.run) (save it somewhere you'll remember. I'll use ~/Downloads in instructions)
If the above link doesn't work, go here: 
[http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html](http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html) and follow along screen prompts to download.
[PHP]cd ~/Downloads
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/256.53/NVIDIA-Linux-x86_64-256.53.run
[/PHP]

2) If you're currently in X Server hit Ctrl+Alt F1 to go to cli login prompt and login

3) Type this in to stop your current X Server session:
[PHP]sudo /etc/init.d/gdm stop[/PHP]

4) Then we need to execute the installer script:
[PHP]sudo sh ~/Downloads/NVIDIA-Linux-x86_64-256.53.run[/PHP]
(The first run it'll babble about the current driver not being disabled and it'll ask if you want it to disabled it with blacklist file, say yes)

5) Restart your computer and redo steps 2, 3 and 4

6) Follow all prompts and continue past any errors, if you get to the screen where it shows a progress bar for building the kernel module you should be in business.

7) Accept the prompt to allow it to generate an xorg.conf file (which will be stored in /etc/X11/)

8) Once it's all done restart and you should be presented with a nice layout, (your screen resolution native max is actually 1920x1080, which is true 1080p resolution)

Let me know if this works!

If you have issues with your sound let me know and I can help with that as well, also I can publish the very generic xorg.conf file that nvidia generated for me if you need to compare should any issues arise with your installation.

Editing to just go ahead and put the sound driver help for the issue people experience with this laptop and other like models (it's really easy to fix)

Run this command:
[PHP]sudo apt-get install linux-backports-modules-alsa-2.6.32-25-generic[/PHP]

That will fix your sounds, enjoy Ubuntu :D

---

