---
title: "Install problems..."
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by Didel on 2005-04-11
Hi guys, 

As you might have seen, i'm brand new here. I registeredd because I have a problem. Some days ago I downloaded the newest version of UBUNTU Hedgehog (5.04). I put the iso-file on a cd and put it in my pc. I rebooted and the Ubuntu install screen ( the one where you see: Boot: [   ] ( at[   ] you have to press enter, or type server))appeared on my screen. When I press enter, mycd player starts buzzing slightly ( likenormally whenyouinstall smt. and i see a greytext scrolling over my momnitor( the text is where it detects my hardware) after it is finished with that, my screen turns black, and i get a out-of-range error message of my monitor, saying that the screenresolution can't be set to 720 x 400 :???: 
In windows i have the resolution set to 1024x768 I tried to rebootr several times but just the same...

My computer is:
AMD Athlon XP 2800+
NVidia GeForce FX 5200
512MB DDR-RAM
And currently running onWindows XP Home-Edition ( legal)

My monitor: 
15"
Display size 304 x 228 mm
Resolution 1024 x 768 mm
0.297 x 0.297 pixel pitch ( area of 1 pixel i suppose)
16.7 M DisplayColor
Contrast Ratio: 350:1
( that's all you need to know i hope)

I hope anyone can help me to find a solution [-o< 
I'm new,so if youhaveone, please explain good
( andsorry, my space-bar is abit weird, that's why some wordsare stuck together :-| )

---

### Post by erkki70 on 2005-04-11
Hi,
First, just after X fails, try this command:
```
sudo dpkg-reconfigure xserver-xorg
```
enter your password and answer all the questions.
If it still fails try the vesa driver or try the following as in this thread [http://ubuntuforums.org/showthread.php?t=8831](http://ubuntuforums.org/showthread.php?t=8831) 
[QUOTE=jbh]after X fails.. (it did for me the first few times too after install)

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable

then edit /etc/X11/XF86Config-4 (for the warty version)
or /etc/X11/xorg.conf (for hoary)

and change this:
```
Section "Device"
	Identifier	"NVIDIA Corporation GeForce 6800GT"
	Driver 		"nvidia"
	Option 		"RenderAccel" "true"
	Option 		"AllowGLXWithComposite" "True"
	Option 		"NoLogo" "1"
	Option 		"NvAgp" "3"
	BusID 		"PCI:1:0:0"
EndSection
```

Try playing around with the NvAgp option, set it to "1" to use the nvidia agp module, which I can't get to work, and x won't boot unless i have it set to "3" (which means use the AGPGART linux driver)

then enter  ```
sudo ln -s /usr/X11R6/lib/modules/extensions/libglx.{so,a}
```

startx. doesn't work, reboot. still doesn't work search for other threads on this forum of screwed up nvidia configs.


you know everything works if X boots and the command 'glxgears' at the prompt works. or 'cat /proc/driver/nvidia/agp/status'[/QUOTE]

---

### Post by Didel on 2005-04-11
Hi,

I don't know what you're talking about exactly... i am current runningon Windows, have neverhad any experiece with linux and when i type in: sudo ....-xorg itsais: No such ... ( forgotit, sorry..., but it is the same if you just type something)
i think qwwehave a slight misunderstanding... I'm talking about the install screen, notabout a login-sreen or something... i don't have yet a linux versiononmy pc...
And again,couldyou be abit morespecific? ( io'm a noOob...)

---

### Post by erkki70 on 2005-04-12
[QUOTE=Didel]Hi,

I don't know what you're talking about exactly... i am current runningon Windows, have neverhad any experiece with linux and when i type in: sudo ....-xorg itsais: No such ... ( forgotit, sorry..., but it is the same if you just type something)
i think qwwehave a slight misunderstanding... I'm talking about the install screen, notabout a login-sreen or something... i don't have yet a linux versiononmy pc...
And again,couldyou be abit morespecific? ( io'm a noOob...)[/QUOTE]

Hi,
In order to provide help people here need detailed infos, no matter if you're a newbie, just try to post facts and error messages as they are displayed to you.
So, could you tell step by step what you've done so far and where exactly do you get stuck? What install did you select? Any special options? Accurate error messages posting will help.
I assume you have a console, so you can type in commands.
Please post the result of ```
ls
```command after typing this to get to the root of your system ```
cd /
```.
This will show how is your system.

Also is it the installer or the Live-CD you're running?

Good luck and hope this helps.
Cheers,
Erkki

---

