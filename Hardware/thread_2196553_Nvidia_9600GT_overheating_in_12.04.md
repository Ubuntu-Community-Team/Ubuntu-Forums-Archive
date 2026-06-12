---
title: "Nvidia 9600GT overheating in 12.04"
date: 2013-12-30
forum: Hardware
---

### Post by Roinou on 2013-12-30
Hi all,

I seem to have quite disturbing problems using my nvidia 9600 GT card over a server installation of Ubuntu 12.04. Whatever nvidia driver I install, my GPU overheats and shuts down the PC.

Here is the situation:

My old desktop was running an Ubuntu 11.10. I was running compiz and using it as an everyday computer worked just fine.
After 3 years in the cellar, I decided to dust it and start hobby mining. I therefore installed a fresh Ubuntu server, 12.04 LTS. Until there, everything works fine. I can SSH to it and administrate like a charm.

Now, I tried to install twice Nvidia drivers, and they both created the same issue:
- the driver from Ubuntu repo, 319.32
- the driver from Nvidia cuda .run package, 319.37

What happens is that, after I restart the computer, I can monitor the GPU temperature, and it start rising 1°C every 5 or 10 seconds. After 10 minutes, the temp is up to 100°C. After 15 or 20 minutes, boom goes the server. I have to manually restart the computer, as it crashed completely. What is weird about this, is that I have no Xserver running at all, nor any GPU consuming application. Just the server installation, with a LAMP, a SSH and a PostgreSQL, no more.

So here are my questions:
- is this a known bug from the Nvidia driver? Has anyone experienced this before? I will try to install an earlier version, but I'm really curious.
- how can I unload / load the driver at startup easily? If I want to test this or that driver, I want to be able to not load the nvidia module at startup and only loaded manually when I'm ready to test. If not, I only have about 10 minutes of work before the machine goes down.


Any thoughts/tips would be welcome to help me debug this.

---

### Post by Kirboosy on 2013-12-30
Is the fan working on the 9600GT? I had a problem with my 9400GT where the fan bearing froze and the fan bound up completely. I found a replacement fan onE-bay for 10  bucks and replaced it. Everything was balmy cool after that.

I currently run Ubuntu 12.04 64 bit on my server (which has a 9400 GT) I don't have any problems whatsoever with it. I even have it Cuda mining for fun. (BTW if you want really good mining performance you might want to upgrade your card. The 9x cards are quite weak for mining.)

Hope that helps!
~Caboose

---

### Post by oldfred on 2013-12-30
I have nVidia 9600GT and run full Ubuntu but not Unity, but fallback and have no issues. I working install is 12.04 but I have installed just about every version and most have the nVidia driver installed. 
Fans kick in at high speed just for a few seconds while booting and then when driver seems to load they slow down and I never do anything that seems to turn them back to high speed.

I only install the most recent version from repositories. Years ago I tried a direct download and had huge issues, so have avoided that since. 

You cannot download nVidia's and install from repository without then having conflicts. You need to totally erase all trace of nVidia from one install before attempting to convert to the other.

---

### Post by Roinou on 2013-12-31
Thanks for the answers, but I think I found the real issue here.

I'll explain what I did, it's very simple.

I installed the **xubuntu-desktop** package to have a X server running on my server. Then I installed the 304 nvidia driver from the .run package of Nvidia official site. Restart the server, and launch "nvidia-smi" to see the temperature. I checked at a few intervals, it tops at 56°C. Great, no problem there. Now, kill the X server by a simple "sudo service lightdm stop". I checked the GPU temperature, and now it raises very fast to 70 or even 80°C. I panic and reboot the server. Temperature is stable at 55°C.

hum... now let's make the test even more simple:
- stop the lightdm daemon -> temperature rises very fast
- start the lightdm daemon -> temperature drops back to normal

I installed again the 319.37 packaged in the CUDA 5.5 installer, and the behavior is the same.

I guess the nvidia driver MUST have an Xserver running to work properly.

I'm now mining LTC on the GPU with a stable environment, temperature not exceeding 76°C, fan only at 65% of speed. I could maybe even push it a bit :)

hope that will help someone!

---

