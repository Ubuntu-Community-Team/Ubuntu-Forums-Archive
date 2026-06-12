---
title: "problems with nvidia driver"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by asafdav2 on 2007-09-14
hello. i'm a fairly new linux user, with kubuntu 7.04 installed an nvidia 6600gt based video card. 

_the history_
at the beginning i installed the 'nvidia-glx' video driver and it workd allright for some time. the problems started (if i remember correctly) when i noticed the 'nvidia-glx-new' driver, which i believed was better suited to my card. i removed the 'nvidia-glx', installed the 'nvidia-glx-new' and restarted. however during boot, after the kubuntu screen with the loading bar, when the bar finished loading i saw a very quick text message (i believe it was there before) i'm seeing again the kubuntu screen with the bar, however this time it's empty for a couple of seconds and then i'm getting to  a blank screen with text curser in the upper left corner. i can write in it using the keyboard but that's about it. pressing alt+f4 allows me to login to my accout in textual mode.  what i did was to edit the xorg.conf file and change all instances for 'nvidia' driver to 'nv'. it happened to work and i was able to start kde. i tried moving back to 'nvidia-glx' driver but the same thing happened, so i just stayed with 'nv' for some time. 

_the problem_
the problem is that this happens again, and this time neither 'nv' nor 'nvidia' in xorg.conf seem to work - so basically i cannot get into kde.

thanks in advance

---

### Post by eggdeng on 2007-09-14
Try ```
Driver    "vesa"
``` to get a GUI.
You want to remove all the old packages
```
sudo apt-get remove nvidia-glx nvidia-glx-new
```
```
sudo apt-get remove nvidia-settings
``` before you reinstall the new ones.

---

### Post by asafdav2 on 2007-09-15
well i tried this but it doesn't seem to work. i even went out, reformatted and installed ubuntu this time. the problem is pretty much the same - whenever i install the nvidia-glx / nvidia-glx-new driver and enable it, i'm getting a blue textual screen on boot after the ubuntu loading bar finishes saying that there's a problem with my X video driver (or something like that, dont remember exactly). i can get regress by coping the xorg.conf backup over. i tried installation thru synaptic / the 'restricted driver' in the menus, same thing. maybe i should try installing using the nvidia .run script? i tried but it asked me to shut down X first and i'm not sure how to do it

edit: one thing to add is that it won't let me have both nvidia-glx and nvidia-settings installed together. not sure if it's important

---

### Post by w4ett on 2007-09-15
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

1. Use the restricted drivers manager in Ubuntu Feisty and above: , System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from Nvidia: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions remove the previous install attempts and  to  install the correct Nvidia proprietary driver.

Good Luck

---

