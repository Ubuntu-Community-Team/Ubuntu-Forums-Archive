---
title: "Nvidia"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by storybookhero on 2005-06-10
how do you install Nvidia Drivers? I'm lost new to linux.

---

### Post by Xian on 2005-06-10
Look in the Starter Guide: [Install Nvidia Drivers](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by FLeiXiuS on 2005-06-10
Welcome to Ubuntu there bud.  It's an amazing distrobution good choice.  

Open up a terminal, right click on your desktop then go to terminal.

Now it's the fun part :-)

[B]$ sudo apt-get install nvidia-glx
$ sudo gedit /etc/X11/xorg.conf[/B]

Scroll down to your video card, and change the driver to "nvidia" rather then what might possibly be there.  

Save!  And voila.  Three finger salute it and you should be good to go.   If not a fresh reboot is always good.

That should just about do it.  There are many many options available for configurations.  For more details:
[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7664/README.txt)

---

### Post by PryGuy on 2005-06-10
there's a simplier way to install the driver, and you will not have to edit any files, just print out or write down the commands below (cause you'll have to type some of them in the text mode):```
sudo apt-get install nvidia-glx
sudo /etc/init.d/gdm stop
sudo nvidia-glx-config enable
sudo gdm
```
then open the terminal and type 'em one after another!
Good Luck! :)

---

### Post by storybookhero on 2005-06-10
thanx man it totally worked...thanx a million!

---

### Post by PryGuy on 2005-06-10
nVidia+Ubuntu=Love :)

---

### Post by storybookhero on 2005-06-10
[QUOTE=PryGuy]nVidia+Ubuntu=Love :)[/QUOTE]
 how do you change the resolution tho...all I can select is 640x480 800x600 and 1024x768 how can I get others to work ?

---

### Post by PryGuy on 2005-06-10
hmmm, guess on this point you'll have to edit the /etc/X11/xorg.conf file... do the following from your terminal:```
sudo gedit /etc/X11/xorg.conf
``` there's a section that has all the resolutions your card operates with, you'll find it easily... It should look somehow like this:```
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes    "1024x768" "800x600" "640x480"
	EndSubSection
``` Try adding, say, 1280X1024 before other modes, so the line should look like this: ```
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
```Save changes, restart X server, or if you don't know how to do it just reboot! I hope it will help

---

### Post by storybookhero on 2005-06-10
I tried the last method that you explained to me and saved it and everything and it still doesnt work....I hate being in 1024x768 and its dricing me insane.  this is what it looked like when I was finished 
Depth		1
		Modes	 "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"

there were plenty of other sections that looked exactly the same...so I edited them as well. I dont know if I did it right or if there is another way around this? let me know plzzz

---

### Post by PryGuy on 2005-06-10
well, I think you better RTFM in this case. :) Actually there are three or four sections looking like the quote in my previous message, but they are for different colour depths as you've probably noticed, there's also the "Default" section. There's also the utility called "Screen size" or something like that in Gnome. Probably you've got the new resolution listed but X server uses the old one. 

Yet it's strange to me why you haven't got the HIGHEST resolution possible after the setup; the thing is Ubuntu autodetects cards (at least it works in case of nVidia) and displays and sets the highest resolution by default... It actually confuses me cause I have a 17 inch display on my dad's PC and Ubuntu automatically sets 1280X1024 there and everything looks too small for this display, so think it's not that great that the installer won't let us choose the resolution we want actually. The question is, are you sure your hardware can do anything higher than 1024X768, cause if it can why the installer failed to set the higher resolution then?

---

### Post by storybookhero on 2005-06-10
I have an Nvidia geforce 6600 gt..so I know its capable of doing the indicated resolutions and I've done so in windows..Im just tired of windows and would like to set up linux on a permanant babsis...I like having the smaller resolution because I like being able to fit more icons on my desktop and it gives it a cleaner look.

---

### Post by PryGuy on 2005-06-10
Yes, nodoubtly, nVidia cards support resolutions higher than 1024X768, but does your display support them, that's the question. Can you look it up in Windows what resolution it uses exactly?

---

### Post by FLeiXiuS on 2005-06-10
Also try taking a look into the VertRefresh in your xorg.conf also.  That depends on the resolutions your aiming for.  If not take a look into modelines.

---

