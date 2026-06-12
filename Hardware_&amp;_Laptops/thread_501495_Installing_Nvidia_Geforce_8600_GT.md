---
title: "Installing Nvidia Geforce 8600 GT"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by TaylorHelferty on 2007-07-15
I just bought the Nvidia Geforce 8600 GT video card and have it installed on my Vista and XP partitions fine. However, I'm having problems getting it to install in Ubuntu. I'm still fairly new to Linux, keep in mind.

I tried going to the restricted drivers manager, since all my other nvidia cards just showed up there and it would download/install the drivers for me. This time there was no restricted driver. So I went to the Nvidia website to download the drivers manually, went to install them, and it said I need to exit the X interface. How do I do this? If someone could give me some step-by-step instructions on how to install this driver, that'd be awesome. I'm sure it's not hard and I'll be kicking myself later, but you can't attempt something when you don't know how to go about attempting it. I read somewhere that ctrl-alt-backspace exits the X interface, but that just brings me to the login screen. So that didn't help much. Any help would be appreciated. Thank you in advance.

---

### Post by w4ett on 2007-07-15
try using the ENVY script for the driver installation.  A lot easier than hand installing.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by TaylorHelferty on 2007-07-29
Sorry for the bump.

I tried Envy, didn't really work. It said it was all installed well, but I couldn't get full resolution and there were still a lot of random graphical errors. Like videos not playing properly, etc. Also there's this problem: Since I put in the new video card, when I boot into Ubuntu (I have a triple boot with Vista and XP), it doesn't show the whole Ubuntu loading screen. The screen turns off until I get to the welcome screen. Well, lately, it won't boot up at all. It just hangs. And since the screen stays off until the welcome screen, I can't see what the problem is. Any one experience this before/have a diagnosis? Any help would be appreciated. I miss my Ubuntu . . .

I also booted into recovery mode and attempted installing the nvidia drivers manually from that, and it said it installed successfully, but I still can't get into Ubuntu and the screen stays off until the welcome screen, which doesn't seem to want to come.

---

### Post by David A Knight on 2007-07-29
as w4ett says, use the ency scripts or install the driver from nvidia.com yourself.  Your graphics card is too new to be supported by the driver available in ubuntu (newer drivers only appear late on in the development versions)  As such the restricted drivers manager is no use.

To exit the X interface you need to drop to the console, alt+ctrl+f1  or alt+ctrl+f2, f3, f4, etc.  Then you need to stop X/gdm running.  

sudo /etc/init.d/gdm stop

then run the installer.

sudo NVIDIA-whatever-it-is

once the installer is done

/etc/init.d/gdm restart to get X started again.

---

### Post by TaylorHelferty on 2007-07-31
Thank you for the help! I got it all working. A couple other quick questions though. Sorry for them, as they're probably simple, but I'm still very new to Linux. 

1. When I start up and shut down, the screen turns off while Ubuntu loads or shuts down, and (when starting up) doesn't come back on until the welcome screen. Before that, the screen stays off. This is mostly a mere annoyance, but it can be more sometimes when there's an error and I can't see what it is to fix it since my monitor won't come on. Is this just something I have to live with currently until there is more support for my video card? Or is there a way to get around this now?

2. I just restarted my computer and the resolution reset back to 1024x768, so I had to go back to the video card options and set it back. Any explanation?

Thank you for all the help so far and in advance for the help I hope to receive for the above small issues.

---

### Post by wizochelle on 2007-09-16
Bump
I am trying to manually install my Nvidia  card as well (8600 GT) the problem is that I tried installing it following different instructions and now I get and error and I don't get the welcome screen.
anyone could tell me how to uninstall nvidia without gui access?
Thanks!

---

### Post by w4ett on 2007-09-16
> **wizochelle said:**
> Bump
I am trying to manually install my Nvidia  card as well (8600 GT) the problem is that I tried installing it following different instructions and now I get and error and I don't get the welcome screen.
anyone could tell me how to uninstall nvidia without gui access?
Thanks!

I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by wizochelle on 2007-09-17
Thanks,
your suggestion worked; restricted drivers failed to notice my card so I used envy and it worked; now I have my gui back; I got a weird screen upon reboot; looks like it failed to start ubuntu and the final line tells me that apt-get is not installed; nothing works on the keyboard and when I click ctrl+alt+del  it starts ubuntu
so it works but is weird... well at least I can play with my ubuntu again.
Thanks!!

---

### Post by rojanu on 2007-09-18
I am having problems with my GeForce 8600 GTS I get little distorted squares
[screenshot]("http://malinux.homelinux.com/apache2-default/")

I then switched back to nv and screen is OK

---

