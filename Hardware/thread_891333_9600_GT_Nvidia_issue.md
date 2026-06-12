---
title: "9600 GT Nvidia issue??"
date: 2008-08-15
forum: Hardware
---

### Post by sfife on 2008-08-15
I am an absolute noob when comes to graphics cards, playing around with the terminal and configuration files:( Recently bought a new computer 9600 GT Nvidia and Ubuntu 8.04 wont even detect it. I have read through various forums and researched Nouveau Wiki and still cant seem to get my head around it. Can anyone out there direct me or give me a solution with my problem.
Thankyou and please help me take one step further away from other operating systems.

---

### Post by sudo_chop on 2008-08-16
Same issue here w/ 9600M GT, new laptop. Subscribed.

---

### Post by sfife on 2008-08-16
Found this link and followed all the prompts and the Nvidia driver seemed to install properly with no hick ups but I think the problem is detection. I'm not sure??

[http://ubuntuforums.org/showthread.php?t=309787](http://ubuntuforums.org/showthread.php?t=309787)

I found the Nvidia package on their site/support. If you wanna try this you'll need libc6 dev installed and you'll need to do it from root so.... thats ctlr+alt+F1 to exit X server and ctlr+altF7 to bring it back. But once in type  sudo /etc/init.d/gdm stop and this will stop your gdm then sudo su to get root and then type: sh 'whatever the location of the file you downloaded was eg. /home/username/NVIDIA-linux-x86 and so on.

Please correct me if I'm wrong because I need help on this as much as the next person :)

---

### Post by sudo_chop on 2008-08-16
So you successfully installed the driver package, but it still doesn't work? I am about to try installing the driver now, so if yours didn't work, then hope is lost for me. Hope we can figure this out

---

### Post by sfife on 2008-08-16
Found a Nvidia package installed in my Applications/System tool and now it's asking me to: 

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server

I tried doing this and it reported more errors. Still trying to figure it out.

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'

I am more confused now. I'm gonna give it a break and try another day. Just remember to back up you xorg.config before messing about too much and if all fails then use the recovery mode from the kernel election screen(Hold esc at grub load).

Goodluck

---

### Post by sudo_chop on 2008-08-16
Sounds like we are in the same spot. I let the nvidia-xconfig change my xorg.conf and as soon as I started gdm it came up and tole me it was in low-graphics mode bc it couldn't detect my video card or my monitor. I went and checked out the xorg.conf setting and it all looked right, then I checked out that system tool you were talking about and got that same error, saying I wasn't using the nvidia driver, even though I am. Hopefully someone who knows whats up can help us!

---

### Post by berdux on 2008-08-16
hello,

i have a problem with my 9600GT too, i connect my pc through HDMI with my LG TV. it used to work fine at the resolution of 1280x720 (in windows). now it only allows me to use 720x480. I have downloaded from nvidia this driver "NVIDIA-Linux-x86-173.14.12-pkg1.run". I do not know how to install it though (total noob with linux :) )

i suppose when i install the driver it should work fine unless if there is any other issue i'm not aware of...

---

### Post by sudo_chop on 2008-08-16
> **berdux said:**
> hello,

i have a problem with my 9600GT too, i connect my pc through HDMI with my LG TV. it used to work fine at the resolution of 1280x720 (in windows). now it only allows me to use 720x480. I have downloaded from nvidia this driver "NVIDIA-Linux-x86-173.14.12-pkg1.run". I do not know how to install it though (total noob with linux :) )

i suppose when i install the driver it should work fine unless if there is any other issue i'm not aware of...

Yea, here is the readme for that .run file. [http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/index.html)

But unfortunately it will probly only get you to the point where we are, which is nowhere really. gl

---

### Post by berdux on 2008-08-16
ok i got to the point that is says 
"-> No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel.

ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package."

how do i do that? :) 
(or is it the place you're stuck also? :P )

---

### Post by sudo_chop on 2008-08-16
you need libc6-dev as stated above. Then the install will work, *then* you will be stuck where we are stuck ;)

---

### Post by sudo_chop on 2008-08-16
> **sfife said:**
> 

I tried doing this and it reported more errors. Still trying to figure it out.

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'

sounds like somebody didn't sudo :)

---

### Post by piwi on 2008-08-16
> **berdux said:**
> ok i got to the point that is says 
"-> No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel.

ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package."

how do i do that? :) 
(or is it the place you're stuck also? :P )

I had the same problem, you need to go to the terminal and do this,

apt-get install build-essential

I found it here [http://www.nvnews.net/vbulletin/showthread.php?t=81456](http://www.nvnews.net/vbulletin/showthread.php?t=81456)

Good luck

---

### Post by berdux on 2008-08-16
good, i found that just before you tell me :) thanks a lot

the driver is installed, now, it shows other resolutions too, but all smaller than 720x480 :(
also the fan of the graphics card started working at low speed, as it should, like it did in windows when i first installed its driver, so the driver is installed but not fully working i guess...

edit: from aplications/system tools/nvidia control panel   i was able to change the resolution, and all is ok for me now (i havent tried any game yet)

edit2: (some hours later) after my next restart, i am at the place you have stuck also guyz... :( now it says i'm not using nvidia driver and is working in low graphics mode...

---

### Post by berdux on 2008-08-16
by reinstalling the driver everything works...

but only until next restart, every time you have to go:
ctrl+alt+F1
sudo /etc/init.d/gdm stop
sudo sh Desktop/pkg.run
sudo gdm

and then change resolution, configuration, etc..

is there any way to fix that?

---

### Post by sfife on 2008-08-16
> **sudo_chop said:**
> sounds like somebody didn't sudo :)

Finally found how to with: sudo gedit /etc/X11/xorg.conf
This got me into my config file where I can have a look to see if I've installed the Nvidia graphics card right?
 This is what it looks like

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

I'm guessing that's wrong??

---

### Post by sudo_chop on 2008-08-17
> Section "Device"
Identifier "Configured Video Device"
Boardname "vesa"
Busid "PCI:1:0:0"
Driver "vesa"
Screen 0
EndSection

it doesnt look right to me, but idk. Hopefully someone here knows for sure

---

### Post by Lantesh on 2008-08-17
Here is an easy solution that will get you up and running on Hardy Heron using the program Envy.  We do however need to get the latest nVidia 173 (older versions do not support the 9600 GT) driver though, and it's not in the regular Ubuntu repo.  It's in the proposed repo.

1. Get rid of whatever botched driver install you already have
```
sudo apt-get remove nvidia*
```
2. Install the program Envy
```
sudo apt-get install envyng-gtk
```
3. Enable the “proposed” repository in your sources.list file.
```
sudo gedit /etc/apt/sources.list
```
Find the line for the repo and uncomment it.  Save the file.
4. Now that you've enabled the proposed repo you need to refresh the package list
```
sudo apt-get update
```
4. Launch Envy with this command
```
sudo envyng -g
```
5. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
6. Once the installation is completed reboot.

---

### Post by sudo_chop on 2008-08-17
> **Lantesh said:**
> 
3. Enable the “proposed” repository in your sources.list file.
```
sudo gedit /etc/apt/sources.list
```
Find the line for the repo and uncomment it.  Save the file.


I don't see a "proposed" repository in my sources.list

The only two I see in there that are commented out are the 'backports' and 'partner' ones.

---

### Post by sudo_chop on 2008-08-17
> **Lantesh said:**
> Here is an easy solution that will get you up and running on Hardy Heron using the program Envy.  We do however need to get the latest nVidia 173 (older versions do not support the 9600 GT) driver though, and it's not in the regular Ubuntu repo.  It's in the proposed repo.

1. Get rid of whatever botched driver install you already have
```
sudo apt-get remove nvidia*
```
2. Install the program Envy
```
sudo apt-get install envyng-gtk
```
3. Enable the “proposed” repository in your sources.list file.
```
sudo gedit /etc/apt/sources.list
```
Find the line for the repo and uncomment it.  Save the file.
4. Now that you've enabled the proposed repo you need to refresh the package list
```
sudo apt-get update
```
4. Launch Envy with this command
```
sudo envyng -g
```
5. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
6. Once the installation is completed reboot.

I enabled the backports repo and it worked like a charm. 1920x1200... so pretty lol

Thanks for the step by step, Lantesh!

---

### Post by Crafty Kisses on 2008-08-17
One of my friends had the same issue, and he downloaded and compiled the drivers off of NVIDIA's website and it worked. :)

---

### Post by berdux on 2008-08-17
thank you Lantesh, it worked fine!

---

### Post by philippe.c on 2008-08-18
hi, I am really fustrated right now, I am trying to get my card to work, but I cant even type my password on the terminal, its just doesn't happend anything when I hit the keyboard. I am a newbie with linux, I am really lost in space right now, heheheeheh. any help will be most appreciated.

---

### Post by Norwal on 2008-09-03
Thanks Lantesh.  I can't believe it was a repository issue.  I got my 32bit harddrive going 4 weeks ago, but couldn't get my 64 bit going until I found your post.:lolflag:

---

### Post by bf1958 on 2008-09-07
Worked fine Lantesh, made my day. I was starting to think that the card was going to take off the cooling fan was spinning so fast.  :guitar:

bf1958

---

### Post by xonegon on 2008-09-08
> **Lantesh said:**
> 

3. Enable the “proposed” repository in your sources.list file.
```
sudo gedit /etc/apt/sources.list
```
Find the line for the repo and uncomment it.  Save the file.


for those like me that didn't understand this at first :
ctrl+f , search for REPO and you'll get around 4 results, go into the big block of text with  "backports" in it, you'll see 2 links or so, delete the words "restricted " and save. the rest is easy as pie.

thx lantesh

---

### Post by tuketko on 2008-09-08
Hi.
I installed my 9600gt on acer aspire 5930 using envyng. All seems like good (compiz is runnig) but one thing bothering me still.

lspci show me:
```
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0649 (rev a1)
```

and glxgear show score ony 3000 fps. I think it's low (correct is cca 17000 I think).

Can you post me your score?
Thanks. (sorry for my english)

---

### Post by chevett on 2008-09-09
I followed Lantesh's instructions.  I enabled the backports repo's.  It didn't work.  Then I tried again after removing 'restricted' from those repos.  It still didn't work.  I get the same error I get whenever I try running envy.

[ATTACH]84740[/ATTACH]

---

### Post by chevett on 2008-09-09
I also added the hardy-proposed repository and I still get the same error.

---

### Post by sunshineacid on 2008-09-11
Lantesh's fix worked for me. It enabled my card without a hitch. But it broke my wireless. I think it disabled my restricted drivers for my dlink card. If i disable the new repository and re update the system on a wired connection do you think it will correct the problem, or am i barking up the wrong tree?

---

### Post by tradet on 2008-09-15
Latesh worked without a hitch.

---

### Post by Lantesh on 2008-09-15
Thanks for the thanks guys.  I'm glad to help when I can.  For the couple of guys that this didn't help I'm sorry, but that's all I've got unfortunately.  Best of luck to you.

---

### Post by tifozif1 on 2008-09-21
> **Lantesh said:**
> Here is an easy solution .....Thank you !!!

---

### Post by Lantesh on 2008-09-24
Hey guys if you really want to push things I just found the new 177.76 driver yesterday in the Intrepid repositories.  I can report it's working fine on my system, although my first attempt at installing it did not go so well.  Be careful and have fun!

---

### Post by james429 on 2008-09-24
9600 GT GPU offers a powerfully immersive entertainment experience designed for extreme high-definition gaming and video playback.
==================
james
[Business For Sale]("http://savvybusiness.com.au")

---

### Post by dancavs on 2008-10-01
> **chevett said:**
> I followed Lantesh's instructions.  I enabled the backports repo's.  It didn't work.  Then I tried again after removing 'restricted' from those repos.  It still didn't work.  I get the same error I get whenever I try running envy.

[ATTACH]84740[/ATTACH]

gday i installed latest driver from nvidia website "manually" for the 9600gt using this how to: 

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

good luck :)

---

### Post by chevett on 2008-10-04
Still no luck for me.  I've tried installing every version of the driver manually.  The results are always the same.  Install goes fine, but x just can't startup.  I either get a black screen or a messed up window talking about "low graphics mode".  Then I have to regenerate my xorg.conf.

I'm running amd64 and I've got the asus en9600gt.  Anybody else getting this combo running?

---

### Post by dancavs on 2008-10-04
> Anybody else getting this combo running? 

yes, lantesh (see above in his signature)

> Hardware: Asus M2N-SLI Deluxe, AMD Athlon 64 6400+, 2 gig DDR2, nVidia 9600GT, 1 TB HD storage
Software: Linux Mint 5 Elyssa 

i also had no display after installing the driver. i had to manually edit my xorg.conf file for correct display resolutions and horiz and vertical refresh rates, then it worked after that. i followed this how to: 

[https://help.ubuntu.com/community/Fi...esolutionHowto](https://help.ubuntu.com/community/Fi...esolutionHowto)

---

### Post by bobthedisease on 2008-10-19
Hi Guys
I had similar issues getting the card working but a manual install worked fine for me and i have Compiz, EVE online etc working great....
However I do have one problem, whenever i try to play 720p media files i get random freezes while watching, like it's having trouble rendering the video. I know these files are fine as they all worked on my Nvidia 7300 which i just removed.
I have also tested removing the drivers and going back the "nv" drivers and they all work fine, so i can only guess that it is something to do with the Nvidia restricted drivers (177.80), i have tried several flavors of Nvidia drives with no luck
Any ideas?

Regards
Rich

System AMD 6000+
2gb DDR3
Ubuntu 8.04

---

### Post by chevett on 2008-10-29
> **dancavs said:**
> 
i also had no display after installing the driver. i had to manually edit my xorg.conf file for correct display resolutions and horiz and vertical refresh rates, then it worked after that. i followed this how to: 
[https://help.ubuntu.com/community/Fi...esolutionHowto](https://help.ubuntu.com/community/Fi...esolutionHowto)

How did you determine the correct values for your refresh rates?

Apparently, running
```
sudo ddcprobe | grep monitorrange
```

will not give you any values on an amd64: [bug#8177]("https://bugs.launchpad.net/ubuntu/+source/vbetool/+bug/8177")

I had values in my generated xorg.conf but I tried changing them to the following:

```
HorizSync       30.0 - 96.0
VertRefresh     48.0 - 120.0
```

I still have the same problem.  X starts, but the screen is mangled.  The top of the screen has some green lines then static in the middle and then on the bottom of the monitor I get the top 2 inches or so of the login screen.  However, what should be the top left of the screen is in the middle.  I can also see a bit of a dialog box warning about low graphics mode.

I also tried manually installing the recently released drivers(177.80), but that didn't help.  Also, when installing the driver manually I accept all the defaults. 

Would posting my xorg.conf help anyone spot the problem?  

Any ideas would be greatly appreciated.  I've been trying to get this going for a long time now and I am totally lost.

---

### Post by LeslieL on 2008-10-30
I nearly have the screen resolution problem resolved. Envy seemed to be the most secure way. Now I've got the resolution on my laptop screen all the way up to 1024 x 768. In Windows it's 1280 x 800, but I can't seem to get that, even by editing my xorg.conf file. I have a generic PnP monitor with an NVIDIA MCP67M card. Any suggestions?

---

