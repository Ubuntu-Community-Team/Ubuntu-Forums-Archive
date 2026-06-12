---
title: "Problems with 8.04 install with NVIDIA geforce 7400 graphics card"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by mnia on 2009-10-19
Hello.
Firstly, I'm a newbie, so please use small words :-)

I'm trying to install ubuntu 8.04 on my Dell XPS 1210 laptop. I have run into problems with the **graphics card** which is a **NVIDIA geforce 7400** card.

When I start the computer, I firstly get the message:
*"There was an error loading the theme Human. Can't open file /usr/share/gdm/themes/Human/Human.xml"*
which I assume is because my graphics card driver isn't set up correctly.

I then go the the login screen, which is a low graphics screen (not the usual brown ubuntu screen), that has a yellow flower on a blue background. When I login, everything is crappy resolution (and I can't change the screen res) and a file manager window flashes on and off before disappearing.

Following the advice in several threads, I installed envy, and then selected the option: "Install NVIDIA driver" (using the automatic detection setting). Envy completes this, but when the computer is restarted I get the same problem.

I have tried going into System>Administration>Restricted Drivers Manager and disabling the NVIDIA driver, then restarting. Didn't help. I tried enabling it then restarting. Didn't help. I tried disabling the driver, then running envy again.

After enabling the driver, when I restart, I get the following message:
*Ubuntu is running in low-graphics moded. Your screen and graphics card could not be detected correctly...*
I then select the configure button and choose the Graphics Card tab, where I specify the driver to be the Nvidia 7-series driver (I tried both open source and restricted options). Doesn't work, but i'm not sure I'm manually selecting the right one. 

I also tried uninstalling linux-restricted-modules & nvidia-kernel-common, then reinstalling them ...following the advice in [http://ubuntuforums.org/showthread.php?t=1277880&highlight=nvidia+geforce+7400+install+8.04+hardy]("http://ubuntuforums.org/showthread.php?t=1277880&highlight=nvidia+geforce+7400+install+8.04+hardy")

Confused. Very stuck. 
Please help!
Thanks :KS

p.s. Output from nvidia-xconfig:
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout; using the first mouse device.

WARNING: The CoreKeyboard device was not specified explicitly in the layout; using the first keyboard device.

ERROR: Unable to write to directory '/etc/X11'.

---

### Post by stlsaint on 2009-10-20
for the human.xml error run this :
```
sudo apt-get install ubuntu-artwork
```

and for xorg/gdm try stop/reconfigure/restarting

stop:
```
sudo /etc/init.d/gdm stop
```

reconfigure Xorg
```
sudo dpkg-reconfigure xserver-xorg
```

restart
```
sudo /etc/init.d/gdm start
```


from there you should be back to square one we can start helping you troubleshoot more.

---

### Post by mnia on 2009-10-20
> **stlsaint said:**
> for the human.xml error run this :
```
sudo apt-get install ubuntu-artwork
```


Ok, ran this and got an error saying that the package wasn't installed. So I started synaptic and it tells me that the ubuntu-artwork package is broken. 

How do I fix this?

> **stlsaint said:**
> 
and for xorg/gdm try stop/reconfigure/restarting

stop:
```
sudo /etc/init.d/gdm stop
```

When I ran this, my computer shut down. On restart, I do now see the correct login screen. 

> **stlsaint said:**
> 
reconfigure Xorg
```
sudo dpkg-reconfigure xserver-xorg
```

There were a lot of options in the reconfigure that I was unsure about, so I tried to just select the default options where possible. I hope I haven't screwed something up here.

> **stlsaint said:**
> 
restart
```
sudo /etc/init.d/gdm start
```

Ran this and restarted my computer.

Current situation:
[LIST]
[*]On restart, I get the message that: *'Ubuntu is running in low-graphics mode. Your screen and graphics card could not be detected correctly.'*
[*]So I select the Configure button, and choose the driver for my graphics card. I selected NVIDIA Geforce 7 series (OpenSource Driver), which sounds like the most likely option.
[*]I then get to the correct log on screen (standard ubuntu brown one), rather than the blue one that I had before. So this bit is fixed.
[*]When I have logged on, I get the file browser window flashing on and off several times before it disappears (which is odd).
[*]The screen resolution is crap. Under System>Preferences>Screen Resolution I only have the options 800x600 and 640x480, even though in the "dpkg-reconfigure xserver-xorg" step above I selected the option for screen res to be 1024x780. 
[*]I tried running glxgears to see if my graphics card is working, and I get the error: *Xlib: extension "GLX" mission on display ":0.0". Error: couldn't get an RGB, Double-buffered visual*
[*]Output from nvidia-xconfig is the same as my first post.
[/LIST]

So I take from all this that I haven't got my graphics card configured properly, or the driver set up, or something. 
Any further help is much appreciated!
Thanks!

---

### Post by mercury00 on 2010-02-18
Same here.  Has anything you've tried gotten this fixed?  Is there anything else someone can suggest?

---

