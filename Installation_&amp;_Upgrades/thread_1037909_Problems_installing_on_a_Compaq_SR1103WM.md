---
title: "Problems installing on a Compaq SR1103WM"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by tilerwen on 2009-01-12
Where to begin.....

I am new to linux. I decided to install it on a Compaq SR1103WM, here are the specs:

Intel Celeron(P) 325 2.53 GHz
MS-6577M-ATX Motherboard
1.5 GB of memory PC2700 (this was upgraded from 256, haha)
40 GB hard drive and 160 GB 
It has an internal video card, I upgraded with a PCI FX5500 nvidia card

I burned a CD and was able to successfully install it on a laptop. Works great and I love it. I went to install it on my desktop and I am running into gobs of problems.

I tried to boot from the live CD and a message flashes saying: 
"Unable to load system description tables."
And then it would hang at the Ubuntu loading screen with the progress bar about 20 percent of the way complete.

After doing much research I found that if I disabled my external video card and hit F6 and typed acpi=off, it was able to start.
I was able to install it inside windows by using a partitioned drive. Now it starts and it gets to the login screen and after i type my username and password, the screen freezes.

It is stuck at a tan screen where I can see my mouse but I can't get any further. I tried to start and add acpi=off to the kernal but it still doesn't work.

My next step would be reinstalling again but I was wandering if anyone else had any ides.

Any help would be appreciated.

---

### Post by tilerwen on 2009-01-12
I figured out how to bypass this.

Since I am using the internal graphics card, apperantly it can't handle the "compiz special effects"

If anyone has this do the following:

1. From the Grub boot menu slect the “recovery mode” option.

2. Select “root       Drop to root shell prompt”

Type the following at the prompt:

3. sudo apt-get remove compiz

4. sudo apt-get remove compiz-core

5. exit

6. Select “resume      Resume normal boot”


This information was taken from "http://benaiah41.wordpress.com/2008/11/01/ubuntu-810-freezes-after-login-screen/"

---

### Post by Matrix7 on 2009-03-25
Very cool man - I have the exact same system (2GB of RAM and an PCI nVidia GeForce 6200OC Video Card though) and will give this a try tonight.  I want to install Kubuntu and Ubuntu Studio SO bad.  If this works you are my new hero.  I have ran across a couple more posts with similar errors around the forum and have directed them to this post to see if it is an across the board fix or specific to this hardware.

Will post back later telling if it works *fingers crossed*

Also - were you ever able to use your video card because I hate using onboard video...and I assume when you disabled your PCI you did so in the BIOS yes?

---

### Post by tilerwen on 2009-03-26
I am really glad that helped you. Yes I was able to use my video card, after much trouble. But it was worth it. ubuntu = awesome

Here was my instructions (My GFX card is different so your instructions will be different):

1) Switch to onboard graphics and install ubuntu (if dosnt work try acpi=off)
2) Boot into ubuntu under onboard graphics and run the envy script - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
3) to install the envy script you need module assistant which you can get from here - [http://packages.debian.org/unstable/devel/module-assistant](http://packages.debian.org/unstable/devel/module-assistant)
4) After running the eny script open up konsole and type - sudo nano -w /etc/modprobe.d/blacklist
5) add "blacklist agpgart" and "blacklist intel_agp" at the bottom
6) press ctrl x to exit and save
7) Now type in - sudo gedit /etc/modules
8) Add nvidia to the bottom, save and exit.
9) Now type in - sudo gedit /etc/hotplug/blacklist
10) Add "agpgart" and "intel_agp" to the bottom
11) Save and exit

Now the fun begins in editing the x.org file

12) open x.org - sudo nano -w /etc/X11/xorg.conf
13) Find the section device that lists your graphics intel graphics card
14) Make that section look like this
"Section "Device"
Identifier "GeForce FX 5500"
Driver "nvidia"
#BusID "PCI:1:9:0"
Option "NvAGP" "1"
Option "RenderAccel" "true"
EndSection

15) Find the section below that says "Screen"
16) Edit the Device row that currently lists your intel integrated card to "GeForce FX 5500'
17) Save and exit "ctrl x"
18) Reboot and change the bios to nvidia graphics card
19) Pray and hope that ubuntu loads properly
20) If dosnt then run - "sudo dpkg-reconfigure -phigh xserver-xorg"

After all this my computer had problems identifying my proper monitor settings, let me know if you have this problem and I will find my instructions to fix that.

Also ubuntu blacklists the onboard video, so you won't be able to install the compiz software, AT FIRST. However, I was able to fix that issue too, and I can find my instructions.

Let me know how it goes.

---

