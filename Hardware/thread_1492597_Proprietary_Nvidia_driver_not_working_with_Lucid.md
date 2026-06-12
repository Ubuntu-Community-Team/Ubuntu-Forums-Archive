---
title: "Proprietary Nvidia driver not working with Lucid"
date: 2010-05-24
forum: Hardware
---

### Post by The Maxx on 2010-05-24
Hi, I'm using Ubuntu 10.04 on my Asus laptop with an Nvidia GeForce GT 220M video card. (When I run the "lspci | grep VGA" command it says "02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GT] (rev a1)")

When I was using 9.10, my proprietary driver worked perfect but after I did a clean install with lucid I started running into problems. After installing Lucid and running an update I opened up "Hardware Drivers" and installed "NVIDIA accelerated graphics driver (version current) [Recommended]" and restarted my computer. It showed the new Ubuntu loading screen but in a much lower resolution and with some flickering. After it finished loading I got a black screen with a window that said > **Ubuntu is running in low-graphics mode**

The following error was encountered. You may need to update your configuration to solve this.

(EE) May 24 19:14:19 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) May 24 19:14:19 NVIDIA(0):     System's kernel log for additional error messages and
(EE) May 24 19:14:19 NVIDIA(0):     Consult the NVIDIA README for details.
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.So I click OK and another window pops up asking me "what would you like to do?" with the options > O Run Ubuntu in low-graphics mode for just one session
O Reconfigure graphics
O Troubleshoot the error
O Exit to console login
O Restart X I went through the options but I'm not experienced enough to do anything with the information or options provided, so I chose to Run Ubuntu in low-graphics mode. Ubuntu then loads looking pretty blurry, and when I open up "Hardware Drivers" again it says "This driver is activated and currently in use." but I can't enable any effects and upon attempting to open "NVIDIA X Server Settings" I'm told "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." 

So I run sudo nvidia-xconfig in terminal and it tells me > Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default Screen".

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
...and I have no Idea what that means. So here I stand, can anybody help me with this because I am in way over my head here.

---

### Post by byStanderone on 2010-05-25
...take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1483898](http://ubuntuforums.org/showthread.php?t=1483898)

---

### Post by The Maxx on 2010-05-25
I followed the link and did everything in the instructions step by step, but still the same effect.

---

### Post by The Maxx on 2010-05-26
Doesn't *anybody* know what's going on here? I can't figure it out.

---

### Post by Shigoki-linux on 2010-05-26
i found this thread [http://ubuntuforums.org/showthread.php?p=9336057](http://ubuntuforums.org/showthread.php?p=9336057). maybe it will be of help?

---

### Post by steveneddy on 2010-05-26
> **The Maxx said:**
> Doesn't *anybody* know what's going on here? I can't figure it out.

Please don't forget that we are all volunteers here and no one is obligated to help.

Now here are my suggestions for your issue because I'm personally not having this issue.

1. Try a different video driver.
2. Search the forums for any one having the same issues.
3. Try Googling for the answer

After re-reading your original post I suggest you start the machine in low graphics mode and simply trying a different driver. Try to get to the nv driver via synaptic, just make sure that you uninstall the other nvidia driverat the same time, then restart.

Also try booting to a terminal and running this command without a GUI running:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by 2hot6ft2 on 2010-05-26
> **The Maxx said:**
> Doesn't *anybody* know what's going on here? I can't figure it out.
Hi Maxx,

The one piece of the puzzle you left out was if you are running 32 bit or 64 bit. In the 64 bit it comes with both kernels 2.6.32-22 and 2.6.32-21.
But 32 bit only comes with 2.6.32-21.
In the 64 bit you have to install the driver to the -21 kernel NOT the -22.
At the time of the release the -22 kernel was not a mainline kernel it was still a proposed kernel.

There is no need to blacklist things like some guides say. Forget about getting the -22 kernel to work in the 64 bit. It will work in the 32 bit though. We have had several things work like the server kernel works with it and many of us have it working with the 2.6.34 kernel.

I'm running the 2.6.34 kernel right now on a couple machines. A couple 32 bit installs and a 64 bit install. All with nvidia cards.
If you want to see a lot of what has been tried and what works and what doesn't take a look at this thread.
[Nvidia issues post here please.]("http://forumubuntusoftware.info/viewforum.php?f=68")

You'll find the trick to the 64 bit install using the -21 kernel along with the kernel options and other things that were tried.
:popcorn:

---

### Post by steveneddy on 2010-05-26
I'm running the -22 kernel and not having any issues.

Maybe this is a netbook issue?

---

### Post by The Maxx on 2010-05-27
> **steveneddy said:**
> Please don't forget that we are all volunteers  here and no one is obligated to help.

Sorry I wasn't trying to be rude, I just didn't know if I was the only person having this problem.

I'm running 64-bit. I tried installing an older driver (version 173) and it seems to work for the most part, but there are some problems, like when I first start up it makes the start-up sound but takes almost 10 seconds for the log-in box to pop up. Also some programs (mostly docky) have laggy animations.

This driver should work good enough for now, but if anyone has some suggestion I could try I would still like to try and get it working better than good enough :)

---

### Post by strobe on 2010-05-27
I have found that while using the Nvidia 173 driver on my Dell 8600 in Lucid environment that it will have a lot of lag.  Especially when playing videos.  In Karmic, CPU usage is around 50-75% when playing mp4 fullscreen.  In Lucid, it is maxed at 100% and stutters.  Something about the Lucid kernal has caused a lot of stress on the cpu when using the Nvidia driver on my system.  It is so bad that I had to go back to 9.10.  

A stable, functional, and smooth system is what I needed and Lucid doen't provide that for me.  I think it requires better specs than my laptop is capable.  Oh, and I can use Compiz and Emerald again while running smoothly on Karmic :guitar:.  No need to upgrade if it acts more like a downgrade.

---

### Post by Beanmonster on 2010-05-28
Maxx, I experienced the same issue and other problems like resolution settings not being saved after restart with lucid, even after fresh installs.

I guess my system and the nvidia-driver need a bit of help, unlike 9.10 that worked as is.

I di manage to find a solution and I hope it works for you and anybody else experiencing display/x-server/login problems after the driver install:

Boot into recovery mode from grub
In terminal:
```
 sudo -s
```
```
 service gdm stop
``````
 chown  -R ***YOURUSERNAME*** /etc/X11 
``````
 dpkg-reconfigure xserver-xorg
``````
 nvidia-xconfig
``````
 service gdm start
``````
 nvidia-settings 
```I restarted and things are all working nicely! Hope this works for at least one person out there :)

---

### Post by mango42 on 2010-05-29
Hi **Beanmonster** - thanks for the real nice clear 'magic words' - I'll give them a try once I reinstall everything 10.04 64bit UbuntuStudio (again^2).

I had finally got net access working after a couple of weeks head scratching - did all the updates straight away and loaded the nVidia 195 driver as recommended. Everything seemed fine. My problem started a day later when I foolishly decided to move the top panel to the bottom of the screen (on a mere whim, I admit!). Imagine my horror when nothing showed up but a shimmering gray bar - no icons, no menus, no nothing, not even right-click menus. Fiddled around with xorg.conf - nada.

So now, being clueless on this, I'm re-installing everything from scratch. I do still wonder what caused such an instant lobotomy, though I suspect if I had known of that ** service gdm start** command, Lucid Studio may have recovered.

---

### Post by davepimp00 on 2010-06-02
when you say "Boot into recovery mode from grub" how exactly do you do this?

---

### Post by Gadaph on 2010-06-02
Hi dave,

After your BIOS splash screen, push and hold the shift key.

That should get you into GRUB recovery mode.

It'll basically show you a list of boot options, including the different kernels on your system and their respective recovery modes.

Good luck.

Gadaph

---

### Post by farbird on 2010-06-02
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install nvidia-current

---

### Post by davepimp00 on 2010-06-08
> **farbird said:**
> sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install nvidia-current

and whats this mean??

---

### Post by farbird on 2010-06-10
it means to install a prepackage installation of the nvidia latest driver that is meant for lucid.

---

### Post by OldBitByter on 2010-07-09
> **farbird said:**
> sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install nvidia-current
Thanks farbird, those 3 lines replaced long lists of commands I'd been trying previously without success.  Everything on my system now seems to be working.  Good Job.

---

