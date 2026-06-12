---
title: "Problem: NVIDIA 9600M Graphics Card with Ubuntu 9.10"
date: 2009-11-18
forum: Hardware
---

### Post by madmax.santana on 2009-11-18
I own an HP HDX 16 customized to order laptop. It has a built-in NVIDIA 9600M graphics card. I had been using Ubuntu Jaunty on this hardware. It caused me a few hardware problems but they were fortunately automatically solved. _Now I have un-installed my Ubuntu Jaunty OS and installed the Ubuntu 9.10 (Karma Koala)..._

I must mention that I am not a pro in linux or Ubuntu, I have been using it just for a few weeks now and I certainly am no specialist for solving hardware problems. Therefore I shall need to rooted, solid, elaborate and easy to understand solution of my problem if yoi please.

**Problem Statement** :)
My graphics card doesn't seem to work... :(
[B]
How did I deduce this?[/B] :P
When I try to apply enhanced graphics effects on my desktop settings window, it simply says, "Graphics effects could not be enables".

**Solutions I have Already Tried:-**
There was same problem with the Jaunty and I did this... System _-> Administration -> Hardware Drivers... Then it displayed that an NVIDIA gfx card used a propreity driver and I shall have to install it from there. It caused a few further problem but eventually it would get solved somehow (I am not sure but maybe the driver was downloaded unknowingly and installed by the driver manager)... I tried to do the same in Karma Koala... The problem is, when I open the Hardware Drivers window it displays "No propriety drivers are in use on this system."

**Sentiments** :P
I am extremely annoyed. Not that I "need" these drivers. But when I spent so much money on the hardware, it is my birth right to be able to use it, wouldn't you agree? ;)

Help needed. Please post the solution or links to the discussions. Thank you very much.
____________________________________
Mario Alexandro "Fransis" Santana


**EDIT**
I came across this post:
[http://ubuntuforums.org/showthread.php?t=990978&highlight=nVidia+9600M](http://ubuntuforums.org/showthread.php?t=990978&highlight=nVidia+9600M)
I have downloaded the driver from nVidia website. But I don't know how to disable my Graphics driver before installing the new one. If anyone could help on that, I would be grateful. _Plus, independent comments (directly related to problem above "Edit") are also welcome._

---

### Post by norwoods on 2009-11-18
is there a box with entries like:
MVIDIA accelerated graphics driver (version 190)
is one of the drivers labelled:
[Recommended]
what happens if you click the line with:
[Recommended]
what happens if you click the Activate button

---

### Post by madmax.santana on 2009-11-19
> **norwoods said:**
> is there a box with entries like:
MVIDIA accelerated graphics driver (version 190)
is one of the drivers labelled:
[Recommended]
what happens if you click the line with:
[Recommended]
what happens if you click the Activate button



Nope... I mentioned that... It was present in Ubuntu Jaunty but not in Karma.

---

### Post by norwoods on 2009-11-20
you can find the latest driver versions for nvidia at:
[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

the latest version today is 190.42

you can find a repository if you google:
launchpad ppa nvidia 190.42

one repository is at:
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

if you follow the instruction there:
Adding this PPA to your system
You can update your system with unsupported packages from this untrusted PPA by adding ppa:nvidia-vdpau/ppa to your system's Software Sources.

and then use synaptic or apt to get:
nvidia-graphics-drivers-190 
nvidia-settings-190

---

### Post by madmax.santana on 2009-11-25
Hi norwoods!

> root@Mean-Machine:~# apt-get install nvidia-graphics-drivers-190 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-graphics-drivers-190


Does it mean I have not correctly added the ppa??? But it gave me no error when I imported the package list by "apt-get update"

---

### Post by madmax.santana on 2009-11-25
Also I must mention that nvidia-settings-190 is correctly installed.

When I start nVidia X-server Settings: It says that it looks like I am not using an nVidia-X graphics driver... So I must start nvidia-xserver in root and re-run my x-server. I haven't given it a tr but I don't get what it all means and how to do it. Also I doubt it will work. Because my x-drivers shall not be installed still.

**EDIT:**  Incidentally I came across this...
> Reading state information... Done
The following packages have been kept back:
  nvidia-185-modaliases
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
This was obtained from running apt-get upgrade

---

### Post by norwoods on 2009-11-26
i am still running 9.04 and it appears that changes have been made in this area.  you probably know more about it than i do at this point.
the most i can suggest is run synaptic and click the Origin button near the lower left and then click ppa.launchpad.net/main and it will tell you what is available from that site.  look for the 190 drivers, of course.

---

### Post by madmax.santana on 2009-11-28
Oh thanks norwoods! I never considered using synaptics in GUI... And when I did, it was really helpful... It appears that it's not nvidia-graphics-drivers-190... It's nvidia-glx-190...

I have selected the mentioned package and am currently installing it... Dunno yet whether it'll work or not... Maybe I'll have to bother you again... :D

---

### Post by madmax.santana on 2009-11-28
Naaah! Same problem!!! Can anyone else suggest a solution?
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

---

### Post by madmax.santana on 2009-12-05
I've been messing around with too remotely relevant things while the solution was in front of me! I already had it in back of my mind but I don't know ehy I was hesitating to try it. I tried it, and it is the exact solution for the NVIDIA Graphics Driver Problem!

For anyone else who has the same problem:

Just download the .so driver binary from the nVidia website.
This is where I downloaded my driver for x86_64 for nVidia GeForce 9600M
[http://www.nvidia.com/object/linux_display_amd64_190.42.html](http://www.nvidia.com/object/linux_display_amd64_190.42.html)

And then follow this procedure.
[COLOR=Red]**1 **[/COLOR]- Press Ctrl+Alt+F1. This will lead you to a console.

**[COLOR=Red]2 [/COLOR]**- For next steps you need to be root. So either you can execute every command by prefixing it with sudo or consider entering the root shell permanently.
> sudo bash
and enter you password.

**[COLOR=Red]3[/COLOR]** - But you should close your X-Server first, that means end your gnome session. That is carried out by:
> service gdm stop
in Karmic
and by:
> /etc/init.d/gdm stop
in previous releases.

**[COLOR=Red]4[/COLOR]** - Once the GNOME has been shutdown, move to the directory in which the downloaded driver binary was located. In my case, it would be ~/Downloads. So:
> cd ~/Download

[COLOR=Red]**5**[/COLOR] - You might consider renaming the file to a short name so that you do not have to type long.
> mv ./Whatever-File-Name ./WFN

[COLOR=Red]**6**[/COLOR] - Then you have choice. Either you can directly run it through sh
> sh ./WFN
**[COLOR=YellowGreen]--OR--[/COLOR]**
You can first make the binary file executable
> chmod +x "WFN"
Then just type the filename and it will be executed directly by the console.

[COLOR=Red]**7**[/COLOR] - This is it... An interactive installer is started. Follow the instructions and let it do its work. This should install new drivers and render old drivers void.

**[COLOR=Red]8[/COLOR]** - After the setup ends restart you computer by
> shutdown -r now

TaDa, you're done. It worked very well for me, should do good for yeh as well. I do not remember exactly where I had read little about this thing long ago, but i sure want to thank whoever told me that. Adios

---

### Post by madmax.santana on 2009-12-05
And thanks everyone else, who spent some time on this post to help me out! **Ubuntu **(the philosophy) is alive because of such people. Really, forums and communities are the soul of the Open Source Software!

---

