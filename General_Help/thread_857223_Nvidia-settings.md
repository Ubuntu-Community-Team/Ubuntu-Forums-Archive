---
title: "Nvidia-settings"
date: 2008-07-12
forum: General Help
---

### Post by Goldpin on 2008-07-12
I'm running an Nvidia DDR 256 card under Hardy.  I've installed an NVIDIA driver using EnvyNG.  However, I can't get the screen resolution to go above 1024x768.  If I try to access the nvidia-settings, I get the following message:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

When I run nvidia-xconfig the NVIDIA icon in the system administration menu disappears (although the menu item remains).  The screen resolution is completely wonky and I have to remove and reinstall the NVIDIA driver. Also I cannot enable the desktop effects.  Has anyone any ideas or suggestions?

When I first installed Hardy, I could get quite a range of resolutions higher than 1024x768.  This is driving me up the wall

Thanks in advance

---

### Post by chazdraves on 2008-07-12
Well... I'd say your driver's not working then. This works for me with three different cards (7300GS, 8800GT, and 9600GT), so - hopefully - this should work for you. I found this elsewhere on the threads, so my apologies for not giving credit to the proper person as I cannot remember who posted it.

1. Download the latest NVIDIA drivers from their site ([http://www.nvidia.com](http://www.nvidia.com))

2. Rename the driver file to "NVIDIA.run" (this will make it easier later on)

3. Open up the Terminal

4. "sudo apt-get remove linux-restricted-modules-common linux-restricted-modules"

5. Also, make sure nvidia-glx-new or any others are not installed via Synaptic

6. "sudo apt-get install pkg-config xserver-xorg-dev build-essential"

7. *** Before doing this, make sure you have the rest of the instructions written down as you will no longer be able to access Firefox *** Stop GDM by running "sudo /etc/init.d/gdm stop". This will bring you to a command prompt outside of X

8. Go to the location of the driver file (should be Desktop, so "cd Desktop").

9. "sudo sh NVIDIA.run"

10. "Okay, Accept, and I Agree" your way through the installation. The installer should mention that it will compile an interface for your driver. Just say "yes" :)

11. Once it's finished, "sudo /etc/init.d/gdm start" and you should have proper video.

I literally just did this with my 9600GT, just minutes ago. Hopefully this works for yours as well. If not, post your findings here and we'll all try and help you. Also, when I did it, I had to try twice before it got everything right. Not sure what happened there, but the point is that I would use this method over envy.

Good luck!
- Chaz

---

### Post by blackbird020377 on 2008-07-12
here's what i've done to get my resolution back and enabled the nvidia card:

1. remove the driver for your nvidia, remove nvidia-settings and nvidia xconfig then restart your pc.
2. after restart you may be ask to configure your display settings... just choose the one that suits your device.
3. after login, install your nvidia driver (nvidia-glx-new or nvidia-glx... pls try any of those 2 drivers that i mention.
4. run nvidia-xconfig on terminal
5. install nvidia-settings
6. restart your pc

if you get the correct resolution on your screen most likely that you have installed the correct driver for your nvidia card :).

i you find this helpful

---

### Post by Goldpin on 2012-05-23
My old computer packed up.  The new one has a more modern video card.  Works like a champ!

---

### Post by overdrank on 2012-05-23
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

